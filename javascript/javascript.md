#### 1. 请阐述JavaScript中instanceof关键字的作用。
参考：在js中，instanceof关键字是用来判断某个Function的prototype属性是否存在于被判断的对象的原型链上。
在js中，所有的值，对象都是通过function构建而来，function的prototype属性是提供给由它所构建的值的__proto__属性引用的。
所以说，如果某个function的prototype属性存在于另外一个对象的原型链上，我们就视为这个对象是由该function构建而来，所以该对象instanceof该function。

#### 2. 简述什么是对象自身属性以及可枚举属性。分别回答for ... in 循环，Object.keys以及Object.hasOwnProperty方法分别处理的是什么类型的属性。
参考：
a. 对象自身属性是指那些对象拥有的但是不是从原型链继承而来的属性；<br />
b. 对象可枚举属性是指那些内部"可枚举"标志设置为true的属性，对于直接赋值和初始化的属性默认为true，对于通过Object.defineProperty等定义的属性默认为false；<br />
c. for ... in 循环遍历对象的所有可枚举属性；  <br />
d. Object.keys 获取所有可枚举且是自身的属性；<br />
e. Object.hasOwnProperty 判断属性是否为对象自身的属性，包括可枚举和不可枚举。<br />

#### 3. 简述一下ES6中新增的关键字let/const的作用以及与关键字var的区别。
a. let/const声明的变量具有块级别的作用域，var声明的变量是function级别的作用域；
```
{
  let a = 10;
  var b = 1;
}

a // ReferenceError: a is not defined.
b // 1
```
b. let/const声明的变量不存在变量提升，var声明的变量存在变量提升；
```
// var 的情况
console.log(foo); // 输出undefined
var foo = 2;

// let 的情况
console.log(bar); // 报错ReferenceError
let bar = 2;
```
c. 只要块级作用域内存在let/const命令，它所声明的变量就“绑定”（binding）这个区域。
```
var tmp = 123;
if (true) {
  tmp = 'abc'; // ReferenceError
  let tmp;
}
```
d. const声明一个只读的常量。一旦声明，常量的值就不能改变。
```
const PI = 3.1415;
PI // 3.1415

PI = 3;
// TypeError: Assignment to constant variable.
```
const实际上保证的，并不是变量的值不得改动，而是变量指向的那个内存地址所保存的数据不得改动。对于简单类型的数据（数值、字符串、布尔值），值就保存在变量指向的那个内存地址，因此等同于常量。但对于复合类型的数据（主要是对象和数组），变量指向的内存地址，保存的只是一个指向实际数据的指针，const只能保证这个指针是固定的（即总是指向另一个固定的地址），至于它指向的数据结构是不是可变的，就完全不能控制了。因此，将一个对象声明为常量必须非常小心。
```
const foo = {};

// 为 foo 添加一个属性，可以成功
foo.prop = 123;
foo.prop // 123

// 将 foo 指向另一个对象，就会报错
foo = {}; // TypeError: "foo" is read-only

```

#### 4. 在js中使用new关键字调用一个function的时候，js内部大概做了哪些事情？
参考：
1. 创建一个object；
2. 处理原型链，即将object的__proto__属性指向该function的prototype属性（如果该prototype是一个object，否则直接指向Object的prototype属性）。
3. 调用该function的call方法并将该object作为其参数，那么function内部的this变量就讲是该object并且赋值。
4. 一般情况返回object，除非function内部显示返回了其他的object类型的值。

#### 5. apply, call和bind有什么区别？
参考：三者都可以把一个函数应用到其他对象上，注意不是自身对象．apply,call是直接执行函数调用，bind是绑定，执行需要再次调用．apply和call的区别是apply接受数组作为参数，而call是接受逗号分隔的无限多个参数列表。

#### 6. 列举数组相关的常用方法。
参考： push/pop, shift/unshift, split/join, slice/splice/concat, sort/reverse, map/reduce, forEach, filter

#### 7. 实现Array​.prototype​.flat()函数的功能，将数组[1,2,3,[1,2,3,4, [2,3,4]]]展开。
```
function flattenDeep(arr1) {
   return arr1.reduce((acc, val) => Array.isArray(val) ? acc.concat(flattenDeep(val)) : acc.concat(val), []);
}
flattenDeep(arr1);
```
```
function flatten(input) {
  const stack = [...input];
  const res = [];
  while (stack.length) {
    // 使用 pop 从 stack 中取出并移除值
    const next = stack.pop();
    if (Array.isArray(next)) {
      // 使用 push 送回内层数组中的元素，不会改动原始输入 original input
      stack.push(...next);
    } else {
      res.push(next);
    }
  }
  // 使用 reverse 恢复原数组的顺序
  return res.reverse();
```

## 技术类

### 一、JavaScipt
#### 1、Javascript如何实现继承（es5、es6）
#### 2、比较两个对象
#### 3、对象的深拷贝
#### 4、使用requestAnimationFrame制作一个动画效果
#### 5、写一个数组去重的方法
#### 6、event中target与currentTarget的区别、事件代理
#### 7、call、apply、bind的区别
#### 8、常见的内存泄漏原因
#### 9、require/exports和import/export的区别

### 二、Vue
#### 1、代码实现数据劫持
#### 2、描述一下虚拟DOM
#### 3、Vuex中actions和mutations的区别
#### 4、Vue-router与location的区别
#### 5、Vue-router如何传递参数
#### 5、WebPack多文件入口配置

### 三、优化
#### 1、网站优化可以采取的几种方法
#### 2、WebPack优化
#### 3、描述强缓存与协商缓存
#### 5、浏览器打开网站的几个阶段

### 四、服务端
#### 1、描述一下 Cache Aside 更新模式

### 五、测试
#### 1、Chrome DevTools中`Preserve Log`选项的优缺点
#### 2、Selenium 如何绕过 `Element is not clickable`

## 业务类
