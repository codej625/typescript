# 기본적인 config 설정을 해보자!(리액트나 뷰 사용시 별도 설정 필요)

<br />

```json
{
  "compilerOptions": {
    "target": "es6",
    "module": "commonjs",
    "strict": true,
    "esModuleInterop": true
  }
}
```
```
compilerOptions -> TypeScript 컴파일러에 대한 다양한 옵션을 지정하는 섹션

target -> 컴파일된 JavaScript 파일의 ECMAScript 대상 버전을 지정 ex) es5 or es6

module -> TypeScript 모듈을 JavaScript 모듈로 컴파일하는 방식을 지정 ex) commonjs

strict -> 엄격한 유형 검사 옵션을 활성화한다. true로 설정하면 모든 엄격한 유형 검사 옵션을 켠다.

esModuleInterop -> CommonJS 모듈과의 호환성을 허용하고 import/export 구문을 require 구문과 함께 사용할 수 있도록 한다.
```
