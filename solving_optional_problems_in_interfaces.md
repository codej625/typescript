# 인터페이스에서의 옵셔널

<br />
<br />

* 공통으로 사용하기 위한 인터페이스의 문제 발생?
---

```
여러 컴포넌트에서 공통으로 사용되는 Props를 처리하기 위해
인터페이스를 만들었을 때 어떤 문제가 발생할까?

가장 흔하게 발생하는 문제는
optional property 문제일 것이다.

이에 관한 예시와 해결방법을 알아보자.
```

<br />
<br />
<br />
<br />

1. 예시

```
여러 컴포넌트에서 공통으로 사용하는 인터페이스를 만들었다.
```

```tsx
// Dialog에 사용되는 Props를 위한 공통 인터페이스

export interface DialogProps {
  id: string;
  open: boolean;
  onClose?: () => void;
  modalMode?: React.Dispatch<React.SetStateAction<boolean>>;
}
```

<br />

```
문제는 ?이 붙어있는 optional property이다.

DialogProps에서 onClose, modalMode를 ?으로 정의했으니,
"이 속성이 없을 수도 있다"는 가능성을 열어둔 셈이다.

실제로 전달 되더라도 타입상으론 undefined일 수 있다고 간주한다.
```

<br />
<br />
<br />

1. 해결

```
그렇다면 optional property을 해결하는 방법을 알아보자.

상황에 맞게 방법들 중 한 가지를 선택하면 된다.
```

```tsx
// 1번 방법 -> modalMode가 항상 필요하다면, DialogProps에서 ?를 제거해서 필수로 만든다.
export interface DialogProps {
  id: string;
  open: boolean;
  onClose?: () => void;
  modalMode: React.Dispatch<React.SetStateAction<boolean>>; // 필수로 변경
}



// 2번 방법 -> 값을 사용하는 곳에서 옵셔널 체이닝을 사용한다.
const handleEditClick = () => {
  modalMode?.(true); // modalMode가 undefined이면 호출 안 함
  setIsEditing(true);
};



// 3번 방법 -> 타입 단언 사용 modalMode가 절대 undefined가 아니라고 확신한다면, 타입 단언으로 강제
const handleEditClick = () => {
  (modalMode as React.Dispatch<React.SetStateAction<boolean>>)(true);
  setIsEditing(true);
};
// 이건 "내가 책임질게"라는 뜻이라, 만약 실제로 undefined가 들어오면 런타임 에러가 날 수 있다.



// 4번 방법 -> 기본값 제공
const CveCheckPlanListDetailDialog = ({
  id,
  open,
  onClose,
  modalMode = () => {}, // 기본 빈 함수
}: DialogProps) => {
  // ...
  const handleEditClick = () => {
    modalMode(true); // 안전하게 호출 가능
    setIsEditing(true);
  };
};



// 5번 방법 -> Non-null Assertion Operator ("절대 null이나 undefined가 아니야"라고 단언)
const handleEditClick = () => {
  modalMode!(true); // !로 undefined 가능성 제거
  setIsEditing(true);
};
// modalMode가 실제로 undefined면 런타임 에러가 발생할 수 있다.
```
