---
title:  "[React] Hello React"
date: 2020-03-31
categories: ['React']
tags: ['React', '리액트']
---

## 1. React 프로젝트 생성

- 명령 프롬프트에 아래 구문을 작성

```
yarn create react-app 프로젝트 이름
```

- 예시

```
yarn create react-app 01-hello-react
```
<br>

## 2. JS 파일 생성

- 01-hello-react를 생성한 후 아래의 그림과 같이 `MyComponent1.js`,`MyComponent2.js`,`MySubComponent.js`를 생성한다.

![hello](/assets/Images/react/chapter2/1_hello.JPG)


## 3. index.js

```javascript
/* 프로그램 시작점. 향후 redux라는 패키지를 사용하기 전까지는 작업 안함.*/

import React from 'react';
import ReactDOM from 'react-dom';
// import './index.css';

// 이 소스파일과 동일한 위치의 APP.js("./App")를 App이라는 이름으로 가져온다.
import App from './App';
import * as serviceWorker from './serviceWorker';


/* 컴포넌트를 페이지에 렌더링한다.*/
// App.js에서 정의한 'App'이라는 이름의 컴포넌트를 HTML 태그처럼 사용한다.
// -> 첫 번째 파라미터 : 사용할 컴포넌트
// -> 두 번째 파라미터 : 컴포넌트를 출력할 pulbic/index.html 페이지에 정의되어 있는 요소
// 프로그램 실행시 'http://localhost:3000/'에 대응되는 위치가 public 폴더

ReactDOM.render(
    <React.StrictMode>
    <App />
  </React.StrictMode>,
    document.getElementById('root')
);

// If you want your app to work offline and load faster, you can change
// unregister() to register() below. Note this comes with some pitfalls.
// Learn more about service workers: https://bit.ly/CRA-PWA
serviceWorker.unregister();
```
<br>

## 4. App.js

```javascript
/*
  필요한 패키지 참조하기
  - 패키지 경로에 "./"나 "../"가 있는 경우
   -> 현재 소스를 기준으로 한 상대경로로 소스파일을 참조함.
  - 패키지 경로가 단어로 시작되는 경우
   -> node_modules에서 패키지를 검색하여 참조함.
*/

// 리액트 패키지 참조 (필수)
import React from 'react';
// import logo from './logo.svg';
// import './App.css';

// 직접 작성한 컴포넌트 참조
import Hello from './MyComponent1.js';
import World from './MyComponent2.js';

/** App이라는 이름의 함수형 컴포넌트 (재사용 가능한 HTML 조각단위) 정의*/
// 프로젝트에서 컴포넌트를 랜더링(화면에 출력)하면 함수에서 반환하고 있는 내용이 브라우저에 나타난다.
// 반환되는 HTML 코드는 JSX 문법을 사용한다.
// JSX ->XML과 비슷한 react 전용 Javascript 확장 문법
function App() {
    return (
        /*
        <div className="App">
      <header className="App-header">
        <img src={logo} className="App-logo" alt="logo" />
        <p>
          Edit <code>src/App.js</code> and save to reload.
        </p>
        <a
          className="App-link"
          href="https://reactjs.org"
          target="_blank"
          rel="noopener noreferrer"
        >
          Learn React
        </a>
      </header>
    </div>*/
        <div>
      <h1>Hello React</h1>
      <Hello />
      <World />
    </div>
    );
}

export default App;
```
<br>

## 5. MyComponent1.js

```javascript
// react 기본 패키지 참조(필수)
import React from 'react';

//직접 작성한 컴포넌트 참조 -> 정의한 이름을 HTML 태그처럼 사용.
import MySubComponent from './MySubComponent.js';

/**
	함수형 컴포넌트 정의
		- 함수 이름은 혼선을 방지하기 위해 소스파일 이름과 동일하게 구성하는 것이 일반적
*/
function MyComponent1() {
    // 리턴은 항상 HTML 구조를 의미하는 JSX 문법이어야 하고,
    // JSX 구조는 무조건 단 하나의 태그요소 하나에 모두 포함되어야 한다는 의미
    return (
        <div>
			<h2>안녕하세요 리액트</h2>
			<p>리액트 컴포넌트 구조 연습입니다.</p>
		{/*컴포넌트는 재사용 가능함*/}
		<MySubComponent/>
		<MySubComponent/>
		<MySubComponent/>
		<MySubComponent/>
		</div>
    );
}

// 이 소스파일에서 정의하는 기능을
// 이 파일을 import하는 다른 파일에서 참조할 수 있도록 내보낸다.
export default MyComponent1;
```
<br>

## 6. MyComponent2.js

```javascript
import React from 'react';

//직접 작성한 컴포넌트 참조 -> 정의한 이름을 HTML 태그처럼 사용.
import MySubComponent from './MySubComponent.js';

/**함수형 컴포넌트를 익명 함수 스타일로 정의*/
const MyComponent2 = function() {
    return (
        <div>
			<h2>Virtual DOM</h2>
			<p>This is React Component</p>
			<MySubComponent />
		</div>
    );
}

export default MyComponent2;
```
<br>

## 7. MySubComponent.js

```javascript
import React from "react";

const MySubComponent = () => {
    return (
        <div>
			<ul>
				<li>item1</li>
				<li>item2</li>
				<li>item3</li>
			</ul>
		</div>
    );
};

export default MySubComponent;
```

## 8. 출력결과

명령프롬프트에 해당 파일(01-hello-react)이 위치한 곳으로 이동한 후 아래의 명령어 입력

```
yarn start
```

![react 결과](/assets/Images/react/chapter2/2_output.JPG)

참조 : 호쌤의 교육자료, (<https://blog.itpaper.co.kr/>)