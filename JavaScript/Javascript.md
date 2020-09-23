# JavaScript 학습 내용 정리

## concat()과 spread operator([...a, b]) 의 차이점

**(link)** https://dev.to/koushikrsk/differences-of-concat-and-spread-operator-1o7#:~:text=Concat()%20will%20add%20the,generator%20return%20to%20the%20array.

- Element 가 많은 긴 Array 의 경우, **spread 는 메모리 이슈가 발생할 수 있습니다**(concat 씁시다)

---

## JS로 HTML 요소 순회하기

### Link

**(link)** https://blog.eunsatio.io/develop/Javascript%EB%A1%9C-HTML-%EC%9A%94%EC%86%8C-%EC%88%9C%ED%9A%8C%ED%95%98%EA%B8%B0

### Summary

- `Element` 객체의 프로토타입 메서드인 `querySelectorAll` 은 `NodeList` 를 반환하고, 이를 통해 NodeList 객체의 프로토타입 메서드인 `forEach` 를 이용하여 순회하는데, **ie는 NodeList 객체에 forEach 메서드를 지원하지 않습니다.(19.04.01 기준)**

- 또한 NodeList 의 사촌 격인 `HTMLCollection` (Element.prototype 의 메서드인 `getElementsByClassName`, `children` 등으로 반환된 객체) 는 아예 forEach 메서드를 지원하지 않습니다.

- 이를 해결하는 방법들은 여러 가지가 있습니다

1. 직접 반복문 작성 또는 `for of` 문 사용

```
const list = document.getElementsByClassName('.list');

for (let index = 0; index < list.length; index++) {
    console.log(list[index]);
}
또는
for (let item of list) {
    console.log(list[index]);
}
```

2. `call` 메서드로 `Array.prototype.forEach` 메서드에 바인딩 해서 사용

```
const list = document.getElementsByClassName('.list');
...
Array.prototype.forEach.call(list, (elem, index) => {
    console.log(elem, index);
});

```

3. `Array.from` 메서드 사용

```
Array.from(document.querySelectorAll(.list)).forEach((elem, index) => {
    ...
})
```

---

## JS event bubbling and capturing

### Link

**(link)** https://blueshw.github.io/2018/04/23/event-bubbling-capturing/

### Summary

---

## Object.keys/values/entries 익히기

```
let user = {
  name: "John",
  age: 30
};

Object.keys(user); // ["name", "age"]
Object.values(user);  // ["John", 30]
Object.entries(user); // [ ["name","John"], ["age",30] ]
```

---

## Array.sort() 익히기

```
var fruit = ['orange', 'apple', 'banana']; // 문자 정렬

/* 일반적인 방법 */
fruit.sort(); // apple, banana, orange

var score = [4, 11, 2, 10, 3, 1]; // 숫자 정렬

/* 오류 */
score.sort(); // 1, 10, 11, 2, 3, 4
              // ASCII 문자 순서로 정렬되어 숫자의 크기대로 나오지 않음

/* 정상 동작 */
score.sort(function(a, b) { // 오름차순
    return a - b;
    // 1, 2, 3, 4, 10, 11
});

score.sort(function(a, b) { // 내림차순
    return b - a;
    // 11, 10, 4, 3, 2, 1
});
```

---

## 화살표 함수에서 한 줄로 객체 리터럴 표현을 반환하는 방법

- 함수 본문(body)을 괄호 속에 넣음

```
params => ({foo: bar}))
```

---

## Truthy and Falsy

- 특정 값이 Truthy 한 값이라면 true, 그렇지 않다면 false 로 값을 표현하는 것을 구현하기

```
const value = { a: 1 };
const truthy = !!value;

// !value가 false가 되고 !false 가 true 가 됨.
```

---

## 단축 평가 논리 계산법

- &&와 || 연산자로 코드 단축시키기

```
console.log(true && 'hello'); // hello
console.log(false && 'hello'); // false
console.log('hello' && 'bye'); // bye
console.log(null && 'hello'); // null
console.log(undefined && 'hello'); // undefined
console.log('' && 'hello'); // ''
console.log(0 && 'hello'); // 0
console.log(1 && 'hello'); // hello
console.log(1 && 1); // 1

// A && B 에서 A가 Truthy 한 값이면 B가 결과값이 되고, A가 Falsy 한 값이면 A 가 결과값이 됨.
// A || B 는 A 가 Truthy 할 경우 결과는 A 가 된다. 반면, A 가 Falsy 하다면 결과는 B 가 된다.
```
