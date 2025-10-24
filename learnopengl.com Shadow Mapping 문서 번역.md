---
tags:
  - graphics
  - translation
---

_빛이 있으면, 그림자도 있다_

---

## 섀도우 매핑 (Shadow Mapping)

그림자는 가려짐(occlusion)으로 인한 **빛의 부재**의 결과이다. 광원의 광선이 다른 물체에 가려져서 어떤 물체에 닿지 않을 때, 그 물체는 그림자 속에 있게 된다. 그림자는 빛이 비치는 장면에 많은 사실감을 더하고, 시청자가 물체들 사이의 공간적 관계를 더 쉽게 관찰할 수 있도록 한다. 그림자는 우리 장면과 물체에 더 큰 깊이감을 제공한다. 예를 들어, 그림자가 있는 장면과 없는 장면의 다음 이미지를 살펴보라:

그림자가 있으면 물체들이 서로 어떻게 관련되어 있는지 훨씬 더 명확해진다는 것을 알 수 있다. 예를 들어, 큐브 중 하나가 다른 큐브들 위에 떠 있다는 사실은 그림자가 있을 때만 실제로 눈에 띈다.

하지만 그림자를 구현하는 것은 다소 까다로운데, 특히 현재의 실시간(래스터화된 그래픽스) 연구에서 **완벽한 그림자 알고리즘**이 아직 개발되지 않았기 때문이다. 몇 가지 좋은 그림자 근사 기법이 있지만, 그것들은 모두 우리가 고려해야 할 작은 단점과 문제점들을 가지고 있다.

대부분의 비디오 게임에서 사용되며 괜찮은 결과를 제공하고 구현하기 비교적 쉬운 한 가지 기법은 **섀도우 매핑(shadow mapping)**이다. 섀도우 매핑은 이해하기에 그리 어렵지 않고, 성능 비용이 많이 들지 않으며, 더 진보된 알고리즘(예: 전방향 섀도우 맵 및 캐스케이드 섀도우 맵)으로 상당히 쉽게 확장된다.

---

## 섀도우 매핑

섀도우 매핑의 아이디어는 매우 간단하다: 우리는 **광원의 시점**에서 장면을 렌더링하고, 광원의 관점에서 보이는 모든 것은 빛을 받고, 볼 수 없는 모든 것은 그림자 속에 있어야 한다. 바닥 부분이 광원과 그 사이에 큰 상자가 있다고 상상해 보라. 광원이 그 방향을 볼 때 이 상자는 보지만 바닥 부분은 보지 못할 것이므로, 그 특정 바닥 부분은 그림자 속에 있어야 한다.

여기서 모든 파란색 선은 광원이 볼 수 있는 프래그먼트들을 나타낸다. 가려진 프래그먼트들은 검은색 선으로 표시된다. 이것들은 그림자진 것으로 렌더링된다. 광원에서 가장 오른쪽 상자의 프래그먼트로 선이나 광선(ray)을 그린다면, 광선이 가장 오른쪽 컨테이너에 닿기 전에 먼저 떠 있는 컨테이너에 닿는 것을 볼 수 있다. 결과적으로, 떠 있는 컨테이너의 프래그먼트는 빛을 받고, 가장 오른쪽 컨테이너의 프래그먼트는 빛을 받지 못하므로 그림자 속에 있게 된다.

우리는 광선이 물체에 처음 부딪힌 지점을 찾아 이 가장 가까운 지점을 이 광선 상의 다른 지점들과 비교하고자 한다. 그런 다음 테스트 지점의 광선 위치가 가장 가까운 지점보다 광선을 따라 더 멀리 있는지 확인하는 기본 테스트를 수행하고, 그렇다면 테스트 지점은 그림자 속에 있어야 한다. 그러한 광원에서 나오는 수천 개의 광선을 반복하는 것은 극도로 비효율적인 접근 방식이며 실시간 렌더링에는 적합하지 않다. 우리는 비슷하지만 광선을 캐스팅하지 않는 작업을 할 수 있다. 대신, 우리가 매우 잘 알고 있는 것, 즉 **깊이 버퍼(depth buffer)**를 사용한다.

