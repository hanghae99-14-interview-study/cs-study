<img src='https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=https%3A%2F%2Fblog.kakaocdn.net%2Fdn%2FdmofMj%2FbtsbTpumFCf%2FmopLD1vUkzW7ikRbjHnfFK%2Fimg.png'>

<br/>

# 시맨틱 태그!

## 시맨틱 태그란 ?

- 시맨틱(semantic)이라는 '의미의', '의미론적인'라는 뜻을 가진 형용사입니다.

- 즉 시맨틱 태그는 의미를 부여한 태그라는 뜻이 됩니다.

- &lt;div&gt; 태그에 의미를 부여했다고 생각하시면 이해가 편합니다.

- 이런 시맨틱 태그는 HTML5에서는 처음 등장했습니다.

- 예를 들자면 &lt;header&gt;나 &lt;footer&gt; 같은 태그들을 말합니다.

- 시맨틱 태그의 등장으로 인해 우리는 태그만 보고서도 문서를 더 쉽게 이해할 수 있게 되었습니다.

<br/>

## 시맨틱 태그를 사용해야 하는 이유!

### 1. HTML 문서의 가독성과 유지보수가 쉬워지기 때문입니다.

- 만약 모든 태그들을 div로 만들었다고 가정해봅시다. HTML 문서가 길어진다면 어디가 어느 부분인지, 어떤 영역인지 한눈에 파악하기가 힘들어지겠죠. 하지만 시맨틱 태그를 활용하면 유지보수를 할 때나 다른 작업자가 코드를 파악하기가 보다 쉬워집니다.

### 2. 웹 브라우저가 HTML만 보고도 상단(header), 본문(main), 하단(footer), 사이드(aside) 어느 영역인지 쉽게 알 수 있습니다.

- 이는 웹 접근성 시각에서 볼 때도 중요하게 사용됩니다. 예를 들어 시각장애인들이 사이트를 사용할 때 사용되는 화면의 텍스트를 읽어주는 스크린 리더기를 사용하여 페이지를 탐색할 때 도움이 됩니다.

### 3. 검색 엔진 최적화(SEO)

- 시멘틱 태그는 웹 페이지의 구조와 내용을 명확하게 정의하기 때문에 검색 엔진이 웹 페이지를 더 잘 이해할 수 있습니다. 이를 통해 검색 결과 페이지에서 노출되는 확률이 높아지며, 검색 엔진 순위를 높일 수 있습니다.

<br/>

## 웹사이트 구성 예시

- Sementic 요소들로 아래와 같이 직관적으로 웹사이트를 구성할 수 있습니다.

<img src='https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=https%3A%2F%2Fblog.kakaocdn.net%2Fdn%2Fbcjhw8%2FbtsbQ3FVH4z%2FkqZgzJtNX3ojhpZGo1GIk1%2Fimg.png'>

<br/>

## 시맨틱 태그 상세 설명

### `<header>`

<img src='https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=https%3A%2F%2Fblog.kakaocdn.net%2Fdn%2FwblPa%2FbtsbUpm2Ab2%2FquA8Y33ISRingVxq2pKlYK%2Fimg.jpg'>

- &lt;header&gt; 태그는 보통 사이트의 도입부, 즉 머릿 부분에 사용되며 사이트의 로고나 제목 등을 기술할 때 사용합니다. 하나의 구역이기에 &lt;header&gt; 태그 안에 부수적인 태그들이 추가로 들어갈 수 있으며 주로 &lt;form&gt; 태그를 사용해 검색창을 넣거나 &lt;nav&gt; 태그를 사용해 사이트 메뉴를 넣습니다. 때로는 사이트의 머리말이 들어갈 수도 있겠죠.

- 또한 HTML 문서 내에 여러 개의 &lt;header&gt; 태그를 작성하는 것 또한 가능합니다.

### `<main>`

<img src='https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=https%3A%2F%2Fblog.kakaocdn.net%2Fdn%2Fda9D2n%2FbtsbVboyA8Q%2FTJZpWOKk6QfygzK0hm99i0%2Fimg.png'>

- &lt;main&gt; 태그는 해당 페이지의 메인 콘텐츠를 나타낼 때 사용하며  반드시 한 번만 사용되어야 합니다. &lt;main&gt; 태그 내의 콘텐츠는 해당 문서의 중심이 되는 주제나 확장되는 콘텐츠로 구성되어야 하며, 문서 전반에 걸쳐 반복되는 내용을 포함해서는 안 됩니다.

### `<nav>`

<img src='https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=https%3A%2F%2Fblog.kakaocdn.net%2Fdn%2FdnD0IL%2FbtsbTV7BEx5%2Ffgyq6hRLJFtffqtQzarWs0%2Fimg.jpg'>

- &lt;nav&gt; 태그는 내비게이션 표현을 위한 태그로써 동일한 사이트 안의 문서나 다른 사이트의 문서로 연결하는 링크들의 모음을 나타냅니다. 이 태그를 사용하면 어느 부분이 내비게이션인지 쉽게 알 수 있습니다. &lt;nav&gt; 태그는 본문 위치에 영향을 받지 않습니다.

