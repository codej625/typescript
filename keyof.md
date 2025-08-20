# keyof

<br />
<br />

* keyof T

---

```
keyof는 타입 안전성을 보장하면서,
객체의 키에 대한 작업을 할 때 매우 유용한 지시어이다.

언제 사용하는지 알아보자.
```

<br />
<br />
<br />
<br />

1. 객체에서 사용예시

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
// string[]는 너무 광범위하다.

Object.keys(obj).forEach((key) => {
  obj[key] // 모든 문자열이 가능하기 때문에 data의 프로퍼티에 접근 불가
});
```

<br />

```ts
// keyof로 정확한 키들만 허용한다.

(Object.keys(obj) as (keyof Obj)[]).forEach((key) => {
  // 정확한 key -> "name" | "age" | "email"
  obj[key] // 안전한 접근 가능
});
```

<br />

```ts
// 정리

const anyString: string = "randomText"; // 어떤 문자열이든 가능
const specificKey: keyof Obj = "name"; // "name" | "age" | "email" 3개 키 중 하나만 가능한 유니온타입
```
