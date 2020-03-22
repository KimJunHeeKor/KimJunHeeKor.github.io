---
title:  "[파이썬] 파이썬 확장모듈(Numpy)"
date: 2020-03-22
categories: ['python']
tags: ['python', '파이썬']
---
## 1. 파이썬 확장모듈

- 오픈 소스 형태의 파이썬 확장 모듈

    (https://pypi.org/)모듈저장소에는 파이썬의 오픈소스 모듈들이 등록되어 있다. 이를 설치해서 사용할 수 있다.

### 1) 확장 모듈설치

- 확장 모듈 설치를 위한 pip 명령어 사용

    파이썬에는 모듈 저장소로부터 필요한 모듈을 내려 받아 설치를 수행하는 `pip 명령어`가 포함되어 있다.

- `pip 명령어` 업데이트 하기

    명령 프롬프트 상에서 다음의 명령어를 수행하여 pip를 최신버전으로 업데이트 한다. 이 명령은 최초 1회만 수행된다.

    ```cmd
    python.exe -m pip install --upgrade pip
    ```
<br>

- 필요한 모듈 설치하기 (pip대신 pip3 명령어 사용 @ Mac)

    ```
    pip install 모듈이름
    ```
<br>

- 특정 모듈 삭제하기 (pip대신 pip3 명령어 사용 @ Mac)

    ```
    pip uninstall -y 모듈이름
    ```
<br><br>

## 2. Numpy 모듈 소개

1. Numarray와 Numeric이라는 오래된 Python 패키지를 계승해서 나온 **수학 및 과학 연산을 위한 파이썬 패키지**이다.

2. `py`는 파이썬을 의미한다.

3. 프로그래밍 하기 어려운 C, C++, Fortran 등의 언어에 비하면 Numpy로 편리하게 수치해석을 실행할 수 있다.

4. Numpy 내부는 상당부분 C나 Fortran으로 작성되어 있어 실행 속도가 빠른편이다.

5. 기본적으로 array라는 자료를 생성하고 이를 바탕으로 색인, 처리, 연산등을 하는 기능을 수행한다.

6. Numpy 자체만으로도 난수생성, 행렬연산, 간단한 기술통계 분석 정도가 가능하지만 **실제로는 `Pandas`(데이터 분석 모듈), `matplotlib`(그래프 모듈) 등 다른 python 패키지와 함께 쓰이는 경우가 많다.**

7. 파이썬으로 수치해석, 통계 관련 기능을 구현할때 Numpy는 가장 기본이 되는 모듈이다. 그 만큼 Numpy는 수치해석/ 통계 관련 작업시 중요한 역할을 한다.
<br><br>

## 3. Numpy 모듈 설치

- 명령프롬프트에 pip 명령어를 통해 numpy 모듈을 설치한다.

```cmd
pip install numpy
```
<br><br>

## 4.Numpy 모듈 기능

- Numpy 모듈을 이용한 배열 생성

```python
#모듈 가져오기
import numpy

# numpy 배열 생성과 기본 활용
# 리스트를 이용한 1차원 배열 만들기
arr = numpy.array([1,3,5,7,9])
print(arr)
print('-'*30)

# 배열의 크기와 각 원소에 접근하기
size = len(arr)
print('배열의 원소는 %d개 입니다.' %size)
print('-'*30)

#배열의 요소에 접근하기
print(arr[0])
print(arr[1])
print(arr[3])
print('-'*30)

# 반복문과 index를 이용한 요소 접근하기
for i, v in enumerate(arr):
	print("%d번째 원소 >> %d" %(i,v))
```
```
[1 3 5 7 9]
-- -- -- -- -- -- -- -- -- -- -- -- -- -- --
배열의 원소는 5 개 입니다.
    -- -- -- -- -- -- -- -- -- -- -- -- -- -- --
1
3
7
-- -- -- -- -- -- -- -- -- -- -- -- -- -- --
0 번째 원소 >> 1
1 번째 원소 >> 3
2 번째 원소 >> 5
3 번째 원소 >> 7
4 번째 원소 >> 9
```
<br>

- numpy 배열의 특성

```python
#모듈 가져오기
import numpy

#서로 다른 타입의 요소를 갖는 list 만들기
arr2 =[1.2, 3, '4']
print(arr2)
print('-'*30)

#정수와 실수가 섞인 리스트를 배열로 변환
arr3 = numpy.array([1, 2.4, 3, 4.6])
print(arr3)
print('-'*30)

#정수, 실수, 문자열이 포함된 리스트를 배열로 변환
arr4 = numpy.array([1.2, 3, '4'])
print(arr4)
print('-'*30)

#모든 원소의 타입을 강제로 정수(int)로 지정
arr5 = numpy.array([1, 2.4, 3, 4.6], dtype='int')
print(arr5)
```
```
[1.2, 3, '4']
------------------------------
[1.  2.4 3.  4.6]
------------------------------
['1.2' '3' '4']
------------------------------
[1 2 3 4]
```
<br>

- 정형화된 값을 갖는 배열 생성하기

```python
#모듈 가져오기
import numpy

# 0부터 15전까지 순차적으로 증가하는 값들을 요소로 갖는 배열
a = numpy.arange(15)
print(a)
print('-'*30)

# 100 ~ 115전까지 순차적으로 증가하는 값들을 요소로 갖는 배열
b = numpy.array(range(100,115))
print(b)
print('-'*30)

# 모든 요소가 실수형 0인 1행 3열의 배열 생성
c = numpy.zeros([3])
print(c)
print('-'*30)

#모든 요소가 정수형 0인 1행 4열의 배열 생성
d = numpy.zeros([4], dtype='int')
print(d)
print('-'*30)

#모든 요소가 실수형 1인 1행 3열의 배열 생성
e = numpy.ones([3])
print(e)
print('-'*30)

# 모든 요소가 정수형 1인 1행 4열의 배열 생성
f = numpy.ones([4],dtype='int')
print(f)
print('-'*30)

#모든 요소가 정수형 7인 1행 5열의 배열 생성
g = numpy.full([5],7)
print(g)
print('-'*30)

#모든 요소가 실수형 7인 1행 4열의 배열 생성
h = numpy.full([4], 7, dtype='float')
print(h)
```
```
[ 0  1  2  3  4  5  6  7  8  9 10 11 12 13 14]
------------------------------
[100 101 102 103 104 105 106 107 108 109 110 111 112 113 114]
------------------------------
[0. 0. 0.]
------------------------------
[0 0 0 0]
------------------------------
[1. 1. 1.]
------------------------------
[1 1 1 1]
------------------------------
[7 7 7 7 7]
------------------------------
[7. 7. 7. 7.]
```

<br><br>

## 5. Numpy 배열 연산

- numpy 배열의 기초 통계값

```python
#모듈 가져오기
import numpy

# 배열구성
grade = numpy.array([82, 77, 91, 88])
print(grade)
print('-'*30)

#모든 요소의 합
s1 = numpy.sum(grade)
print("총점: %d" %s1)
print('-'*30)

#모든 원소의 평균
s2 = numpy.average(grade)
print("평균: %d" %s2)
print('-'*30)

#최대, 최소값
s3 = numpy.max(grade)
s4 = numpy.min(grade)
print("최대값 : %d, 최소값 : %d" %(s3,s4))
```
```
[82 77 91 88]
------------------------------
총점: 338
------------------------------
평균: 84
------------------------------
최대값 : 91, 최소값 : 77
```
<br>

- numpy 배열의 각 요소의 연산

```python
#모듈 가져오기
import numpy

#모든 요소에 대한 사칙연산 수행
new1 = grade+2
print(new1)
print('-'*30)

# 모든 요소를 5씩 뺌
new2 = grade -5
print(new2)
```
```
[84 79 93 90]
------------------------------
[77 72 86 83]
```
<br>

- numpy 배열간의 연산(1)

```python
#모듈 가져오기
import numpy

#연산자를 사용한 배열간의 연산
arr1 = numpy.array([10, 15, 20, 25, 30])
arr2 = numpy.array([2,3,4,5,6])
print(arr1)
print(arr2)
print('-'*30)

a = arr1 + arr2
print(a)
print('-'*30)

b = arr1 - arr2
print(b)
print('-'*30)

c = arr1 * arr2
print(c)
print('-'*30)

d = arr1 / arr2
print(d)
```
```
[10 15 20 25 30]
[2 3 4 5 6]
------------------------------
[12 18 24 30 36]
------------------------------
[ 8 12 16 20 24]
------------------------------
[ 20  45  80 125 180]
------------------------------
[5. 5. 5. 5. 5.]
```
<br>

- numpy 배열간의 연산(2)

```python
#모듈 가져오기
import numpy

#연산자를 사용한 배열간의 연산
arr1 = numpy.array([10, 15, 20, 25, 30])
arr2 = numpy.array([2,3,4,5,6])

e = numpy.add(arr1, arr2)
print(e)
print('-'*30)

f = numpy.subtract(arr1, arr2)
print(f)
print('-'*30)

g = numpy.multiply(arr1, arr2)
print(g)
print('-'*30)

h = numpy.divide(arr1, arr2)
print(h)
```
```
[12 18 24 30 36]
------------------------------
[ 8 12 16 20 24]
------------------------------
[ 20  45  80 125 180]
------------------------------
[5. 5. 5. 5. 5.]
```

<br><br>

## 6. Numpy 배열의 index와 slicing

- 배열의 기본 index, slicing

```python
#모듈 가져오기
import numpy

# 배열 생성
grade = numpy.array([82, 77, 91, 88])
print(grade)
print('-'*30)

# index
# 2열의 데이터 접근
print(grade[2])
print('-'*30)

# slicing
# 1열부터 3열 전까지 범위를 추출
print(grade[1:3])
print('-'*30)

# 처음부터 2열까지 범위를 추출
print(grade[:2])
print('-'*30)

# 1열~ 끝까지 범위를 추출
print(grade[1:])
```
```
[82 77 91 88]
------------------------------
91
------------------------------
[77 91]
------------------------------
[82 77]
------------------------------
[77 91 88]
```
<br>

- 조건에 맞는 값 추출하기

```python
#모듈 가져오기
import numpy

grade = numpy.array([82, 77, 91, 88])
bool_array=numpy.array([True, False, True, False])

#조건에 맞는 항목만 1차 배열로 추출
result1 = grade[bool_array]
print(result1)
print('-'*30)

#80점 이상인 데이터만 추려냄.
result2 = grade[grade>= 80]
print(result2)
print('-'*30)

#logical_and함수를 사용하여 80점 이상이고 90점 이하인 데이터만 추려냄.
result3 = grade[numpy.logical_and(grade>=80, grade<=90)]
print(result3)
print('-'*30)

#logical_or함수를 사용하여 80점 미만이고 90점 이상인 데이터만 추려냄.
result4 = grade[numpy.logical_or(grade<80, grade >90)]
print(result4)
```
```
[82 91]
------------------------------
[82 91 88]
------------------------------
[82 88]
------------------------------
[77 91]
```

<br><br>

## 7. 2차원 배열

- numpy 2차배열 생성 및 기본 정보 조회

```python
#모듈 가져오기
import numpy

grade = numpy.array([
	[98,72, 80, 64],
	[88, 90, 80, 72],
	[92, 88, 82, 76]

	])
print(grade)
print('-'*30)

#배열 정보
print("차원의 크기 : %d"  %grade.ndim)
print(grade.shape)
print(grade.dtype)
print('-'*30)
```
```
[[98 72 80 64]
 [88 90 80 72]
 [92 88 82 76]]
------------------------------
차원의 크기 : 2
(3, 4)
int32
```
<br>

- 기본 index과 slicing

```python
#모듈 가져오기
import numpy

grade = numpy.array([
	[98,72, 80, 64],
	[88, 90, 80, 72],
	[92, 88, 82, 76]

	])

#정수형 index
print(grade[1,2])
print('-'*30)

#slicing
print(grade[1:3, 1:4])
print('-'*30)

#0~2행 전까지, 0~3열 전까지 범위를 추출
print(grade[:2,:3])
print('-'*30)

# 1~ 끝행, 2~끝열 범위를 추출
print(grade[1:, 2:])
```
```
80
------------------------------
[[90 80 72]
 [88 82 76]]
 ------------------------------
[[98 72 80]
 [88 90 80]]
 ------------------------------
[[80 72]
 [82 76]]
```
<br>

- 기초 통계 산출

```python
#모듈 가져오기
import numpy
grade = numpy.array([
	[98,72, 80, 64],
	[88, 90, 80, 72],
	[92, 88, 82, 76]

	])

#각 열끼리 더함
s1 = numpy.sum(grade, axis =0)
print(type(s1))
print(s1)
print('-'*30)

#각 행끼리 더함
s2 = numpy.sum(grade, axis =1)
print(type(s2))
print(s2)
```
```
<class 'numpy.ndarray'>
[278 250 242 212]
------------------------------
<class 'numpy.ndarray'>
[314 330 338]
```
<br>

- 조건에 맞는 값 추출하기

```python
#모듈 가져오기
import numpy
grade = numpy.array([
	[98,72, 80, 64],
	[88, 90, 80, 72],
	[92, 88, 82, 76]

	])
bool_array = numpy.array([
	[True, False, True, False],
	[True, True, True, False],
	[True, True, True, False]
	])

#조건에 맞는 항목만 1차 배열로 추출
result1 = grade[bool_array]
print(result1)
print('-'*30)

#80점 이상인 데이터만 추려냄.
result2 = grade[grade>=80]
print(result2)
print('-'*30)

#logical_and함수를 사용하여 80점 이상이고 90점 이하인 데이터만 추려냄.
result3 = grade[numpy.logical_and(grade >=80, grade <= 90)]
print(result3)
print('-'*30)

#logical_or함수를 사용하여 80점 미만이고 90점 이상인 데이터만 추려냄.
result4 = grade[numpy.logical_or(grade<80, grade>90)]
print(result4)
```
```
[98 80 88 90 80 92 88 82]
------------------------------
[98 80 88 90 80 92 88 82]
------------------------------
[80 88 90 80 88 82]
------------------------------
[98 72 64 72 92 76]
```

참조 : 호쌤의 교육자료, (<https://blog.itpaper.co.kr/>)