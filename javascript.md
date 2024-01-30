# Objects and Object Constructors

### 1. Introduction

```js
const myObject = {
  property: "Value",
  otherProperty: 77,
  "obnoxious property": function () {
    // do stuff
  },
};
```

- 객체의 정보를 불러오는 방법(dot, bracket)

```js
// dot notation
myObject.property; //"Value"

//bracket notation
myObject["obnoxious property"]; //[Function]
```

- 주로 사용하는 건 <span style="font-weight : bold;  color: skyblue">dot notation</span>이지만, 위의 객체의 프로퍼티 중에 "obnoxious property"의 경우, dot notation으로는 error가 발생하기 때문에(myObject."obnoxious property") 이런 경우라면 <span style="color: white">bracket notation</span>을 사용해야한다.

### 2. Objects as a design pattern

- 코드를 조직화 하기 가장 쉬운 방법중 하나는 object를 그룹화하는 것이다.

```js
// example 1
const playerOneName = "tim";
const playerTwoName = "jenn";
const playerOneMarker = "X";
const playerTwoMarker = "O";

// example 2
const playerOne = {
  name: "tim",
  marker: "X",
};

const playerTwo = {
  name: "jenn",
  marker: "O",
};

// which one better?
```

### 3. Object contructors

- 복제할 필요가 있는 특정 유형의 객체가 있을때, object contructor가 좋은 방법일 수 있다.

```js
// object constructor
function Player(name, marker) {
  this.name = name;
  this.marker = marker;
}

// 호출할때,
const player = new Player("steve", "X");
console.log(player.name); //'steve'

// 위 방법 그대로 함수도 생성할 수 있다.
function Player(name, marker) {
  this.name = name;
  this.marker = marker;
  this.sayName = () => {
    console.log(this.name);
  };
}

const player1 = new Player("steve", "X");
const player2 = new Player("also steve", "O");
player1.sayName(); //'steve'
player2.sayName(); //'also steve'
```

### 4. The prototype

- js의 모든 object는 prototype을 가지고 있다.
- prototype은 original 객체로부터 상속받은 다른 객체이고, original은 상속한 prototype의 모든 메소드와 프로퍼티에 접근할 수 있다.

### 5. Prototypal inheritance

- memory를 save하기 위해 prototype에 프로퍼티와 함수들을 정의한다.
- Prototypal Inheritance 예시

```js
let animal = {
  eats: true,
};

let rabbits = {
  jumps: true,
};

// prototype 설정
rabbit.__proto__ = animal;

console.log(rabbit.eats); // true
console.log(rabbits.jumps); // true
```

- 위의 토끼의 prototype을 animal로 설정해두고, 토끼의 eats을 호출하게되면, 원래 rabbits엔 eats이 없어 false를 호출해야할 것인데, prototype의 eats를 호출 하게 된다. 즉 원래 객체에 존재하지 않는 프로퍼티나 함수가 있게되면 prototype의 함수나 프로퍼티를 호출하게 되는데 이것을 prototypal inheritance라 한다.

# Factory Functinos and the Module Pattern

### 1. Scoopfuls of scopes

- global, local variables

### 2. Closures

```js
function makeAdding(firstNumber) {
  // "first" is scoped within the makeAdding function
  const first = firstNumber;
  return function resulting(secondNumber) {
    // "second" is scoped within the resulting function
    const second = secondNumber;
    return first + second;
  };
}

// but we've not seen an example of a "function"
// being returned, thus far - how do we use it?
const add5 = makeAdding(5);
console.log(add5(2)); // logs 7
```

- 자바스크립트의 함수는 closures를 형성하고 있다.
- closure는 함수와 함수가 선언된 surrounding state의 결합을 의미한다.
- surrounding state = lexical environment

# Webpack

### 1. Bundling

- webpack에게 entry point로서 file을 주게되면, dist에 하나의 .js 로 번들링되기 전에 import/export 한 지점을 기본으로 dependency graph를 구축하게된다.

- asset이나 css같은 것들도 dist안에 복사하거나 번들시켜준다.

### 2. Html-webpack-plugin

- html-webpack-plugin 이라는 플러그인은 우리가 프로젝트를 빌드할 때, dist경로에 html file을 자동적으로 생성해준다.

# JSON

### 1. what is JSON?

- JSON은 자바스크립트 객체 문법에 기반해서 구조화된 데이터를 표현하기 위한 표준 텍스트 기반 형식이다.
- JSON은 string으로 존재해서, 네트워크를 통해 데이터를 전달하고자 할 때 유용하다.
- 자바스크립트는 string과 native object사이를 변환할 수 있는 메소드를 가진 global JSON 객체를 제공한다
- desrialization : string -> native object
- serialization : native object -> string
