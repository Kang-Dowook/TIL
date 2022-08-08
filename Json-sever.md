# json-sever란?
>- json-server란 아주 간단한 DB와 API 서버를 생성해주는 패키지.
>- Backend(이하 BE)에서 실제 DB와 API Sever가 구축될 때까지 Frontend(이하 FE) 개발에 임시적으로 사용할 mock data를 생성하기 위함.

  BE의 작업을 기다리지 않고, FE의 로직과 화면을 구현 할 수 있어 효율적으로 협업 할 수 있다.<br/>
  
  - 설치하기
  CRA로 프로젝트 생성후 yarn 또는 npm을 이용하여 설치.
  >- yarn add json-server

  # json-server 사용하기
    (1) json-server 실행하기
    json-server가 패키지이긴 하지만 서버이다. 리액트와 별개로 따로 실행시켜줘야된다.<br/>
    >- 실행 명령어
    >- yarn json-server --watch db.json --port 3001
    db.json을 db로 설정하고 3001포트에서 서버를 시작한다.<br/>
    json서버는 실제 서비스를하는데는 적절하지 않다. 테스트 또는 mock data용도로만 사용.
    