깊이 테스트 챕터에서 기억하겠지만, 깊이 버퍼의 값은 카메라의 시점에서 $[0,1]$로 클램프된 프래그먼트의 깊이에 해당한다. 장면을 광원의 관점에서 렌더링하고 그 결과 깊이 값들을 텍스처에 저장한다면 어떨까? 이런 식으로, 우리는 광원의 관점에서 보이는 가장 가까운 깊이 값들을 샘플링할 수 있다. 결국, 깊이 값들은 광원의 관점에서 보이는 첫 번째 프래그먼트를 보여준다. 우리는 이 모든 깊이 값들을 **깊이 맵(depth map)** 또는 **섀도우 맵(shadow map)**이라고 부르는 텍스처에 저장한다.

왼쪽 이미지는 방향성 광원(모든 광선이 평행함)이 큐브 아래 표면에 그림자를 드리우는 것을 보여준다. 깊이 맵에 저장된 깊이 값들을 사용하여 가장 가까운 지점을 찾고, 그것을 사용하여 프래그먼트가 그림자 속에 있는지 여부를 결정한다. 우리는 그 광원 고유의 **뷰(view)** 및 **투영(projection)** 행렬을 사용하여 장면을 (광원의 관점에서) 렌더링함으로써 깊이 맵을 생성한다. 이 투영 및 뷰 행렬은 함께 모든 3D 위치를 광원의 (보이는) 좌표 공간으로 변환하는 변환 $T$를 형성한다.

방향성 광원은 무한히 멀리 떨어져 있는 것으로 모델링되므로 위치가 없다. 그러나 섀도우 매핑을 위해 우리는 광원의 관점에서 장면을 렌더링해야 하므로, 광원 방향을 따라 어딘가에 있는 위치에서 장면을 렌더링해야 한다.

오른쪽 이미지에서 우리는 동일한 방향성 광원과 뷰어를 본다. 우리는 점 $\bar{P}$에서 프래그먼트를 렌더링하며, 이 점이 그림자 속에 있는지 여부를 결정해야 한다. 이를 위해, 우리는 먼저 $T$를 사용하여 점 $\bar{P}$를 광원의 좌표 공간으로 변환한다. 이제 점 $\bar{P}$는 광원의 관점에서 보이기 때문에, 그것의 $z$ 좌표는 깊이에 해당하며 이 예에서는 $0.9$이다. 점 $\bar{P}$를 사용하여 깊이/섀도우 맵에 인덱싱함으로써 광원의 관점에서 가장 가까운 가시 깊이를 얻을 수도 있는데, 이는 샘플링된 깊이가 $0.4$인 점 $\bar{C}$에 있다. 깊이 맵에 인덱싱한 결과가 점 $\bar{P}$에서의 깊이보다 작은 깊이를 반환하므로, 우리는 점 $\bar{P}$가 가려져(occluded) 있으므로 그림자 속에 있다고 결론지을 수 있다.

따라서 섀도우 매핑은 두 번의 패스(pass)로 구성된다: 첫 번째로 깊이 맵을 렌더링하고, 두 번째 패스에서는 장면을 정상적으로 렌더링하며 생성된 깊이 맵을 사용하여 프래그먼트가 그림자 속에 있는지 여부를 계산한다. 다소 복잡하게 들릴 수 있지만, 이 기법을 단계별로 살펴보면 이해가 되기 시작할 것이다.

---

## 깊이 맵 (The depth map)

첫 번째 패스는 우리가 깊이 맵을 생성하도록 요구한다. 깊이 맵은 그림자 테스트에 사용할 광원의 관점에서 렌더링된 깊이 텍스처이다. 장면의 렌더링된 결과를 텍스처에 저장해야 하므로, 우리는 다시 **프레임버퍼(framebuffers)**가 필요할 것이다.

먼저 깊이 맵 렌더링을 위한 프레임버퍼 객체를 생성할 것이다:

C++

```
unsigned int depthMapFBO;
glGenFramebuffers(1, &depthMapFBO);
```

다음으로 프레임버퍼의 깊이 버퍼로 사용할 2D 텍스처를 생성한다:

C++

