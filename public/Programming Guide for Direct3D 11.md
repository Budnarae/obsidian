---
tags:
  - directX11
  - translation
---

# Devices

A Direct3D device allocates and destroys objects, renders primitives, and communicates with a graphics driver and the hardware.

Direct3D 디바이스는 객체를 할당하고 소멸시키며, 

In Direct3D 11, a device is separated into a device object for creating resources and a device-context object, which performs rendering. This section describes Direct3D 11 device and device-context objects.

Objects created from one device cannot be used directly with other devices. Use a shared resource to share data between multiple devices, with the constraint that a shared object can be used only by the device that created it.
