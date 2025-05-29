## 1. 우분투 시스템 패키지 업데이트
```
sudo apt-get update
```
- apt : Advanced Packaging Tool
## 2. 필요한 패키지 설치
```
sudo apt-get install apt-transport-https ca-certificates curl gnupg-agent software-properties-common
```
- apt-transport-https : 패키지 툴이 https를 통해 데이터 및 패키지에 접근가능하게 해줍니다.
- ca-certificates : ca-certificate는 certificate authority에서 발행되는 디지털 서명. SSL 인증서의 PEM 파일이 포함되어 있어 SSL 기반 앱이 SSL 연결이 되어있는지 확인할 수 있습니다
- curl : URL을 통하여 데이터를 다운로드 받을 때 사용합니다
- software-properties-common : *PPA를 추가하거나 제거할 때 사용합니다.
## 3. Docker의 공식 GPG키를 추가
```
mkdir ~/dockerGPG
cd ~/dockerGPG
curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo apt-key add -
```
- GPG키 : 비대칭 키로 암호화된 키로 유효성 검사를 하기 위한 키
## 4. Docker의 공식 apt 저장소를 추가
```
sudo add-apt-repository "deb [arch=amd64] https://download.docker.com/linux/ubuntu $(lsb_release -cs) stable"
```
## 5. 시스템 패키지 업데이트
```
sudo apt-get update
```
## 6. Docker 설치
```
sudo apt-get install docker-ce docker-ce-cli containerd.io
```

```
sudo apt-get update
sudo apt-get install apt-transport-https ca-certificates curl gnupg-agent software-properties-common
curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo apt-key add -
sudo add-apt-repository "deb [arch=amd64] https://download.docker.com/linux/ubuntu $(lsb_release -cs) stable"
sudo apt-get update
sudo apt-get install docker-ce docker-ce-cli containerd.io
```

## 7. Docker가 설치 확인
### 7-1 도커 실행상태 확인
```
sudo systemctl status docker
```
### 7-2 도커 실행
```
sudo docker run hello-world
```

## 8. 도커 관리툴 Portainer
### 8-1. 볼륨 설정
```
sudo docker volume create portainer_data
```
### 8-2. 실행
```
sudo docker run -d -p 9000:9000 -v /var/run/docker.sock:/var/run/docker.sock -v portainer_data:/data --restart=always portainer/portainer
```
