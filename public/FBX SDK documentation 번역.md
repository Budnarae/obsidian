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

---

**첫 번째 FBX SDK 프로그램**

이 주제는 첫 번째 FBX SDK 프로그램에 대한 기본 개요를 제공합니다.

이 프로그램은 정적으로 링크된 버전의 FBX SDK를 사용합니다. 환경에 맞게 FBX SDK를 설치하고 구성하는 방법에 대한 추가 정보는 설치 및 구성을 참조하십시오.

다음 FBX SDK 프로그램은 다음 작업 방법에 대한 개요를 제공합니다:

- FBX SDK 메모리 관리 객체를 인스턴스화합니다. (FbxManager)
- FBX 파일의 내용을 씬으로 가져옵니다. (FbxIOSettings, FbxImporter, FbxScene)
- 씬의 요소 계층 구조를 순회합니다. (FbxScene, FbxNode, FbxNodeAttribute)
- 씬의 요소에 대한 기본 정보에 액세스하고 출력합니다. (FbxNode, FbxNodeAttribute, FbxString)

**객체 관리**

**관련 주제:** FBX SDK 관리자를 사용한 메모리 관리

FBX SDK에서 조작되는 대부분의 객체는 SDK의 메모리 관리자 객체(FbxManager)에 대한 참조와 함께 인스턴스화됩니다. 일반적으로 FBX SDK를 사용하는 프로그램에서 가장 먼저 생성되는 객체 중 하나이며, FbxManager::Create() 함수로 인스턴스화됩니다. 프로그램에는 FbxManager의 인스턴스가 하나만 필요합니다. FbxManager::Destroy() 메서드를 사용하여 FbxManager의 인스턴스가 소멸되면, 이와 함께 생성된 다른 모든 FBX SDK 객체도 소멸됩니다.

```cpp
#include <fbxsdk.h>

// ...

/**
 * 메인 함수 - 하드코딩된 fbx 파일을 로드하고,
 * 그 내용을 xml 형식으로 stdout에 출력합니다.
 */
int main(int argc, char** argv) {

    // 다음 파일명을 적절한 파일명 값으로 변경하십시오.
    const char* lFilename = "file.fbx";

    // SDK 관리자를 초기화합니다. 이 객체는 메모리 관리를 처리합니다.
    FbxManager* lSdkManager = FbxManager::Create();
```

**FBX 파일의 내용 가져오기**

**관련 주제:**

- 지원되는 파일 형식
- IO 설정
- 씬 가져오기

FBX 파일의 내용을 가져오려면 FbxIOSettings 객체와 FbxImporter 객체를 생성해야 합니다. FbxImporter 객체는 가져올 파일의 파일명과 가져오기 요구 사항에 맞게 적절히 구성된 FbxIOSettings 객체를 제공하여 초기화됩니다({ IO 설정 } 참조).

```cpp
// IO 설정 객체를 생성합니다.
FbxIOSettings *ios = FbxIOSettings::Create(lSdkManager, IOSROOT);
lSdkManager->SetIOSettings(ios);

// SDK 관리자를 사용하여 임포터를 생성합니다.
FbxImporter* lImporter = FbxImporter::Create(lSdkManager,"");

// 첫 번째 인수를 임포터의 파일명으로 사용합니다.
if(!lImporter->Initialize(lFilename, -1, lSdkManager->GetIOSettings())) {
    printf("Call to FbxImporter::Initialize() failed.\n");
    printf("Error returned: %s\n\n", lImporter->GetStatus().GetErrorString());
    exit(-1);
}
```

FbxImporter 객체는 제공된 FbxScene 객체를 FBX 파일에 포함된 요소로 채웁니다. FbxScene::Create() 함수의 두 번째 매개변수로 빈 문자열이 전달되는 것을 관찰하십시오. FBX SDK에서 생성된 객체에는 임의의 고유하지 않은 이름을 지정할 수 있으며, 이를 통해 사용자나 다른 프로그램이 내보낸 후 객체를 식별할 수 있습니다. FbxScene이 채워진 후에는 FbxImporter를 안전하게 소멸시킬 수 있습니다.

