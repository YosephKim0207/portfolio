# konlpy 사용 후기

방학 중 진행된 운영체제 연구실 내 인공지능 스터디 참가 후 인공지능에 대한 관심을 갖게 되었다.
1학기에 인공지능 수업을 들으며 해당 분야에 대한 관심은 더욱 깊어졌다. 과제로 YOLOv3를 이용한 객체 탐지 성능 테스트, GAN을 이용한 진짜 옷 찾기 프로그램을 만들어 봤지만 자연어 처리 분야는 예제만 조금 만져본 수준이라 아쉬움이 남았다. 인공지능 학부 수업을 들으며 특히 관심을 갖게 된 분야가 자연어처리 및 추천 시스템 분야였던지라 방학 중 혼자 공부해볼 계획을 갖고 있던 와중에 '오픈소스 컨트리뷰션 아카데미'를 알게 되었고, 'NLP with U' 프로젝트를 알게 되었다.

NLP와 추천시스템을 위해 뭐부터 공부해야하나 막연하던 찰나 'NLP with U'에서 소개해준 'konlpy'를 설치해 해당 툴을 다뤄보기로 하였다. 프로젝트 소개 페이지에서 제공한 konlpy의 github 링크를 들어가면서 학부의 오픈소스 소프트웨어 수업을 들으면서 github를 이용했던 좋지 않은 경험이 떠올라 살짝 긴장하기도 하였다. 당시 과제를 진행하며 소규모 프로젝트에서 배포하는 장고 어플리케이션들을 이용했는데 장고 버전업에 따른 변경된 함수가 적용되지 않는 등 도큐먼트의 업데이트가 미흡하여 단순히 어플리케이션을 사용하는데에도 한참 시간을 들여야 했기 때문이다. 다행히 konlpy는 초심자도 접근하기 쉽도록 nlp에 대한 간단한 안내부터 시작하여 설치 과정 및 이용 방법을 친절하게 정리해두었다.

설치를 마치고 이 도구를 어떻게 활용해야할지 막막한 마음이 들었다. 다행히 konlpy의 도큐먼트에는 활용 방안에 대한 예시들도 안내되어 있었다. 예시들 중 워드클라우드 코드를 직접 실행해보기로 하였으나 문제가 발생하였다. 오류 내용을 읽어보니 서버와의 통신 쪽에서 문제가 발생한 것 같아 웹브라우저를 통해 예시 코드에서 제공하는 url에 직접 접근해보기로 하였다. 
확인 결과 아쉽게도 예시에서 활용하는 국회 의안 내용을 제공하는 포커- 'http://pokr.kr' - 는 현재 서비스를 제공하지 않는 것 같았다.

![](https://user-images.githubusercontent.com/46564046/126978735-5ad682ba-29bc-482b-b485-badec6c5423b.png)

<현재는 폐쇄된 해당 사이트>


빠른 기능 확인을 위해 인터넷 신문기사를 txt파일로 만들어 konlpy를 이용한 wordcloud를 테스트해보았다.
([해당코드](https://github.com/YosephKim0207/portfolio/blob/main/WordCloud_code))


![](https://user-images.githubusercontent.com/46564046/126978534-5aac3ba9-efc3-4445-b951-fa8891384b63.png)

![](https://user-images.githubusercontent.com/46564046/126980598-0fdbfec3-74ac-454f-beea-2939a0ebba6d.png![image](https://user-images.githubusercontent.com/46564046/126980620-53296b84-e01a-49fb-b540-852aee3d9cee.png)
)
<연어(collocation)찾기 예시 실행>

비록 konlpy 도큐먼트에서 제공하는 예시들만을 수행해보았지만 입문자로서 자연어 처리에 대한 키우고 도구가 활용될 수 있는 가능성을 알 수 있는 유의미한 경험이었다.
