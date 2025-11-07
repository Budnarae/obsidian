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

