# GitHub Proxy 연결

내부망에서 GitHub 엔터프라이즈에 연결하기 위해서 GitHub Proxy 서버로의 연결이 필요하여 작업

## 인증서 등록

```bash
$ cp {GITHUB_PROXY_CERT} /etc/pki/ca-trust/source/anchors/
$ update-ca-trust
```

1. GitHub Proxy 서버의 인증서 파일을 서버에 저장
2. 인증서 파일을 서버의 인증서 저장 공간에 복사
3. 인증서 파일을 서버의 신뢰할 수 있는 인증서로 등록

## Jenkins 설정

Jenkins 관리 -> 시스템 설정 -> Global properties -> Environment variables -> 아래 키-값 추가

```bash
HTTP_PROXY=http://proxy.github.com
HTTPS_PROXY=http://proxy.github.com
NO_PROXY= # GitHub 이외의 git 형상관리 URL
```
