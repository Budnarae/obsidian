---
tags:
  - directX11
  - translation
---

![[7fa0daea1cf9f3859e206a516f12cb10_MD5.jpeg]]

# Summary

In the previous tutorial, we set up a vertex buffer and passed one triangle to the GPU.

이전 튜토리얼에서, 정점 버퍼를 설정한 후 GPU에 삼각형 하나를 전달했다.

Now, we will actually step through the graphics pipeline and look at how each stage works.

이제, 그래픽 파이프라인 실제 그래픽 파이프라인을 살펴보고 각 스테이지가 어떻게 동작하는지 알아볼 것이다.

The concept of shaders and the effect system will be explained.

셰이더와 효과 시스템의 컨셉을 설명할 것이다.

Note that this tutorial shares the same source code as the previous one, but will emphasize a different section.

이번 튜토리얼은 이전 튜토리얼과 소스코드를 공유하지만, 좀 다른 부분을 자세히 볼 것이다.

## Source

`(SDK root)\Samples\C++\Direct3D11\Tutorials\Tutorial03`

# The Graphics Pipeline

In the previous tutorial, we set up the vertex buffer, and then we associated a vertex layout with a vertex shader.

이전 튜토리얼에서 정점 버퍼를 설정하고 정점 레이아웃을 정점 셰이더와 연결했다.

Now, we will explain what a shader is and how it works.

이제 셰이더의 정의와 동작을 설명할 것이다.

To fully understand the individual shaders, we will take a step back and look at the whole graphical pipeline.

개개의 셰이더를 완전히 이해하기 위해서, 일단 한걸음 물러나 전체 그래픽 파이프라인을 살펴보도록 하자.

In Tutorial 2, when we called **VSSetShader()** and **PSSetShader()**, we actually bound our shader to a stage in the pipeline.

[[DirectX SDK Document - Tutorial 2 Rendering a Triangle | tutorial 2]]에서, `VSSetShader()`와 `PSSetShader()`를 호출하여 셰이더를 파이프라인의 각 스테이지에 바인드했다.

Then, when we called **Draw**, we start processing the vertex data passed into the graphics pipeline.

그런다음, `Draw()`를 호출하여 정점 정보를 그래픽 파이프라인에 넘겨 처리했다.

The following sections describe in detail what happens after the **Draw** command.

다음 단락은 `Draw()` 명령을 호출했

# Shaders

In Direct3D 11, shaders reside in different stages of the graphics pipeline. They are short programs that, executed by the GPU, take certain input data, process that data, and then output the result to the next stage of the pipeline. Direct3D 11 supports three basic types of shaders: vertex shader, geometry shader, and pixel shader. A vertex shader takes a vertex as input. It is run once for every vertex passed to the GPU via vertex buffers. A geometry shader takes a primitive as input, and is run once for every primitive passed to the GPU. A primitive is a point, a line, or a triangle. A pixel shader takes a pixel (or sometimes called a fragment) as input, and is run once for each pixel of a primitive that we wish to render. Together, vertex, geometry, and pixel shaders are where the meat of the action occurs. When rendering with Direct3D 11, the GPU must have a valid vertex shader and pixel shader. Geometry shader is an advanced feature in Direct3D 11 and is optional, so we will not discuss geometry shaders in this tutorial. In Direct3D 11 there are also hull and domain shaders for tessellation and compute shaders for compute. For more information about these, see the other samples.

## Vertex Shaders

Vertex shaders are short programs that are executed by the GPU on vertices. Think of vertex shaders as C functions that take each vertex as input, process the input, and then output the modified vertex. After the application passes vertex data to the GPU in the form of a vertex buffer, the GPU iterates through the vertices in the vertex buffer, and executes the active vertex shader once for each vertex, passing the vertex's data to the vertex shader as input parameters.

While a vertex shader can be used to carry out many tasks, the most important job of a vertex shader is transformation. Transformation is the process of converting vectors from one coordinate system to another. For example, a triangle in a 3D scene may have its vertices at the positions (0, 0, 0) (1, 0, 0) (0, 1, 0). When the triangle is drawn on a 2D texture buffer, the GPU has to know the 2D coordinates of the points on the buffer that the vertices should be drawn at. It is transformation that helps us accomplish this. Transformation will be discussed in detail in the next tutorial. For this tutorial, we will be using a simple vertex shader that does nothing except passing the input data through as output.

