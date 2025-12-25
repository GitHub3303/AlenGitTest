# TypeScript 

## 一、TypeScript 介绍

TypeScript 简称『TS』，是微软开发的一个开源的编程语言。

## 二、TS 特点

TS 主要有如下几个特点:

* 完全兼容 JavaScript，是 JavaScript 的超集
* 引入类型系统，可以尽早的定位错误位置, 帮助提升开发效率
* 先进的 JavaScript，支持 JavaScript 的最新特性

> TypeScript 在社区的流行度越来越高，它非常适用于一些大型项目，也非常适用于一些基础库，极大地帮助我们提升了开发效率和体验。

 ## 三、TS 环境搭建

学习 TS 阶段我们可以借助 TypeScript 的编译工具『typescript』

```shell
npm i -g typescript
```

使用下面的命令检查是否安装成功以及查看包的版本

```
tsc -v
```

## 四、TS 初体验

1. typescript 初始化.  创建 ts 的配置文件`tsconfig.json`

   ```
   tsc --init
   ```

2. 创建一个 JS 文件 『hello.ts』

   ```javascript
   let str: string = 'hello world';
   console.log(str);
   
   function add(a: number, b:number):number{
     return a + b;
   }
   console.log(add(1, 100));
   ```

3. 命令行运行，`这里的后缀是 ts`

   ```sh
   tsc hello.ts
   ```

4. 命令行运行，`这里的后缀是 js`

   ```shell
   node hello.js
   ```

   > 可以使用 `tsc -w` 命令开启自动编译

## 五、TS 语法

### 5.1 TS 基础类型

TypeScript 支持与 JavaScript 几乎相同的数据类型，此外还提供了实用的枚举类型方便我们使用

TS 支持的变量类型如下：

| 类型       | 描述                                                    |
| ---------- | ------------------------------------------------------- |
| boolean    | 限制为布尔类型， true 或者 false                        |
| number     | 限制为任意的数字。 二进制，八进制，十进制，十六进制均可 |
| string     | 限制为任意的字符串。单引号，双引号，反引号均可          |
| 字面量     | 限制为某个字面量                                        |
| any        | 限制为任意类型                                          |
| void       | 限制为 undefined, 一般用来限制函数的返回值              |
| object     | 限制为对象类型                                          |
| array      | 限制为数组类型    string[]   Array<number>              |
| tuple 元组 | 限制为固定长度与类型的数组                              |
| enum 枚举  | 限制为枚举的数据                                        |

#### 5.1.1 布尔类型

最基本的数据类型就是简单的 true/false 值，在JavaScript 和 TypeScript 里叫做 `boolean`（其它语言中也一样）。

```js
let isDone: boolean = false;
isDone = true;
// isDone = 2 // error
```

#### 5.1.2 数字类型

除了支持十进制和十六进制字面量，也支持二进制和八进制字面量。

```js
let a1: number = 10 // 十进制
let a2: number = 0b1010  // 二进制
let a3: number = 0o12 // 八进制
let a4: number = 0xa // 十六进制
```

#### 5.1.3 字符串类型

JavaScript 程序的另一项基本操作是处理网页或服务器端的文本数据。 像其它语言里一样，我们使用 `string` 表示文本数据类型。 和 JavaScript 一样，可以使用双引号（`"`）或单引号（`'`）表示字符串。

```js
let name:string = 'tom'
name = 'jack'
// name = 12 // error
let age:number = 12
const info = `My name is ${name}, I am ${age} years old!`
```

#### 5.1.4 字面量类型

TS 允许限制某个变量为固定的某个值

```js
let z: 521 = 521;
let z2: 'love' = 'love';
// z='abc'; //类型不符 error
```

#### 5.1.5 any

any 类型允许变量的值为任意类型, 并且可以进行任意类型的赋值

```js
let a: any = 100;
a = 'iloveyou';
```

> 尽量不要用 any, 因为对于 any 类型 typeScript 会关闭类型检查功能

#### 5.1.6 void

void 表示空的, 该类型主要用在函数返回值上

```js
function fn():void{
  
    
}
```

#### 5.1.7 对象

object 限制类型为对象,  `用的比较少`

```js
//object 类型
let o: object = {}
o = [];
```

> object 用的也非常少, 因为存在的可能性太多了, 起不到约束的效果

