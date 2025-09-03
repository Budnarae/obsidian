---
tags:
  - directX11
  - translation
---

_rain, fire, smoke..._

---

This tutorial will cover how to create particle systems in DirectX 11 using HLSL and C++.

이번 튜토리얼은 DirectX11에서 HLSL과 C++을 사용해서 파티클 시스템을 생성하는 법을 다룬다.

Particles are usually made by using a single texture placed on a quad.

파티클은 주로 쿼드에 놓여진 하나의 텍스처를 사용하여 만든다.

And then that quad is rendered hundreds of times each frame using some basic physics to mimic things such as snow, rain, smoke, fire, foliage, and numerous other systems that are generally made up of many small but similar elements.

그리고 그 쿼드는 하나의 프레임 당 몇백번이 넘게 렌더링된다. 파티클은 기초적인 물리학을 적용하여 구현되는데, 눈, 비, 연기, 불, 나뭇잎, 그리고 일반적으로 많고 서로 유사하고 미세한 입자로 구성되어 있는 다른 시스템을 모사하기 위해서이다.

In this particle tutorial we will use a single diamond texture and render it hundreds of times each frame to create a colorful diamond waterfall style effect.

이번 파티클 튜토리얼에서 우리는 하나의 다이아몬드 텍스처를 사용할 것이다. 그리고 그것을 각 프레임 당 수백번 렌더링하여 다채로운 색상의 다이아몬든 폭포 효과를 생성할 것이다.

Additionally, we will also use blending to blend the particles together so that layered particles cumulatively add their color to each other.

추가적으로, 우리는 블렌딩도 사용할 것이다. 결과적으로 파티클들은 서로 블렌드 되어 층을 이룬 파티클들이 점증적으로 그들의 색상을 다른 입자에 더할 것이다.

Make sure to also read the summary after going over the tutorial as that is where I explain how to expand this basic particle system into a more advanced, robust, and efficient implementation.

튜토리얼을 모두 살펴본 후에는 요약 부분도 꼭 읽어보세요.
그곳에서 이 기본적인 파티클 시스템을 더 고급스럽고, 견고하며, 효율적인 구현으로 확장하는 방법을 설명하고 있습니다.

# Framework

The framework for this tutorial has the basics as usual.

이번 튜토리얼을 위한 프레임워크는 언제나 그렇듯 기본적인 요소들로 구성된다.

It also uses the TimerClass for timing when to emit new particles.

이번에는 또한 새로운 입자를 방출할 타이밍을 구하기 위한 TimerClass를 사용한다.

The new class used for shading the particles is called ParticleShaderClass.

새로운 클래스인 ParticleShaderClass는 새로운 파티클을 셰이딩하기 위해 사용된다.

And finally, the new particle system itself is encapsulated in the ParticleSystemClass.

그리고 마침내, 새로운 파티클 시스템 그 스스로는 ParticleSystemClass에 의해 캡슐화될 것이다.

![[c4c07faa0ecdbde96ff5dc39933fd87d_MD5.jpeg]]

We will start the code section by looking at the particle shader first.

우리는 파티클 셰이더 코드 부분부터 살펴볼 것이다.

# Particle.vs

The particle.vs and particle.ps HLSL shader programs are what we use to render the particles.

파티클을 렌더하기 위해 `particle.vs`와 `particle.ps` HLSL 셰이더 프로그램들을 사용한다.

They are the basic texture shader with an added color modifying component.

이것들은 기본 텍스처 셰이더에 색상 조정 기능이 추가된 형태이다.

```hlsl

/* Filename: particle.vs */

// Globals
cbuffer MatrixBuffer
{
	matrix worldMatrix;
	matrix viewMatrix;
	matrix projectionMatrix;
};

// Typedef

```

The two input types both have a color component so that the particle can have an individual color that is added to the texture base color.

두 개의 입력 형식은 둘 다 색상 요소를 가진다. 따라서 파티클은 텍스처의 기본적인 색깔에 추가되는 독립적인 색깔을 가질 수 있다.

