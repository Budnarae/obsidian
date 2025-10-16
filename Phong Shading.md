---
tags:
  - graphics
  - translation
---

_Let There Be Light_
_빛이 있으라_

---

### ✅ 영어 원문

Phong shading (or normal‑vector interpolation shading) is an interpolation technique for surface shading, invented by computer graphics pioneer Bui Tuong Phong. Phong shading interpolates surface normals across rasterized polygons and computes pixel colors based on the interpolated normals and a reflection model. Phong shading may also refer to the specific combination of Phong interpolation and the Phong reflection model. ([위키백과](https://en.wikipedia.org/wiki/Phong_shading?utm_source=chatgpt.com "Phong shading"))

#### History

Phong shading and the Phong reflection model were developed at the University of Utah by Bui Tuong Phong, who published them in his 1973 Ph.D. dissertation and a 1975 paper. ([위키백과](https://en.wikipedia.org/wiki/Phong_shading?utm_source=chatgpt.com "Phong shading")) Phong's methods were considered radical at the time of their introduction, but have since become the de facto baseline shading method for many rendering applications. Phong's methods have proven popular due to their generally efficient use of computation time per rendered pixel. ([위키백과](https://en.wikipedia.org/wiki/Phong_shading?utm_source=chatgpt.com "Phong shading"))

#### Phong interpolation

Phong shading improves upon Gouraud shading and provides a better approximation of the shading of a smooth surface. Phong shading assumes a smoothly varying surface normal vector. The Phong interpolation method works better than Gouraud shading when applied to a reflection model with small specular highlights such as the Phong reflection model. ([위키백과](https://en.wikipedia.org/wiki/Phong_shading?utm_source=chatgpt.com "Phong shading"))

The most serious problem with Gouraud shading occurs when specular highlights are found in the middle of a large polygon. Since these specular highlights are absent from the polygon's vertices and Gouraud shading interpolates based on the vertex colors, the specular highlight will be missing from the polygon's interior. This problem is fixed by Phong shading. ([위키백과](https://en.wikipedia.org/wiki/Phong_shading?utm_source=chatgpt.com "Phong shading"))

Unlike Gouraud shading, which interpolates colors across polygons, in Phong shading, a normal vector is linearly interpolated across the surface of the polygon from the polygon's vertex normals. The surface normal is interpolated and normalized at each pixel and then used in a reflection model, e.g. the Phong reflection model, to obtain the final pixel color. Phong shading is more computationally expensive than Gouraud shading since the reflection model must be computed at each pixel instead of at each vertex. ([위키백과](https://en.wikipedia.org/wiki/Phong_shading?utm_source=chatgpt.com "Phong shading"))

In modern graphics hardware, variants of this algorithm are implemented using pixel or fragment shaders. ([위키백과](https://en.wikipedia.org/wiki/Phong_shading?utm_source=chatgpt.com "Phong shading"))

#### Phong reflection model

Phong shading may also refer to the specific combination of Phong interpolation and the Phong reflection model, which is an empirical model of local illumination. It describes the way a surface reflects light as a combination of the diffuse reflection of rough surfaces with the specular reflection of shiny surfaces. It is based on Bui Tuong Phong's informal observation that shiny surfaces have small intense specular highlights, while dull surfaces have large highlights that fall off more gradually. The reflection model also includes an ambient term to account for the small amount of light that is scattered about the entire scene. ([위키백과](https://en.wikipedia.org/wiki/Phong_shading?utm_source=chatgpt.com "Phong shading"))

---

### 🇰🇷 한국어 번역

Phong 셰이딩(또는 법선 벡터 보간 셰이딩)은 컴퓨터 그래픽스 개척자 **부이 투옹 퐁(Bui Tuong Phong)**이 고안한 표면 셰이딩을 위한 보간 기법입니다. Phong 셰이딩은 래스터화된 다각형 내부를 가로질러 표면 법선(surface normal)을 보간(interpolate)하고, 보간된 법선을 사용해 반사 모델(reflection model)에 기반해 픽셀 색상을 계산합니다. 또한 Phong 셰이딩은 **Phong 보간 방식 + Phong 반사 모델**의 조합을 가리키기도 합니다. ([위키백과](https://en.wikipedia.org/wiki/Phong_shading?utm_source=chatgpt.com "Phong shading"))

#### 역사

Phong 셰이딩과 Phong 반사 모델은 유타 대학교(University of Utah)에서 부이 투옹 퐁이 개발하였고, 그는 1973년 박사 논문과 1975년 논문에서 이를 발표했습니다. ([위키백과](https://en.wikipedia.org/wiki/Phong_shading?utm_source=chatgpt.com "Phong shading")) 당시에는 혁신적인 접근으로 평가되었지만, 이후 많은 렌더링 응용에서 사실상 표준 셰이딩 방식이 되었습니다. 픽셀당 계산 시간 대비 효율적으로 작동한다는 장점 덕분에 널리 채택되었습니다. ([위키백과](https://en.wikipedia.org/wiki/Phong_shading?utm_source=chatgpt.com "Phong shading"))

#### Phong 보간 방식

Phong 셰이딩은 Gouraud 셰이딩보다 개선된 방식으로, 부드러운 표면 셰이딩을 더 정확하게 근사할 수 있어요. Phong 셰이딩은 표면 법선이 매끄럽게 변화한다고 가정합니다. 특히 **작은 반사 하이라이트(specular highlight)** 가 존재하는 반사 모델에 대해선, Phong 보간 방식이 Gouraud 보다 더 우수하게 동작합니다. ([위키백과](https://en.wikipedia.org/wiki/Phong_shading?utm_source=chatgpt.com "Phong shading"))

Gouraud 셰이딩의 가장 큰 문제는, 반사 하이라이트가 큰 폴리곤 내부 한가운데 있을 때입니다. 그 하이라이트가 정점에 없으면, Gouraud는 정점 색상을 보간하므로 내부 픽셀에 하이라이트가 보이지 않을 수 있어요. Phong 셰이딩은 이 문제를 해결합니다. ([위키백과](https://en.wikipedia.org/wiki/Phong_shading?utm_source=chatgpt.com "Phong shading"))

Gouraud 셰이딩은 색상(color)을 보간하지만, Phong 셰이딩은 다각형의 정점 법선(vertex normals)들로부터 법선을 **선형 보간**합니다. 그런 다음 각 픽셀마다 보간된 법선을 정규화(normalize)하고, 이 법선을 기반으로 반사 모델(예: Phong 반사 모델)을 적용해 최종 픽셀 색상을 계산합니다. 이 때문에 Phong 셰이딩은 Gouraud 셰이딩보다 계산 비용이 더 큽니다 — 조명 계산을 매 픽셀마다 해야 하기 때문이죠. ([위키백과](https://en.wikipedia.org/wiki/Phong_shading?utm_source=chatgpt.com "Phong shading"))

현대 그래픽 하드웨어에서는 이 알고리즘의 변형들이 픽셀 셰이더(fragment shader) 또는 프래그먼트 수준 셰이더로 구현됩니다. ([위키백과](https://en.wikipedia.org/wiki/Phong_shading?utm_source=chatgpt.com "Phong shading"))

#### Phong 반사 모델

Phong 셰이딩은 Phong 보간 방식과 Phong 반사 모델의 조합을 의미하기도 해요. Phong 반사 모델은 **국소 조명(local illumination)** 모델로, 표면이 빛을 반사하는 방식을 경험적으로 설명합니다. 이 모델은 거친 표면의 확산 반사(diffuse reflection)와 광택 있는 표면의 정반사(specular reflection)를 합친 형태입니다. 퐁은, 반짝이는(shiny) 표면은 작고 강한 하이라이트를 가진 반면, 덜 반짝이는 표면은 더 넓고 점차 사라지는 하이라이트를 갖는다는 관찰에 기반을 두었어요. 또한 이 반사 모델은 **ambient(환경광)** 항을 포함하여, 장면 전체에 퍼지는 약한 산란광을 보정해 줍니다. ([위키백과](https://en.wikipedia.org/wiki/Phong_shading?utm_source=chatgpt.com "Phong shading"))