#### 5.1.8 数组

TypeScript 像 JavaScript 一样可以操作数组元素。 不过数组中元素值的类型都是一样的.

有两种方式可以定义数组。 

​	第一种，可以在`元素类型后面接上[]`，表示由此类型元素组成的一个数组：

​	第二种,  方式是使用数组泛型，`Array<元素类型>`：

```js
let arr: number[] = [1,2,3];
// arr.push('abc');// error
let arr2: Array<number> = [4,5,6];
```

#### 5.1.9 元组

元组（Tuple）类型允许表示一个已知元素数量和类型的数组，`各元素的类型不必相同`

```js
let t1: [string, number] = ['james', 30];
console.log(t1[0].toUpperCase());
//console.log(t1[1].slice(1));// error
```

#### 5.1.10 枚举

枚举（enum）类型是对 JavaScript 标准数据类型的一个补充。 使用枚举类型可以`为一组数值赋予友好的名字`。 一般用于组织一些有相似之处的常量，让这些常量更规范、更统一。

```tsx
enum Gender{
  Female,
  Male,
  Secret
}

let me: object = {
  gender: Gender.Male,
}

console.log(me);
```

#### 5.1.11 联合类型

联合类型（Union Types）表示取值可以为多种类型中的一种。

```js
let v1: number | string;
v1 = 5211314;
v1 = 'iloveyou'
```



#### 5.1.12 类型断言

类型断言（Type Assertion）可以告诉编译器，“相信我，我知道自己在干什么，别报错，出了事我负责”。

```typescript
let root = document.querySelector('#root') as HTMLElement;
root.querySelector('span');
```



#### 5.1.13 类型推断

TS 会在没有明确的指定类型的时候推测出一个类型。主要有下面两种情况

1. 变量声明时赋值了，推断为值对应的类型
2. 变量声明时没有赋值， 推断为 any 类型

```js
let v3 = 100; // number 类型
// v3 = 'loveyou'; //类型 error
let v4; // any 类型
v4 = 100; 
v4 = 'loveyou';
```

### 5.2 函数

#### 5.2.1 参数与返回值类型

TypeScript 可以为参数与返回值设置类型，代码示例如下：

```typescript
function add(x: number, y: number): number {
  return x + y
}

let sub = function(x: number, y: number): number { 
  return x + y
}

let times = (a: number, b: number): number => {
    return a * b;
}
```

>  TypeScript 能够根据返回语句自动推断出返回值类型，因此我们通常省略返回值的类型。

#### 5.2.2 函数声明放到前面

现在我们已经为函数指定了类型，下面让我们写出函数的完整类型。

```typescript
let divide: (a: number, b: number) => number = function(a, b){
    return a / b;
}
```

#### 5.2.3 可选参数

TypeScript 默认要求函数实参数量要与形参的数量保持一致，不过可以使用『 ?: 』设置参数为可选参数

```typescript
//截取字符串
function slice(str: string, start: number, end ?: number): string{
    return 'iloveyou';
}
```

#### 5.2.4 参数默认值

TypeScript 与 JavaScript 一样，允许为参数设置默认值

```typescript
//构建手机号
function buildPhone(code:string, area : string = '+86'){
    return area + code;
}
```

#### 5.2.5 剩余参数

针对不定个数参数的函数时，我们可以使用 ES6 提供的 rest 参数来处理。不过在 TypeScript 中需要设置类型。

```typescript
//剩余参数
function add(a: number, b: number, ...args: number[]){
  //求和
  args = [a, b, ...args];
  return args.reduce((prev: number, current: number) => {
    return prev + current;
  })
}
```

### 5.3 类

TS 中的类与 JS 的类使用方式类似,  不过增加了对属性与方法的类型限制

#### 5.3.1 成员类型限制

这里的类型限制跟变量和函数的类型限制是非常相似的

```typescript
class Person{
    //声明属性
    name: string;
    age: number;
    //声明并赋值
    alias: string = '张三';

    //构造方法
    constructor(name: string, age: number){
        this.name = name;
        this.age = age;
    }

    //声明方法
    intro():void{
        console.log(`我叫 ${this.name}, 今年 ${this.age} 岁`)
    }
}

//实例化对象
let me: Person = new Person('xiaohigh', 35);

//调用实例方法
me.intro();
```

