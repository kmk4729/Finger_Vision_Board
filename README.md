# Finger_Vision_Board

Winter 2023 Hyper Robotics ROS2 Project  
(Original: [sendoru/hyper-2023-winter-ros2](https://github.com/sendoru/hyper-2023-winter-ros2))

---

## 📌 프로젝트 개요

이 프로젝트는 **Intel RealSense 카메라와 ROS2 Foxy** 환경을 기반으로,  
이미지 스트림을 퍼블리시하고, 실시간 비전 데이터를 활용하는 ROS2 패키지 예제입니다.  
주요 목적은 로봇 비전 센서의 데이터 획득, 처리, 전송 파이프라인을 실습하고  
향후 로봇 손가락(Manipulator) 비전 보드 개발에 적용하는 것입니다.

---

## 🛠️ 개발 환경 및 의존성

- **OS**: Ubuntu 20.04 LTS
- **ROS2 Distro**: Foxy Fitzroy
- **필수 패키지**
  - [realsense-ros](https://github.com/IntelRealSense/realsense-ros) (Intel RealSense 카메라 ROS2 Wrapper)
  - OpenCV2
- **라이선스**: Apache 2.0

---

## 🚀 주요 기능 및 코드 구조

- **img_publisher**  
  - OpenCV를 이용해 이미지 파일 또는 카메라 스트림을 ROS2 토픽으로 퍼블리시합니다.
  - 실시간 영상 데이터를 로봇 시스템에 전송할 수 있습니다.

- **realsense_publisher**  
  - Intel RealSense 카메라에서 RGB/Depth 이미지를 받아 ROS2 토픽으로 퍼블리시합니다.
  - 다양한 로봇 비전 실험 및 응용에 활용 가능합니다.

- **공통**  
  - ROS2 노드로 동작하며, 토픽 이름과 QoS 설정 등은 코드 내에서 쉽게 조정할 수 있습니다.
  - Ctrl+C로 프로세스가 정상 종료되지 않는 이슈가 있음(TODO 참고).

---

## ⚙️ 설치 및 실행 방법

1. **레포지토리 클론**
    ```
    cd <your_ros2_ws>/src
    git clone https://github.com/kmk4729/Finger_Vision_Board.git
    ```

2. **의존성 설치**
    ```
    sudo apt update
    sudo apt install ros-foxy-vision-opencv ros-foxy-image-transport
    # RealSense ROS2 Wrapper 설치
    cd <your_ros2_ws>/src
    git clone https://github.com/IntelRealSense/realsense-ros.git
    cd ..
    colcon build
    source install/setup.bash
    ```

3. **노드 실행 예시**
    ```
    ros2 run finger_vision_board img_publisher
    ros2 run finger_vision_board realsense_publisher
    ```

---

## 📝 TODO 및 참고 사항

- `img_publisher`, `realsense_publisher` 노드에서 Ctrl+C로 정상 종료되지 않는 이슈가 있습니다.
- README를 더욱 보기 좋게 꾸미는 작업이 필요합니다.
- 실시간 비전 데이터를 활용한 로봇 손가락 제어, 객체 인식 등으로 확장 가능합니다.

---

## 💡 확장 아이디어

- **Finger Vision Board**로 실제 로봇 손가락(Manipulator) 비전 피드백 제어에 적용
- YOLO, OpenPose 등 딥러닝 기반 객체 인식 연동
- Gazebo, RViz2 등 시뮬레이션 환경에서의 비전 테스트
- 다양한 센서(Depth, IR 등) 데이터 통합

---

## 📂 폴더 구조 예시

Finger_Vision_Board/
├── img_publisher/ # 이미지 퍼블리셔 노드
├── realsense_publisher/ # RealSense 퍼블리셔 노드
├── test/ # 테스트 코드 및 스크립트
├── README.md
└── LICENSE

text

---

## 📮 문의 및 기여

- 질문, 버그 제보, 기여는 [Issues](https://github.com/kmk4729/Finger_Vision_Board/issues)로 남겨주세요.

---

## License

Apache 2.0