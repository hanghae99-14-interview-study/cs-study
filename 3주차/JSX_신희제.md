<img src='https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=https%3A%2F%2Fblog.kakaocdn.net%2Fdn%2FkGd94%2FbtscZqF8SMO%2FrCSJLY0dkcSRx1lP6K0GK1%2Fimg.png'>

#### **JSX**

**JSX(JavaScript XML)는 Javascript에 XML을 추가하여 확장한 문법입니다.**

**JSX는 리액트로 프로젝트를 개발할 때 사용되므로 공식적인 자바스크립트 문법은 아닙니다.**

**브라우저에서 실행하기 전에 바벨을 사용하여 일반 자바스크립트 형태의 코드로 변환된다.**

**바벨(Babel)은 Node.js에서 실행되며 최신 JavaScript 코드를 구 버전 Javascript 코드로 변환해 주는 도구입니다.**

**최신 Javascript 기능이 추가된 코드를 작성하더라도,**

**이전 버전의 브라우저에서도 실행 가능한 코드로 변환해주는 것이 바벨의 역할입니다.**

```
// JSX예시
function App () {
	return (
    	<h1>Hello!</h1>
    )
}


// 위 처럼 작성하면, 바벨이 다음과 같이 자바스크립트로 해석하여 준다.
function App () {
	return React.createElement("h1", null, "Hello!"
}
```

**JSX는 하나의 파일에 자바스크립트와 HTML을 동시에 작성하여 편리하다.**

**자바스크립트에서 HTML을 작성하듯이 하기 때문에 가독성이 높고 작성하기 쉽다.**

#### **JSX 문법**

**1\. 반드시 부모 요소 하나가 감싸는 형태여야 한다.**

**\- Virtual DOM에서 컴포넌트 변화를 감지할 때 효율적으로 비교할 수 있도록 컴포넌트 내부는**

**하나의 DOM 트리 구조로 이루어져야 한다는 규칙이 있다.**

```
function App () {
	return (
    	<div>
        	<div>Hello</div>
        </div>
    )
}
```

```
function App () {
	return (
    	<>
        	<div>Hello</div>
        </>
    )
}
```

#### **표현식**

**2\. JSX 안에서도 자바스크립트 표현식을 사용할 수 있다.** 

**자바스크립트 표현식을 작성하려면 JSX내부에서 코드를 {}로 감싸주면 된다.**

```
function App () {
	const name = '신희제'
    return (
    	<div>
        	<div>{name}</div>
        </div>
    )
}
```

**3\. if문(for문) 대신 삼항 연산자 (조건부 연산자) 사용**

**if 구문과 for 루프는 Javascript 표현식이 아니기 때문에 JSX 내부 자바스크립트**

**표현식에서는 사용할 수 없다.**

**왜냐하면 **JSX 내부에서 사용되는 Javascript 코드는 모두 표현식이어야 하며 값을 반환 합니다.****

**if 구문과 for문은 표현식이 아니라 제어구조라 값을 반환 하지 않기 **때문에 사용하지 못합니다.****

****그렇기 때문에 {}안에서 삼항 연산자(조건부 연산자)를 사용 한다.****

****외부에서 사용 : if문****

```
function App() {
	let desc = '';
	const loginYn = 'Y';
	if(loginYn === 'Y') {
		desc = <div>회원 입니다.</div>;
	} else {
		desc = <div>비회원 입니다.</div>;
	}
	return (
		<>
			{desc}
		</>
	);
}
```

****외부에서 사용 : 삼항 연산자****

```
function App() {
	const loginYn = 'Y';
	return (
		<>
			<div>
				{loginYn === 'Y' ? (
					<div>회원 입니다.</div>
				) : (
					<div>비회원 입니다.</div>
				)}
			</div>
		</>
	);
}
```

**3\. class 대신 className**

**일반 HTML에서 CSS 클래스를 사용할 때에는 class 라는 속성을 사용하지만**

**JSX에서는 class가 아닌 className을 사용한다.**

```
function App() {
	return (
		<div className="testClass">Hello, GodDaeHee!</div>
	);
}
```

**4\. 꼭 닫혀 있어야 하는 태그 문법**

**태그는 무조건 닫혀 있어야 한다.**

**일반태그들은 닫혀있지만, 종료태그가 없는 태그는 반드시 /> 처리를 해줘야 합니다.**

**JSX에서 종료 태그를 사용하지 않을 경우, 빌드 시 경고 메시지가 발생할 수 있습니다.**

**이러한 경고는 코드를 디버깅할 때 혼란스러울 수 있기 때문에 종료 태그를 사용하는 것이 좋습니다.**
