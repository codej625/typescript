# 기본적인 타입스크립트 Config 설정

<br />
<br />

* Typescript Config

---

```
tsconfig.json은 TypeScript 프로젝트의 루트 디렉터리에 위치하며,
컴파일러가 TypeScript 코드를 JavaScript로 변환할 때 사용하는 설정을 정의한다.
```

<br />
<br />
<br />
<br />

1. tsconfig.json 내용

```json
// tsconfig.json

{
  "compilerOptions": {
    "target": "es6", // 컴파일된 JS의 ECMAScript 버전을 ES6로 설정
    "module": "esnext", // 모듈 시스템을 ESNext로 설정, 번들러와 호환
    "jsx": "react-jsx", // JSX를 React 17+의 새로운 JSX Transform으로 처리
    "moduleResolution": "bundler", // 번들러 방식으로 모듈 해석
    "strict": true, // 엄격한 타입 검사 활성화
    "esModuleInterop": true, // CommonJS와 ES 모듈 간 상호 운용성 개선
    "allowSyntheticDefaultImports": true, // 기본 내보내기 없는 모듈의 기본 임포트 허용
    "baseUrl": "./src", // 모듈 경로의 기준을 src 폴더로 설정
    "paths": {
      "@/*": ["*"] // @ 별칭으로 src 내 파일을 절대 경로로 참조
    },
    "outDir": "./dist", // 컴파일된 JS 파일을 dist 폴더에 저장
    "sourceMap": true, // 디버깅용 소스 맵 파일 생성
    "noEmitOnError": true // 컴파일 에러 시 JS 파일 생성 방지
  },
  "include": ["src/**/*"], // src 폴더 내 모든 TS/TSX 파일을 컴파일 대상으로
  "exclude": ["node_modules", "dist"] // node_modules와 dist 폴더를 컴파일에서 제외
}
```
