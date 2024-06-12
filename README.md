# 정한서 201930129

## 6월 12일 강의

### CSS란?

- CSS는 Cascading Style Sheets의 약자로 스타일링을 위한 언어입니다.

- Cascading이란 계단식이라는 뜻으로 여러 스타일을 한 엘리먼트에 적용될 경우 <u>스타일간의 충돌을 막기 위해 계단식으로 스타일을 적용</u>

- 하나의 스타일이 여러 엘리먼트에 적용될 수 있고, 여러 스타일이 하나의 엘리먼트에 적용될 수 있음

### CSS 문법과 선택자

- 선택자를 먼저 쓰고 다음에 적용할 스타일을 중괄호 안에 세미콜론으로 구분하여 하나씩 작성.

- 스타일은 property(속성)과 key value(키 값)로 이루어 지며, 이들은 콜론(:)으로 구분하고, 각 스타일은 세미콜론(;)으로 구분

- 레이아웃과 관련된 속성

  - `display: none | block | inline | flex;`

  - none은 존재는 하지만 화면에 보이지 않는 것으로, 자바스크립트를 넣을 때 많이 사용

  - block은 세로로 정렬되며, width와 height를 갖을 수 있다. 크기와 상관없이 한 줄을 점유

  - inline은 가로로 정렬. width와 height 등 특성을 사용할 수 없다.
    -inline-block은 기본적으로 inline의 특성을 갖지만, width와 height 등 block의 특성을 사용할 수 있다.

  - `flex` : 컨테이너의 형태로 엘리먼트를 관리

  - `Grid` : Flex가 1차원적이라면, Grid는 2차원적이다.

  - visibility 속성은 엘리먼트의 가시성을 정의

  - `display:none` 과 `visibility:hidden` 의 차이

    - `display:none` 는 엘리먼트의 영역이 보이지 않음

    - `visibility:hidden` 는 영역은 보임

- 폰트와 관련된 속성

  - `font-size` : 단위 혹은 키워드로 사용된다.

    - 일반적으로 px, em, % 등의 단위를 사용한다.
    - 별도의 지정이 없을 경우 대부분 브라우저의 기본값은 16px = 1em 이다.

  - `font-style` : 기본값은 normal 이다.

    - 일반적으로 이탤릭체를 만들기 위해 많이 사용된다.

    - 이탤릭체를 위해서는 italic 또는 oblique 를 사용한다.

  - `font-weight` : 폰트의 가중치(weight)나 굵기(boldness)를 명시한다.

    - 기본값은 noraml = 400 이다.

    - bold, lighter, bolder 와 같은 키워드,
      혹은 100 단위의 숫자로 지정한다.

    - 폰트마다 지원하는 굵기의 정도가 약간씩 다를 수 있다.

  - `line-height` : 줄 상자의 높이를 설정한다.

    - 일반적으로 텍스트 줄 사이의 거리를 설정하는 데 사용된다.

    - 폰트 크기의 위/아래로 여백을 준다.

    - 기본값은 1.0 ~ 1.2 이다.

    - 폰트가 만들어질 때 기본적으로 디자인된다.

  - `font-family` : 요소에 우선 순위가 지정된 font family 이름과
    generic family 이름을 지정할 수 있게 해준다.

    - generic family : 브라우저가 대체할 수 있는 폰트가 필요한 경우 선택할 수 있게 해준다.

    - ex) serif, sans-serif, monospace, ...

### styled-components

- css 문법을 그대로 사용하면서 결과물을 스타일링된 컴포넌트 형태로 만들어 주는 오픈소스 라이브러리
- 컴포넌트의 개념을 사용하고 있어 리액트 갭라에 많이 사용된다.

  #### styled-components 설치하기

  - npm install styled-components

  #### styled-components 기본 사용법

  - 태그드 템플릿 리터럴을 사용하여 구성 요소의 스타일을 지정

  - 태그드 템플릿 리터럴은 자바스크립트에서 제공하는 문법 중 내장된 표현식을 허용하는 문자열 리터럴

  #### styled-components의 props 사용하기

  - props를 이용하여 조건이나 동적으로 변하는 값을 사용해서 스타일링를 할 수 있다.

  #### styled-components의 스타일 확장하기

  - 먼저 정의한 스타일 컴포넌트에 스타일을 추가하여 재정의

## 6월 11일 강의

### 상속에 대해 알아보기

- 이전 강의 이어서 ~

  #### [3]. Containment와 Specialization을 같이 사용하기

  - Containment를 위해서 `prop.children`을 사용하고, Specialization을 위해 직접 정의한 `props`를 사용하면 된다.

    ```jsx
    export default function FancyBorder(props) {
      return (
        <div className={`FancyBorder` + props.color}>{props.children}</div>
      );
    }
    ```

    ```jsx
    import FancyBorder from "./FancyBorder";

    export default function WelcomeDialog(props) {
      return (
        <FancyBorder color="blue">
          <h1 className="Dialog-title">어서와.</h1>
          <p className="Dialog-message">내 사이트는 처음이지?</p>
          {props.children}
        </FancyBorder>
      );
    }
    ```

- 합성과 대비되는 개념으로 상속이 있다.

- 자식 클래스는 부모 클래스가 가진 변수나 함수 등의 속성을 모두 갖게 되는 개념.

- 하지만 리액트에서는 상속보다는 합성을 통해 새로운 컴포넌트를 생성.

**복잡한 컴포넌트를 쪼개 여러 개의 컴포넌트로 만들고, 만든 컴포넌트들을 조합하여 새로운 컴포넌트를 만들자**

### 컨텍스트란 무엇인가?

- 기존의 일반적인 리액트에서는 데이가 컴포넌트의 `props`를 통해 부모에서 자식으로 단방향으로 전달하였음.

- 컨텍스트는 리액트 컴포넌트들 사이에서 데이터를 기존의 `props`를 통해 전달하는 방식 대신 _'컴포넌트 트리를 통해 곧바로 컴포넌트에 전달하는 새로운 방식'_ 을 제공한다.

