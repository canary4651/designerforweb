# 디자이너를 위한 웹코딩6

# Front-End Basics

## Part2

### CSS

- Shadows
- [Selectors](https://techhtml.github.io/)
    - 어떤 요소에 css를 적용할 것인가 (js에서도 사용 → querySelector)
    - HTML의 특정 요소를 가져오기 위한 수식
        - 식/문 구분: 항상 값이 나오는 게 식 1+2 , 없어도 되는 게 문 if문
        - element selector 요소 셀렉터
        - element가 여러개가 되면 개별 제어하는 게 불가능

            //HTML
            <div></div> -> 요소 셀렉터(선택자)
            
            //css
            dic {} 

        - class selector
            - 개별 요소 가능
            - 클래스 명을 잘 지어야 함. 이름만 가지고도 어떤 요소가 어떤 이름을 가지고 있겠네, 라고 바로 알게!
            - 자주 쓰이는 클래스명
                - wrapper : 하나의 요소를 감싸는 클래스명

                        <div class="wrapper>
                        	<div></div>
                        </div>

                - container : 여러 요소를 감싸는 클래스명

                        <div class="container">
                        	<div></div>
                        	<div></div>
                        </div>

                - header
                - main
                - content : 그냥 자주 쓰임
                - article
                - section
                - footer
                - aside (옆에 붙어 있는 거)

                TIp: 요소명도 잘 써야 하고, 적절하게 잘 배치해야 함. 네이밍 중요!

            - attribute Selector
                - 특정한 속성을 가지고 있거나, 속성에 특정한 값을 가지고 있거나
                - 많이 쓰진 않음. 존재만 하는 느낌

                    //html
                    <div lang="ko">이 친구를 Select</div>
                    <div lang="ko-KR">이 친구를 select</div>
                    //css
                    [lang="ko"]
                    [lang] // 이 속성을 가지고만 있어도 ok인 경우
                    [lang*="ko"] // ko 속성을 조금이라도 가지고 있으면 다 
                    [class="wrapper"] 

            //HTML
            <div class="a"></div> -> 요소 셀렉터(선택자)
            
            //css
            .a {}

    - Combinator
        - Selctor를 조합
        - Child combinator : 정말 많이 쓰이고 중요함

            <div class="header">
            	<h1 class="title">My Title</h1>
            </div>
            
            css:
            . haeader .title {} 
            /* header라는 클래스의 자손 요소인 .title에게만 Css를 줘(자손과 자식은 다름) */

        - childeren combinator

            <div class="header">
            	<h1 class="title">My Title</h1>
            	<div class="header-description">
            		<p> 어쩌구저쩌구 문단 문단 </P>
            	</div>
            </div>
            
            
            NODE TREE:
            .header
            	.title
            	.header-description
            		p
            css:
            . haeader > title {} 
            /* 자식 요소 : 부모의 바로 밑에 있는 요소!!! 요소의 깊이가 길어질 때, 깔끔하게 처리하기 위해 사용  */

        - sibling combinator
            - Next sibling combinator

            <div class="main">
            	<p> 어쩌구저쩌구 문단 문단 </P>
            	<p> 어쩌구sdfdsf저쩌구 문단 문단sdfsdf </P>
            	<div>hello</div>
            	<p>hello world</p> // 밑에서 지정한 css 적용 안되는데
            	<p>hellow owrld2</p> // 여기서부터는 p + p 니까 적용됨 (next sibling combnator) 얘한테만 적용됨!
            </div>
            
            
            /* 첫번째 요소가 아닌, 2번째 요소부터 css 적용하기 */
            :nth-child(2) -> 그치만 2번쩨만 적용 
            :nth-child(wn) {} / 2,4,6,8,10.... 
            CSS
            .mian p + p {} / p요소 뒤에 바로 붙어있는 p요소 

        - subsequent-sibling-combinator

            .main p ~ p {}
            /* 한번이라도 p 요소가 존재하고, 그 뒤에 모든 p 요소 적용 */

        ![6/Untitled.png](6/Untitled.png)

- pseudeo delemtns

- Responsive web design
    - 어떤 디바이스에서 내 사이트를 접속하더라도 최적의 ux를 제공한다
    1. 콘텐츠 구조
        1. 미리 고민해서 모바일, 데탑 비슷하게 하는 게 좋음 (인터랙션도) 
    2. 브레이크 포인트 (어느 지점까지 대응할 건지) 
        1. 모바일 대응 
        2. 데스크탑 대응
        3. 테블릿은,,,흠,,,🤔
        4. 스크린 사이즈
            - 아이패드 미니 부터 태블릿 이라고 생각하면 됨
            - css

                mobile
                p {margin: 0}
                
                @media (min-width: 768 px){
                	/* tablet start */
                }
                
                @media (min-width: 768 px) and (max-width: 1365 px) {
                	/* tablet start */
                }
                
                @media(min-widht:1360 px) {
                	/* desktop start */
                }
                
                // 순서 중요 

        - 미디어 쿼리(media query)
            - 특정한 미디어에서 특정한 조건이 맞을 때만 css적용

                    @media (min-width: 480px) {
                    /* 브라우저 사이즈가 480px 이상인 경우에만 해당 css 적용 */
                    }
                    
                    // 치명적인 문제 
                    - 내 브라우저 사이즈가 1000px
                    - 적층형 구조라서 조건이 맞으면 다 들어감 (모든 css가) 
                    - 단점이자 장점 
                    - mobile first : 콘텐츠가 적은 화면에서 큰 화면으로 넘어가는 게 배치가 쉬움 
                    - seo 검색엔젠 최적화 : resposive web design으로 구현된 사이트가 상대적으로 먼저 뜸
                    	 ex) 구글에 검색하면 네이버 모바일 블로그(반응형)이 데탑보다 먼저 뜸

    3. 인터랙션
    - - @media
    - Structured web app

### JS

- variable
- functions
- events

## 실습

- 다음 주 과제: 코드를 그대로 따라하기
- 하지 않는 것들을 css로 구현하기 (마크업에 있는 거 html) 저자정보, relative 기사들...
- 다음주는 이걸로 대체!
- 깃헙으로 코드 쉐어