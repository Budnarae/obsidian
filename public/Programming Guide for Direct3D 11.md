---
tags:
  - directX11
  - translation
---

# Devices

A Direct3D device allocates and destroys objects, renders primitives, and communicates with a graphics driver and the hardware.

Direct3D 장치는 객체를 할당하고 소멸시키며, 프리미티브(원시 도형, 간단한 이미지 등으로 번역될 수 있음)를 렌더하며, 그래픽스 드라이버 그리고 하드웨어와 통신한다.

In Direct3D 11, a device is separated into a device object for creating resources and a device-context object, which performs rendering.

DIrect3 11에서, 하나의 장치는 리소스를 생성하기 위한 `device` 객체와 렌더링을 위한 `device-context` 객체로 나뉜다.

This section describes Direct3D 11 device and device-context objects.

이번 단락에서는 Direct3D 11의 `device` 그리고 `device-context` 객체에 대해 서술한다.

Objects created from one device cannot be used directly with other devices.

하나의 장치에 의해 생성된 객체들은 다른 장치들에 의해 직접적으로 사용될 수 없다.

Use a shared resource to share data between multiple devices, with the constraint that a shared object can be used only by the device that created it.

공유 리소스를 사용하여 여러 장치 간에 데이터를 공유할 수 있으며, 공유 객체는 해당 객체를 만든 장치에서만 사용할 수 있다는 제약 조건이 있다.

# Indrocution to a Device in Direct3D 11

The Direct3D 11 object model separates resource creation and rendering functionality into a device and one or more contexts; this separation is designed to facilitate multithreading.

Direct3D 11의 객체 모델은 리소스 생성과 렌더링 기능을 `device`와 하나 또는 그 이상의 `contexts`로 분할한다; 이러한 분할은 멀티 스레딩을 용이하게 하기 위해 설계되었다.

## Device

A device is used to create resources and to enumerate the capabilities of a display adapter.

`device`는 리소스를 생성하고 디스플레이 어댑터의 기능을 열거하기 위해 사용된다.

