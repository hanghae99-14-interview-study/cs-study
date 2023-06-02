# 예외와 에러처리

<aside>
💡 자바스크립트에서 예외와 에러처리

우리는 모두 예외 없는 상황에서 지내길 원하죠? 하지만 늘 예외는 따라다닙니다.
코드로 구현한 어플리케이션 역시 현실과 마찬가지 입니다.
아무리 볼륨이 작은 어플리케이션 이라도 우리의 의도와 다르게 예외가 발생할 수 있습니다.

좋은 코드란 예외가 하나도 없는 코드가 아니라 예외가 발생할 가능성을 늘 염두하고
적극적으로, 정당한 방식으로 예외처리를 하는 코드가 아닐까 싶습니다.

간단한 발표 이지만 오늘 발표를 듣는 분들이 예외처리에 대해 조금 덜 두려워 하실 수 있으면 너무 뿌듯한 시간이 될 것 같습니다.

발표는 간단한 코드를 작성하고 에러를 발생 시키면서
throw, try-catch, Promise async/await 등 다양한 방식으로 예외를 처리하는 형태로 진행될 예정입니다

발표에 앞서 간단히 예외에 대해 정의하고 가도록 하겠습니다. 자바스크립트로 코드를 작성하다보면 다양한 에러를 마주하게 되는데요. 오늘 예외와 에러처리 발표에서는 문법적인 오류나 정의되지 않은 객체를 참조하여서 자바스크립트 엔진이 발생시켜주는 에러가 아니라 우리가 작성한 코드 내에서 우리의 의도대로 실행되지 않았을때 발생하는 에러들. 즉, 로직 상의 의도되지 않은 처리를 예외로 정의하고 다루도록 하겠습니다.

</aside>

## thorw

```jsx
function calculater (x, y) {
    return x+y
}
```

간단한 코드를 작성했습니다. 코드를 설명하자면 x,y를 매개변수로 받고 해당 값을 더해서 리턴해주는 함수를 작성했습니다.

사용자가 값을 입력했다는 가정하에 인자로 값을 넣어주고 그 결과를 콘솔로 출력해 보면 다음과 같이 나옵니다.

```jsx
console.log( calculater(3, 7) )      // 출력 >> 10
console.log( calculater(6, 'zero') ) // 출력 >> 6zero
```

어떤 문법적 에러도 발생하지 않고 결과가 return 되는 것을 확인할 수 있습니다.

하지만 우리가 의도한 것은 숫자를 받아서 연산을 하는 것이었기 때문에 ‘zero’라는 문자열이 입력되면 에러를 발생시켜야 합니다. 이럴때 우리는 코드에서 thorw를 통해서 에러가 발생했음 을 알릴 수 있습니다.

```jsx
function calculater (x, y) {
    if(typeof x !== Number || typeof y !== Number){
        throw '숫자만 입력해주세요.'
    }
    return x+y
}
console.log( calculater(3, 7) )
console.log( calculater(6, 'ten') )
```

이렇게 코드를 작성하게 되면 두번째 입력에서 exception이 발생하고 throw 하게 됩니다. 

vsCode 에서 결과를 확인한 모습입니다.

![캡처1 (1).png](%E1%84%8B%E1%85%A8%E1%84%8B%E1%85%AC%E1%84%8B%E1%85%AA%20%E1%84%8B%E1%85%A6%E1%84%85%E1%85%A5%E1%84%8E%E1%85%A5%E1%84%85%E1%85%B5%200f50c2bdceeb4509b0761e6e5c1ef11b/%25E1%2584%258F%25E1%2585%25A2%25E1%2586%25B8%25E1%2584%258E%25E1%2585%25A51_(1).png)

어느 파일의 몇번째 라인에서 thorwo가 발생햇는지 알려줍니다. 여기서는 throw2.js 파일의 4번째 라인에서 에러가 발생했음을 알 수 있습니다.

throw로 스트링을 리턴할 경우 이렇게 throw가 발생했음만 알 수 있습니다.

여기서 node —trace-uncaught 옵션과 함께 실행하게 되면 다음과 같은 정보를 얻을 수 있습니다.

```bash
node --trace-uncaught throw2.js
```