```cpp
// 가져온 파일로 채울 수 있도록 새 씬을 생성합니다.
FbxScene* lScene = FbxScene::Create(lSdkManager,"myScene");

// 파일의 내용을 씬으로 가져옵니다.
lImporter->Import(lScene);

// 파일을 가져왔으므로 임포터를 제거합니다.
lImporter->Destroy();
```

**씬 탐색**

**관련 주제:**

- FBX 씬
- FBX 노드
- FBX 노드 속성
- 두 씬 병합

FbxScene 객체는 씬 내에 존재하는 요소의 컨테이너 역할을 합니다. 가져오거나 내보낸 파일당 FbxScene 객체는 하나만 있을 수 있습니다. 씬에는 메시, 조명, 카메라, 스켈레톤, NURBS(몇 가지만 언급하자면) 등 다양한 요소가 포함될 수 있습니다. FbxScene의 요소는 FbxNode의 계층적 트리로 구성됩니다. 씬의 루트 노드는 FbxScene::GetRootNode()를 통해 액세스됩니다. 씬의 루트 노드는 씬을 파일로 내보낼 때 저장되지 않으며, 그 자식만 저장됩니다. 노드의 자식은 FbxNode::GetChild()를 통해 액세스할 수 있습니다. 마찬가지로 노드의 부모는 FbxNode::GetParent()를 통해 액세스할 수 있습니다. 개념적으로 FbxNode는 하나 이상의 씬 요소에 대한 컨테이너 역할을 합니다. 예를 들어, 씬의 한 FbxNode에는 카메라가 포함될 수 있고, 다른 FbxNode에는 메시가 포함될 수 있습니다. FBX SDK에서 메시, 조명, 카메라, 스켈레톤, NURBS, 애니메이션 커브 등과 같은 씬 요소는 FbxNodeAttribute에서 파생된 클래스로 정의됩니다. FbxNode당 둘 이상의 FbxNodeAttribute가 있을 수 있습니다.

```cpp
// 씬의 노드와 그 속성을 재귀적으로 출력합니다.
// 루트 노드는 속성을 포함해서는 안 되므로
// 출력하지 않습니다.
FbxNode* lRootNode = lScene->GetRootNode();
if(lRootNode) {
    for(int i = 0; i < lRootNode->GetChildCount(); i++)
        PrintNode(lRootNode->GetChild(i));
}
// SDK 관리자와 그것이 처리하던 다른 모든 객체를 소멸시킵니다.
lSdkManager->Destroy();
```

FbxNode는 로컬 이동(FbxNode::LclTranslation), 회전(FbxNode::LclRotation) 및 스케일링(FbxNode::LclScaling) 속성에 대한 액세스를 제공합니다. 이러한 속성은 현재 노드의 위치, 방향 및 스케일을 얻기 위해 부모 노드의 위치, 방향 및 스케일에 적용되는 변환을 나타냅니다.

```cpp
/**
 * 노드, 그 속성 및 모든 자식을 재귀적으로 출력합니다.
 */
void PrintNode(FbxNode* pNode) {
    PrintTabs();
    const char* nodeName = pNode->GetName();
    FbxDouble3 translation = pNode->LclTranslation.Get();
    FbxDouble3 rotation = pNode->LclRotation.Get();
    FbxDouble3 scaling = pNode->LclScaling.Get();

    // 노드의 내용을 출력합니다.
    printf("<node name='%s' translation='(%f, %f, %f)' rotation='(%f, %f, %f)' scaling='(%f, %f, %f)'>\n",
        nodeName,
        translation[0], translation[1], translation[2],
        rotation[0], rotation[1], rotation[2],
        scaling[0], scaling[1], scaling[2]
        );
    numTabs++;

    // 노드의 속성을 출력합니다.
    for(int i = 0; i < pNode->GetNodeAttributeCount(); i++)
        PrintAttribute(pNode->GetNodeAttributeByIndex(i));

    // 자식을 재귀적으로 출력합니다.
    for(int j = 0; j < pNode->GetChildCount(); j++)
        PrintNode(pNode->GetChild(j));

    numTabs--;
    PrintTabs();
    printf("</node>\n");
}
```

