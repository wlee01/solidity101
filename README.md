# solidity101

# 🧠 솔리디티(Solidity)란?
✨ 한 줄 정의
Solidity는 이더리움 스마트 컨트랙트를 작성하는 프로그래밍 언어다.

Solidity는 블록체인 기술의 핵심인 "스마트 컨트랙트(Smart Contract)"를 만들기 위해 고안된 언어입니다.
기존의 중앙 서버가 아닌 탈중앙화된 네트워크 상에서 신뢰를 기반으로 자동으로 실행되는 계약을 작성할 수 있게 해줍니다.

쉽게 말해, Solidity는 "코드로 약속을 만드는 언어"입니다.

Solidity는 JavaScript, Python, C++에서 영감을 받아 설계되었으며, 개발자가 쉽게 접근할 수 있도록 문법이 직관적입니다. 
이더리움 가상 머신(EVM)에서 실행되며, 이더리움뿐만 아니라 Binance Smart Chain, Polygon 등 EVM 호환 네트워크에서도 활용됩니다.

Solidity 설치
Solidity는 다양한 개발 환경에서 실행할 수 있습니다. 기본적인 개발을 위해 Hardhat, Truffle, Remix IDE를 사용할 수 있습니다.

═════════════════════════════════════════════════════════════════════════════════════════════════════════

# Solidity 컴파일러 설치

npm install -g solc
또는 Hardhat과 함께 사용하려면:
npm install --save-dev hardhat

# 🤔 컴파일러(Compiler)란?

💡 정의
컴파일러(compiler)는 우리가 쓴 코드(고급 언어)를 컴퓨터가 이해할 수 있는 언어(바이트코드)로 바꿔주는 프로그램.

 📘 이름의 의미

- `compile` = 모으다, 정리하다, 번역하다  
- 어원: 라틴어 com- (함께) + pilare (모으다)

즉, 우리가 쓴 코드들을 한데 모아서(compile) 기계어로 바꿔주는 도구  

# 🛠️ Solidity에서는?

- Solidity 소스 코드는 `.sol` 파일에 작성됨
- 이걸 컴파일하면 → EVM(Ethereum Virtual Machine)이 이해할 수 있는 **바이트코드**로 변환됨
- 이 바이트코드를 블록체인에 배포하게 됨

═════════════════════════════════════════════════════════════════════════════════════════════════════════

# 🧠 정적 타입(static typing)이란?
✨ 핵심 개념 설명
정적 타입 언어란, 변수를 사용할 때 그 데이터의 "종류(타입)"를 코드에 명확히 적어줘야 하는 언어.

즉, "이 변수는 숫자다!", "이건 문자열이다!" 를 처음부터 선언해야 하는 언어다.

# 현실 비유	설명
서류 양식에 칸 정하기	나이: 숫자만 써라 / 이름: 글자만 써라 / 이메일: 이메일 형식만 써라

# ✅ 예: Solidity에서의 정적 타입 선언

uint256 age = 30;       // 숫자만 저장
string name = "Alice";  // 문자열만 저장
bool isActive = true;   // true/false만 저장

🧩 왜 Solidity는 정적 타입이어야 할까?

# 💰 블록체인 실행 비용 절감: 타입이 고정돼 있어 처리 속도가 빠르고 가스 소모 적음
# 🔐 보안성: 타입 오류로 인한 자산 손실 방지
# 🛑 에러 사전 차단: 배포 전에 컴파일러가 에러 감지 가능
# 🧱 예측 가능한 코드 실행: 스마트 컨트랙트는 예측 가능성이 중요함

- uint: 부호 없는 정수 → 예: uint age = 25;
- int: 부호 있는 정수 → 예: int temperature = -10;
- string: 문자열 → 예: string name = "Alice";
- bool: 논리값(true/false) → 예: bool isActive = true;
- address: 이더리움 주소 → 예: address user = msg.sender;
═════════════════════════════════════════════════════════════════════════════════════════════════════════

⚠️error⚠️

# Solidity에서 오류 처리란?
스마트 컨트랙트 실행 중 오류가 발생하면 트랜잭션이 즉시 중단되고, 모든 변경 사항이 롤백된다.
즉, 처음부터 아무 일도 없었던 것처럼 되돌아간다.

# 오류 처리 방법 3가지
require(조건, 메시지)
- 주로 입력값이나 조건 검증에 사용
- 조건이 false면 오류 발생 + 메시지 출력

# assert(조건)
- 내부 로직 검증용
- 실패 시 전체 가스 소모 → 주로 개발자 디버깅용

# revert(메시지)
- 명시적으로 실행 중단
- 조건문이 복잡할 때 코드 깔끔하게 정리할 수 있음

# 요약
require() → 가장 자주 사용, 안전한 입력 검증용
assert() → 내부 로직 오류 확인용, 실무에선 잘 안 씀
revert() → 명확하게 실패 처리할 때 사용

✅ pragma solidity란?
Solidity 파일의 최상단에 작성되는 지시문으로,
이 코드가 어떤 Solidity 컴파일러 버전에서 작동해야 하는지 명시합니다.

pragma solidity ^0.8.19;
📌 버전 명시를 하지 않으면 예상치 못한 오류나 취약점이 생길 수 있습니다.

═════════════════════════════════════════════════════════════════════════════════════════════════════════

🧠 Solidity에서 데이터 타입이란?

Solidity에서 "데이터 타입"은 스마트 컨트랙트가 변수를 저장하고 처리하는 방법을 정의하는 것입니다.  
이더리움 블록체인에서 데이터를 다루려면, 각 변수가 어떤 종류의 데이터를 저장할 것인지 명확히 지정해야 합니다.

