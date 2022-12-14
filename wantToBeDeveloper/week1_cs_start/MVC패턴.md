### **MVC 패턴**

디자인 패턴 중 하나, 프로그램이나 어떤 특정한 것을 개발할 때 발생했던 문제점을 정리해서 상황에 따라 적용해서 쓸 수 있는 것을 특정 규약을 통해 쉽게 쓸 수 있는 형태로 만든 것, 간단히 말해 **소프트웨어 개발 방법을 공식화한 것**이다.
<br />

### MVC: Model View Controller

View, 눈에 보이는 것, 사용자가 보는 화면을 그리는 역할을 하는데 웹의 경우 HTML, CSS로 나타내는 요소를 말한다.
Controller, 무언가를 제어하는 것, 프로그래밍이 이루어지는 곳, 모델에게 전달해주기 전에 데이터를 가공하며 뷰와 모델 사이의 중개자 역할을 한다
Model, 데이터베이스에서 데이터를 가지고 올수도 있고 가지고 있을수도 있다. 데이터베이스와 소통하고 컨트롤러에게 데이터를 전달한다.

간단한 예시를 들어보자면 **모델**은 식료품 창고를 관리하고 음식을 만드는 주방장이라면 **뷰**는 주방장이 만든 음식을 플레이팅하는 직원이고 주문도 받고 서빙도 하는 매니저를 **컨트롤러**라고 볼 수 있다.
<br /><br />

### MVC 전체 구조를 웹에 비유하자면

![https://blog.kakaocdn.net/dn/dms9n6/btrIBU4QUlU/L7oPac9f3gCeelWE3CNTXk/img.png](https://blog.kakaocdn.net/dn/dms9n6/btrIBU4QUlU/L7oPac9f3gCeelWE3CNTXk/img.png)

사진에서 보이는 것처럼 모델, 뷰, 컨트롤러, 데이터베이스, 브라우저, 라우터가 존재한다. 여기서 라우터는 어떤 주소로 접속했을 때 어떤 페이지를 보여줄지, 간단히 말해서 메뉴판을 마련해 두는 것을 말한다.

사용자가 브라우저에 ‘맛집’이라고 검색한다면 컨트롤러가 모델에게 ‘맛집’에 대한 검색 결과를 달라고 요청한다. 그러면 모델이 데이터베이스에서 데이터를 가져오고 모델이 컨트롤러에서 검색 결과를 넘겨준다. 데이터를 받은 컨트롤러가 뷰에게 전달하면 뷰가 사용자가 보는 UI에 검색결과를 넣어서 웹 페이지를 보여준다.
<br /><br />

### MVC 패턴을 지키면서 코딩하는 규칙

1. Model은 Controller와 View에 의존하지 않아야 한다.

   모델 내부에 컨트롤러와 뷰에 관련된 코드가 있으면 안된다. 쉽게 말해서 모델 클래스에서 컨트롤러와 뷰의 클래스를 import해서 사용하면 안된다.  
   모델은 데이터와 관련된 부분이기 때문에 언제든 깔끔하고 정제된 데이터를 꺼낼 수 있는 상태로 존재해야 한다.

2. View는 Model에만 의존해야 하고 Controller에는 의존하면 안된다.

   뷰에는 모델의 코드만 있을 수 있고 컨트롤러의 코드가 있으면 안된다

3. View가 Model로 부터 데이터를 받을 때는 사용자마다 다르게 보여주어야 하는데이터에 대해서만 받아야 한다.

   > UI + Model로부터 받은 데이터 = View
   > 뷰는 사용자한테 보이는 UI와 모델로부터 받은 데이터가 합쳐져 만들어진 화면이다
   > 뷰가 모델로부터 데이터를 받을 때는 사용자마다 다르게 보여주어야 하는 데이터만 받아야 한다.

4. Controller는 Model과 View에 의존해도 된다.

   컨트롤러는 모델과 뷰의 중개자 역할을 하면서 전체 로직을 구성하기 때문에 컨트롤러 내부에는 모델과 뷰의 코드가 있을 수 있다.

5. View가 Model로부터 데이터를 받을 때는 Controller에서 받아야 한다

   뷰가 모델로부터 데이터를 받을 때는 컨트롤러 코드 내에서, 안에서 받아야 한다.

### 추가적: 모델1

![https://blog.kakaocdn.net/dn/bl4eV7/btrIypctqqB/bMcqLE0aAy7tTeizzahk5k/img.png](https://blog.kakaocdn.net/dn/bl4eV7/btrIypctqqB/bMcqLE0aAy7tTeizzahk5k/img.png)

뷰와 로직을 모두 JSP 페이지 하나에서 처리하는 구조, 위의 사진처럼 JSP와 자바빈 혹은 서비스 클래스로 나눌 수 있고 JSP페이지에서 로직 처리를 위한 자바 코드와 출력을 위한 코드가 함께 섞여서 삽입된다. 브라우저에서 요청이 들어오면 JSP는 자신이 직접, 자바빈을 이용해서 작업을 처리한다. 처리한 정보를 클라이언트의 출력 구조가 단순하기 때문에 익히기 쉽고 숙련된 개발자가 아니더라도 구현이 용이하다.

출력을 위한 뷰 코드와 로직 처리를 위한 자바 코드가 섞여있기 때문에 JSP 복잡, 프론트와 백이 혼재, 분업이 용이하지 않다

### 추가적: 모델2

![https://blog.kakaocdn.net/dn/bl4eV7/btrIypctqqB/bMcqLE0aAy7tTeizzahk5k/img.png](https://blog.kakaocdn.net/dn/bl4eV7/btrIypctqqB/bMcqLE0aAy7tTeizzahk5k/img.png)

요청이 들어오면 요청에 대한 로직 처리를할 모델인 자바빈 혹은 서비스 클래스, 요청 결과를 유저에게 보여줄 뷰 역할을 하는 JSP, 모든 흐름을 제어하는 컨트롤러 역할을 하는 서블릿이 있다

- Model: 자바빈, 서비스 클래스
- View: JSP
- Controller: 서블릿

모델2는 뷰 코드와 로직 처리를 위한 코드가 분리되었기 때문에 모델1에 비해 코드가 복잡하지 않고 기능에 따라 분리되어있다. 유지보수가 용이하지만 자바에 대한 깊은 이해가 필요하고 구조가 복잡하기 때문에 습득이 어렵고 작업량이 많다.
