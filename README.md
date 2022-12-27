# Vue



## 사전 준비

- VSCode Vetur extension 설치
  - 문법 하이라이팅, 자동완성, 디버깅 기능 제공
- Chrome Vue devtools extension 설치 및 설정
  - 크롬 브라우저 개발자 도구에서 vue 디버깅 기능 제공

---

## Front-end Development

- Vue.js === JavaScript Front-end Framework

- Front-end ( FE ) 개발이란?
  
  - 사용자에게 보여주는 화면 만들기

- Web APP ( SPA ) 을 만들 때 사용하는 도구
  
  - SPA - Single Page Application

- Web App이란?
  
  - 웹 프라우저에서 실행되는 어플리케이션 소프트웨어
  - 개발자 도구 > 디바이스 모드
  - 웹 페이지가 그대로 보이는 것이 아닌, **디바이스에 설치된 App**처럼 보이는 것
  - 웹 페이지가 디바이스에 맞는 적절한 UX/UI로 표현되는 형태

- SPA ( Single Page Application )
  
  - Web App과 함께 자주 등장할 용어 SPA
  
  - 이전까지는 사용자의 요청에 대해 적절한 페이지 별 template을 반환
  
  - SPA는 서버에서 최초 1장의 HTML만 전달받아 모든 요청에 대응하는 방식
    
    - 어떻게 한 페이지로 모든 요청에 대응할 수 있을까?
    
    - **CSR** ( Client Side Rendering ) 방식으로 요청을 처리하기 때문
      
      - 참고) SSR vs CSR
        
        - SSR
          
          - 기존의 요청 처리 방식은 SSR
          - Server가 사용자의 요청에 적합한 HTML을 렌더링하여 제공하는 방식
          - 전달 받은 새 문서를 보여주기 위해 브라우저는 새로고침을 진행
          
          ![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/786863ee-f3c0-4abf-83bd-3632a12e39cc/Untitled.png)
        
        - CSR
          
          - 최초 한 장의 HTML을 받아오는 것은 동일
            - 단, server로부터 최초로 받아오는 문서는 빈 HTML 문서
          - 각 요청에 대한 대응을 JavaScript를 사용하여 필요한 부분만 다시 렌더링
          1. 필요한 페이지를 서버에 AJAX로 요청
          2. 서버는 화면을 그리기 위해 필요한 데이터를 JSON 방식으로 전달
          3. JSON 데이터를 JavaScript로 처리, DOM 트리에 반영 ( 렌더링 )
          
          ![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/e606eae4-41e2-4832-b113-e2450b1b912a/Untitled.png)
        
        - 왜 CSR 방식을 사용하는 걸까?
          
          1. 모든 HTML 페이지를 서버로부터 받아서 표시하지 않아도 됨
             
             == 클라이언트 - 서버간 통신, 즉 트래픽 감소
             
             == 트래픽이 감소한다
             
             == 응답 속도가 빨라진다
          
          2. 매번 새 문서를 받아 새로고침하는 거시 아니라 필요한 부분만 고쳐 나가므로 각 요청이 끊김없이 진행
             
             - SNS에서 추천을 누를 때마다 첫 페이지로 돌아간다 = 끔찍한 App
             - 요청이 자연스럽게 진행된다 = UX 향상
          
          3. BE와 FE의 작업 영역을 명확히 분리할 수 있음
             
             - 각자 맡은 역할을 명확히 분리한다 = 협업이 용이해짐
        
        - CSR은 만능일까?
          
          - 첫 구동 시 필요한 데이터가 많으면 많을수록 최초 작동 시작까지 오랜 시간이 소요
          - Naver, Netflix, Disney+ 등 모바일에 설치된 Web-App을 실행하게 되면 잠깐의 로딩 시간이 필요
          - **검색 엔진 최적화** ( SEO, Search Engine Optimization ) 가 어려움
            - 서버가 제공하는 것은 텅 빈 HTML
            - 내용을 채우는 것은 AJAX 요청으로 얻은 JSON 데이터로 클라이언트(브라우저)가 진행
          - 대체적으로 HTML에 작성된 내용을 기반으로 하는 검색 엔진에 빈 HTML을 공유하는 SPA 서비스가 노출되기는 어려움
          - 참고) SEO ( Search Engine Optimization )
            - google, bing과 같은 검색 엔진 등에 내 서비스나 제품 등이 효율적으로 검색 엔진에 노출되도록 개선하는 과정을 일컫는 작업
            - **검색** = 각 사이트가 운용하는 검색 엔진에 의해 이루어지는 작업
            - **검색 엔진** = 웹 상에 존재하는 가능한 모든 정보들을 긁어 모으는 방식으로 동작
              - 정보의 대상은 주로 HTML에 작성된 내용
              - JavaScript가 실행된 이후의 결과를 확인하는 과정이 없음
            - 최근에는 SPA, 즉 CSR 로 구성된 서비스의 비중이 증가
              - SPA 서비스도 검색 대상을 넓히기 위해 JS를 지원하는 방식으로 발전
            - 단, 단순 HTML만을 분석하는 것보다 몇 배의 리소스가 필요한 작업이기에 여전히 CSR의 검색 엔진 최적화 문제가 모두 해결된 것은 아님
        
        - CSR과 SSR은 흑백이 아님
          
          - 내 서비스에 적합한 렌더링 방식을 적절하게 활용할 수 있어야 함
        
        - SPA 서비스에서도 SSR을 지원하는 Framework이 발전하고 있음
          
          - Vue의 Nuxt.js
          - React의 Next.js
          - Angular Universal 등
  
  - 여러 가지 Front-end Framework
    
    - Front-end Framework == HTML + CSS + JS를 더 편하게 작업하기 위한 툴
      - React, Angular, Svelte, Vue 등
    - 이런 Framework를 꼭 써야 할까?
      - NO! 더 쉽게 개발하기 위해서 사용하는 것
      - 실제로 Github는 이러한 Front-end Framework를 사용하지 않음
      - 하지만 대부분의 기업에서는 생산성과 협업을 위해 Framework를 사용해서 개발
  
  - Vue CDN
    
    - Vue로 작업을 시작하기 위하여 CDN을 가져와야 함
    
    - Django == Python Web Framework
      
      - pip install
    
    - Vue === JS Front-end Framework
      
      - Bootstrap에서 사용하였던 CDN 방식 제공
    
    - Vue CDN을 위하여 Vue2 공식 문서 접속
      
      - [https://v2.vuejs.org/](https://v2.vuejs.org/)
      1. Getting Started
      2. Installation
      3. Development version CDN 복사
      
      ---
      
      