Solidity의 데이터 타입은 크게 두 가지로 나뉩니다:
1. 값 타입 (Value Type)
2. 참조 타입 (Reference Type)

1️⃣ 값 타입 (Value Type)

값 타입은 변수가 **직접 데이터를 저장**하는 유형이며, 스마트 컨트랙트에서 가장 자주 사용됩니다.

- 정수형 (Integer)

  - `uint256`: 부호 없는 정수 (0 이상의 수)
  - `int256`: 부호 있는 정수 (음수 포함)
  - 예시:
    ```solidity
    uint256 public positiveNumber = 100;
    int256 public negativeNumber = -50;
    ```
  - ✅ `uint8 ~ uint256`, `int8 ~ int256`까지 8비트 단위로 다양한 크기 제공

- 불리언 (Boolean)

  - `true` 또는 `false` 값을 저장
  - 예시:
    ```solidity
    bool public isActive = true;
    ```

- 주소 (Address)

  - 이더리움 주소를 저장
  - 예시:
    ```solidity
    address public wallet = 0x1234567890abcdef1234567890abcdef12345678;
    address payable public recipient = payable(wallet);
    ```

- 바이트 (Bytes)

  - 고정 크기 바이트 배열 (`bytes1` ~ `bytes32`)
  - 예시:
    ```solidity
    bytes32 public data = "0xabcdef123456";
    ```
  - 📌 `bytes`는 가변 크기이므로 참조 타입으로 분류됨

- 열거형 (Enum)

  - 미리 정의된 값 중 하나만 선택 가능
  - 예시:
    ```solidity
    enum State { Created, Active, Inactive }
    State public state = State.Active;
    ```
  - 기본값은 첫 번째 값 (여기선 `State.Created`)

---

2️⃣ 데이터 타입을 올바르게 사용하는 이유

- ✅ 블록체인 저장 비용 절감
  - 가변 타입보다 고정 타입 사용 시 저장 비용(Gas) 감소
- ✅ 불필요한 연산 방지
  - 계산에 최적화된 타입을 사용하면 효율적
- ✅ 코드 오류 예방
  - 정적 타입 언어의 특성을 활용해 실수 방지

---
## 🔢 Solidity 숫자 타입 (Number Types)

Solidity에서 숫자 타입은 **정수(integer)**만 존재하며,  
실수(float)는 지원하지 않습니다.

숫자 타입은 크게 **부호 있는 정수(int)**와 **부호 없는 정수(uint)**로 나뉩니다.

---

# ✅ 1. 정수 타입 종류

- `uint`: 부호 없는 정수 (0 이상의 값만 저장)
- `int`: 부호 있는 정수 (음수와 양수 모두 저장 가능)

# 크기 단위
- 정수 타입은 **8비트 단위로 크기 지정** 가능
- 사용 예시:

  uint8    a = 255;        // 0 ~ 255
  uint256  b = 1000000;    // 0 ~ 2^256 - 1
  int8     c = -128;       // -128 ~ 127
  int256   d = -50000;     // -2^255 ~ 2^255 - 1

# ✅ 2. 숫자 타입을 사용하는 이유
💰 이더 단위 저장 (잔액, 금액, 수량 등)
🔐 조건 판단 (예: 특정 값 이상인지 확인)
🧮 계산 로직 수행 (세금, 포인트, 보상 등)

---

🔥 오버플로우(Overflow)
✅ 개념
변수에 저장할 수 있는 최댓값을 넘어서면
값이 0부터 다시 시작됨 → “되감기 현상”

🔢 예시: uint8 타입 (0 ~ 255)

uint8 x = 255;
x = x + 1; // 오버플로우 발생

# 결과 (Solidity 0.8.0 이전)
x의 최대값은 255
255 + 1 = ❌ 256 (불가능)
대신 다시 0으로 되감김

💥 언더플로우(Underflow)
✅ 개념
변수에서 0보다 작은 값을 만들려고 하면
최댓값으로 다시 돌아감

🔢 예시: uint8 타입 (0 ~ 255)

uint8 y = 0;
y = y - 1; // 언더플로우 발생

# 결과 (Solidity 0.8.0 이전)
0 - 1 = ❌ -1 (uint는 음수 불가)
y = 255; // 되돌아감 (wrap around)

═════════════════════════════════════════════════════════════════════════════════════════════════════════

📘 Solidity 불리언(Boolean) 타입 요약

1️⃣ 개념 정의
- Boolean은 `true` 또는 `false` 값을 갖는 논리 타입
- 조건문, 상태 변수, 접근 제어 등에서 사용

2️⃣ 기본 선언 및 초기값
- 선언 예시: `bool public isActive = true;`
- 초기화하지 않으면 기본값은 `false`

3️⃣ 조건문과 Boolean
- 비교 연산(예: `num > 10`)의 결과는 Boolean
- `if (조건)`은 내부적으로 `true`/`false`로 판단

4️⃣ 논리 연산자
- `&&` (AND): 둘 다 `true`일 때만 `true`
- `||` (OR): 하나라도 `true`면 `true`
- `!` (NOT): 값을 반전

5️⃣ 상태 제어 활용
- 불리언 값으로 기능 on/off 제어 가능
- 예: `votingOpen = false;` → 투표 종료

6️⃣ 접근 제어 활용
- `require(isAdmin)` 등으로 특정 조건 만족 시에만 함수 실행
- `modifier`와 함께 보안 체크 가능

7️⃣ 주의사항
- `bool`이라는 단어가 없어도 조건식은 Boolean 값
- 선언 후 값을 지정하지 않으면 기본값은 `false`

8️⃣ 실습 예시
```solidity
bool public isActive = true;

function toggle() public {
    isActive = !isActive;
}

function isAdult(uint age) public pure returns (bool) {
    return age >= 20;
}