**첫 번째 프로그램**

```cpp
#include <fbxsdk.h>

/* 탭 문자("\t") 카운터 */
int numTabs = 0;

/**
 * 필요한 수의 탭을 출력합니다.
 */
void PrintTabs() {
    for(int i = 0; i < numTabs; i++)
        printf("\t");
}

/**
 * 속성 타입에 기반한 문자열 표현을 반환합니다.
 */
FbxString GetAttributeTypeName(FbxNodeAttribute::EType type) {
    switch(type) {
        case FbxNodeAttribute::eUnknown: return "unidentified";
        case FbxNodeAttribute::eNull: return "null";
        case FbxNodeAttribute::eMarker: return "marker";
        case FbxNodeAttribute::eSkeleton: return "skeleton";
        case FbxNodeAttribute::eMesh: return "mesh";
        case FbxNodeAttribute::eNurbs: return "nurbs";
        case FbxNodeAttribute::ePatch: return "patch";
        case FbxNodeAttribute::eCamera: return "camera";
        case FbxNodeAttribute::eCameraStereo: return "stereo";
        case FbxNodeAttribute::eCameraSwitcher: return "camera switcher";
        case FbxNodeAttribute::eLight: return "light";
        case FbxNodeAttribute::eOpticalReference: return "optical reference";
        case FbxNodeAttribute::eOpticalMarker: return "marker";
        case FbxNodeAttribute::eNurbsCurve: return "nurbs curve";
        case FbxNodeAttribute::eTrimNurbsSurface: return "trim nurbs surface";
        case FbxNodeAttribute::eBoundary: return "boundary";
        case FbxNodeAttribute::eNurbsSurface: return "nurbs surface";
        case FbxNodeAttribute::eShape: return "shape";
        case FbxNodeAttribute::eLODGroup: return "lodgroup";
        case FbxNodeAttribute::eSubDiv: return "subdiv";
        default: return "unknown";
    }
}

/**
 * 속성을 출력합니다.
 */
void PrintAttribute(FbxNodeAttribute* pAttribute) {
    if(!pAttribute) return;

    FbxString typeName = GetAttributeTypeName(pAttribute->GetAttributeType());
    FbxString attrName = pAttribute->GetName();
    PrintTabs();
    // 참고: FbxString의 문자 배열을 검색하려면 Buffer() 메서드를 사용하십시오.
    printf("<attribute type='%s' name='%s'/>\n", typeName.Buffer(), attrName.Buffer());
}

/**
 * 노드, 그 속성 및 모든 자식을 재귀적으로 출력합니다.
 */
void PrintNode(FbxNode* pNode) {
    PrintTabs();
    const char* nodeName = pNode->GetName();
    FbxDouble3 translation = pNode->LclTranslation.Get();
    FbxDouble3 rotation = pNode->LclRotation.Get();
    FbxDouble3 scaling = pNode->LclScaling.Get();

    // 노드의 내용을 출력합니다.
    printf("<node name='%s' translation='(%f, %f, %f)' rotation='(%f, %f, %f)' scaling='(%f, %f, %f)'>\n",
        nodeName,
        translation[0], translation[1], translation[2],
        rotation[0], rotation[1], rotation[2],
        scaling[0], scaling[1], scaling[2]
        );
    numTabs++;

    // 노드의 속성을 출력합니다.
    for(int i = 0; i < pNode->GetNodeAttributeCount(); i++)
        PrintAttribute(pNode->GetNodeAttributeByIndex(i));

    // 자식을 재귀적으로 출력합니다.
    for(int j = 0; j < pNode->GetChildCount(); j++)
        PrintNode(pNode->GetChild(j));

    numTabs--;
    PrintTabs();
    printf("</node>\n");
}

/**
 * 메인 함수 - 하드코딩된 fbx 파일을 로드하고,
 * 그 내용을 xml 형식으로 stdout에 출력합니다.
 */
int main(int argc, char** argv) {

    // 다음 파일명을 적절한 파일명 값으로 변경하십시오.
    const char* lFilename = "file.fbx";

    // SDK 관리자를 초기화합니다. 이 객체는 모든 메모리 관리를 처리합니다.
    FbxManager* lSdkManager = FbxManager::Create();

    // IO 설정 객체를 생성합니다.
    FbxIOSettings *ios = FbxIOSettings::Create(lSdkManager, IOSROOT);
    lSdkManager->SetIOSettings(ios);

    // SDK 관리자를 사용하여 임포터를 생성합니다.
    FbxImporter* lImporter = FbxImporter::Create(lSdkManager,"");

    // 첫 번째 인수를 임포터의 파일명으로 사용합니다.
    if(!lImporter->Initialize(lFilename, -1, lSdkManager->GetIOSettings())) {
        printf("Call to FbxImporter::Initialize() failed.\n");
        printf("Error returned: %s\n\n", lImporter->GetStatus().GetErrorString());
        exit(-1);
    }

    // 가져온 파일로 채울 수 있도록 새 씬을 생성합니다.
    FbxScene* lScene = FbxScene::Create(lSdkManager,"myScene");

    // 파일의 내용을 씬으로 가져옵니다.
    lImporter->Import(lScene);

    // 파일을 가져왔으므로 임포터를 제거합니다.
    lImporter->Destroy();

    // 씬의 노드와 그 속성을 재귀적으로 출력합니다.
    // 루트 노드는 속성을 포함해서는 안 되므로
    // 출력하지 않습니다.
    FbxNode* lRootNode = lScene->GetRootNode();
    if(lRootNode) {
        for(int i = 0; i < lRootNode->GetChildCount(); i++)
            PrintNode(lRootNode->GetChild(i));
    }
    // SDK 관리자와 그것이 처리하던 다른 모든 객체를 소멸시킵니다.
    lSdkManager->Destroy();
    return 0;
}
```

