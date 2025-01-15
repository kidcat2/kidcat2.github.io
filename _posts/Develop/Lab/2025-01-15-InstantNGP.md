---
title: "[3D Reconstruction] Instant NGP 실행해보기"
date: 2023-07-14 +0000
categories: [Develop, Lab]
tags: [DeepLearning, Computer Graphics, Computer Vision]
math: true
published : true
---

# 실행 가이드

1. [링크1](https://www.youtube.com/watch?v=C9JHhkDJSpM&t=844s)
2. [링크2](https://ikaros79.tistory.com/entry/Instant-NGP-01-Windows%EC%97%90%EC%84%9C-%EC%84%A4%EC%B9%98%ED%95%98%EA%B8%B0)
3. [링크3](https://yongbba.tistory.com/56)

1번은 전체적인 실행 과정을 보여주는 영상이고, 2~3번은 Window에서 실행 방법과 WSL 설치에 대한 내용이다.

![Desktop View](/assets/img/Lab/NGP1.png){:style="border:1px solid #eaeaea; border-radius: 7px; padding: 0px;" .w-75 .normal}

Instant NGP Github의 환경 설정에 대한 내용이다.

`C++14↑`, `Visual Studio 19,22`, `CUDA 11.5↑`, `CMake 3.21↑` 까지는 필수라고 하는데, `Optix` 까지는 설치하는 것이 좋다

참고로 `Visual Studio 22` 를 사용한다면 `CUDA 11.6` 이상 설치해야 한다. `CUDA 11.5` 는 22를 지원하지 않는다(23.9.10기준)

전체적인 설치 과정은 영상과 [github](https://github.com/NVlabs/instant-ngp) 를 참고하면 된다. 

# 오류 

1. `testbed.exe` 

예전 Instant-NGP Github에서는 `build` 후 실행 파일명이 `testbed.exe` 였기 때문에 발생하는 문제이다. 
지금은 `instant-ngp.exe` 로 변경되었기 때문에 아래와 같이 입력해주면 된다.

```sh
/build/instant-ngp --scene data/nerf/fox 또는
/build/instant-ngp --scene ./data/nerf/fox
```

2. `WSL Error: 0x80370102`  오류

`WSL` 설치 시 본인 컴퓨터의 `BIOS` 가상 환경 설정이 Disable 로 되어있는 경우라면 설치가 되지 않는다. 
[링크](https://velog.io/@jaylnne/WSL-Error-0x80370102-%ED%95%B4%EA%B2%B0)에 자세한 해결 방법이 나와있다.

3. `cmake --build build --config RelWithDebInfo -j` 실행 시 발생하는 오류

VS는 2022 인데 CUDA가 11.5일 경우 발생하는 오류이다. 11.6으로 바꿔서 설치해주면 해결된다.

4. `"CMakeCUDACompilerId.cu" failed.` 오류

정확한 오류 메시지는 아래와 같다.

```sh
CMake Error at /usr/share/cmake-3.22/Modules/CMakeDetermineCompilerId.cmake:726 (message):
Compiling the CUDA compiler identification source file
"CMakeCUDACompilerId.cu" failed.
Compiler: /usr/bin/nvcc
```

CUDA Compiler를 찾지 못하거나 CUDA가 여러개 깔려있을 경우 발생한다.
CUDA 컴파일러를 명시적으로 지정해주면 된다.[링크](https://github.com/NVlabs/instant-ngp/issues/923)

```sh
-D CMAKE_CUDA_COMPILER=$(which nvcc)
cmake . -D TCNN_CUDA_ARCHITECTURES=86 -D CMAKE_CUDA_COMPILER=$(which nvcc) -B build
```