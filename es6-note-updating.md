# es6语法扫盲更新ing

## 对象扩展

*扩展运算符(对象展开符(...),写法如下)* 
```
let { x, y, ...z } = { x: 1, y: 2, a: 3, b: 4 };
x // 1
y // 2
z // { a: 3, b: 4 }

let a = {...z} // 克隆对象
a // { a: 3, b: 4 }

let arr = [1,2,3,4,5]
let arr2 = [6,7,8]
let oarr1 = [...arr] // 数组克隆
let oarr2 = [...arr, ...arr2] // 合并数组
oarr1 // [1,2,3,4,5]
oarr2 // [1,2,3,4,5]

[...'hello'] // ['h', 'e', 'l', 'l', 'o']

// function
function foo(...args){
  args // [...arguments]
}
foo(1,2,3) // args = [1,2,3]
```


## 箭头函数

*ES6允许使用“箭头”（=>）定义函数* 
```
var f = x => x; // 相当于 var f = function(x){return x;}
var b = (x, y) => ({x, y})
```

- 注意事项
  - 函数体内的this对象，就是定义时所在的对象，而不是使用时所在的对象，并且this不可改变
  - 不可以当作构造函数，也就是说，不可以使用new命令，否则会抛出一个错误
  - 不可以使用arguments对象，该对象在函数体内不存在
  - 不可以使用yield命令，因此箭头函数不能用作Generator函数


## 函数绑定

*函数绑定运算符是并排的两个双冒号（::），双冒号左边是一个对象，右边是一个函数。该运算符会自动将左边的对象，作为上下文环境（即this对象），绑定到右边的函数上面* 

```
  function bar(){
  }
  var foo = {}
  foo::bar // 等同于 bar.bind(foo)
```

## Class

*ES6提供了更接近传统语言的写法，引入了Class（类）这个概念，作为对象的模板。通过class关键字，可以定义类* 

```
 //定义类
  class Point {
    constructor() {}
    toString(){}
    render(){}
  }
  // 等价于
  function Point(){}
  Point.prototype.toSring = function(){}
  Point.prototype.render = function(){}

  // 类表达式
  const Point = class Temp{} // 类的名字为 Point，Temp只会在类的内部使用，Temp可省略
```

- tip
  - constructor 是类的默认方法，用 new 调用时执行的方法
  - 只能使用 new 实例化类
  - 有name属性, Point.name -> 'Point'
  - 不存在变量提升

*Class 继承* 

```
  class ColorPoint extends Point{
    constructor(){
      super() // 调用父类的构造函数，如果有constructor，必须调用，如果没有constructor，后台自动调用
    }
  }
```
- tip
  - 只要是有prototype属性的函数，就能被继承
  - 如果继承 null，相当于继承 Function
  - super 代表父类构造函数，也可作为对象调用，可访问父类实例的方法和属性


## Module

*javascript 模块体系，模块功能主要由两个命令构成：export和import。export命令用于规定模块的对外接口，import命令用于输入其他模块提供的功能*

```
一个模块就是一个独立的文件。该文件内部的所有变量，外部无法获取。如果你希望外部能够读取模块内部的某个变量，就必须使用export关键字输出该变量。

// profile.js
export var firstName = 'Michael';
export var lastName = 'Jackson';
export var year = 1958;
export function getFullName(){}
export default {firstName, lastName, year} // 默认模块
export * from 'lodash'; // 模块继承，导出lodash模块的所有方法
import 导入

使用export命令定义了模块的对外接口以后，其他JS文件就可以通过import命令加载这个模块（文件）。

// main.js

import {firstName, lastName} from './profile';
import {firstName as fn, lastName as ln} from './profile'; // 重命名
import Profile from './profile';
import Profile as p from './profile';
import 有变量提升

```



不定时更新ing........