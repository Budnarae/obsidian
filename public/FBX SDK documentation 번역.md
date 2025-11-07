---
tags:
  - graphics
  - translation
---

_Filmbox_

---

**Autodesk FBX 기술이란 무엇인가**

이 주제는 Autodesk FBX 기술과 그 기능에 대한 광범위한 설명을 제공합니다.

FBX SDK는 Autodesk FBX 기술의 일부로, 3D 콘텐츠 개발자가 3D 데이터를 가져오고 내보낼 수 있게 해주는 도구 제품군입니다. Autodesk FBX는 미디어 및 엔터테인먼트 산업에 종사하는 조직들이 다양한 2D 및 3D 디지털 콘텐츠 제작 애플리케이션을 혼합하고 매치할 수 있도록 함으로써 유연성에 기여합니다.

**3D 씬을 위한 FBX 파일 형식**

FBX 파일(.fbx)은 일반적으로 바이너리(또는 네이티브) 형식으로 저장되지만, ASCII 형식으로도 저장될 수 있습니다. 바이너리 FBX 파일과 ASCII FBX 파일 모두 .fbx 파일명 확장자를 사용합니다.

FBX 파일은 카메라, 조명, 메시, NURBS 및 3D 씬의 기타 요소에 대한 데이터를 저장합니다. Autodesk 3ds Max, Autodesk Maya, Autodesk MotionBuilder와 같은 애플리케이션은 FBX 파일에서 씬 데이터의 전체 또는 일부를 가져올 수 있습니다. 또한 씬 데이터를 FBX 파일로 내보낼 수도 있습니다. 이러한 모든 작업은 FBX SDK를 사용합니다.

다음은 ASCII 형식의 작은 FBX 파일을 축약한 버전입니다. 생략된 줄은 ...으로 표시되며, 일부 주석을 수동으로 추가했습니다. 주석은 줄의 어느 곳에서나 세미콜론(";")으로 시작합니다.

```
; FBX 7.1.0 프로젝트 파일
; Copyright (C) 1997-2010 Autodesk Inc. and/or its licensors.
; All rights reserved.
; ----------------------------------------------------
FBXHeaderExtension:  {
       ; 헤더 정보: 전역 파일 정보.
    FBXHeaderVersion: 1003
    FBXVersion: 7100
    CreationTimeStamp:  {
        Version: 1000
        Year: 2010
        Month: 1
        Day: 19
        Hour: 16
        Minute: 30
        Second: 28
        Millisecond: 884
    }
    Creator: "FBX SDK/FBX Plugins version 2011.2"
    SceneInfo: "SceneInfo::GlobalInfo", "UserData" {
 ...
}
GlobalSettings:  {
    Version: 1000
    Properties70:  {
        P: "UpAxis", "int", "Integer", "",1
        P: "UpAxisSign", "int", "Integer", "",1
        P: "FrontAxis", "int", "Integer", "",2
        P: "FrontAxisSign", "int", "Integer", "",1
        P: "CoordAxis", "int", "Integer", "",0
        P: "CoordAxisSign", "int", "Integer", "",1
        P: "OriginalUpAxis", "int", "Integer", "",-1
        P: "OriginalUpAxisSign", "int", "Integer", "",1
        P: "UnitScaleFactor", "double", "Number", "",1
        P: "OriginalUnitScaleFactor", "double", "Number", "",1
        P: "AmbientColor", "ColorRGB", "Color", "",0,0,0
        P: "DefaultCamera", "KString", "", "", "Producer Perspective"
        P: "TimeMode", "enum", "", "",6
        P: "TimeSpanStart", "KTime", "Time", "",0
        P: "TimeSpanStop", "KTime", "Time", "",46186158000
    }
}
 ...
; 객체 정의
;------------------------------------------------------------------
Definitions:  {
    Version: 100
    Count: 2251
    ObjectType: "GlobalSettings" {
        Count: 1
    }
    ObjectType: "Model" {
        Count: 86
        PropertyTemplate: "FbxNode" {
            Properties70:  {
                P: "QuaternionInterpolate", "bool", "", "",0
                P: "RotationOffset", "Vector3D", "Vector", "",0,0,0
                P: "RotationPivot", "Vector3D", "Vector", "",0,0,0
                P: "ScalingOffset", "Vector3D", "Vector", "",0,0,0
                P: "ScalingPivot", "Vector3D", "Vector", "",0,0,0
 ...}
    ObjectType: "Material" {
        Count: 1
        PropertyTemplate: "FbxSurfacePhong" {
            Properties70:  {
                P: "ShadingModel", "KString", "", "", "Phong"
                P: "MultiLayer", "bool", "", "",0
                P: "EmissiveColor", "ColorRGB", "Color", "",0,0,0
                P: "EmissiveFactor", "double", "Number", "",1
                P: "AmbientColor", "ColorRGB", "Color", "",0.2,0.2,0.2
 ...}
    Model: 21883936, "Model::Humanoid:Hips", "LimbNode" {
        Version: 232
        Properties70:  {
            P: "ScalingMin", "Vector3D", "Vector", "",1,1,1
            P: "NegativePercentShapeSupport", "bool", "", "",0
            P: "DefaultAttributeIndex", "int", "Integer", "",0
            P: "Lcl Translation", "Lcl Translation", "", "A+",-271.281097412109,-762.185852050781,528.336242675781
            P: "Lcl Rotation", "Lcl Rotation", "", "A+",-1.35128843784332,2.6148145198822,0.42334708571434
            P: "Lcl Scaling", "Lcl Scaling", "", "A+",1,0.99999988079071,1
 ...
```

