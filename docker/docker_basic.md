# Docker 기초

- 2019.03.14: 첫 작성
- 2019.03.15: 사진 자료 추가

## 가상 머신과 Docker

### Virtual Machine(VM, 가상 머신)

- 컴퓨터 안에 컴퓨터를 만드는 일
- 각각의 머신이 완벽히 고립된 상태로 서로 영향을 주지 않음
- 크게 2가지 형태로 나누어짐
  - **시스템 가상 머신**
    - 하드웨어 가상 머신이라고도 함
    - 물리 컴퓨터 다중화: 한 컴퓨터에 여러 OS 사용 가능
    - Hypervisor 가 여기 해당함
  - **프로세스 가상 머신**
    - 한 운영체제 안에서 가상 머신이 동작함
    - 독립 프로그래밍 환경 제공: 어떤 플랫폼에서나 같은 동작 실행
    - JVM 이 여기에 해당함

### Hypervisor

- Virtual Machine Monitor(VMM) 이라고도 함
- 가상 머신을 만들거나 실행할 수 있는 소프트웨어/펌웨어/하드웨어를 통칭하는 말
- 기반이 되는 컴퓨터를 Host Machine, 가상 머신을 Guest Machine 이라고 부름
![Container Diagram](https://www.docker.com/sites/default/files/d8/2018-11/docker-containerized-and-vm-transparent-bg.png)
*출처: [Docker 공식 사이트: What is a Container?](https://www.docker.com/resources/what-container)*

### Container

- Operating-system-level virtualization 이라고도 함
- 격리된 공간에서 실행되어 각 가상 머신 마다 다른 환경 제공 가능
- 가상 공간을 만들지만 실행 파일을 Host OS의 kernel 을 사용해서 실행
- OS 자원을 공유해서 용량을 절약하고 속도가 빠름

### Docker

![Docker architecture](https://docs.docker.com/engine/images/architecture.svg)
*출처: [Docker 공식 문서](https://docs.docker.com/engine/docker-overview/)*

- Git 과 같이 이미지 버전 관리 기능 있음
- 배포 및 생성에 특화됨: 어떤 실행 환경을 만들고 공유할 수 있음
- **Image**
  - 서비스 운영에 필요한 서버 프로그램, 소스 코드, 컴파일된 실행 파일을 묶은 형태
  - 베이스 이미지에서 변경 부분만 따로 이미지로 생성됨
    - 컨테이너 실행 시 베이스 이미지 + 바뀐 부분 합쳐 실행
  ![Docker Image Layer Sample](https://ouseful.files.wordpress.com/2015/08/imagelayers___a_docker_image_visualizer.png)
  *출처: [OUseful.Info, the blog…: Seven Graphical Interfaces to Docker](https://blog.ouseful.info/2015/08/10/seven-graphical-interfaces-to-docker/)*
- **Container**
  - 이미지를 실제 실행한 상태

## 출처

- [Wikipedia: Virtual machine](https://en.wikipedia.org/wiki/Virtual_machine)
- [Wikipedia: Hypervisor](https://en.wikipedia.org/wiki/Hypervisor)
- [Wikipedia: Hardware virtualization](https://en.wikipedia.org/wiki/Hardware_virtualization)
- [CIO Korea: 'SW와 HW의 분리'··· 하이퍼바이저의 이해](http://www.ciokorea.com/news/36713)
- [WEBDIR: 가상머신(Virtual Machine)의 이해](https://webdir.tistory.com/392)
- [Docker 공식 블로그: ARE CONTAINERS REPLACING VIRTUAL MACHINES?](https://blog.docker.com/2018/08/containers-replacing-virtual-machines/)
- [Docker 공식 사이트: What is a Container?](https://www.docker.com/resources/what-container)
- [Docker 공식 문서: Docker overview](https://docs.docker.com/engine/docker-overview/)

## 참고자료(개념 잡기 공부용)

- [도커 무작정 따라하기](https://www.slideshare.net/pyrasis/docker-fordummies-44424016)