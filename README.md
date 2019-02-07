# functional_es6
함수형 프로그래밍과 JavaScript ES6+ 인프런 강좌 정리 (https://www.inflearn.com/course/functional-es6/)

## 평가와 일급

### 평가

코드가 계산(Evaluation) 되어 값을 만드는 것

### 일급

- 값을 다룰 수 있다.
- 변수에 담을 수 있다.
- 함수의 인자로 사용 될 수 있다.
- 함수의 결과로 사용 될 수 있다

### 일급 함수

- 함수를 값으로 다룰 수 있다.
- 조합성과 추상화의 도구

```js
const a = 10;
const add10 = a => a + 10;
const r = add10(a);
console.log(r);	// 20
```