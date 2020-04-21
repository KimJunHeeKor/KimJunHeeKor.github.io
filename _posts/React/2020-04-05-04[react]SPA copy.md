---
title:  "[React] JSX"
date: 2020-04-05
categories: ['React']
tags: ['React', '리액트']
---

## 1. JSX

JSX : Javascript를 확장한 문법(JavaScript + XML)

<br>

## 2. 예제 작성 트리

![tree](/assets/Images/react/chapter4/1_tree.JPG)

<br>

## 3. App.js

```js
import React from 'react';
import { Route, Link, Switch} from "react-router-dom";

/** 각 예제별 컴포넌트 import */
import Expr from "./pages/Expr";
import If1 from "./pages/If1";
import If2 from "./pages/If2";
import If3 from "./pages/If3";
import If4 from "./pages/If4";
import Loop1 from "./pages/Loop1";
import Loop2 from "./pages/Loop2";
import Loop3 from "./pages/Loop3";

function App() {
  return (
    <div>
      <h1>03-jsx</h1>
      {/* Link 구성 */}
      <Link to="/expr">[Expr]</Link>
      <Link to="/If1">[If1]</Link>
      <Link to="/If2">[If2]</Link>
      <Link to="/If3">[If3]</Link>
      <Link to="/If4">[If4]</Link>
      <Link to="/Loop1">[Loop1]</Link>
      <Link to="/Loop2">[Loop2]</Link>
      <Link to="/Loop3">[Loop3]</Link>
      <hr/>
      {/* 각 예제 페이지 Route 적용 */}
      <Switch>
        <Route path='/expr' component={Expr} />
        <Route path='/If1' component={If1} />
        <Route path='/If2' component={If2} />
        <Route path='/If3' component={If3} />
        <Route path='/If4' component={If4} />
        <Route path='/Loop1' component={Loop1} />
        <Route path='/Loop2' component={Loop2} />
        <Route path='/Loop3' component={Loop3} />
      </Switch>
    </div>
  );
}

export default App;
```

![home](/assets/Images/react/chapter4/2_home.JPG)

<br>

## 3. Expr.js

```js
import React from 'react';

/** 기본 표현식 연습 */
const Expr = () => {
    /** 사용자 정의 변수 */
    const name ="리엑트";
    const age = 19;
    const color = "#f00";
    const message = "리엑트는 가장 주목받는 프론트엔드 프레임워크 입니다.";

    /** 개발자가 직접 정의한 함수 */
    const myEllipsis = (message, len) => {
        let str = message;
        if (str.length > len) {
            str = str.substring(0, len) + "...";
        }
        return str;
    };
    return (
        <div>
            <h2>Expr <small>(jsx 기본 표현식)</small></h2>

            {/* 기본 변수 출력하기 - 간단한 사칙연산 가능 */}
            <h3>{name}님은 {age+1}세 입니다.</h3>
            <p>
                <font color="#00f">{name}</font>님은&nbsp;
                {/* HTML 속성에 변수를 출력할 경우 따옴표를 사용할 수 없다. */}
                <font color={color}>리액트 개발자</font>입니다.
            </p>

            {/* 사용자 정의 함수 호출하기 */}
            <blockquote>
                {myEllipsis(message, 15)}
            </blockquote>
        </div>
    );
};

export default Expr;
```

![expr](/assets/Images/react/chapter4/3_expr.JPG)

<br>

## 4. lf1.js

```js
import React from 'react';

/** JSX 조건분기(1) - 함수를 통한 리턴값 분기 */
const If1 = () => {
    /** 조건에 따라 다른 jsx를 반환하는 함수 정의 */
    function btnLogin(isLogin) {
        if (isLogin ===true ) {
            return <button type='button'> Logout</button>;
        } else {
            return <button type = 'button'>Login</button>;
        }
    }

    // 조건에 따라 다른 결과를 표시하는 첫 번째 방법은 호출하는 함수안에서 판별.
    return (
        <div>
            <h2>If1</h2>
            {btnLogin(true)}
        </div>
    );
};

export default If1;
```

![expr](/assets/Images/react/chapter4/4_lf1.JPG)

<br>

참조 : 호쌤의 교육자료, (<https://blog.itpaper.co.kr/>)