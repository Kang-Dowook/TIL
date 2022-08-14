# json-sever란?
>- json-server란 아주 간단한 DB와 API 서버를 생성해주는 패키지.
>- Backend(이하 BE)에서 실제 DB와 API Sever가 구축될 때까지 Frontend(이하 FE) 개발에 임시적으로 사용할 mock data를 생성하기 위함.

  BE의 작업을 기다리지 않고, FE의 로직과 화면을 구현 할 수 있어 효율적으로 협업 할 수 있다.<br/>
  
  - 설치하기
  CRA로 프로젝트 생성후 yarn 또는 npm을 이용하여 설치.
  >- yarn add json-server

  ### json-server 사용하기
    (1) json-server 실행하기
    json-server가 패키지이긴 하지만 서버이다. 리액트와 별개로 따로 실행시켜줘야된다.<br/>
    >- 실행 명령어
    >- yarn json-server --watch db.json --port 3001
    db.json을 db로 설정하고 3001포트에서 서버를 시작한다.<br/>
    json서버는 실제 서비스를하는데는 적절하지 않다. 테스트 또는 mock data용도로만 사용.

# Axios란?
  >- node.js와 브라우저를 위한 Promise 기반 http 클라이언트.
  >- http를 이용해서 서버와 통신하기 위해 사용하는 패키지.

  Axios 설치하기<br/>
  >- yarn add axios

import React, { useEffect, useState } from "react";
import styled from "styled-components";
import { useDispatch, useSelector } from "react-redux";
import { useNavigate } from "react-router-dom";

const TodoAddTodoForm = () => {
  const dispatch = useDispatch();
  const navigate = useNavigate();
  // const isSuccess = useSelector((state) => state.todos.isSuccess);
  const [todo, setTodo] = useState({
    title: "",
    body: "",
    username: "",
  });

  // useEffect(() => {
  //   if (!isSuccess) return;
  //   if (isSuccess) navigate("/works");

  //   return () => dispatch(clearTodo());
  // }, [dispatch, isSuccess, navigate]);

  // const onChangeHandler = (event) => {
  //   const { name, value } = event.target;
  //   setTodo({
  //     ...todo,
  //     [name]: value,
  //   });
  // };

  return (
    <StContainer>
      <StForm
        // onSubmit={(event) => {
        //   event.preventDefault();
        //   if (
        //     todo.body.trim() === "" ||
        //     todo.username.trim() === "" ||
        //     todo.title.trim() === ""
        //   ) {
        //     return alert("모든 항목을 입력해주세요.");
        //   }
        //   dispatch(__addTodoThunk(todo));
        //   setTodo({ title: "", body: "", username: "" });
        // }}
      >
        <StMain>
          <Wrapper mg="10px 0">
            <Text size="24">작성자</Text>
          </Wrapper>
          <Input
            type="text"
            onChange={onChangeHandler}
            placeholder="작성자의 이름을 입력해주세요. (5자 이내)"
            value={todo.username}
            name="username"
            maxLength={5}
          />
          <Wrapper mg="10px 0">
            <Text size="24">제목</Text>
          </Wrapper>
          <Input
            type="text"
            onChange={onChangeHandler}
            placeholder="제목을 입력해주세요. (50자 이내)"
            value={todo.title}
            name="title"
            maxLength={50}
          />
          <Wrapper mg="10px 0">
            <Text size="24">내용</Text>
          </Wrapper>
          <Textarea
            name="body"
            rows="10"
            maxLength={200}
            onChange={onChangeHandler}
            placeholder="내용을 입력해주세요. (200자 이내)"
            value={todo.body}
          />
        </StMain>
        <Button size="large">추가하기</Button>
      </StForm>
    </StContainer>
  );
};

export default TodoAddFormPage;

const StForm = styled.form`
  width: 100%;
  height: 100%;
  ${flex({
    direction: "column",
    align: "start",
    jusify: "space-between",
  })}
`;

const StContainer = styled.div`
  height: 100%;
`;

const Textarea = styled.textarea`
  width: 100%;
  border: 1px solid #eee;
  padding: 12px;
  font-size: 14px;
`;

const StMain = styled.div`
  width: 100%;
`;