#### 5.3.2 继承

TypeScript 继承语法与 JavaScript 完全相同

```typescript
class Programmer extends Person{
  constructor(name: string, age: number, experience: number){
    super(name, age);
  }

  //编程的功能
  program(){
    console.log('我可以编程哦~~');
  }
}
```

#### 5.3.3 成员修饰符

一些面向对象编程语言（Java, C++）中都有成员修饰符特性，TypeScript 也引入成员修饰符。

成员修饰符有三个：

* public (默认)      公开的
* protected            受保护的
* private                 私有的

这些修饰符实现了对象成员的访问控制

|           | 自身类 | 子类 | 类外部 |
| --------- | ------ | ---- | ------ |
| public    | √      | √    | √      |
| protected | √      | √    | X      |
| private   | √      | X    | X      |

```js
//继承
class Father {
  public name: string;
  protected age: number;
  private salary: number;

  constructor(name: string, age: number, salary: number){
    this.name = name;
    this.age = age;
    this.salary = salary;
  }

  info(){
    console.log(this.name);
    console.log(this.age);
    console.log(this.salary);
  }
}

class Son extends Father{
  constructor(name: string, age: number, salary: number){
    super(name, age, salary);
  }

  checkSalary(){
    console.log(this.name);
    console.log(this.age);
  }
}

let xue = new Son('xue', 26, 16000);

console.log(xue.name);
```

### 5.4 接口

#### 5.4.1 基本使用

TypeScript 中引入了接口，用来限制对象的结构与类型。代码示例：

```typescript
//声明接口
interface BoyFriend{
    name: string;
    age: number;
}
//声明对象 满足接口结构与类型要求
let zhangsan: BoyFriend = {
    name: '张三',
    age: 18,
}

console.log(zhangsan);
```

> 上述代码中，对象的属性不能多， 也不能少，属性值的类型也必须满足接口的要求

#### 5.4.2 可选属性

如果某些属性不是固定的，只是某些条件下存在，可以使用可选属性配置

```typescript
interface BoyFriend{
    name: string,
    age: number,
    car ?: string
}
```

这样设置之后，对象中的 car 属性就不是必须的属性

#### 5.4.3 只读属性

如果一些属性的值不允许修改，则可以使用『readonly』标志，这样一旦发现被修改，立即报错

```typescript
interface BoyFriend{
    readonly id: number,
    name: string,
    age: number,
    car ?: string
}
```

这样设置后， 如果修改 id 属性， 编译器就会报错

> readonly 与 const 的功能很像，不过 readonly 是限制对象的属性， const 是限制变量的值

#### 5.4.4 限制方法

接口除了可以限制属性类型之外，也可以对对象的方法进行限制

```typescript
interface BoyFriend{
    readonly id: number,
    name: string,
    age: number,
    car ?: string,
    cook: () => void  
    cook() : void
}
```

该接口要求对象必须要有 cook 方法且返回结果必须为 undefined

#### 5.4.5 类与接口[了解]

之前接口只能限制单个对象的结构与类型，接口与类结合之后，可以约束一类对象的结构与类型

```typescript
interface BoyFriend {
    name: string;
    age: number;
    car ?: string;
    cook: () => void
}

class Person implements BoyFriend{
    name: string;
    age: number;
    car: string;

    constructor(name: string, age: number, car: string){
        this.name = name;
        this.age = age;
        this.car = car;
    }

    cook(){
        console.log('我可以做蛋炒饭~~');
    }
}
```

#### 5.4.6 类的多实现[了解]

一个类可以同时实现多个接口，类必须要包含对应的属性和方法才能通过编译

```typescript
interface BoyFriend{
    readonly id: number,
    name: string,
    age: number,
    car ?: string,
    cook: () => void  
}

interface Staff{
    name: string
    age: number
    programTS: () => void;
}

class Person implements BoyFriend, Staff{
    //对象属性
    id:number
    name: string
    age: number

    //构造方法
    constructor(id: number, name: string, age: number){
        this.id = id;
        this.name = name;
        this.age = age;
    }

    //对象的方法
    cook(): void{
        console.log('做方便面。。。');
    }

    //对象方法
    programTS(){
        console.log('我可以编写 TypeScript');
    }
}
```

