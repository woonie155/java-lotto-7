# java-lotto-precourse

## 기능 목록

1. 간단한 로또 발매기

   1.1 금액 입력 기능
    1. 안내문구를 출력한다.
    2. 금액을 입력받는다.
    3. 예외 처리
        - 1000 단위의 양수가 아닌 입력인 경우
        - 100개를 초과해 구매하는 경우

   1.2 로또 발행 기능
    1. 발행 결과를 출력한다.
    2. 구입 금액에 해당하는 만큼 발행한다.
    3. 각 로또는 1~45 사이의 중복되지 않는 6개의 양수와 오름차순으로 발행된다.

   1.3 당첨 번호 입력 기능
    1. 안내문구를 출력한다.
    2. 5개의 번호를 쉼표로 구분해 입력받는다.
    3. 예외 처리
        - 양수와 쉼표가 아닌 입력인 경우
        - 총 5개의 번호가 입력되지 않은 경우
        - 1~45 사이의 값이 아닌 입력인 경우
        - 중복된 번호가 입력된 경우

   1.4 보너스 번호 입력 기능
    1. 안내문구를 출력한다.
    2. 1개의 번호를 입력받는다.
    3. 예외 처리
        - 총 1개의 번호가 입력되지 않은 경우
        - 1~45 사이의 값이 아닌 입력인 경우
        - 당첨 번호와 중복된 번호인 경우

   1.5 사용자 결과 확인 기능
    1. 결과를 출력한다.
    2. 당첨 통계를 계산한다.
    3. 수익률을 계산한다.

---

## 기능 요구 사항

```
1. 로또 번호의 숫자 범위는 1~45까지이다.
2. 1개의 로또를 발행할 때 중복되지 않는 6개의 숫자를 뽑는다.
3. 당첨 번호 추첨 시 중복되지 않는 숫자 6개와 보너스 번호 1개를 뽑는다.
4. 당첨은 1등부터 5등까지 있다. 당첨 기준과 금액은 아래와 같다.
   1등: 6개 번호 일치 / 2,000,000,000원
   2등: 5개 번호 + 보너스 번호 일치 / 30,000,000원
   3등: 5개 번호 일치 / 1,500,000원
   4등: 4개 번호 일치 / 50,000원
   5등: 3개 번호 일치 / 5,000원
5. 로또 구입 금액을 입력하면 구입 금액에 해당하는 만큼 로또를 발행해야 한다.
6. 로또 1장의 가격은 1,000원이다.
7. 당첨 번호와 보너스 번호를 입력받는다.
8. 사용자가 구매한 로또 번호와 당첨 번호를 비교하여 당첨 내역 및 수익률을 출력하고 로또 게임을 종료한다.
9. 사용자가 잘못된 값을 입력할 경우 IllegalArgumentException을 발생시키고, "[ERROR]"로 시작하는 에러 메시지를 출력 후 그 부분부터 입력을 다시 받는다.
   Exception이 아닌 IllegalArgumentException, IllegalStateException 등과 같은 명확한 유형을 처리한다.
```

### 입력 요구사항

1. 로또 구입 금액을 입력 받는다. 구입 금액은 1,000원 단위로 입력 받으며 1,000원으로 나누어 떨어지지 않는 경우 예외 처리한다.

   ```14000```

2. 당첨 번호를 입력 받는다. 번호는 쉼표(,)를 기준으로 구분한다.

   ```1,2,3,4,5,6```

3. 보너스 번호를 입력 받는다.

   ```7```

### 출력 요구사항

1. 발행한 로또 수량 및 번호를 출력한다. 로또 번호는 오름차순으로 정렬하여 보여준다.

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

2. 당첨 내역을 출력한다.

```
3개 일치 (5,000원) - 1개
4개 일치 (50,000원) - 0개
5개 일치 (1,500,000원) - 0개
5개 일치, 보너스 볼 일치 (30,000,000원) - 0개
6개 일치 (2,000,000,000원) - 0개
```

3. 수익률은 소수점 둘째 자리에서 반올림한다. (ex. 100.0%, 51.5%, 1,000,000.0%)

```
총 수익률은 62.5%입니다.
```

4. 예외 상황 시 에러 문구를 출력해야 한다. 단, 에러 문구는 "[ERROR]"로 시작해야 한다.

```
[ERROR] 로또 번호는 1부터 45 사이의 숫자여야 합니다.
```

### 실행 결과 예시

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