**참고:** FBX 파일 형식은 문서화되어 있지 않습니다. 애플리케이션은 FBX SDK를 사용하여 씬 데이터를 FBX 파일(및 FBX SDK가 지원하는 기타 파일 형식)로 내보내고 가져와야 합니다.

**FBX 소프트웨어 개발 키트**

FBX 소프트웨어 개발 키트(FBX SDK)는 소프트웨어 개발자가 FBX 기술을 사용하는 애플리케이션을 만들거나, 기존 애플리케이션에 FBX 기술을 통합할 수 있도록 합니다.

FBX SDK는 GNU 일반 공중 사용 허가서(GPL)의 적용을 받지 않으며, 소스 코드는 공개적으로 제공되지 않습니다. Maya 및 3ds Max FBX 플러그인을 사용자 정의하기 위한 일부 소스 코드는 존재하지만, 이는 FBX SDK 자체가 아닌 FBX Extensions SDK에 패키지되어 있습니다. FBX SDK의 최신 릴리스 및 이전 버전은 http://www.autodesk.com/fbx의 Autodesk FBX 웹사이트에서 얻을 수 있습니다. FBX SDK는 Autodesk의 서면 허가 없이 재배포하거나 재패키징할 수 없습니다. FBX SDK를 사용하는 오픈 소스 프로젝트를 배포하려는 경우, 사용자가 필요한 버전의 FBX SDK를 설치할 수 있도록 Autodesk FBX 웹사이트에 대한 링크를 포함해야 합니다.

---

**샘플 FBX 애플리케이션**

**Autodesk 3ds Max 및 Autodesk Maya용 FBX 플러그인**

Autodesk 3ds Max는 사용자가 FBX 파일에 저장된 씬의 전체 또는 일부를 3ds Max 씬으로 가져오고, 3ds Max 씬의 전체 또는 일부를 FBX 파일로 내보낼 수 있도록 합니다. 다음은 3ds Max용 FBX 내보내기 대화 상자입니다:

Maya는 해당 씬에 대해 동등한 가져오기/내보내기 기능을 제공합니다. 다음은 .fbx 파일에 대한 Maya의 내보내기 대화 상자입니다:

3ds Max와 Maya 모두 FBX 기능을 플러그인으로 제공합니다. 이러한 플러그인은 FBX SDK로 작성됩니다.

**FBX Review**

FBX Review는 3D 자산 및 애니메이션을 검토하기 위한 독립 실행형 도구입니다. 이 도구를 사용하면 3D 저작 소프트웨어를 사용하지 않고도 3D 콘텐츠를 검토할 수 있습니다.

