# GitHub Proxy 연결

내부망에서 GitHub 엔터프라이즈에 연결하기 위해서 GitHub Proxy 서버로의 연결이 필요하여 작업

## 인증서 등록

### 1. GitHub Proxy 인증서 파일을 서버에 저장

### 2. 인증서를 신뢰할 수 있는 인증서로 등록

```bash
cp {GITHUB_PROXY_CERT} /etc/pki/ca-trust/source/anchors/
update-ca-trust
```

- `{GITHUB_PROXY_CERT}`: GitHub Proxy 서버의 인증서 파일 경로
- 인증서 파일을 시스템의 신뢰할 수 있는 인증서 저장소에 복사 및 등록

## Jenkins 설정

### Proxy 환경 변수 설정

**Jenkins 관리** → **시스템 설정** → **Global properties** → **Environment variables**

아래 환경 변수 추가:

| Key | Value | 설명 |
|-----|-------|------|
| `HTTP_PROXY` | `http://proxy.github.com` | HTTP 프록시 서버 주소 |
| `HTTPS_PROXY` | `http://proxy.github.com` | HTTPS 프록시 서버 주소 |
| `NO_PROXY` | (GitHub 이외의 git 형상관리 URL) | 프록시를 사용하지 않을 주소 목록 |
