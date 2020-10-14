# dcm4chee-arc-light 5.22.3

## 실행


```sh
$docker-compose stop
$docker-compose rm
$rm -rf ./dcm4chee-arc
$mkdir -p ./dcm4chee-arc/logstash && touch ./dcm4chee-arc/logstash/filter-hashtree && sudo chown 1000:1000 dcm4chee-arc/logstash/filter-hashtree
$docker-compose up
```

## NOTE

### OIDC 클라이언트 등록

Keycloak 으로 인증을 수행하며, 반드시 OIDC 클라이언트를 등록해주어야 함

  1. [Register the Archive UI as OIDC client in Keycloak as described in Run secured archive services on a single host](https://github.com/dcm4che/dcm4chee-arc-light/wiki/Run-secured-archive-services-on-a-single-host#register-the-archive-ui-as-oidc-client-in-keycloak)
  1. (Optional) [Register the WildFly Administration Console as OIDC client in Keycloak as described in Run secured archive services on a single host](https://github.com/dcm4che/dcm4chee-arc-light/wiki/Run-secured-archive-services-on-a-single-host#register-the-wildfly-administration-console-as-oidc-client-in-keycloak)
  1. (Optional) Register Keyclock Gatekeeper as OIDC client in Keycloak

### localhost 를 사용하지 말 것

keycloak 의 정책으로 인해, localhost(127.0.0.1) 을 호스트 주소로 사용할 수 없다.

이를 회피하기 위해, docker 가 설치되면 기본으로 생성되는 Bridge 인터페이스의 주소인 172.17.0.1 을 기본 주소로 설정하였다.

### 서비스의 주소

* Archive UI (PACS): https://172.17.0.1:8443/dcm4chee-arc/ui2/
* Wildfly Console: https://172.17.0.1:9993/console
* Keycloak: https://172.17.0.1:8843/auth/admin/dcm4che/console
* E.L.K Stack: <OIDC 등록이 필요함>

## SEE ALSO

* [Run secured archive services and Elastic Stack on a single host](https://github.com/dcm4che/dcm4chee-arc-light/wiki/Run-secured-archive-services-and-Elastic-Stack-on-a-single-host)