```
const unsigned int SHADOW_WIDTH = 1024, SHADOW_HEIGHT = 1024;
unsigned int depthMap;
glGenTextures(1, &depthMap);
glBindTexture(GL_TEXTURE_2D, depthMap);
glTexImage2D(GL_TEXTURE_2D, 0, GL_DEPTH_COMPONENT, SHADOW_WIDTH, SHADOW_HEIGHT, 0, GL_DEPTH_COMPONENT, GL_FLOAT, NULL);
glTexParameteri(GL_TEXTURE_2D, GL_TEXTURE_MIN_FILTER, GL_NEAREST);
glTexParameteri(GL_TEXTURE_2D, GL_TEXTURE_MAG_FILTER, GL_NEAREST);
glTexParameteri(GL_TEXTURE_2D, GL_TEXTURE_WRAP_S, GL_REPEAT);
glTexParameteri(GL_TEXTURE_2D, GL_TEXTURE_WRAP_T, GL_REPEAT);
```

깊이 맵 생성은 그리 복잡해 보이지 않을 것이다. 우리는 깊이 값에만 관심이 있으므로 텍스처의 형식을 `GL_DEPTH_COMPONENT`로 지정한다. 또한 텍스처에 `1024`의 너비와 높이를 부여한다. 이것이 깊이 맵의 해상도이다.

생성된 깊이 텍스처로, 우리는 그것을 프레임버퍼의 깊이 버퍼로 첨부할 수 있다:

C++

```
glBindFramebuffer(GL_FRAMEBUFFER, depthMapFBO);
glFramebufferTexture2D(GL_FRAMEBUFFER, GL_DEPTH_ATTACHMENT, GL_TEXTURE_2D, depthMap, 0);
glDrawBuffer(GL_NONE);
glReadBuffer(GL_NONE);
glBindFramebuffer(GL_FRAMEBUFFER, 0);
```

장면을 광원의 관점에서 렌더링할 때 우리는 깊이 정보만 필요하므로 색상 버퍼가 필요 없다. 하지만 프레임버퍼 객체는 색상 버퍼 없이는 완전하지 않으므로, 우리는 어떤 색상 데이터도 렌더링하지 않을 것임을 OpenGL에 명시적으로 알려야 한다. 우리는 `glDrawBuffer`와 `glReadbuffer`를 사용하여 읽기 및 그리기 버퍼를 모두 `GL_NONE`으로 설정함으로써 이를 수행한다.

깊이 값을 텍스처로 렌더링하는 올바르게 구성된 프레임버퍼를 사용하여 우리는 첫 번째 패스인 깊이 맵 생성 작업을 시작할 수 있다. 두 번째 패스와 결합하면, 전체 렌더링 단계는 다음과 같이 보일 것이다:

C++

```
// 1. first render to depth map
glViewport(0, 0, SHADOW_WIDTH, SHADOW_HEIGHT);
glBindFramebuffer(GL_FRAMEBUFFER, depthMapFBO);
glClear(GL_DEPTH_BUFFER_BIT);
ConfigureShaderAndMatrices();
RenderScene();
glBindFramebuffer(GL_FRAMEBUFFER, 0);
// 2. then render scene as normal with shadow mapping (using depth map)
glViewport(0, 0, SCR_WIDTH, SCR_HEIGHT);
glClear(GL_COLOR_BUFFER_BIT | GL_DEPTH_BUFFER_BIT);
ConfigureShaderAndMatrices();
glBindTexture(GL_TEXTURE_2D, depthMap);
RenderScene();
```

이 코드는 일부 세부 사항을 생략했지만, 섀도우 매핑의 일반적인 아이디어를 제공할 것이다. 여기서 주목해야 할 중요한 점은 `glViewport` 호출이다. 섀도우 맵은 우리가 원래 장면을 렌더링하는 해상도(일반적으로 창 해상도)와 다른 해상도를 가질 때가 많으므로, 우리는 섀도우 맵의 크기에 맞추기 위해 뷰포트 매개변수를 변경해야 한다. 뷰포트 매개변수를 업데이트하는 것을 잊으면, 결과 깊이 맵은 불완전하거나 너무 작을 것이다.

---