---

**샘플 프로그램**

FBX SDK는 지원되는 모든 플랫폼에서 실행되는 샘플 프로그램과 함께 제공됩니다.

**기능 중심 프로그램**

이러한 샘플은 FBX SDK의 특정 기능을 보여줍니다. 이러한 각 샘플의 폴더는 \<yourFBXSDKpath>\samples\에 있습니다. 각 폴더에는 샘플을 빌드하고 실행하는 데 도움이 되는 Visual Studio 프로젝트 파일(Windows만 해당) 또는 makefile(Mac OS 또는 Linux)을 생성하는 데 사용되는 CMakeList.txt 파일이 포함되어 있습니다. __샘플 프로그램 빌드 및 실행__을 참조하십시오.

**튜토리얼 프로그램**

튜토리얼 프로그램은 FBX SDK를 처음 사용하는 개발자를 대상으로 합니다. FBX SDK를 효과적으로 사용하는 방법을 설명하는 순서로 FBX 기능을 소개합니다. __튜토리얼 프로그램__을 참조하십시오.

---

**튜토리얼 프로그램**

이러한 튜토리얼 프로그램은 FBX SDK를 학습하는 프로그래머를 대상으로 합니다. 이러한 튜토리얼은 Windows에서만 실행됩니다. 각 튜토리얼 프로그램은:

- 학습자에게 적합한 순서로 FBX 기능과 요구 사항을 소개합니다.
- 실용적인 목적을 가지고 있습니다.
- 애플리케이션 내의 일반적인 워크플로를 보여줍니다.
- 의미 있는 결과를 보여줍니다.
- 이 FBX Developer Help의 다음 튜토리얼 섹션 중 하나 이상에 해당합니다:

|튜토리얼 프로그램|튜토리얼 섹션|설명|
|---|---|---|
|**Tutorial: ImportExport**|**씬 가져오기 및 내보내기**|파일을 가져오는 방법과 파일을 내보내는 방법을 보여줍니다.|
|**Tutorial: SceneTreeView**|**노드 및 씬 그래프**|FBX 씬의 모든 노드를 순회하는 방법과 각 노드의 내용을 결정하는 방법, 즉 노드에 카메라, 조명, 메시 등이 포함되어 있는지 확인하는 방법을 보여줍니다.|
|**Tutorial: CubeCreator**|**메시, 머티리얼 및 텍스처**|메시에 텍스처와 머티리얼을 추가하는 방법을 보여줍니다.|
|**Tutorial: CubeCreator**|**애니메이션**|씬에서 메시, 카메라 및 기타 객체를 애니메이션하는 방법을 보여줍니다.|

