# ch1-발상의 전환
## 객체지향 정의
- 높은 응집도(기능의 집중도), 낮은 결합도(관계의 의존성)를 지향하며 유연한 소프트웨어를 추구하는 개발 기법
### 어떻게 유연한 소프트웨어를 추구할 수 있을까
- 로직 구현보다는 객체가 외부에 노출하는 인터페이스를 잘 설계하는 것
- 객체지향적으로 리팩토링 하면서 객체 내부와 객체 간의 관계를 깔끔하게 정리하는 것
    - 인터페이스를 통해 여러 객체와 **협력**하는 것

### 핵심
- 점(객체 하나 하나)보다 선(**객체 간의 협력** 관계)로 접근한다.

#### 내 생각
- 테스트코드를 작성하면 자연스럽게 객체지향적으로 코드 작성할 수 있다는 걸 집과 비교해서 독서실에 가면 공부에만 집중할 수 있다는 것과 비교하는 게 인상 깊었음. 테스트코드에 의도적으로 좀 시간을 들여서 작성해야겠다.

> Q. 프로덕션 코드를 작성하기 전에 테스트 코드를 작성해서 객체지향적으로 코드가 작성되는 경험을 해본 적이 있으면 공유해주세요! 만약 없다면 그렇게 하기 위해서는 어떻게 연습을 해야한다고 생각을 하시나요?

# ch2-객체지향을 돕는 도구

## 절차지향과 객체지향의 차이
- 절차 지향
  - 대부분 데이터를 공동으로 관리하기 때문에 여러 함수가 특정 데이터를 같이 의존하게 된다. 
- 객체 지향
  - 데이터 관리 주체(데이터와 기능을 가지는 객체)가 데이터를 소유한 객체로 명확하게 지정되도록 유도한다.

## 추상화
- 추상화의 본질은 한 가지 특징만 잡아내는 것
- 추상화는 곧 단순화

## UML 그릴 때 고려해야 할 사항
- 얼마나 의사소통에 유익하게 그릴 것인가를 우선순위에 둔다. 
  - UML은 의사소통을 편리하게 하기 위한 목적이다. 


> Q. 객체지향적으로 코드를 작성할 때 절차지향과 비교해서 어떻게 관계의 의존성을 낮추고 기능의 집중도는 올릴 수 있는 걸까?

# ch3-객체지향의 넓이
객체 지향의 기본 요소 5가지
- 객체
- 클래스
- 속성
- 메서드
- 생성자
## 객체
- 데이터(속성)와 기능(메소드)을 포함한 독립적으로 실행할 수 있는 최소 단위.
## 클래스
- 클래스는 유사한 특징을 가진 대상들을 일정하게 묶어서 하나의 종류로 정의한 분류와 범주이다.
> 분류와 범주 = 클래스 = 추상적 (분류와 범주와 클래스가 완전히 같다는 의미는 아니다.)
> 객체화 = 객체 = 구체적
## 속성
- 속성은 객체가 가진 고유한 값이다.
- 객체가 다른 객체와 잘 협력할 수 있도록 돕는 속성을 찾아야 한다.
- 점(객체 하나하나)보다 선(객체 간의 협력 관계)으로 접근하면 지킬 수 있다.
## 메소드
- 메소드는 객체가 자신 또는 다른 객체에게 제공하는 '기능'이다.
- 메소드는 객체 속성을 변경하는 유일한 통로이자 다른 객체와 상호 작용하는 통로여야 한다.
## 생성자
- 객체가 처음 생성될 때 호출되는 메서드
- 오버 로딩 기법을 자주 사용함

## 객체지향의 근본 조건
- 낮은 관계의 의존성과 높은 기능의 집중도를 추구하는 객체지향의 장점을 지키기 위한 필수 조건
  - 상속(세로), 오버로딩, 오버라이딩, 폴리모피즘, 캡슐화, 인터페이스, 위임(가로)
### 오버로딩
- 생성자 호출에서 많이 씀
- 메소드 이름은 같지만 메소드의 인자를 다르게 해서 별도의 메서드처럼 접근할 수 있는 개념
- 오버로딩이 없다면?
  - 똑같이 상품의 판매 상태를 알려주는 메소드지만 메소드 이름을 다 다르게 해줘야 함
    - ex) getStatusOfGoods1, getStatusOfGoods2, getStatusOfGoods3 -> 메서드 이름 고민 + 메소드 기능 해석하는데 불필요한 시간 낭비를 하게 됨
### 오버라이딩
- 상속 관계, 하위 클래스에서 하위 클래스의 특징에 따라 재구현하는 것
- 메소드 이름, 매개변수, 타입 모두 동일해야 함
### 폴리모피즘
- 같은 그룹에 속하는 클래스들의 동일한 메서드를 호출할 때 하위 클래스들이 각자 다른 로직을 수행하고 리턴하는 것
  - ex) 사용자가 결제 진행 메시지를 결제 그룹에 전달하면 메시지를 받은 객체가 메시지에 따라 카드, 계좌이체 등의 다른 행동을 한다. -> 상위 클래스가 제공하는 결제같은 메서드(기능)를 각자 다른 기능 구현으로 재정의(오버라이딩) 한 상태이다.