## 광원 공간 변환 (Light space transform)

이전 코드 조각에서 알려지지 않은 부분은 `ConfigureShaderAndMatrices` 함수이다. 두 번째 패스에서는 이것이 평소의 작업이다: 적절한 투영 및 뷰 행렬이 설정되었는지 확인하고, 객체별 관련 모델 행렬을 설정한다. 그러나 첫 번째 패스에서는 장면을 광원의 시점에서 렌더링하기 위해 다른 투영 및 뷰 행렬을 사용해야 한다.

우리는 **방향성 광원(directional light source)**을 모델링하고 있기 때문에, 그 모든 광선은 평행하다. 이러한 이유로, 우리는 원근 변형(perspective deform)이 없는 광원에 대한 **직교 투영 행렬(orthographic projection matrix)**을 사용할 것이다:

C++

```
float near_plane = 1.0f, far_plane = 7.5f;
glm::mat4 lightProjection = glm::ortho(-10.0f, 10.0f, -10.0f, 10.0f, near_plane, far_plane);
```

여기에 이 챕터의 데모 장면에 사용된 직교 투영 행렬의 예가 있다. 투영 행렬은 보이는 것의 범위(예: 클리핑되지 않는 것)를 간접적으로 결정하기 때문에, 투영 절두체(projection frustum)의 크기가 깊이 맵에 포함되기를 원하는 객체들을 올바르게 포함하는지 확인해야 한다. 객체나 프래그먼트가 깊이 맵에 없으면 그림자를 생성하지 않을 것이다.

각 객체를 광원의 시점에서 보이도록 변환하는 뷰 행렬을 생성하기 위해, 우리는 악명 높은 `glm::lookAt` 함수를 사용할 것이다. 이번에는 광원의 위치가 장면의 중심을 바라보도록 한다.

C++

```
glm::mat4 lightView = glm::lookAt(glm::vec3(-2.0f, 4.0f, -1.0f), 
                                  glm::vec3( 0.0f, 0.0f, 0.0f), 
                                  glm::vec3( 0.0f, 1.0f, 0.0f));
```

이 두 가지를 결합하면 각 월드 공간 벡터를 광원에서 보이는 공간으로 변환하는 **광원 공간 변환 행렬(light space transformation matrix)**이 제공된다. 이는 깊이 맵을 렌더링하는 데 정확히 필요한 것이다.

C++

```
glm::mat4 lightSpaceMatrix = lightProjection * lightView;
```

이 `lightSpaceMatrix`는 우리가 이전에 $T$로 표시했던 변환 행렬이다. 이 `lightSpaceMatrix`를 사용하면, 각 셰이더에 투영 및 뷰 행렬의 광원 공간 등가물을 제공하는 한 장면을 평소와 같이 렌더링할 수 있다. 그러나 우리는 깊이 값에만 관심이 있고 모든 비용이 많이 드는 프래그먼트(조명) 계산에는 관심이 없다. 성능을 절약하기 위해 우리는 깊이 맵으로 렌더링하는 데 다르고 훨씬 간단한 셰이더를 사용할 것이다.

---

## 깊이 맵으로 렌더링 (Render to depth map)

장면을 광원의 관점에서 렌더링할 때, 우리는 정점(vertices)을 광원 공간으로만 변환하고 그 이상은 하지 않는 간단한 셰이더를 사용하는 것을 훨씬 선호할 것이다. `simpleDepthShader`라고 불리는 그러한 간단한 셰이더를 위해 우리는 다음 **정점 셰이더**를 사용할 것이다:

OpenGL Shading Language

```
#version 330 core
layout (location = 0) in vec3 aPos;
uniform mat4 lightSpaceMatrix;
uniform mat4 model;

void main()
{
    gl_Position = lightSpaceMatrix * model * vec4(aPos, 1.0);
}
```

이 정점 셰이더는 객체별 `model`과 정점을 취하고, `lightSpaceMatrix`를 사용하여 모든 정점을 광원 공간으로 변환한다.

우리는 색상 버퍼가 없고 그리기 및 읽기 버퍼를 비활성화했으므로, 결과 프래그먼트는 어떤 처리도 필요하지 않으므로 단순히 **빈 프래그먼트 셰이더**를 사용할 수 있다:

OpenGL Shading Language

```
#version 330 core

void main()
{
    // gl_FragDepth = gl_FragCoord.z;
}
```

이 빈 프래그먼트 셰이더는 어떤 처리도 하지 않으며, 실행이 끝날 때 깊이 버퍼가 업데이트된다. 우리는 한 줄의 주석을 해제함으로써 명시적으로 깊이를 설정할 수 있지만, 이것은 어쨌든 비하인드에서 일어나는 일과 실질적으로 같다.

이제 깊이/섀도우 맵을 렌더링하는 것은 실질적으로 다음과 같이 된다:

C++

```
simpleDepthShader.use();
glUniformMatrix4fv(lightSpaceMatrixLocation, 1, GL_FALSE, glm::value_ptr(lightSpaceMatrix));

glViewport(0, 0, SHADOW_WIDTH, SHADOW_HEIGHT);
glBindFramebuffer(GL_FRAMEBUFFER, depthMapFBO);
glClear(GL_DEPTH_BUFFER_BIT);
RenderScene(simpleDepthShader);
glBindFramebuffer(GL_FRAMEBUFFER, 0);
```

여기서 `RenderScene` 함수는 셰이더 프로그램을 취하고, 모든 관련 그리기 함수를 호출하며, 필요한 경우 해당 모델 행렬을 설정한다.

그 결과는 광원의 관점에서 보이는 각 프래그먼트의 가장 가까운 깊이를 담고 있는 멋지게 채워진 깊이 버퍼이다. 이 텍스처를 렌더링함으로써...

...적절하게 생성된 깊이 맵을 가지고 실제 그림자를 렌더링하기 시작할 수 있습니다. 프래그먼트가 그림자 속에 있는지 확인하는 코드는 (당연히) 프래그먼트 셰이더에서 실행되지만, 광원 공간 변환은 정점 셰이더에서 수행합니다:

```
#version 330 core
layout (location = 0) in vec3 aPos;
layout (location = 1) in vec3 aNormal;
layout (location = 2) in vec2 aTexCoords;

out VS_OUT {
    vec3 FragPos;
    vec3 Normal;
    vec2 TexCoords;
    vec4 FragPosLightSpace;
} vs_out;

uniform mat4 projection;
uniform mat4 view;
uniform mat4 model;
uniform mat4 lightSpaceMatrix;

void main()
{
    vs_out.FragPos = vec3(model * vec4(aPos, 1.0));
    vs_out.Normal = transpose(inverse(mat3(model))) * aNormal;
    vs_out.TexCoords = aTexCoords;
    vs_out.FragPosLightSpace = lightSpaceMatrix * vec4(vs_out.FragPos, 1.0);
    gl_Position = projection * view * vec4(aPos, 1.0);
}
```

여기서 새로운 것은 추가 출력 벡터 `FragPosLightSpace`입니다. 우리는 깊이 맵 단계에서 정점을 광원 공간으로 변환하는 데 사용된 것과 동일한 `lightSpaceMatrix`를 가져와 월드 공간 정점 위치를 프래그먼트 셰이더에서 사용하기 위해 광원 공간으로 변환합니다.

씬을 렌더링하는 데 사용할 메인 프래그먼트 셰이더는 블린-퐁(Blinn-Phong) 조명 모델을 사용합니다. 그런 다음 프래그먼트 셰이더 내에서 프래그먼트가 그림자 속에 있을 때 `1.0`이고 그림자 속에 없을 때 `0.0`인 그림자 값을 계산합니다. 결과 확산(diffuse) 및 반사(specular) 요소는 이 그림자 요소와 곱해집니다. 그림자는 (빛의 산란(light scattering)으로 인해) 완전히 어두운 경우는 거의 없기 때문에, 주변광(ambient) 요소는 그림자 곱셈에서 제외합니다.