- 이것을 통해 어떤 컴포넌트라도 쉽게 데이터에 접근할 수 있다.

### 언제 컨텍스트를 사용해야 할까?

- 여러 컴포넌트에서 자주 필요로 하는 데이터

- Ex) 로그인 여부, 로그인 정보, UI테마(다크/라이트 모드), 현재 선언된 언어 등

- `props`를 통해 데이터를 전달하는 방식은 계속 props로 넘겨줘야 하는 Props drilling을 해줘야 하기 때문에 불편하다(가독성 저하).

- **Props drilling**: 중첩된 여러 계층의 컴포넌트들에게 `props`를 전달해 주는 것

### 컨텍스트를 사용하기 전에 고려할 점

- 컨텍스트는 다른 레벨의 많은 컴포넌트가 특정 데이터를 필요로 하는 경우에 주로 사용한다.

- 하지만 무조건 컨텍스트를 사용하는 것이 좋은 것은 아니다.

- 컴포넌트와 컨텍스트가 연동되면 재사용성이 떨어지지 때문이다.

- 다른 레벨의 많은 컴포넌트가 데이터를 필요로 하는 경우가 아니면 `props`를 통해 데이터를 전달하는 컴포넌트 합성 방법이 더 적합하다.

### [1]. React.createContext

- Context 객체를 컴포넌트에서 렌더링할 때 React는 트리 상위에서 가장 가까이 있는 짝이 맞는 `Provider`로부터 현재값을 읽는다.

- `defaultValue` 매개변수는 트리 안에서 적절한 `Provider`를 찾지 못했을 때만 쓰이는 값입니다.

- `Provider`를 통해 `undefined`을 값으로 보낸다고 해도 컴포넌트들이 `defaultValue`` 를 읽지는 않는다는 점에 주의할 것

### [2]. Context.Provider

- `Provider`는 context를 사용하는 컴포넌트들에게 context의 변화를 알리는 역할을 한다.

- `Provider`` 컴포넌트는 value prop을 받아서 이 값을 하위에 있는 컴포넌트에게 전달한다.

- 값을 전달받을 수 있는 컴포넌트의 수에 제한은 없습니다.

- `Provider` 하위에 또 다른 `Provider`를 배치하는 것도 가능하며, 이 경우 하위 Provider의 값이 우선시됩니다.

- `Provider` 하위에서 context를 사용하는 모든 컴포넌트는 `Provider`의 value prop가 바뀔 때마다 다시 렌더링 됩니다.

### [3]. Class.contextType

- `React.createContext()`로 생성한 Context 객체를 원하는 클래스의 contextType 프로퍼티로 지정할 수 있습니다.

- 클래스 타입은 더 이상 사용하지 않음.

### [4]. Context.Consumer

- Context.Consumer의 자식은 함수여야한다.

- 이 함수는 context의 현재값을 받고 React 노드를 반환한다.

- 이 함수가 받는 value 매개변수 값은 해당 context의 `Provider`` 중 상위 트리에서 가장 가까운 Provider의 value prop과 동일하다.

- 상위에 `Provider`가 없다면 value 매개변수 값은 createContext()에 보냈던 defaultValue와 동일할 것이다.

### [5]. Context.displayName

- Context 객체는 `displayName` 문자열 속성을 설정할 수 있다.

- React 개발자 도구는 이 문자열을 사용해서 context를 어떻게 보여줄 지 결정합니다.

### 여러 개의 컨텍스트 사용하기

- 여러 개의 컨텍스트를 동시에 사용하려면 Context.Provider를 중첩해서 사용.

- 하지만 두 개 또는 그 이상의 컨텍스트의 값이 자주 함께 사용될 경우 모든 값을 한 번에 제공해주는 별도의 render prop 컴포넌트를 직접 만드는 것이 더 좋음

### useContext

- 함수형 컨포넌트에서 컨텍스트를 사용하기 위해 컴포넌트를 매번 Consumer 컴포넌트로 감싸주는 것보다 더 좋은 방법이 있다. 바로 Hook이다.

- 상위 컴포넌트의 data가 필요한 하위 컴포넌트들은 `useContext()` 훅을 사용해서 해당 데이터를 받아오기만 하면 된다.

- useContext는 Context로 분류한 데이터를 쉽게 받아올 수 있게 도와주는 역할을 한다.

- context는 꼭 필요할 때만 사용한다.

- context를 사용하면 컴포넌트를 재사용하기 어려워질 수 있다.

- context의 주된 목적인 다양한 레벨이 있는 많은 컴포넌트들에게 전역적인 데이터를 전달하기 위함이다.

- 리액트 공식 문서에는 context를 사용하는 이유가 단지 prop drilling을 핗기 위한 목적이라면 component composition(컴포넌트 합성)이 더 간단한 해결책이라고 제시하고 있다.

## 6월 5일 강의

### Shared State

- Shared state는 state의 공유를 의미한다.

- 같은 부모 컴포넌트의 state를 자식 컴포넌트가 공유해서 사용하는 것이다.

- 다음 그림은 부모 컴포넌트가 섭씨 온도의 state를 갖고 있고, 이것을 컴포넌트 C와 컴포넌트가 공유해서 서용하는 것을 보여줌

  ![Shared State](https://ko.react.dev/_next/image?url=%2Fimages%2Fdocs%2Fdiagrams%2Fsharing_state_child.png&w=1080&q=75)

### Shared State 적용하기

```jsx
export default function TemperatureInput(props) {
  const handleChange = (event) => {
    props.onTemperatureChange(event.target.value);
  };
  const scaleNames = {
    c: "섭씨",
    f: "화씨",
  };
  return (
    <fieldset>
      <legend>온도를 입력해주세요(단위:{scaleNames[props.scale]}):</legend>
      <input value={props.temperature} onChange={handleChange} />
    </fieldset>
  );
}
```

```jsx
import { useState } from "react";
import TemperatureInput from "./TemperatureInput";

