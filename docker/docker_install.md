# DOCKER 설치

2019.03.20

## 설치 환경

- Server: AWS EC2 free tier
- OS: Ubuntu 18.04

## 설치 과정

- Docker CE(Community Edition) 기준
- apt 사용해서 설치

```bash
# 패키지들과 그 버전들의 리스트 업데이트
sudo apt-get update

# HTTPS 저장소를 사용하기 위한 패키기 설치
sudo apt-get install \
    apt-transport-https \
    ca-certificates \
    curl \
    gnupg-agent \
    software-properties-common

# Docker GPG Key 추가
curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo apt-key add -
# OK 가 나오면 성공

# 받아온 키 등록 - 이제 docker 를 저장소에서 설치할 수 있게 됨
sudo apt-key fingerprint 0EBFCD88
# 다시한번 패키지 리스트 업데이트
sudo apt-get update
# Docker CE 설치
sudo apt-get install docker-ce docker-ce-cli containerd.io
# Hello world 실행
sudo docker run hello-world
```

## 출처

- [Docker 공식 문서: Get Docker CE for Ubuntu](https://docs.docker.com/install/linux/docker-ce/ubuntu/)
- [꿈꾸는 사람 블로그: apt-get update에서 발생하는 GPG public key 오류 해결 방법.](https://dreamlog.tistory.com/76)