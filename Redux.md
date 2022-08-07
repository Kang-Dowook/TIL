# Redux
<hr/>

## 컨테이너 컴포넌트 만들기
> 컴포넌트에서 리덕스 스토어에 접근하여 원하는 상태를 받아 오고, 액션도 디스패치해줄 차례.
> 리덕스 스토어와 연동된 컴포넌트를 컨테이너 컴포넌트라고 한다.

- mapStateToProps: 리덕스 스토어 안의 상태를 컴포넌트의 props로 넘겨주기 위해 설정하는 함수.
- mapDispatchToProps: 액션 생성 함수를 컴포넌트의 props로 넘겨주기 위해 사용하는 함수.

> 컴포넌트를 리덕스와 연동하려면 connect 함수를 사용해야 한다. 다음과 같이 사용한다.
> `connect(mapStateToProps, mapDispatchToProps) (연동할 컴포넌트)`