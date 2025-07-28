---
tags:
  - directX11
  - translation
---

![[8de55a1c149d557ef0ac0c190529e6e8_MD5.jpeg]]

# Summary

In the previous tutorial, we introduced lighting to our project.

이전 튜토리얼에서 프로젝트에 조명 효과를 추가했다.

Now we will build on that by adding textures to our cube.

이제 

Also, we will introduce the concept of constant buffers, and explain how you can use buffers to speed up processing by minimizing bandwidth usage.

The purpose of this tutorial is to modify the center cube to have a texture mapped onto it.

# Source

(SDK root)\Samples\C++\Direct3D11\Tutorials\Tutorial07

# Texture Mapping

Texture mapping refers to the projection of a 2D image onto 3D geometry. We can think of it as wrapping a present, by placing decorative paper over an otherwise bland box. To do this, we have to specify how the points on the surface of the geometry correspond with the 2D image.

The trick is to properly align the coordinates of the model with the texture. For complex models, it is difficult to determine the coordinates for the textures by hand. Thus, 3D modeling packages generally will export models with corresponding texture coordinates. Since our example is a cube, it is easy to determine the coordinates needed to match the texture. Texture coordinates are defined at the vertices, and are then interpolated for individual pixels on a surface.

## Creating a Shader Resource from the Texture and Sampler State

The texture is a 2D image that is retrieved from file and used to create a shader-resource view, so that it can be read from a shader.

     
hr = D3DX11CreateShaderResourceViewFromFile( g_pd3dDevice, L"seafloor.dds", NULL, NULL, 
         &g_pTextureRV, NULL );

We also need to create a sampler state that controls how the shader handles filtering, MIPs, and addressing. For this tutorial we will enable simple sampler state that enables linear filtering and wrap addressing. To create the sampler state, we will use **ID3D11Device::CreateSamplerState()**.

     
    // Create the sample state
    D3D11_SAMPLER_DESC sampDesc;
    ZeroMemory( &sampDesc, sizeof(sampDesc) );
    sampDesc.Filter = D3D11_FILTER_MIN_MAG_MIP_LINEAR;
    sampDesc.AddressU = D3D11_TEXTURE_ADDRESS_WRAP;
    sampDesc.AddressV = D3D11_TEXTURE_ADDRESS_WRAP;
    sampDesc.AddressW = D3D11_TEXTURE_ADDRESS_WRAP;
    sampDesc.ComparisonFunc = D3D11_COMPARISON_NEVER;
    sampDesc.MinLOD = 0;
    sampDesc.MaxLOD = D3D11_FLOAT32_MAX;
    hr = g_pd3dDevice->CreateSamplerState( &sampDesc, &g_pSamplerLinear );

## Defining the Coordinates

Before we can map the image onto our cube, we must first define the texture coordinates on each of the vertices of the cube. Since images can be of any size, the coordinate system used has been normalized to [0, 1]. The top left corner of the texture corresponds to (0,0) and the bottom right corner maps to (1,1).

In this example, we're having the whole texture spread across each side of the cube. This simplifies the definition of the coordinates, without confusion. However, it is entirely possible to specify the texture to stretch across all six faces, although it's more difficult to define the points, and it will appear stretched and distorted.

First, we updated the structure used to define our vertices to include the texture coordinates.

    
struct SimpleVertex
{
    XMFLOAT3 Pos;
    XMFLOAT2 Tex;
};

Next, we updated the input layout to the shaders to also include these coordinates.

// Define the input layout
D3D11_INPUT_ELEMENT_DESC layout[] =
{
    { "POSITION", 0, DXGI_FORMAT_R32G32B32_FLOAT, 0, 0, D3D11_INPUT_PER_VERTEX_DATA, 0 },
    { "TEXCOORD", 0, DXGI_FORMAT_R32G32_FLOAT, 0, 12, D3D11_INPUT_PER_VERTEX_DATA, 0 },
};

Since the input layout changed, the corresponding vertex shader input must also be modified to match the addition.

struct VS_INPUT
{
    float4 Pos : POSITION;
    float2 Tex : TEXCOORD;
};

