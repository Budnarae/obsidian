---
tags:
  - directX11
  - translation
---

# ID3D11


# IDXGI

## IDXGISwapChain

IDXGISwapChain 인터페이스는 렌더링된 데이터를 출력에 표시하기 전에 저장하기 위해 하나 이상의 그래픽 표면(버퍼 등으로 의역하는 것이 자연스러울 듯)을 구현합니다.

### Inheritance

IDXGISwapChain 인터페이스는 IDXGIDeviceSubObject에서 상속합니다. IDXGISwapChain 또한 부모 객체의 멤버를 갖는다:

### Method

#### IDXGISwapChain::GetBuffer

스왑 체인의 백 퍼버들 중 하나에 접근한다.

##### Syntax

```cpp

HRESULT GetBuffer(
        UINT   Buffer,
  [in]  REFIID riid,
  [out] void   **ppSurface
);

```

##### Parameters

`Buffer`

타입 : UINT

0이 기본인 버퍼 인덱스입니다.

스왑 체인의 스왑 효과가 DXGI_SWAP_EFFECT_DISCARD인 경우 이 메서드는 첫 번째 버퍼에만 액세스할 수 있으므로 이 경우 인덱스를 0으로 설정합니다.

스왑 체인의 스왑 효과가 DXGI_SWAP_EFFECT_SEQUENTIAL 또는 DXGI_SWAP_EFFECT_FLIP_SEQUENTIAL인 경우, 스왑 체인의 0 인덱스 버퍼만 읽고 쓸 수 있습니다. 인덱스가 0보다 큰 스왑 체인의 버퍼는 읽기만 가능하므로, 이러한 버퍼에 대해 IDXGIResource::GetUsage 메서드를 호출하면 DXGI_USAGE_READ_ONLY 플래그가 설정되어 있습니다.

[in] riid

유형: REFIID

버퍼를 조작하는 데 사용되는 인터페이스 유형입니다.

[out] ppSurface

유형: void**

백 버퍼 인터페이스에 대한 포인터입니다.

##### Return value

타입: HRESULT

DXGI_ERROR 중 하나를 반환합니다.