# 조건문

## 1. 조건문 개요

특정 조건을 충족할 경우에만 실행되는 코드

### 조건문의 종류
|종류| 설명|
|:--:|--|
|if문| 주어진 '조건'이 참(True)일 경우에만 실행됨.|
|if ~ else문| 주어진 조건이 참(True)일 경우 if문이 실행되지만 거짓(False)일 경우 else문이 실행됨.|
|if ~elif ~else문| 조건을 여러개로 세분화하여 사용하는 if문|

<br><br>

## 2. if문
if문은 주어진 조건식이 참(True)일 경우에 지정된 코드(구문)이 실행된다.

if와 조건식을 합쳐 `if조건식`으로 조건을 명시하고 참일 경우 실행되는 코드는 콜론(`:`)을 지정하여 하위블록에 명시한다.

단, 하위블록은 if문보다 더 깊게 들여쓰기가 된 상태에서 작성되어야 한다.

```
if 조건식:
    ..실행코드..
    ..실행코드..
```

실행할 구문이 한 줄만 있을 경우 줄바꿈 없이 명시할 수 있다.
```
if 조건식: ... 실행코드...
```

#### 예시 코드
```python
a = 100
if a>=100:
    print("a는 100보다 크거나 같다. 따라서 이 글귀는 출력된다.")
```

<br><br>

## 3. if문에서 사용되는 조건식

if문에서 사용되는 조건식은 값이나 식의 형식에 따라 다양하다.

|형식 | 참| 거짓|
|:--:|:--:|:--:|
|논리값(boolean)| True| False|
|숫자형| 0이 아닌 모든 값| 0|
|비교식| 식 결과가 True| 식 결과가 False|
|논리식| 식 결과가 True| 식 결과가 False|
|문자열| 빈 문자열이 아닌 경우| 빈 문자열인 경우|
|리스트| 요소가 하나라도 존재하는 경우| 요소가 하나도 없는 경우|
|tuple| 요소가 하나라도 존재하는 경우| 요소가 하나도 없는 경우|
|Dictionary| 요소가 하나라도 존재하는 경우| 요소가 하나도 없는 경우|

#### 예시 코드
```python
#조건식이 숫자형 변수인 경우
a = 10
if a:
    print("a")  #a가 출력됨.

#조건식이 문자열인 경우
b = "python"
if b:
    print("b")  #b가 출력됨.

#조건식이 리스트인 경우
c = [1,2,3]
if c:
    print("c")  #c가 출력됨.

#조건식이 비교식인 경우

d = 5
if d >=1:
    print("d")  #d가 출력됨.

if a and d<10:
    print("출력")   #'출력'이 출력됨.
```
<br><br>

## 4. if문 사용시 주의점

if문의 하위코드들의 들여쓰기가 다를 경우 에러가 발생
```python
a = 100
if a >=100:
    print("python")
        print("is easy")    # 들여쓰기가 다르므로 에러가 발생

if b>=200:
    print("python")         # 들여쓰기를 tab으로 설정
    print("is so good")     # 들여쓰기를 space로 설정
    #들여쓰기의 크기는 같으나 공백의 성질이 다르므로 오류
```

<br><br>

## 5. in, not in, is, is not 연산자

if문의 조건식에서 사용할 수 있는 연산자
|연산자| 설명|
|:--:|:--|
|A in B| A는 값, B는 리스트일 때, A가 B에 포함되어 있다면 True|
|A not in B| A는 값, B는 리스트일 때, A가 B에 포함되어 있지 않다면 True|
|A is B| A와 B가 데이터 타입까지 일치할 경우 True|
|A is not B| A와 B가 일치하지 않을 경우 True(값과 데이터 타입이 같을 경우만 False)|

<br>

####예제 코드
```python
a = 1
b = 1
c = 2

if a is b:
    print("a=b")            #a=b 출력
if b is c:
    print("b와 c는 다름")    #출력되지 않음.

# is는 '=='와 다르게 데이터 타입까지 비교함.
x = 1
y = 1
z = 1.0

if x == z:
    print("x와 z는 같다")   # x와 z는 같다.
if y is z:
    print("y와 z는 같다")   # 출력되지 않음.

#is not은 값과 데이터 타입이 같아야 False
d = 123.0
e = 123
f = 234

if d is not e:
    print("d와 e는 다르다") #d와 e는 다르다.
if e is not f:
    print("e와 f는 다르다") #e와 f는 다르다.

# in 연산자
user1 = 'hello'
user2 = 'world'
member_list=['hello','python', 'life']

a1 = user1 in member_list
print(a1)               #True

b1 = user2 in member_list
print(b1)               #False

if user1 in member_list:
    print(user1 + "(은)는 이미 가입되어 있습니다.")     #hello(은)는 이미 가입되어 있습니다.

if user2 in member_list:
    print(user2 + "(은)는 이미 가입되어 있습니다.")     #출력되지 않음.

# not in 연산자
if user1 not in member_list:
    print(user1 + "(은)는 이미 가입되어 있습니다.")     #출력되지 않음.

if user2 not in member_list:
    print(user2 + "(은)는 이미 가입되어 있습니다.")     #world(은)는 가입되어 있지 않습니다.
```
<br>

## 6. if~else문

if문의 조건식이 참일 경우 if문의 하위 코드가 실행되지만 if문의 조건식이 거짓일 경우 else문의 하위 코드가 실행된다.

```python
if 조건식:
    ...if문의 하위코드..
else:
    ...else문의 하위코드..
```

#### 예제 코드
```python
is_korean = False
if is_korean == True:
    print('한국사람입니다.")
else:
    print("한국사람이 아닙니다.")
```

<br>

## 7. if ~elif ~ else문

if문과 else문 사이에 elif문을 정의함으로서 조건을 추가할 수 있다. elif문은 필요한 만큼 나열할 수 있으며 else문을 생략할수 있다.

```python
if 1차 조건식:
    ...if문 하위코드...
elif 2차 조건식:
    ...elif문 하위코드...
elif 3차 조건식:
    ...elif문 하위코드...
elif n차 조건식:
    ...elif문 하위코드...
else:
    ...else문 하위코드...
```

#### 예제 코드
```python
point = 72

if point > 90:
    print("A학점")
elif point > 80:
    print("B학점")
elif point > 70:
    print("C학점")
elif point > 60:
    print("D학점")
else:
    print("F학점")

#C학점
```

참조: (https://blog.itpaper.co.kr/)의 교육자료