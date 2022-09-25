# Basic Project Setup

## lite-server 설치

node.js 는 npm 을 이용하여 실제로 사용되는 코드 뿐만이 아니라 개발에 도움되는 여러 기능들을 설치할 수 있다.

그 중 lite-server 는 유저의 기기를 하나의 작은 서버로 만들어, 유저가 만든 페이지를 표시해주고, 거기에서 더하여 내부의 파일이 바뀔 때 이를 페이지에 반영해준다.

```
$ npm init
$ npm install lite-server --save-dev
```

```
// package.json
"scripts": {
    "start": "lite-server"
}
```

위와 같이 수정해주면 

```
$ npm start
```
 
를 통하여 lite-server 를 동작시키고, http://localhost:3000 의 주소로 현재 만들어진 페이지를 확인해볼 수 있다.

