---
tags:
  - directX11
  - translation
---

The Direct3D 11 programmable pipeline is designed for generating graphics for realtime gaming applications.

Direct3D 11의 프로그래밍 가능한 파이프라인은 실시간 게임 실행프로그램을 위한 그래픽을 생성하기 위해 설계되었다.

This section describes the Direct3D 11 programmable pipeline.

이 단락은 Direct3D 11의 프로그래밍 가능한 파이프라인을 서술한다.

The following diagram shows the data flow from input to output through each of the programmable stages.

다음의 다이아그램은 각 프로그래밍 가능한 단계의 입력과 출력을 넘나들며 데이터가 흐르는 것을 보여준다.

![[f36ecbf65050e43f57b2dd24838b5f56_MD5.jpg]]

The graphics pipeline for Microsoft Direct3D 11 supports the same stages as the [Direct3D 10 graphics pipeline](https://learn.microsoft.com/en-us/windows/desktop/direct3d10/d3d10-graphics-programming-guide-pipeline-stages), with additional stages to support advanced features.

마이크로소프트 Direct3D의 그래픽스 파이프라인은 Direct3D 10의 그래픽스 파이프라인과 동일한 단계들을 제공하며, 몇몇 발전된 특성들을 제공하기 위한 추가적인 단계들이 있다.

You can use the Direct3D 11API to configure all of the stages.

당신은 Direct3D 11 API를 사용하여 모든 단계들을 configure

Stages that feature common shader cores (the rounded rectangular blocks) are programmable by using the [HLSL](https://learn.microsoft.com/en-us/windows/desktop/direct3dhlsl/dx-graphics-hlsl) programming language. As you will see, this makes the pipeline extremely flexible and adaptable.
