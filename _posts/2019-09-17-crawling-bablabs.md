---
layout: post
published: true
title: Crawling-bablabs
subtitle: 파이썬 BeautifulSoup를 이용하여 크롤링하기
date: '2019-09-17'
---
## 밥대생 크롤링

### 크롤링이란?

- 웹 페이지의 Contents를 수집하고 필요한 데이터를 추출하는 것

### 목표

- 밥대생(대학교 식단 제공 사이트)에서 식단 정보를 수집 후 출력

본 포스트에서는 [공주대학교 천안캠퍼스 학생생활관 식단](https://bds.bablabs.com/restaurants/MTA5NDAwMjU=?campus_id=wqNWwIvBVE)을 기준으로 크롤링을 진행한다.

![image](https://user-images.githubusercontent.com/50393277/65023850-aa66bb00-d96e-11e9-82a8-3721b17cdd7c.png)

위의 웹페이지에서 파란색 박스에 있는 날짜 및 식단 정보를 수집해보자.

### [BeautifulSoup](https://www.google.com/search?q=beautifulsoup&oq=beautifulsoup&aqs=chrome..69i57j69i59j35i39l2j69i60l2.3275j0j7&sourceid=chrome&ie=UTF-8)

- HTML 및 XML 문서를 구문 분석하기 위한 Python 패키지
- 페이지에 대한 트리 작성
- 트리에서 필요한 정보를 추출하여 사용

<br>

## 요소 추출 방법

![image](https://user-images.githubusercontent.com/50393277/65024730-61b00180-d970-11e9-9dc8-319bf60a8f40.png)

추출을 원하는 영역에 마우스 커서를 올리고 오른쪽 버튼 클릭 후 **검사** 클릭

<br>

![image](https://user-images.githubusercontent.com/50393277/65024861-97ed8100-d970-11e9-9880-436ea0e2b7be.png)

**<div data-v-45a7895a="" class="card-title">** 북어해장국 치킨너겟 명엽채볶음 참나물무침 식혜/깍두기</div>

현재 지정한 영역을 살펴보면 **div** 태그로 둘러쌓여있으며 **card-title** 이라는 **class** 에 포함되어 있는 것을 확인할 수 있다.

해당 영역의 정보를 BeautifulSoup를 이용하여 얻어보자.

### 페이지 정보 얻어오기

가장 먼저 페이지에 있는 HTML 요소를 얻어오기 위하여 url에 request를 보내서 정보를 얻어온다.

```python
from bs4 import BeautifulSoup as bs
import requests

#Get elemnets from url
url = "https://bds.bablabs.com/restaurants/MTA5NDAwMjU=?campus_id=wqNWwIvBVE"
page = requests.get(url)
data = page.text
soup = bs(data, 'html.parser')
```

<br>

![image](https://user-images.githubusercontent.com/50393277/65025415-a5573b00-d971-11e9-89af-1f1d443afccb.png)

실행 결과 정보를 url에 대하여 정보를 받아온 것을 확인할 수 있다.

이 데이터 중에서 우리가 필요한 것을 추출해보도록 하자.

### 특정 데이터 추출

위에서 언급하였던 것처럼 우리는 **class** 를 기준으로 요소를 추출할 것이다.

필요한 데이터는 3가지이다.

1. 날짜 (20xx년 x월 x일)
2. 시간 (아침 / 점심 / 저녁)
3. 식단

아래는 각각의 데이터에 대하여 태그를 검사하여 필터링 기준을 결정한 것이다.

날짜 - class="data-title"
시간 - span 태그
식단 - class="card-title"

아래는 위 기준을 이용하여 정보를 추출하는 코드이다.

```python
#Get elements with matching class name
def match_class(target):                                                        
    def do_match(tag):                                                          
        classes = tag.get('class', [])                                          
        return all(c in classes for c in target)                                
    return do_match

#get date and food list
dates = soup.find_all(match_class(["date-title"]))
times = soup.find_all("span")
times = times[3:]
foods = soup.find_all(match_class(["card-title"]))[1:]
```

* 시간 같은 경우 모든 span 태그를 가져오기 때문에 필요없는 부분을 버리는 작업을 거쳤다.

일치하는 class명을 가지는 요소를 찾기 위하여 match_class 함수를 정의하였다.

이후 find_all 함수를 이용하여 해당 클래스를 가지고 있는 모든 요소를 추출하였으며 시간(times)은 span 태그를 가지는 모든 요소를 추출하였다.

<br>

![image](https://user-images.githubusercontent.com/50393277/65026210-0c292400-d973-11e9-8627-d0f804b336d6.png)

실행 결과를 확인하면 정보뿐만이 아니라 여러가지 태그가 섞여있는 것을 확인할 수 있다.

## 정보 가공 및 출력하기


