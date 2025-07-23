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
