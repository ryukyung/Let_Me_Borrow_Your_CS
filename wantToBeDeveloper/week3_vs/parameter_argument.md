### 매개변수: parameter

- 변수의 특별한 한 종류, 함수 등과 같은 서브루틴의 input으로 제공되는 여러 데이터 중 하나를 가리키기 위해서 사용한다.
- 간단히 말해서 함수의 정의 부분에 나열되어 있는 변수들을 의미한다.
- 따라서 값이 아니라 변수(variable)로 봐야 한다.
  <br />

### 전달인자: argument

- 서브루틴의 input으로 제공되는 여러 데이터들을 말한다.
- 간단히 말해서 함수를 호출할 때 전달되는 실제 값을 의미한다.
- 따라서 값(value)로 봐야 한다.
  <br />

```jsx
// parameter: a, b
function funcAdd(a, b) {
  return a + b;
}
// argument: 1, 2
funcAdd(1, 2);
```
