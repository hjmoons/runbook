# Jenkins Error 페이지 설정

Jenkins를 사용할 때 내장되어 있는 웹서버를 사용할 경우, 401/403/404 에러 발생 시 Jetty의 버전 정보가 노출되어 해당 정보가 출력되지 않도록 수정이 필요했다.

## Jenkins Version

```bash
2.289.1
```

## 조치방법

### web 설정 경로

웹설정관련 파일이 위치한 경로

```bash
# CentOS 7, Jenkins WEB_ROOT 경로 (Default)
/var/cache/jenkins/war
```

### error page 생성

```bash
mkdir /var/cache/jenkins/war/error
vi error_404.html # 404 에러 발생시 나타낼 페이지 생성
```

### error page 설정

web 설정 파일에 에러코드에 맞는 html 파일 경로 매핑 설정 추가

- WEB_INF/web.xml

```xml
  <error-page>
    <error-code>404</error-code>
    <location>/error/error_404.html</location>
  </error-page>
  ```

### Jenkins 재기동

```bash
sudo systemctl restart jenkins
```
