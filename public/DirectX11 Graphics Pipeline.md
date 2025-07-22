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

당신은 Direct3D 11 API를 사용하여 모든 단계들을 구성할 수 있다.

Stages that feature common shader cores (the rounded rectangular blocks) are programmable by using the [HLSL](https://learn.microsoft.com/en-us/windows/desktop/direct3dhlsl/dx-graphics-hlsl) programming language.

공통 셰이더 코어(둥근 직사각형 블록)가 있는 스테이지는 HLSL 언어를 사용하여 프로그래밍할 수 있다.

As you will see, this makes the pipeline extremely flexible and adaptable.

당신이 앞으로 보게 될 것처럼, 이러한 특성은 파이프라인을 매우 유연하고 적응성 있게 만든다.

# Input-Assembler Stage

The Direct3D 10 and higher API separates functional areas of the pipeline into stages; the first stage in the pipeline is the input-assembler (IA) stage.

Direct3D 10과 그보다 높은 버전의 API는 pipeline의 기능적인 영역들을 단계(stage)들로 분할한다; 파이프라인의 첫번째 단계는 input-assembler (IA) 단계이다.

The purpose of the input-assembler stage is to read primitive data (points, lines and/or triangles) from user-filled buffers and assemble the data into primitives that will be used by the other pipeline stages.

input-assembler 단계의 목적은 

The IA stage can assemble vertices into several different [primitive types](https://learn.microsoft.com/en-us/windows/win32/direct3d11/d3d10-graphics-programming-guide-primitive-topologies) (such as line lists, triangle strips, or primitives with adjacency). New primitive types (such as a line list with adjacency or a triangle list with adjacency) have been added to support the geometry shader.

Adjacency information is visible to an application only in a geometry shader. If a geometry shader were invoked with a triangle including adjacency, for instance, the input data would contain 3 vertices for each triangle and 3 vertices for adjacency data per triangle.

When the input-assembler stage is requested to output adjacency data, the input data must include adjacency data. This may require providing a dummy vertex (forming a degenerate triangle), or perhaps by flagging in one of the vertex attributes whether the vertex exists or not. This would also need to be detected and handled by a geometry shader, although culling of degenerate geometry will happen in the rasterizer stage.

While assembling primitives, a secondary purpose of the IA is to attach [system-generated values](https://learn.microsoft.com/en-us/windows/desktop/direct3dhlsl/dx-graphics-hlsl-semantics) to help make shaders more efficient. System-generated values are text strings that are also called semantics. All three shader stages are constructed from a common shader core, and the shader core uses system-generated values (such as a primitive id, an instance id, or a vertex id) so that a shader stage can reduce processing to only those primitives, instances, or vertices that have not already been processed.

As shown in the [pipeline-block diagram](https://learn.microsoft.com/en-us/windows/desktop/direct3d10/d3d10-graphics-programming-guide-pipeline-stages), once the IA stage reads data from memory (assembles the data into primitives and attaches system-generated values), the data is output to the [vertex shader stage](https://learn.microsoft.com/en-us/previous-versions//bb205146\(v=vs.85\)).
