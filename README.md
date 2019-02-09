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
const log = console.log;
const a = 10;
const add10 = a => a + 10;
const r = add10(a);
log(r);	// 20
```

## 일급 함수

```js
const log = console.log;
const add5 = a => a + 5;
log(add5);
log(add5(5));

const f1 = () => () => 1;
log(f1());

const f2 = f1();
log(f2);
log(f2());
```

## 고차 함수

- 함수를 값으로 다루는 함수

### 함수를 인자로 받아서 실행하는 함수

- apply1
- times

```js
const log = console.log;
const apply1 = f => f(1);
const add2 = a => a + 2;
log(apply1(add2));	// 3
log(apply1(a => a - 1));	// 0
```

```js
const log = console.log;
const times = (f, n) => {
	let i = -1;
	while (++i < n) f(i);
}
times(log, 3); // 0부터 2까지 순차적으로 출력
times(a=>log(a+10), 3);	// 	10부터 12까지 순차적으로 출력
```


### 함수를 만들어 리턴하는 함수 (클로저를 만들어서 리턴하는 함수)

- addMaker

```js
const log = console.log;
const addMaker = a => b => a + b;
const add10 = addMaker(10);
log(add10(5));	// 15
log(add10(10));	// 20
```

## 기존과 달라진 ES6에서의 리스트 순회

- for i++
- for of

```js
const log = console.log;
const list = [1, 2, 3];
for(var i = 0; i < list.length; i++) {
	log(list[i]);
	// 1
	// 2
	// 3
}
const str = 'abc';
for(var i = 0; i < str.length; i++) {
	log(str[i]);
	// a
	// b
	// c
}
```

```js
const log = console.log;
const list = [1, 2, 3];
const str = 'abc';
for (const a of list) {
	log(a);
} 
for (const a of str) {
	log(a);
} 
```

## Array, Set, Map을 통해 알아보는 이터러블/이터레이터 프로토콜


### Array 통해 알아보기

```js
const log = console.log;
const arr = [1, 2, 3];
let iter1 = arr[Symbol.iterator]();
for(const a of iter1) log(a);
```

### Set을 통해 알아보기

```js
const log = console.log;
const set = new Set([1, 2, 3]);
for(const a of set) log(a);
```

### Map을 통해 알아보기

```js
const log = console.log;
const map = new Map([['a',1],['b',2],['c',3]]);
for(const a of map) log(a);
for(const a of map.keys()) log(a);
for(const a of map.values()) log(a);
for(const a of map.entries()) log(a);
```

### 이터러블/이터레이터 프로토콜

- 이터러블 : 이터레이터를 리턴하는 `[Symbol.iterator]()` 를 가진 값
- 이터레이터 : `{value,done}` 객체를 리턴하는 next()를 가진 값
- 이터러블/이터레이터 프로토콜 : 이터러블을 for...of, 전개 연산자 등과 함께 동작하도록 규약