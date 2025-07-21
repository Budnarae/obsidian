---
tags:
  - directX11
  - translation
---

# Devices

A Direct3D device allocates and destroys objects, renders primitives, and communicates with a graphics driver and the hardware.

Direct3D 장치는 객체를 할당하고 소멸시키며, 프리미티브(원시 도형, 간단한 이미지 등으로 번역될 수 있음)를 렌더하며, 그래픽스 드라이버 그리고 하드웨어와 통신한다.

In Direct3D 11, a device is separated into a device object for creating resources and a device-context object, which performs rendering.

DIrect3 11에서, 하나의 장치는 리소스를 생성하기 위한 `device` 객체와 `device-context`

This section describes Direct3D 11 device and device-context objects.

Objects created from one device cannot be used directly with other devices. Use a shared resource to share data between multiple devices, with the constraint that a shared object can be used only by the device that created it.