**소스 코드 및 프로젝트 파일 찾기**

이러한 각 프로그램의 폴더는 \<yourFBXSDKpath>\samples\UI Examples에 있습니다. 각 폴더에는 튜토리얼 프로그램의 소스 코드와 프로그램을 빌드하고 실행하는 데 도움이 되는 Visual Studio 프로젝트 파일이 포함되어 있습니다.

**모든 튜토리얼 프로그램에서 사용되는 공통 코드**

\<yourFBXSDKpath>\samples\UI Examples\Common 폴더에는 튜토리얼 프로그램에서 사용되는 공통 코드가 포함되어 있습니다.

**이 섹션의 페이지**

- Tutorial: ImportExport
- Tutorial: SceneTreeView
- Tutorial: CubeCreator

---

**Tutorial: ImportExport**

ImportExport 튜토리얼 프로그램은 파일을 한 파일 형식(FBX 바이너리, FBX ASCII, DAE 등)에서 다른 형식으로 변환하는 방법을 보여줍니다. 자세한 내용은 씬 가져오기 및 내보내기를 참조하십시오.

작업에는 다음이 포함됩니다:

- Visual Studio를 사용하여 샘플 프로그램을 빌드하고 실행합니다.
- SDK Manager로 메모리를 관리합니다.
- 빈 씬을 생성합니다.
- 파일 임포터를 생성합니다.
- 가져오기 파일을 씬에 로드합니다.
- 파일 익스포터를 생성합니다.
- 내보내기 파일의 파일 형식을 지정합니다.
- 미디어가 내보내기 파일에 포함되는지 여부를 지정합니다.
- 씬을 내보내기 파일로 내보냅니다.
- 정리 및 종료합니다.

**참고:** Windows에서만 빌드 및 실행됩니다.

**프로젝트 구성**

