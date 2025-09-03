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


