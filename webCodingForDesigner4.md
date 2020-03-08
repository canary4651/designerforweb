# 디자이너를 위한 웹코딩4

- Transform: css 요소를 변형시키는 css 속성 중 하나
- opacity
- html → parse 렌더링 : DOM
- css → cssom
- 합쳐서 render tree

- 화면에 그린 요소들을 정리
- 트리 구조
- render tree - reflow (flow를 계산하는 과정) - repaint(화면에 그려줌)
- reflow와 repaint가 웹의 성능 90%, 웹에서 그림이 느리면 reflowrk 느린거.

![4/Untitled.png](4/Untitled.png)

- 이미지 크기 줄이기, 비디오 용량 줄이기 문제가 첫 이슈 : 한계 존재

![4/Untitled%201.png](4/Untitled%201.png)

- transfrom: translate(0,0) ← css function
    - **translate(x,y) : 이동 많이씀**
    - **scale(%)**
    - rotate(deg)
    - matrix
    - 3d로 가면 밑도끝고 없음,,, 대신 담주엔 평면에서 보여지는 3d할거임
- opacity
- absolute
- fixed

- animation이 많아지면 성능이 느려짐
- -[https://codepen.io/ChoEun/pen/NWqjZYN](https://codepen.io/ChoEun/pen/NWqjZYN)

    <div class="box"></div>

    body {
      margin: 0;
    }
    .box {
      width: 150px;
      height: 150px;
      background: royalblue;
      animation: 1s move-animation;
      animation-fillmode: forward;
    }
    
    @keyframes move-animation {
      0% {
        /* start */
        transform: translate(0, 0);
      }
      100% {
        /* end */
        transform: translate(100px, 200px)
      }
    }

    body {
      margin: 0;
    }
    .box {
      width: 150px;
      height: 150px;
      background: royalblue;
      animation: 3s move-animation;
      animation-iteration-count: infinite;
      animation-fill-mode: forwards;
    }
    
    @keyframes move-animation {
      0% {
        /* start */
        transform: translate(0, 0);
      }
      50% {
        /* end */
        transform: translate(100px, 200px);
        transform-origin: top left;
    // transform은 중앙부터 시작 
    // 프레임수로 움직이지는 않음 
      }
      100% {
        transform: translate(0, 0);
      }
    }

    // html
    <div class="container">
      <div class="box"></div>
    </div>
    //
    
    
    
    body {
      margin: 0;
    }
    .container {
      width: 100px;
      height: 100px;
      background: crimson;
    }
    .box {
      width: 150px;
      height: 150px;
      background: royalblue;
      transform: translate(100vw, 100vh);
      /* 150, 150 */
    // 브라우저 크기도 지원 
    }
    
    
    // 돌아가게 바꾸기 
    
    body {
      margin: 0;
    }
    .container {
      width: 100px;
      height: 100px;
      background: crimson;
    }
    .box {
      width: 150px;
      height: 150px;
      background: royalblue;
      transform: rotate(45deg);
      /* 150, 150 */
    }
    

// 스크롤 애니메이션 (우리가 하려는)

    <div class="wrapper">
      <div class="container">
        <div class="box box-opacity"></div>
        <div class="box box-opacity"></div>
        <div class="box"></div>
        <div class="box box-opacity"></div>
        <div class="box box-opacity"></div>
      </div>
    </div>

    body {
      margin: 0;
    }
    
    .wrapper {
      width: 100vw;
      overflow: hidden;
    }
    .container {
      position: fixed;
      left: 0;
      top: 0;
      width: 100vw;
      display: flex;
      justify-content: space-between;
      transform: scale(5);
    }
    .box {
      width: 19vw;
      height: 100vh;
      background: royalblue;
    }
    .wrapper {
      height: 500vh;
    }
    .box-opacity {
      opacity: 0;
    }

    window.addEventListener("scroll", function() {
      if(scrollY <= 480) {
        let scaleY = (600 - scrollY) / 600;
        let opacity = scrollY / 480;
        let scale = scaleY * 5;
        document.querySelector(".container").setAttribute("style", "transform: scale(" + scale + ")");
        document.querySelectorAll(".box-opacity").forEach(function(o,i) {
          o.style.opacity = opacity;
        });
      }
    })
    
    // 최대값 기준으로 빠지는 역산계산 (0에서 600까지 애니메이션)
    // -> 600에서 0으로 바꾼거
    // setAttribute : 속성을 바로 지정

//논리 설명 

-