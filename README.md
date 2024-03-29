# 정한서 201930129

## 3월 27일 강의

### JSX
- JSX란 Javascript Syntax eXtension 즉 자바스크립트를 확장한 문법이다. 

1. JSX의 역할
    - JSX는 내부적으로 XML/HTML 코드를 자바스크립트로 변환
    - React가 createElement함수를 사용하여 자동으로 스크립트로 변환해 줌
    - JS로 작업할 경우 직접 createElement함수를 사용해야한다.
    - 결국 JSX는 가독성을 높여주는 역할을 한다.

2. JSX의 장점
    - 코드가 간결하다.
    - 가독성이 좋아 유지보수가 용이하다.
    - Injection Attact 해킹방법을 방어함으로써 보안에 강하다.

3. JSX 사용법
    - 모든 자바스크립트 문법을 지원한다.
    - 자바스크립트 문법에 XML과 HTML을 섞어서 사용한다.
    - HTML이나 XML에 자바스크립트 코드를 사용하고 싶으면 {}괄호를 사용한다.
    - 태그의 속성값을 넣고 싶은 때는 다음과 같이 한다.
    ```jsx
    // 큰따옴표 사이에 문자열을 넣거나
    const element = <div tabIndex="0"></div>;
    // 중괄호 사이에 자바스크립트 코드를 넣으면 됨
    const element = <img src={user.avatarlr}></img>;
    ```
### Element Rendering
- 엘리먼트의 정의
    - 리액트 앱을 구성하는 요소를 의미
    - 공식페이지에는 "엘리먼트는 리액트 앱의 가장 작은 빌딩 블록들"이라고 설명하고 있다.
    - 웹사이트의 경우는 DOM 엘리먼트이며, HTML요소를 의미한다.

    - 리액트 엘리먼트와 DOM 엘리먼트의 차이  
    
    | |DOM|Virtual DOM|
    |---|---|---|
    |업데이트|느리다|빠르다|
    |element업테이트 방식|DOM 전체 업데이트|해당 엘리먼트와 그 자식 엘리먼트를 이전의 엘리먼트와 비교하여 필요한 경우에만 DOM을 업데이트합니다.|
    |메모리|낭비가 심함|효율적|

- 엘리먼트의 생김새
    - 리액트 엘리먼트는 자바스크립트 객체의 형태로 존재한다.
    - 컴포넌트, 속성 및 내부의 모든 children을 포함하는 일반 JS객체입니다.
    - 이 객체는 마음대로 변경할 수 없는 불변성을 갖고 있다.

- 엘리먼트의 특징
    - 리액트 엘리먼트의 가장 큰 특징은 불변성이다.
    - 한번 생성된 엘리먼트의 children이나 속성을 바꿀 수 없다.

- 엘리먼트 렌더링하기  
    **Root DOM node**
    html코드는 id값이 root인 div태그로 단순하지만 리액트에 필수로 들어가는 아주 중요한 코드이다.
    이 div태그안에 리액트 앨리먼트가 렌더링 하게되면, 이 것을 root DOM node라고 합니다.
    앨리먼트를 렌터링하기 위해서는 다음과 같은 코드가 필요
    
    ```jsx
    <div id="root"></div>
    ReactDOM.render(element, document.getElementById('root'));
    ```
    이때 render()함수를 사용

- 렌더링된 엘리먼트 업데이트하기
    - 다음 코드는 tick() 함수를 정의
    - 현재 시간을 포함한 element를 생성 root div에 렌더링
    - setInterval() 함수를 이용해 위해서 정의한 tick() 1초에 한번씩 호출
    - 1초에 한번씩 element를 새로 만들고 교체
    ```jsx
    function tick() {
        const element = (
        <div>
            <h1>Hello, world!</h1>
            <h2>It is {new Date().toLocaleTimeString()}.</h2>
        </div>
        );
        ReactDOM.render(element, document.getElementById('root'));
    }
    setInterval(tick, 1000);
    ```
- 컴포넌트와 Props
    - 리액트는 컴포넌트 기반의 구조를 가진다.
    - 컴포넌트 구조는 작은 컴포넌트가 모여 큰 컴포넌트를 구성하고서 이런 컴포넌트들이 모여서 전체 페이지를 구성한다.
    - 컴포넌트는 재사용이 가능하기 때문에 <u>전체 코드 양</u>을 줄일 수 있어 <u>개발 시간</u>과 <u>유지보수 비용</u>도 줄일 수 있다.
    - 컴포넌트는 JS 함수처럼 입력과 출력이 있다는 면에서는 유사하다.
    - 입력은 Props가 담당, 출력은 리액트 엘리먼트의 형태로 출력
    - 엘리먼트를 필요한 만큼 만들어 사용한다는 면에서는 객체지향과 유사하다.

