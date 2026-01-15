# Docker Agent 사용 시 권한 문제

처음 도커를 설치한 후에 일반 계정으로 도커 명령어를 날릴 경우 permission denied 문제 발생

```bash
jenkins@HyoJong:~$ docker images
permission denied while trying to connect to the Docker daemon socket at unix:///var/run/docker.sock: Head "http://%2Fvar%2Frun%2Fdocker.sock/_ping": dial unix /var/run/docker.sock: connect: permission denied
```

## 원인

도커는 root로 설치되기 떄문에 일반사용자는 실행권한이 존재하지 않는다. 하지만 도커 실행파일의 그룹권한이 docker로 설정되어 있기 때문에 도커를 사용할 계정을 docker 그룹에 포함시켜주면 된다.

### 도커 실행파일 권한 상태

```bash
jenkins@HyoJong:~$ ll /var/run/docker.sock
srw-rw---- 1 root docker 0 Dec 17 14:02 /var/run/docker.sock
```

## 그룹권한 부여 명령어

도커 명령어를 사용할 일반 계정에 docker 그룹 권한을 추가

```bash
usermod -G docker jenkins
```

## 결과

permission denied 오류는 사라지고 도커 이미지 조회 명령어가 정상적으로 실행되는 모습을 볼 수 있다. (아래는 도커 이미지가 없는 상태)

```bash
jenkins@HyoJong:~$ docker images
REPOSITORY   TAG       IMAGE ID   CREATED   SIZE
```