```
#version 330 core
out vec4 FragColor;

in VS_OUT {
    vec3 FragPos;
    vec3 Normal;
    vec2 TexCoords;
    vec4 FragPosLightSpace;
} fs_in;

uniform sampler2D diffuseTexture;
uniform sampler2D shadowMap;

uniform vec3 lightPos;
uniform vec3 viewPos;

float ShadowCalculation(vec4 fragPosLightSpace)
{
    [...]
}

void main()
{
    vec3 color = texture(diffuseTexture, fs_in.TexCoords).rgb;
    vec3 normal = normalize(fs_in.Normal);
    vec3 lightColor = vec3(1.0);

    // ambient (주변광)
    vec3 ambient = 0.15 * lightColor;

    // diffuse (확산광)
    vec3 lightDir = normalize(lightPos - fs_in.FragPos);
    float diff = max(dot(lightDir, normal), 0.0);
    vec3 diffuse = diff * lightColor;

    // specular (반사광)
    vec3 viewDir = normalize(viewPos - fs_in.FragPos);
    float spec = 0.0;
    vec3 halfwayDir = normalize(lightDir + viewDir);
    spec = pow(max(dot(normal, halfwayDir), 0.0), 64.0);
    vec3 specular = spec * lightColor;

    // calculate shadow (그림자 계산)
    float shadow = ShadowCalculation(fs_in.FragPosLightSpace);                      
    vec3 lighting = (ambient + (1.0 - shadow) * (diffuse + specular)) * color;    

    FragColor = vec4(lighting, 1.0);
}
```

이 프래그먼트 셰이더는 우리가 고급 조명(advanced lighting) 챕터에서 사용했던 것의 대부분을 복사한 것이지만, 추가된...

...일종의 가상의 광원 영역이 있고, 이 영역 바깥의 큰 부분이 그림자 속에 있습니다. 이 영역은 바닥에 투영된 깊이 맵의 크기를 나타냅니다. 이런 일이 발생하는 이유는 우리가 이전에 깊이 맵의 래핑 옵션을 `GL_REPEAT`로 설정했기 때문입니다.

우리가 원하는 것은 깊이 맵의 범위를 벗어난 모든 좌표가 깊이 $1.0$을 가지는 것입니다. 그 결과 이러한 좌표는 절대 그림자 속에 있지 않게 됩니다 (객체의 깊이가 $1.0$보다 클 수 없으므로). 이것은 텍스처 경계 색상(texture border color)을 구성하고 깊이 맵의 텍스처 래핑 옵션을 `GL_CLAMP_TO_BORDER`로 설정하여 수행할 수 있습니다:

C++

```
glTexParameteri(GL_TEXTURE_2D, GL_TEXTURE_WRAP_S, GL_CLAMP_TO_BORDER);
glTexParameteri(GL_TEXTURE_2D, GL_TEXTURE_WRAP_T, GL_CLAMP_TO_BORDER);
float borderColor[] = { 1.0f, 1.0f, 1.0f, 1.0f };
glTexParameterfv(GL_TEXTURE_2D, GL_TEXTURE_BORDER_COLOR, borderColor);
```

이제 깊이 맵의 $[0, 1]$ 좌표 범위를 벗어난 곳을 샘플링할 때마다, 텍스처 함수는 항상 깊이 $1.0$을 반환하여, $0.0$의 그림자 값을 생성합니다. 이제 결과는 더 그럴듯해 보입니다:

여전히 어두운 영역을 보여주는 한 부분이 있는 것 같습니다. 이는 광원의 직교 절두체의 **원거리 평면(far plane)** 바깥에 있는 좌표입니다. 그림자 방향을 보면 이 어두운 영역이 항상 광원의 절두체 끝 부분에서 발생한다는 것을 알 수 있습니다.

광원 공간으로 투영된 프래그먼트 좌표는 $z$ 좌표가 $1.0$보다 클 때 광원의 원거리 평면보다 더 멀리 있습니다. 이 경우, 좌표의 $z$ 구성 요소를 깊이 맵 값과 비교하므로 `GL_CLAMP_TO_BORDER` 래핑 방식이 더 이상 작동하지 않습니다. $z$가 $1.0$보다 클 때 이는 항상 참을 반환합니다.

이에 대한 수정은 상대적으로 쉽습니다. 투영된 벡터의 $z$ 좌표가 $1.0$보다 클 때마다 그림자 값을 $0.0$으로 강제 설정하면 됩니다:

