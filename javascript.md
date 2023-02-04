# JavaScript

## Destructuring Expression

```javascript
{x,y} = foo;

x = foo.x;
y = foo.y;

{width, height, color} = options

width = options.width; 
height = options.height; 
color = options.color

const { items } = args

const items = args.items
```

## Array Filter Method

The original array doesn't change.

```javascript
const words = ['spray', 'limit', 'elite', 'exuberant', 'destruction', 'present'];

const result = words.filter((word) => word.length > 6); // only select words which length is greater than 6.

console.log(result);
// expected output: Array ["exuberant", "destruction", "present"]
```

## Constructor

```javascript
/*
Constructor is used to create multiple objects with different values.
Constructor is a copy machine of objects.
비슷한 오브젝트를 쉽게 찍어낼 수 있는 문법
*/

let student = { name: "Eddie", age: 15 };

// constructor to create a student object
function Student(name, age) {
  // this 는 새로 생성되는 오브젝트를 뜻함. (instance)
  this.name = name;
  this.age = age;
  this.sayHi = () => {
    console.log(`안녕하세요 ${name} 입니다`)
  }
}

// let a = new Student('Shin', 20)
// a.sayHi()


// Inheritance
// prototype 은 유전자.
// 생성자 생성시 prototype 이라는 공간이 자동으로 생김.
// If you add properties in prototype, all instances can access them.
// check instance variables first and if not exists, check variables in prototype (class variables)
// 1) prototype can be created in function
// 2) instance.__proto__ can be used to see the parent properties (one level higher only)
// 3) prototype chain

Student.prototype.gender = 'Male'

// console.log(a.gender)

let parent = { name : 'Shin' }
let child = {}

child.__proto__ = parent
console.log(child.name)

// Q1

function Parent(){
  this.name = 'Kim';
}
var x = new Parent();

x.__proto__.name = 'Park';
console.log(x.name) // Kim ==> look for instance variables first

// Q2

function Student(이름, 나이){
  this.name = 이름;
  this.age = 나이;
}

Student.prototype.sayHi = function() {
    console.log('안녕 나는 ' + this.name + '이야');
  }
var 학생1 = new Student('Kim', 20);

학생1.sayHi(); //왜 이 코드가 제대로 안나오죠? this in prototype refers prototype object, and it doesn't contain name attribute?

// We used arrow function to define sayHi() so this is not correct.
// this was actually referring to window and window.name = undefined.
// 

// Q3

Array.prototype.remove3 = function() {
  console.log(this)
  for (let i=0; i < this.length; i++) {
    if (this[i] === 3) {
      this.splice(i,1)
    }
  }
  // this.forEach(n => {
  //   if (n === 3) {
  //     this.splice
  //   }
  // })
  // this = this.filter(n => n !== 3)
}

let arr = [1,2,3];
arr.remove3();
console.log(arr)
```

## Functions

```javascript
function app(a, b, c) {
  console.log(arguments);
}

// ...
// 1) spread operator
// 2) rest

function good(a, b, ...rest) {}
// 필요한 파라미터만 빼 모두 rest array 에 담을 수 있다.
// if ... is located inside function parameter, it's ...rest.
// if ... is used elsewhere, it's spread operator.

function fun2(...rest) {
  rest.forEach((arg) => console.log(arg));
}

fun2(1, 2, 3);

// Question 1

var a = [1, 2, 3];
var b = "김밥";
var c = [...b, ...a];
console.log(c); // ['김', '밥', 1, 2, 3]

// Q2

var a = [1, 2, 3];
var b = ["you", "are"];
var c = function (a, b) {
  console.log([[...a], ...[...b]][1]);
  // [[1,2,3], ...['you', 'are']][1]
  // [[1,2,3], 'you', 'are'][1]
  // 'you'
};
c(a, b);

// Q3

function 함수(a = 5, b = a * 2) {
  console.log(a + b);
  return 10;
}
함수(3); // a = 3, b = 6 ==> console.log(9)

// Q4

function 함수(a = 5, b = a * 2) {
  console.log(a + b);
}
함수(undefined, undefined); // console.log(5 + 10) = 15

// Q5

function 어레이(...rest) {
  return rest;
}

var newArray = 어레이(1, 2, 3, 4, 5);
console.log(newArray);

// Q6

var numbers = [2,3,4,5,6,1,3,2,5,5,4,6,7];

console.log(Math.max(...numbers))

// Q7

function strSort(word) {
  console.log(...[...word].sort())
}

strSort('bear')

// Q8

function 글자세기(word) {
  let counts = {}

  let strArr = [...word]

  [strArr].forEach((ch) => {
    if (ch in counts) {
      counts[ch] += 1
    } else {
      counts[ch] = 1
    }
  })
  console.log(counts)
  // console.log(...[...word].sort())
}

글자세기('aacbbb')
```

## Regular Expressions

```javascript
/a/.test('abcde') // checks whether a is in abcde

/[a-z]/.test('abcde') // a부터 z까지 영어 소문자 중 아무 글자 하나를 뜻함.

/[A-Z]/.test('abcde') // 대문자 A부터 Z까지 아무 글자 1개.

/[a-zA-z]/.test('abcde') // 소문자, 대문자 상관없이 아무 알파벳 1개.

/[0-9]/ // 숫자 0~9까지 아무 숫자 1개.

/\S/ // 아무 문자 하나. (특수기호 포함.)

/^a/ // a로 시작하나?

/a$/ // a로 끝나나?

/a|b/ // a or b

/a&b/ // a and b

정규식에서 .은 특수한 문법으로 쓰임. . 을 쓰고 싶은 경우 \. 사용. (백슬래시)

/\S+/ // +는 왼쪽 문자 반복검색 (글자수 상관없음)
```
