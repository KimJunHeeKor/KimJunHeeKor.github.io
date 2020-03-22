# CSV 파일 입출력

## 1. CSV 파일
엑셀에서 사용하는 표 형식을 텍스트 형태로 변환한 파일

- 데이터 구조를 표현하는 가장 간결한 형태의 파일로서 엑셀의 행은 한 줄로 표현하고 엑셀의 열은 콤마(`,`)로 구분하는 형식이다.

<br><br>

## 2. CSV 파일 저장하기
Dictionary를 요소로 갖는 리스트를 csv로 저장하기

``` python

grade = [
    {"name":"철수", "kor" : 95, "eng": 88, "math": 72},
    {"name":"영희", "kor" : 92, "eng": 90, "math": 95},
    {"name":"철민", "kor" : 88, "eng": 76, "math": 64}
]

tpl = "{0}, {1}, {2}, {3} \n"

with open("grade.scv","w", encoding='euc-kr') as f:
    f.write("이름, 국어, 영어, 수학\n")

    #각 데이터를 한 줄씩 콤마로 구분하여 기록
    for item in grade:
        tmp = tpl.format(item["name"], item["kor"], item["eng"], item["math"])
        f.write(tmp)
```

```
이름,국어,영어,수학
철수,95,88,72
영희,92,90,95
철민,88,76,64
```

<br><br>

## 3. CSV 파일 데이터 처리

csv파일 읽기
```python
with open("grade.csv", "r", encoding='euc-kr') as f:
    #파일의 각 행을 요소로 갖는 리스트를 생성
    csv_list = f.readlines()
    print(csv_list)
    print('-'*30)

    for i, line in enumerate(csv_list):
        if i>0:
            #현재 행의 내용을 콤마를 기준으로 자르고 리스트로 변환
            item = line.strip().split(",")
            print(item)

            #이름과 점수로 분리-> 점수는 정수형으로 변환
            name = item[0]
            kor = int(item[1])
            eng = int(item[2])
            math = int(item[3])
            total = kor + eng + math    # 총점
            avg = total /3              # 평균

            #결과 출력
            tpl = "{0}의 총점은 {1}점이고 평균은 {2:0.2f}점 입니다."
            print(tpl.format(name, total, avg))
```
```
['이름,국어,영어,수학\n', '철수,95,88,72\n', '영희,92,90,95\n', '철민,88,76,64\n']
------------------------------
['철수', '95', '88', '72']
철수의 총점은 255점이고 평균은 85.00점 입니다.
['영희', '92', '90', '95']
영희의 총점은 277점이고 평균은 92.33점 입니다.
['철민', '88', '76', '64']
철민의 총점은 228점이고 평균은 76.00점 입니다.
```

참조: (https://blog.itpaper.co.kr/)의 교육자료