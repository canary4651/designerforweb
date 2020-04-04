# 디자이너를 위한 웹코딩7

# JavaScript

## Basis

### Table of Content

- History
    - 1995년
- A Brief concept of API
    - API : application Programming Interface
    - 특정한 어플리케이션 개발을 하기 위한 도구들의 집합
    - 크롬 브라우저
        - 내가 개발하는 모든 웹사이트는 크롬이라는 어플맄이션을 통해서 오픈
        - 브라우저 내의 특정 기능을 사용한 기능을 내 웹사이트에 구현
            - 브라우저 api
        - scroll event
            - browser Api > Event APi

    어디까지가 api고 어디까지가 언어일까? → 이 특징을 잘 분리해서 생각하기 

- Variables
    - 변수( 그릇)
    - 특정한 값은 특정한 키워드에 저장하는 것 = 변수

        const start
        10 // Number
        
        return 10 * 30; //40
        
        // 논리의 연속
        // 만약에 a가 10이라면 do something 
        // 만약에 a가 20이라면 do something
        
        let hour = 10
        let minute = 50
        let second = 40
        
        retrun `${hour}:${minute}:${second}`

- scope
    - 변수명은 중복이 가능

        let hour = 10
        let minute = 50
        let second = 40
        
        retrun `${hour}:${minute}:${second}`

        let num = 50;
        
        function sum() {
          let num = 300;
          // 300
          return num + num;
        }
        
        console.log(sum());
        
        num = 100;
        
        console.log(sum());
        // 600
        
        num = 1000;
        
        // num = 1000
        
        console.log(sum());
        // 600
        
        num = sum();
        
        // num = 600

- Types🤯
    - 데이터의 형태
    - Number
    - String
    - Boolean
    - Object
    - Undefined
    - Null

        // Number
        // 64비트 부동소수점 (소수점, 양수, 음수)
        let num = 100;
        let negative = -10;
        let decimal = 0.1;
        
        // String
        let name = "조은"
        
        // String에 우선순위를 가집니다.
        // 10100
        "10" + 100 // "10100"
        100 + "10" // "10010"
        
        // Boolean
        let buy = true; // true or false
        
        // Object
        let choeun = {
          name: "조은",
          age: 28
        }

- FUNCTIONS
- Objects
    - [https://codepen.io/ChoEun/professor/abOrPzX?editors=1011](https://codepen.io/ChoEun/professor/abOrPzX?editors=1011)

        // Object (객체)
        // Object Oriented Programming (객체 지향 프로그래밍)
        
        // Object (객체)
        // key : value로 이루어진 값
        
        // 이름 : 조은
        // 나이 : 28
        // 성별 : 남성
        // 주소 : ??
        
        let choeun = {
          name: "조은",
          age: 28,
          address: "서울시 강남구 역삼동 XXX"
        }
        
        // 객체라는게 무제한으로 생성 가능하다 (1)
        
        choeun.name; // "조은"
        choeun.age; // 28
        choeun.address; // "서울시 강남구 역삼동 XXX"
        
        // 객체 지향
        // 제 3자가 내 코드를 해킹하는 걸 방지
        
        (function() {
          
          let newsData = {
            "bloter": {
              "title": "블로터 2000",
              "subscription": 1000000,
              "updated": "2019-04-04 11:27:00",
              "newsList": [
                {
                  "thumb": "https://",
                  "title": "폭탄들 막아라...",
                  "description": "코로나 19 확산으로...",
                  "href": "https://"
                },
                {
                  "thumb": "https://",
                  "title": "폭탄들 막아라...",
                  "description": "코로나 19 확산으로...",
                  "href": "https://"
                },
                {
                  "thumb": "https://",
                  "title": "폭탄들 막아라...",
                  "description": "코로나 19 확산으로...",
                  "href": "https://"
                }
              ]
            }
          }
          
          function drawNews() {
            for (newsTitle in newsData) {
              let news = newsData[newsTitle];
              
              let template = `
                <div class="news">
                  <div class="news-title">${news.title}</div>
                  <div class="news-subscription">${news.subscription}</div>
                  <div class="news-updated">${news.updated}</div>
                </div>`
              
              document.body.innerHTML = template
            }
          }
          
          drawNews();
          
        })() // 익명함수 호출
        
        
        // 컴퓨터 = 메모리
        // 메모리 사용량을 초과 = 클라이언트 뻗음
        // 메모리 사용량이 가장 많은 부분 = 객체

    <form id="form">
      <div>
        <label for="name">Name:</label>
        <input id="name" name="name">
      </div>
      <div>
        <label for="age">age:</label>
        <input id="age" name="age">
      </div>
      <div>
        <label for="address">address:</label>
        <input id="address" name="address">
      </div>
    	<input type="submit" value="데이터 전송하기">
    </form>
    
    <div id="result">
      
    </div>

    // DOM API
    // Document Object Model
    // 브라우저 상에 존재하는 HTML에 접근해서 데이터를 가져오거나, 편집하거나, 수정하거나 하는 API
    
    // Element API
    let form = document.querySelector("#form");
    
    console.log(form);
    
    let name = document.querySelector("#name");
    let age = document.querySelector("#age");
    let address = document.querySelector("#address");
    
    console.log(name, age, address) // input 3개가 나옴
    
    // person 이라는 객체
    let person = {
      name: name.value,
      age: age.value,
      address: address.value,
      nationality: 'South Korea'
    }
    
    // 1
    console.log(name.value, age.value, address.value);
    
    // 2
    console.log(person.name, person.age, person.address);
    
    // 2번이 더 보기 좋음 -> 직관적 (가독성) 
    
    
    // arrow function
    let onSubmit = (event) => {
      event.preventDefault();
    
    	let person = {
      name: name.value,
      age: age.value,
      address: address.value,
      nationality: 'South Korea'
    }
      
      let template = `
        <div class="person-data">
          <h1>${person.name}</h1>
          <p>${person.nationality} / ${person.age}</p>
          <p>${person.address}</p>
        </div>
      `
    	document.querySelector("#result").innerHTML = template;  
    }
    
    form.addEventListener("submit", onSubmit);
    
    

// 숙제 : Twitter 사이트의 Data Structure 고민해오기

- DOM
    - Elements
    - Events
- Babel
- WebPack

[https://github.com/nefe/You-Dont-Need-jQuery/blob/master/README.ko-KR.md](https://github.com/nefe/You-Dont-Need-jQuery/blob/master/README.ko-KR.md)