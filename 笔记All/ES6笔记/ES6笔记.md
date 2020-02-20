# ES6

## let和const

### 1.暂时性死区

let和const命名声明的变量无变量提升，且都会被锁定在声明的代码块中，在let和const命令执行前，使用该变量都会将报错，这一部分称为“暂时性死区”。

```javascript
var tmp = 123;

if(true){
    tmp = "abc";
    let tmp;
}
```

`let tmp`将`tmp`变量绑定至`{}`代码块之内，外部的`tmp`声明无效，`tmp = 'abc'`就处在死区，所以报错。同理在以前没有`let`和`const`命令的时候，`typeof`是一个安全的运算符，即使变量没有被声明，也会正常返回`undefined`，但如果typeof处在死区中，处理了在后文被`let`和`const`的变量，将会报错。

```javascript
typeof undeclared_variable; // undefined 未被let和const声明反而没事
if (true) {
  // TDZ开始 (Temporal Dead Zone: 暂时性死区)
  typeof tmp // ReferenceError
  let tmp; // TDZ结束
  console.log(tmp); // undefined
}
```

### 顶层对象

`var`和`function`的全局声明会自动绑定到`window`或`global`对象，这是ES5全局变量的一个[缺陷](http://es6.ruanyifeng.com/#docs/let#%E9%A1%B6%E5%B1%82%E5%AF%B9%E8%B1%A1%E7%9A%84%E5%B1%9E%E6%80%A7)，`let`和`const`不会。

```javascript
var a = 1;
// 如果在 Node 的 REPL 环境，可以写成 global.a
// 或者采用通用方法，写成 this.a
window.a // 1

let b = 1;
window.b // undefined
```

### const命令

`const`声明的变量只是引用无法修改，对象的内部结构可以改变，使用`Object.freeze()`可以彻底锁定某对象，需递归锁定多层级对象。

```javascript
var constantize = (obj) => {
  Object.freeze(obj);
  Object.keys(obj).forEach( (key, i) => {
    if ( typeof obj[key] === 'object' ) {
      constantize( obj[key] );
    }
  });
};
```

## 2.变量的解构赋值

- 解构时分为匹配模式和被赋值的变量，若相同可简写，注意区分

```javascript
// 被解构的对象的key，和后边被赋值的变量同名，可以简写。
let { matchValue } = { matchValue: 123 };
console.log(matchValue); //123
```

- 等价

```javascript
let { matchValue: matchValue } = { matchValue: 123 }
console.log(matchValue); //123
```

- 通过代码的亮亮可以看出相互之间的对应关系。所以

```javascript
let { matchValue: value } = { matchValue: 123 }
console.log(matchValue); //报错，未定义，这个只是匹配模式，不会被赋值
console.log(value); //123
```

### 函数参数

首先解构赋值允许指定默认值，这为函数参数设置默认值提供基础。

```JavaScript
// 数组解构赋值的默认值
let [x, y = 'b'] = ['a']; // x='a', y='b'
let [x = 'a', y = 'b'] = ['aa', undefined]; // x='aa', y='b'

// 对象解构赋值的默认值
let {x, y = 5} = {x: 1};
x // 1
y // 5
```



这里只讨论一下参数为`Object`类型时，该如何设置默认值，比如一些`options`的设置，通过设置默认值，可有效避免`var foo = options.foo || 'default foo';`。有三种形式，注意这三种的区别：

```JavaScript
const ajax1 = function (url, { type = 'GET', dataType = 'json'} = {}) {
  // TODO
}
const ajax2 = function (url, {} = { type = 'GET', dataType = 'json' }) {
  // TODO
}
const ajax3 = function (url, { type = 'GET', dataType = 'json'} ) {
  // TODO
}
```

`ajax1`的默认参数表示，如果没有传入`options`，则用一个没有键值对的对象`{}`作为默认值，但也正是因此，传入的`options`没有`options.type` 和 `options.dataType`这两个属性，则赋予默认值`type = 'GET', dataType = 'json'`，这是针对键值对某一个`key`设默认值。

`ajax2`的默认参数表示，如果没有传入`options`对象，则用一个`{ type = 'GET', dataType = 'json' }`这样的`options`对象作为默认值，这是针对这一整个`options`设默认值。弊端就是如果开发者在使用时这样写

```javascript
ajax2(url, {type = 'POST'})
```

那么`dataType`参数将要丢失，因为`{type = 'POST'}`代替了默认参数`{ type = 'GET', dataType = 'json' }`，所以一般通过形如`ajax1`的方式定义默认参数。

`ajax3`的默认参数有一个问题，就是当没有传入`options`的时候，相当于从`undefined`中取值`type`，`dataType`来解构，所以会报错，所以`ajax1`会通过`= {}`的方式，把不传入`options`的情况过滤掉。

## 3.各种数据结构的扩展

### 字符串

\````表示模板字符串，就不多介绍了，功能强大好用。codePointAt`可作为`charCodeAt`的替代品，必要时使用`for...of`遍历字符串，他们都是为了处理32 位的 UTF-16 字符。

```javascript
var s = "𠮷a";
s.length // 3  无法正确识别字符串长度，会把‘𠮷’识别为2个字符
s.charAt(0) // '' charAt无法处理这个字
s.charAt(1) // ''
s.charCodeAt(0) // 55362 charCodeAt只能两字节两字节的分开返回
s.charCodeAt(1) // 57271
```

下面看一下ES6的`codePointAt`和`for...of`

```javascript
let s = '𠮷a';
s.codePointAt(0) // 134071 可以识别一整个字
s.codePointAt(1) // 57271 第三，四字节会被返回
s.codePointAt(2) // 97 字符串长度仍有问题
// 使用for...of循环正确处理
for (let ch of s) {
  console.log(ch.codePointAt(0).toString(16));
}
// 20bb7 134071是10进制，20bb7为16进制表示
// 61 字符串长度也没问题，循环执行了2次
```

还引入了`includes`，`startWith`，`endWith`，`padStart`，`padEnd`等方法，具体使用方法可以通过API手册了解一下。

### Number

`parseInt`等全局方法挂在到`Number`上，如`Number.parseInt`，`Number.parseFloat`等，增加了一些高阶计算函数。

### 函数

箭头函数，`this`的指向在函数生成时固定，说白了就是`this`指向与外部一致。

-----------------------------------------------

函数参数设置默认值，前文已经说明。补充一点，设置某参数必须可以：

```javascript
function throwNeedThisParamException(param) {
  throw new Error(`Missing parameter: ${param}`);
}
function demo (x = throwNeedThisParamException('x')) {

}
```

参数的默认值是在取不到值的情况下才会执行，所以正常情况不会抛出这个错误。

---------------------------

参数的`rest`形式，例子如下：

```javascript
function demo (...values) {
  console.log(values)
  console.log('-----------------------')
  console.log(arguments)
}
demo(1,2,3,4)   
//[1,2,3,4]  
-----------------------
//[1, 2, 3, 4, callee: (...), Symbol(Symbol.iterator): ƒ]
```

内置的`arguments`为类数组结构，可以看见有一个`Symbol`类型的字段`Symbol.iterator`，这是它的迭代器，使其可以向数组一样遍历。但如果展开看其`__proto__`，值为`Object`。而使用`rest`形式的参数，可以直接将参数转为数组。注意`rest`形式的参数只能用作最后一个参数。

--------------------

函数的`length`属性返回函数参数的个数，`name`属性返回声明的函数名称，ES6的变量式声明返回变量名。

```js
function f1 () {}
f1.name // f1
const f2 = function (x,y) {}
f2.name // f2
f2.length // 2
```

--------------

双冒号运算符，代替`bind`，`call`，`apply`绑定`this`对象指向。`foo::bar(arguments)`相当于`bar.apply(foo, arguments)`

--------------

[尾调用](http://es6.ruanyifeng.com/#docs/function#%E5%B0%BE%E8%B0%83%E7%94%A8%E4%BC%98%E5%8C%96)，说白了就是最后返回值为执行另一个函数`return anotherFunction()`，而`return anotherFunction() + 1`不属于尾调用，因为在执行完`anotherFunction`后还需要`+1`。尾调用的优势就是在`return`后，可以释放当前函数执行所需要的一切资源空间。对比如下两个例子，是做斐波那契数列求值的：

```js
function Fibonacci (n) {
  if ( n <= 1 ) {return 1};

  return Fibonacci(n - 1) + Fibonacci(n - 2);
}
Fibonacci(10) // 89
Fibonacci(100) // 堆栈溢出
Fibonacci(500) // 堆栈溢出
```

这是最简单的写法，清晰明了，第n项就是前两项的和。但是，为了计算加号两边的值，必须要保存函数执行的全部资源，递归后造成堆栈溢出。这不属于尾调用。

```js
function Fibonacci2 (n , ac1 = 1 , ac2 = 1) {
  if( n <= 1 ) {return ac2};
  return Fibonacci2 (n - 1, ac2, ac1 + ac2);
}
Fibonacci2(100) // 573147844013817200000
Fibonacci2(1000) // 7.0330367711422765e+208
Fibonacci2(10000) // Infinity
```

这是优化过的递归调用，`return`之后无需保存函数所需要的资源，所以不会堆栈溢出，只是在逻辑上不好理解。这种写法`Fibonacci2 (n - 1, ac2, ac1 + ac2)`可以看成一个从前到后推导过程，`n`相当于一个计数器，每次值的增长是通过两个数求和`ac1 + ac2`作为第二个数，`ac2`作为第一个数。

### 数组

扩展运算符`...`，与上文的`rest参数`是相反的用法，`rest参数`是把一个个的参数总和到数组`rest参数`中，而扩展运算符是把数组中的元素一个个提取出来。
扩展运算符可以用来方便的复制一个数组。

```js
let arr = [1,2,3]
console.log(...arr)  // 等价于console.log(1,2,3)
let arr2 = [...arr] // 等价于let arr2 = [1,2,3]，新建一个数组
arr.push(4)
console.log(arr2) // [1,2,3]
```

------------

数组可以通过`Array.from`，`Array.of`生成，可以通过`keys()`，`values()`，`entries()`遍历。
 `Array.from`可以从具有`iterator`的数据结构生成数组，比如`arguments`对象，`document.querySelectorAll()`获得的DOM对象，这些都是类数组，或者`Map`，`Set`等新增的数据结构。
 `Array.of`可以代替`new Array()`，因为`new Array()`的参数与行为不统一，当传入一个参数且为数字时，表示数组长度，`Array.of`不会有这个问题，会通过参数创建数组。
 Array还新增了一些工具方法，如`find`，`findIndex`，`includes`等可以参考其他API手册。

### 对象

`Object.assign`是合并对象，把多个对象合并到第一个对象上。
 `Object.create`是以某原型，生成一个新对象。可选第二个参数，为属性描述符，使用方式参见下方代码。
 `Object.getPrototypeOf`，`Object.setPrototypeOf`是获取和设置对象的原型属性`__proto__`，不应显式使用`__proto__`这个属性。
 `Object.getOwnPropertyDescriptors`是获取对象的属性信息，包括`value`，`writable`，`enumerable`，`configurable`。

```js
const target = { a: 1 };
const source1 = { b: 2 };
const source2 = { c: 3 };
Object.assign(target, source1, source2);
target // {a:1, b:2, c:3}
-------------------
Object.setPrototypeOf(target, { myProto: 'PROTO'})
Object.getPrototypeOf(target) //{ myProto: 'PROTO', __proto__: Object}
let newObj = Object.create(Object.getPrototypeOf(target))
newObj // 无显式属性{ __proto__:{ myProto: 'PROTO', __proto__: Object} } 
-------------------
const descriptors = Object.getOwnPropertyDescriptors(target)
console.log(descriptors)
// {
//   a: {value: 1, writable: true, enumerable: true, configurable: true},
//   b: {value: 2, writable: true, enumerable: true, configurable: true},
//   c: {value: 3, writable: true, enumerable: true, configurable: true}
// }
newObj = Object.create(Object.getPrototypeOf(target), descriptors)
newObj // { a:1, b:2, c:3, __proto__:{ myProto: 'PROTO', __proto__: Object} } 
```

------------

ES6允许字面量定义对象时，用表达式作为属性名，把表达式放在方括号内。

```js
const propKey = 'foo';

const obj = {
  [propKey]: true,
  ['a' + 'bc']: 123
};
obj // { foo: true, abc: 123 }
```

--------------

`Object.is`优化了`===`运算符，处理了`===`的两个问题。

```js
NaN === NaN // false
Object.is(NaN, NaN) // true
--------------
+0 === -0 // true 
Object.is(+0, -0) // false
```

## 4.第七种数据类型Symbol  

`Symbol`为不会重复的值，第七种基本数据类型，类似字符串，可以作为对象的`key`，但不会被`for...of`，`for...in`，`Object.getOwnPropertyNames()`，`Object.keys()`返回，如需要遍历，需使用`Object.getOwnPropertySymbols()`，或者`Reflect.ownKeys()`返回全部`key`。

```js
let foo = Symbol('foo');
const obj = { [foo]: 'foobar' }
for (let i in obj) {
  console.log(i); // 无输出
}
Object.getOwnPropertyNames(obj)
// []
Object.getOwnPropertySymbols(obj)
// [Symbol(foo)]
Reflect.ownKeys(obj)
// [Symbol(foo)]
```

### Symbol.for() 和 Symbol.keyFor()

`Symbol`可以去确保生成的值不同，但有时需要保存下来以便再次使用，类似于单例，如果存在就不会重新创建。这个时候就需要使用`Symbol.for()`。

```js
let s1 = Symbol('foo');
let s2 = Symbol.for('foo');
let s3 = Symbol.for('foo');
s1 === s2 // false
s2 === s3 // true
```

```js
s2 === s3 // true
```

从上例可以看出，`Symbol.for`类似于将这个`Symbol`登记，所以`s1`这个未登记的`Symbol`不会等于其他`Symbol`。
 `Symbol.keyFor`会返回已登记的`Symbol`的`key`，一定是登记过的才会返回。接上例：

```javascript
Symbol.keyFor(s1) // undefiend
Symbol.keyFor(s2) // "foo"
```

## 5.Proxy和Reflect

`Proxy`代理对象的各种内置方法，`get` `set` `construct`等，类似于拦截器。
 `Reflect`则作为`Object`的替代者，`Object`上的一些静态方法被移植到了`Reflect`上。
 `Reflect`对象一共有 13 个静态方法。

- Reflect.apply(target, thisArg, args)
- Reflect.construct(target, args)
- Reflect.get(target, name, receiver)
- Reflect.set(target, name, value, receiver)
- Reflect.defineProperty(target, name, desc)
- Reflect.deleteProperty(target, name)
- Reflect.has(target, name)
- Reflect.ownKeys(target)
- Reflect.isExtensible(target)
- Reflect.preventExtensions(target)
- Reflect.getOwnPropertyDescriptor(target, name)
- Reflect.getPrototypeOf(target)
- Reflect.setPrototypeOf(target, prototype)
   通过`Proxy`和`Reflect`可以实现观察者模式，说白了就是：监听`set`方法，执行相应操作。

```js
const person = { name: 'Li', age: 18}
const personObserved = observe(person)

function observe(obj) {
  return new Proxy(obj, {
    set: function (target, key, value, receiver) {
      console.log(`setting ${key} to ${value}!`);
      return Reflect.set(target, key, value, receiver);
    }
  })
}

personObserved.name = 'zhang'
// setting name to zhang!
```

## 6.Promise

`Promise`用来处理异步操作，是构造函数，参数为`then`和`catch`后需要执行的方法。下面是使用`Promise`封装的`ajax`：

```js
const getJSON = function(url) {
  const promise = new Promise((resolve, reject) => {
    const handler = function() {
      if (this.readyState !== 4) {
        return;
      }
      if (this.status === 200) {
        resolve(this.response);
      } else {
        reject(new Error(this.statusText));
      }
    };
    const client = new XMLHttpRequest();
    client.open("GET", url);
    client.onreadystatechange = handler;
    client.responseType = "json";
    client.setRequestHeader("Accept", "application/json");
    client.send();
  });
  return promise;
};

getJSON("/posts.json").then(function(json) {
  console.log('Contents: ' + json);
}, function(error) {
  console.error('出错了', error);
});
```

## 7. Iterator 和 for...of循环

`Iterator`被挂载在对象的`Symbol.iterator`属性下，`Symbol.iterator`不是一个`Iterator`，而是会返回`Iterator`的函数。

```js
const arr = [1,2,3,4,5]
let iterator = arr[Symbol.iterator]();
iterator // Array Iterator {}
iterator.next() // {value: 1, done: false}
......
iterator.next() // {value: 5, done: false}
iterator.next() // {value: undefined, done: true}
```

## 8. Generator 和 yield

```js
function* demo(){
  console.log(`${yield 1}`);
  console.log(`${yield 2}`);
  yield* demo2(); //返回另一个generator的结果
}
function* demo2(){
  yield 3;
}
let ite = demo();
ite.next() // 返回值：{value: 1, done: false}
ite.next() // console：undefined, 返回值：{value: 2, done: false}
ite.next(123456789) // console: 123456789, 返回值：{value: 3, done: false} 
```

解释一下运行结果：第一次`ite.next()`时，程序执行到`yield 1`被终止，故没有打印日志，再次执行ite.next()时，代码继续，开始执行`console.log(`${yield 1}`);`，但输出不是`1`而是`undefiend`，因为`ite.next()`的参数值会被当做上次`yield`语句的执行结果，所以下面的`ite.next(123456789)`会输出数字`123456789`。