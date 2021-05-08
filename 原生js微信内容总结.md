## js微信内容总结

### 原生js基本内容

#### 1.  js中undefined的几种情况

+ 变量声明且没有赋值；
+ 获取对象中不存在的属性时；
+ 函数需要实参，但是调用时没有传值，形参是undefined；
+ 函数调用没有返回值或者return后没有数据，接收函数返回的变量是undefined。

#### 2. js中的return

<img src="C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20210501195409023.png" alt="image-20210501195409023" style="zoom:80%;" />

+ return 的本意其实是退出函数的运行，如果return后面值的话，那么会在退出的同时，返回一个结果
+ .这里的var n=1是if外的全局变量，所以当运行else语句后会将n=1的值return返回
+ if内的var n=2是if内的变量，当其声明时，会把声明提升至当前作用域的顶部，也到了if外全局变量的位置
+ 由此可得出结论，if内外声明变量的都是在当前作用域的顶部，所以，函数return都可以得到值

#### 3. js中函数中的return及未声明赋值变量问题

![image-20210501200109602](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20210501200109602.png)

> 1、对于未声明的变量直接赋值，那么js会自动在全局声明
>
> 2、函数中没有return ，运行的函数拿不到任何结果

#### 4. 值和表达式

> 值和表达式是一个意思

#### 5. 闭包

+ **闭包的理解**
  1. 闭包的理解，是使用嵌套内部的函数的一种方法
  2. 概念：函数使用了不属于自己的局部变量，这种结构叫闭包（函数套函数）
  3. 作用：保护变量的/避免全局污染
  4. 性能问题：内存泄漏作用域中的局部变量一直被使用着，导致该作用域释放不掉
  5. javascript语言的特别之处就在于：函数内部可以直接读取全局变量，但是在函数外部无法读取函数内部的局部变量 ,就是利用此种特性
  
  

![image-20210501201043583](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20210501201043583.png)

> 案例总结：
>
> + **f1、f2、f3**为**foo**函数创建的三个函数实例，它们都指向**function(){console.log(i++)}**这个匿名函数，它们都是重新调用函数并赋值得到
>
> + 拿f1举例，第一次调用**f1()** 此时**i=0**参与运算，打印出结果为**0** 然后再加1赋值，调用完成后**i=1**
>
> + 第二次调用**f1()** 此时 **i=1** 参与运算，打印出结果为 **1** 然后再加1赋值，调用完成后 **i=2**



#### 6. 对象的属性名为变量情况

![image-20210501203158291](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20210501203158291.png)

> + 属性名如果想要是变量的话，就得给属性名套上中括号，就代表一个属性名是个变量，可以被赋值替代，改变属性名
> + for循环中遍历的key是个变量，所以得用中括号进行取值

#### 7. js中的join方法和split方法

```javascript
var arr = ['xiaoming',1,'xiaohong']
    arr = arr.join()   // join方法是将数组转化为字符串
    console.log(arr)  // xiaoming,1,xiaohong

    var a = "hello world"
    b = a.split("l")  // split方法是将字符串分割成数组
    console.log(b)  // ["he", "", "o wor", "d"]

```

> join()方法 是将数组拼接为字符串
>
> + 如果一个元素 undefined 或 null , 它会被转换成空字符串
>
> split()方法 是将字符串分割成数组

##### 7.1 for...of 无法修改原数组的情况

```javascript
var arr = 'you can you up';

a = arr.split(' ')  // ["you", "can", "you", "up"]

for (var i = 0; i < a.length; i++) {
	a[i] = a[i][0].toUpperCase() + a[i].substring(1)
}
 var str = a.join(' ')
 console.log(str) // You Can You Up

// 若是利用for...of则无法修改原数组
for(var i of a){
 i = i[0].toUpperCase()+i.substring(1)
}
console.log(a) // you can you up
```

> 这次的案例进行split()和join()方法的应用
>
> 并证明了for...of无法修改原数组

#### 8. 数组去重的方法

>+ 一、 es5方法 + splice去重

```javascript
var arr = [12,53,56,12,89,53]

for(var i = 0;i<arr.length;i++){
  for(var j = i+1;j<arr.length;j++){
    if(arr[i]==arr[j]){
      arr.splice(j,1);
      j--;
    }
  }
}
console.log(arr) // [12, 53, 56, 89]
```

> - 二、indexOf + for ... of

```javascript
var b = [];
for(var i of arr){
  if(b.indexOf(i)==-1){
    b.push(i)
  }
}
console.log(b) // [12, 53, 56, 89]
```

>- 三、indexOf + filter

```javascript
var b = [];
b = arr.filter((item, index) => {
  return arr.indexOf(item) == index
})
console.log(b) // [12, 53, 56, 89]
```

> - 四、数组遍历 + indexOf

```javascript
var b = [];
for(var i=0;i<arr.length;i++){
  if(arr.indexOf(arr[i]) == i){
    b.push(arr[i])
  }
}
console.log(b) // [12, 53, 56, 89]
```

> - 五、ES6  new Set()

```javascript
[...new Set(arr)]
```

#### 9. 正则表达式

```javascript
var patt = /e/;
patt.test('The best things in life are free!')  //true
```

> test() 方法是一个正则表达式的方法
>
> test() 方法用于检测某一个字符串是否匹配某个模式，如果字符串中含有匹配的文本，则返回true,
>
> 否则返回false

#### 10. 匿名函数的使用问题

> - 关于采取不采取匿名函数，就看它是否只用一次。若使用多次就考虑封装到一个函数里面