function BoilingVerdict(props) {
  if (props.celsius >= 100) {
    return <p>물이 끓습니다.</p>;
  }
  return <p>물이 끓지 않습니다.</p>;
}

function toCelsius(fahrenheit) {
  return ((fahrenheit - 32) * 5) / 9;
}

function toFahrenheit(celsius) {
  return (celsius * 9) / 5 + 32;
}

function tryConvert(temperature, convert) {
  const input = parseFloat(temperature);
  if (Number.isNaN(input)) {
    return "";
  }
  const output = convert(input);
  const rounded = Math.round(output * 1000) / 1000;
  return rounded.toString();
}

export default function Calculator() {
  const [temperature, setTemperature] = useState("");
  const [scale, setScale] = useState("c");

  const handleCelsiusChange = (temperature) => {
    setTemperature(temperature);
    setScale("c");
  };

  const handleFahrenheitChange = (temperature) => {
    setTemperature(temperature);
    setScale("f");
  };

  const celsius =
    scale === "f" ? tryConvert(temperature, toCelsius) : temperature;
  const fahrenheit =
    scale === "c" ? tryConvert(temperature, toFahrenheit) : temperature;

  return (
    <div>
      <TemperatureInput
        scale="c"
        temperature={celsius}
        onTemperatureChange={handleCelsiusChange}
      />
      <TemperatureInput
        scale="f"
        temperature={fahrenheit}
        onTemperatureChange={handleFahrenheitChange}
      />
      <BoilingVerdict celsius={parseFloat(celsius)} />
    </div>
  );
}
```

### 합성에 대해 알아보기

- 합성(Composition)은 여러 개의 컴포넌트를 합쳐서 새로운 컴포넌트를 만드는 것이다.

- 조합 방법에 따라 합성의 사용 기법은 다음과 같이 나눈 수 있습니다.

  #### [1]. Containment(담다. 포함하다. 격리하다.)

  - 특정 컴포넌트가 하위 컴포넌트를 포함하는 형태의 합성방법이다.

  - 컴포넌트에 따라서는 어떤 자식 엘리먼트가 들어올 지 미리 예상할 수 없는 경우가 있다.

  - 범용적인 박스 역할을 하는 Sidebar 혹은 Dialog와 같은 컴포넌트에 특히 자주 볼 수 있습니다.

  - 이런 컴포넌트에서는 children prop을 사용하여 자식 엘리먼트를 출력에 그대로 전달하는 것이 좋다.

  - 다음과 같이 props.children을 사용하면 해당 컴포넌트의 하위 컴포넌트가 모두 children으로 들어오게 된다.

    ```jsx
    export default function FancyBorder(props) {
      return (
        <div className={`FancyBorder` + props.color}>{props.children}</div>
      );
    }
    ```

  - 만일 여러 개의 children 집합이 필요할 경우는 별도로 props를 정의해서 각각 원하는 컴포넌트를 넣어준다.

  #### [2]. Specialization (특수화, 전문화)

  - 웰컴다이얼로그는 다이얼로그의 특별한 케이스입니다.

  - 범용적인 개념을 구별이 되게 구체화하는 것을 특수화라고 합니다.

  - 객체지향 언어에서는 상속을 사용하여 특수화를 구현합니다.

  - 리액트에서는 합성을 사용하여 특수화를 구현합니다.

  ```jsx
  function Dialog(props) {
    return (
      <FancyBorder color="blue">
        <h1 className="Dialog-title">{props.title}</h1>
        <p className="Dialog-message">{props.message}</p>
      </FancyBorder>
    );
  }
  ```

  ### React.createElement()에 관하여

  - 내용추가

## 5월 29일 강의

### ~ 22일 강의의 연장선

1. select 태그

   ```jsx
   <select>
     <option value="apple">사과</option>
     <option value="pear">배</option>
     <option value="banana">바나나</option>
   </select>
   ```

2. File input 태그

   - File input 태그는 그 값이 읽기 전용이기 때문에 리액트에서는 비제어 컴포넌트가 된다.  
     `<input type="file" />`

3. 여러 개의 입력 다루기

   ```jsx
   import { useState } from "react";

   export default function SignUp() {
     const [name, setName] = useState();
     const [gender, setGender] = useState("남자");

     const handleChangeName = (e) => {
       setName(e.target.value);
     };

     const handleChangeGender = (e) => {
       setGender(e.target.value);
     };

     const handleSubmit = (e) => {
       alert(`이름: ${name} / ${gender}`);
       e.preventDefault();
     };

     return (
       <form onSubmit={handleSubmit}>
         <label>
           이름 :{" "}
           <input
             type="text"
             value={name}
             onChange={handleChangeName}
             placeholder="이름을 입력해 주세요."
           />
         </label>
         <label>
           성별 :
           <select value={gender} onChange={handleChangeGender}>
             <option value="남자">남</option>
             <option value="여자">여</option>
           </select>
         </label>
         <button type="submit">제출</button>
       </form>
     );
   }
   ```

4. input null value

   - 제어 컴포넌트에 value prop을 정해진 값으로 넣으면 코드를 수정하지 않는 한 입력값을 바꿀 수 없습니다.

   - 만약 value prop은 넣되 자유롭게 입력할 수 있게 만들고 싶다면 값이 undefined 또는 null을 넣으면 된다.

## 5월 22일 강의

### 폼이란 무엇인가?

1. 제어 컴포넌트

   - 제어 컴포넌트는 사용자의 입력을 기반으로 자신의 state를 관리하고 업데이트한다.

   - React에서는 변경할 수 있는 state가 일반적으로 컴포넌트의 state 속성에 유지되며 setState()에 의해 업데이트됩니다.

   - 예를 들어, `<input>` 요소의 값을 상태(state)로 관리하고, `onChange` 이벤트 핸들러를 통해 상태(state)를 업데이트하여 사용자 입력에 따라 UI가 동적으로 변화하는 것이 제어 컴포넌트의 특징이다.

2. 제어 컴포넌트 만들기

   ```jsx
   import { useState } from "react";

   export default function NameForm() {
     const [value, setValue] = useState("");
     const handleChange = (e) => {
       setValue(e.target.value);
     };

     const handleSubmit = (e) => {
       alert("입력한 이름: " + value);
       e.preventDefault();
     };

     return (
       <form onSubmit={handleSubmit} action="">
         <label>
           이름 :
           <input type="text" value={value} onChange={handleChange} />
           <button type="submit">클릭</button>
         </label>
       </form>
     );
   }
   ```

### 리스트와 키

1. 리스트와 키란 무엇인다?

   - 리스트는 Js의 변수나 객체를 하나의 변수로 묶어 놓은 배열 같은 것

   - 키는 각 객체나 아이템을 구분할 수 있는 고유한 값을 의미

   - 리액트에서는 배열과 키를 사용하여 반복되는 엘리먼트를 쉽게 렌더링 가능

2. 여러개의 컴포넌트 렌더링하기

   - 엘리먼트 모음을 만들고 중괄호 {}를 이용하여 JSX에 포함할 수 있다.

   - 아래의 JavaScript map() 함수를 사용하여 numbers 배열을 반복 실행하였다.

   - 각 항목에 대해 \<li> 엘리먼트를 반환하고 엘리먼트 배열의 결과를 listItems에 저장하였다.

   ```jsx
   export default function NumberList() {
     const numbers = [1, 2, 3, 4, 5];
     const listItems = numbers.map((num) => <li>{num}</li>);

     return <ol>{listItems}</ol>;
   }
   ```

3. 기본 리스트 컴포넌트

   - 일반적으로 컴포넌트 안에서 리스트를 렌더링합니다.

   - 이전 예시를 numbers 배열을 받아서 순서 없는 엘리먼트 리스트를 출력하는 컴포넌트로 리팩토링할 수 있습니다.

   ```jsx
   export default function NumberList() {
     const numbers = [1, 2, 3, 4, 5];
     const listItems = numbers.map((number) => <li>{number}</li>);

     return <ul>{listItems}</ul>;
   }
   ```

4.. 리스트의 키에 대해 알아보기

- 리스트에서는 키는 "리스트에서 아이템을 구별하기 위한 고유한 문자열"

- 이 키는 리스트에서 어떤 아이템이 변경, 추가 또는 제거되었는지 구분하기 위해 사용

- 키는 같은 리스트에 있는 엘리먼트 사이에서만 고유한 값이면 된다.

5. 출석부 출력

   ```jsx
   export default function NumberList() {
     const numbers = [1, 2, 3, 4, 5];
     const todos = [
       { id: 1, name: "홍길동1" },
       { id: 2, name: "홍길동2" },
       { id: 3, name: "홍길동3" },
       { id: 4, name: "홍길동4" },
       { id: 5, name: "홍길동5" },
     ];

     const listItems = numbers.map((num) => <li key={num}>{num}</li>);
     const todoItems = todos.map((todo) => <li key={todo.id}>{todo.name}</li>);

     const indexItems = todos.map((todo, index) => (
       <li key={index}>{todo.name}</li>
     ));
     return (
       <>
         <ul>{listItems}</ul>
         <ul>{todoItems}</ul>
       </>
     );
   }
   ```

## 5월 8일 강의

### Arguments

- 함수를 정의할 때는 파라미터() 혹은 매개변수, 함수를 사용할 때는 아귀먼트() 혹은 인수라고 부른다.

- 이벤트 핸들러에 매개변수를 전달해야 하는 경우도 많음.

  ```jsx
  <button onClick={(e) => this.deleteItem(id, e)}>삭제하기</button>
  ```

- (실습) 클릭 이벤트 처리하기

  ```jsx
  import { useState } from "react";

  export default function Toggle() {
    const [isToggleOn, setIsToggleOn] = useState(false);

    const handClick = () => {
      setIsToggleOn((isToggleOn) => !isToggleOn);
    };

    return (
      <>
        <p>결과 : {isToggleOn ? "켜짐" : "꺼짐"}</p>
        <button onClick={handClick}>버튼</button>
      </>
    );
  }
  ```

### 조건부 렌더링이란?

- 컴포넌트는 서로 다른 조건에 따라 다른 것을 보여줘야 하는 경우가 자주 발생한다.

- React에서는 if 문, &&, ? : 연산자 같은 JavaScript 문법을 사용해 조건부로 JSX를 렌더링할 수 있음.

- 아래는 상품의 포장 여부를 표시하는 여러 개의 Item을 렌더링하는 PackingList 컴포넌트

```jsx
function Item({ name, isPacked }) {
  return <li className="item">{name}</li>;
}

