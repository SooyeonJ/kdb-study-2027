# 2026년 11월 2주차 KDB IT 전공 스터디

- 출제자: 승혜
- 출제 과목: SE(소프트웨어공학), PL(프로그래밍언어)
- 출제 문항: 총 2문항
- 출제 유형: 서술형

---

## 문제 1. SE — 소프트웨어공학 (10점)

한 금융기관은 대출 신청 및 심사 시스템을 운영하고 있다. 현재 `LoanService`는 대출 신청 접수, 신용평가, 승인 처리, 고객 알림 발송을 모두 담당한다.

최근 대출 승인 기준이 변경되면서 승인 처리와 무관한 알림 기능까지 수정해야 했으며, 배포 이후 일부 고객에게 알림이 중복 발송되는 장애가 발생하였다.

개발팀은 다음과 같은 개선안을 제시하였다.

- (가) 신용평가, 승인 처리, 알림 발송 기능을 각각 독립적인 모듈로 분리한다.
- (나) 각 모듈은 구체적인 구현 클래스가 아닌 인터페이스를 통해 상호작용하도록 설계한다.
- (다) 기능 수정 후 관련 모듈 간 상호작용과 기존 기능의 정상 동작 여부를 검증한다.

### 물음

**(1) [3점]** (가)의 개선안과 관련하여 소프트웨어 설계에서 응집도(Cohesion)와 결합도(Coupling)의 바람직한 방향을 각각 기술하고, 그 이유를 설명하시오.

**(2) [3점]** (나)에 적용된 SOLID 설계 원칙의 명칭을 쓰고, 해당 원칙이 시스템 유지보수에 기여하는 이유를 설명하시오.

**(3) [4점]** (다)의 검증을 위해 적절한 소프트웨어 테스트 유형 두 가지를 제시하고, 각 테스트의 목적을 설명하시오.

---

## 문제 2. PL — 프로그래밍언어 (10점)

다음은 Java로 작성된 프로그램이다. 코드를 분석하고 물음에 답하시오.

```java
class Main {
    static class Account {
        int balance;

        Account(int balance) {
            this.balance = balance;
        }
    }

    static int update(Account a, Account b) {
        try {
            a.balance += 100;
            a = new Account(500);

            b.balance += a.balance;

            return a.balance + b.balance;
        } catch (Exception e) {
            return -1;
        } finally {
            a.balance += 200;
            b = new Account(1000);
        }
    }

    public static void main(String[] args) {
        Account x = new Account(100);
        Account y = new Account(200);

        int result = update(x, y);

        System.out.println(result);
        System.out.println(x.balance);
        System.out.println(y.balance);
    }
}
```

### 물음

**(1) [3점]** 위 프로그램의 출력 결과를 순서대로 작성하시오.

**(2) [3점]** `a = new Account(500)` 이후 `a.balance`를 변경하더라도 `x.balance`가 동일하게 변경되지 않는 이유를 Java의 매개변수 전달 방식과 관련지어 서술하시오.

**(3) [4점]** `finally` 블록은 `return`문이 실행되는 경우에도 수행된다. 위 코드에서 `finally` 실행이 반환값과 `y.balance`에 미치는 영향을 각각 설명하시오.
