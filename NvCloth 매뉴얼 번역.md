---
tags:
  - translation
  - graphics
---

_NvCloth_

---

# Compiling¶  

---

[원문](https://nvidiagameworks.github.io/NvCloth/1.1/Compiling/index.html)

---

CMake은(는) Android를 제외한 모든 플랫폼에서 NVIDIA의 packman 스크립트를 사용하여 자동으로 획득됩니다. 인터넷 연결이 필요합니다.

Windows¶  
Windows의 경우: 아래 의존성들을 다운로드하여 설치하세요:

- Visual Studio 12 이상(2013 이상)
    
- Windows 8.1 SDK [https://developer.microsoft.com/en-us/windows/downloads/windows-8-1-sdk](https://developer.microsoft.com/en-us/windows/downloads/windows-8-1-sdk)
    
- CUDA SDK [https://developer.nvidia.com/cuda-downloads](https://developer.nvidia.com/cuda-downloads) (버전 8 이상)
    

`scripts/locate_cuda.bat`을 편집하여 `bin`, `include`, `lib` 폴더를 포함하는 CUDA 설치 폴더를 가리키도록 설정하고, `scripts/locate_win8sdk.bat`을 편집하여 Windows SDK를 가리키도록 설정하세요(기본값: `C:\Program Files (x86)\Windows Kits\8.1`).

`CmakeGenerateAll.bat`를 실행하여 `compiler/vcXXwinXX-cmake/`에 Visual Studio 솔루션 파일들을 생성하세요. 예를 들어 Visual Studio 2015, 64-bit 대상 프로세서용 솔루션은 `compiler/vc14win64-cmake/` 폴더에 생성됩니다. 그런 다음 `NvCloth.sln`을 열고 Release/Debug 구성 중 하나를 선택하여 솔루션을 빌드하세요. 라이브러리 바이너리는 `compiler` 폴더 옆의 `bin` 폴더에 배치됩니다.

위의 프로젝트 생성 스크립트는 CUDA/DX11 솔버를 활성화할지 제어하는 선택적 명령행 인자를 제공합니다:

```
CmakeGenerateProjects.bat <0|1:use_cuda (default is 1)> <0|1:use_dx11 (default is 1)>
```

예:

```
CmakeGenerateProjects.bat 1 0
```

는 컴파일에 CUDA 솔버를 포함하지만 DX11 솔버는 제외합니다.

샘플의 Visual Studio 솔루션 파일을 생성하려면 `samples/CmakeGenerateProjects.bat`를 실행하세요 — 생성된 파일은 `samples/compiler/vc14winXX-cmake/CmakeGenerateProjects.bat`에 위치합니다. 샘플을 빌드하기 전에 assimp를 먼저 빌드해야 합니다. 예를 들어 `E:\nx0\sw\devrel\libdev\NvCloth\trunk\samples\external\assimp-4.1.0`을 실행한 뒤 `samples\external\assimp-4.1.0\compiler\vc14winXX-cmake\Assimp.sln`을 빌드하세요.

Linux¶  
`GenerateProjectsLinux.sh`를 실행하면 `compiler/linux64-XXXXX-cmake/`에 make 파일들이 생성됩니다.

CUDA 지원을 활성화/비활성화하려면 배포판에 포함된 `BuildProjectsLinux.sh` 스크립트에서 다음 줄을 변경하세요:

```
export USE_CUDA=0 # 0 for disable 1 for enable
```

`BuildProjectsLinux.sh` 스크립트를 실행하면 `compiler` 폴더에 다양한 makefile 기반 프로젝트가 생성됩니다. 필요한 디렉터리를 선택한 뒤 예를 들어 다음과 같이 빌드하세요:

```
cd compiler/linux64-release-cmake
```

그런 다음 (병렬 5개 프로세스로) 빌드 과정을 실행합니다:

```
make --jobs=5
```

라이브러리 바이너리는 `compiler` 폴더 옆의 `bin` 폴더에 배치됩니다.

참고: Linux 프로젝트 생성 스크립트 `GenerateProjectsLinux.sh`를 실행했을 때 다음과 같은 오류가 발생하면:

```
env: bash\r: No such file or directory
```

다음 명령으로 줄바꿈(라인엔딩)을 수정하면 됩니다:

```
sed $'s/\r$//' GenerateProjectsLinux.sh > GenerateProjectsLinux.sh.fixed && mv GenerateProjectsLinux.sh.fixed GenerateProjectsLinux.sh && chmod +x GenerateProjectsLinux.sh
```

또는 선호하는 텍스트 에디터를 사용하세요.

Mac¶  
`GenerateProjectsOsx.sh`를 실행하면 `compiler` 폴더에 Xcode 기반 프로젝트(32-bit 및 64-bit)가 생성됩니다. 필요한 프로젝트를 선택하세요. 예:

```
cd compiler/osx64-cmake
```

프로젝트를 Xcode에서 열어 IDE 내에서 빌드하거나, 대신 `BuildProjectsOsx.sh`를 사용하여 명령행에서 전체를 빌드할 수 있습니다.

라이브러리 바이너리는 `compiler` 폴더 옆의 `bin` 폴더에 배치됩니다.

참고: Mac 프로젝트 생성 스크립트 `GenerateProjectsOsx.sh`를 실행했을 때 다음과 같은 오류가 발생하면:

```
env: bash\r: No such file or directory
```

다음 명령으로 줄바꿈(라인엔딩)을 수정하세요:

```
sed $'s/\r$//' GenerateProjectsOsx.sh > GenerateProjectsOsx.sh.fixed && mv GenerateProjectsOsx.sh.fixed GenerateProjectsOsx.sh && chmod +x GenerateProjectsOsx.sh
```

iOS¶  
`GenerateProjectsIOS.sh`를 실행하면 `compiler/ios-cmake` 폴더에 Xcode 기반 프로젝트가 생성됩니다. 생성이 완료되면 Xcode에서 프로젝트를 열고 IDE 내에서 빌드하세요.

기본 iOS 배포 대상 버전은 8.0입니다(프로젝트 생성기 스크립트 내에서 변경할 수 있습니다).

또는 `BuildProjectsIOS.sh`를 사용하여 명령행에서 모든 것을 빌드할 수도 있습니다.

Android¶  
CMake 3.7을 [https://cmake.org/download/](https://cmake.org/download/) 에서 다운로드하여 설치하세요. `scripts/locate_cmake.bat`을 편집하여 CMake 실행 파일을 가리키도록 설정합니다.

NDK는 [https://developer.android.com/ndk/downloads/index.html](https://developer.android.com/ndk/downloads/index.html) 에서 다운로드하세요(테스트된 버전: r15c, r13b, r12b). `ANDROID_NDK_ROOT` 환경 변수를 NDK 루트 폴더를 가리키도록 설정하세요. 프로젝트 생성 스크립트를 실행합니다:

```
CmakeGenerateAndroid.bat release
```

CMake가 PATH에 있어야 합니다.

다음으로 `compiler\android-arm64-v8a-release-cmake` 폴더로 이동하여 다음을 실행하세요:

```
cmake --build .  -- -j5
```

라이브러리 바이너리는 `compiler` 폴더 옆의 `bin` 폴더에 배치됩니다.

참고: CMake를 사용해 Android 바이너리를 빌드하려면 NDK 내 특정 폴더가 필요한 바이너리를 가리키도록 되어 있어야 합니다. 구체적으로 다음의 심볼릭 링크(또는 복사/이름 변경)를 생성해야 할 수 있습니다:

```
<path_to_android_ndk>/toolchains/aarch64-linux-android-4.9/prebuilt/windows
```

를 다음으로:

```
<path_to_android_ndk>/toolchains/aarch64-linux-android-4.9/prebuilt/windows-x86_64
```

신규 NDK 버전에서는 이 작업이 필요하지 않을 수도 있으나 일부 버전에서는 필요할 수 있습니다.

---