- 즉 &lt;header&gt;&lt;footer&gt;&lt;aside&gt; 태그들 안에 포함시킬 수도 있고 독립해서 사용할 수도 있습니다. 즉 &lt;body&gt; 태그 안에는 어디든지 사용이 가능합니다.

### `<hgroup>`

- &lt;hgroup&gt;은 제목과 부제목을 묶어서 나타내 주는 요소로 즉 &lt;h1&gt;, &lt;h2&gt;... 이렇게 연속해서 나올 때 묶어주기 위한 태그입니다. 페이지 전체 구조에 대한 개념으로 쉽게 눈에 들어오게 하는 역할을 담당합니다.

### `<footer>`

<img src='https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=https%3A%2F%2Fblog.kakaocdn.net%2Fdn%2F0AdFy%2FbtsbSMwo8aq%2Fb4slVpVXv3T2B5aKcHxIl1%2Fimg.jpg'>

- &lt;footer&gt; 태그는 일반적으로 웹 문서 끝자락에 들어가는 태그로 보통 저작권 정보나 저작권 표기와 같은 내용이 들어가는 부분입니다. &lt;footer&gt; 태그 안에  &lt;section&gt;, &lt;article&gt; 등 다른 레이아웃 태그들을 모두 사용할 수 있고 이런 태그들을 활용하여 푸터 안에 다양한 정보들을 넣을 수 있습니다.

### `<aside>`

<img src='https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=https%3A%2F%2Fblog.kakaocdn.net%2Fdn%2FcNNS6t%2FbtsbRyrVDH1%2FH3aaKytkgquHcDxK5LMCK0%2Fimg.jpg'>

- 블로그에서 왼쪽이나 오른쪽, 혹은 하단에 사이드바가 표현된 것을 본 적이 있으실 텐데요. 이렇게 웹 콘텐츠 제작 시 주 내용이 아닌 왼쪽이나 오른쪽에 부수적인 내용이 들어가는 부분을 &lt;aside&gt; 태그로 표현합니다.

- 특히 sidebar를 &lt;aside&gt; 태그를 사용하면 굉장히 편리합니다.

### `<article>`

<img src='https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=https%3A%2F%2Fblog.kakaocdn.net%2Fdn%2F3TVn7%2FbtsbVcntkmX%2FkbJcEj1EkxMXr1BKylo5mK%2Fimg.jpg'>

- &lt;article&gt; 태그는 웹페이지 상에서의 실제 내용을 의미합니다. 보통 블로그의 포스트나 웹사이트의 내용, 사용자가 등록한 코멘트, 독립적인 웹 콘텐츠 항목 등이 있으며 한마디로 정의하자면 태그를 적용한 부분을 떼어 내 독립적으로 배포하거나 재사용하더라도 완전히 하나의 콘텐츠가 된다면 &lt;article&gt; 태그를 사용하면 됩니다.

- 이렇게 &lt;article&gt; 태그를 사용한 웹 콘텐츠는 다른 곳에 배포하거나 재사용할 수 있습니다. 검색엔진의 검색로봇에서는 &lt;article&gt; 태그가 사용된 콘텐츠를 배포할 수 있는 콘텐츠로 인식합니다.

<br/>

## 시맨틱 태그 종류

| 태그            | 설명                                                                                                               |
| --------------- | ------------------------------------------------------------------------------------------------------------------ |
| &lt;header&gt;  | 사이트의 로고나 이름 등에 사용                                                                                     |
| &lt;nav&gt;     | 웹페이지의 메뉴를 만들 때 사용                                                                                     |
| &lt;main&gt;    | 메인 콘텐츠를 나타내는데 사용 안에 &lt;nav&gt;, &lt;aside&gt;, &lt;section&gt;, &lt;article&gt; 등이 포함되어있다. |
| &lt;section&gt; | 제목별로 나눌 수 있는 문서의 콘텐츠 영역을 구성하는 요소 &lt;article&gt;이 포함되어있다.                           |
| &lt;article&gt; | 개별 콘텐츠를 나타내는 요소 콘텐츠별로 여러개의 article을 사용할 수 있다.                                          |
| &lt;aside&gt;   | 좌우측의 사이드 영역 부분                                                                                          |
| &lt;footer&gt;  | 사이트의 바닥부분, 회사주소나, 연락처 등에 사용                                                                    |
| &lt;hgroup&gt;  | 제목과 부제목을 묶어서 나타내는 요소                                                                               |
| &lt;details&gt; | 열림 상태일 때만, 내부 정보를 보여주는 정보 공개 위젯을 생성                                                       |
| &lt;summary&gt; | 요약이나 레이블 &lt;details&gt; 요소에서 화면에 보일 제목(visible heading)을 명시할 때 사용합니다.                 |
| &lt;address&gt; | 사람, 단체, 조직등에 대한 연락처 정보를 나타냄                                                                     |
