---
tags:
  - directX11
  - translation
---

[[4e6681295c8988ce3e1188ea76afffae_MD5.jpeg|Open: Pasted image 20250726152301.png]]
![[4e6681295c8988ce3e1188ea76afffae_MD5.jpeg]]

# Summary

In the previous tutorial, we rendered a cube from model space to the screen.

이전 튜토리얼에서, 모델 공간의 큐브를 화면에 띄워보았다.

In this tutorial, we will extend the concept of transformations and demonstrate simple animation that can be achieved with these transformations.

이 튜토리얼에서, 변환의 개념을 확장하고 이러한 변환들을 통해 얻을 수 있는 간단한 애니메이션을 시연해볼 것이다.

The outcome of this tutorial will be an object that orbits around another.

이 튜토리얼의 결과는 다른 물체 주위를 도는 물체가 될 것이다.

It would be useful to demonstrate the transformations and how they can be combined to achieve the desired effect.

변환을 시현하고 원하는 효과를 얻기 위해 변환을 조합하는 방법을 배우는 것은 유용할 것이다.

Future tutorials will be building on this foundation as we introduce new concepts.

향후 튜토리얼에서는 이러한 기반을 바탕으로 새로운 개념을 소개할 예정이다.
# Source

(SDK root)\Samples\C++\Direct3D11\Tutorials\Tutorial05

# Transformation

In 3D graphics, transformation is often used to operate on vertices and vectors.

3차원 그래픽스에서, 변환은 정점들과 벡터들에 대한 작업에 보통 사용된다.

It is also used to convert them in one space to another.

변환은 또한 정점들과 벡터들을 한 공간에서 다른 공간으로 변환시키기 위해서도 사용된다.

Transformation is performed by way of multiplication with a matrix.

변환은 행렬 간 곱셈에 의해 이루어진다.

There are typically three types of primitive transformation that can be performed on vertices: translation (where it lies in space relative to the origin), rotation (its direction in relation to the x, y, z frame), and scaling (its distance from origin).

일반적으로 정점에 대해 수행할 수 있는 기본 변환에는 이동(원점을 기준으로 공간에 놓이는 위치), 회전(x, y, z 프레임에 대한 방향), 배율(원점과의 거리) 등 세 가지 유형이 있다.

In addition to those, projection transformation is used to go from view space to projection space.

이러한 변환들에 더하여, 

The XNA Math library contains APIs that can conveniently construct a matrix for many purposes such as translation, rotation, scaling, world-to-view transformation, view-to-projection transformation, and so on. An application can then use these matrices to transform vertices in its scene. A basic understanding of matrix transformations is required. We will briefly look at some examples below.

# Translation

Translation refers to moving or displacing for a certain distance in space. In 3D, the matrix used for translation has the form

    1  0  0  0
    0  1  0  0
    0  0  1  0
    a  b  c  1

where (a, b, c) is the vector that defines the direction and distance to move. For example, to move a vertex -5 unit along the X axis (negative X direction), we can multiply it with this matrix:

      
    1  0  0  0
    0  1  0  0
    0  0  1  0
   -5  0  0  1

If we apply this to a cube object centered at origin, the result is that the box is moved 5 units towards the negative X axis, as figure 5 shows, after translation is applied.

**Figure 1.  The effect of translation**

[[64db42eb4ec42b245b1a3dee65829b2a_MD5.jpeg|Open: Pasted image 20250726152423.png]]
![[64db42eb4ec42b245b1a3dee65829b2a_MD5.jpeg]]

In 3D, a space is typically defined by an origin and three unique axes from the origin: X, Y and Z. There are several spaces commonly used in computer graphics: object space, world space, view space, projection space, and screen space.

**Figure 2.  A cube defined in object space**

[[0a55d7a46a9d38605ac796827c66c46b_MD5.jpeg|Open: Pasted image 20250726152440.png]]
![[0a55d7a46a9d38605ac796827c66c46b_MD5.jpeg]]

# Rotation

Rotation refers to rotating vertices about an axis going through the origin. Three such axes are the X, Y, and Z axes in the space. An example in 2D would be rotating the vector [1 0] 90 degrees counter-clockwise. The result from the rotation is the vector [0 1]. The matrix used for rotating ΐ degrees clockwise about the Y axis looks like this:

    cosΐ  0  -sinΐ   0
     0    1     0    0
    sinΐ  0   cosΐ  0
     0    0     0    1

