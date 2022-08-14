# 1. State

  (1) State란
  >- State란 컴포넌트 내부에서 바뀔 수 있는 값을 의미한다.
  >- State를 만들 때는 `useState()`를 사용한다.
  >- `useState`는 함수 이고 리액트에서만 제공하는 기능이다.
  >- 이러한 것을 hook이라고 부른다.
------
  `useState` 훅을 사용하는 방법
  `const = [ value, setValue ] = useState( initial state )

  (2) State 변경하기
  > State를 변경할때는 setValue(바꾸고 싶은 값)를 사용한다.

  setName을 통해 바꾼 값은 어디에 저장되는 것이 아니고 단순히 화면에서만 바뀐 값으로 렌더링하는 작업.
  

  ::: 리액트 훅이란 무엇인가?[공식문서](https://ko.reactjs.org/docs/hooks-intro.html)::: <br/>
  ::: 다른 훅의 종류는? ::: <br/>
  ::: const는 상수인데 어떻게 setState를 이요해서 변경할 수 있나? :::

# 2. useState 응용하여 input과 button 다루기


### useState 정의

  useState는 <b>함수 컴포넌트에서 가변적인 상태를 가지게 해준다</b><br/>
  
  >- `const [ state, setState ] = useState(initialState);`
  
  state를 변수로 사용했고, setState를 이용해서 state값을 수정.<br/>
  만약 state가 원시 데이터타입이 아닌 객체 데이터 타입인 경우 불변성을 유지해줘야한다.

### (1) State + onClick Event
  
  ```
  function App() {
    const [ name, setName ] = useState('길동이');

    function onClickHandler() {
      setName('누렁이');
    }

    return (
      <div>
        {name}
        <button onClick={onClickHandler}> 버튼 </button>
      </div>
    );
  }
  ```
  >- `onClick`에 화살표 함수를 주는 방법에서 `onClickHandler`를 이용해서 버튼 기능 구현

### (2) useState + onChang Event
  >- input과 state 구현하기

  사용자가 입력한 input값을 state로 관리하는 패턴.

  >- 이벤트핸들러를 구현하고 state와 연결하기
  ```
  const App = () => {
    const [ value, setValue ] = useState('');

    const onChangeHandler = (e) => {
      const inputValue = e.target.value;
      setValue(inputValue);
    };

    return (
      <div>
        <input type='text' onChange={onChangeHandler} value={value} />
      </div>
    );
  };
  ```
  input과 생성한 state(value)를 연결. onChange에 이벤트 핸들러 함수를 넣어 준다. <br/>
  사용자가 입렵한 input값을 이벤트 핸들러 안에서 JS의 event 객체를 사용할 수 있도록  event.target.value로 설정.
  마지막으로 state인 value를 input의 attribute인 value에 넣어 주면 input과 state 연결.<br/>
  onChange(사용자가 input값을 입력)될 때마다 value라는 state에 setValue해서 값을 넣어준다.<br/>

# 3. 불변성
  >- 불변성이란 메모리에 있는 값을 변겅할 수 없는 의미.
  >- JS데이터 형태 중 원시 데이터는 불변성이고, 객체,배열,함수는 불변성이 없다.
  <br/>
  

  (1) 원시 데이터의 불변성

  원시 데이터의 경우 변수를 선언하였을때, 메모리에 변수의 값이 저장된다. 그리고 변수는 메모리에 있는 1을 참조한다. <br/>
  만약 `let number = 1`과 `let secondNumber = 1`이라는 변수를 같은 값으로 선언한다면 `number`와 `secondNumber`는 이름은 다르지만 같은 <b>메모리의 값</b>을 참조하게 된다.
  <br/>
  하지만 객체, 배열, 함수는 같은 값을 지정해주었을때, 메모리를 공유하지 않고 새롭게 저장 공간을 만든다.
  <br/>
  
  (2) 데이터 수정

  원시 데이터 number를 `number = 2`라고 새롭게 할당할 경우 기존 메모리에 저장되어 있는 1이라는 값이 변하지 않고, 새로운 메모리 저장공간에 2가 생긴다.
  ```
  number = 1 = secondNumber // number값 변경전 메모리 공유

  numer = 2 = secondNumber // 이런 형태가 아니라 1의 값은 불변성을 유지하므로

           1 = secondNumber // secondNumber는 1의 값을 유지하며
  number = 2                // 새로운 2라는 메모리 저장소가 만들어지고 number가 참조한다.
  ```
  원시데이터가 아닌 데이터의 경우 값을 수정하게되면, 불변성이 없기 때문에 기존 메모리 저장공간의 값이 변하게 된다.
  <br/>

  (3) 리액트에서 불변성의 중요성

  >- 리액트는 state의 변화를 통해 화면의 리렌더링을 결정한다. state가 변할경우 리렌더링된다.
  >- state의 변화를 `메모리 주소`통해 비교한다. 이때, 객체,배열,함수 등의 데이터에 직접적인 변화를 주면 `값`은 바뀌지만 `메모리 주소`는 변함이 없어 인지하지 못한다.

::: 원시 데이터 타입이란? ::: <br/>
::: 객체, 배열, 함수의 불변성을 지키면서 값을 수정할 수 있는 메서드들은 뭐가 있을까? :::