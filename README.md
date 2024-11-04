# 🎉로또🎉

<br>

## 📌 프로젝트 소개
<p><i> "엄마.. 나 로또 당첨됐어..." </i></p>
<p>간단한 <b>로또 발매기</b>를 구현한다.</p>
<p>사용자는 로또를 여러 장 구매할 수 있으며, 구매 금액 대비 당첨금의 비율인 수익률을 구해보자.</p>
<p>과연 로또는 남는 장사일까?</p>

<br>

## 🛠️ 기능 요구 사항
* 로또 번호의 숫자 범위는 1~45까지이다.
* 1개의 로또를 발행할 때 중복되지 않는 6개의 숫자를 뽑는다.
* 당첨 번호 추첨 시 중복되지 않는 숫자 6개와 보너스 번호 1개를 뽑는다.
* 당첨은 1등부터 5등까지 있다. 당첨 기준과 금액은 아래와 같다.
```plaintext
    - 1등: 6개 번호 일치 / 2,000,000,000원
    - 2등: 5개 번호 + 보너스 번호 일치 / 30,000,000원
    - 3등: 5개 번호 일치 / 1,500,000원
    - 4등: 4개 번호 일치 / 50,000원
    - 5등: 3개 번호 일치 / 5,000원
```
* 로또 구입 금액을 입력하면 구입 금액에 해당하는 만큼 로또를 발행해야 한다.
* 로또 1장의 가격은 1,000원이다.
* 당첨 번호와 보너스 번호를 입력받는다.
* 사용자가 구매한 로또 번호와 당첨 번호를 비교하여 당첨 내역 및 수익률을 출력하고 로또 게임을 종료한다.
* 사용자가 잘못된 값을 입력할 경우 IllegalArgumentException을 발생시키고, "[ERROR]"로 시작하는 에러 메시지를 출력 후 그 부분부터 입력을 다시 받는다.
* Exception이 아닌 IllegalArgumentException, IllegalStateException 등과 같은 명확한 유형을 처리한다.


<br>

## 📝 주요 기능 목록

### 1. 입력 기능 및 유효성 검사
- **로또 구입 금액 입력**
  - 로또 구입 금액을 입력 받는다. 
  - 구입 금액은 1,000원 단위이며, 1,000으로 나누어 떨어지지 않을 시 예외 처리한다.
  - 양의 정수 값이 아닌 입력 시 예외 처리한다.
  - 공백 입력 시 예외 처리한다.
- **당첨 번호 입력**
  - 당첨 번호를 입력 받는다. 
  - 당첨 번호는 쉼표(,)를 기준으로 구분한 6자리 숫자이며, 각 숫자는 1에서 45 사이의 중복되지 않는 값을 가진다. 
  - 당첨 번호가 6자리가 아닐 시 예외 처리한다.
  - 하나의 당첨 번호라도 1과 45 사이의 값을 벗어날 시 예외 처리한다.
  - 당첨 번호 간의 중복된 값이 있을 시 예외 처리한다.
  - 당첨 번호 입력 시, 문자 사이의 여백을 허용한다.
- **보너스 번호 입력**
  - 보너스 번호를 입력 받는다.
  - 보너스 번호는 1과 45 사이의 값을 가지며, 이에 위배될 시 예외 처리한다.
  - 숫자가 아닌 값 혹은 공백 입력 시 예외 처리한다.

### 2. 출력 기능
- **발행 로또 수량 및 번호 출력**
  - 발행한 로또의 정보를 출력한다. 로또 번호는 오름차순으로 출력한다.
- **당첨 내역 출력**
  - 당첨 수량, 당첨 금액 등의 내역을 출력한다.
- **수익률 출력**
  - 소수점 둘째 자리에서 반올림한 수익률을 출력한다. (ex. 100.0%, 51.5%, 1,000,000.0%)
- **예외 상황 시 에러 출력**
  - 예외 상황이 발생할 시, 해당 에러에 대한 에러 문구를 출력한다.
  - 에러 문구는 "[ERROR]"로 시작한다.

### 3. 로또 객체 관련 기능
- **로또 발행**
  - 구입 금액에 맞는 로또 개수를 구하여 발행한다.
  - 이 때 발행하는 로또 번호는 오름차순으로 정렬한다.
- **로또 당첨**
  - 당첨 번호와 로또 번호들을 비교하여 당첨 현황을 저장 및 출력한다.
- **로또 매니저**
  - 로또 객체를 관리하는 매니저 클래스이다.
    - 금액 대비 로또 발행
    - 로또 당첨 비교 및 수익률 계산 / 출력
    - 로또 티켓 시각화
    - Rank : enum class

<br>

## 💻 실행 예시

```plaintext
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