.fbx, .obj 등 다양한 형식의 3D 파일을 열고 검토할 수 있습니다. 또한 애니메이션 재생, 셰이딩 모드 전환, 씬 조명, 카메라 및 테이크 전환과 같은 많은 기능을 제공합니다.

---

**제작 파이프라인에서 FBX가 적합한 위치**

**콘텐츠 개발자가 FBX 기술로 할 수 있는 일**

콘텐츠 개발자는 영화, 텔레비전 및 게임을 위한 3D 모델링 및 애니메이션 작업을 하는 사람들입니다. 다음은 콘텐츠 개발자가 FBX 기술을 사용하는 몇 가지 방법입니다:

**씬 자산 공유(상호 운용성)** 모델 및 기타 씬 자산을 도구에서 도구로, 제작 회사에서 제작 회사로 이동합니다. 예를 들어, Studio 1은 3ds Max에서 캐릭터를 만든 다음 FBX 파일로 내보냅니다. Studio 2는 FBX 파일을 MotionBuilder로 가져와서 캐릭터에 모션 캡처 데이터를 추가한 다음 FBX 파일로 내보냅니다. Studio 3은 두 번째 파일을 Maya로 가져와서 모델의 스키닝을 수정한 다음 세 번째 FBX 파일로 내보냅니다. Studio 4는 세 번째 파일을 자체 독점 도구로 가져오는 식으로 계속됩니다.

**씬 자산 저장** 내구성 있는 파일 형식으로 씬 자산을 저장합니다. FBX의 각 새 릴리스는 이전 버전의 FBX 파일을 읽을 수 있습니다.

**애니메이션 처리** 예를 들어, 애니메이션 커브에 필터를 적용합니다.

**판매용 모델 패키징** 3D 모델 공급업체는 FBX를 파일 형식으로 사용합니다.

**디자이너가 FBX 기술로 할 수 있는 일**

건축가, 디자이너, 엔지니어 및 디자인 시각화 전문가는 Autodesk Revit Architecture와 같은 제품을 사용하여 건물 및 기타 객체를 설계하고 시각화합니다.

이러한 디자이너는 FBX 기술을 사용하여 광고 및 마케팅 자료를 준비하는 콘텐츠 개발자가 사용할 수 있는 파일 형식으로 모델, 메타데이터 및 기타 자산을 저장합니다.

**FBX 기술을 지원하는 애플리케이션**

다음 Autodesk 제품은 FBX 기술을 사용하여 파일을 가져오고 내보냅니다:

|제품|설명|
|---|---|
|Autodesk 3ds Max|3D 애니메이션, 모델링 및 렌더링 솔루션. FBX 파일을 가져오고 내보내는 플러그인 포함.|
|Autodesk Maya|3D 모델링, 애니메이션 및 렌더링 솔루션. FBX 파일을 가져오고 내보내는 플러그인 포함.|
|Autodesk Maya LT|3D 모델링 및 애니메이션 소프트웨어. FBX 파일을 가져오고 내보냄.|
|Autodesk MotionBuilder|3D 캐릭터 애니메이션을 위한 생산성 제품군. FBX 파일을 가져오고 내보냄.|
|Autodesk Mudbox|3D 모델러 및 텍스처 아티스트를 위한 디지털 조각 및 텍스처 페인팅 소프트웨어. FBX 파일을 가져오고 내보냄.|
|Autodesk Flame|실시간 시각 효과 디자인 및 합성 시스템. FBX 파일을 가져오고 내보냄.|
|Autodesk Smoke|SD, HD, 2K 필름 이상을 위한 통합 편집 및 마무리 시스템. FBX 파일을 가져오고 내보냄.|
|AutoCAD Revit Architecture|빌딩 정보 모델링(BIM) 애플리케이션. FBX 파일을 내보냄.|
|AutoCAD|범용 CAD 모델링 패키지. FBX 파일을 가져오고 내보냄.|

많은 타사 소프트웨어 제품도 FBX SDK를 사용하여 파일을 가져오고 내보냅니다. 자세한 내용은 __http://www.autodesk.com/fbx__를 참조하십시오.