```hlsl

struct VertexInputType
{
	float4 position:POSITION;
	float2 tex:TEXCOORD0;
	float4 color:COLOR;
};

struct PixelInputType
{
	float4 position:SV_POSITION;
	float2 tex:TEXCOORD0;
	float4 color:COLOR;
};

// Vertex Shader
PixelInputType ParticleVertexShader(VertexInputType input)
{
	PixelInputType output;
	
	// Change the position vector to be 4 units for proper matrix calculations.
	input.position.w = 1.0f;
	
	// Calculate the position of the vertex against the world, view, and projection matrices.
	output.position = mul(input.position, worldMatrix);
	output.position = mul(output.position, viewMatrix);
	output.position = mul(output.position, projectionMatrix);
	
	// Store the texture coordinates for the pixel shader.
	output.tex = input.tex;

```

The color is sent through to the pixel shader here.

색상은 다음의 부분을 통해 픽셀 셰이더로 전달된다.

```hlsl

	// Store the particle color for the pixel shader.
	output.color = input.color;
	
	return output;

}

```

# Particle.ps

```hlsl

// Filename: particle.ps

// Global
Texture2D shaderTexture : register(t0);
SamplerState SampleType : register(s0);

// Typedefs

```

The PixelInputType has the added color component in the pixel shader also.

`PixelInputType`에는 픽셀 셰이더에서 사용할 수 있도록 색상(color) 컴포넌트도 추가되어 있습니다.

```hlsl

struct PixelInputType
{
	float4 position : SV_POSITION;
	float2 tex : TEXCOORD0;
	float4 color : COLOR;
};

// Pixel Shader

float4 ParticlePixelShader(PixelInputType input) : SV_TARGET
{
	float4 textureColor;
	float4 finalColor;
	
	// Sample the pixel color from the texture using the sampler at this texture coordinate location.
	textureColor = shaderTexture.Sample(SampleType, input.tex);

```

Here is where we combine the texture color and the input particle color to get the final output color.

다음은 텍스처의 색상과 입력받은 파티클 색상을 혼합하여 최종 색상을 더하는 부분이다.

```hlsl

	// Combine the texture color and the particle color to get the final color result.
	finalColor = textureColor * input.color;
	
	return finalColor;
}

```

# Particleshaderclass.h

The ParticleShaderClass is just the TextureShaderClass modified to handle a color component for the particles.

`ParticleShaderClass`는 단지 파티클을 위한 색상 요소를 다루는 텍스처 셰이더 클래스이다. 

```hlsl

// Filename : Particleshaderclass.h
#pragma once

// INCLUDES

#include <d3d11.h>
#include <d3dcompiler.h>
#include <directxmath.h>
#include <fstream>

using namespace DirectX;
using namespace std;

// Class name: ParticleShaderClass

class ParticleShaderClass
{
private:
	struct MatrixBufferType
	{
		XMMATRIX world;
		XMMATRIX view;
		XMMATRIX projection;
	};

public:
	ParticleShaderClass();
	ParticleShaderClass(const ParticleShaderClass&);
	~ParticleShaderClass();

	bool Initialize(ID3D11Device*, HWND);
	void Shutdown();
	bool Render(ID3D11DeviceContext*, int, XMMATRIX, XMMATRIX, XMMATRIX, ID3D11ShaderResourceView*);

private:
	bool InitializeShader(ID3D11Device*, HWND, WCHAR*, WCHAR*);
	void ShutdownShader();
	void OutputShaderErrorMessage(ID3D10Blob*, HWND, WCHAR*);

	bool SetShaderParameters(ID3D11DeviceContext*, XMMATRIX, XMMATRIX, XMMATRIX, ID3D11ShaderResourceView*);
	void RenderShader(ID3D11DeviceContext*, int);

private:
	ID3D11VertexShader* m_vertexShader;
	ID3D11PixelShader* m_pixelShader;
	ID3D11InputLayout* m_layout;
	ID3D11Buffer* m_matrixBuffer;
	ID3D11SamplerState* m_sampleState;
};

```

# Particleshaderclass.cpp

