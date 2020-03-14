# 디자이너를 위한 웹코딩3

# Scroll Animation

- 자바스크립트
- A(state) ↔ B(state)
- web
    - transition
    - animation
- html: 뼈 → ECMA
- css: 외형 → script
- JS: 신경 근육 → 6+ : Reacst, Angular, Vue, svelte, typescript
- Front end : html, css 와 많은 부분은 JS
- 웹 퍼블리셔는 2:8 정도 프론트엔드는 1:9 정도
- html에서 DOM(document/object/model)이 js와 css로 반응을함
- html을 잘 알아야 js에서 작동하기 쉬운 모델을 짤 수 있음 (아니면 헬파티..)
- DOM은 트리구조가 있다
- Root - node a/ node b

![3/Untitled.png](3/Untitled.png)

- 그룹핑을 잘 해야하는 이유
- 상속 : Inheritance : Prototype 상속 - 이미 기존에 있던 형질을 물려받음

![3/Untitled%201.png](3/Untitled%201.png)

- Dom은 브라우저에서 시작
- 브라우저 엘리트 : 브라우저의 최상위 = 윈도우 (브라우저 창)
    - 네비게이터 : 최초로 만든 브라우저 이름에서 유래. 브라우저 정보
    - 도큐먼트 : 문서 정보
    - 스크린 : 화면 정보
    - 이 3개는 윈도우의 자식 노드 (더 많은 데 이정도만 알아둬도 됌)

- 스크롤 애니메이션 좌표 (console 창에서)
- Event : 유저가 브라우저에서 하는 모든 액션
    - 엄청 중요! 이걸 가지고 js에서 유저 액션을 제어
    - Browser
    - 물리장치 : 마우스, 키보드, 터치 를 통해서 브라우저에 무언가를 할 수 있음 (클릭할수도 있고)

    ![3/Untitled%202.png](3/Untitled%202.png)

    - 액션이 일어나는 것 = Fire
        - (스크롤을 했다, 뭘 했다)
        - 이벤트가 발생 = Fire Event
- 이벤트 종류 자체가 많음. 유저가 하는 모든 걸 캐치
- Mouse, keyboard, Touch, scroll, click, load 등등

![3/Untitled%203.png](3/Untitled%203.png)

- 애니메이션 구현은 별로 안 어려운데, 논리를 짜기가 어려움

![3/Untitled%204.png](3/Untitled%204.png)

- 원을 내려오게 하고 싶은데, 몇초 후에 내려올 지 투명도는 어떻게 줄지 등등 고민
- 개발자에게 절대로 해서는 안되는 말 : 슝! ㅋㅋㅋㅋㅋ 칼들고 쫓아온대 ㅠㅜㅠㅜ 이미 했는뎈ㅋㅋㅋㅋㅋ
- 250px 움직였냐 300px 움직였나, 가속을 어마나 줄 거냐에 따라 많이 달라지기 때문에 어렵다
- 인터랙션 가이드는 디테일 할 수록 좋다.
- 프레임웍, 프로토파이 등등 다 호환되게 만든 것들

### 실제 구현

