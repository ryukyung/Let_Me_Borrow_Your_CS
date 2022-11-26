### 람다란?

**익명함수**(Anonymous functions)를 지칭하는 용어

> **익명함수**
>
> 함수의 이름이 없는 함수를 말하고 일급객체라는 특징을 가지고 있다.
>
> 다른 객체들에 적용 가능한 연산을 모두 지원하는 개체를 가르키고 함수를 값으로 사용할 수 있으며 파라미터로 전달 및 변수에 대입과 같은 연산이 가능하다.

<br />
<br />

### 람다의 특징

- 코드의 간결성 - 람다 사용 시 불필요한 반복문의 삭제가 가능하며 복잡한 식을 단순하게 표현할 수 있다.
- 지연연산 수행 - 지연연산을 수행함으로써 불필요한 연산을 최소화할 수 있다.
- 병렬처리 가능 - 멀티스레드를 활용하여 병렬처리를 사용할 수 있따.
- 람다식의 호출이 까다롭다
- stream 사용 시 단순 for문 혹은 while문 사용 시 성능이 떨어진다.
- 너무 많이 사용하면 오히려 가독성을 떨어뜨린다.
- 괄호와 화살표로 표현할 수 있으며 람다의 반환값은 함수형 인터페이스이기 때문에 이를 이용해야 한다.
  <br />
  <br />

### 람다의 표현식

```java
@FunctionalInterface
interface MyFunctionalInterface {
	String test();
}
public class Lambda{
	public static void main(String[] args) throws Throwable{
		String str = "Bello";
		MyFunctionalInterface func = () -> str.replaceAll("\\s"+"");
		System.out.println(func.test());
	}
}
```
