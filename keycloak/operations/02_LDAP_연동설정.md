# Keycloak <> LDAP 연동 설정

keycloak에서 LDAP 데이터를 연동하기 위해서 인증서 설치 후에 테스트를 진행하면 오류 발생

## 조치사항

- 인증서를 설치한 JVM 경로를 keycloak이 찾을 수 있도록 경로 지정이 필요
- 경로 정보를 keycloak.conf 파일에 추가
- 추가 후 keycloak 재기동

```bash
...
# LDAP Certification Setting
https-trust-store-file=$JAVA_HOME/lib/security/cacerts
https-trust-store-password=$CERT_PASSWORD_SETTING
...
```
