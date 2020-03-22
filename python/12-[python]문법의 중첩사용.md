# 문법의 중첩사용

## 1. 변수의 범위
- 어떤 변수에 최초로 값을 할당하는 것을 **변수 선언**이라고 한다.

- 상위코드에서 선언한 변수는 하위코드에서 실행이 가능하다.

(python에서 Scope(블록, 실행되는 범위)는 들여쓰기를 말하며 다른 프로그래밍언어에서는 중괄호(`{}`)로 표현한다.)

- 유효한 범위의 예
```python
num = 100
if num ==100:
    print("%d" %num)
```

```python
num = 100
for i in range(0,10):
    print("%d" % (num+i))
```

<br><br>

## 2. 조건문에서 변수의 범위
- 변수가 선언된 Scope 밖에서는 Scope의 실행 여부에 따라 식별 여부가 결정된다.
```python
num =100
if num ==100:
    result = num+100

#if문이 실행되었으므로 변수 result를 식별 할 수 있음.
print("%d" %result)
```

```python
num = 100

if num > 100:
    result = num+100

#if문이 실행되지 않았으므로 변수 result를 식별할 수 없음 >> 에러
print("%d" % result)
```

<br><br>

## 3. 반복문에서 변수의 범위
- 상위 Scope에서 선언된 변수는 하위 Scope안에서 사용가능
- 변수가 선언된 Scopce 밖에서는 Scope의 실행 여부에 따라 식별 여부가 결정된다.
- for문에서 초기식의 역할로 정의한 변수 역시 반복문 수행여부에 따라 식별 여부가 결정된다.

```python
for i in range(0, 10):
    a = i+1

#반복문이 1회 이상 수행되었으므로 a와 i 식별 가능
print("%d, %d" % (i,a))
```

```python
k = 100
while k>100:
    a = k+1

#반복문이 수행되지 않았으므로 a는 식별 불가>> 에러
print("%d" %a)
```

<br><br>

## 4. 문법의 중첩
if, while, for문을 서로 중첩해서 사용할 수 있다.

### 1) if문의 중첩 사용
특정 조건을 좀 더 상세하게 판단하기 위해서 사용한다.
```python
point = 78

if point >70:
    print("패스입니다.")

    if point>90:
        print("A입니다.")
    elif point>80:
        print("B입니다.")
    else:
        print("C입니다.")
else:
    print("패스하지 못했습니다.")
```
```
패스입니다.
C입니다.
```

<br>

### 2) 반복문과 if문의 중첩
주로 반복문에서 설정되는 조건값을 검사한다.

```python
x = 0
y = 0

for i in range(1, 11):
    if i%2 ==0:
        print("%d(은)는 짝수" %i)
        x +=i
    else:
        print("%d(은)는 홀수"%i)
        y +=i
print("1~10까지 짝수들의 합: %d" %x)
print("1~10까지 홀수들의 합: %d" %y)
```
```
1(은)는 홀수
2(은)는 짝수
3(은)는 홀수
4(은)는 짝수
5(은)는 홀수
6(은)는 짝수
7(은)는 홀수
8(은)는 짝수
9(은)는 홀수
10(은)는 짝수
1~10 까지 짝수들의 합: 30
1~10 까지 홀수들의 합: 25
```

<br>

### 3) 반복문의 중첩
바깥의 반복은 행을 처리하고 안쪽은 반복은 열을 처리한다.

```python
# 구구단
tpl = "{0} x {1} = {2}"

for i in range(2, 10):
    for j in range(1, 10):
        k=i*j
        print(tpl.format(i,j,k))
```
```
2 x 1 = 2
2 x 2 = 4
2 x 3 = 6
2 x 4 = 8
2 x 5 = 10
2 x 6 = 12
2 x 7 = 14
2 x 8 = 16
2 x 9 = 18
3 x 1 = 3
... 생략...
9 x 4 = 36
9 x 5 = 45
9 x 6 = 54
9 x 7 = 63
9 x 8 = 72
9 x 9 = 81
```

<br>

### 4) 무한루프
- 반복 조건이 잘못 설정되어 실행코드가 중단되지 않고 계속 수행되는 반복문
- 무한루프는 피해야 하는 현상이다.

#### 반복문의 흐름제어
- 반복의 수행범위를 명확하게 판단할 수 없을 경우, 부득이하게 무한반복을 설정하고 특정 조건이 발생하면 반복의 상태를 제어할 수 있다.

- `break` : 반복문 안에서 break 키워드를 만나면 반복을 강제 종료한다.
- `continue` : 실행흐름이 조건식으로 강제 이동된다.

#### 예시 코드
1. 무한루프
```python
x = 1

#실행시 종료되지 않으므로 주석으로 막음.
#while x <10:
#    print(x)
#    x -=1
```

2. 반복문의 흐름제어
```python
y = 0
while True:
    y +=1
    
    if y %2 == 0:
        continue
    if y >100:
        break
    print("Hello (%d)" %y)
```
```
Hello (1)
Hello (3)
Hello (5)
Hello (7)
Hello (9)
..생략..
Hello (93)
Hello (95)
Hello (97)
Hello (99)
```

<br><br>

## 5. 반복문 예제

### 1) 별찍기
총 5행이며 각 행마다 별이 1씩 증가
(1행: 별 한개, 2행 : 별 두개, .., 5행: 별 5개)

```python
for i in range(0,5):
    star=""
    for j in range(0, i+1):
        star +="*"
    print(star)
```
```
*
**
***
****
*****
```

<br>

### 2) 리스트의 요소를 역순 배치
```python

mylist =[5,3,7,1,9]

size = len(mylist)  #리스트 길이

# index 정 중앙에 위치한 2번 요소를 기준으로 index가 i와 index가 리스트의 길이-i인 요소를 서로 교환하면 된다. 
half = size//2

for i in range(0, half):
    p = size -i -1

    mylist[i], mylist[p] = mylist[p], mylist[i]

print(mylist)
```
```
[9, 1, 7, 3, 5]
```

<br>

### 3) 리스트 정렬
index가 i인 요소와 i+1부터 리스트의 마지막까지의 요소를 반복문을 통해 하나씩 비교하여 요소 중 가장 작은 값을 index i에 넣는다. 그 후 index i를 하나 증가하여(i+1) 위의 과정을 반복 수행한다. 이 과정은 i가 리스트의 마지막 요소 전이 될때까지 진행된다.

참고: 인터넷 포털에서 `버블정렬`을 검색하면 더 많은 정보를 얻을 수 있다.

```python
mylist =[5,3,7,1,9]
print(mylist)

size = len(mylist)  #리스트 길이

for i in range(0, size-1):
    for j in range(i+1, size):
        if mylist[i]>mylist[j]:
            mylist[i], mylist[j] = mylist[j], mylist[i]
print(mylist)
```
```
[5, 3, 7, 1, 9]
[1, 3, 5, 7, 9]
```

참조: (https://blog.itpaper.co.kr/)의 교육자료