- 장점
  - 관계의 의존도가 낮다.
    - 사용자는 인터페이스만 알면 된다.
      - 사용자 코드의 변경 없이 기능의 수정과 확장이 가능하다.
- 폴리모피즘으로 구성하지 않으면?
  - 관계 의존성이 높아지고, 기능이 수정되거나 확장되면 사용자 코드 변경이 필요함

>Q. 폴리모피즘에 대해서 이해한만큼 쉽게 설명해주세요.

### 캡슐화
- 정의
  - 대상 분리 -> 숨기고 보호
- 속성의 캡슐화 (잘 알면 -> 다른 객체의 조작에 의해 객체가 훼손되는 경우를 막음)
  - 속성은 private 으로
  - getter로만 속성 가져올 수 있게 한다.
  - setter는 가능한 한 쓰지 않거나 제한적으로 허용한다.
- 기능의 캡슐화(잘 알면 -> 기능 수정과 확장에 유연)
  - 변하는 기능 인식하고 변하지 않는 기능으로부터 분리해서 별도 클래스 그룹으로 추출한다.
- 정보의 캡슐화(정보 은닉), 집합(추상화 과정)과 분해(전체를 세부로 분할하는 과정) (잘 알면 -> 정보의 집합과 분해에 능숙, 정보의 추상화 개념을 알고 쓴다, 필요 이상의 정보가 담긴 클래스를 의존하고 조작하는 상황을 막을 수 있음)
  - 정보 은닉을 잘 지원하는 객체 지향 요소는?
    - 인터페이스
      - 클라이언트 클래스는 인터페이스에 명시된 기능의 용도만 알기 때문에 정보의 캡슐화를 지킬 수 있다.
### 인터페이스
- 인터페이스는 어떤 대상의 의미를 구현할 때 지켜야 할 규칙과 표준을 의미한다.
- 그리고 상호 교류하는 대상끼리 정보를 주고 받는 방법에 대한 규칙과 표준이다.
- 인터페이스의 효과 -> 낮은 관계의 의존성, 높은 기능의 집중도 지향
  - 다중 상속 효과
  - 인터페이스와 로직이 명확하게 분리된다.
    - 상위 클래스 코드 깔끔
    - 직관적으로 메소드 목록을 클라이언트 클래스에게 알려줄 수 있음
    - 외부에 노출할 필요 없는 로직을 캡슐화한다.
### 위임(delegation)
- 상속의 문제를 위임이 해결한다. -> 인터페이스 활용(어떤 기능을 자신이 처리하지 않고 다른 객체에 위임시켜 그 객체가 일을 처리하도록 하는 것)
  - 상속의 문제
    - 상위 클래스에서 상속을 받았는데 하위 클래스에서는 필요없는 경우가 생길 수 있음
    - 객체의 행동(메소드 내부 로직)이 컴파일 시 결정되고, 프로그램 실행 중에 행동을 바꿀 수 없음
## 객체지향 구현 원리 5가지(SOLID)
### SRP
- single responsibility principle
- 하나의 클래스는 하나의 책임만 가지는 것
- 클래스의 수정 이유는 단 하나여야 한다.
- 예시
  - 휴대폰은 자신을 음성 수신한다.(O), 휴대폰은 자신을 음성 송신한다(O), 휴대폰은 자신을 기기 충전한다.(X), 휴대폰은 자신을 전화 걸기/받기를 한다(X)
### OCP
- open closed principle
- 기능 확장에는 열려있지만, 코드 수정에는 닫혀 있어야 한다.
- 기존 클래스를 수정하면 사이드 이펙트가 발생하기 쉽고 수정 후 정상 작동 유무+사이트 이펙트 발생 유무에 대해서 테스트도 해야한다.
### LSP
- liskov Substitution principle
- 하위 클래스는 상위 클래스가 사용되는 곳에 대체될 수 있어야 한다.
### ISP
- interface segregation principle
- 클래스는 자신이 사용하지 않는 메소드에 의존하면 안된다.
### DRY / DIP
- DRY
  - Don't repeat yourself
  - 중복되는 코드는 하나로 통합한다.
  - 공통되는 코드를 추출해서 추상화하고 한 곳에 둬서 중복 코드를 피한다.
- DIP
  - Dependency Inversion principle
  - 구체적인 클래스 대신 추상적인 클래스에 의존하라.
    - ArrayList list = new ArralyList() -> List list = new ArralyList()

>Q. 객체지향 구현 원리 중 코드를 작성할 때 특히 어떤 원리를 구현하기 위해서 고민을 하나요? 없다면 어떤 원리를 유용하게 쓸 수 있을 것 같나요?

# ch04-디자인 패턴의 깊이
- strategy 패턴이란?
  - 위임 활용
  - 메소드의 구현을 다른 클래스에 위임
  - 바뀌는 부분, 바뀌지 않는 부분을 분리한다.
    - 바뀌는 부분은 캡슐화시킨다.
> Q. IoC는 어떻게 Strategy 패턴을 편하게 설정할 수 있게 해주나요?

# ch05-한 점 보기
>Q. 면접에서 객체지향에 뭐냐고 물어보면 뭐라고 대답할 건가요? 