Finally, we are ready to include texture coordinates in our vertices we defined back in Tutorial 4. Note the second parameter input is a D3DXVECTOR2 containing the texture coordinates. Each vertex on the cube will correspond to a corner of the texture. This creates a simple mapping where each vertex gets (0,0) (0,1) (1,0) or (1,1) as the coordinate.

     
// Create vertex buffer
SimpleVertex vertices[] =
{
    { XMFLOAT3( -1.0f, 1.0f, -1.0f ), XMFLOAT2( 0.0f, 0.0f ) },
    { XMFLOAT3( 1.0f, 1.0f, -1.0f ), XMFLOAT2( 1.0f, 0.0f ) },
    { XMFLOAT3( 1.0f, 1.0f, 1.0f ), XMFLOAT2( 1.0f, 1.0f ) },
    { XMFLOAT3( -1.0f, 1.0f, 1.0f ), XMFLOAT2( 0.0f, 1.0f ) },

    { XMFLOAT3( -1.0f, -1.0f, -1.0f ), XMFLOAT2( 0.0f, 0.0f ) },
    { XMFLOAT3( 1.0f, -1.0f, -1.0f ), XMFLOAT2( 1.0f, 0.0f ) },
    { XMFLOAT3( 1.0f, -1.0f, 1.0f ), XMFLOAT2( 1.0f, 1.0f ) },
    { XMFLOAT3( -1.0f, -1.0f, 1.0f ), XMFLOAT2( 0.0f, 1.0f ) },

    { XMFLOAT3( -1.0f, -1.0f, 1.0f ), XMFLOAT2( 0.0f, 0.0f ) },
    { XMFLOAT3( -1.0f, -1.0f, -1.0f ), XMFLOAT2( 1.0f, 0.0f ) },
    { XMFLOAT3( -1.0f, 1.0f, -1.0f ), XMFLOAT2( 1.0f, 1.0f ) },
    { XMFLOAT3( -1.0f, 1.0f, 1.0f ), XMFLOAT2( 0.0f, 1.0f ) },

    { XMFLOAT3( 1.0f, -1.0f, 1.0f ), XMFLOAT2( 0.0f, 0.0f ) },
    { XMFLOAT3( 1.0f, -1.0f, -1.0f ), XMFLOAT2( 1.0f, 0.0f ) },
    { XMFLOAT3( 1.0f, 1.0f, -1.0f ), XMFLOAT2( 1.0f, 1.0f ) },
    { XMFLOAT3( 1.0f, 1.0f, 1.0f ), XMFLOAT2( 0.0f, 1.0f ) },

    { XMFLOAT3( -1.0f, -1.0f, -1.0f ), XMFLOAT2( 0.0f, 0.0f ) },
    { XMFLOAT3( 1.0f, -1.0f, -1.0f ), XMFLOAT2( 1.0f, 0.0f ) },
    { XMFLOAT3( 1.0f, 1.0f, -1.0f ), XMFLOAT2( 1.0f, 1.0f ) },
    { XMFLOAT3( -1.0f, 1.0f, -1.0f ), XMFLOAT2( 0.0f, 1.0f ) },

    { XMFLOAT3( -1.0f, -1.0f, 1.0f ), XMFLOAT2( 0.0f, 0.0f ) },
    { XMFLOAT3( 1.0f, -1.0f, 1.0f ), XMFLOAT2( 1.0f, 0.0f ) },
    { XMFLOAT3( 1.0f, 1.0f, 1.0f ), XMFLOAT2( 1.0f, 1.0f ) },
    { XMFLOAT3( -1.0f, 1.0f, 1.0f ), XMFLOAT2( 0.0f, 1.0f ) },
};

When we sample the texture, we will need to modulate it with a material color for the geometry underneath.

## Bind Texture as Shader Resource

A texture and sampler state are objects like the constant buffers that we have seen in previous tutorials. Before they can be used by the shader, they need to be set with the **ID3D11DeviceContext::PSSetSamplers()** and **ID3D11DeviceContext::PSSetShaderResources()** APIs.

     
    g_pImmediateContext->PSSetShaderResources( 0, 1, &g_pTextureRV );
    g_pImmediateContext->PSSetSamplers( 0, 1, &g_pSamplerLinear );

There we go, now we're ready to use the texture within the shader.

## Applying the Texture

To map the texture on top of the geometry, we will be calling a texture lookup function within the pixel shader. The function **Sample** will perform a texture lookup of a 2D texture, and then return the sampled color. The pixel shader shown below calls this function and multiplies it by the underlying mesh color (or material color), and then outputs the final color.

- txDiffuse is the object storing our texture that we passed in from the code above, when we bound the resource view g_pTextureRV to it.
- samLinear will be described below; it is the sampler specifications for the texture lookup.
- input.Tex is the coordinates of the texture that we have specified in the source.

// Pixel Shader
float4 PS( PS_INPUT input) : SV_Target
{
    return txDiffuse.Sample( samLinear, input.Tex ) * vMeshColor;
}

Another thing we must remember to do is to pass the texture coordinates through the vertex shader. If we don't, the data is lost when it gets to the pixel shader. Here, we just copy the input's coordinates to the output, and let the hardware handle the rest.

// Vertex Shader
PS_INPUT VS( VS_INPUT input )
{
    PS_INPUT output = (PS_INPUT)0;
    output.Pos = mul( input.Pos, World );
    output.Pos = mul( output.Pos, View );
    output.Pos = mul( output.Pos, Projection );
    output.Tex = input.Tex;
        
    return output;
}

# Constant Buffers

In Direct3D 11, an application can use a constant buffer to set shader constants (shader variables). Constant buffers are declared using a syntax similar to C-style structs. Constant buffers reduce the bandwidth required to update shader constants by allowing shader constants to be grouped together and committed at the same time, rather than making individual calls to commit each constant separately.

In the previous tutorials, we used a single constant buffer to hold all of the shader constants we need. But the best way to efficiently use constant buffers is to organize shader variables into constant buffers based on their frequency of update. This allows an application to minimize the bandwidth required for updating shader constants. As an example, this tutorial groups constants into three structures: one for variables that change every frame, one for variables that change only when a window size is changed, and one for variables that are set once and then do not change.

The following constant buffers are defined in this tutorial's .fx file.

    cbuffer cbNeverChanges
    {
        matrix View;
    };
    
    cbuffer cbChangeOnResize
    {
        matrix Projection;
    };
    
    cbuffer cbChangesEveryFrame
    {
        matrix World;
        float4 vMeshColor;
    };

To work with these constant buffers, you need to create a ID3D11Buffer object for each one. Then you can call **ID3D11DeviceContext::UpdateSubresource()** to update each constant buffer when needed without affecting the other constant buffers.

    
    //
    // Update variables that change once per frame
    //
    CBChangesEveryFrame cb;
    cb.mWorld = XMMatrixTranspose( g_World );
    cb.vMeshColor = g_vMeshColor;
    g_pImmediateContext->UpdateSubresource( g_pCBChangesEveryFrame, 0, NULL, &cb, 0, 0 );