export default function PackingList() {
  return (
    <section>
      <h1>Sally Ride's Packing List</h1>
      <ul>
        <Item isPacked={true} name="Space suit" />
        <Item isPacked={true} name="Helmet with a golden leaf" />
        <Item isPacked={false} name="Photo of Tam" />
      </ul>
    </section>
  );
}
```

- 일부 Item 컴포넌트의 isPacked prop이 false가 아닌 true로 설정되어 있다.
- isPacked={true}인 경우, 패킹된 아이템에 체크 표시(✔)를 추가해보았다.

```jsx
function Item({ name, isPacked }) {
  if (isPacked) {
    return <li className="item">{name} ✔</li>;
  }
  return <li className="item">{name}</li>;
}
```

### 엘리먼트 변수

- 렌더링해야 될 컴포넌트를 변수처럼 사용하는 방법이 엘리먼트 변수이다.

  ```jsx
  // 엘리먼트 변수
  let button;
  if (isLoggedIn) {
    button = <LogoutButton onClick={handleLogoutClick} />;
  } else {
    button = <LoginButton onClick={handleLoginClick} />;
  }

  return (
    <>
      <Greeting isLoggedIn={isLoggedIn} />
      {button} {/* 엘리먼트 변수 호출 */}
    </>
  );
  ```

### 인라인 조건

- 필요한 곳에 조건문을 직접 넣어 사용하는 방법이다.

1. 인라인 if

   - if문을 직접 사용하지 않고, 동일한 효과를 내기 위해 &&논리 연산자를 사용한다.

   - &&는 and연산자로 모든 조건이 참일때만 참이 된다.

   - 첫번째 조건이 거짓이면 두번째 조건은 판단할 필요없음. (단락평가, 단축평가)

     ```jsx
     {
       count && <h1>현재 카운트 : {count}</h1>;
     }
     ```

2. 인라인 if-else

   - 삼항 연산자를 사용함.

   - 문자열이나 엘리먼트를 넣어서 사용할 수도 있음.

### 컴포넌트 렌더링 막기

- 컴포넌트 렌더링하고 싶지 않은 때에는 null을 리턴합니다.

  ```jsx
  function WarningBanner(props) {
    if (!props.warning) {
      return null;
    }

    return;
  }
  ```

###

## 5월 1일 강의

### Hook의 규칙

- [훅의 두가지 규칙]

  - 무조건 최상위 레벨에서만 호출해야 해야함.
  - 따라서 반복문이나 조건문 또는 중첩된 함수들 안에서 Hook을 호출하면 안됨.
  - 이 규칙에 따라서 훅은 컴포넌트가 렌더링 될 때마다 같은 순서로 호출되어야 함

  ```jsx
  // 잘못된 코드 예시
  function MyComponent(props) {
      const [name, setName] = useState('Hanseo');

      if (name !== '') {
          useEffect(() => {
              ...
          });
      }
      ...
  }
  ```

  - 함수형 컴포넌트에서만 Hook을 호출해야함.
  - 따라서 일반 자바스크립트 함수에서 Hook을 호출하면 안됨.
  - Hook은 함수형 컴포넌트 또는 직접 만든 커스텀 Hook에서만 호출할 수 있다.

### 나만의 Hook 만들기

- 필요하다면 직접 Hook을 만들어 쓸 수도 있다. 이것을 커스텀 Hook이라고 한다.

```jsx
import { useEffect, useState } from "react";

