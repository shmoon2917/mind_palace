# CORS(Cross-Origin Resource Sharing) 관련 정리

## CORS 이슈

- 두 개의 다른 포트를 가지고 있는 서버는 아무 설정없이 Request 를 보낼 수 없다.
- 해결을 위해서는
  - 서버 쪽에서 따로 허용 설정을 하는 방법
  - Proxy 설정 사용
