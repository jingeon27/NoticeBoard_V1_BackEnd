# NoticeBoard 개인프로젝트

- 게시판과 oauth기능을 만들며, 백엔드와 nest에 대해 공부하는 repository입니다.

## 개발 기간

- 최소 1주 ~ 최대 2주로 생각하고 있습니다.

---

## SOLID

SOLID는 객체지향 설계의 5대원칙으로 SRP(단일 책임 원칙), OCP(개방-폐쇄 원칙), LSP(리스코프 치환 원칙), ISP(인터페이스 분리 원칙), DIP(의존 역전 원칙)을 말한다.
앞글자만 따서 SOLID 원칙이 되었다.

### 단일 책임 원칙 (Single Responsiblity Principle)

- SRP
  모든 클래스는 각각 하나의 책임만 가져야 한다.
  클래스는 그 책임을 완전히 캡슐화해야 한다.

사칙연산 함수를 가지고 있는 계산 클래스가 있다고 하자.
이 상태의 계산 클래스는 사칙연산 기능만을 책임진다.
이 클래스를 수정한다면 그 이유는 사칙연산 함수와 관련된 문제일 뿐이다.

### 개방-폐쇄 원칙 (Open Closed Principle)

- OCP
  확장에는 열려있고 수정 시에는 닫혀있는, 기존의 코드를 변경하지 않으면서(Closed) 기능을 추가할 수 있도록(Open) 설계가 되어야 한다는 원칙이다.

캐릭터를 하나 생성한다면, 각각의 캐릭터가 움직임이 다를 경우에
움직임의 패턴 구현을 하위 클래스에 맡긴다면 캐릭터 클래스의 수정은 필요가 없고(Closed) 움직임의 패턴만 재정의하면 된다(Open).

### 리스코프 치환 원칙 (Liskov Substitution Principle)

- LSP
  자식 클래스는 언제나 자신의 부모 클래스를 대체할 수 있다는 원칙이다.
  부모 클래스가 들어갈 자리에 자식 클래스를 넣어도 계획대로 작동해야 한다.

자식 클래스는 부모 클래스의 책임을 무시하거나 재정의하지 않고 확장만 수행하도록 해야 LSP를 만족할 수 있다.

### 인터페이스 분리 원칙 (Interface Segregation Principle)

- ISP
  한 클래스는 자신이 사용하지 않는 인터페이스는 구현하지 말아야 한다.
  하나의 일반적인 인터페이스보다 여러 개의 구체적인 인터페이스가 낫다.

### 의존 역전 원칙 (Dependency Inversion Principle)

- DIP
  의존 관계를 맺을 때 변화하기 쉬운 것, 자주 변화하는 것보다는 변화하기 어려운 것, 거의 변화가 없는 것에 의존하라는 원칙이다.

구체적인 클래스보다 인터페이스나 추상 클래스와 관계를 맺으라는 것이다.

## DRY

Don't Repeat Yourself
모든 형태의 정보중복을 지양하는 원리이다.
중복 배제의 원리는 모든 지식은 시스템 내에서 유일하고 중복이 없으며 권위있는 표상만을 가진다는 말이다.

## YAGNI

### You Ain't Gonna Need it

프로그래머가 필요하다고 간주할 때까지 기능을 추가하지 않는 것이 좋다는 익스트림 프로그래밍(XP)의 원칙이다.
익스트림 프로그래밍의 공동 설립자 론 제프리스는 다음과 같이 말했다.
실제로 필요할 때 무조건 구현하되, 그저 필요할 것이라고 예상하는 때에는 절대 구현하지 말라.

## KISS

### Keep it simple, stupid

디자인에서 간단하고 알기 쉽게 만드는 편이 좋다는 원리이다.

---

## nest

### decorator

- nest에선 데코레이터를 이용하여 get, post, delete등 rest api요청을 처리하고, dto를 따로 dto 이름이 들어간 파일을 만들어 선언해 데코레이터 옆에 정의 해준다.

### controler

- controler는 만들 때 모듈에 선언해주어서 작동한다.
- 콘솔 명령어로 controler를 만들 수 있다.

### provider

- provider 역시 콘솔 명령어로 만들 수 있다.
- provider는 DI 할 수 있다. 개체 인스턴스를 연결하는 기능이다.
- provider는 일반적으로 애플리케이션 생명주기와 같은 스코프를 갖고 있다
