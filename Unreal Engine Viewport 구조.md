---
tags:
  - Unreal_Engine
---

_Slate_

---
  🎨 화면 영역 클래스 아키텍처 요약

  📦 계층 구조

  USlateManager (최상위 매니저)
      └─ SSplitter (레이아웃 분할기)
          ├─ SViewportWindow (뷰포트 윈도우)
          │   └─ FViewport (렌더링 영역)
          │       └─ FViewportClient (입력/렌더링 로직)
          └─ SWindow (일반 UI 패널)

  ---
  1️⃣ USlateManager - 중앙 관리자

  역할: 전체 UI 시스템의 싱글톤 매니저

  📌 주요 기능

  - 레이아웃 관리: SingleMain(단일) ↔ FourSplit(4분할) 전환
  - 입력 라우팅: 마우스/키보드 입력을 적절한 윈도우로 전달
  - 뷰포트 관리: 최대 4개의 뷰포트 생성/관리
  - 패널 관리: Details, Control 패널 등 UI 요소 관리
  - 콘솔: 오버레이 콘솔 토글 및 애니메이션

  🔑 핵심 메서드

  Initialize()         // 초기화
  SwitchLayout()      // 레이아웃 모드 전환
  Render()            // 전체 UI 렌더링
  ProcessInput()      // 입력 처리
  ToggleConsole()     // 콘솔 토글

  ---
  2️⃣ SWindow - UI 윈도우 기본 클래스

  역할: 모든 UI 요소의 베이스 클래스 (추상 클래스)

  📌 주요 기능

  - 영역 정의: FRect - 화면 좌표계에서의 위치/크기
  - 마우스 감지: IsHover() - 마우스가 영역 안에 있는지 체크
  - 가상 함수: 하위 클래스에서 구현할 이벤트 핸들러

  🔑 핵심 속성

  FRect Rect;         // 화면상 위치/크기 (Left, Top, Right, Bottom)

  🎯 상속 관계

  - SViewportWindow - 뷰포트 영역
  - SSplitter - 분할 컨테이너
  - SDetailsWindow - 디테일 패널
  - SSceneIOWindow - Scene I/O 패널

  ---
  3️⃣ SSplitter - 화면 분할기

  역할: 두 개의 자식 윈도우를 분할하는 컨테이너 (추상 클래스)

  📌 주요 기능

  - 양방향 분할: 수평/수직 분할 지원
    - SSplitterH - 좌우 분할 (Horizontal)
    - SSplitterV - 상하 분할 (Vertical)
  - 드래그 조절: 스플리터 바를 드래그하여 비율 조정
  - 비율 저장: 분할 비율을 파일로 저장/로드 (Config)

  🔑 핵심 속성

  SWindow* SideLT;        // 왼쪽/위쪽 윈도우
  SWindow* SideRB;        // 오른쪽/아래쪽 윈도우
  float SplitRatio;       // 분할 비율 (0.1 ~ 0.9)
  int SplitterThickness;  // 구분선 두께 (8px)
  bool bIsDragging;       // 드래그 중 여부

  🎯 사용 예시

  TopPanel (SSplitterH)
  ├─ LeftPanel (뷰포트 영역)
  └─ RightPanel (SSplitterV)
      ├─ ControlPanel (위)
      └─ DetailPanel (아래)

  ---
  4️⃣ SViewportWindow - 뷰포트 윈도우

  역할: 3D 씬을 렌더링하는 뷰포트 영역 (SWindow 상속)

  📌 주요 기능

  - FViewport 관리: 실제 렌더링 영역 소유
  - 툴바 제공: Gizmo 모드, ViewMode, ShowFlag 등 UI
  - 활성화 상태: bIsActive - 포커스된 뷰포트 표시
  - 뷰포트 타입: Perspective, Top, Front, Side 등

  🔑 핵심 속성

  FViewport* Viewport;              // 렌더링 영역
  FViewportClient* ViewportClient;  // 입력/렌더링 로직
  EViewportType ViewportType;       // 뷰포트 타입
  bool bIsActive;                   // 활성 상태

  🎨 툴바 기능

  - Gizmo 모드: Select, Move, Rotate, Scale
  - View 모드: Lit, Unlit, Wireframe, BufferVis
  - Show Flags: Grid, Collision, Shadow, Fog 등

  ---
  5️⃣ FViewport - 렌더링 영역

  역할: D3D11 렌더링이 실제로 일어나는 영역 (순수 C++ 클래스)

  📌 주요 기능

  - D3D11 렌더링: RTV, DSV 관리
  - 크기 조정: Resize() - 뷰포트 영역 변경
  - 입력 전달: 마우스/키보드 이벤트를 ViewportClient에 전달
  - ViewportClient 소유: 렌더링 로직 위임

  🔑 핵심 속성

  uint32 SizeX, SizeY;          // 뷰포트 크기
  uint32 StartX, StartY;        // 화면상 시작 위치
  ID3D11Device* D3DDevice;      // D3D11 디바이스
  FViewportClient* ViewportClient; // 렌더링 로직

  🔄 렌더링 흐름

  BeginRenderFrame()  // 렌더타겟 바인딩
    → Render()         // ViewportClient->Draw() 호출
  EndRenderFrame()    // 렌더링 완료

  ---
  6️⃣ FViewportClient - 뷰포트 로직

  역할: 뷰포트의 실제 렌더링 및 입력 처리 로직

  📌 주요 기능

  - 씬 렌더링: Draw() - 3D 씬 렌더링 수행
  - 카메라 관리: View Matrix 계산
  - 입력 처리: 마우스 드래그로 카메라 조작
  - 뷰포트 설정: ViewMode, ViewportType 관리

  🔑 핵심 속성

  UWorld* World;                // 렌더링할 월드
  ACameraActor* Camera;         // 카메라
  EViewportType ViewportType;   // Perspective/Top/Front/Side
  EViewMode ViewMode;           // Lit/Unlit/Wireframe

  🎮 입력 처리

  - 마우스 드래그: 카메라 회전/이동
  - 마우스 휠: 줌 인/아웃
  - Ortho 뷰: Top/Front/Side에서 2D 카메라 조작

  ---
  🔗 실제 사용 흐름

  1. 초기화

  USlateManager::Initialize()
    → SSplitter 생성 (레이아웃)
      → SViewportWindow 생성 (4개)
        → FViewport 생성
          → FViewportClient 생성

  2. 입력 처리

  USlateManager::ProcessInput()
    → SSplitter::OnMouseMove()
      → SViewportWindow::OnMouseMove()
        → FViewport::ProcessMouseMove()
          → FViewportClient::MouseMove()

  3. 렌더링

  USlateManager::Render()
    → SSplitter::OnRender()
      → SViewportWindow::OnRender()
        → FViewport::Render()
          → FViewportClient::Draw()
            → 실제 3D 씬 렌더링

  ---
  📊 클래스 책임 요약

  | 클래스             | 계층     | 책임                    |
  |-----------------|--------|-----------------------|
  | USlateManager   | 최상위    | 전체 UI 시스템 관리, 레이아웃 전환 |
  | SWindow         | 베이스    | UI 윈도우 공통 속성 (위치, 크기) |
  | SSplitter       | 컨테이너   | 화면 분할, 드래그 조절         |
  | SViewportWindow | UI 윈도우 | 뷰포트 영역, 툴바 제공         |
  | FViewport       | 렌더링    | D3D11 렌더링 영역, 입력 전달   |
  | FViewportClient | 로직     | 씬 렌더링, 카메라 조작         |

  ---
  이렇게 계층적 분리를 통해 각 클래스가 명확한 책임을 가지며, Unreal Engine의 Slate 시스템을 모방한 구조입니다!