export default function UseStatus(props) {
  const [isOnline, setIsOnline] = useState(null);
  useEffect(() => {
    function handleStatusChange(status) {
      setIsOnline(status.isOnline);
    }
    ServerAPI.subscribeUserStatus(props.user.id, handleStatusChange);
    return () => {
      ServerAPI.subscribeUserStatus(props.user.id, handleStatusChange);
    };
  });
  if (isOnline === null) {
    return "대기중...";
  }
  return isOnline ? "온라인" : "오프라인";
}
```

### 훅을 사용한 컴포넌트 개발

1. useCounter() 훅 만들기

   ```jsx
   import { useState } from "react";

   export default function useCounter(initialValue) {
     const [count, setCount] = useState(initialValue);

     const increaseCount = () => setCount((count) => count + 1);
     const decreaseCount = () => setCount((count) => Math.max(count - 1, 0));

     return [count, increaseCount, decreaseCount];
   }
   ```

2. Accommodate 함수 만들기

   ```jsx
   import React, { useEffect, useState } from "react";
   import useCounter from "./useCounter";

   const MAX_CAPACITY = 10;

   export default function Accommodate(props) {
     const [isFull, setIsFull] = useState(false);
     const [count, increaseCount, decreaseCount] = useCounter(0);

     useEffect(() => {
       console.log("=========");
       console.log("useEffect() is called.");
       console.log(`isFull: ${isFull}`);
     });

     useEffect(() => {
       setIsFull(count >= MAX_CAPACITY);
       console.log(`Current count value: ${count}`);
     }, [count]);

     return (
       <div>
         <p>{`총 ${count} 수용했습니다.`}</p>
         <button onClick={increaseCount} disabled={isFull}>
           입장
         </button>
         <button onClick={decreaseCount}>퇴장</button>

         {isFull && <p style={{ color: "red" }}>정원이 가득 찼습니다.</p>}
       </div>
     );
   }
   ```

### 이벤트 처리하기

- DOM에서 클릭 이벤트를 처리하는 예제코드
- React에서 클릭 이벤트를 처리하는 예제코드

- 둘의 차이점은

  - 이벤트 이름이 onclick에서 onClick을 변경(Camel case)
  - 전달하려는 함수는 문자열에서 함수 그대로 전달

- 이벤트가 발생했을 때 해장 이벤트를 처리하는 함수를 '이벤트 핸들러'라고 함 또는 이벤트가 발생하는 것을 계속 듣고 있다는 의미로 '이벤트 리스너'라고도 함

## 4월 17일 강의

### Hook이란 무엇인가?

- 클래스형 컴포넌트에서 이용하던 코드를 작성할 필요없이 함수형 컴포넌트에서 다양한 기능을 사용할 수 있게 만들어준 라이브러리 [React 16.8 버전에 추가됨]

- 함수형 컴포넌트에 맞게 만들어진 것으로 함수형 컴포넌트에서만 사용 가능하다.

  - Hook은 일반적인 js 함수에서는 호출하면 안된다.

  - 같은 훅을 여러번 호출 가능하다.

  - custom hook에서는 호출 가능

- 최상위에서만 Hook을 호출해야한다.

  - 반복문, 조건문 혹은 중첩된 함수 내에서 호출하면 안된다.

- 블록 스코프 안에서는 사용 불가능

- 비동기 함수(async 키워드가 붙은 함수)는 콜백함수로 사용할 수 없다

- 훅의 이름은 모두 use로 시작해야함

### useState

- useState는 함수형 컴포넌트에서 state를 사용하기 위한 Hook이다.

- 현재 상태를 나타내는 state값과 이 상태를 변경하는 setState값을 한 쌍으로 제공한다.

- state는 초기값을 설정할 수 있으며, 초기값은 첫 렌더링 때 한번 사용된다.

- useState로 선언된 변수는 상태(state)가 변할 때 마다 페이지를 리렌더링을 한다.

- 이때 함수는 비동기로 처리 되는데, 이는 함수가 호출 될 때 마다 화면을 다시 렌더링 하기 때문에 성능이슈가 발생 할 수 있기 때문이다.

- state는 객체일 필요 없이 문자열, 숫자, boolean, 배열, null, 객체 등의 여러가지 다양한 값을 넣을 수 있다.

  ```jsx
  import React, { useState } from "react";

  function Example() {
    // "count"라는 새 상태 변수를 선언합니다
    const [count, setCount] = useState(0);

    return (
      <div>
        <p>You clicked {count} times</p>
        <button onClick={() => setCount(count + 1)}>Click me</button>
      </div>
    );
  }
  ```

### useEffect

- useState와 함께 가장 많이 사용하는 Hook이다.

- 클래스 컴포넌트의 생명주기 함수와 같은 기능을 하나로 통합한 기능을 제공

  - componentDidMount
  - componentDidUpdate
  - componentWillUnmount

- Effect Hook을 사용하면 함수 컴포넌트에서 side effect를 수행할 수 있다.
- useEffect는 기본적으로 useEffect(function, deps)의 형태로 사용한다.

- sideEffect는 렌더링 외에 실핼해야 하는 부수적인 코드를 말한다.

- function에는 실행시킬 함수를 넣고, deps에는 의존성 배열을 담는다.

- 의존성 배열에 어떤 것이 담기느냐에 따라 부수적인 효과 함수가 실행된다.

- 의존성 배열 없이 useEffect를 실행시키면 페이지가 렌더링 될때마다 데이터를 불러온다.

- effect를 실행하고 정리(clean-up)하는 과정을 (마운트와 마운트 해제 시에)딱 한 번씩만 실행하려면, 빈 배열을 두 번째 인수로 넘기면 된다.

  ```jsx
  import React, { useState, useEffect } from "react";

  function Example() {
    const [count, setCount] = useState(0);

    // componentDidMount, componentDidUpdate와 같은 방식으로
    useEffect(() => {
      // 브라우저 API를 이용하여 문서 타이틀을 업데이트합니다.
      document.title = `You clicked ${count} times`;
    });

    return (
      <div>
        <p>You clicked {count} times</p>
        <button onClick={() => setCount(count + 1)}>Click me</button>
      </div>
    );
  }
  ```

### useMemo

- useMemo() 훅은 memoized value를 리턴하는 훅이다.

- useMemo는 의존성이 변경되었을 때에만 메모이제이션된 값만 다시 계산한다.

- 이전 계산값을 갖고 있기 때문에 연산량이 많은 작업의 반복을 피할 수 있다.

- useMemo로 전달된 함수는 렌더링 중에 실행된다.

- 따라서 렌더링이 일어나는 동안 실행되서는 안될 작업을 넣으면 안된다.

- 배열이 없는 경우 매 렌더링 때마다 새 값을 계산하게 될 것이다.

  ```jsx
  import { useMemo } from "react";

  // useMemo(calculateValue, dependencies) 형태

  function TodoList({ todos, tab, theme }) {
    const visibleTodos = useMemo(() => filterTodos(todos, tab), [todos, tab]);
    // ...
  }
  ```

> ※ 메모이제이션(memoization): 컴퓨터 프로그램이 동일한 계산을 반복해야 할 때, 이전에 계산한 값을 메모리에 저장함으로써 동일한 계산의 반복 수행을 제거하여 프로그램 실행 속도를 빠르게 하는 기술이다.

### useCallback

- useCallback() 훅은 useMemo()와 유사한 역할을 한다.

- 차이점은 useMemo() 훅은 memoized value 반환하고, useCallback()은 memoized function을 반환한다.

- 의존성 값의 배열이 콜백에 인자로 전달되지는 않는다.

- 그러나 개념적으로는, 이 기법은 콜백 함수가 무엇일지를 표현하는 방법이기 때문에 콜백 안에서 참조되는 모든 값은 의존성 값의 배열에 나타나야 한다.

- useCallback(fn, deps)은 useMemo(() => fn, deps)와 같습니다.

  ```jsx
  import { useCallback } from 'react';

  export default function ProductPage({ productId, referrer, theme }) {
  	const handleSubmit = useCallback((orderDetails) => {
  		post('/product/' + productId + '/buy', {
    			referrer,
    			orderDetails,
  		});
  		}, [productId, referrer]);
  // ...
  ```

### useRef

- useRef() 훅은 레퍼런스를 사용하기 위한 훅이다.

- 특정 DOM에 접근하여 DOM 조작을 가능하게 하는 훅이다.

- useRef는 .current 프로퍼티로 전달된 인자로 초기화된 변경 가능한 ref 객체를 반환, 반환된 객체는 컴포넌트의 전 생애주기를 통해 유지된다.

- useRef()는 순수 자바스크립트 객체를 생성하는데, useRef()와 {current: ...} 객체 자체를 생성하는 것의 유일한 차이점이라면 useRef는 매번 렌더링을 할 때 동일한 ref 객체를 제공한다.

- useRef는 내용이 변경될 때 변경점을 알려주지 않는 점을 주의해야함.

  ```jsx
  function TextInputWithFocusButton() {
    const inputEl = useRef(null);
    const onButtonClick = () => {
      // `current` points to the mounted text input element
      inputEl.current.focus();
    };
    return (
      <>
        <input ref={inputEl} type="text" />
        <button onClick={onButtonClick}>Focus the input</button>
      </>
    );
  }
  ```

## 4월 3일 강의

### Props

1. Props의 개념

   - props는 prop(property:속성, 특성)의 준말이다.

   - props가 컴포넌트의 속성

   - 컴포넌트에 어떤 속성, props를 넣느냐에 따라서 속성이 다른 엘리먼트가 출력
   - props는 컴포넌트에 전달 할 다양한 정보를 담고 있는 JS 객체이다

2. Props의 특징

   - 읽기 전용

   - 속성이 다른 엘리먼트를 생성하려면 새로운 props를 컴포넌트에 전달하면 된다.

   #### Pure 함수 VS Impure 함수

   - Pure함수는 인수로 받은 정보가 함수 내부에서 <u>변하지 않는 함수</u>.

   - Impure함수는 인수로 받은 정보가 함수 내부에서 <u>변하는 함수</u>.
     ```jsx
     // Pure 함수
     function sum(a, b) {
       return a + b;
     }
     // Impure 함수
     function withraw(account, amount) {
       account.total -= amount;
     }
     ```

3. Props 사용법

   - jsx에서는 key-value쌍으로 props를 구성

     ```jsx
     function App(props) {
       return (
         <Profile
           name="한서"
           introduction="안녕하세요, 한서입니다."
           viewCount={1500}
         />
       );
     }
     ```

   위 코드는

   - Profile 컴포넌트로 name, introduction, viewCount를 전달한다.
   - 이때 전달되는 props 는 다음과 같은 자바스크립트 객체이다.
   - JSX에서는 중괄호를 사용하면 JS코드를 넣을 수 있다.
   - 다음 코드처럼 props를 통해서 value를 할당할 수도 있고, 직접 중괄호를 사용하여 할당할 수도 있다.

     ```jsx
     function App(props) {
       return (
         <Layout
           width={2500}
           height={1440}
           header={<Header title="한서의 학습자료입니다." />}
           footer={<Footer />}
         />
       );
     }
     ```

   - JSX를 사용하지 않는 경우 props의 전달 방법은 createElement() 함수를 사용하는 것이다.
   - createElement() 함수의 두번째 매개변수가 props이다.

### 컴포넌트 만들기

1. 컴포넌트의 종류

   - 리액트 초기 버전을 사용할 때는 클래스형 컴포넌트를 주로 사용했다.

   - 이후 Hook이라는 개념이 나오면서 최근에는 함수형 컴포넌트를 주로 사용

   - 예전에 작성된 코드나 문서들이 클래스형 컴포넌트를 사용하고 있기 때문

   - 클래스형 컴포넌트와 컴포넌트의 생명주에 관해서도 공부해두자.

   ![컴포넌트 종류](https://velog.velcdn.com/images/sjmh0507/post/1491b6fb-0cff-4c03-81ee-1928df942ff3/image.png)

2. 함수형 컴포넌트

   - 모든 리액트 컴포넌트는 퓨어함수같은 역할을 해야한다. 리액트의 컴포넌트를 일종의 함수처럼 생각해도 된다.

   ```jsx
   function Welcome(props) {
     return <h1>안녕, {props.name}</h1>;
   }
   ```

3. 클래스형 컴포넌트

   - 클래스 컴포넌트의 class는 ES6의 그 class이다. 함수 컴포넌트보다 몇 가지 더 추가 기능을 가지고 있다.

   ```jsx
   class Welcome extends React.Component {
       return <h1>안녕, {this.props.name}</h1>;
   }
   ```

   - 위 코드는 함수형 컴포넌트의 클래스 컴포넌트 버전이다.

   - 리액트의 모든 클래스 컴포넌트는 React.Component를 상속받아서 만든다.

   - '상속'이라는 개념은 객체지향 프로그래밍에서 나오는 개념인데, 한 클래스의 변수들과 함수들을 상속받아 새로운 자식 클래스를 만드는 방법이다.

   > 컴포넌트 이름을 소문자로 하면 돔 태그로 인식(내장 컴포넌트)하기 때문에 대문자로 시작해서 리액트 컴포넌트로 인식하도록 해야한다.

4. 컴포넌트 명명 규칙

   - 이름은 항상 대문자로 시작

   - 리액트는 소문지로 시작하는 컴포넌트를 DOM 태그로 인식하기 때문이다.

   - ※ 컴포넌트 파일 이름과 컴포넌트 이름은 같게 한다.

5. 컴포넌트의 렌더링

   ```jsx
   function Welcome(props) {
     return <h1>안녕, {props.name}</h1>;
   }
   const element = <Welcome name="한서" />;
   ReactDOM.render(element, document.getElementById("root"));
   ```

6. 컴포넌트 합성

   - 합성 컴포넌트란 소프트웨어 개발에서 재사용이 가능한 구성 요소를 만들기 위해 여러 개의 다른 컴포넌트를 조합하는 디자인 패턴이다.

   - 복합적인 기능을 가진 큰 컴포넌트를 작은 단위의 컴포넌트들로 구성함으로써 코드의 유지보수성과 확장성을 높일 수 있다.

   - 합성 컴포넌트 패턴에서는 컴포넌트들이 계층 구조로 구성된다.

   - 각 컴포넌트는 하위 컴포넌트들을 가지며, 최상위 컴포넌트는 하위 컴포넌트들의 조합으로 이루어진다.

   - 이로 인해 단일 컴포넌트를 사용하는 것보다 더 복잡하고 다양한 기능을 제공할 수 있다.

     ```jsx
     function Welcome(props) {
       return <h1>Hello, {props.name}</h1>;
     }
     function App(props) {
       return (
         <div>
           <Welcome name="Mike" />
           <Welcome name="Steve" />
           <Welcome name="Jane" />
         </div>
       );
     }
     ReactDOM.render(<App />, document.getElementById("root"));
     ```

   위 코드는 props 의 값을 다르게 해서 Welcome Component 를 여러번 사용한다.  
   -> App 이라는 Component 는 Welcome 이라는 Component 를 3개 포함하고 있는 Component 다.

7. 컴포넌트 추출

   - Component 추출을 사용하게 되면 Component 의 재사용성이 올라간다.

   - Component 가 작아질 수록 기능이 명확해지고, prop 도 단순해 지기 때문에, 다른 곳에서 사용하기 좋아진다.

   - 재사용성이 높아지면서 개발 속도도 올라간다.

   - 아래 코드는 댓글을 표현하기 위한 Component 이다.

     ```jsx
     function Comment(props) {
       return (
         <div className="comment">
           <div className="user-info">
             <img
               className="avatar"
               src={props.author.avatarUrl}
               alt={props.author.name}
             />
             <div className="user-info-name">{props.author.name}</div>
           </div>

           <div className="comment-text">{props.text}</div>

           <div className="comment-date">{formatDate(props.date)}</div>
         </div>
       );
     }
     ```

   - Avatar 추출하기

     ```jsx
     function Avatar(props) {
       return (
         <img
           className="avatar"
           src={props.user.avatarUrl}
           alt={props.user.name}
         />
       );
     }
     ```

     - 위와 같이 Avatar 을 추출해 준 뒤, Comment Component 에 img 태그 대신

     ```jsx
     <Avatar user={props.author} />
     ```

     위 코드를 넣어주면 된다.

   - UseInfo 추출하기

     ```jsx
     function UserInfo(props) {
       return (
         <div className="user-info">
           <Avatar user={props.user} />
           <div className="user-info-name">{props.user.name}</div>
         </div>
       );
     }
     ```

     ```jsx
     <UserInfo user={props.author} />
     ```

   - 사용자정보를 class 로 가진 div 대신에 위 코드를 넣어주면 된다.
   - 결과

     ```jsx
     function Comment(props) {
       return (
         <div className="comment">
           <UserInfo user={props.author} />
           <div className="comment-text">{props.text}</div>
           <div className="comment-date">{formatDate(props.date)}</div>
         </div>
       );
     }
     ```

### state

1. state란?

   - state는 리액트 컴포넌트의 상태를 의미

   - 상태의 의미는 정상인지 비정상인지가 아니라 컴포넌트의 데이터를 의미

   - 컴포넌트의 변경 가능한 데이터를 의미

   - state가 변하면 다시 렌더링이 되기 때문에 렌더링과 관련된 값만 state에 포함시켜야 함

2. state의 특징

   - 리액트만의 특별한 형태가 아닌 단지 JS객체일 뿐이다.

   - state는 변경은 가능하다고 했지만 직접 수정해서는 안됨

   - 불가능 하다고 생각하는 것이 좋다

   - state를 변경하고자 할 때는 setState() 함수를 사용함.

### 컴포넌트vs인스턴스vs엘리먼트

- element는 화면에 나타낼 DOM tree에 대한 정보를 가지고 있는 순수 객체

- Component는 props를 input으로 받아 DOM Node를 출력하는, 리액트로 만들어진 앱을 이루는 최소한의 단위

- instance 클래스로 선언된 Component에서만 갖는 것.

### 생명주기(Lifecycle)에 대해 알아보기

- 생명주기는 컴포넌트의 생성 시점, 사용 시점, 종료 시점을 나타냄

- constructor가 실행되면서 컴포넌트가 생성된다.

- 생성 직후 compomentDidMount() 함수가 호출

- 컴포넌트가 소멸하기 전까지 여러 번 랜더링 한다.

- 렌더링은 props, setState(), forceUpdate()에 의해 상태가 변경되면 이루어짐

- 렌더링이 끝나면 compomentDidUpdate()가 호출

- 마지막으로 컴포넌트가 언마운트 되면 compomentWillUnmount()함수 가 호출됨

![마운팅,업데이팅,언마운팅1.jpg](https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=https%3A%2F%2Fblog.kakaocdn.net%2Fdn%2FzNVQp%2FbtsDfPeNMg9%2FhkXlv1oQnXVHlDZnkJ47TK%2Fimg.png)
![마운팅,업데이팅,언마운팅2.jpg](https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=https%3A%2F%2Fblog.kakaocdn.net%2Fdn%2FAgYkW%2FbtsDLKxfeHN%2FacLRPKVYV36YLWeXCPTvZ1%2Fimg.png)

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

  |                      | DOM               | Virtual DOM                                                                                         |
  | -------------------- | ----------------- | --------------------------------------------------------------------------------------------------- |
  | 업데이트             | 느리다            | 빠르다                                                                                              |
  | element업테이트 방식 | DOM 전체 업데이트 | 해당 엘리먼트와 그 자식 엘리먼트를 이전의 엘리먼트와 비교하여 필요한 경우에만 DOM을 업데이트합니다. |
  | 메모리               | 낭비가 심함       | 효율적                                                                                              |

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
  <div id="root"></div>;
  ReactDOM.render(element, document.getElementById("root"));
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
    ReactDOM.render(element, document.getElementById("root"));
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

- Pure 함수 VS Impure 함수 - Pure함수는 인수로 받은 정보가 함수 내부에서 <u>변하지 않는 함수</u>. - Impure함수는 인수로 받은 정보가 함수 내부에서 <u>변하는 함수</u>.
  `jsx
// Pure 함수
function sum(a, b) {
    return a + b
}
// Impure 함수
function withraw(account, amount) {
    account.total -= amount
}
`
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
     return a + b;
   }
   console.log(sum(10, 20));
   ```
   - Arrow function expression 형 : 화살표 함수
   ```js
   const sum = (a, b) => {
     return a + b;
   };
   console.log(sum(10, 20));
   ```

### Node.js

다운로드 https://nodejs.org/en

LTS = 안정적  
Current = 가장 최신
<br>

## 3월 6일 강의

### 내용

> 아이폰 출시 이후 모바일 트래픽이 데스크톱 트래픽을 추월함  
> semantic versioning 이란 [유의적 버전]
> 버전을 주. 부. 수 숫자로 하고
> 기존 버전과 호환되지 않게 API가 바뀌면 '주(主) 버전'을 올림
> 기존 버전과 호환되면서 새로운 기능을 추가할 때는 `부(部)버전` 올림
> 기존 버전과 호환되면서 버그를 수정한 것이라면 `수(修)버전` 올림

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

_이텔릭체_  
**굵게**  
**_이텔릭+굵게_**

`js ` <- 코드작성

개행은  
스페이스 두개
[구글 링크](https://www.google.com)  
[페이지 내 링크](#리스트)  
![리트리버 인절미](puppy-1189067_1280.jpg)
```
