---
title:  "[파이썬] crawler"
date: 2020-05-06
categories: [python]
---

## 1. 클롤링 구현에 활용할 모듈 만들기

모듈이 구현해야 하는 기능들을 포함할 클래스 정의

- 클롤링을 위해 URL로 웹 페이지에 접근하는 처리는 파이썬 기반의 크롤러가 항상 필요로 하는 기능들이므로 클래스 형태로 이 기능을 함축해 모듈화 해 놓으면 필요한 시점에 코드를 재사용할 수 있다.

```python

#--------------
# crawler.py
#-----------------

import os
import requests
from bs4 import BeautifulSoup

#------------
#크롤링 클래스
#------------
class Crawler:
    # 멤버변수(1) - 브라우저 버전 정보 문자열
    user_agent = "Mozilla/5.0 (Macintosh; Intel Mac OS X 10_14_2) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/71.0.3578.98 Safari/537.36"

    # 멤버변수(2) - 접속에 사용될 세션객체 (생성자에서 사용된다.)
    session = None

    #----------
    # 생성자 - 접속을 생성한다.
    #----------
    def __init__(self, header={}, referer=None):
        # 접속에 필요한 정보 구성
        ses_info={'referer':referer, 'User-agent':self.user_agent}

        # 추가적인 header 정보가 전달되면 ses_info에 병합한다.
        if header:
            keys = list(header.keys())
            for k in keys:
                ses_info[k]=header[k]
        
        # 세션객체 생성
        self.seesion = requests.Session()

        # 세션에 접속 정보 설정
        self.session.headers.update(ses_info)

    #----------
    # HTML 페이지에 접속하여 페이지의 모든 소스코드를 가져온다.
    #----------
    def get(self, url, encoding='utf-8'):
        try:
            #생성자에서 만든 세션 객체를 사용하여 URL 접근
            r = self.session.get(url)
        except:
            print("[Network Error] Connection Fail")
            return None
        
        #에러가 발생했다면 None을 리턴하고 처리 중단
        if r.status_code != 200:
            print("[%d Error] %s" % (r.status_code, r.reason))
            return None

        # 인코딩 설정
        r.encoding = encoding

        # 결과 문자열의 앞, 뒤 공백을 제거한 상태로 리턴
        return r.text.strip()

    #----------
    # HTML 페이지에 접속하여 특정 셀렉터에 대하여 파싱한 결과를 list로 반환한다.
    #----------
    def select(self, url, selector='html', encoding='utf-8'):
        #웹 페이지 접속 함수를 호출하여 소스코드 리턴받기
        source = self.get(url, encoding)

        # 리턴 값이 없다면 처리 중단
        if not source:
            return None

        # 웹 페이지의 소스코드 HTML 분석 객체로 생성
        soup = BeautifulSoup(source, 'html.parser')

        # CSS 선택자를 활용하여 가져오기를 원하는 부분 지정
        # -> list로 리턴
        return soup.select(selector)

    #----------
    # 크롤링한 결과 원본(item)에서 tage와 selector가 일치하는 항목을 삭제
    #----------
    def remove(self, item, tag, selector=None):
        for target in item.find_all(tag, selector):
            target.extract()

    #----------
    #특정 URL의 파일을 다운로드 한다.
    #----------
    def download(self, url, filename=""):
        try:
            #접속 객체를 사용하여 파라미터로 전달된 URL 다운로드 받기
            r = self.session.get(url, stream=True)
        except:
            print("[Network Error] Connection Fail")
            return None

        #에러여부 검사 - 에러가 발생했다면 None을 리턴하며 처리 종료
        if r.status_code !=200:
            print("[%d Error] %s" %(r.status_code, r.reason))
            return None

        # 이미지의 byte 데이터를 추출
        img = r.raw.read()

        # 추출한 데이터를 저장
        with open(filename, 'wb') as f:
            f.write(img)
        
        #저장된 파일 이름만 리턴
        return filename
```

<br>

## 2. 완성된 모듈 활용하기

- 코드 구현

```python
# 필요한 모듈 참조하기
from crawler import Crawler

# sample.py에서 필요한 데이터 참조
from sample import naver_news_url   #가져올 뉴스의 URL
from sample import image_url        #다운로드 할 이미지의 URL

#-----------------------------
# 모듈객체 생성하기
#-----------------------------
crawler = Crawler()

#-----------------------------
# 이미지 파일 내려받기
#-----------------------------
savename = crawler.download(image_url, filename="download.jpg")
print(savename + "(이)가 저장되었습니다.")
print("-"*30)


#-----------------------------
# 웹 페이지 크롤링
#-----------------------------
# -> 가져올 페이지의 URL과 추출할 영역의 CSS 셀력터를 지정한다.
# -> encoding이 utf-8인 경우는 파라미터 설정을 생략한다.(기본값 사용)
element = crawler.select(naver_news_url, encoding="euc-kr", selector='#articleBodyContetns')

#크롤링 결과의 원소 수 만큼 반복하면서 불필요한 태그를 제거한다.
for item in element:
    crawler.remove(item, 'script')
    crawler.remove(item, 'a')
    crawler.remove(item, 'br')
    crawler.remove(item, 'span', {'class':'end_photo_org'})

    #크롤링 처리된 최종 결과
    print(item.text.strip())

```

참조 : 호쌤의 교육자료, (<https://blog.itpaper.co.kr/>)