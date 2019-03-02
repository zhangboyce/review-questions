#### 1. 请阐述JavaScript中instanceof关键字的作用。
参考：在js中，instanceof关键字是用来判断某个Function的prototype属性是否存在于被判断的对象的原型链上。
在js中，所有的值，对象都是通过function构建而来，function的prototype属性是提供给由它所构建的值的__proto__属性引用的。
所以说，如果某个function的prototype属性存在于另外一个对象的原型链上，我们就视为这个对象是由该function构建而来，所以该对象instanceof该function。

#### 2. 简述什么是对象自身属性以及可枚举属性。分别回答for ... in 循环，Object.keys以及Object.hasOwnProperty方法分别处理的是什么类型的属性。

#### 3. 简述一下ES6中新增的关键字let/const的作用以及与关键字var的区别。

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

#### 7. nodejs文件读写的同步api是怎么实现的？