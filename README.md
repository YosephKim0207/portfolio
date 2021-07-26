# konlpy 사용 후기

방학 중 진행된 운영체제 연구실 내 인공지능 스터디 참가 후 인공지능에 대한 관심을 갖게 되었다.
1학기에 인공지능 수업을 들으며 해당 분야에 대한 관심은 더욱 깊어졌다. 과제로 YOLOv3를 이용한 객체 탐지 성능 테스트, GAN을 이용한 진짜 옷 찾기 프로그램을 만들어 봤지만 자연어 처리 분야는 예제만 조금 만져본 수준이라 아쉬움이 남았다. 인공지능 학부 수업을 들으며 특히 관심을 갖게 된 분야가 자연어처리 및 추천 시스템 분야였던지라 방학 중 혼자 공부해볼 계획을 갖고 있던 와중에 '오픈소스 컨트리뷰션 아카데미'를 알게 되었고, 'NLP with U' 프로젝트를 알게 되었다.

NLP와 추천시스템을 위해 뭐부터 공부해야하나 막연하던 찰나 'NLP with U'에서 소개해준 'konlpy'를 설치해 해당 툴을 다뤄보기로 하였다. 프로젝트 소개 페이지에서 제공한 konlpy의 github 링크를 들어가면서 학부의 오픈소스 소프트웨어 수업을 들으면서 github를 이용했던 좋지 않은 경험이 떠올라 살짝 긴장하기도 하였다. 당시 과제를 진행하며 소규모 프로젝트에서 배포하는 장고 어플리케이션들을 이용했는데 장고 버전업에 따른 변경된 함수가 적용되지 않는 등 도큐먼트의 업데이트가 미흡하여 단순히 어플리케이션을 사용하는데에도 한참 시간을 들여야 했기 때문이다. 다행히 konlpy는 초심자도 접근하기 쉽도록 nlp에 대한 간단한 안내부터 시작하여 설치 과정 및 이용 방법을 친절하게 정리해두었다.

설치를 마치고 이 도구를 어떻게 활용해야할지 막막한 마음이 들었다. 다행히 konlpy의 도큐먼트에는 활용 방안에 대한 예시들도 안내되어 있었다. 예시들 중 워드클라우드 코드를 직접 실행해보기로 하였으나 문제가 발생하였다. 오류 내용을 읽어보니 서버와의 통신 쪽에서 문제가 발생한 것 같아 웹브라우저를 통해 예시 코드에서 제공하는 url에 직접 접근해보기로 하였다. 
확인 결과 아쉽게도 예시에서 활용하는 국회 의안 내용을 제공하는 포커- 'http://pokr.kr' - 는 현재 서비스를 제공하지 않는 것 같았다.

![](https://user-images.githubusercontent.com/46564046/126978735-5ad682ba-29bc-482b-b485-badec6c5423b.png)


빠른 기능 확인을 위해 인터넷 신문기사를 txt파일로 만들어 konlpy를 이용한 wordcloud를 테스트해보았다.
<details>
<summary>접기/펼치기 버튼</summary>
<div markdown="1">

'''
#! /usr/bin/python2.7
# -*- coding: utf-8 -*-

from collections import Counter
import urllib
import random
import webbrowser

from konlpy.tag import Hannanum
from lxml import html
import pytagcloud # requires Korean font support
import sys

if sys.version_info[0] >= 3:
    urlopen = urllib.request.urlopen
else:
    urlopen = urllib.urlopen


r = lambda: random.randint(0,255)
color = lambda: (r(), r(), r())

'''
def get_bill_text(billnum):
    #url = 'http://pokr.kr/bill/%s/text' % billnum
    url = 'http://www.aitimes.com/news/articleView.html?idxno=%s' % billnum
    response = urlopen(url).read().decode('utf-8')
    page = html.fromstring(response)
    #/html/body/div[1]/div/section/div[2]/div/section/article/div[2]/div/article[1]
   # //*[@id="article-view-content-div"]
    text = page.xpath("//*[@id=\"article-view-content-div\"]")[0]
    return text
'''

def get_tags(text, ntags=50, multiplier=10):
    h = Hannanum()
    nouns = h.nouns(text)
    count = Counter(nouns)
    return [{ 'color': color(), 'tag': n, 'size': c*multiplier }for n, c in count.most_common(ntags)]

def draw_cloud(tags, filename, fontname='Noto Sans CJK', size=(800, 600)):
    pytagcloud.create_tag_image(tags, filename, fontname=fontname, size=size)
    webbrowser.open(filename)


#bill_num = '139784'
text = open('/Users/yosephkim/OneDrive - 전북대학교/4학년 1학기/인공지능/대학원/개인연구/news.txt', encoding='utf-8')
file = text.read()
print(file)
tags = get_tags(file)
print(tags)
draw_cloud(tags, 'wordcloud.png')
'''

</div>
</details>

![](https://user-images.githubusercontent.com/46564046/126978534-5aac3ba9-efc3-4445-b951-fa8891384b63.png)
