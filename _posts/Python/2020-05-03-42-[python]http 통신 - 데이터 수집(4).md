---
title:  "[파이썬] HTTP 통신 - 데이터 수집(4)"
date: 2020-05-03
categories: [python]
---

## 1. URL을 통한 데이터 수집하기

### 1) requests 모듈

웹상의 URL을 파라미터로 받아 그 페이지의 내용을 가져오는 모듈

```
pip install requests
```

### 2) URL을 통한 requests 객체 생성

```
import requests
r = requests.get("http://...")
```

### 3) requests 객체 사용

|코드|내용|
|:--:|:--:|
|r.status_code| 결과 코드를 갖고 있는 변수|
|r.reason|에러가 발생한 경우 에러 메시지를 갖는 변수 값|
|r.encoding|이 속성에 "utf-8"이나 "enc-kr"등을 할당하여 text 속성값의 인코딩을 설정한다.|
|r.text|requests 모듈이 URL에 접속하여 가져온 내용 전문|

### 간단한 HTTP 접속 예제

```python
import requests

# 온라인 상의 text 파일URL
simple_text_url = "http://itpaper.co.kr/demo/python/simple_text.txt"

#특정 웹 페에지에 접속
r = requests.get(simple_text_url)

# 접속에 실패한 경우
if r.status_code !=200:
    # 에러코드와 에러메시지 출력
    print("[%d Error] %s" %(r.status_code, r.reason))
    # 프로그램 강제 종료
    quit()

# 인코딩 형식 지정
r.encoding="utf-8"

# 텍스트 출력
print(r.text)
```

```
Hello Python~!!!
안녕하세요. 파이썬~!!!
```

<br>

## 2. 수집된 데이터 형식

URL을 통해 가져올 수 있는 데이터 형식의 종류

|데이터 종류| 내용| 예|
|:--:|:--|:--|
|text|단순한 텍스트 형식, 텍스트파일을 URL을 통해 가져오는 것이기 때문에 처리 결과는 단순한 문자열 값이다.| Hello Python|
|html| 웹페이지의 화면을 구성하는 프로그래밍 언어, 웹페이지 크롤링은 html을 가져오는 것을 의미한다. 가져온 결과 안에서 의미있는 값들을 추출하는 별도의 처리가 필요하다.|```<html><head></head><body></body></html>```|
|xml|다른 종류의 시스템간에 데이터를 쉽게 주고 받을 수 있게 하기 위한 언어, 지금은 json에 그 역할을 내주고 잘 사용되지 않는다.| ``` <data><item></item></data>```|
|json|파이썬의 딕셔너리와 동일한 구조를 갖는 데이터 표현 방식, 현재 다른 종류의 시스템간 데이터 교환에 가장 널리 사용되고 있다. 파이썬의 딕셔너리와 호환된다.|``` {"data":{"item":"Hello Python"}} ```|

<br>

## 3. JSON 데이터의 이해

### 1) JSON 표기법

JSON(Javascript Object Notation)은 경량의 데이터 교환형식으로, 원래는 javascript에서 객체지향을 구현하기 위해 사용된 문법적 표현이다.

### 2) JSON 표기법의 중요성

- JSON은 특정 프로그래밍 언어에 종속되지 않고 언어로부터 완벽하게 독립적으로 존재할 수 있으며, 여러 개의 데이터를 구조적으로 표현할 수 있는 가장 간결한 표현방법이다.

- 최근에는 웹, 모바일 등을 중심으로 서로 다른 플랫폼 간의 데이터 교환을 위하여 활용된다.

- Java 언어에서는 프로그램 외부에 저장된 파일의 내용을 JSON 형식으로 구성하거나 통신을 통하여 수신하는 데이터를 JSON으로 처리하여 외부로 부터 데이터 읽기에 활용하고 있다.

### 3) JSON 형식의 데이터 만들기

1. 기본 형식

- 빈 객체("{}") 안에 배열과 같이 콤마로 구별하여 여러개의 값을 하나의 객체안에 포함시킨다. 이때, "이름": "값" 형태로 할당한다.

```
{"이름": "값", "이름": "값", ..., "이름": "값"}
```

2. 배열을 포함하기

