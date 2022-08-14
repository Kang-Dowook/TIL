# Redux Toolkit

>- 리덕스를 사용하기 위해 작성했던 ducks 패턴의 요소들이 전체적인 코드의 양을 늘리게 되어<br/>
이를 보안하기 위해 ducks 패턴의 요소들이 어느정도 자동화 되도록 만들기 위한 것.
- toolkit 패키지 설치 : $ yarn add react-redux @reduxjs/toolkit
- 리덕스와 큰 차이는 Action Value와 Action Creator를 직접 생성하지 않고 Action Value, Action Creator, Reducer가 하나로 합쳐진점.
- createSlice라는 API를 통해 슬라이스를 만들고 그 인자로 설정정를 '객체'로 받는다. 객체의 값으로는 이 모듈의' name: '', initialState: {}, reducers: {} '가 있다.

