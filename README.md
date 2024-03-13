# 정한서 201930129

## 3월 20일 강의
내용

## 3월 13일 강의

### HTML
1. HTML이란 무엇인가?
2. 웹사이트의 뼈대를 구성하는 태그들
3. SPA(Single Page Application)

### 자바 스크립트
1. 자바스크립트란 무엇인가?

2. ES6 (ECMAScript6) - 표준 ECMA-262

3. 자바스크립트의 자료형
    - var : 중복 선언 <u>가능</u>, 재할당 가능
    - let : 중복 선언 <u>불가능</u>, 재행당 가능
    - const : 상수
    - Array type : 배열 [ ]
    - Object type : 객체 **{ key : value }** <- JSON 스타일

4. 자바스크립트의 연산자

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
기존 버전과 호환되면서 버그를 수정한 것이라면 '수(修)버전' 올림

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