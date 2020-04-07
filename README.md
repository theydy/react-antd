# react-antd

## 第 2 章

### typescript 究竟是什么

- JavaScript that scales
- 静态类型风格的类型系统
- 从 es6 到 es10 甚至是 esnext 的语法支持
- 兼容各种浏览器，各种系统，各种服务器，完全开源

### 为什么要用 typescript

- 程序更容易理解
  - 问题：函数或者方法输入输出的参数类型，外部条件等
  - 动态语言的约束：需要手动调试等过程
- 效率更高
  - 在不通的代码块和定义中进行跳转
  - 代码自动补全
  - 丰富的接口提示
- 更少的错误
  - 编译期间能够发现大部分错误
  - 杜绝一些比较常见错误
- 非常好的包容性
  - 完全兼容 JavaScript
  - 第三方库可以单独编写类型文件
  - 刘丽霞的项目都支持 typescript
- 一点小缺点
  - 增加了一些学习成本
  - 短期内增加了一些开发成本

### Interface 接口

- 对 对象的形状 (shape) 进行描述
- 对类 (class) 进行抽象
- Duck Typing (鸭子类型)
  - 如果它像鸭子那样的叫、走路，那就可以看作是鸭子
  - 接口更关注对象如何被使用，而不是对象的类型是什么

### class 类

- 类 (Class)：定义了一切事物的抽象特点
- 对象 (Object)：类的实例
- 面向对象 (OOP) 三大特性：封装、继承、多态

### Generics

```js
function echo<T>(arg: T): T {
  return arg;
}
const result = echo(true);
function swap<T, U>(tuple: [T: U]): [U: T] {
  return [tuple[1], tuple[0]];
}
const result2= swap(['str', 123])
```

- 泛型的约束
  - 有这么一个需求：
  - 传入的参数必须得有 length 这个属性

```js
interface IWithLength {
  length: number
}
function echowithLenght<T extends IWithLength>(arg: T): T {
  console.log(arg.length)
  return arg
}
```

- 泛型类和接口

```js
class Queue<T> {
  private data = [];

  push(item: T) {
    return this.data.push(item);
  }

  pop(): T {
    return this.data.shift();
  }
}

const queue = new Queue<number>();
queue.push(1);
// queue.push('str');
console.log(queue.pop().toFixed());
// --------
interface KeyPair<T, U> {
  key: T;
  value: U;
}
let key1: KeyPair<number, string> = {key: 1, value: "str"}
```

- _泛型修饰函数_

```js
interface IPlus<T> {
  (a: T, b: T): T;
}


function plus(a: number, b: number): number {
  return a + b;
}


function connect(a: string, b: string): string {
  return a + b;
}


const a: IPlus<number> = plus;
const b: IPlus<String> = connect;
```

## 第 4 章

### 创建自己组件库的色彩体系

- 系统色板- 基础色板 + 中性色板
- 产品色板 - 品牌色 + 功能色板

### 组件库样式变量分类

- 基础色彩系统
- 字体系统
- 表单
- 按钮
- 边框和阴影
- 可选配置开关
