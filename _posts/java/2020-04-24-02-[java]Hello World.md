---
title: "[java] HelloWorld"
date: 2020-04-24
categories: java
---

개발환경이 설치된 후 확인을 위한 목적으로 간단한 메시지를 출력하는 프로그램

개발환경 구축 여부 테스트와 기본적인 코드작성 구조를 확인할 수 있다.


## 1. 코드 작성하기

작업폴더 안에 **HelloWorld.java** 파일을 서브프라임을 통해서 생성한다.

### 1) HelloWorld.java

```java
public class HelloWorld{
	public static void main(String[] args){
		System.out.println("HelloWorld");
		System.out.println("안녕하세요. 자바!!");
	}
}
```


## 2. 컴파일

1. 소스파일이 있는 폴더의 빈 곳에서 `Shift + 마우스 우클릭`
2. **여기에 PowerShell창 열기** 선택
3. `javac 파일이름`형식으로 컴파일 명령어를 수행
	- `javac HelloWorld.java`
	- 정상적인 경우 아무런 출력이 없다.
	- 코드에 문제가 있는 경우, 해당파일의 이름과 위치(라인수)가 에러 메시지와 함께 출력된다.


## 3. 실행

`java 확장자를 뺀_파일이름` 형식으로 실행한다.

```Shell
$ java HelloWorld
```


## 4. 주석문

프로그램 소스코드 안에 개발자가 작성하는 설명문

프로그램 컴파일에서 제외된다.

### 1) 한 줄 짜리 주석문

문장 앞에 `//`를 적용한다.

#### ex)

```java
// 이 부분은 주석입니다.
// 여러 줄을 작성하기 위해서는 모든 라인 앞에 "//"를 추가해야 합니다.
```

```java
public class HelloWorld{
	public static void main(String[] args){
		// 괄호 안의 내용을 출력하는 명령어
		System.out.println("HelloWorld");
		System.out.println("안녕하세요. 자바!!");
	}
}
```

>주석 설정, 해제를 위한 Sublime 단축키 : `Ctrl + /`

### 2) 두 줄 이상에 대한 주석문

`/*  */` 형태로 블록을 구성한다.

이 영역안에서는 줄바꿈이 자유롭다.

#### ex)

```java
/*
	이 안에서는 자유롭게 여러 줄을 작성할 수 있습니다.

	상당히 긴 내용을 정리할 때 사용한다.
*/
```

```java
public class HelloWorld{
	public static void main(String[] args){
		/* 괄호 안의 내용을 출력하는 명령어,
		java에서 한글은 mapping되어 있지 않은 character이므로
		유니코드를 utf-8로 설정하여 한글을 인식할 수 있게 한다.*/
		System.out.println("HelloWorld");
		System.out.println("안녕하세요. 자바!!");

	}
}
```

>주석 설정, 해제를 위한 Sublime 단축키 : `Ctrl + Shift + /`

### 3) 주석의 활용

#### [1] 특정 블록의 컴파일을 방지

아래 코드에서 **"안녕하세요. 자바!!"**라는 문장은 컴파일 되지 않는다.

```java
public class HelloWorld{
	public static void main(String[] args){
		System.out.println("HelloWorld");
		// System.out.println("안녕하세요. 자바!!");
	}
}
```

#### [2] 프로그램 설명문

프로그램 소스코드의 최상단에서 해당 소스파일의 작성자와 주요 기능을 설명하는 내용을 명시하는 형식.

특별히 정해진 형식은 없다.

개발자 개인마다 혹은 회사마다 형식을 정해놓고 사용한다.

> 미리 정의된 소스코드 작성 규칙을 **코딩 컨벤션**이라고 한다.

```java
/**
 * @filename	: HelloWorld.java
 * @descrption	: 자바 소스코드의 기본 구조를 파악하기 위한 에제
 * @author		: 김준희 (kimjunheekor@gmail.com)
 */
public class HelloWorld{
	public static void main(String[] args){
		System.out.println("HelloWorld");
		System.out.println("안녕하세요. 자바!!");
	}
}
```

> 위의 설명문 형식은 향후 모든 포트폴리오형 평가 답안 제출시 적용되어야 합니다. 그렇지 않을 경우, 1 ~ 3점 감점


## 5. HelloWorld 코드분석

### 1) 기본 규칙

프로그램 소스코드는 줄바꿈이나 들여쓰기를 특별히 강조하지 않는다. 모든 줄바꿈과 들여쓰기를 개발자가 보기에 좋은 형식으로 정리하기 위한 용도이다.

대소문자를 엄격하게 구분한다.

프로그램 구문은 블록간의 중첩으로 구성된다. 블록은 **중괄호(`{}`)**로 표현한다.

서로 중첩된 블록간에는 들여쓰기로 블록의 깊이(depth)를 표현하기도 한다.

### 2) 예약어

프로그램 코드에서 특별한 기능을 갖는 키워드

여기서 각 예약어들의 기능을 설명하기는 이르기 때문에 정해진 코드 양식정도로 여기고 외워두도록 하자.

| 이 예제에서의 예약어들 |
|----|
|public, class, static, void, String[], main|

### 3) 명령어

특정 기능을 수행하기 위한 문장

하나의 명령어는 만드시 **세미콜론(`;`)**으로 종료되어야 한다.

원래의 이름은 클래스, 객체, 메서드 등으로 불리지만 아직은 진도가 이르기 때문에 다음의 구문을 통째로 **출력을 위한 명령어**로 기억하자.

```java
System.out.println(... 출력할 내용...);
```

### 4) 문자열 (String)

쌍따옴표로 감싸진 문장

에제에서는 출력할 내용으로 사용되었다.

### 5) 클래스 (매우중요)

자바 프로그램의 최소단위이자 최상위 블록.

1. 하나의 소스파일은 하나 이상의 클래스로 구성되어야 한다.
2. public이 적용된 클래스는 소스파일 내에서 반드시 단 하나밖에 존재하지 못한다.
3. public이 적용된 클래스는 소스파일의 이름과 반드시 동일해야 한다.

```java
public class 소스파일이름 {
	//... 기능구현 ...
}
```

### 6) 메서드 (매우중요)

클래스 안에서 기능을 구현하기 위한 블록단위

하나의 클래스 안에는 여러 개의 메서드가 존재할 수 있다.

메서드 이름은 개발자가 자유롭게 정의할 수 있다.

> 1. 메서드를 함수라고 부르기도 한다.
> 2. 메서드 이름 앞에 명시되는 예약어들은 상황에 따라 다르지만 당분간은 'public static void'를 규정화 해서 사용하도록 합니다.

```java
public class 소스파일이름 {
	public static void 메서드1(){
		//...기능구현...
	}

	public static void 메서드2(){
		//...기능구현...
	}
}
```


#### [1] main 메서드

프로그램의 시작점이 되는 사전에 미리 약속되어진 메서드

프로그램이 실행될 때 무조건 main 메서드의 블록이 실행된다.

main 메서드는 이름 오른쪽 소괄호에 `String[] args`라는 구문을 명시하도록 약속되어 있다.

main 메서드를 포함하는 클래서를 특별히 main 클래스라고 부르기도 한다.

#### [2] 결론 (자바 소스코드의 최소단위)

```java
public class 클래스이름{
	public static void main(String[] args){
		//... 기능구현 ...
	}
}
```

참조 : 호쌤의 교육자료, (<https://blog.itpaper.co.kr/> )