In the Direct3D 11 tutorials, we will write our shaders in High-Level Shading Language (HLSL). Recall that our vertex data has a 3D position element, and the vertex shader will do no processing on the input at all. The resulting vertex shader looks like the following:

```hlsl

float4 VS( float4 Pos : POSITION ) : SV_POSITION
{
	return Pos;
}

```

This vertex shader looks a lot like a C function. HLSL uses C-like syntax to make learning easier for C/C++ programmers. We can see that this vertex shader, named VS, takes a parameter of float4 type and returns a float4 value. In HLSL, a float4 is a 4-component vector where each component is a floating-point number. The colons define the semantics of the parameter as well as the return value. As mentioned above, the semantics in HLSL describe the nature of the data. In our shader above, we choose POSITION as the semantics of the Pos input parameter because this parameter will contain the vertex position. The return value's semantics, SV_POSITION, is a pre-defined semantics with special meaning. This semantics tells the graphics pipeline that the data associated with the semantics defines the clip-space position. This position is needed by the GPU in order to drawn pixels on the screen. (We will discuss clip-space in the next tutorial.) In our shader, we take the input position data and output the exact same data back to the pipeline.

## Pixel Shaders

Modern computer monitors are commonly raster display, which means the screen is actually a two-dimensional grid of small dots called pixels. Each pixel contains a color independent of other pixels. When we render a triangle on the screen, we don't really render a triangle as one entity. Rather, we light up the group of pixels that are covered by the triangle's area. Figure 2 shows an illustration of this.

![[83909e09315bc3a0d0ce3fe2f7747373_MD5.jpeg]]

**Figure 2. Left: What we would like to draw. Right: What is actually on the screen.**

The process of converting a triangle defined by three vertices to a bunch of pixels covered by the triangle is called rasterization. The GPU first determines what pixels are covered by the triangle being rendered. Then it invokes the active pixel shader for each of these pixels. A pixel shader's primary purpose is to compute the color that each pixel should have. The shader takes certain input about the pixel being colored, computes the pixel's color, then outputs that color back to the pipeline. The input that it takes comes from the active geometry shader, or, if a geometry shader is not present, such as the case in this tutorial, the input comes directly from the vertex shader.

The vertex shader we created above outputs a float4 with the semantics SV_POSITION. This will be the input of our pixel shader. Since pixel shaders output color values, the output of our pixel shader will be a float4. We give the output the semantics SV_TARGET to signify outputting to the render target format. The pixel shader looks like the following:

```hlsl

float4 PS( float4 Pos : SV_POSITION ) : SV_Target
{
	return float4( 1.0f, 1.0f, 0.0f, 1.0f );    // Yellow, with Alpha = 1
}

```

## Creating the Shaders

In the application code, we will need to create a vertex shader and a pixel shader object. These objects represent our shaders, and are created by calling **D3DX11CompileFromFile()**. The code is demonstrated below:

  
```cpp

// Create the vertex shader
if( FAILED( D3DX11CompileFromFile( "Tutorial03.fx", NULL, NULL, "VS", "vs_4_0", D3DCOMPILE_ENABLE_STRICTNESS, NULL, NULL, &pVSBlob, &pErrorBlob, NULL ) ) )
	return FALSE;

// Create the pixel shader
if( FAILED( D3DX11CompileFromFile( "Tutorial03.fx", NULL, NULL, "PS", "ps_4_0", D3DCOMPILE_ENABLE_STRICTNESS, NULL, NULL, &pPSBlob, &pErrorBlob, NULL ) ) )
	return FALSE;

```

# Putting It Together

After walking through the graphics pipeline, we can start to understand the process of rendering the triangle we created at the beginning of Tutorial 2. Creating Direct3D applications requires two distinct steps. The first would be creating the source data in vertex data, as we've done in Tutorial 2. The second stage would be to create the shaders which would transform that data for rendering, which we showed in this tutorial.