---

**새로운 기능/변경 사항**

이 섹션은 FBX SDK의 각 릴리스 간의 중요한 변경 사항에 대한 개요를 제공합니다.

FBX SDK의 이전 버전 이후의 모든 변경 사항에 대한 세부 정보는 FBX SDK 설치 루트 디렉토리에 있는 readme.txt 파일에 있습니다.

**더 이상 사용되지 않는 클래스 및 함수 피하기**

FBX SDK의 각 릴리스에서 더 이상 사용되지 않는 클래스 및 함수는 `K_DEPRECATED`로 선언됩니다:

```
K_DEPRECATED KFbxTakeNode* GetDefaultTakeNode();
```

더 이상 사용되지 않는 함수를 계속 사용할 수 있지만 다음 사항에 유의하십시오:

- 컴파일러에서 경고가 발생합니다.
- 현재 릴리스에서 더 이상 사용되지 않는 함수는 다음 릴리스에서 완전히 제거됩니다.

**이 섹션의 페이지**

- FBX SDK 2020
- FBX SDK 2019
- FBX SDK 2018
- FBX SDK 2017
- FBX SDK 2016
- FBX SDK 2015
- FBX SDK 2014
- FBX SDK 2013
- FBX SDK 2012
- FBX SDK 2011

---

**플랫폼 요구 사항**

FBX SDK는 다음 플랫폼의 32비트 및 64비트 버전에서 실행됩니다:

|플랫폼|요구 사항|
|---|---|
|Microsoft Windows|Windows 7.0<br>Windows 8.0 / Windows 8.1<br>Windows 10|
|Windows Store 앱|Windows 8.0 이상.|
|Linux|GCC 버전 9.3 이상을 제공하는 모든 Linux 구현.|
|Mac OS|Intel 프로세서(64비트만) 또는 Apple M1(ARM64)이 탑재된 버전 10.8 이상|
|iOS|버전 7.0. ARMv7, ARMv7s 및 ARM64 아키텍처 지원.|

자세한 내용은 __권장 개발 환경__을 참조하십시오.

---

**지원되는 파일 형식**

FBX SDK는 다음을 수행할 수 있습니다:

- FBX 파일 형식 버전 7.5, 7.4, 7.3, 7.2, 7.1, 7.0, 6.1 및 6.0과 호환되는 FBX 파일을 가져옵니다.
- FBX 파일 형식 버전 7.5, 7.4, 7.3, 7.2, 7.1, 7.0 및 6.1과 호환되는 FBX 파일을 내보냅니다.

FBX SDK는 다음 애플리케이션과 호환되는 FBX 파일을 가져오고 내보냅니다:

|소프트웨어|버전|
|---|---|
|MotionBuilder|버전 5.5 이상.|
|FBX Plug-in for 3ds Max|모든 버전.|
|FBX Plug-in for Maya|모든 버전.|
|FBX Plug-in for Maya LT|모든 버전. 참고: Maya LT 2016에서 FBX 파일을 내보낼 때 이제 한 번에 최대 100,000개의 폴리곤을 내보낼 수 있습니다. 씬 또는 선택한 객체가 100,000개 제한을 초과하면 오류가 표시됩니다. 자세한 내용은 Maya LT 도움말을 참조하십시오.|
|Mudbox|버전 2010 이상.|
|Flame|버전 8.0 이상.|
|Smoke|버전 6.0 이상.|
|Revit Architecture|버전 2009.1 이상.|
|AutoCAD|버전 2011 이상.|

FBX SDK는 다음 파일 형식의 파일도 가져오고 내보냅니다:

|파일 형식|버전|
|---|---|
|Autodesk AutoCAD DXF (.dxf)|버전 13 이하.|
|Collada DAE (.dae)|버전 1.5 이하.|
|Alias OBJ (.obj)|모든 버전.|

**참고:** FBX SDK 2012.0부터 .3ds 파일 형식 쓰기가 중단되었습니다. 그러나 .3ds 파일 리더는 계속 유지됩니다.

---

**지원되는 씬 요소**

