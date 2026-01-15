# jenkins-install
systemd를 사용하지 못할 경우, Jenkins 실행파일을 직접 실행시킬 수 있도록 설정. rpm 설치 시 생성되는 jenkins.service 파일 (systemd 실행스크립트) 참고

### jenkins version
```
2.462.2
```

### 디렉토리 구조
```
.root
├─bin
├─log
├─war
└─workspace
```
- bin: Jenkins 실행파일 저장 경로
- log: log 파일 저장 경로
- war: web 파일 저장경로
- workspace: Jenkins Home 경로
- 위 경로들은 사용자 환경에 맞게 변경 가능

## 실행방법
### 1. User 생성
```shell
adduser jenkins # jenkins 계정 생성
passwd jenkins # 비밀번호 설정
```

### 2. 패키지 clone
```shell
git clone https://{github_url}
```

### 3. 설정
디렉토리가 위치한 절대경로로 설정 변경
##### bin/jenkins
```bash
JENKINS_HOME= # Jenkins Home (workspace) 경로
JENKINS_WAR= # Jenkins 실행파일 경로 (jenkins.war)
JENKINS_WEBROOT= # Jenkins WEB 파일 경로
LOG_HOME= # 로그 저장 경로
```

##### bin/jenkinsctl
```bash
JENKINS= # Jenkins 실행파일 경로 (jenkins.war)
LOG_DIR= # 로그 저장 경로
```

### 4. 실행
```shell
bin/jenkinsctl start # 실행
bin/jenkinsctl stop # 종료
bin/jenkinsctl status # 프로세스 확인
```