```hlsl

////////////////////////////////////////////////////////////////////////////////
// Filename: particleshaderclass.cpp
////////////////////////////////////////////////////////////////////////////////
#include "particleshaderclass.h"


ParticleShaderClass::ParticleShaderClass()
{
    m_vertexShader = 0;
    m_pixelShader = 0;
    m_layout = 0;
    m_matrixBuffer = 0;
    m_sampleState = 0;
}


ParticleShaderClass::ParticleShaderClass(const ParticleShaderClass& other)
{
}


ParticleShaderClass::~ParticleShaderClass()
{
}


bool ParticleShaderClass::Initialize(ID3D11Device* device, HWND hwnd)
{
    wchar_t vsFilename[128], psFilename[128];
    int error;
    bool result;

```

We load the particle.vs and particle.ps HLSL shader files here.

이 부분에서 particle.vs와 particle.ps hlsls 셰이더 파일을 로드한다.

```hlsl

	// Set the filename of the vertex shader.
    error = wcscpy_s(vsFilename, 128, L"../Engine/particle.vs");
    if(error != 0)
    {
        return false;
    }

    // Set the filename of the pixel shader.
    error = wcscpy_s(psFilename, 128, L"../Engine/particle.ps");
    if(error != 0)
    {
        return false;
    }

    // Initialize the vertex and pixel shaders.
    result = InitializeShader(device, hwnd, vsFilename, psFilename);
    if(!result)
    {
        return false;
    }

    return true;
}


void ParticleShaderClass::Shutdown()
{
    // Shutdown the vertex and pixel shaders as well as the related objects.
    ShutdownShader();

    return;
}


bool ParticleShaderClass::Render(ID3D11DeviceContext* deviceContext, int indexCount, XMMATRIX worldMatrix, XMMATRIX viewMatrix, XMMATRIX projectionMatrix, ID3D11ShaderResourceView* texture)
{
    bool result;


    // Set the shader parameters that it will use for rendering.
    result = SetShaderParameters(deviceContext, worldMatrix, viewMatrix, projectionMatrix, texture);
    if(!result)
    {
        return false;
    }

    // Now render the prepared buffers with the shader.
    RenderShader(deviceContext, indexCount);

    return true;
}


bool ParticleShaderClass::InitializeShader(ID3D11Device* device, HWND hwnd, WCHAR* vsFilename, WCHAR* psFilename)
{
    HRESULT result;
    ID3D10Blob* errorMessage;
    ID3D10Blob* vertexShaderBuffer;
    ID3D10Blob* pixelShaderBuffer;

```

The layout will require a third element.

레이아웃은 세번째 인자를 필요로 한다.

```hlsl

D3D11_INPUT_ELEMENT_DESC polygonLayout[3];
    unsigned int numElements;
    D3D11_BUFFER_DESC matrixBufferDesc;
    D3D11_SAMPLER_DESC samplerDesc;


    // Initialize the pointers this function will use to null.
    errorMessage = 0;
    vertexShaderBuffer = 0;
    pixelShaderBuffer = 0;

```

Load the particle vertex shader here.

이 부분에서 파티클 정점 셰이더를 로드한다.

```hlsl

	// Compile the vertex shader code.
    result = D3DCompileFromFile(vsFilename, NULL, NULL, "ParticleVertexShader", "vs_5_0", D3D10_SHADER_ENABLE_STRICTNESS, 0,
                                &vertexShaderBuffer, &errorMessage);
    if(FAILED(result))
    {
        // If the shader failed to compile it should have writen something to the error message.
        if(errorMessage)
        {
            OutputShaderErrorMessage(errorMessage, hwnd, vsFilename);
        }
        // If there was nothing in the error message then it simply could not find the shader file itself.
        else
        {
            MessageBox(hwnd, vsFilename, L"Missing Shader File", MB_OK);
        }

        return false;
    }

```

여기서 파티클 픽셀 셰이더를 로드한다.

