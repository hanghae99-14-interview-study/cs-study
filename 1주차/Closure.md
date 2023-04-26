## **Closure**

**Closure** **의 정의는 : 클로저는 함수와 그 함수가 선언된 렉시컬 환경과의 조합이다!.**

**먼저  **Closure 를 알아보기 전에 렉시컬 환경과 스코프 체이닝을 먼저 알고 접근하는 것이 좋다!!****

**렉시컬 환경 = LexicalEnvironment = LE라고 불리는데** **실행 컨텍스트 객체의 담기는 정보중에 하나입니다.**

**렉시컬 환경은 VE(VariableEnvironment)과 동일하지만**

**차이점은 VE는 최초 실행시에 Snapshot을 유지하지만 LE는 실시간으로 변경사항을 반영한다!**

**렉시컬 환경은 식별자 정보(record)와 외부 환경 정보(outer)를 갖고 있다.**

**여기서 확인해야할 것이 outer이다.**

**outer는 현재 호출된 함수가 선언될 당시의  LexicalEnvironment를 참조한다** 

**\= 그 당시의 환경 정보를 저장한다.**

**그림으로 설명을 해보자면**

<img src = "https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=https%3A%2F%2Fblog.kakaocdn.net%2Fdn%2FbQTUTR%2Fbtr94knKZd2%2F2UDbFIKIu2mgOa4xGWFQxk%2Fimg.png">

**a : 전역 context가 들어 올태고**

**b : a의 **LexicalEnvironment(외부 환경 정보)를 b의 outer로 가지고 있다!****

**c : b의 **LexicalEnvironment(외부 환경 정보)를 c의 outer로 가지고 있다!****

**d : c의 **LexicalEnvironment(외부 환경 정보)를 d의 outer로 가지고 있다! 가 됩니다!****

**Scope : 식별자에 대한 유효범위**

**Scope Chain : 식별자의 유효 범위를 안에서부터 바깥으로 차례대로 검색해 나가는 것**

**Global execute context에서**

**var, let, const가 Scope Chain이 어떻게 되는지 알아보겠습니다.**

<img src= "https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=https%3A%2F%2Fblog.kakaocdn.net%2Fdn%2FrjKq9%2Fbtr93nLLlnJ%2FL9ogtbtKrnd9XP1mLNFyB1%2Fimg.png">

**그냥 아무 식별자없이 n0 = 'n0'이라 선언을 했을때**

**n0은 script라는 Scope내부에 저장되는 것이 아니라 그 밖인 global에 저장되는 것을 알 수 있습니다.**

**global은 window라는 객체는 global scope갖기 때문에 global이라는 최상단scope에 저장됩니다.**

<img src = "https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=https%3A%2F%2Fblog.kakaocdn.net%2Fdn%2Fz3htL%2Fbtr95qOLhpH%2Fjzb63QLccO4ejbXKLadoak%2Fimg.png">

**그아래 var v0 = 'v0'으로 선언을 했을때도 마찬가지로 script가 아닌 global 저장된것을 확인할 수 있습니다.**

<img src="https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=https%3A%2F%2Fblog.kakaocdn.net%2Fdn%2FBelqy%2Fbtr900xoOCy%2FKPDirZB8kW7jXH1n224Ge0%2Fimg.png">

**let 과 const는 어디에 저장 되는지 보면**

<img src ="https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=https%3A%2F%2Fblog.kakaocdn.net%2Fdn%2FboSo8s%2Fbtr94iKktep%2FyklSE6BInvgtOpA4wsbMt1%2Fimg.png">

**let l0 = 'l0' 와 const c0 = 'co' 의 선언들은 script라는 스코프에 담기는것을 확인할 수 있습니다.**

<img src ="https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=https%3A%2F%2Fblog.kakaocdn.net%2Fdn%2FbgGHBa%2Fbtr91yN8d27%2FUkvKZK7RRejwsLT8dIuErk%2Fimg.png">

**그러면 이 console.log(window.v0, window.n0, window.l0, window.c0) 을 실행하면** 

**v0 n0 undefined undefined 가 출력됩니다! 왜냐하면** 

**v0와 n0는 global 스코프에 저장돼있기 때문에 출력이 되지만 안에서 바깥으로 **Scope Chain을 하기 때문에****

****Script 스코프에는 접근할 수 가 없어서 undefined가 출렵되는 겁니다.****

****다음은 Function execute context에서 실행될 때는 보겠습니다.****

**fn1 이라는 함수를 실행 시키면 안에 변수들은 어떤 스코프에 저장되는지 확인해 보면**

<img src ="https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=https%3A%2F%2Fblog.kakaocdn.net%2Fdn%2FDi29t%2Fbtr92trZaLm%2FooqqORiYLUbJCSpyh1SVqK%2Fimg.png">

**n1 = 'n1'은 아까 Global execute context에서 실행 했듯이 global scope에 저장되고**

**이번에는 var, let, const로 선언한 변수들은 새로운 Local scope에 저장되는 것을 확인할 수 있습니다.**

<img src = "https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=https%3A%2F%2Fblog.kakaocdn.net%2Fdn%2FmOuv4%2Fbtr94uw9BC4%2FetBKAVRnA2ZVbOn8FaJyzk%2Fimg.png">