> 类实现接口时, 类可以包含比接口更多的属性, 但是接口要求的属性和方法必须要有

#### 5.4.7 接口的继承[了解]

当接口中出现重复结构时，可以对公共部分进行抽离，然后通过继承来简化代码

```typescript
interface BasicInfo{
    name: string,
    age: number,
}

interface BoyFriend extends BasicInfo{
    readonly id: number,
    car ?: string,
    cook: () => void  
}

interface Staff extends BasicInfo{
    programTS: () => void;
}
```

#### 5.4.8 接口的多继承[了解]

```tsx
interface A {
    a: number;
    b: number;
}

interface B{
    c: number;
}


interface D extends A, B{
    d: number;
}
```

#### 5.4.9 接口的重复声明[了解]

接口是允许重复声明的, 变量如果指定为该类型, 必须要将所有同名接口的结构都实现

```jsx
interface Person{
  name: string;
}

interface Person{
  age: number;
}

let me: Person = {
  name: 'xxx',
  age: 18
}
```



### 5.5 泛型

泛型（generic）是 TypeScript 中一个非常重要的特性, 它允许我们编写可以处理多种类型的`通用`代码, 同时还能保持类型的安全性

> 泛型就是可以接收类型的变量

#### 5.5.1 引入

下面创建一个函数, 实现功能: 根据指定的数量 `count` 和数据 `value` , 创建一个包含 `count` 个 `value` 的数组 不用泛型的话，这个函数可能是下面这样：

```js
function createArray (count:number,value:any):any[]{
  const arr:any[] = []
  for (let index = 0; index < count; index++) {
    arr.push(value)
  }
  return arr
}

const arr01 = createArray(3,'hello')
const arr02 = createArray(3,100)

console.log(arr01[0].split('')) //运行不报错，但编码时没有提示
console.log(arr02[0].toFixed(3)) //运行不报错，但编码时没有提示
console.log(arr02[0].split('')) //运行报错，但编码时没有提示错误 
```

#### 5.5.2 泛型函数

```js
function createArray <P>(count:number,value:P):P[]{
  const arr:P[]= []
  for (let index = 0; index < count; index++) {
    arr.push(value)
  }
  return arr
}

const arr03 = createArray<string>(3,'hello')
const arr04 = createArray<number>(3,100)
console.log(arr03[0].split(''))
console.log(arr04[0].toFixed(1))
console.log(arr04[0].split('')) //error 类型“number”上不存在属性“split”
```



#### 5.5.3 多个泛型参数的函数

一个函数可以定义多个泛型参数

```js
function createArray <T,P> (a: T, b: P): [T, P] {
  return [a, b]
}

const result = createArray<string, number>('abc', 123)
console.log(result[0].length)
console.log(result[1].toFixed())
```

#### 5.5.4 泛型接口

在定义接口时, 为接口中的属性或方法定义泛型类型
在使用接口时, 再指定具体的泛型类型

```tsx
// 声明一个接口
interface Response<T>{
  status: number,
  headers: object,
  data: T,
}

interface Stu{
  id: number,
  name: string,
  age: number,
}

interface Book{
  id: number,
  title: string,
  price: number
}

//一个对象
let response: Response<Book> = {
  status: 200,
  headers: {},
  data: {
    id: 1,
    title: '西游记',
    price: 28
  }
}

let response2: Response<Stu> = {
  status: 200,
  headers: {},
  data: {
    id: 1,
    name: 'xx',
    age: 19
  }
}
```

#### 5.5.5 泛型类

在定义类时, 为类中的属性或方法定义泛型类型 在创建类的实例时, 再指定特定的泛型类型

```js
//泛型类
class Container<T>{
  //用于储存数据
  store: T[];
  constructor(store: T[]){
    this.store = store;
  }
}

let books = new Container<Book>([{id: 1, title: '西游记', price: 10}, {id: 2, title: '三国演义', price: 25}])
```

#### 5.5.6 泛型约束

如果我们直接对一个泛型类型参数取 `length` 属性, 会报错, 因为这个泛型根本就不知道它有这个属性

```js
// 没有泛型约束
function fn <T>(x: T): void {
  // console.log(x.length)  // error
}
```

我们可以使用泛型约束来实现

