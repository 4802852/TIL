# What is Typescript

Javascript Superset: Javascript 에 기반한 언어이고, 자바스크립트에 새로운 특징과 이점들을 더해준다.

Javascript 환경(browser 같은)에서 직접적으로 실행이 불가능하기 때문에 작성이 완료되고 나서는 Javascript 로 컴파일해야 한다. 즉, Typescript 가 주는 특징과 이점들은 Javascript 에서 불가능한 것들을 해주는 것이 아니라, 그러한 기능들을 조금 더 깔끔하고 쉽게 사용할 수 있도록 도와주는 것이다.

가장 큰 특징은 type: 에러에 대한 체크를 좀더 빠르게 찾고 고칠 수 있도록 해준다.

## Why Typescript

Javascript 에서는 변수에 타입이 정해져있지 않기 때문에, 이로 인하여 개발자가 원하지 않는 방식으로 동작할 수 있다. 예를 들어, 2 + 3 의 수학적인 계산이 필요한 함수에서 실수로 '2' 와 '3' 의 문자를 전달한다면, javascript 는 이 두 문자를 연결하여 '23' 이라는 결과를 내놓을 것이다. 하지만 미리 함수에 입력받을 타입을 정해놓는다면 '2', '3' 문자가 전달되었을 때, 문자가 아닌 숫자를 입력하도록 경고해줄 수 있다.

Javascript 에서도 함수가 전달받는 인풋의 타입이 원하는 타입과 다를 때, 에러를 표시하도록 할 수 있지만, 이러한 경우 추가적인 코드를 통해서(타입을 검사하여 일치하는지 확인하는) 이루어져야 하기 때문에 코드의 길이가 길어지게 된다.

## Basic Usage of Typescript

### Install Typescript

Typescript 는 npm 으로 설치해야하기 때문에 node.js 설치가 필요하다.

```
$ sudo npm install -g typescript
```

### Basic Usage of Typescript

```
const button = document.getElementById("button");
const input = document.getElementById("num1");

button.addEventListener("click", function() {
    console.log(input.value)
})
```

Javascript 에서는 아무런 문제가 없는 위의 코드도 Typescript 에서는 오류를 발생하게 된다. Typescript 는 html 코드를 검사하지 않기 때문에 getElementById 가 정확하게 작동하여 input 이라는 녀석이 제대로 지정되었는지 알 수 없다. 따라서 input 이 어떤 Element 를 말하는지, 또 해당 Element 에 value 라는 정보가 있을 지 알 수 없으므로 오류를 띄우게 된다.

Typescript 는 개발자에게 이러한 부분을 다시 한번 체크하고 표현을 명확하게 하도록 강요한다.

```
const input = document.getElementById("num1")! as HTMLInputElement;
```

위와 같이 변경하여 코드를 명확하게 함으로써 input.value 에 있던 오류 표시를 제거할 수 있다. ! 표시는 Typescript 에게 element id 를 체크했고 이 부분은 절대 null 이 아니라는 것을 알려주는 것이고, 이 요소는 HTMLInputElement 이라는 것을 알려주게 된다. 따라서 HTMLInputElement 라는 요소는 value 를 갖고 있기 때문에 input.value 는 명확한 값을 표시한다고 Typescript 가 명확하게 알 수 있다.

```
function add(num1, num2) {
    return num1 + num2;
}
```

위의 코드에서 num1 과 num2 에 마우스오버해보면 num1: any 로 표시되며 타입을 정하는 것이 좋다고 알려준다.

이런 경우, num1 과 num2 가 number 이길 원한다면 다음과 같이 그 타입을 지정해줄 수 있다.

```
function add(num1: number, num2: number) {
    return num1 + num2;
}
```

이제 add 함수를 이용하는 다른 위치에서 변수에 number 가 아닌 string 등을 실수로 넣는다면 에러코드를 발생시키게 된다.

이러한 식으로 Typescript 는 개발자에게 더 명확하고 클린한 코드를 작성할 수 있도록 해줌으로써 원하지 않는 에러를 방지할 수 있게 한다.

### Compile Typescript

```
$ tsc abc.ts
```

커맨드라인에서 위와 같이 입력하여 Typescript 로 작성된 파일을 Javascript 로 컴파일해줄 수 있고, 이 js 파일을 이용하여 browser 에서 실행될 수 있다.