Figure 6 shows the effect of rotating a cube centered at origin for 45 degrees about the Y axis.

**Figure 3.  The effect of rotation about the Y axis**

[[34bc925d2c2df5677b5d2a654e2f6018_MD5.jpeg|Open: Pasted image 20250726152515.png]]
![[34bc925d2c2df5677b5d2a654e2f6018_MD5.jpeg]]

# Scaling

Scaling refers to enlarging or shrinking the size of vector components along axis directions. For example, a vector can be scaled up along all directions or scaled down along the X axis only. To scale, we usually apply the scaling matrix below:

    p  0  0  0
    0  q  0  0
    0  0  r  0
    0  0  0  1

where p, q, and r are the scaling factor along the X, Y, and Z direction, respectively. The figure below shows the effect of scaling by 2 along the X axis and scaling by 0.5 along the Y axis.

**Figure 4.  The effect of Scaling**

[[55969b12301be3d937029fe63e4ad0eb_MD5.jpeg|Open: Pasted image 20250726152538.png]]
![[55969b12301be3d937029fe63e4ad0eb_MD5.jpeg]]

# Multiple Transformations

To apply multiple transformations to a vector, we can simply multiply the vector by the first transformation matrix, then multiply the resulting vector by the second transformation matrix, and so on. Because vector and matrix multiplication is associative, we can also multiply all of the matrices first, then multiply the vector by the product matrix and obtain an identical result. The figure below shows how the cube would end up if we combine a rotation and a translation transformation together.

**Figure 5.  The effect of rotation and translation**

[[d7966247dce0f8d9d09a5aa136f49713_MD5.jpeg|Open: Pasted image 20250726152557.png]]
![[d7966247dce0f8d9d09a5aa136f49713_MD5.jpeg]]

# Creating the Orbit

In this tutorial, we will be transforming two cubes. The first one will rotate in place, while the second one will rotate around the first, while spinning on its own axis. The two cubes will have its own world transformation matrix associated with it, and this matrix will be reapplied to it in every frame rendered.

There are functions within XNA Math that will assist in the creation of the rotation, translation, and scaling matrices.

- Rotations performed around the X, Y. and Z axis are accomplished with the functions **XMMatrixRotationX**, **XMMatrixRotationY**, and **XMMatrixRotationZ**, respectively. They create basic rotation matrices that rotate around one of the primary axis. Complex rotations around other axis can be done by multiplying together several of them.
- Translations can be performed by invoking the **XMMatrixTranslation** function. This function will create a matrix that will translate points specified by the parameters.
- Scaling is done with **XMMatrixScaling**. It scales only along the primary axes. If scaling along arbitrary axis is desired, then the scaling matrix can be multiplied with an appropriate rotation matrix to achieve the effect.

The first cube will be spinning in place and act as the center for the orbit. The cube has a rotation along the Y axis applied to the associated world matrix. This is done by calling the **XMMatrixRotationY** function shown in the following code. The cube is rotated by a set amount each frame. Since the cubes are suppose to continuously rotate, the value which the rotation matrix is based on gets incremented with every frame.

      
    // 1st Cube: Rotate around the origin
    g_World1 = XMMatrixRotationY( t );

The second cube will be orbiting around the first one. To demonstrate multiple transformations, a scaling factor, and its own axis spin will be added. The formula used is shown right below the code (in comments). First the cube will be scale down to 30% size, and then it will be rotated along its spin axis (the Z axis in this case). To simulate the orbit, it will get translated away from the origin, and then rotated along the Y axis. The desired effect can be achieved by using four separate matrices with its individual transformation (mScale, mSpin, mTranslate, mOrbit), then multiplied together.

      
    // 2nd Cube:  Rotate around origin
    XMMATRIX mSpin = XMMatrixRotationZ( -t );
    XMMATRIX mOrbit = XMMatrixRotationY( -t * 2.0f );
    XMMATRIX mTranslate = XMMatrixTranslation( -4.0f, 0.0f, 0.0f );
    XMMATRIX mScale = XMMatrixScaling( 0.3f, 0.3f, 0.3f );
    g_World2 = mScale * mSpin * mTranslate * mOrbit;

An important point to note is that these operations are not commutative. The order in which the transformations are applied matter. Experiment with the order of transformation and observe the results.

Since all the transformation functions will create a new matrix from the parameters, the amount at which they rotate has to be incremented. This is done by updating the "time" variable.

    // Update our time
    t += XM_PI * 0.0125f;

