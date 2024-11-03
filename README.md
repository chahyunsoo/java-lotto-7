# **java-lotto-precourse**

## **👊 미션 개요 및 이전 미션 공통 피드백 Remind**

### 미션 개요

- 자동차 경주 게임에서는 사용자가 입력한 자동차 이름과 라운드 수에 따라, 자동차가 조건에 맞춰 전진하고, 최종 우승자를 계산해 출력하는 기능을 구현하는 것이 목표입니다.
- 단일 책임 원칙 준수: 여러 역할을 수행하는 함수를 단일 역할을 수행하는 작은 함수로 분리합니다.
- 테스트 도구 사용: 테스트 도구를 활용하여 코드가 제대로 작동하는지 검증합니다.
- 요구 사항 분석 및 기능 단위 분리: 요구 사항을 분석하고 기능을 분리하여 독립적으로 동작하도록 설계합니다.

### 이전 미션 공통 피드백 Remind

> 이전 미션에서 한번 더 생각해야 할 마인드 Set 입니다.

- README.md를 상세하게 작성합니다.
    - 해당 프로젝트가 어떤 프로젝트인지, 주요 기능이 무엇인지를 소개해야 합니다.
- 기능 목록을 재검토합니다.
    - 클래스 설계와 구현, 메소드 설계와 구현 같은 상세한 내용은 포함시키지 않습니다.(언제든지 변경될 수 있기 때문에)
    - 구현해야할 기능 목록을 중심으로 작성하되, 정상적인 경우만이 아닌 예외 상화도 함께 정리합니다.(계속해서 업데이트)
- 기능 목록을 업데이트 합니다.

---

## 📞 기능 요구사항

- 주어진 횟수 동안 n대의 자동차는 전진 또는 멈출 수 있다.
- 각 자동차에 이름을 부여할 수 있다. 전진하는 자동차를 출력할 때 자동차 이름을 같이 출력한다.
- 자동차 이름은 쉼표(,)를 기준으로 구분하며 이름은 5자 이하만 가능하다.
- 사용자는 몇 번의 이동을 할 것인지를 입력할 수 있어야 한다.
- 전진하는 조건은 0에서 9 사이에서 무작위 값을 구한 후 무작위 값이 4 이상일 경우이다.
- 자동차 경주 게임을 완료한 후 누가 우승했는지를 알려준다. 우승자는 한 명 이상일 수 있다.
- 우승자가 여러 명일 경우 쉼표(,)를 이용하여 구분한다.
- 사용자가 잘못된 값을 입력할 경우 IllegalArgumentException을 발생시킨 후 애플리케이션은 종료되어야 한다.

### 입출력 요구 사항

- 입력
    - 로또 구입 금액을 입력 받는다. 구입 금액은 1,000원 단위로 입력 받으며 1,000원으로 나누어 떨어지지 않는 경우 예외 처리한다.
  > 1400

    - 당첨 번호를 입력 받는다. 번호는 쉼표(,)를 기준으로 구분한다.
  > 1,2,3,4,5,6

    - 보너스 번호를 입력 받는다.
  > 7

- 출력
    - 발행한 로또 수량 및 번호를 출력한다. 로또 번호는 오름차순으로 정렬하여 보여준다.
  ```
    8개를 구매했습니다.
    [8, 21, 23, 41, 42, 43]
    [3, 5, 11, 16, 32, 38]
    [7, 11, 16, 35, 36, 44]
    [1, 8, 11, 31, 41, 42]
    [13, 14, 16, 38, 42, 45]
    [7, 11, 30, 40, 42, 43]
    [2, 13, 22, 32, 38, 45]
    [1, 3, 5, 14, 22, 45]
  ```

    - 당첨 내역을 출력한다.
  ```
  3개 일치 (5,000원) - 1개
  4개 일치 (50,000원) - 0개
  5개 일치 (1,500,000원) - 0개
  5개 일치, 보너스 볼 일치 (30,000,000원) - 0개
  6개 일치 (2,000,000,000원) - 0개
  ```

    - 수익률은 소수점 둘째 자리에서 반올림한다. (ex. 100.0%, 51.5%, 1,000,000.0%)
  > 총 수익률은 62.5%입니다.

    - 예외 상황 시 에러 문구를 출력해야 한다. 단, 에러 문구는 "[ERROR]"로 시작해야 한다.
    - [ERROR] 로또 번호는 1부터 45 사이의 숫자여야 합니다.