ImportExport 프로젝트는 `\<yourFBXSDKpath>\examples\UI Examples\importexport\`에 있습니다.

ImportExport에는 두 개의 소스 파일이 있습니다:

|소스 파일|설명|
|---|---|
|ImportExport.cpp|파일을 FBX가 지원하는 한 파일 형식에서 다른 형식으로 변환하는 플랫폼 독립적인 함수. 주요 로직이 있는 함수는 `ImportExport()`입니다.|
|UI.cpp|`ImportExport()`에 대한 사용자 인터페이스. 사용자 인터페이스 코드는 FBX SDK를 다운로드한 플랫폼에 따라 다릅니다. 이 소스 파일은 살펴보지 않을 것입니다.|

**사용자 인터페이스**

ImportExport 튜토리얼 프로그램의 사용자 인터페이스. Execute 버튼 옆의 큰 텍스트 상자에 메시지가 나타납니다.

**주요 로직**

ImportExport의 `ImportExport()` 함수에는 파일 변환 프로그램의 주요 로직이 포함되어 있습니다. `ImportExport()`는 다음을 수행합니다:

- 호출 프로그램(즉, UI.cpp)으로부터 다음 매개변수를 받습니다:
    - 가져올 파일의 경로 및 이름;
    - 내보낼 파일의 이름 및 경로;
    - 내보낼 파일의 파일 형식.
- 다른 FBX 객체가 사용하는 메모리를 관리하기 위해 SDK 관리자 객체를 생성합니다.
- 가져오기 파일의 데이터를 보관할 씬 객체를 생성합니다.
- 파일을 씬에 로드하기 위한 임포터 객체를 생성합니다.
- 가져오기 파일에서 씬으로 데이터를 로드합니다.
- 씬에서 내보내기 파일로 데이터를 저장합니다.
- SDK 관리자를 소멸시켜 모든 FBX 객체가 소멸되도록, 즉 SDK가 사용한 모든 메모리가 해제되도록 합니다.
- 호출 프로그램으로 제어를 반환합니다.

---

**Tutorial: SceneTreeView**

FBX 씬의 모든 노드를 순회하는 방법과 각 노드의 내용을 결정하는 방법, 즉 노드에 카메라, 조명, 메시 등이 포함되어 있는지 확인하는 방법을 보여줍니다. 자세한 내용은 __노드 및 씬 그래프__를 참조하십시오.

작업에는 다음이 포함됩니다:

- 씬의 루트 노드에 대한 참조를 가져옵니다.
- 각 자식 노드에 대한 참조를 가져옵니다.
- 양방향 관계의 양쪽 방향으로 참조를 가져옵니다.
- 노드의 속성을 공간의 한 점으로 가져옵니다.
- 노드의 속성 타입과 내용을 가져옵니다.

**참고:** Windows에서만 빌드 및 실행됩니다.

**프로젝트 구성**

SceneTreeView 프로젝트는 `\<yourFBXSDKpath>\examples\UI Examples\SceneTreeView\`에 있습니다.

SceneTreeView에는 두 개의 소스 파일이 있습니다:

|소스 파일|설명|
|---|---|
|SDK_Utility.cxx|FBX SDK를 호출하여 씬을 생성하고, 파일을 가져오고, 씬 그래프의 각 노드에서 데이터를 검색하고, 큐브에 머티리얼, 텍스처 및 애니메이션을 추가하는 플랫폼 독립적인 코드를 포함합니다. 이 튜토리얼은 이 파일의 코드 대부분을 설명합니다.|
|UI.cxx|사용자 및 Windows와 상호 작용하고, 씬 그래프를 순회하여 씬의 트리 뷰를 표시하는 코드를 포함합니다. 이 코드에는 FBX SDK에 대한 일부 호출이 포함되어 있습니다.|

**사용자 인터페이스**

SceneTreeView 샘플 프로그램은 FBX 파일을 빈 씬으로 가져온 다음 씬 그래프를 표시합니다. 씬 그래프는 더 정확하게는 트리이며, 노드 계층 구조라고도 합니다.

트리의 노드는 FBX 파일에서 가져온 씬 요소—카메라, 조명, 메시, 스켈레톤, NURBS 등—를 참조합니다. 이 트리를 표시하기 위해 SceneTreeView는 전체 트리를 순회해야 합니다. 즉, 각 노드를 방문해야 합니다.

**주요 로직**

SceneTreeView 로직:

- 사용자 인터페이스로부터 가져올 파일의 이름과 경로를 받습니다.
- 가져오기 파일을 씬에 로드합니다.
- 씬의 루트 노드에 대한 참조를 가져옵니다.

루트 노드부터 시작하여 SceneTreeView는 트리를 재귀적으로 순회합니다. 각 노드에서 SceneTreeView는:

- 노드의 이름과 속성 타입을 표시합니다.
- 노드 속성에 저장된 속성을 포함하여 노드의 선택된 속성을 표시합니다.
- 해당 노드의 각 자식에 대한 참조를 가져옵니다.

---

**Tutorial: CubeCreator**

이 튜토리얼 프로그램은 모델(이 경우 큐브)을 나타내는 메시에 텍스처, 머티리얼 및 애니메이션을 추가하는 방법을 보여줍니다. 작업에는 다음이 포함됩니다:

|상위 수준 작업|하위 수준 작업|
|---|---|
|기준 씬 구성|- 애니메이션을 포함할 애니메이션 스택 및 애니메이션 레이어 정의\<br>- 카메라에 애니메이션 추가\<br>- 초기 씬 그래프 구성|

**참고:** Windows에서만 빌드 및 실행됩니다.

**프로젝트 구성**

CubeCreator 프로젝트는 `\<yourFBXSDKpath>\examples\UI Examples\CubeCreator\`에 있습니다.

CubeCreator에는 두 개의 소스 파일이 있습니다:

|소스 파일|설명|
|---|---|
|SDK_Utility.cxx|FBX SDK를 호출하여 씬을 생성하고, 큐브를 추가하고, 큐브에 머티리얼, 텍스처 및 애니메이션을 추가하는 모든 코드를 포함합니다.\<br>이 튜토리얼은 이 파일의 코드 대부분을 설명합니다.|
|UI.cxx|씬의 트리 뷰를 표시하고 사용자와 상호 작용하는 코드를 포함합니다. 이 코드는 FBX SDK를 사용하여 UI가 트리 뷰에 표시하는 씬 데이터를 검색합니다.\<br>이 튜토리얼은 이 파일의 코드를 설명하지 않습니다.|

**사용자 인터페이스**

CubeCreator 샘플 프로그램은 씬의 모델에 텍스처, 머티리얼 및 애니메이션을 추가하는 방법을 보여줍니다.

시작 시 CubeCreator는 마커와 카메라만 포함된 씬의 트리 뷰를 표시합니다.

사용자는 씬에 큐브를 한 번에 하나씩 추가할 수 있습니다. 각 큐브에 대해 다음을 선택할 수 있습니다:

- 텍스처를 추가합니다.
- 머티리얼을 추가합니다.
- 애니메이션을 추가합니다.

씬을 FBX 파일(또는 FBX SDK에서 내보내는 모든 파일 형식)로 저장할 수 있습니다.

다음은 FBX for QuickTime에서 열었을 때 `8cubes.fbx`(위에 트리로 표시된 씬)의 모습입니다:

**런타임 시 텍스처 파일의 위치**

`<yourFBXSDKpath>\examples\UI Examples\CubeCreator\`에는 CubeCreator가 텍스처 파일로 사용하는 `crate.jpg`라는 파일이 있습니다.

이 텍스처 파일을 CubeCreator의 실행 파일이 시작될 폴더에 복사해야 합니다. CubeCreator 프로젝트의 설정을 변경하지 않는 한:

- 빌드 시 `CubeCreator.exe`는 `<yourFBXSDKpath>\bin\CubeCreator\`의 하위 디렉토리에 저장됩니다.
- 런타임 시 `CubeCreator.exe`는 동일한 디렉토리에서 실행됩니다. 해당 위치에서 텍스처 파일을 검색합니다.

FBX for QuickTime이 표면에 대한 텍스처 파일을 찾을 수 없으면 표면을 체커보드 패턴으로 렌더링합니다. 큐브의 면에 대한 모습은 다음과 같습니다:

**주요 로직**

CubeCreator는 다음 작업을 수행합니다:

- 마커, 카메라 및 조명이 포함된 기준 씬을 구성합니다.
- 카메라를 마커로 향하게 한 다음 카메라에 애니메이션을 추가합니다. 애니메이션은 항상 동일합니다: 뒤로 그리고 위로 쓸어 올리는 큐브의 뷰입니다.
- 사용자가 모든 큐브에 적용할 수 있는 하나의 머티리얼을 정의합니다.
- 모든 큐브에 적용할 수 있는 하나의 텍스처를 정의합니다.
- 모든 큐브에 적용할 수 있는 애니메이션을 정의합니다. 큐브에 적용하면 애니메이션으로 인해 큐브가 회전 축을 중심으로 회전합니다.
- 큐브를 한 번에 하나씩 추가할 수 있게 합니다. 큐브는 메시 객체입니다.
- 첫 번째 큐브를 마커 근처에 배치합니다.
- 후속 큐브를 번갈아 배치합니다: 가장 왼쪽 큐브의 왼쪽 및 위쪽, 그 다음 가장 오른쪽 큐브의 오른쪽 및 위쪽입니다.
- 각 큐브에 회전 축을 부여합니다: X, Y 또는 Z입니다.
- 사용자가 0~n개의 큐브를 추가할 수 있게 합니다. 추가된 각 큐브에 대해 머티리얼, 텍스처 및 애니메이션 중 일부 또는 전부를 추가할 수 있는 옵션이 있습니다. 씬을 FBX 파일(또는 FBX가 지원하는 다른 파일 형식)로 저장할 수 있게 합니다.
- 저장된 파일에 저장된 씬을 보고 상호 작용하기 위해 FBX for QuickTime을 사용하도록 초대합니다.