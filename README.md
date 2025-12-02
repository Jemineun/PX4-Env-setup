# PX4-SITL-Environment-Setup

드론제어 알고리즘을 하드웨어 없이 안전한 환경에서 테스트를 진행하기 위해서 환경을 구축하게 되었다.

## Tech Stack (사용 기술) 
- OS: windows11(WSL2 - Ubuntu22.04)
- Simulator: Gazebo Classic 11
- Firmware: PX4 Autopilot v1.14.0
- Language: Python 3.10 (예정)

## Demo(실행 화면)
![Demo Image](./demo_capture.png)

## Key Features (구현 기능)
1. SITL 환경구축: 리눅스 환경에서 툴체인 및 빌드 환경 직접 구성
2. 자동 이착륙 제어: MAVLink 프로토콜을 이용한 Arming, Takeoff, Landing 시퀀스 구현
3. 상태 모니터링: 비동기 통신으로 드론의 연결 상태 실시간 확인

## Trouble Shooting (문제 해결 기록)
문제1: Gazebo 실행 시 화면이 바로 꺼지는 문제 발생
- 원인: WSL2 환경에서의 그래픽 렌더링(GPU) 호환성 문제
- 해결: 'export LIBGL_AlWAYS_SOFTWARE=1' 환경변수를 설정하여 CPU 렌더링으로 전환하여 해결함.

문제2: 최신 PX4 버전과 Gazebo 버전 불일치
- 원인: main 브렌치의 업데이트로 Gazebo Classic 지원이 중단됨.
- 해결: 안정적인 학습을 위해 'git checkout v1.14.0'으로 버전을 고정하고 서브모듈을 재설정함.