### **실행 결과 예시**

```
구입금액을 입력해 주세요.
8000

8개를 구매했습니다.
[8, 21, 23, 41, 42, 43] 
[3, 5, 11, 16, 32, 38] 
[7, 11, 16, 35, 36, 44] 
[1, 8, 11, 31, 41, 42] 
[13, 14, 16, 38, 42, 45] 
[7, 11, 30, 40, 42, 43] 
[2, 13, 22, 32, 38, 45] 
[1, 3, 5, 14, 22, 45]

당첨 번호를 입력해 주세요.
1,2,3,4,5,6

보너스 번호를 입력해 주세요.
7

당첨 통계
---
3개 일치 (5,000원) - 1개
4개 일치 (50,000원) - 0개
5개 일치 (1,500,000원) - 0개
5개 일치, 보너스 볼 일치 (30,000,000원) - 0개
6개 일치 (2,000,000,000원) - 0개
총 수익률은 62.5%입니다.
```

---

## **💻 프로그래밍 요구사항 1**

- JDK 21 버전에서 실행 가능해야 한다.
- 프로그램 실행의 시작점은 Application의 main()이다.
- build.gradle 파일은 변경할 수 없으며, 제공된 라이브러리 이외의 외부 라이브러리는 사용하지 않는다.
- 프로그램 종료 시 System.exit()를 호출하지 않는다.
- 프로그래밍 요구 사항에서 달리 명시하지 않는 한 파일, 패키지 등의 이름을 바꾸거나 이동하지 않는다.
- 자바 코드 컨벤션을 지키면서 프로그래밍한다.
- 기본적으로 Java Style Guide를 원칙으로 한다.

## **💻 프로그래밍 요구사항 2**

- indent(인덴트, 들여쓰기) depth를 3이 넘지 않도록 구현한다. 2까지만 허용한다.
    - 예를 들어 while문 안에 if문이 있으면 들여쓰기는 2이다.
    - 힌트: indent(인덴트, 들여쓰기) depth를 줄이는 좋은 방법은 함수(또는 메서드)를 분리하면 된다.
- 3항 연산자를 쓰지 않는다.
- 함수(또는 메서드)가 한 가지 일만 하도록 최대한 작게 만들어라.
- JUnit 5와 AssertJ를 이용하여 정리한 기능 목록이 정상적으로 작동하는지 테스트 코드로 확인한다.
    - 테스트 도구 사용법이 익숙하지 않다면 아래 문서를 참고하여 학습한 후 테스트를 구현한다.
        - JUnit 5 User Guide
        - AssertJ User Guide
        - AssertJ Exception Assertions
        - Guide to JUnit 5 Parameterized Tests

## **💻 프로그래밍 요구사항 3**

- 함수(또는 메서드)의 길이가 15라인을 넘어가지 않도록 구현한다.
    - 함수(또는 메서드)가 한 가지 일만 잘 하도록 구현한다.
- else 예약어를 쓰지 않는다.
    - else를 쓰지 말라고 하니 switch/case로 구현하는 경우가 있는데 switch/case도 허용하지 않는다.
    - 힌트: if 조건절에서 값을 return하는 방식으로 구현하면 else를 사용하지 않아도 된다.
- Java Enum을 적용하여 프로그램을 구현한다.
- 구현한 기능에 대한 단위 테스트를 작성한다. 단, UI(System.out, System.in, Scanner) 로직은 제외한다.
    - 단위 테스트 작성이 익숙하지 않다면 LottoTest를 참고하여 학습한 후 테스트를 작성한다.

## **💻 라이브러리**