- Props의 개념
    - props는 prop(property:속성, 특성)의 준말이다.
    - props가 컴포넌트의 속성
    - 컴포넌트에 어떤 속성, props를 넣느냐에 따라서 속성이 다른 엘리먼트가 출력
    - props는 컴포넌트에 전달 할 다양한 정보를 담고 있는 JS 객체이다

- Props의 특징
    - 읽기 전용
    - 속성이 다른 엘리먼트를 생성하려면 새로운 props를 컴포넌트에 전달하면 된다.

- Pure 함수 VS Impure 함수
    - Pure함수는 인수로 받은 정보가 함수 내부에서 <u>변하지 않는 함수</u>.
    - Impure함수는 인수로 받은 정보가 함수 내부에서 <u>변하는 함수</u>.
    ```jsx
    // Pure 함수
    function sum(a, b) {
        return a + b
    }
    // Impure 함수
    function withraw(account, amount) {
        account.total -= amount
    }
    ```
※ React 공식 문서에 의하면 다음과 같다.
- 모든 리액트 컴포넌트는 그들의 props에 관하여 Pure 함수 같은 역할을 해야 한다.
- 모든 리액트 컴포넌트는 props를 직접 바꿀 수 없고, 같은 props에 대해 항상 같은 결과를 보여준다.

## 3월 20일 강의

### React
1. 리액트는 무엇인가?
    > 사용자 인터페이스를 만들기 위한 자바스크립트 라이브러리.

2. 다양한 JavaScript UI Framworks
    1. React.js
    2. Express
    3. Next.js
    4. Vue.js
    5. Anguler
    6. Node.js
    7. Svelte
    8. NestJS
    9. NuxtJS
    10. Gatsby

3. 리액트 개념 정리
    - 복잡한 사이트를 쉽고 빠르게 만들고, 관리하기 위해 만들어진 것이 바로 리액트
    - 다른 표현으로는 SPA를 쉽고 빠르게 만들 수 있도록 해주는 도구

