# Router 관련 정리

## Listening History (Router 변경 감지)

### Link

https://www.it-swarm.dev/ko/reactjs/%EB%B0%98%EC%9D%91-%EB%9D%BC%EC%9A%B0%ED%84%B0%EB%A1%9C-%EA%B2%BD%EB%A1%9C-%EB%B3%80%EA%B2%BD-%EA%B0%90%EC%A7%80/833161534/

### Summary

- `history.listen()` 함수 사용해서 경로가 변경될 때마다 감지 가능
- 위 함수는 `unlisten` 함수를 반환함. 컴포넌트가 언마운트될 때 호출해주면 됨.