```tsx
interface Lengthwise {
  length: number;
}

// 指定泛型约束
function fn2 <T extends Lengthwise>(x: T): void {
  console.log(x.length)
}

fn2('abc')
// fn2(123) // error  number没有length属性
```

### 5.6 其他 

#### 5.6.1 类型声明

可以使用 type 关键字声明类型别名

```tsx
//1. 类型别名设置
interface Person{
  name: string,
  age: number
}

type Persons = Person[];

//2. 获取某个变量的类型
let me: string = '尚硅谷';
type SchoolType = typeof me;

//3. 获取接口键名的联合类型
function getInfo(obj: Person, key: keyof Person): void{
  obj[key]
}

//4. 获取函数的返回值类型
type retType = ReturnType<typeof getInfo>;
                          
//5. 获取函数参数类型. 返回类型为『元组』类型
type paramsType = Parameters<typeof getInfo>
                          
//6. 获取接口属性的类型
let me:Person['name']; //这里等效于 string
```

#### 5.6.2 声明语句【掌握】

假如我们想使用第三方库 jQuery，一种常见的方式是在 html 中通过 `<script>` 标签引入 `jQuery`，然后就可以使用全局变量 `$` 或 `jQuery` 了。

```js
//变量声明
declare var $:(selector: string) => any;
$('body').css('background','#aef'); 
```

也可以创建一个声明文件名字为 `xxx.d.ts` ,  TS 编译器会扫描并加载项目中所有的 TS 声明文件

```tsx
declare var $:(selector: string) => any;
```

#### 5.6.3 npm 包类型设置

很多的第三方库都定义了对应的声明文件库, 库文件名一般为 `@types/xxx` 

例如 jquery 类型包为 `@types/jquery`

```js
import $ from 'jquery';
$('body').css('background','#aef');
```

#### 5.6.4 内置类型

JavaScript 中有很多内置对象，它们可以直接在 TypeScript 中当做定义好了的类型。

内置对象是指根据标准在全局作用域（Global）上存在的对象。

这里的标准是指 ECMAScript 和其他环境（比如 DOM）的标准。

##### ECMAScript 的内置对象

1. Boolean    
2. Number
3. String
4. Date
5. RegExp
6. Error

```tsx
let b: Boolean = new Boolean(1)    // Boolean  boolean
let n: Number = new Number(true)
let s: String = new String('abc')
let d: Date = new Date()
let r: RegExp = /^1/
let e: Error = new Error('error message')
b = true
// let bb: boolean = new Boolean(2)  // error
```

##### BOM 和 DOM 的内置对象

* Window
* Document
* HTMLElement
* DocumentFragment
* Event
* NodeList

```tsx
const div: HTMLElement = document.getElementById('test') as HTMLElement
const divs: NodeList = document.querySelectorAll('div')
document.addEventListener('click', (event: MouseEvent) => {
  console.dir(event.target)
})

const root = reactDOM.createRoot(document.getElementById('root') as HTMLElement)
```



## 六、Webpack 打包 TS 文件

项目中可以借助 webpack 打包工具来直接处理 ts 文件。操作步骤如下：

1. 创建目录结构

   ```
   - src
       - index.ts
   - public
   	- index.html
   ```

2. 安装 webpack 以及相关的工具包

   ```sh
   npm init
   npm i webpack webpack-cli webpack-dev-server ts-loader html-webpack-plugin typescript  -D
   ```

3. src 同级目录下创建配置文件 webpack.config.js

   ```js
   const {resolve} = require('path');
   const HtmlWebpackPlugin = require('html-webpack-plugin')
   
   module.exports = {
       entry: './src/index.ts',
       output: {
           path: resolve(__dirname, 'build'),
           filename: 'js/bundle.js' 
       },
       mode: 'development',
       module: {
           rules: [
               {
                   test: /\.tsx?$/,
                   use: 'ts-loader'
               }
           ]
       },
       resolve: {
           extensions: ['.ts','.tsx','.js']
       },
       plugins: [
           new HtmlWebpackPlugin({
               template: './public/index.html'
           })
       ],
       devServer: {
           port: 3000,
           open: true
       }
   }
   ```

4. 项目根目录下创建 『tsconfig.json』

   ```
   tsc --init
   ```

5. 运行命令

   ```
   npx webpack-dev-server          # 启动开发服务
   npx webpack                     # 打包代码
   ```

   



