# 디자이너를 위한 웹코딩2

- [웹 레이아](https://brunch.co.kr/@techhtml/21?fbclid=IwAR3EAwU21FG3FxM0DGmnHgi8z_pmQK62H7C1QP1OFvIdYW-y6Hig-T6t-5c)웃
- [html실습](https://codepen.io/ChoEun/pen/WNvrBPY?editors=1000&fbclid=IwAR0jyklrpGp6nBRPFCw1TybllnZ7SboHKC_goF_7F0YcCA31c04ZKJl22pU)

< 오늘의 목표> 

- 레이아웃
- 애니메이션
- 타이포그래피

# 1. 타이포그래피

- os에 대한 이해 : 모든 os에는 폰트가 있다. 기본 폰트, 설치한 폰트(커스텀 폰트)
    - 얼마전에 애플이 샌드란시스코라는 새 폰트를 만듬
    - 기본폰트는 os마다 다 다름
        - mac: 애플 sd 고딕 네오
        - window: 맑은 고딕, 돋움, 굴림, 궁서, 바탕
        - 안드로이드 : 노토 산스 / 안드로이드 10부터는 폰트를 못 바꾸게 함.

    - 설치형 폰트의 가장 큰 단점: 유저가 설치하기 전에는 폰트를 보여줄 수 없음
    - 그래서 나온게 `웹폰트`!
        - 폰트를 서버에서 다운받게!
        - 단점: 한국어 폰트의 평균크기 (2550자인가 최적화 했다고 하면) 2.5mb → 11mb (전체를 다하면) → 굵기랑 ^_^ / 영어는 300kb
        - 웹폰트는 ie에서 만든 스펙
- 폰트는 기본적으로 900가지의 폰트가 있음
    - 굵기:
        - 100 ultra light/
        - 200 thin/
        - 300 light
        - 400 regular
        - 500 medium/
        - 600 semi-bold/
        - 700 bold/
        - 800 ?기억안남 잘 안씀 /
        - 900 black, heavy
        - 100-300/ 400-500/ 600-900 그룹임. os별로 조금씩 다름. 숫자를 그대로 쓰는 게 베스트! (글씨만 쓰지 말고)
        - css로 어떻게 지정할까?
            - fontFamily: 폰트이름
            - fontWeight: 폰트 크기
        - css 문법

            // <div> 요소에 스타일을 넣어라 
            div: {
            	fontFamily: 'apple SD gothic Neo' , '맑은 고딕', san-serif,  
            # 다이렉트르 꽂을 때 단점 - 다른 os에서는 보이지 않음 
            # 그래서 ,를 찍고 뒤이어서 폰트를 추가해주면 됌 그리고 **폰트 타입** 적어주기
            # 폰트에는 타입이 존제 : serif/san-serif/
            # mono-space(고정폭), fantasy(코믹북 같은 폰트)
            	fontWeight: '500' ,
            }

        ![2/Untitled.png](2/Untitled.png)

        - san serif를 적지 않아서 (맥을 신경쓰지 않아서) 깨지는 무00 홈페이지 예시
        - os 별 폰트 타입이 있다는 걸 확인하고 쓰기!

### 폰트를 다루는 2가지 타입

1. 폰트 font : 글자의 형태를 의미(크기/굵기/패밀리)
    - fontSize
    - fontFamily (폰트 선언)
    - fontWeight : 100-900 사이/ 보통 타이틀은 700
    - color

2. 텍스트 text : 글자의 상태, 글 전체 제어 ( 행간, 자간, 정렬  )  
    - lineHeight
    - letterSpacing : 1이 기본이고 소수점으로 쪼갤 수 있음, 보통 px로 많이 함
    - textAlign - left / center/ right/ justify(양끝)
    - textShadow
    - wordBreak : 글자를 단어단위로 혹은 글자 단위로 끊을건지 하는 속성 (breaak-all 모두 , keep-all , brack-word 단어 단위) → 전체 한번 쓰고 거의 안 쓰는 속성 중 하나임

    - fontsize와 lineheight는 같이 감 : 만약 16px, 아무리 못해도 19px은 행간을 줘야함 (3-4px 정도는!) → 하나하나 계산하는 거 귀찮음. 폰트사이즈의 1.2배(120% ghrdms tntwk 1.2 쓰면 됨)
    - px과 서브 px이란 개념이 있음.

# *웹 레이아웃*

- 웹은 그래픽을 깊이 있게 다를 순 없다(캔버스가 있긴 하지만)
- position :
    - static(정적) → flow(쌓이는 구조) : 기본값
    - fixed : 뷰포트를 기준으로 특정 위치에 고정 (옮겨지던 말던 항상 고정) : 많이 씀! [li.me](http://li.me) 사이트 보면 헤더 같은 애들
        - 부분적으로 쓸 때도 있음: 스크롤이 있어도 움직이지 않음

        ![2/Untitled%201.png](2/Untitled%201.png)

- absolute/ relative :
    - absolute는 지정을 안하면 기본 flow를 벗어나고 뷰포트를 따라간다. 대신 고정은 안된다 (뷰포트에 따라 움직임). 캔버스의 영역이 무제한이더라도 뷰포트로 고정이 된다.
        - 생활 속의 꿀팁 : 드래그 방지 할 때 (배경색을 안주면 투명이됨) 많이 씀~~~ 인스타에서도 지우면,,,,이미지도 다운로드 할 수 있다~~~ ㅋㅋㅋㅋㅋ
    - Relative: 바디가 캔버스니까 기준이 캔버스로 바뀜. 상대적으로 좌표를 잡고 싶을 때 설정.

    - left/top/right/bottom

### 실습

# 박스모델

- height, width : 보통 width를 많이 지정함. 하이트는 지정을 하든 안하든 컨텐츠 영역만큼 가져가서 딱히 안함. 물론 할 수는 있음.
- padding: 컨텐츠와 박스 사이를 넓히고 싶을 때!
- margin: 마진의 배경색은 투명색! 바스 외부 간격을 정의
- border: 외곽선

    div {
    width: 150px;
    height: 150px;
    border: 10x solid #ddd;
    padding: 15px; /* padding:<top><right><bottom><left>를 축약형*/
    marding:150x; /* margin:<top><right><bottom><left>를 축약형*/
    }

# Flex

- 중요!
- flex 영역(특정한 영역) : 요소들을 배치할 수 있는 공간을 만듬
- 의미 자체가 유동적이라는 의미라서 내부 영역이 자유로움. (늘어거나 줄이거나)
- display: flex
- flex 영역 내에는 배치를 어떻게 할 것인가를 결정하는 2가지 요소가 있음
    1. Main-axis : 메인 축은 플렉스 컨테이너 내 플렉스 아이템을 배치할 때 주된 축 방향 (왼 → 오)  : !!!!!!!!원래는 기본 static은 위에서 아래인데 flex는 반대로 왼→오가 기본 메인축이다!!!!!!!!!!
    2. Cross-axis: 수직 축을 크로스 축이라고 부름(위 → 아래) 
    - 당연히 메인,크로스 값들은 바꿀 수 있음. flex-direction 으로 둘 다 바꿀 수 있음. 값이 row, column 두개가 있음
        - row(기본값): 메인 축을 수평으로하며, 좌측부터 우측으로 쌓임(왼오)
        - column: 메인축을 수직으로(위-아래)

        ![2/Untitled%202.png](2/Untitled%202.png)

        - reverse도 할 수 있음 (굳이 ㅎㅎ... 근데 거의 안씀) 반대로 됌! (우 → 좌) (밑-위)

        ### 플렉스 아이템을 정렬

        - 메인 축을 가지고 정렬 : Justify-content
        - 크로스 축 : align-items
            - 둘 다 속성값은 비슷함 : flex-start, flex-end, centet, ((space-betwwn, space-around): 메인축 한정) // <<stretch, baseline>: 크로스 축 한정>

        ![2/Untitled%203.png](2/Untitled%203.png)

        ![2/Untitled%204.png](2/Untitled%204.png)

        ![2/Untitled%205.png](2/Untitled%205.png)

        - 예시

        ![2/Untitled%206.png](2/Untitled%206.png)

- html 마크업을 할 때, 큰 박스 단위를 잘 짜야함. 개별 아이템을 일일이 옮긴다가 아니라 박스로!

### 박스 사이징 (box-sizing)

- width, height, padding, border를 묶어줌
- margin은 포함 못시킴.
- 자세히 보면 위에 했던 download app이 넘쳤는데, 이거 넣으면 잘 갇혀있게 변함!!

![2/Untitled%207.png](2/Untitled%207.png)

- 인스펙터로 트랜지션 펑션 보기

    ![2/Untitled%208.png](2/Untitled%208.png)

- 오늘 수업 내용만 이해해도 사이트를 만들 수 있음 ㅎㅎㅎ
- 어떻게 이걸 구현할 수 있을까를 끝없이 고민하는 게 개발~~~

- inline-block: 박스를 기준으로 보면 텍스트만 컨텐츠임. 이미지는 굳이 따지면 비쥬얼. 이미지에 alt를 넣지 않으면 컨텐츠로 보기 어려움. 웹에는 텍스트를 처리하기 위한 게 잘 구현되어있는 데 그중 하나가 block과 inline이다.
- block은 전체를 다 싸줌. 줄바꿈은 자동으로 해줌.
- 인라인 : 텍스트 사이사이 강조, 링크, 텍스트에 위치한 요소, 줄바꿈 되지 않게 하려고! strong이나 bold나 ltalic 등 강조하는 친구들은 전부 인라인 버튼도!  그래서 w, h를 지정해도 안들어감. p,m도 블럭이랑 좀 다르게 들어감.
- 오늘 실습 중 사용한건 img와 a 빼곤 인라인
- 근데 인라인 만으론 표현 못하는 게 있음. img! 기존에 들어가는 애들(s,b,등..)은 그냥 인라인 이어도 돼는데, Img는 외부에서 가져오는 데 본문 안에 넣을 수 있음. 그래서 얘를 위해 생긴게 인라인-블럭. w,h,p,m 다 들어감. 글 이야기 하다가 중간에 이미지 하나 나올 때.

- flex의 가장 큰 단점 : IE에서 안됌 ㅎㅎ

[CANIUSE 사이트 : 속성을 어느 버전까지 지원해주는지 알려주는 사이트](https://caniuse.com/) 

# 과제

- li 사이트 헤더 구현
- 무산사 헤더 구현