Before the rendering calls are made, the constant buffer must be updated for the shaders. Note that the world matrix is unique to each cube, and thus, changes for every object that gets passed into it.

      
    //
    // Update variables for the first cube
    //
    ConstantBuffer cb1;
    cb1.mWorld = XMMatrixTranspose( g_World1 );
    cb1.mView = XMMatrixTranspose( g_View );
    cb1.mProjection = XMMatrixTranspose( g_Projection );
    g_pImmediateContext->UpdateSubresource( g_pConstantBuffer, 0, NULL, &cb1, 0, 0 );

    //
    // Render the first cube
    //
    g_pImmediateContext->VSSetShader( g_pVertexShader, NULL, 0 );
    g_pImmediateContext->VSSetConstantBuffers( 0, 1, &g_pConstantBuffer );
    g_pImmediateContext->PSSetShader( g_pPixelShader, NULL, 0 );
    g_pImmediateContext->DrawIndexed( 36, 0, 0 );

    //
    // Update variables for the second cube
    //
    ConstantBuffer cb2;
    cb2.mWorld = XMMatrixTranspose( g_World2 );
    cb2.mView = XMMatrixTranspose( g_View );
    cb2.mProjection = XMMatrixTranspose( g_Projection );
    g_pImmediateContext->UpdateSubresource( g_pConstantBuffer, 0, NULL, &cb2, 0, 0 );

    //
    // Render the second cube
    //
    g_pImmediateContext->DrawIndexed( 36, 0, 0 );

# The Depth Buffer

There is one other important addition to this tutorial, and that is the depth buffer. Without it, the smaller orbiting cube would still be drawn on top of the larger center cube when it went around the back of the latter. The depth buffer allows Direct3D to keep track of the depth of every pixel drawn to the screen. The default behavior of the depth buffer in Direct3D 11 is to check every pixel being drawn to the screen against the value stored in the depth buffer for that screen-space pixel. If the depth of the pixel being rendered is less than or equal to the value already in the depth buffer, the pixel is drawn and the value in the depth buffer is updated to the depth of the newly drawn pixel. On the other hand, if the pixel being draw has a depth greater than the value already in the depth buffer, the pixel is discarded and the depth value in the depth buffer remains unchanged.

The following code in the sample creates a depth buffer (a DepthStencil texture). It also creates a DepthStencilView of the depth buffer so that Direct3D 11 knows to use it as a Depth Stencil texture.

      
    // Create depth stencil texture
    D3D11_TEXTURE2D_DESC descDepth;
    ZeroMemory( &descDepth, sizeof(descDepth) );
    descDepth.Width = width;
    descDepth.Height = height;
    descDepth.MipLevels = 1;
    descDepth.ArraySize = 1;
    descDepth.Format = DXGI_FORMAT_D24_UNORM_S8_UINT;
    descDepth.SampleDesc.Count = 1;
    descDepth.SampleDesc.Quality = 0;
    descDepth.Usage = D3D11_USAGE_DEFAULT;
    descDepth.BindFlags = D3D11_BIND_DEPTH_STENCIL;
    descDepth.CPUAccessFlags = 0;
    descDepth.MiscFlags = 0;
    hr = g_pd3dDevice->CreateTexture2D( &descDepth, NULL, &g_pDepthStencil );
    if( FAILED(hr) )
        return hr;

    // Create the depth stencil view
    D3D11_DEPTH_STENCIL_VIEW_DESC descDSV;
    ZeroMemory( &descDSV, sizeof(descDSV) );
    descDSV.Format = descDepth.Format;
    descDSV.ViewDimension = D3D11_DSV_DIMENSION_TEXTURE2D;
    descDSV.Texture2D.MipSlice = 0;
    hr = g_pd3dDevice->CreateDepthStencilView( g_pDepthStencil, &descDSV, &g_pDepthStencilView );
    if( FAILED(hr) )
        return hr;

In order to use this newly created depth stencil buffer, the tutorial must bind it to the device. This is done by passing the depth stencil view to the third parameter of the **OMSetRenderTargets** function.

    g_pImmediateContext->OMSetRenderTargets( 1, &g_pRenderTargetView, g_pDepthStencilView );

As with the render target, we must also clear the depth buffer before rendering. This ensures that depth values from previous frames do not incorrectly discard pixels in the current frame. In the code below the tutorial is actually setting the depth buffer to be the maximum amount (1.0).

      
    //
    // Clear the depth buffer to 1.0 (max depth)
    //