In Direct3D 11, a device is represented with an [**ID3D11Device**](https://learn.microsoft.com/en-us/windows/desktop/api/D3D11/nn-d3d11-id3d11device) interface.

Direct3D 11에서, `device`는 **ID3D11Device** 인터페이스에 의해 나타내진다.

Each application must have at least one device, most applications only create one device.

각 실행프로그램은 적어도 하나의 `device`를 보유해야 하며, 대부분의 실행프로그램은 딱 하나의 `device`만 생성한다.

Create a device for one of the hardware drivers installed on your machine by calling [**D3D11CreateDevice**](https://learn.microsoft.com/en-us/windows/desktop/api/D3D11/nf-d3d11-d3d11createdevice) or [**D3D11CreateDeviceAndSwapChain**](https://learn.microsoft.com/en-us/windows/desktop/api/D3D11/nf-d3d11-d3d11createdeviceandswapchain) and specify the driver type with the [**D3D_DRIVER_TYPE**](https://learn.microsoft.com/en-us/windows/desktop/api/D3DCommon/ne-d3dcommon-d3d_driver_type) flag.

당신의 기기 위에 설치된 하드웨어 드라이브 중 하나를 위한 `device`를 생성하기 위해 **D3D11CreateDevice** 또는 **D3D11CreateDeviceandSwapChain**을 호출한다.
**D3D_DRIVER_TYPE** 플래그로 드라이버의 타입을 특정한다.

Each device can use one or more device contexts, depending on the functionality desired.

각각의 `device`는  원하는 기능에 따라 하나 혹은 그 이상의 `device contexts`를 사용할 수 있다.

## Device Context

A device context contains the circumstance or setting in which a device is used.

`device context`는 장치가 사용되는 상황 또는 설정을 포함한다.

More specifically, a device context is used to set pipeline state and generate rendering commands using the resources owned by a device.

더 자세히 말하자면, `device context`는 파이프라인의 상태를 설정하거나, 디바이스가 보유한 리소스를 사용한 렌더링 명령어를 생성하는데 사용된다.

Direct3D 11 implements two types of device contexts, one for immediate rendering and the other for deferred rendering; both contexts are represented with an [**ID3D11DeviceContext**](https://learn.microsoft.com/en-us/windows/desktop/api/D3D11/nn-d3d11-id3d11devicecontext) interface.

Direct3D 11은 두 종류의 `device context`를 가진다. 하나는 즉시 렌더링을 위한 것이고 하나는 지연 렌더링을 위한 것이다; 두 개의 ``

[](https://learn.microsoft.com/en-us/windows/win32/direct3d11/overviews-direct3d-11-devices-intro#immediate-context)

### Immediate Context

An immediate context renders directly to the driver. Each device has one and only one immediate context which can retrieve data from the GPU. An immediate context can be used to immediately render (or play back) a [command list](https://learn.microsoft.com/en-us/windows/win32/direct3d11/overviews-direct3d-11-render-multi-thread-command-list).

There are two ways to get an immediate context:

- By calling either [**D3D11CreateDevice**](https://learn.microsoft.com/en-us/windows/desktop/api/D3D11/nf-d3d11-d3d11createdevice) or [**D3D11CreateDeviceAndSwapChain**](https://learn.microsoft.com/en-us/windows/desktop/api/D3D11/nf-d3d11-d3d11createdeviceandswapchain).
- By calling [**ID3D11Device::GetImmediateContext**](https://learn.microsoft.com/en-us/windows/desktop/api/D3D11/nf-d3d11-id3d11device-getimmediatecontext).

[](https://learn.microsoft.com/en-us/windows/win32/direct3d11/overviews-direct3d-11-devices-intro#deferred-context)

### Deferred Context

A deferred context records GPU commands into a [command list](https://learn.microsoft.com/en-us/windows/win32/direct3d11/overviews-direct3d-11-render-multi-thread-command-list). A deferred context is primarily used for multithreading and is not necessary for a single-threaded application. A deferred context is generally used by a worker thread instead of the main rendering thread. When you create a deferred context, it does not inherit any state from the immediate context.

To get a deferred context, call [**ID3D11Device::CreateDeferredContext**](https://learn.microsoft.com/en-us/windows/desktop/api/D3D11/nf-d3d11-id3d11device-createdeferredcontext).

Any context -- immediate or deferred -- can be used on any thread as long as the context is only used in one thread at a time.

[](https://learn.microsoft.com/en-us/windows/win32/direct3d11/overviews-direct3d-11-devices-intro#threading-considerations)

## Threading Considerations

This table highlights the differences in the threading model in Direct3D 11 from prior versions of Direct3D.

Differences between Direct3D 11 and previous versions of Direct3D:  
All [**ID3D11Device**](https://learn.microsoft.com/en-us/windows/desktop/api/D3D11/nn-d3d11-id3d11device) interface methods are free-threaded, which means it is safe to have multiple threads call the functions at the same time.  

- All [**ID3D11DeviceChild**](https://learn.microsoft.com/en-us/windows/desktop/api/D3D11/nn-d3d11-id3d11devicechild)-derived interfaces ([**ID3D11Buffer**](https://learn.microsoft.com/en-us/windows/desktop/api/D3D11/nn-d3d11-id3d11buffer), [**ID3D11Query**](https://learn.microsoft.com/en-us/windows/desktop/api/D3D11/nn-d3d11-id3d11query), etc.) are free-threaded.
- Direct3D 11 splits resource creating and rendering into two interfaces. Map, Unmap, Begin, End, and GetData are implemented on [**ID3D11DeviceContext**](https://learn.microsoft.com/en-us/windows/desktop/api/D3D11/nn-d3d11-id3d11devicecontext) because [**ID3D11Device**](https://learn.microsoft.com/en-us/windows/desktop/api/D3D11/nn-d3d11-id3d11device) strongly defines the order of operations. [**ID3D11Resource**](https://learn.microsoft.com/en-us/windows/desktop/api/D3D11/nn-d3d11-id3d11resource) and [**ID3D11Asynchronous**](https://learn.microsoft.com/en-us/windows/desktop/api/D3D11/nn-d3d11-id3d11asynchronous) interfaces also implement methods for free-threaded operations.
- The [**ID3D11DeviceContext**](https://learn.microsoft.com/en-us/windows/desktop/api/D3D11/nn-d3d11-id3d11devicecontext) methods (except for those that exist on [**ID3D11DeviceChild**](https://learn.microsoft.com/en-us/windows/desktop/api/D3D11/nn-d3d11-id3d11devicechild)) are not free-threaded, that is, they require single threading. Only one thread may safely be calling any of its methods (Draw, Copy, Map, etc.) at a time.
- In general, free-threading minimizes the number of synchronization primitives used as well as their duration. However, an application that uses synchronization held for a long time can directly impact how much concurrency an application can expect to achieve.

ID3D10Device interface methods are not designed to be free-threaded. ID3D10Device implements all create and rendering functionality (as does ID3D9Device in Direct3D 9. Map and Unmap are implemented on ID3D10Resource-derived interfaces, Begin, End, and GetData are implemented on ID3D10Asynchronous-derived interfaces.