FBX SDK를 사용하면 씬(`FbxScene`)의 다음 요소에 액세스하거나, 생성하거나, 수정할 수 있습니다:

- 메시 - `FbxMesh`
- 상세도(LOD) 그룹 - `FbxLodGroup`
- 카메라(3D용 스테레오 카메라 포함) - `FbxCamera`
- 조명 및 고보 - `FbxLight`, `FbxGobo`
- NURBS - `FbxNurbs`, `FbxNurbsCurve`, `FbxNurbsSurface`, `FbxTrimNurbsSurface`
- 지오메트리에 대한 텍스처 매핑 - `FbxTexture`
- 지오메트리에 대한 머티리얼 매핑 - `FbxSurfaceMaterial`
- 제약 조건 - `FbxConstraint`
- 지오메트리의 제어점에 대한 정점 캐시 애니메이션 - `FbxDeformer`
- Up-Axis(X/Y/Z) 및 씬 스케일링(단위)을 제공하는 씬 설정 - `FbxGlobalSettings`, `FbxAxisSystem`
- 위치, 회전, 스케일, 부모를 포함한 변환 데이터 - `FbxNode`
- 마커 - `FbxMarker`
- 선 - `FbxLine`
- 스켈레톤 세그먼트(루트, 림, 림 노드) - `FbxSkeleton`
- 애니메이션 커브 - `FbxAnimCurve`
- 노드 목록(본 및 지오메트리)에 대한 레스트 및 바인드 포즈 - `FbxPose`

---

**정보 및 기술 지원**

이 주제는 정보 및 기술 지원을 위한 참조 자료 세트를 제공합니다.

FBX SDK 사용자를 위해 Autodesk FBX 웹사이트, FBX Developer Help, C++ Reference, Autodesk Developer Network 및 AREA 토론 포럼을 포함한 다양한 정보 출처를 이용할 수 있습니다.

**FBX Developer Help**

현재 읽고 계신 문서가 FBX Developer Help입니다. 이 문서의 목적은 FBX SDK의 핵심 개념에 익숙해지도록 하는 것입니다. 이 주제는 통찰력 있는 샘플 프로그램이나 C++ Reference 내의 관련 문서를 안내합니다. 마지막 순간의 문서 변경 사항에 대해서는 FBX SDK 설치의 루트 폴더에 있는 readme.txt 파일도 참조하십시오.

**C++ 레퍼런스**

