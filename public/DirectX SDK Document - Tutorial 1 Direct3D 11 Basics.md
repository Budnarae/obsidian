---
tags:
  - directX11
  - translation
---
---

# Summary

In this first tutorial, we will go through the elements necessary to create a minimal Direct3D 11 application.

이 튜토리얼에서 우리는 최소한의 Direct3D 11 응용프로그램을 만들기 위해 필수적인 요소를 살펴볼 것이다.

Every Direct3D 11 application must have these elements to function properly.

모든 Direct3D 11 응용프로그램은 제대로 기능하기 위해서 이 요소들이 필요하다.

The elements include setting up a window and a device object, and then displaying a color on the window.

요소는 창이나 장치 객체를 설정하거나, 창에 색깔을 표시하는 것을 포함한다.

==Source==

`(SDK root)\Samples\C++\Direct3D11\Tutorials\Tutorial01`

## Setting up The Direct3D 11 Device

The first steps of creating the window and message loop are identical in Direct3D 9, Direct3D 10, and DIrectD3 11.

창과 메시지 루프를 만드는 첫번째 단계는 Direct3D 9, 10, 11에서 모두 동일하다.

See DIrect3D 10 Tutorial 00: Win32 Basics for an introduction to this process.

이 단계에 대해 소개한 [[DirectX SDK Document - Tutorial 0 Win32 Basics]]을 보도록 하자.

Now that we have a window that is displaying, we can continue to set up a Direct3D 11 device.

이제 우리는 창을 얻었으므로, 계속해서 Direct3D 11 장치를 설정해보자.

SetUp is necessary if we are going to render any 3D scene.

3차원 장면을 렌더링하는데 설정은 필수적이다.

The first thing to do is to create three objects: a device, an immediate context, and a swap chain.

첫번째로 해야할 일은 3개의 객체를 만드는 것이다: 장치, 즉시 컨텍스트, 스왑 체인.

THe immediate context is a new object in Direct3D 11.

즉시 컨텍스트는 Direct3D 11의 새로운 객체이다.

---

In Direct3D 10, the device object was used to perform both rendering and resource creation.

DIrect3D 10에서, 장치 객체는 렌더링과 리소스 생성을 둘 다 수행했다.

In Direct3D 11, the immeidate context is used by the application to perform rendering onto a buffer, and the device contains methods to create resources.

Direct3D 11에서 즉시 컨텍스트는 응용프로그램이 버퍼에 렌더링할 때 사용하고, 장치는 리소스를 생성하는 메서드를 가진다.

---

The swap chain is responsible for taking the buffer to which the device renders, and displaying the content, on the actual monitor screen.

스왑 체인은 장치가 렌더링하는 버퍼를 저장하며, 버퍼의 내용을 실제 모니터 화면에 내용을 보여주는 역할을 한다.

The swap chain contians two or more buffers, mainly the front and the back.

스왑 체인은 두 개 이상의 버퍼를 포함하는데, 주로 프론트 버퍼와 백 버퍼이다.

These are textures to which the device renders in order to display on the monitor.

이들은 장치가 모니터에 표시하기 위해 렌더링할 텍스처들이다.

The front buffer is what is being presented currently to the user.

프론트 버퍼는 현재 사용자에게 보여지고 있는 버퍼이다.

This buffer is read-only and cannot be modified.

이 버퍼는 읽기 전용이며 수정이 불가능하다.

The back buffer is the render target to which the device will draw.

백 버퍼는 장치가 그리기를 수행할 렌더 타켓이다.

Once it finishes the drawing operation, the swap chain will present the backbuffer by swapping the two buffers.

한번 그리기를 수행하면, 장치는 백 버퍼를 보존하기 위해 두 개의 버퍼를 뒤바꾼다.

The back buffer becomes the front buffer, and vice versa.

백 버퍼는 프론트 버퍼가 되고, 프론트 버퍼는 백 버퍼가 된다.

---

To create the swap chain, we fill out a DXGI_SWAPCHAIN_DESC structure that describes the swap chain we are about to create.

스왑 체인을 만들기 위해, 우리가 만들 스왑 체인을 나타내는 DXGI_SWAPCHAIN_DESC 구조체를 작성한다.

A few fields are worth mentioning.

몇몇 필드는 언급할 가치가 있다.

**BackBufferUsage** is a flag that tells the application how the back buffer will be used.

**BackBufferUsage**는 응용프로그램에게 백버퍼가 어떻게 사용될지 알려주는 플래그이다.

In this case, we want to render to the back buffer, so we'll set **BackBufferUsage** to DXGI_USAGE_RENDER_TARGET_OUTPUT.