OpenGL Shading Language

```
float ShadowCalculation(vec4 fragPosLightSpace)
{
    [...]
    if(projCoords.z > 1.0)
        shadow = 0.0;
    return shadow;
}
```

원거리 평면을 확인하고 깊이 맵을 수동으로 지정된 경계 색상으로 클램핑하는 것은 깊이 맵의 과도한 샘플링(over-sampling)을 해결합니다. 이로써 마침내 우리가 찾고 있던 결과를 얻게 됩니다:

---

## 원거리 평면 (The far plane)

광원 공간에 투영된 프래그먼트 좌표는 $z$ 좌표가 $1.0$보다 클 때 광원의 원거리 평면(far plane)보다 더 멀리 있다. 이 경우, 좌표의 $z$ 구성 요소를 깊이 맵 값과 비교하기 때문에 `GL_CLAMP_TO_BORDER` 래핑 방법은 더 이상 작동하지 않는다. $z$가 $1.0$보다 클 때는 항상 `true`를 반환하기 때문이다.

이에 대한 해결책 또한 비교적 쉬운데, 투영된 벡터의 $z$ 좌표가 $1.0$보다 클 때마다 그림자 값(shadow value)을 단순히 $0.0$으로 강제하기 때문이다:

OpenGL Shading Language

```
float ShadowCalculation(vec4 fragPosLightSpace)
{
    [...]
    if(projCoords.z > 1.0)
        shadow = 0.0;
    return shadow;
}
```

원거리 평면을 확인하고 깊이 맵을 수동으로 지정된 경계 색상으로 클램프하는 것은 깊이 맵의 과도한 샘플링을 해결한다. 이것은 마침내 우리가 찾고 있는 결과를 제공한다:

이 모든 것의 결과는 투영된 프래그먼트 좌표가 깊이 맵 범위 내에 있는 곳에서만 그림자가 생긴다는 것을 의미하므로, 광원 절두체 외부에 있는 모든 것은 눈에 보이는 그림자가 없을 것이다. 게임에서는 일반적으로 이것이 먼 거리에서만 발생하도록 하기 때문에, 이전에 가졌던 명백한 검은색 영역보다 훨씬 더 그럴듯한 효과이다.

---

## PCF

현재 그림자는 장면에 멋진 추가 요소이지만, 여전히 우리가 원하는 것과는 정확히 일치하지 않는다. 그림자를 확대해 보면 섀도우 매핑의 해상도 의존성이 빠르게 분명해진다.

깊이 맵은 고정된 해상도를 가지기 때문에, 깊이가 종종 하나의 텍셀(texel)당 하나 이상의 프래그먼트에 걸쳐 있다. 결과적으로, 여러 프래그먼트가 깊이 맵에서 동일한 깊이 값을 샘플링하고 동일한 그림자 결론에 도달하여 이러한 들쭉날쭉한 블록 모양의 가장자리를 생성한다.

이러한 블록 모양의 그림자는 깊이 맵 해상도를 높이거나, 광원 절두체를 장면에 가능한 한 가깝게 맞추려 노력함으로써 줄일 수 있다.

이러한 들쭉날쭉한 가장자리에 대한 또 다른 (부분적인) 해결책은 **PCF**, 즉 **percentage-closer filtering (근접 비율 필터링)**이라고 불리는데, 이는 더 부드러운 그림자를 생성하여 블록 모양이 덜하거나 딱딱하지 않게 보이도록 하는 많은 다른 필터링 함수를 포함하는 용어이다. 아이디어는 깊이 맵에서 한 번 이상 샘플링하는 것인데, 매번 약간씩 다른 텍스처 좌표를 사용한다. 각 개별 샘플에 대해 그림자 속에 있는지 여부를 확인한다. 그런 다음 모든 하위 결과가 결합되고 평균화되어 우리는 보기 좋고 부드러운 그림자를 얻게 된다.

PCF의 한 가지 간단한 구현은 깊이 맵 주변 텍셀을 단순히 샘플링하고 그 결과를 평균화하는 것이다:

OpenGL Shading Language