C++ Reference에는 각 클래스, 멤버 함수, 열거형 등에 대한 API 문서가 포함되어 있습니다. FBX SDK는 Autodesk 3ds Max 및 Autodesk Maya용 FBX 플러그인을 개발하는 데 사용되었습니다. 또한 FBX Converter 및 FBX for QuickTime 프로그램을 개발하는 데도 사용되었습니다. 이러한 도구의 기능은 FBX SDK의 기능에 대한 좋은 소개를 제공합니다(이러한 도구에 대한 링크는 **http://www.autodesk.com/fbx** 참조).

**레퍼런스 가이드 명명 규칙**

레퍼런스 가이드의 헤더 파일과 샘플 프로그램은 일반적으로 다음 명명 규칙을 따릅니다.

|접두사|참고|
|---|---|
|`Fbx`|대부분의 FBX SDK 클래스 이름은 Fbx로 시작합니다. 예: `FbxNode`, `FbxScene`, `FbxCamera`|
|`p`|멤버 함수에 전달되는 매개변수는 소문자 "p"로 시작합니다. 예: `pWriteFileFormat`, `pScene`, `pFilename`|
|`l`|지역 변수는 소문자 "l"로 시작합니다. 예: `lWriteFileFormat`, `lScene`, `lFilename`|
|`g`|전역 변수는 소문자 "g"로 시작합니다. 예: `gStart`, `gStop`, `gCurrentTime`|
|`m`|멤버 데이터(멤버 변수)는 소문자 "m"으로 시작합니다. 예: `mDescription`, `mImportname`, `mSelect`|

**Autodesk Developer Network**

FBX SDK에 대한 기술 지원은 Autodesk Developer Network(ADN) Sparks 타사 개발자 프로그램을 통해 제공됩니다. 프로그램 세부 정보, 혜택 및 가격은 **Autodesk Developer Network** 웹 페이지에서 확인할 수 있습니다.

**토론 포럼**

개발자 및 기타 사용자를 위한 무료 사용자 간 토론 포럼을 이용하려면 디지털 엔터테인먼트 및 시각화를 위한 Autodesk 커뮤니티인 AREA의 FBX 섹션을 방문하십시오: **https://forums.autodesk.com/t5/fbx-forum/bd-p/area-b64**

---
---

**시작하기**

이 섹션은 FBX SDK를 설치하고 구성하는 방법에 대한 정보를 제공합니다. 또한 FBX SDK에 익숙해지는 데 도움이 되는 기본 프로그램도 포함되어 있습니다.

**이 섹션의 페이지**

- 설치 및 구성
- 첫 번째 FBX SDK 프로그램

---

**설치 및 구성**

이 섹션은 개발 플랫폼에 따라 FBX SDK를 설치하고 구성하는 방법을 설명합니다.

**참고:** FBX SDK에 대한 C++ 인터페이스 대신 Python FBX를 사용할 계획이라면 __Scripting with Python FBX__를 참조하십시오.

**이 섹션의 페이지**

- 권장 개발 환경
- 디렉토리 구조
- Windows용 FBX SDK 구성
- Linux용 FBX SDK 구성
- Mac OS용 FBX SDK 구성

---

**권장 개발 환경**

다음 표는 FBX SDK로 플러그인, 변환기 및 기타 애플리케이션을 개발하는 데 권장되는 플랫폼과 컴파일러를 나열합니다:

|지원되는 플랫폼|지원되는 개발 환경 또는 컴파일러|
|---|---|
|Windows 7.0|Visual Studio 2015, Visual Studio 2017, Visual Studio 2019|
|Windows 8.0 / Windows 8.1||
|Windows 10.0||
|Linux|GCC 버전 9.3 이상을 제공하는 모든 구현.|
|Mac OS X|Clang (Xcode 12.0)|

**참고:**

- 플랫폼 또는 컴파일러가 위에 나열되어 있지 않은 경우, FBX SDK를 사용하는 프로그램을 컴파일하지 못할 수 있습니다.
- FBX SDK로 개발된 애플리케이션을 실행할 수 있는 플랫폼에 대한 정보는 __플랫폼 요구 사항__을 참조하십시오.

---

**디렉토리 구조**

FBX SDK의 디렉토리 구조는 지원되는 모든 플랫폼에서 동일합니다: **Windows용 FBX SDK 구성**, **Mac OS용 FBX SDK 구성** 및 **Linux용 FBX SDK 구성**.

| 디렉토리 경로                   | 설명                                                         |
| ------------------------- | ---------------------------------------------------------- |
| \<yourFBXSDKpath>         | FBX 배포 디렉토리의 루트. readme 파일, 라이선스 텍스트 및 제거 프로그램이 포함되어 있습니다. |
| \<yourFBXSDKpath>\samples | 각각 자체 하위 폴더에 있는 샘플 프로그램. CMake 파일, 소스 등이 포함되어 있습니다.        |
| \<yourFBXSDKpath>\include | FBX SDK용 헤더 파일.                                            |
| \<yourFBXSDKpath>\lib     | FBX SDK용 런타임 라이브러리.                                        |

---

**Windows용 FBX SDK 구성**

**FBX SDK 다운로드 및 설치**

Windows에서 FBX SDK를 다운로드하고 설치하려면:

1. http://www.autodesk.com/fbx로 이동합니다.
2. GET FBX SDK를 클릭하여 FBX SDK 다운로드 페이지에 액세스합니다.
3. Visual Studio 버전에 맞는 Windows용 FBX SDK를 선택하고 설치 파일을 다운로드합니다.
4. 설치 프로그램을 실행하고 지침을 따릅니다.
5. 설치 프로그램을 통해 대상 폴더를 지정할 수 있습니다. 새 폴더 또는 빈 폴더를 지정하십시오. 이 주제에서는 **<yourFBXSDKpath>**라고 하며, FBX SDK의 배포 디렉토리입니다.
6. <yourFBXSDKpath>\readme.txt 파일을 읽으십시오. readme.txt 파일에는 이전 버전 이후 FBX SDK의 변경 사항에 대한 자세한 정보와 마지막 순간의 문서가 포함되어 있습니다.

**참고:**

- 설치 프로그램은 Windows 레지스트리나 Windows 시작 메뉴를 수정하지 않습니다.
- 각 버전을 별도의 폴더에 설치하는 경우 컴퓨터에 FBX SDK의 여러 버전을 설치할 수 있습니다.

**FBX SDK 제거**

컴퓨터에서 FBX SDK를 제거하려면:

<yourFBXSDKpath>\uninstall.exe를 실행합니다.

**Windows용 런타임 라이브러리**

Visual Studio 버전과 대상 애플리케이션의 프로세서 아키텍처에 적합한 런타임 라이브러리를 사용해야 합니다. FBX 라이브러리는 Visual Studio 버전, 프로세서 유형 및 빌드 모드에 따라 <yourFBXSDKpath>\lib 아래의 하위 디렉토리로 구성됩니다:

```
<yourFBXSDKpath>\lib\<compiler_version>\<processor_type>\<build_mode>
```

예를 들어:

```
<yourFBXSDKpath>\lib\vs2015\x64\release
```

이러한 각 하위 디렉토리에는 서로 다른 플래그로 컴파일된 여러 버전의 라이브러리가 포함되어 있습니다. 다음 표는 FBX SDK 라이브러리 파일 이름과 설명을 제공합니다.

**참고:** 동적 .lib 파일은 애플리케이션 실행 시 해당 .dll 파일을 사용할 수 있어야 합니다(아래 표의 애플리케이션 종속성 열 참조). 애플리케이션에서 FBX SDK의 동적 라이브러리 버전을 사용하려는 경우 실행 파일과 함께 적절한 .dll을 배포해야 합니다.

|라이브러리 파일|라이브러리 설명|필요한 런타임 라이브러리 옵션|필요한 전처리기 정의|
|---|---|---|---|
|libfbxsdk.lib|동적 링킹||FBXSDK_SHARED|
|libfbxsdk-md.lib|정적 링킹|/MD||
|libfbxsdk-mt.lib|정적 링킹|/MT||

다음 표는 관련 런타임 라이브러리 옵션에 대한 설명을 제공합니다. 이러한 설명은 http://msdn.microsoft.com/en-us/library/2kzt1wy3.aspx에서도 찾을 수 있습니다.

|런타임 라이브러리 옵션|설명|
|---|---|
|MT|애플리케이션이 런타임 라이브러리의 멀티스레드 정적 버전을 사용하도록 합니다. _MT를 정의하고 컴파일러가 라이브러리 이름 LIBCMT.lib를 .obj 파일에 배치하여 링커가 LIBCMT.lib를 사용하여 외부 심볼을 확인하도록 합니다.|
|MD|애플리케이션이 런타임 라이브러리의 멀티스레드 및 DLL 관련 버전을 사용하도록 합니다. _MT 및 _DLL을 정의하고 컴파일러가 라이브러리 이름 MSVCRT.lib를 .obj 파일에 배치하도록 합니다. 이 옵션으로 컴파일된 애플리케이션은 MSVCRT.lib에 정적으로 링크됩니다. 이 라이브러리는 링커가 외부 참조를 확인할 수 있도록 하는 코드 계층을 제공합니다. 실제 작업 코드는 MSVCR100.DLL에 포함되어 있으며, 이는 MSVCRT.lib와 링크된 애플리케이션에서 실행 시 사용할 수 있어야 합니다.|

**참고:** 이러한 라이브러리는 모두 Microsoft의 멀티스레드 C 라이브러리에 링크될 수 있습니다. 그러나 FBX SDK 코드는 스레드 안전이 보장되지 않습니다.

**Visual Studio 구성**

이 섹션의 지침은 Visual Studio 2010을 기반으로 합니다.

**참고** FBX SDK용 샘플 프로그램을 빌드하고 실행하려면 샘플 프로그램 빌드 및 실행을 참조하십시오.

FBX SDK를 사용하는 새 Visual Studio 솔루션을 만들려면:

1. Visual Studio를 시작합니다.
    
2. 새 프로젝트를 만들려면 파일 메뉴에서 새로 만들기 > 프로젝트를 선택합니다.
    
3. Visual C++ > Win32를 선택합니다.
    
4. 평소와 같이 계속한 다음 마침을 클릭합니다. 새 프로젝트와 솔루션이 나타납니다.
    
5. 프로젝트 > 속성을 선택합니다. 속성 페이지 대화 상자가 나타납니다.
    
6. 속성 페이지 대화 상자의 왼쪽 속성 트리에서 구성 속성 > C/C++ > 일반을 선택합니다.
    
7. 대화 상자 오른쪽의 속성 시트에서 추가 포함 디렉터리 드롭다운 상자에서 <편집..>을 선택합니다. 추가 포함 디렉터리 대화 상자가 나타납니다.
    
8. 추가 포함 디렉터리 대화 상자 상단의 목록 상자에서 디렉터리를 찾아볼 수 있는 컨트롤이 나타날 때까지 맨 위의 빈 줄을 클릭합니다.
    
9. 이 컨트롤을 사용하여 <yourFBXSDKpath>\include 디렉터리의 전체 경로를 추가하고 확인을 클릭합니다.
    
10. 속성 페이지 대화 상자의 왼쪽 트리에서 코드 생성을 선택합니다.
    
11. 오른쪽 속성 시트에서 런타임 라이브러리 드롭다운 상자에서 프로젝트에 대한 런타임 라이브러리 유형을 선택합니다. 목록은 Visual C++ 컴파일러 옵션에 해당합니다: /MD, /MDd, /MT, /MTd 등. 모든 Visual Studio 버전에서 모든 컴파일러 옵션을 사용할 수 있는 것은 아닙니다(Windows용 FBX SDK 구성 참조).
    
12. 속성 페이지 대화 상자에서 링커 > 일반을 선택합니다.
    
13. 추가 라이브러리 종속성 드롭다운 상자에서 <편집..>을 선택합니다. 추가 라이브러리 디렉터리 대화 상자가 나타납니다.
    
14. FBX SDK 배포의 <yourFBXSDKpath>\lib 폴더에 대한 전체 경로를 입력합니다.
    
15. 속성 페이지 대화 상자에서 링커 > 입력을 선택합니다. 추가 종속성 드롭다운 상자에서 <편집>을 선택합니다. 추가 종속성 대화 상자가 나타납니다. 적절한 FBX SDK 라이브러리를 추가합니다. 사용 가능한 FBX SDK 라이브러리 파일을 설명하는 표는 Windows용 FBX SDK 구성을 참조하십시오.
    
16. 이전 단계에서 정적 링킹을 사용하는 FBX SDK 라이브러리의 디버그 버전을 선택한 경우 다음을 수행해야 합니다:
    
    - 특정 기본 라이브러리 무시 드롭다운 상자에서 <편집>을 선택합니다. 특정 기본 라이브러리 무시 대화 상자가 나타납니다.
    - LIBCMT를 입력하고 확인을 클릭합니다.
    - 추가 종속성 드롭다운 상자에서 <편집>을 선택합니다. 추가 종속성 대화 상자가 나타납니다.
    - wininet.lib를 입력하고 확인을 클릭합니다.

**참고:** FBX SDK의 동적 라이브러리 버전을 사용하는 경우 프로젝트의 전처리기 정의에 FBXSDK_SHARED를 추가하십시오.

**프로젝트의 전처리기 정의에 대한 중요 참고 사항**

FBX SDK의 동적 라이브러리 버전을 사용하는 경우 프로젝트의 전처리기 정의에 FBXSDK_SHARED를 추가하십시오. Visual Studio에서 이를 수행하려면 프로젝트에서 프로젝트 > 속성 > 구성 속성 > C/C++ > 전처리기를 선택하고 전처리기 정의 필드를 편집합니다.