- camp.nextstep.edu.missionutils에서 제공하는 Randoms 및 Console API를 사용하여 구현해야 한다.
    - Random 값 추출은 camp.nextstep.edu.missionutils.Randoms의 pickNumberInRange()를 활용한다.
    - 사용자가 입력하는 값은 camp.nextstep.edu.missionutils.Console의 readLine()을 활용한다.

- 사용 예시
    - 1에서 45 사이의 중복되지 않은 정수 6개 반환
  > Randoms.pickUniqueNumbersInRange(1, 45, 6);

## **📝 구현해야할 기능 목록 & 고려해야할 예외 사항**

### 기능 목록

> 작은 기능들을 하나 씩 구현하면 해당 메소드를 검증할 수 있는 단위 테스트를 함께 작성하며 구현을 해나갑니다.

1. 입력 기능

- [X] : 사용자로부터 로또 구매 금액을 입력받습니다.
- [X] : 사용자로부터 당첨번호를 입력받습니다.(쉼표를 기준으로 6개의 숫자를 입력받게 합니다.)
- [X] : 사용자로부터 보너스 번호를 입력받습니다.

2. 로또 발행 기능

- [X] : 구입 금액에 해당하는 수량의 로또를 발행한다. (로또 한 장의 가격은 1,000원)
- [X] : 1 ~ 45 까지의 숫자중에서 6개의 중복되지 않는 숫자가 포함된 로또를 발행합니다.
- [X] : 발행된 로또 번호는 오름차순으로 정렬하여 보여줘야 합니다.

3. 당첨 번호 검증 기능

- [ ] : 로또 번호와 당첨 번호를 비교하여 일치하는 숫자 개수를 확인해야 합니다.
- [ ] : 일치한 숫자 개수에 따라 등수를 판별하고 해당 당첨 금액을 계산합니다.


4. 출력 기능

- [X] : 구입금액에 따른 로또 티켓 구매 갯수를 출력합니다.
- [X] : 구매 갯수에 맞게 로또 번호를 개별적으로 출력합니다.
- [X] : 1등부터 5등까지의 당첨 결과를 출력합니다.
- [X] : 각 등수에 해당하는 당첨 개수도 함께 출력해야 합니다.

5. 수익률 계산 및 출력 기능

- [X] : 총 수익률을 계산하여 소수점 둘째 자리까지 반올림한 값을 출력합니다.
    - [X] : 수익률은 ((당첨금액/ 구입금액) * 100) 으로 계산됩니다.

6. 예외 처리 기능

- [ ] : 잘못된 값 입력 시 IllegalArgumentException을 발생시키고, [ERROR]로 시작하는 에러 메시지를 출력한다.

### 예외 사항

- [ ] : 입력된 구매 금액이 1,000원으로 나누어 떨어지지 않을 경우의 예외를 처리합니다.
- [ ] : 입력된 구매 금액이 0 혹은 음수일 경우도 예외를 처리합니다.
- [X] : 로또 번호는 1~45 사이의 정수여야 하며, 중복이 없어야 합니다.
- [ ] : 입력된 당첨 번호와 보너스 번호가 중복될 경우 예외로 처리합니다.
    - [ ] : 알파벳이나 특수 문자가 입력된 경우 예외로 처리합니다.
- [ ] : 입력된 당첨 번호가 6개가 아닐 경우 예외로 처리합니다.
- [ ] : 수익률이 정상적으로 계산되지 않는 경우도 예외로 처리합니다.
- [ ] : 올바른 형식으로 입력되지 않았을 때 에러 메시지를 출력하고 재입력을 유도합니다.

---

## **📌 Commit Message Format**

```
<type>(scope): <subject> - Subject line
<BLANK LINE>               - 줄 바꿈으로 구분한다.
<body>                     - Message body
```

- **Subject line**
    - 변경 사항에 대한 간단한 설명을 한다.
    - 70자를 넘기지 않도록 한다.
- **Message body**
    - 수정 이유와 전후 비교 설명을 한다.
    - 명령형 현재 시제로 작성한다.
    - 70자를 넘기면 줄바꿈한다.