```hlsl

	// Compile the pixel shader code.
    result = D3DCompileFromFile(psFilename, NULL, NULL, "ParticlePixelShader", "ps_5_0", D3D10_SHADER_ENABLE_STRICTNESS, 0,
                                &pixelShaderBuffer, &errorMessage);
    if(FAILED(result))
    {
        // If the shader failed to compile it should have writen something to the error message.
        if(errorMessage)
        {
            OutputShaderErrorMessage(errorMessage, hwnd, psFilename);
        }
        // If there was nothing in the error message then it simply could not find the file itself.
        else
        {
            MessageBox(hwnd, psFilename, L"Missing Shader File", MB_OK);
        }

        return false;
    }

    // Create the vertex shader from the buffer.
    result = device->CreateVertexShader(vertexShaderBuffer->GetBufferPointer(), vertexShaderBuffer->GetBufferSize(), NULL, &m_vertexShader);
    if(FAILED(result))
    {
        return false;
    }

    // Create the pixel shader from the buffer.
    result = device->CreatePixelShader(pixelShaderBuffer->GetBufferPointer(), pixelShaderBuffer->GetBufferSize(), NULL, &m_pixelShader);
    if(FAILED(result))
    {
        return false;
    }

    // Create the vertex input layout description.
    polygonLayout[0].SemanticName = "POSITION";
    polygonLayout[0].SemanticIndex = 0;
    polygonLayout[0].Format = DXGI_FORMAT_R32G32B32_FLOAT;
    polygonLayout[0].InputSlot = 0;
    polygonLayout[0].AlignedByteOffset = 0;
    polygonLayout[0].InputSlotClass = D3D11_INPUT_PER_VERTEX_DATA;
    polygonLayout[0].InstanceDataStepRate = 0;

    polygonLayout[1].SemanticName = "TEXCOORD";
    polygonLayout[1].SemanticIndex = 0;
    polygonLayout[1].Format = DXGI_FORMAT_R32G32_FLOAT;
    polygonLayout[1].InputSlot = 0;
    polygonLayout[1].AlignedByteOffset = D3D11_APPEND_ALIGNED_ELEMENT;
    polygonLayout[1].InputSlotClass = D3D11_INPUT_PER_VERTEX_DATA;
    polygonLayout[1].InstanceDataStepRate = 0;

```

Add a third component to the layout for the particle shader.

파티클 셰이더를 위해 레이아웃에 세번째 요소를 추가한다.

The third component is the individual color of each particle.

세번째 요소는 각 파티클을 위한 독립적인 색상이다.

