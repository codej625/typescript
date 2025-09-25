# keyof

<br />
<br />

* keyof T

---

```
keyof는 타입 안전성을 보장하면서,
객체의 키에 대한 접근을 할 때 매우 유용한 지시어이다.
```

<br />
<br />
<br />
<br />

1. 객체에서 사용 예시

```ts
// obj라는 객체가 있다고 가정

interface Obj {
  name: string;
  age: number;
  email: string;
}

const obj: Obj = {
  name: "codej625",
  age: 35,
  email: "codej625@gmail.com"
}
```

<br />

```ts
// Object.keys()는 항상 string[]을 반환한다.

Object.keys(obj) // 타입은 string[]
```

<br />

```ts
// string[]는 너무 광범위하다. 모든 문자열로 만들어진 배열을 뜻한다.

Object.keys(obj).forEach((key) => {
  obj[key] // 모든 문자열이 가능하기 때문에, 타입스크립트에서는 obj의 프로퍼티에 접근 불가 (에러)
});
```

<br />

```ts
// keyof을 사용해서 유효한 key의 type으로 제한한다.

(Object.keys(obj) as (keyof Obj)[]).forEach((key) => {
  // 유효한 key -> "name" | "age" | "email"
  obj[key] // 안전한 접근 가능
});
```

<br />

```ts
// 정리

const anyString: string = "randomText"; // 어떤 문자열이든 가능

const specificKey: keyof Obj = "name"; // "name" | "age" | "email" 3개 키 중 하나만 가능한 유니온타입
```