![캡처2.png](%E1%84%8B%E1%85%A8%E1%84%8B%E1%85%AC%E1%84%8B%E1%85%AA%20%E1%84%8B%E1%85%A6%E1%84%85%E1%85%A5%E1%84%8E%E1%85%A5%E1%84%85%E1%85%B5%200f50c2bdceeb4509b0761e6e5c1ef11b/%25E1%2584%258F%25E1%2585%25A2%25E1%2586%25B8%25E1%2584%258E%25E1%2585%25A52.png)

어느 라인에서 호출했으며 어느 함수가 실행되다가 몇번째 throw를 타고 익셉션을 던져주었는지 까지 비교적 상세한 정보를 보여주고있습니다. 노드에서 제공하는 trace 옵션을 를 통해 우리는 이런 결과를 얻을 수 있는데요.

지금은 예시라서 간단한 코드기 때문에 이렇게 trace 옵션을 사용하지 않더라도 앞선 로그만으로도 throw가 어느곳에서 발생했는지 바로 알 수 있지만 코드가 복잡해질수록 단순히 문자열을 throw로 을 던지는 것만으로는 에러를 추적하기 어렵습니다.

## Error 객체

그래서 우리는 주로 Error 객체를 사용하게 됩니다. 

```jsx
function calculater (x, y) {
    if(typeof x !== Number || typeof y !== Number){
        throw new Error('숫자만 입력해주세요. 에러객체')
    }
    return x+y
}
console.log( calculater(3, 7) )
console.log( calculater(6, 'ten') )
```

```bash
node throw2.js
```

같은 오류를 에러 객체를 생성해서 담아주게 되면 trace옵션을 적용한 것 처럼 더 상세한 정보를 얻을 수 있습니다. 

![캡처3.png](%E1%84%8B%E1%85%A8%E1%84%8B%E1%85%AC%E1%84%8B%E1%85%AA%20%E1%84%8B%E1%85%A6%E1%84%85%E1%85%A5%E1%84%8E%E1%85%A5%E1%84%85%E1%85%B5%200f50c2bdceeb4509b0761e6e5c1ef11b/%25E1%2584%258F%25E1%2585%25A2%25E1%2586%25B8%25E1%2584%258E%25E1%2585%25A53.png)

이는 에러 객체에는 현재 콜스택 정보가 같이 담기기 때문입니다.

Error 객체는 instanceof 연산자를 써서 ERROR 인스턴스가 반환되는지 여부를 확인하는 형태로도 사용 가능합니다.

```jsx
const email_test1 = "test1@test.com"
const email_test2 = "test2(a)test.com"

/** 
 * '@'기호가 있으면 정상적인 이메일로 체크, 이메일을 리턴한다,
 * 아니라면 에러를 리턴한다.
 */
function validateEmail (email) {
    if(email.match(/@/)){
        return email
    }else{
        return new Error('이메일 유효성 검사 실패 : '+email)
    }
}

function emailIsOk (email) {
    const returnValidated = validateEmail(email)
    if (returnValidated instanceof Error){
        console.log("Error 메세지 :"+returnValidated.message)
    }else{
        console.log("Email 검사가 완료되었습니다. "+email )
    }
}

//실행
emailIsOk(email_test1)
emailIsOk(email_test2)
```

![스크린샷 2023-05-05 오전 1.08.42.png](%E1%84%8B%E1%85%A8%E1%84%8B%E1%85%AC%E1%84%8B%E1%85%AA%20%E1%84%8B%E1%85%A6%E1%84%85%E1%85%A5%E1%84%8E%E1%85%A5%E1%84%85%E1%85%B5%200f50c2bdceeb4509b0761e6e5c1ef11b/%25E1%2584%2589%25E1%2585%25B3%25E1%2584%258F%25E1%2585%25B3%25E1%2584%2585%25E1%2585%25B5%25E1%2586%25AB%25E1%2584%2589%25E1%2585%25A3%25E1%2586%25BA_2023-05-05_%25E1%2584%258B%25E1%2585%25A9%25E1%2584%258C%25E1%2585%25A5%25E1%2586%25AB_1.08.42.png)

정상적인 이메일을 넣었을 때와 아닐때를 validateEmail 함수에서 구분해서 Error 인스턴스를 넘겨주고, validateEmail 함수를 호출하는 곳에서 instanceof 연산자를 통해 Error 객체가 있는지 여부를 확인하고 있습니다. 이렇게 되면 에러가 발생하더라도 멈추지 않고 대응해서 다른 동작을 이어서 할 수 있도록 하게됩니다.

