# 타입스크립트 문법을 알아보자!

<br />

1) primitive type(원시 타입)
```typescript
let numberValue: number = 10;
let stringValue: string = "Hello";
let booleanValue: boolean = true;
let nullValue: null = null;
let undefinedValue: undefined = undefined;
let symbolValue: symbol = Symbol("key");
let bigintValue: bigint = 100n;
```

2) object types(객체 타입)
```typescriptlet
objectValue: object = { key: "value" };
let arrayValue: number[] = [1, 2, 3];
let functionValue: Function = () => { console.log("Function called."); };
```

3) special types(특별한 타입)
```typescript
let anyValue: any = 10; /* 어떤 유형의 값이든 허용됨 */
let voidFunction: () => void = () => { console.log("This function returns nothing."); };
let neverValue: never = (() => { throw new Error("Never returns."); })();
let unknownValue: unknown = "unknown value";
```

4) advanced types(고급 타입)
```typescript
let unionValue: string | number = "text"; /* 문자열 또는 숫자 타입 중 하나 */
let intersectionValue: { key1: string } & { key2: number } = { key1: "value", key2: 10 }; /* 두 타입의 교집합 */
let tupleValue: [number, string] = [1, "text"]; /* 정확한 요소 유형 및 순서를 가진 배열 */
enum Direction { Up, Down, Left, Right }; /* 열거형 */
let enumValue: Direction = Direction.Up; /* 열거형 값 */
```

5) special types(타입 별칭)
```typescript
let unionValue: string | number = "text"; /* 문자열 또는 숫자 타입 중 하나 */
let intersectionValue: { key1: string } & { key2: number } = { key1: "value", key2: 10 }; /* 두 타입의 교집합 */
let tupleValue: [number, string] = [1, "text"]; /* 정확한 요소 유형 및 순서를 가진 배열 */
enum Direction { Up, Down, Left, Right }; /* 열거형 */
let enumValue: Direction = Direction.Up; /* 열거형 값 */
```

6) type Aliases
```typescript
type Point = { x: number, y: number }; /* 타입 별칭 */
let pointValue: Point = { x: 10, y: 20 }; /* 타입 별칭 사용 */
```