```
float shadow = 0.0;
vec2 texelSize = 1.0 / textureSize(shadowMap, 0);
for(int x = -1; x <= 1; ++x)
{
    for(int y = -1; y <= 1; ++y)
    {
        float pcfDepth = texture(shadowMap, projCoords.xy + vec2(x, y) * texelSize).r;
        shadow += currentDepth - bias > pcfDepth ? 1.0 : 0.0;
    }
}
shadow /= 9.0;
```

여기서 `textureSize`는 밉맵 레벨 $0$에서 주어진 샘플러 텍스처의 너비와 높이의 `vec2`를 반환한다. $1$을 이것으로 나눈 값은 단일 텍셀의 크기를 반환하며, 우리는 이것을 텍스처 좌표를 오프셋하는 데 사용하여 각 새 샘플이 다른 깊이 값을 샘플링하도록 한다. 여기서 우리는 투영된 좌표의 $x$ 및 $y$ 값 주변에서 $9$개의 값을 샘플링하고, 그림자 가려짐을 테스트하며, 마지막으로 총 샘플 수로 결과를 평균화한다.

더 많은 샘플을 사용하거나/또는 `texelSize` 변수를 변경함으로써 부드러운 그림자의 품질을 높일 수 있다. 아래에서 간단한 PCF가 적용된 그림자를 볼 수 있다:

멀리서 보면 그림자가 훨씬 더 좋아 보이고 덜 딱딱하다. 확대하면 여전히 섀도우 매핑의 해상도 아티팩트를 볼 수 있지만, 일반적으로 대부분의 애플리케이션에 좋은 결과를 제공한다.

여기에서 예제의 전체 소스 코드를 찾을 수 있다.

실제로 PCF에는 훨씬 더 많은 것이 있으며, 부드러운 그림자의 품질을 상당히 향상시키는 꽤 많은 기법들이 있지만, 이 챕터의 길이를 고려하여 그것은 나중 논의를 위해 남겨둘 것이다.

---

## 직교 투영 대 원근 투영 (Orthographic vs perspective)

**직교 투영(orthographic)** 또는 **원근 투영(perspective)** 행렬로 깊이 맵을 렌더링하는 것 사이에는 차이가 있다. 직교 투영 행렬은 원근으로 장면을 변형시키지 않으므로 모든 뷰/광선이 평행하다. 이것은 **방향성 광원**에 훌륭한 투영 행렬이 되게 한다. 반면에 원근 투영 행렬은 원근을 기반으로 모든 정점을 변형시키며 이는 다른 결과를 제공한다. 다음 이미지는 두 투영 방법의 다른 그림자 영역을 보여준다:

원근 투영은 방향성 광원과는 달리 실제 위치를 가진 광원에 가장 적합하다. 원근 투영은 주로 **스포트라이트(spotlights)** 및 **점 광원(point lights)**과 함께 사용되는 반면, 직교 투영은 **방향성 광원**에 사용된다.

원근 투영 행렬을 사용할 때의 또 다른 미묘한 차이점은 깊이 버퍼를 시각화할 때 종종 거의 완전히 흰색 결과가 나타난다는 것이다. 이것은 원근 투영을 사용하면 깊이가 **비선형 깊이 값(non-linear depth values)**으로 변환되며, 눈에 띄는 대부분의 범위가 근거리 평면(near plane)에 가깝기 때문에 발생한다. 직교 투영에서 했던 것처럼 깊이 값을 제대로 볼 수 있도록 하려면, 깊이 테스트 챕터에서 논의했듯이 먼저 비선형 깊이 값을 선형으로 변환해야 한다:1

OpenGL Shading Language

```
#version 330 core
out vec4 FragColor;
in vec2 TexCoords;

uniform sampler2D depthMap;
uniform float near_plane;
uniform float far_plane;

float LinearizeDepth(float depth)
{
    float z = depth * 2.0 - 1.0; // Back to NDC
    return (2.0 * near_plane * far_plane) / (far_plane + near_plane - z * (far_plane - near_plane));
}

void main()
{
    float depthValue = texture(depthMap, TexCoords).r;
    FragColor = vec4(vec3(LinearizeDepth(depthValue)
```