#### 11. 原型对象

![image-20210503011254272](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20210503011254272.png)

> - 原型(prototype)：方法背后，专门保存由方法创建出来的对象的共有属性
> - 通过构造函数的形式 new Date() new Array() new Object() new RegExp()构造函数/对象模板：专门用来创建相同结构对象的专门方法
> - new关键字做了哪几件事？
>   - 创建了一个空对象 var ll={}
>   - 改变this指向 call apply
>   - 给这个对象添加属性和方法
>   - 返回这个对象
> - 共有属性：由同一构造函数创建出来的对象共同享有的属性 
>   - 构造函数.prototype.属性名=属性值添加的属性
> - 自有属性：属于对象实例私有的属性任何对象没有权利修改原型中的属性
> - 继承：使用现有类型，创建出新的类型，新的类型可以使用现有类型的属性和方法，也可以拓展出现有类型没有的属性和方法
> - 原型链
>   - Function 代表的是所有函数的父类
>   - \__proto__:隐式原型。 任何一个对象都有隐式原型，用来实现继承的
>   - 一个对象的隐式原型默认指向创建该对象的构造函数的原型对象

#### 12. 如何更改placeholder属性中文字颜色

```css
<style>
  input::-webkit-input-placeholder{
    color:red;
  }
  input::-moz-placeholder{   /* Mozilla Firefox 19+ */
    color:red;
  }
  input:-moz-placeholder{    /* Mozilla Firefox 4 to 18 */
    color:red;
  }
  input:-ms-input-placeholder{  /* Internet Explorer 10-11 */ 
    color:red;
  }
</style>
```

> - 因为每个浏览器的CSS选择器都有所差异，所以需要针对每个浏览器做单独的设定(可以在冒号前面写input和textarea)

#### 13. addEventListener和removeEventListener

> - document.removeEventListener() 方法用于移除由 document.addEventListener() 方法添加的事件句柄。
> - [_注意: 如果要移除事件句柄，addEventListener() 的执行函数必须使用外部函数，如上实例所示 (myFunction)。_]
>   - 匿名函数，类似 "document.removeEventListener("event", function(){ myScript });" 该事件是无法移除的。







### 原生Dom

#### 1. querySelector

```html
<div>
  <div id='box'></div>
</div>
```

```javascript
const box = document.querySelector('#box')
console.log(box) // <div id='box'></div>
```

> - querySelector()  参数为dom元素的css选择器

#### 2. 事件触发的两种方式

```html
<div onclick='foo()'></div>
```

```javascript
function foo(){
  alert(1)
}
```

> - 第一种方式 是 直接将定义的函数在开始标签中调用

```html
<div id='btn'>你好</div>
```

```javascript
function foo(m){
	alert(m)
}
var btn = document.getElementById('btn')

// btn.onclick = foo(5)  此种情况在未点击情况下直接调用foo函数

btn.onclick = function(){
  foo(5)
}
```

> - 第二种方式 是 在script标签中调用。
> - 这里有个匿名函数的使用，这里的使用是为了满足点击后才执行foo函数的调用
>   1. 点击后执行匿名函数
>   2. foo(5)函数的调用执行

#### 3. 缩小查询范围情况

> - document是从整个页面去找这个元素，document是整个页面的对象。
> - 如果不想从整个页面去找，也可以缩小范围从获取的到的对象调用getElementby…获取它下面的子集的元素。
> - 例如 **lists.getElementById('box')** 查询 **lists** 元素对象中的 **id** 名为 **box** 的元素

#### 4. RegExp对象只能使用一次的问题

> ? 这还真是个问题啦

#### 5. document.defaultView.getComputedStyle()

```html
<div id="box" style="color: red;">
    你好
  </div>
```

```javascript
var box = document.getElementById('box')
var cssStyle = document.defaultView.getComputedStyle(box,null) // cssStyle包含所有的样式
console.log(cssStyle.width) // 200px
console.log(box.style.color) //red 获取到开始标签上的属性值
```

> - 如何取到当前dom元素的外部样式？
>
>   1. document.defaultView.getComputedStyle(box,null)  其中第一个参数传递的是获取到的元素对象 
>
>   第二个参数传递的是null固定搭配
>
>   ​	2.  按上例中的cssStyle.width（或其他属性）取得外部样式的值
>
> - 如何获取到当前dom元素的开始标签内设置的样式？
>
>   1.  对象.style.属性名

#### 6. 定时器

##### 6.1 setTimeout

##### 6.2 setInterval

#### 7. for循环和事件结合引发的问题

```javascript
var divs = document.getElementById('div')

for(var i=0;i<divs.length;i++){
  // 在执行onclick事件之前for循环已经完成了 i打印的只能是最终的结果
  divs[i].onclick=function(){
    console.log(i)
  }
}
```

```javascript
for(let i = 0;i<divs.length;i++){
  // 用es6中的let可以满足我们想要的结果
	divs[i].onclick=function(){
    console.log(i)
  }
}
```

> - 问题点：
>   - 在执行onclick事件之前for循环已经完成了, i打印的只能是最终的结果
> - 解题方法：
>   - 利用es6中的let 块级作用域的特点-->每次递加都会生成一个块级作用域

#### 8. 事件委托

> 将要绑定给子元素的事件绑定给父元素，在子元素执行后，通过事件的冒泡原理，执行父元素的绑定的事件程序
>
> 好处： 通过动态创建的子元素，不用再次绑定事件，通过事件委托触发效果