```hlsl

	polygonLayout[2].SemanticName = "COLOR";
    polygonLayout[2].SemanticIndex = 0;
    polygonLayout[2].Format = DXGI_FORMAT_R32G32B32A32_FLOAT;
    polygonLayout[2].InputSlot = 0;
    polygonLayout[2].AlignedByteOffset = D3D11_APPEND_ALIGNED_ELEMENT;
    polygonLayout[2].InputSlotClass = D3D11_INPUT_PER_VERTEX_DATA;
    polygonLayout[2].InstanceDataStepRate = 0;

    // Get a count of the elements in the layout.
    numElements = sizeof(polygonLayout) / sizeof(polygonLayout[0]);

    // Create the vertex input layout.
    result = device->CreateInputLayout(polygonLayout, numElements, vertexShaderBuffer->GetBufferPointer(), 
                                       vertexShaderBuffer->GetBufferSize(), &m_layout);
    if(FAILED(result))
    {
        return false;
    }
    
    // Release the vertex shader buffer and pixel shader buffer since they are no longer needed.
    vertexShaderBuffer->Release();
    vertexShaderBuffer = 0;

    pixelShaderBuffer->Release();
    pixelShaderBuffer = 0;

    // Setup the description of the dynamic matrix constant buffer that is in the vertex shader.
    matrixBufferDesc.Usage = D3D11_USAGE_DYNAMIC;
    matrixBufferDesc.ByteWidth = sizeof(MatrixBufferType);
    matrixBufferDesc.BindFlags = D3D11_BIND_CONSTANT_BUFFER;
    matrixBufferDesc.CPUAccessFlags = D3D11_CPU_ACCESS_WRITE;
    matrixBufferDesc.MiscFlags = 0;
    matrixBufferDesc.StructureByteStride = 0;

    // Create the constant buffer pointer so we can access the vertex shader constant buffer from within this class.
    result = device->CreateBuffer(&matrixBufferDesc, NULL, &m_matrixBuffer);
    if(FAILED(result))
    {
        return false;
    }

    // Create a texture sampler state description.
    samplerDesc.Filter = D3D11_FILTER_MIN_MAG_MIP_LINEAR;
    samplerDesc.AddressU = D3D11_TEXTURE_ADDRESS_WRAP;
    samplerDesc.AddressV = D3D11_TEXTURE_ADDRESS_WRAP;
    samplerDesc.AddressW = D3D11_TEXTURE_ADDRESS_WRAP;
    samplerDesc.MipLODBias = 0.0f;
    samplerDesc.MaxAnisotropy = 1;
    samplerDesc.ComparisonFunc = D3D11_COMPARISON_ALWAYS;
    samplerDesc.BorderColor[0] = 0;
    samplerDesc.BorderColor[1] = 0;
    samplerDesc.BorderColor[2] = 0;
    samplerDesc.BorderColor[3] = 0;
    samplerDesc.MinLOD = 0;
    samplerDesc.MaxLOD = D3D11_FLOAT32_MAX;

    // Create the texture sampler state.
    result = device->CreateSamplerState(&samplerDesc, &m_sampleState);
    if(FAILED(result))
    {
        return false;
    }

    return true;
}


void ParticleShaderClass::ShutdownShader()
{
    // Release the sampler state.
    if(m_sampleState)
    {
        m_sampleState->Release();
        m_sampleState = 0;
    }

    // Release the matrix constant buffer.
    if(m_matrixBuffer)
    {
        m_matrixBuffer->Release();
        m_matrixBuffer = 0;
    }

    // Release the layout.
    if(m_layout)
    {
        m_layout->Release();
        m_layout = 0;
    }

    // Release the pixel shader.
    if(m_pixelShader)
    {
        m_pixelShader->Release();
        m_pixelShader = 0;
    }

    // Release the vertex shader.
    if(m_vertexShader)
    {
        m_vertexShader->Release();
        m_vertexShader = 0;
    }

    return;
}


void ParticleShaderClass::OutputShaderErrorMessage(ID3D10Blob* errorMessage, HWND hwnd, WCHAR* shaderFilename)
{
    char* compileErrors;
    unsigned long long bufferSize, i;
    ofstream fout;


    // Get a pointer to the error message text buffer.
    compileErrors = (char*)(errorMessage->GetBufferPointer());

    // Get the length of the message.
    bufferSize = errorMessage->GetBufferSize();

    // Open a file to write the error message to.
    fout.open("shader-error.txt");

    // Write out the error message.
    for(i=0; i<bufferSize; i++)
    {
        fout << compileErrors[i];
    }

    // Close the file.
    fout.close();

    // Release the error message.
    errorMessage->Release();
    errorMessage = 0;

    // Pop a message up on the screen to notify the user to check the text file for compile errors.
    MessageBox(hwnd, L"Error compiling shader.  Check shader-error.txt for message.", shaderFilename, MB_OK);

    return;
}

```

The SetShaderParameters function is the same as the texture shader class since we only set the three matrices and the texture.

`SetShaderParameters` 함수는 오직 세 개의 행렬과 텍스처만 설정한다는 점에서 텍스처 셰이더 클래스와 같다.