4. 리액트의 장점
    1. 빠른 업데이트와 렌더링 속도
        - Virtual DOM 방식

        - DOM ( Document Object Model ) 이란 XML, HTML 문서의 각 항목을 계층으로 표현하여 생성, 변형, 삭제할 수 있도록 돕는 인터페이스. W3C의 표준이다.
        
        - Virtual DOM은 DOM 조작이 비효율적인 이유로 속도가 느리기 때문에 고안된 방법
        
        - DOM은 동기식, Virtual DOM 비동기식 방법으로 렌더링
        ![Virtual DOM 렌더링](https://velog.velcdn.com/images/dongjun187/post/d87f9425-b92b-4a96-8a53-d55fd87dbbc6/image.png)
        출처 : https://velog.io/@dongjun187/React-Virtual-DOM-%EA%B8%B0%EC%B4%88-%EB%8F%99%EC%9E%91-%EC%9B%90%EB%A6%AC
        
        - 브라우저의 동작 원리 : Gecko와 유사하다
        ![웹킷 동작 과정](https://d2.naver.com/content/images/2015/06/helloworld-59361-3.png)  
        출처 : https://d2.naver.com/helloworld/59361

    2. 컴포넌트 기반 구조
        - 리액트의 모든 페이지는 컴포넌트로 구성
        - 하나의 컴포넌트는 다른 여러개의 컴포넌트의 조합으로 구성
        - 리액트로 개발을 하다보면 레고 블록을 조립하는 것처럼 컴포넌트를 조합해서 웹사이트를 개발하게 됨
        - 에어비앤비 사이트 화면의 컴포넌트 구조

    3. 재사용성
        - 반복적인 작업을 줄여주기 때문에 생선성을 높여준다.
        - 유지보수가 용이하다.
        - 재사용이 가능 하려면 해당 모듈의 의존성이 없어야함
    
    4. 든든한 지원군 
        - 메타 ( 구 : 페이스북 ) 에서 오픈소스 프로젝트로 관리하고 있어 계속 발전하고 있다.
    
    5. 활발한 지식공유 & 커뮤니티

    6. 모바일 앱 개발가능
        - 리액트 네이티브라는 모바일 환경 UI프레임워크를 사용하면 크로스 플랫폼 모바일앱을 개발할 수 있음

5. 리액트의 단점
    1. 방대한 학습량
        - 자바스크립트를 공부한 경우 빠르게 학습할 수 있다.

    2. 높은 상태 관리 복잡도
        - state, component life cycle 등의 개념이 있지만 그리 어렵지 않다.

6. 리액트 설치
- 터미널에 npx create-react-app 폴더명
- 오류 발생 시 조치사항
    - npm 버전이 최신인지 확인 `npm -v`
    - npm 최신버전 설치 후 실행 `npm install -g npm@latest`
    - npm 삭제 후 재설치
        ```
        npm uninstall -g create-react-app
        npm install -g create-react-app
        ```
    - npm 캐시 삭제 후 실행
        ```
        npm cache clean --force
        npm install
        ```

## 3월 13일 강의

### HTML
1. HTML이란 무엇인가?
    > [Hyper Text Markup Language] 웹 페이지 표시를 위해 개발된 지배적인 마크업 언어다.
    > 또한, HTML은 제목, 단락, 목록 등과 같은 본문을 위한 구조적 의미를 나타내는 것뿐만 아니라 링크, 인용과 그 밖의 항목으로 구조적 문서를 만들 수 있는 방법을 제공한다.

2. 웹사이트의 뼈대를 구성하는 태그들  

    ![Layout tag](https://thebook.io/img/006943/065_1.jpg)

3. SPA(Single Page Application)
   > 싱글 페이지 애플리케이션은 서버로부터 완전한 새로운 페이지를 불러오지 않고 현재의 페이지를 동적으로 다시 작성함으로써 사용자와 소통하는 웹 애플리케이션이나 웹사이트를 말한다.

   아래 그림은 SPA와 MPA의 차이를 설명하는 그림
   ![SPA vs MPA](https://miro.medium.com/v2/resize:fit:1358/1*zr1yTjLEsUZB6BkEve8FTA.png)
### 자바 스크립트
1. 자바스크립트란 무엇인가?
   > 1995년 넷스케이프에서 근무하던 브랜든 아이크에 의하여 개발되었다.  
   > 자바스크립트는 객체 기반의 스크립트 프로그래밍 언어이다.  
   > 이 언어는 웹 브라우저 내에서 주로 사용되며, 다른 응용 프로그램의 내장 객체에도 접근할 수 있는 기능을 가지고 있다.  
   > 또한 Node.js와 같은 런타임 환경과 같이 서버 프로그래밍에도 사용되고 있다.  
   > JavaScript (JS)는 가벼운, 인터프리터 혹은 just-in-time 컴파일 프로그래밍 언어로, 일급 함수를 지원한다.

2. ES6 (ECMAScript6) - 표준 ECMA-262
   > JavaScript ES6 ( ECMAScript 2015 또는 ECMAScript 6 이라고도 함 )은 2015년에 도입된 최신 버전의 JavaScript
   > ECMAScript 는 JavaScript 프로그래밍 언어가 사용하는 표준

3. 자바스크립트의 자료형
    - var : 중복 선언 <u>가능</u>, 재할당 가능
    - let : 중복 선언 <u>불가능</u>, 재행당 가능
    - const : 상수
    - Array type : 배열 [ ]
    - Object type : 객체 **{ key : value }** <- JSON 스타일

4. 자바스크립트의 연산자
    - 할당 연산자 : `=`
    - 비교 연산자 : `>=`, `<=`, `==`, `!=`, `>`, `<`
    - 산술 연산자 : `+`, `-`, `*`, `/`, `%`, `**`, `++`, `--`
    - 비트 연산자 : `&`, `|`, `^`, `~`, `>>`, `<<`, `>>>`, `<<<`
    - 논리 연산자 : `&&`, `||`, `!`
    - 문자열 연산자 : `"한" + "글" == "한글"`
    - 조건 (삼항) 연산자 : `let status = age >= 18 ? "성인" : "미성년자"`
    - 단항 연산자 : `delete`, `typeof`, `void`
    - 관계 연산자 : `in`, `instanceof`

5. 자바스크립트 함수
    - Fucntion statement 형 : 일반적 함수의 형태
    ```js
    function sum(a, b) {
        return a + b
    }
    console.log(sum(10, 20))
    ```
    - Arrow function expression 형 : 화살표 함수
    ```js
    const sum = (a, b) => {
        return a + b
    }
    console.log(sum(10, 20))
    ```
    
### Node.js
다운로드 https://nodejs.org/en

LTS = 안정적  
Current = 가장 최신
<br>

## 3월 6일 강의
### 내용
> 아이폰 출시 이후 모바일 트래픽이 데스크톱 트래픽을 추월함  
semantic versioning 이란 [유의적 버전]
버전을 주. 부. 수 숫자로 하고
기존 버전과 호환되지 않게 API가 바뀌면 '주(主) 버전'을 올림
기존 버전과 호환되면서 새로운 기능을 추가할 때는 `부(部)버전` 올림
기존 버전과 호환되면서 버그를 수정한 것이라면 `수(修)버전` 올림

```md
# h1
## h2
### h3
#### h4
##### h5
###### h6

# 리스트
1. 첫번쨰
2. 두번째
3. 세번째

- 첫번째
- 두번째
- 세번째

*이텔릭체*  
**굵게**  
***이텔릭+굵게***  

```js ``` <- 코드작성  

개행은  
스페이스 두개
[구글 링크](https://www.google.com)  
[페이지 내 링크](#리스트)  
![리트리버 인절미](puppy-1189067_1280.jpg)
```
