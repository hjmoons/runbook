# Runbook

운영 업무 중 발생한 이슈 사항 및 구축, 설정 내역 정리

## 📁 구조

### Jenkins
- **[install/](jenkins/install/)**: Jenkins 설치 및 실행 스크립트
  - systemd 없이 Jenkins를 실행하는 방법
  - Jenkins 2.462.2 버전 기준
- **[operations/](jenkins/operations/)**: Jenkins 운영 가이드
  - 에러 페이지 설정
  - SSO 연동
  - Docker Agent 설정

### Keycloak
- **[config/](keycloak/config/)**: Keycloak 설정 파일
  - cache-ispn.xml: 클러스터 캐시 설정
  - keycloak.conf: 실행 옵션
  - keycloakctl: 실행 스크립트
- **[operations/](keycloak/operations/)**: Keycloak 운영 가이드
  - 실행 및 설정 방법
  - LDAP 연동 설정
  - 클러스터 구성

### Kubernetes
- **[nginx/](kubernetes/nginx/)**: Nginx 서비스 manifest
- **[keycloak/](kubernetes/keycloak/)**: Keycloak 서비스 manifest
- **[logging/](kubernetes/logging/)**: 로깅 스택 (Grafana, Loki, Promtail)

## 🔍 빠른 검색

### Jenkins 관련
- [Jenkins 설치 방법](jenkins/install/README.md)
- [Jenkins 에러 페이지 설정](jenkins/operations/01_에러페이지설정.md)
- [Jenkins SSO 연동](jenkins/operations/02_SSO연동.md)
- [Jenkins Docker Agent](jenkins/operations/03_Docker_Agent.md)

### Keycloak 관련
- [Keycloak 실행](keycloak/operations/00_실행.md)
- [Keycloak 설정](keycloak/operations/01_설정.md)
- [Keycloak LDAP 연동](keycloak/operations/02_LDAP_연동설정.md)
- [Kubernetes Keycloak 설치](kubernetes/keycloak/install.md)

### Kubernetes 관련
- [Nginx 배포](kubernetes/nginx/)
- [Keycloak 배포](kubernetes/keycloak/)
- [Logging 스택 배포](kubernetes/logging/)

## 📝 원본 폴더

이 문서는 다음 폴더들을 통합하여 재구성한 것입니다:
- `jenkins-install/`: Jenkins 설치 스크립트
- `kubernetes/`: Kubernetes manifest 파일
- `operation-history/`: 운영 이슈 및 가이드