정리를 해보자면!

| **global execute context** |  |
| --- | --- |
| a = 1 | global |
| var a = 1 | global |
| let a = 1 | script |
| const a = 1 | script |

| **function execute context** |  |
| --- | --- |
| a = 1 | global |
| var a = 1 | local |
| let a = 1 | local |
| const a = 1 | local |

**이 알아본 내용을 가지고 Closure를 보면 더욱 이해가 잘 될겁니다!**

**Closure의 규칙** 

**▶ 외부 함수보다 중접 함수가 더 오래 유지되는 경우**

**▶ ****외부 함수의**** 생명 주기가 종료 됐을때 (즉시 실행 함수)**

**▶ 중첩함수가 **외부 함수의 변수를 여전히 참조할 수 있을 때****

****예제를 보면서 확인해보겠 습니다!****

****Closure를 사용 하기 전****

```
// 카운트 상태 변수
let num = 0;

const increase = function () {
    // 카운트 상태를 1만큼 증가시킨다.
    return ++num;
};

console.log(increase());
// num = 100; // 치명적인 단점이 있어요.
console.log(increase());
console.log(increase());

// 보완해야 할 사항
// 1. 카운트 상태(num변수 값) => increase함수가 호출되기 전까지는 변경되지 x
// 2. 이를 위해서 count 상태는 increase 함수만이 변경!
// 3. 전역변수 num 요놈이 문제다. -> 지역변수
```

**Closure를 사용한 후!**

```
// 카운트 상태 변경 함수 
const increase = (function () {
  // 카운트 상태 변수
  let num = 0;

  // 클로저
  return function () {
    return ++num;
  };
})();

// 이전 상태값을 유지
console.log(increase()); //1
console.log(increase()); //2
console.log(increase()); //3

// [코드 설명]
// 1. 위 코드가 실행되면, '즉시 실행 함수' 가 호출!! 
// 2. 함수가 반환 (inner) -> increase에 할당
// 3. increase변수에 할당된 함수는 자신이 정의된 위치에 의해서 결정된
// 상위 스코프인 즉시 실행 함수의 '렉시컬 환경'을 기억하는 클로저 
// --> let num = 0 을 기억한다
// 3. 즉시 실행함수는 -> 즉시 소멸된다 
// 결론 : num은 초기화 x 외부에서 접근할 수 없는 은닉된 값!
```

**num의 값이 유지되는 이유**

<img src ="https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=https%3A%2F%2Fblog.kakaocdn.net%2Fdn%2Fbi3PHc%2FbtsakcpbD4C%2Fw8xWciKhVDabiOx1mvbtNK%2Fimg.png">

**num 변수는  Closure의 내부에 존재하며, **Closure는 함숙 정의된 위치의**   ****LexicalEnvironment환경을 기억합니다.******

******따라서 increase 함수가 반환된 후에도 num의 변수는 클로저 내부에 존재하며, 클로저가 참조하는 함수에는 num 변수를 계속해서 참조할 수 있습니다.******

**위에서 즉시 실행 함수를 사용 한 이유!**

**Closure의 규칙 외부 함수의 생명 주기가 종료 됐을때 를 지키기 위해 !**

**Closure를 사용하는 이유!**

**1\. 전역 변수 사용을 억제하고 전역변수의 문제점을 보안 하기 위해**

**▶ 전역변수의 문제점**

```
전역 변수는 모든 코드가 전역변수를 참조하고 변경할 수 있기때문에 상태가 변경 될 수 있는 위험성이 높다.

생명주기가 어플리케이션의 생명주기와 동일하기때문에 메모리 리소스도 오랜 기간 소비한다.

스코프 체인의 종점에 위치하기 때문에 변수 검색 속도가 느리다

자바스크립트는 파일이 분리 되어있다해도 하나의 전역 스코프를 공유하기때문에 
같은 스코프 내에 전역변수나 전역함수가 예상치 못한 결과를 가져올 수 있다.
```

**2\. 상태가 의도치 않게 변경되지 않도록 안전하게 은닉하고 특정 함수에게만 상태 변경을 허용하여 상태를 안전하게 변경하고 유지하기 위해 사용한다.**

**즉시실행함수를 그룹연산자(괄호) 로 감싸는 이유**

```
function () { // SyntaxError: Function statements require a function name
 // ...
}();
```

**이 코드의 경우 자바스크립트 엔진이 함수 선언문으로 해석하는 문맥이다. 함수 선언문의 경우 함수 이름을 생략할 수 없어서 에러가 발생한다.**

```
function foo() {
 // ...
}(); // SyntaxError: Unexpected token ')'
```

**이 코드의 경우 자바스크립트 엔진이 암묵적으로 수행하는 세미콜론 자동 삽입 기능에 의해 함수 선언문이 끝나는 위치에 세미콜론이 추가된다.**

```
function foo() {};(); 
```

**추가된 세미콜론 뒤에 괄호는 함수 호출 연산자가 아니라 그룹 연산자로 해석되고 그룹 연산자의 피연산자가 없기때문에 에러가 발생한다.**

**그룹 연산자로 즉시 실행 함수를 감싸는 이유는 함수를 평가해서 함수 객체를 생성하기 위해서다.**