- 자바스크립트 기본 문법
- [https://codepen.io/ChoEun/professor/GRJNELO](https://codepen.io/ChoEun/professor/GRJNELO)

    // 이벤트 부여
    window.addEventListener("scroll", 
    	function() {
    		//원래 window.scrollY 라고 써야하는데 자식이라서 window 생략 가능
    		console.log(scrollY)
    })
    

    body {
      margin: 0;
    }
    .screen {
      width: 100vw;
      height: 100vh;
      background: hotpink;
      transition: 1s background;
    }
    .screen:nth-of-type(even) { //우선순위
      background: royalblue;
    }
    .screen.screen-on {
      background: gold;
    }

    <div class="screen"></div>
    <div id="target-screen" class="screen"></div>
    <div class="screen"></div>
    <div class="screen"></div>

- 돔의 지옥..! taget-screen은 뭐의 자식일까? 어떤 요소의 하위 일까?

    <구조>
    // window
      // document
        // html
          // body
            // div
    				// div 
    				// ...

- html의 모든 요소는 document 안에 있음

    document.querySelector("#taget-sceen") 
    // css selector를 가지고 dom을 찾는 것
    // querySelector: 특정요소를 가지고 옴 
    
    document.querySelector("#taget-sceen").offsetTop
    // 304 정도 나옴. 상단 위치에서부터 스크롤이 얼마나 떨어져있는 지 알려줌.

- console에서 잘 나오는 지 테스트 해보기. 테스트는 꾸준히 계속하자
- 이제 논리 구조를 만들자.
    1. 스크롤 위치 
    2. 타겟 요소의 스크롤 위치
    - if문!
    - .classList.add() : 클래스를 찾아서 목록에 위치 시킴

    // 이벤트 부여
    window.addEventListener("scroll", function() {
      console.log(scrollY);
      
      
      // scroll 위치
      // 타겟 요소의 scroll 위치
      
      if(scrollY > document.querySelector("#target-screen").offsetTop) {
        document.querySelector("#target-screen").classList.add("screen-on")
        // do Something
      } else {
        // do Something   
      }
    })

- 잘 됨! 근데 문제가 있다?
- 끝까지 도달해야 애니메이션이 나옴. 넣는 것까진 성공했지만 모든 게 끝난 건 아니다. 디테일한 조정 필요. 그래서 시놉시스가 필요하다!
- 하나 더 추가 : 다시 위로 갔다가 아래로 가면 애니메이션이 같이 되게 하고 싶다.
    - 클래스로 제어해도 되지만, remove가 있음

    // 이벤트 부여
    window.addEventListener("scroll", function() {
      console.log(scrollY);
      
      
      // scroll 위치
      // 타겟 요소의 scroll 위치
      
      if(scrollY > document.querySelector("#target-screen").offsetTop) {
        document.querySelector("#target-screen").classList.add("screen-on")
        // do Something
      } else {
        document.querySelector("#target-screen").classList.remove("screen-on")
        // do Something   
      }
    })

- js의 변수
    - let : 숫자들어가면 안되고 _들어가면 안되고
    - const = 상수 선언 (바뀌지 않는 값)

    // 이벤트 부여
    // 이벤트 부여
    window.addEventListener("scroll", function() {
      // let = 변수 선언
      let targetScreen = document.querySelector("#target-screen");
      
      // const = 상수 선언
      const tyming = 100;
    	//타이밍은 이제 쭉 100임
      
      if(scrollY > targetScreen.offsetTop) {
        targetScreen.classList.add("screen-on")
        // do Something
      } else {
        targetScreen.classList.remove("screen-on")
        // do Something   
      }
    })
    // let을 설정해주니까 targetScreen으로 깔끔하게 바꿀 수 있음 

- var는 오래되서 쓰지 않음.
    - var와 let 차이?

    var a = 10;
    var a = 20;
    var a = 30;
    //가능
    let a = 10;
    a = 20;
    a = 30;
    //이렇게 써줘야함 

- 마우스 이벤트

    window.addEventListener("mousemove", function(e) {
      console.log(e)
    })
    // 유저가 움직이는 마우스움직임 확인 가능 
    
    window.addEventListener("mousemove", function(e) {
      console.log(e.clientX, e.clientY);
    })
    // 유저가 사이트 내에서 움직이는 거 파악 가능 -> ux적으로 분석 가능

- id는 한 html 내에서 중복이 안됨. 특정한 이름(키)를 발급하는 것.
- React로 쓸 때

    const App = () => {
      return render(
        <div>Hello</div>
      )
    }
    // 자바 스크립트 인데 조금 다름 

- 개발자들끼리도 리액트다 뷰다 앵귤러다 로 싸움 ㅎㅎ

### 실습 2

    // 이벤트 부여
    
    window.addEventListener("scroll", function(e) {
      console.log(scrollY, e)
    })
    //addEventListener 철자 주의~ 

    // 이벤트 부여
    
    let prevScrollPosition = scrollY;
    
    window.addEventListener("scroll", function() {
      if(prevScrollPosition > scrollY) {
        document.querySelector("header").classList.remove("header-off")
        // header 보여주기
      } else {
        document.querySelector("header").classList.add("header-off")
        // header 없애기
      }
      
      prevScrollPosition = scrollY;
    })
    
    window.addEventListener("scroll", function() {
      // let = 변수 선언
      let targetScreen = document.querySelector("#target-screen");
      
      // const = 상수 선언
      const tyming = 100;
      
      if(scrollY > targetScreen.offsetTop) {
        targetScreen.classList.add("screen-on")
        // do Something
      } else {
        targetScreen.classList.remove("screen-on")
        // do Something
      }
    })

    body {
      margin: 0;
    }
    header {
      width: 100%;
      position: fixed;
      top: 0;
      left: 0;
      height: 100px;
      background: black;
      transition: .4s transform;
    }
    .header-off {
      transform: translate(0, -100%);
    }
    .screen {
      width: 100vw;
      height: 100vh;
      background: hotpink;
      transition: 1s background;
    }
    .screen:nth-of-type(even) {
      background: royalblue;
    }
    .screen.screen-on {
      background: gold;
    }

![3/Untitled%205.png](3/Untitled%205.png)

- 애플 에어팟 사이트 애니메이션 구현 과정 봄 ㅎㅎ
    - 캔버스에서 하나하나 스톱모션처럼 사진이 움직이는 걸 자바스크립트로 구현
    - 왜 영상으로 안했을까? → 동영상은 시작과 끝을 조정하기가 어려운 반면, 구현하는 방식은 내가 다 조절할 수 있으니까
    - 웹진 three.js 에서 3d 모델링을 웹으로 구현한 것도 볼 수 있음 (캔버스에서 이런것도 할 수 있다!)