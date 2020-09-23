# 짜잘한 팁들 정리

### 1. Ref 용도

hooks 에서 사용하는 `Ref` 는 DOM 에 접근하는 용도 뿐만 아니라 **화면에는 영향을 미치지 않지만 값이 바뀌는 것들** 을 표현하기 위한 용도로도 사용한다. (setTimeout, setInterval 등을 통해서 만들어진 id / 외부 라이브러리를 사용하여 만들어진 인스턴스 / scroll 위치 등의 값)

### 2. JSX 를 배열로 반환

React 에서는 배열 안에 JSX 구문을 담아서 반환하는 것도 가능하다.

### 3. useEffect 사용하여 마운트/업마운트 시 할 작업 설정하기

주로 마운트 시에 하는 작업들로는 다음과 같은 것들이 있다.

- props 로 받은 값을 컴포넌트의 로컬 상태로 설정
- 외부 API 요청 (REST API 등)
- 라이브러리 사용 (D3, Video.js 등)
- setInterval 을 통한 반복작업 또는 setTimeout 을 통한 작업 예약

언마운트 시에 하는 작업들로는

- setInterval, setTimeout 을 사용하여 등록한 작업들 clear 하기 (clearInterval, clearTimeout)
- 라이브러리 인스턴스 제거

**(규칙)** useEffect 안에서 사용하는 상태나 props 가 있다면, useEffect 의 deps에 넣어줘야 한다.

### 4. useEffect 를 마운트 말고 업데이트용으로만 사용하고 싶다면

```
const mounted = useRef(false);
useEffect(() => {
  if (!mounted.current) {
    mounted.current = true;
  } else {
    // 원하는 코드
  }
}, [요소]);
```

### 5. props 의 기본값 설정

- 전달되는 props 의 기본값을 설정할 수 있다(defaultProps)

```
const Hello = ({ name, color }) => {
  ...
};

//
Hello.defaultProps = {
  name: "이름없음",
};
```