```hlsl

bool ParticleShaderClass::SetShaderParameters(ID3D11DeviceContext* deviceContext, XMMATRIX worldMatrix, XMMATRIX viewMatrix,
                                              XMMATRIX projectionMatrix, ID3D11ShaderResourceView* texture)
{
    HRESULT result;
    D3D11_MAPPED_SUBRESOURCE mappedResource;
    MatrixBufferType* dataPtr;
    unsigned int bufferNumber;


    // Transpose the matrices to prepare them for the shader.
    worldMatrix = XMMatrixTranspose(worldMatrix);
    viewMatrix = XMMatrixTranspose(viewMatrix);
    projectionMatrix = XMMatrixTranspose(projectionMatrix);

    // Lock the constant buffer so it can be written to.
    result = deviceContext->Map(m_matrixBuffer, 0, D3D11_MAP_WRITE_DISCARD, 0, &mappedResource);
    if(FAILED(result))
    {
        return false;
    }

    // Get a pointer to the data in the constant buffer.
    dataPtr = (MatrixBufferType*)mappedResource.pData;

    // Copy the matrices into the constant buffer.
    dataPtr->world = worldMatrix;
    dataPtr->view = viewMatrix;
    dataPtr->projection = projectionMatrix;

    // Unlock the constant buffer.
    deviceContext->Unmap(m_matrixBuffer, 0);

    // Set the position of the constant buffer in the vertex shader.
    bufferNumber = 0;

    // Finally set the constant buffer in the vertex shader with the updated values.
    deviceContext->VSSetConstantBuffers(bufferNumber, 1, &m_matrixBuffer);

    // Set shader texture resource in the pixel shader.
    deviceContext->PSSetShaderResources(0, 1, &texture);

    return true;
}


void ParticleShaderClass::RenderShader(ID3D11DeviceContext* deviceContext, int indexCount)
{
    // Set the vertex input layout.
    deviceContext->IASetInputLayout(m_layout);

    // Set the vertex and pixel shaders that will be used to render this triangle.
    deviceContext->VSSetShader(m_vertexShader, NULL, 0);
    deviceContext->PSSetShader(m_pixelShader, NULL, 0);

    // Set the sampler state in the pixel shader.
    deviceContext->PSSetSamplers(0, 1, &m_sampleState);

    // Render the triangle.
    deviceContext->DrawIndexed(indexCount, 0, 0);

    return;
}


```

# Particlesystemclass.h

```hlsl

//////////////
// INCLUDES //
//////////////
#include <d3d11.h>
#include <directxmath.h>
using namespace DirectX;


///////////////////////
// MY CLASS INCLUDES //
///////////////////////
#include "textureclass.h"


////////////////////////////////////////////////////////////////////////////////
// Class name: ParticleSystemClass
////////////////////////////////////////////////////////////////////////////////
class ParticleSystemClass
{
private:

```

The VertexType for rendering particles just requires position, texture coordinates, and color to match up with the ParticleType properties.

렌더링할 파티클을 위한 `VertexType`은 `ParticleType` 요소와 매치하기 위해 오직 위치, 텍스처 좌표, 그리고 색상만을 요구한다.

```hlsl

	struct VertexType
    {
        XMFLOAT3 position;
        XMFLOAT2 texture;
        XMFLOAT4 color;
    };

```

Particles can have any number of properties that define them.

파티클은 스스로를 정의하기 위해 어떠한 개수의 프로퍼티도 가질 수 있다.

In this implementation we put all the properties of a particle in the ParticleType structure.

이번 예제에서 우리는 파티클의 모든 프로퍼티를 `ParticleType` 구조체에 넣을 것이다.

You can add many more but for this tutorial I am just going to cover position, speed, and color.

더 많은 프로퍼티를 추가할 수도 있지만 이번 튜토리얼에서는 위치, 속도, 그리고 색상만을 다룬다.

```hlsl

	struct ParticleType
    {
        float positionX, positionY, positionZ;
        float red, green, blue;
        float velocity;
        bool active;
    };
	
public:
    ParticleSystemClass();
    ParticleSystemClass(const ParticleSystemClass&);
    ~ParticleSystemClass();

```

The class functions are the regular initialize, shutdown, frame, and render.

이 클래스는 보통 사용하는 `initialize`, `shutdown`, `frame`, `render` 함수들을 포함하고 있습니다.

However, note that the Frame function is where we do all the work of updating, sorting, and rebuilding the of vertex buffer each frame so the particles can be rendered correctly.

다만 유의해야 할 점은, 파티클이 제대로 렌더링되도록 하기 위해 `Frame` 함수 내에서 매 프레임마다 파티클의 업데이트, 정렬, 그리고 정점 버퍼의 재구성이 이루어진다는 점입니다.

