---
title: "총싸움 ET 프로젝트 Log"
date: 2025-03-21 +0800
categories: [Book]
tags: [Book, Book review]
published: false
---

모작 게임 : https://www.youtube.com/watch?v=7gsfjYKVV2M


2025.03.21. 제작 시작

1. 모델링 & Mixamo
- Mixamo Animation 적용하기 : https://papabee.tistory.com/515

2025.04.07 케릭터 애니메이션 만들기

1. Mixamo 모델링
- fbx file 
    > Rig : Humanoid,  Avatar Definition : Creat From this Model, Copy Model
    > Animation 이름 변경

2. Moving Animator
    - Project > 우클릭 > Create > Animator Controller
    - Mixamo Animation Clip 넣기
    - 상태 전이
    - Parameter 설정

    각 Parameter 타입 설명과 사용 예시

    Trigger	: 한 번만 발동되는 "신호", ex : 죽음(Die), 총쏘기(Shoot), 점프(Jump) 등 `단발성` 행동
    Bool : 참/거짓,	ex : 뛰고 있는가?, 땅에 있는가?, 공격 중인가?
    Int : 정수 값, ex :  상태 구분	공격 패턴 1~3, 방향 구분 등
    Float : 부동소수값, ex : 주로 속도/거리/각도에 사용	이동 속도, 거리 기반 애니메이션 블렌딩 등

    - transition 화살표 클릭 후 conditions 를 통해 설정
    - Has Exit time : 종료 시점 활성화, 즉시 전이 할것인지 천천히, 
    - Transition Duration : 현재 애니메이션 클립과 나중 애니메이션 클립 섞어서 자연스럽게 할 것인지의 시간 결정

3. PlayerController
    > Logic
        Jump : E + 좌클릭
        Attack : A + 좌클릭
        Run : 우클릭한 장소로
        Idle : 평소 상태
        Die : 죽었을 때

    Q1. 우클릭한 지점으로 이동하기 (https://www.youtube.com/watch?v=7eAwVUsiqZU)
        - Unity Navigation System 사용
            - NavMesh : 에이전트가 걸어 다닐 수 있는 곳
            - NavMesh Agent : NavMesh 위에서 경로를 계산하고 이동하는 주체(캐릭터, 컴포넌트, 오브젝트), 경로는 Unity Navigation에서 최적의로 계산해준다.
            - NavMesh Obstacle : Agent가 가지 못하는 곳 (벽, 이동 제한..) 
            - Off Mesh Link : 끊어진 NavMesh 영역들을 잇는 연결 지점, `뛰어넘을 수 있는 울타리나 타고 올라갈 수 있는 담벼락 구현에 사용`
            - NavMesh는 실시간으로 (Q,W,E,R) 등으로 움직이는 플레이어에는 잘 사용되지 않고, NPC, AI, 몬스터 등에 자주 사용됨.
        - 내가 마우스 클릭한 위치는 스크린 좌표계이기 때문에 월드 좌표계로 변환한 위치를 사용해야 되는 것을 고려해야 함.

        - NavMesh 굽기
            - Window > AI > Navigation
            - NavMesh 할 Object 선택 
            - Object
                - Static : 해당 오브젝트가 움직이지 않는다.
                - Navigation Area : 상황에 맞게 설정

        - 애니메이션 
            - Idle : Loop Time 설정
            - Running : Loop Time 설정

        - P1. 목적지에 도착하지 않고 빙글빙글 도는 현상
            > Stopping Distance 값을 증가
            > Distance 값을 증가시키면, 너무 목표한 위치로부터 먼 곳에 멈추고 낮추면 빙글빙글 돈다. >...
        - P2. 방향 전환을 하는 경우 최단거리가 아니라 원을 그리며 이동하는 현상
            > Angular speed 증가로 해결

        
    Q2. 높이가 다른 영역을 점프로 넘어갈 때 어떻게 구현해야 할까?