자바스크립트는 예외 처리시 어느 형태로든 리턴이 가능하지만 Error 인스턴스를 넘기는 것이 가장 기본적이고 편리하다고 할 수 있습니다.

에러가 발생했을때 에러가 발생한것은 인식은 하지만 그에 따라 처리하는 것을 에러처리한다고 합니다.

에러 인스턴스를 사용하면 에러를 인식하고 처리까지 가능합니다.

그런데 이렇게 instanceof를 활용하는 것도 좋지만 Error 객체는 try/catch와 함께할때 가장 빛을 발합니다.

## try/catch

try…catch를 통해 에러가 발생할 경우 그 에러에 따른 처리흐름을 변경할 수 있습니다.

만약 개발자가 예상하지 못한 에러가 발생하면 어떻게 될까요? 위의 예시코드를 활용해 보겠습니다.

```jsx
const email_test1 = null
const email_test2 = "test2(a)test.com"

/** 
 * '@'기호가 있으면 정상적인 이메일로 체크, 이메일을 리턴한다,
 * 아니라면 에러를 리턴한다.
 */
function validateEmail (email) {
    if(email.match(/@/)){
        return email
    }else{
        return new Error('이메일 유효성 검사 실패 : '+email)
    }
}

function emailIsOk (email) {
    const returnValidated = validateEmail(email)
    if (returnValidated instanceof Error){
        console.log("Error 있을 유 :"+returnValidated.message)
    }else{
        console.log("Email 검사가 완료되었습니다."+email )
    }
}

//실행
emailIsOk(email_test1)
emailIsOk(email_test2)
```

null이 들어올 것이라는 예상을 하지 못해서 처리하지 못했고 에러가 발생하면서 프로그램 동작이 종료됩니다. 

![캡처5.png](%E1%84%8B%E1%85%A8%E1%84%8B%E1%85%AC%E1%84%8B%E1%85%AA%20%E1%84%8B%E1%85%A6%E1%84%85%E1%85%A5%E1%84%8E%E1%85%A5%E1%84%85%E1%85%B5%200f50c2bdceeb4509b0761e6e5c1ef11b/%25E1%2584%258F%25E1%2585%25A2%25E1%2586%25B8%25E1%2584%258E%25E1%2585%25A55.png)

이렇게 예상치 못한 에러에 대응하기 위해 try/catch문을 사용합니다.

emailIsOk를 try/catch로 감싸주었습니다.

```jsx
const email_test1 = null
const email_test2 = "test2(a)test.com"

/** 
 * '@'기호가 있으면 정상적인 이메일로 체크, 이메일을 리턴한다,
 * 아니라면 에러를 리턴한다.
 */
function validateEmail(email) {
    if (email.match(/@/)) {
        return email
    } else {
        return new Error('이메일 유효성 검사 실패 : ' + email)
    }
}

function emailIsOk(email) {
    try {
        const returnValidated = validateEmail(email)
        if (returnValidated instanceof Error) {
            console.log("Error 있을 유 :" + returnValidated.message)
        } else {
            console.log("Email 검사가 완료되었습니다." + email)
        }
    } catch (error) {
        console.log("예상치 못한 에러가 발생했습니다.",error.message)
    }

}

//실행
emailIsOk(email_test1)
emailIsOk(email_test2)
```

![스크린샷 2023-05-05 오전 1.57.51.png](%E1%84%8B%E1%85%A8%E1%84%8B%E1%85%AC%E1%84%8B%E1%85%AA%20%E1%84%8B%E1%85%A6%E1%84%85%E1%85%A5%E1%84%8E%E1%85%A5%E1%84%85%E1%85%B5%200f50c2bdceeb4509b0761e6e5c1ef11b/%25E1%2584%2589%25E1%2585%25B3%25E1%2584%258F%25E1%2585%25B3%25E1%2584%2585%25E1%2585%25B5%25E1%2586%25AB%25E1%2584%2589%25E1%2585%25A3%25E1%2586%25BA_2023-05-05_%25E1%2584%258B%25E1%2585%25A9%25E1%2584%258C%25E1%2585%25A5%25E1%2586%25AB_1.57.51.png)

에러가 발생한 것에 대해 catch 블록의 흐름을 처리하고 뒤의 내용도 멈추지 않고 처리하는 것을 볼 수 있다.

## Promise

## async/await