```hlsl

    bool Initialize(ID3D11Device*, ID3D11DeviceContext*, char*);
    void Shutdown();
    bool Frame(float, ID3D11DeviceContext*);
    void Render(ID3D11DeviceContext*);

    ID3D11ShaderResourceView* GetTexture();
    int GetIndexCount();

private:
    bool LoadTexture(ID3D11Device*, ID3D11DeviceContext*, char*);
    void ReleaseTexture();

    bool InitializeParticleSystem();
    void ShutdownParticleSystem();

    bool InitializeBuffers(ID3D11Device*);
    void ShutdownBuffers();
    void RenderBuffers(ID3D11DeviceContext*);
	
    void EmitParticles(float);
    void UpdateParticles(float);
    void KillParticles();
    bool UpdateBuffers(ID3D11DeviceContext*);

private:

```

We use a single texture for all the particles in this tutorial.

이번 튜토리얼에서 구현하는 모든 파티클들은 하나의 텍스처를 사용하여 만든다.

```hlsl

    TextureClass* m_Texture;

```

The particle system is an array of particles made up from the ParticleType structure.

파티클 시스템은 `ParticleType` 구조체로부터 생성된 파티클 배열이다.

```hlsl

	 ParticleType* m_particleList;

```

The next variables are for setting up a single vertex and index buffer.

다음 변수들은 하나의 정점과 하나의 인덱스 버퍼를 설정하기 위한 것들이다.

Note that the vertex buffer will be dynamic since it will change all particle positions each frame.

```hlsl

	VertexType* m_vertices;
    ID3D11Buffer* m_vertexBuffer, * m_indexBuffer;
    int m_vertexCount, m_indexCount;

```

The following private class variables are the ones used for the particle properties.

다음의 private 클래스 멤버변수들은 파티클 프로퍼티를 위해 사용되는 것들이다.

They define how the particle system will work and changing each of them has a unique effect on how the particle system will react.

이 값들은 파티클 시스템이 어떻게 동작할지를 정의하며, 각 값을 변경하면 파티클 시스템의 반응 방식에 고유한 영향을 미치게 됩니다.

If you plan to add more functionality to the particle system you would add it here by using additional variables for modifying the particles.

만약 파티클 시스템에 추가 기능을 넣는 것을 계획하고 있다면 파티클을 변경하기 위한 추가적인 변수를 여기에 추가하면 된다.

```hlsl

	float m_particleDeviationX, m_particleDeviationY, m_particleDeviationZ;
    float m_particleVelocity, m_particleVelocityVariation;
    float m_particleSize, m_particlesPerSecond;
    int m_maxParticles;

```

We require a count and an accumulated time variable for timing the emission of particles.

파티클 방출 타이밍을 제어하기 위해서는 카운트 변수와 누적 시간(accumulated time) 변수가 필요합니다.

```hlsl

	int m_currentParticleCount;
    float m_accumulatedTime;
};

```

# Particlesystemclass.cpp

```hlsl

////////////////////////////////////////////////////////////////////////////////
// Filename: particlesystemclass.cpp
////////////////////////////////////////////////////////////////////////////////
#include "particlesystemclass.h"

```

The class constructor initializes the private member variables to null.

클래스 생성자는 private 멤버 변수를 null로 초기화한다.

```hlsl

ParticleSystemClass::ParticleSystemClass()
{
    m_Texture = 0;
    m_particleList = 0;
    m_vertices = 0;
    m_vertexBuffer = 0;
    m_indexBuffer = 0;
}


ParticleSystemClass::ParticleSystemClass(const ParticleSystemClass& other)
{
}


ParticleSystemClass::~ParticleSystemClass()
{
}

```

The Initialize function first loads the texture that will be used for the particles.

`Initialize` 함수는 처음에 파티클에 사용될 텍스처를 로드한다.

After the texture is loaded it then initializes the particle system.

텍스처가 로드되면 텍스처는 파티클 시스템을 시작한다.

Once the particle system has been initialized it then creates the initial empty vertex and index buffers.

파티클 시스템이 시작되면 초기 공백 정점 버퍼와 인텍스 버퍼를 생성한다.

The buffers are created empty at first as there are no particles emitted yet.


