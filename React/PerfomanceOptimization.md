# 성능 최적화 관련 정리

## React 성능 최적화: React.memo 와 useCallback, 함수형 업데이트

### Link

**(main)** https://darrengwon.tistory.com/608?category=858368
(sub) https://ui.toast.com/weekly-pick/ko_20190731/#:~:text=React.memo()%20%EC%9D%80%20%EC%84%B1%EB%8A%A5,%EC%A0%9C%EC%9D%B4%EC%85%98%EC%97%90%20%EC%9D%98%EC%A1%B4%ED%95%98%EB%A9%B4%20%EC%95%88%EB%90%9C%EB%8B%A4.
(sub) https://velog.io/@yejinh/useCallback과-React.Memo을-통한-렌더링-최적화

### Summary

- 리스트를 렌더링 할 때는

1. React.memo 를 통해 리스트 아이템과 리스트를 감싸줘서 props 가 동일하면 리렌더링이 되는 것을 방지하고,
2. 인라인 함수들(대개 onClick, onSubmit 등)을 useCallback 으로 감싸줘야 하며(함수가 새로 계속 생성되기 때문에 자식 쪽에서 리렌더링 발생함)
3. setState 를 이용하여 새로운 state 를 반영할 시 그 업데이트는 함수형 업데이트로 이뤄져야 한다.

- 퍼포먼스 측정을 위해서는 profiling 을 사용하면 된다(in Chrome)

---

## setState 를 함수형으로 사용하기

### Link

**(main)** https://medium.com/@saturnuss/setstate-%EB%A5%BC-%ED%95%A8%EC%88%98%ED%98%95%EC%9C%BC%EB%A1%9C-%EC%82%AC%EC%9A%A9%ED%95%98%EA%B8%B0-763402cbc3e5

### Summary

- 함수형으로 사용하여야 리액트의 비동기 상태 업데이트 방식(batching)에 영향을 받지 않는다.

- 함수형으로 작성하면 컴포넌트 외부에 선언해놓고 가져다 쓸 수 있다. **테스트도 쉬워지고 계속 새로운 함수를 생성하지 않아도 된다.**
