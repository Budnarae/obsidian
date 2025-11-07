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