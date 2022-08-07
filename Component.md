# REACT Component!
<hr/>

## INDEX
- Component


## 1. Component
> - Component란? 컴포넌트는 화면을 구성하는 하나의 단위이며, 함수.
```
// App 컴포넌트

function App() {
  return <div></div>
}
```
> - 리액트의 컴포넌트는 html을 return하는 함수이다.
> - 컴포넌트를 만들때 반드시 가장 첫 글자는 <b>대문자</b>로 만들어야 한다.
> - 폴더는 소문자로 시작하는 카멜케이스로 작성하고, 컴포넌트를 만드는 파일은 대문자로 시작하는 카펠케이스로 이름을 짓는다.

::: 클래스 컴포넌트와 함수 컴포넌트란? :::

## 2. 부모-자식관계 Component
>- 컴포넌트는 다른 컴포넌트를 품을 수 있다.
>- 다른 컴포넌트를 품은 컴포넌트를 부모 컴포넌트. 품어지는 컴포넌트를 자식 컴포넌트.
>- 부모 컴포넌트는 export default를 통해 화면에 보여지게 된다.
>- 화면에 보여지게하는 과정을 Rendering이라고 한다.
>- 부모 컴포넌트는 자식 컴포넌트를 HTML 태그처럼 사용할 수 있고 이런 방식을 JSX라고 부른다.

## 3. JSX
>- 리액트에서는 하나의 html 파일만 존재한다(public 폴더의 index.html).
>- 리액트는 JSX문법을 사용해서 React요소를 만들고 DOM에 렌더링 시켜서 꾸민다.

<b>JSX 문법 규칙</b>

- 컴포넌트에서 반환 할 수 있는 엘리먼트는 1개.
- JSX에서 Javascript값을 가져오려면 중괄호{}를 쓴다.
- map, 삼항연산자 등 자바스크립트 문법을 JSX안에 쓸 때도 {}를 이용.
- JSX 내에서 태그의 클래스명은 class대신 className을 사용한다.
- 인라인으로 style 주기
  - HTML
  ` <p style="color: orange; font-size: 20px;">orange</p> `
  - JSX
  ```
  // 중괄호를 두 번 쓰는 이유? 딕셔너리도 자바스크립트니까요!
  // 이렇게 쓰거나,
  <p style={{color: 'orange', fontSize: '20px'}}>orange</p>

  //혹은 스타일 딕셔너리를 변수로 만들고 쓸 수 있어요!
  function App() {
    const styles = {
      color: 'orange',
      fontSize: '20px'
    };

    return (
      <div className="App">
        <p style={styles}>orange</p>
      </div>
    );
  }
  ```

  ::: 리액트에서 렌더링이란? :::

## 4. Props
>- Props는 부모컴포넌트로 부터 받아온 데이터.
>- props는 부모 컴포넌트에서 자식 컴포넌트로만 props를 전달 할 수 있다.

  <p>props로 값 전달하기</p>
  
  ```
  function Child() {
    return <div>연결 성공</div>;
  }

  function Mother() {
    const name = '홍부인';
    return <Child motherName={name} />; // 'props로 name을 전달'
  }
  ```

컴포넌트(부모-자식)간의 정보를 교류할때 Props를 사용한다.
아래의 Mother컴포넌트가 가지고 있는 정보(값)를 Child에게 주고 싶을 때는 motherName이라는 이름으로 name값을 Child 컴포넌트에게 전달해준다.<br/>
🔥🔥<Child>태그 내에 motherName이라는 props로 {name}을 전달해준다는 문법 형태!!!🔥🔥
<br/>
Mother가 전달해준 motherName은 Child가 어떻게 받을 수 있을까?

```
function Child(props) {
  return <div> {props.motehrName} </div>
}
```

자식 컴포넌트에서 파라미터로 props의 값을 받아 사용할 수 있다.
props는 object literal 형태( {key: “value”} 데이터 형태 )이기 때문에 <br/>
{props.motherName}으로 꺼내서 사용가능. object literal의 key가 motherName인 이유는 <br/>
Child로 보내줄 때 motherName={name}으로 보내주었기 때문.

::: props Drilling이란? :::

## 5. Children

>- `<Component props={props}>`와 다른 방식의 전달 방법.
>- `props.children` 사용.

  ```
  // src/App.js
  import React from "react";

  function User() {
    return <div></div>;
  }

  function App() {
    return <User>안녕하세요</User>;
  }
  export default App;
  ```
  
  위의 코드에서 <Component props={props}> 방식이 아닌 자식 태그로 감싸서 정보를 전달하려고 한다.
  자식 컴포넌트에 {props.childen}을 사용해 정보 전다.
  
  ```
  import React from "react";

  function User(props) {
    return <div>{props.children}</div>;
  }

  function App() {
    return <User>안녕하세요</User>;
  }
  export default App;
  ```
::: 'children을 활용하여 컴포넌트 만딜기' 알아보기:::

## 6. props 구조분해 할당과 defaultProps
  (1) 구조분해 할당을 통해 prop 내부값 추출.

  ```
    function Todo(props){
      return <div>{props.todo}</div>
    }
  ```
  props는 object literal 형태의 데이터이기에 구조분해 할당을 이용해 코드를 줄일 수 있다.
  
  ```
    function Todo({ title, body, isDone, id }){
      return <div>{title}</div>
    }
  ```

  (2) defaultProps
  >- 부모컴포넌트에서 props를 보내주지 않아도 설정될 초기 값.
  >- 자식 컴포넌트가 부모컴포넌트로 부터 변수에 대한 props 정보를 받지 못하고 있는을때, props를 반기전까지 임시로 사용 할 수 있는 props를 설정해주는것.

  defaultProps 사용방법.
  ```
  // components/Child.js
  import React from 'react';

  function Child({ name }){
    return <div>내 이름은 {name} 입니다. </div>
  }

  // 이렇게 설정합니다.
  Child.defaultProps={
    name: '기본 이름'
  }

  export default Child
  ```

  ```
  import React from 'react';

  // 구조 분해 할당 문법을 사용하면 이렇게도 할 수 있어요.
  function Child({ name = '기본이름' }){
    return <div>내 이름은 {name} 입니다. </div>
  }

  export default Child
  ```

::: object literal이란? :::

::: default argument란? :::