- 일반 값 형식 대신 배열을 포함할 수 있다.
- 배열을 구성할 때는 "[]"를 사용한다.

```
{"이름" : ["값0", "값1", "값2"]}
```

3. JSON을 포함하는 JSON

- JSON 데이터의 각 항목에는 어떠한 형식의 데이터든지 할당할 수 있다.
- 따라서, 새로운 JSON 데이터를 할당하여 각가의 JSON 데이터들이 하나의 그룹 안에서 계층을 형성할 수 있다.

```
{
    이름: { 이름: 값, 이름: 값},
    이름: { 이름: 값, 이름: 값}
};
```

4. 배열의 원소로 다른 JSON 데이터 포함하기

- 계층형 JSON 구조에서 각각의 데이터가 독립적이라는 점을 배열로 보환하여 하나의 키 이름 안에서 다수의 데이터를 JSON으로 표현할 수 있다.

```
{"java programming": ["java", "jsp", "android"]}

// JSON  안에서 하나의 이름에 대한 배열을 구성하고,
// 각 배열의 요소를 새로운 JSON으로 표현한 형태

{"javaprogramming": [
    {"name":"java", "desc": "프로그래밍 기본"},
    {"name":"JSP", "desc": "웹 프로그래밍"},
    {"name":"Android", "desc": "모바일 개발"}
]}
```

<br>

## 4. 구글 크롬 브라우저에 JSONView 플러그인 설치

1. 크롬브라우저에서 "웹스토어"를 실행

2. JSONview를 검색하고 crome에 추가를 눌러 실행

<br>

## 5. 간단한 JSON 데이터 가져오기

- 온라인 상의 JSON 데이터 가져오기

```python
#필요한 모듈 참조
import requests
import json
from print_df import print_df

# 간단한 JSON Object URL
simple_json_url = "http://www.itpaper.co.kr/demo/python/phone.json"

# 웹페이지에 접속
r = requests.get(simple_json_url)

# 접속에 실패한 경우
if r.status_code !=200:
    #에러코드와 에러메시지 출력
    print("[%d Error] %s" % (r.status_code, r.reason))
    #프로그램 강제 종료
    quit()

# 인코딩 설정 및 결과값 출력
r.encoding = "utf-8"
print_df(r.text)
```

```
<class 'str'>
{
    "rt": "OK",
    "rtmsg": "SUCCESS",
    "item": {
        "name": "갤럭시 S6",
        "type": "삼성",
        "img": "http://itpaper.co.kr/demo/app/img/GalaxyS6.png",
        "price": {
            "fixed": 1000000,
            "sale": 850000
        }
    }
}
```

<br>

## 6. 배열 형식의 JSON 데이터 가져오기

- JSON 형식의 문자열을 딕셔너리로 변환
    - 파이썬 내장 모듈인 json 모듈을 사용하면 json 형식의 문자열을 딕셔너리로 변환할 수 있다. -> 계층화된 딕셔너리로 표현된다.

    - 변환된 딕셔너리는 key를 통해 value에 접근할 수 있다.

```python
# 가져온 결과를 딕셔너리로 변환
result = json.loads(r.text)
print_df(result)

print("결과코드: %s" % result['rt'])
print("결과메시지: %s" % result['rtmsg'])
print("제품명: %s" % result['item']['name'])
print("제조사: %s" % result['item']['type'])
print("사진: %s" % result['item']['img'])
print("정가: %s" % result['item']['price']['fixed'])
print("판매가: %s" % result['item']['price']['sale'])
```

```
<class 'dict'>
    {'rt': 'OK', 'rtmsg': 'SUCCESS', 'item': {'name': '갤럭시 S6', 'type': '삼성', 'img': 'http://itpaper.co.kr/demo/app/img/GalaxyS6.png', 'price': {'fixed': 1000000, 'sale': 850000}}}
    결과코드: OK
    결과메시지: SUCCESS
    제품명: 갤럭시 S6
    제조사: 삼성
    사진: http://itpaper.co.kr/demo/app/img/GalaxyS6.png
    정가: 1000000 
```


참조 : 호쌤의 교육자료, (<https://blog.itpaper.co.kr/>)