이 튜토리얼에서 우리는 백 버퍼에 렌더링하기를 원하므로 **BackBufferUsage**를 DXGI_USAGE_RENDER_TARGET_OUTPUT로 설정할 것이다.

The **OutputWindow** field represents the window that the swap chain will use to present images on the screen.

**OutputWindow** 필드는 스왑 체인이 화면에 이미지를 표시하기 위한 창을 나타낸다.


SampleDesc is used to enable multi-sampling.

SampleDesc는 멀티 샘플링을 가능하게 하기 위해 사용된다.

Since this tutorial does not use multi-sampling, SampleDesc's Count is set to 1 and Quality to 0 to have multi-sampling disabled.

이 튜토리얼은 멀티샘플링을 사용하지 않으므로, SampleDesc의 Count는 1로, Quality는 0으로 설정해서 멀티샘플링을 비활성화한다.

Once the description has been filled out, we can call the D3D11CreateDeviceAndSwapChain function to create both the device and the swap chain for us.

작성이 끝나면, 우리는 D3D11CreateDeviceAndSwapChain 함수를 호출하여 장치와 스왑 체인을
생성할 수 있다.

```cpp

DXGI_SWAP_CHAIN_DESC sd;
ZeroMemory( &sd, sizeof(sd) );
sd.BufferCount = 1;
sd.BufferDesc.Width = 640;
sd.BufferDesc.Height = 480;
sd.BufferDesc.Format = DXGI_FORMAT_R8G8B8A8_UNORM;
sd.BufferDesc.RefreshRate.Numerator = 60;
sd.BufferDesc.RefreshRate.Denominator = 1;
sd.BufferUsage = DXGI_USAGE_RENDER_TARGET_OUTPUT;
sd.OutputWindow = g_hWnd;
sd.SampleDesc.Count = 1;
sd.SampleDesc.Quality = 0;
sd.Windowed = TRUE;

if( FAILED( D3D11CreateDeviceAndSwapChain( NULL, D3D_DRIVER_TYPE_HARDWARE, NULL, 0, featureLevels, numFeatureLevels, D3D11_SDK_VERSION, &sd, &g_pSwapChain, &g_pd3dDevice, NULL, &g_pImmediateContext ) ) )
{
	return FALSE;
}

```

The next thing we need to do is to create a render view.

다음으로 할 일은 렌더 뷰를 만드는 것이다.

A render target view is a type of resource view in Direct3D 11.

Direct3D 11에서 렌더 타겟 뷰는 리소스 뷰의 한 종류이다.

A resource view allows a resource to be bound to the graphics pipeline at a specific stage.

리소스 뷰는 리소스를 그래픽 파이프라인의 특정 단계에 바인딩할 수 있도록 해준다.

Think of resource views as typecast in C.

리소스 뷰를 C의 타입캐스트로 생각해보자.

A chunk of raw memory in C can be cast to any data type.

C에서 원시 메모리 덩어리는 어떠한 타입으로든 캐스트될 수 있다.

We can cast that chunk of memory to an array of integers, an array of floats, a structure, an array of structures, and so on.

우리는 메모리 덩어리를 정수 배열, 실수 배열, 구조체, 구조체 배열 등등으로 캐스트할 수 있다.

The raw memory itself is not very useful to us if we don't know its type.

원시 메모리는 그것의 타입을 알 수 없다면 우리에게 그닥 쓸모있지 않다.

Direct3D 11 resource views act in a similar way.

Direct3D 11 리소스 뷰는 비슷한 원리로 동작한다.

For instance, a 2D texture, analogous to the raw memory chunk, is the raw underlying resource.

예를 들어, 2차원 텍스처는, 원시 메모리 덩어리와 비슷하게, 원시 저수준 리소스이다.

Once we have that resource we can create different resource views to bind that texture to different stages in the graphics pipeline with different formats: as a render target to which to render, as a depth stencil buffer that will receive depth information, or as a texture resource.

우리는 리소스를 사용하여 그래픽스 파이프라인에 자

Where C typecasts allow a memory chunk to be used in a different manner, so do Direct3D 11 resource views.

---

We need to create a render target view because we would like to bind the back buffer of our swap chain as a render target. This enables Direct3D 11 to render onto it. We first call **GetBuffer()** to get the back buffer object. Optionally, we can fill in a D3D11_RENDERTARGETVIEW_DESC structure that describes the render target view to be created. This description is normally the second parameter to **CreateRenderTargetView**. However, for these tutorials, the default render target view will suffice. The default render target view can be obtained by passing NULL as the second parameter. Once we have created the render target view, we can call **OMSetRenderTargets()** on the immediate context to bind it to the pipeline. This ensures the output that the pipeline renders gets written to the back buffer. The code to create and set the render target view is as follows:
