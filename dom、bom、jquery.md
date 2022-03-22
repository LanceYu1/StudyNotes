### DOM

###### dom的全称是什么？

文档对象模型-document object model

###### dom里面有什么？

1. 获取元素的方法（获取元素的方法）
2. 操作元素
3. 操作css方法
4. 事件

##### DOM选择器（获取元素的方法）

对应jQuery 选择器（获取元素的方法）来看

是什么？![snipaste20220309_140713](C:\Users\俞子青\Desktop\前端笔记\笔记截图\snipaste20220309_140713.png)

有什么区别？

![snipaste20220309_140805](C:\Users\俞子青\Desktop\前端笔记\笔记截图\snipaste20220309_140805.png)

###### 什么是元素？什么是节点？

页面中的所有标签都是元素，DOM 中使用 element 表示

网页中的所有内容都是节点（标签、属性、文本、注释等）

注:节点的范围肯定比元素的范围大，但是获取元素是我们的需求，利用节点层级关系获取元素只是获取元素的一种方法

###### 利用dom提供的方法获取元素

1. 根据 ID 获取

​	 document.getElementById('id');

2. 根据标签名获取

   document.getElementsByTagName('标签名');

3. 根据类名返回元素对象集合

​		document.getElementsByClassName(‘类名’)；

4. 根据指定选择器返回第一个元素对象

   document.querySelector('选择器');

5. 根据指定选择器返回

​		document.querySelectorAll('选择器'); 

6. 获取body元素

   doucumnet.body

7. 获取html元素

   document.documentElement

###### 利用节点层级关系获取元素

node.parentNode ：获取子元素的父元素

parentNode.children：获取父元素的子元素

 parentNode.chilren[0] （parentNode.firstElementChild有兼容性问题）： 返回第一个子元素节点

parentNode.chilren[parentNode.chilren.length - 1] （parentNode.lastElementChild有兼容性问题）：返回最后一个子元素节点

nextElementSibling 返回当前元素下一个兄弟元素节点

node.previousElementSibling返回当前元素上一个兄弟节点

###### 两者的区别

前者是直取：我想得到那个元素，直接找到它

后者是间接取得：我想得到那个元素并不能直接取得，要通过它的父元素或者兄弟元素才能取得

##### 操作元素（增删改查）

和jQuery对应起来

###### 增

1. node.appendChild(child) 
2. node.insertBefore(child, 指定元素) 

###### 删除

 node.removeChild(child) 

###### 改变元素的内容

1. element.innerText

   从起始位置到终止位置的内容,  同时空格和换行也会去掉，如果有html标签，不会渲染到页面中

2. element.innerHTML

   起始位置到终止位置的全部内容，同时保留空格和换行，如果有html标签，会渲染到页面中

###### 创建

 document.createElement('tagName')

###### 复制

 node.cloneNode() 

注意：

1. 如果括号参数为空或者为 false ，则是浅拷贝，即只克隆复制节点本身，不克隆里面的子节点。
2. 如果括号参数为 true ，则是深度拷贝，会复制节点本身以及里面所有的子节点。

##### 操作css方法

![snipaste20220309_191730](C:\Users\俞子青\Desktop\前端笔记\笔记截图\snipaste20220309_191730.png)

#### 事件

##### 事件概述

###### 什么是事件？

![snipaste20220310_143415](C:\Users\俞子青\Desktop\前端笔记\笔记截图\snipaste20220310_143415.png)

总结：事件就是一种行为。比如点击，敲击键盘上的按键

###### 注册事件两种方法

![snipaste20220310_142002](C:\Users\俞子青\Desktop\前端笔记\笔记截图\snipaste20220310_142002.png)

传统注册方式和方法监听注册方式

两者的区别：传统方式同一元素同一事件只能设置一个处理函数，方法监听方式同一元素同一事件可以设置多个处理函数

![snipaste20220316_084251](C:\Users\俞子青\Desktop\前端笔记\笔记截图\snipaste20220316_084251.png)

###### 方法监听方式注册事件的语法

![snipaste20220310_142412](C:\Users\俞子青\Desktop\前端笔记\笔记截图\snipaste20220310_142412.png)
true代表处于捕获阶段，false代表处于冒泡阶段

###### 删除事件的方式

![snipaste20220310_142542](C:\Users\俞子青\Desktop\前端笔记\笔记截图\snipaste20220310_142542.png)

![snipaste20220316_084556](C:\Users\俞子青\Desktop\前端笔记\笔记截图\snipaste20220316_084556.png)

##### 具体事件

###### change事件

当元素的值发生改变时，会发生 change 事件。

```
$('#id').on('change', function(e) {
   alert('监听到了change事件')
})
```

常用于

###### 表单提交事件submit

```
$('#form1').on('submit', function(e) {
   alert('监听到了表单的提交事件')
})

```

注意这是为表单提交的事件

###### 鼠标事件

![snipaste20220311_155028](C:\Users\俞子青\Desktop\前端笔记\笔记截图\snipaste20220311_155028.png)

![snipaste20220311_155459](C:\Users\俞子青\Desktop\前端笔记\笔记截图\snipaste20220311_155459.png)

```
document.addEventListener('contextmenu', function(e) {
e.preventDefault();
})

```

![snipaste20220311_155544](C:\Users\俞子青\Desktop\前端笔记\笔记截图\snipaste20220311_155544.png)

```
   document.addEventListener('selectstart', function(e) {
    e.preventDefault();
   })

```

###### 鼠标的mouseenter 事件和mouseover事件的区别

* 给父盒子添加一个点击事件，mouseover是经过它里面的子盒子会触发一次事件（这是由于冒泡，虽然子盒子并没有绑定事件），经过父盒子还会触发一次事件。
* mouseenter 是只有经过父盒子才能触发事件，而经过子盒子时并不会出发，这是由于mouseenter 没有冒泡所决定的。

###### 常用键盘事件

![snipaste20220311_195052](C:\Users\俞子青\Desktop\前端笔记\笔记截图\snipaste20220311_195052.png)

##### 事件对象

###### 什么是事件对象？

![snipaste20220310_143005](C:\Users\俞子青\Desktop\前端笔记\笔记截图\snipaste20220310_143005.png)

![snipaste20220310_143045](C:\Users\俞子青\Desktop\前端笔记\笔记截图\snipaste20220310_143045.png)

###### e.target和this的区别

![snipaste20220310_184336](C:\Users\俞子青\Desktop\前端笔记\笔记截图\snipaste20220310_184336.png)

举个例子：

![snipaste20220310_184513](C:\Users\俞子青\Desktop\前端笔记\笔记截图\snipaste20220310_184513.png)

##### 事件对象的常见属性和方法

###### 事件对象通用属性和方法

* 这些属性和方法是事件对象所通用的，鼠标和键盘事件对象有其所独有的属性和方法

![snipaste20220310_184555](C:\Users\俞子青\Desktop\前端笔记\笔记截图\snipaste20220310_184555.png)

###### 键盘事件对象所特有的属性和方法

![snipaste20220311_195226](C:\Users\俞子青\Desktop\前端笔记\笔记截图\snipaste20220311_195226.png)

###### 鼠标事件对象所的有的属性和方法

![snipaste20220311_155711](C:\Users\俞子青\Desktop\前端笔记\笔记截图\snipaste20220311_155711.png)

##### 事件、事件对象、事件对象的属性和方法总结

有事件才有事件对象，才有事件对象的属性和方法

##### dom事件流

###### dom事件流是什么？

![snipaste20220310_181743](C:\Users\俞子青\Desktop\前端笔记\笔记截图\snipaste20220310_181743.png)

###### 捕获阶段

一层一层往内找

![snipaste20220310_185813](C:\Users\俞子青\Desktop\前端笔记\笔记截图\snipaste20220310_185813.png)

我点击了son，son中的alert（‘son’）执行理所当然。但是，实际上father中的alert（‘father’）也会执行，这是为什么？因为处于捕获阶段，执行的顺序是document->htnl->body->father->son,father会首先执行

###### 冒泡阶段

一层一层往外翻

![snipaste20220310_190521](C:\Users\俞子青\Desktop\前端笔记\笔记截图\snipaste20220310_190521.png)

冒泡的顺序则正好相反，先是son然后是father，所有先弹出我是son，再弹出我是father

###### 阻止事件冒泡

e.stopPropagation();

![snipaste20220310_190751](C:\Users\俞子青\Desktop\前端笔记\笔记截图\snipaste20220310_190751.png)

组织冒泡之后只会弹出我是son

##### 事件委托

![snipaste20220310_191447](C:\Users\俞子青\Desktop\前端笔记\笔记截图\snipaste20220310_191447.png)

![snipaste20220310_191337](C:\Users\俞子青\Desktop\前端笔记\笔记截图\snipaste20220310_191337.png)

想实现点击一个li就弹出知否知否。。。这句话，根据冒泡的原理，只要给父元素添加点击事件就可以。因为当你点击li的时候，根据冒泡的原理，会依次执行li上的回调函数，再执行ul上的回调函数，虽热li上没有回调函数，但是ul上有啊。

###  BOM

BOM（Browser Object Model）即浏览器对象模型，它提供了独立于内容而与浏览器窗口进行交互的对象，其核心对象是 window。

###### dom和bom的区别

![snipaste20220313_185644](C:\Users\俞子青\Desktop\前端笔记\笔记截图\snipaste20220313_185644.png)

###### bom中有什么？

![snipaste20220313_185740](C:\Users\俞子青\Desktop\前端笔记\笔记截图\snipaste20220313_185740.png)

###### 调整窗口大小事件

![snipaste20220313_190131](C:\Users\俞子青\Desktop\前端笔记\笔记截图\snipaste20220313_190131.png)

##### 定时器	

定时器是window 对象提供的**方法**

###### setTimeout() 定时器

![snipaste20220313_190256](C:\Users\俞子青\Desktop\前端笔记\笔记截图\snipaste20220313_190256.png)

###### 停止 setTimeout() 定时器

![snipaste20220313_191357](C:\Users\俞子青\Desktop\前端笔记\笔记截图\snipaste20220313_191357.png)

######  setInterval() 定时器

![snipaste20220313_191434](C:\Users\俞子青\Desktop\前端笔记\笔记截图\snipaste20220313_191434.png)

###### 停止 setInterval() 定时器

![snipaste20220313_195837](C:\Users\俞子青\Desktop\前端笔记\笔记截图\snipaste20220313_195837.png)

##### 回调函数

![snipaste20220313_190329](C:\Users\俞子青\Desktop\前端笔记\笔记截图\snipaste20220313_190329.png)

##### 按钮的禁用属性？？？

按钮点击之后， 会禁用 disabled 为true

##### js执行机制

###### 同步和异步

同步：前一个任务结束后再执行后一个任务，程序的执行顺序与任务的排列顺序是一致的、同步的。

异步：在做这件事的同时，你还可以去处理其他事情。

###### 同步任务和异步任务

同步任务：同步任务都在主线程上执行，形成一个执行栈。

同步任务有哪些：除了回调函数中的内容，其他都是同步任务。注：回调函数的声明是同步任务，它会被放到执行栈中，只是函数里面的代码不属于同步任务。

异步任务：异步任务相关回调函数添加到任务队列中（任务队列也称为消息队列）。

异步任务的类型：1、普通事件，如 click、resize 等2、资源加载，如 load、error 等3、定时器，包括 setInterval、setTimeout 等

异步任务有哪些：回调函数中的代码都是异步任务。

###### 执行机制

1. 先执行执行栈中的同步任务。
2. 异步任务（回调函数）放入任务队列中。
3. 一旦执行栈中的所有同步任务执行完毕，系统就会按次序读取任务队列中的异步任务，于是被读取的异步任务结束等待状态，进入执行栈，开始执行。

##### location 对象

window 对象给我们提供了一个 location 属性用于获取或设置窗体的 URL，并且可以用于解析 URL 。 因为这个属性返回的是一个对象，所以我们将这个属性也称为 location 对象。

* 该对象用于获取、设置、解析url

###### URL

统一资源定位符 (Uniform Resource Locator, URL)：可以理解为资源所存放的位置

![snipaste20220314_130621](C:\Users\俞子青\Desktop\前端笔记\笔记截图\snipaste20220314_130621.png)

######  location 对象的属性

![snipaste20220314_130821](C:\Users\俞子青\Desktop\前端笔记\笔记截图\snipaste20220314_130821.png)

![snipaste20220317_082002](C:\Users\俞子青\Desktop\前端笔记\笔记截图\snipaste20220317_082002.png)



![snipaste20220320_090849](C:\Users\俞子青\Desktop\前端笔记\笔记截图\snipaste20220320_090849.png)

![snipaste20220320_091457](C:\Users\俞子青\Desktop\前端笔记\笔记截图\snipaste20220320_091457.png)

###### location 对象的方法

![snipaste20220314_134517](C:\Users\俞子青\Desktop\前端笔记\笔记截图\snipaste20220314_134517.png)

![snipaste20220317_082716](C:\Users\俞子青\Desktop\前端笔记\笔记截图\snipaste20220317_082716.png)

* location.assign只有在绑定事件后使用才会记录历史，否则也是没有记录历史的

  ![snipaste20220320_091950](C:\Users\俞子青\Desktop\前端笔记\笔记截图\snipaste20220320_091950.png)

##### navigator 对象

![snipaste20220314_134835](C:\Users\俞子青\Desktop\前端笔记\笔记截图\snipaste20220314_134835.png)

* 可以理解为该对象包含浏览器的一些信息

#####  history 对象

![snipaste20220314_135122](C:\Users\俞子青\Desktop\前端笔记\笔记截图\snipaste20220314_135122.png)

* 就是用代码模拟浏览器的后退和前进功能

![snipaste20220317_083040](C:\Users\俞子青\Desktop\前端笔记\笔记截图\snipaste20220317_083040.png)

![snipaste20220320_092600](C:\Users\俞子青\Desktop\前端笔记\笔记截图\snipaste20220320_092600.png)

##### 元素偏移量 offset 系列

offset 翻译过来就是偏移量， 我们使用 offset 系列相关属性可以动态的得到该元素的位置（偏移）、大小等。

![snipaste20220315_115805](C:\Users\俞子青\Desktop\前端笔记\笔记截图\snipaste20220315_115805.png)

###### offset 系列常用属性

![snipaste20220315_120032](C:\Users\俞子青\Desktop\前端笔记\笔记截图\snipaste20220315_120032.png)

* 什么叫带有定位的父元素？就是说父级有定位，那它的偏移量是根据父级来定的；如果没有定位，那它的偏移量就根据body来定	
* 第一个的意思就是返回它的爸爸（爸爸带有定位）
* ![snipaste20220315_121344](C:\Users\俞子青\Desktop\前端笔记\笔记截图\snipaste20220315_121344.png)

######  offset 与 style 区别 

![snipaste20220315_120329](C:\Users\俞子青\Desktop\前端笔记\笔记截图\snipaste20220315_120329.png)

* 样内式表分为行内样式表、内嵌样式表和外链样式表（这不是就是引入样式表的三种方法吗）

  ![snipaste20220315_120540](C:\Users\俞子青\Desktop\前端笔记\笔记截图\snipaste20220315_120540.png)

  这就是行内样式表

##### 元素可视区 client 系列

client 翻译过来就是客户端，我们使用 client 系列的相关属性来获取元素可视区的相关信息。通过 client 系列的相关属性可以动态的得到该元素的边框大小、元素大小等。

![snipaste20220315_132428](C:\Users\俞子青\Desktop\前端笔记\笔记截图\snipaste20220315_132428.png)

![snipaste20220315_132530](C:\Users\俞子青\Desktop\前端笔记\笔记截图\snipaste20220315_132530.png)

##### 元素 scroll 系列属性

scroll 翻译过来就是滚动的，我们使用 scroll 系列的相关属性可以动态的得到该元素的大小、滚动距离等。

![snipaste20220315_133352](C:\Users\俞子青\Desktop\前端笔记\笔记截图\snipaste20220315_133352.png)

![snipaste20220315_133607](C:\Users\俞子青\Desktop\前端笔记\笔记截图\snipaste20220315_133607.png)

##### offset和client的区别

前者包含边框，后者不包含边框

##### 三大系列区别

![snipaste20220315_134430](C:\Users\俞子青\Desktop\前端笔记\笔记截图\snipaste20220315_134430.png)

##### 立即执行函数

(function() {})()  或者 (function(){}())

不需要调用直接执行

##### 动画函数？？？？

##### 节流阀

![snipaste20220317_083756](C:\Users\俞子青\Desktop\前端笔记\笔记截图\snipaste20220317_083756.png)

##### 移动端网页特效

###### 触屏事件

![snipaste20220316_175446](C:\Users\俞子青\Desktop\前端笔记\笔记截图\snipaste20220316_175446.png)

* 可以类比于pc端中的鼠标事件记忆。鼠标相当于人的手指

  ![snipaste20220316_175818](C:\Users\俞子青\Desktop\前端笔记\笔记截图\snipaste20220316_175818.png)

###### 触摸事件对象

![snipaste20220316_180647](C:\Users\俞子青\Desktop\前端笔记\笔记截图\snipaste20220316_180647.png)

###### 移动端拖动元素

![snipaste20220316_180813](C:\Users\俞子青\Desktop\前端笔记\笔记截图\snipaste20220316_180813.png)

##### 轮播图

###### Swiper 插件

中文官网地址： https://www.swiper.com.cn/

* 要注意不同版本啊，每个版本引入的相关文件都会变的，要引入对应版本的文件
* 似乎它的父级要给确定的高和宽，这不确定，有待以后的认证
* 引入什么样式，什么js，要查看它的网页源代码去一点点复制，否则结果出不来
* 样式能写最顶上就写最顶上，因为怕他被覆盖

###### 其他移动端常见插件 

superslide： http://www.superslide2.com/

 iscroll： https://github.com/cubiq/iscroll

##### 移动端视频插件

zy.media.js

##### 散点

###### innerHTML 效率要比 creatElement 高

###### 阻止链接跳转

javascript:;

###### focus()方法

![snipaste20220311_200901](C:\Users\俞子青\Desktop\前端笔记\笔记截图\snipaste20220311_200901.png)

![snipaste20220317_084207](C:\Users\俞子青\Desktop\前端笔记\笔记截图\snipaste20220317_084207.png)

##### 本地存储

![snipaste20220321_145129](C:\Users\俞子青\Desktop\前端笔记\笔记截图\snipaste20220321_145129.png)

###### window.sessionStorage

![snipaste20220321_152526](C:\Users\俞子青\Desktop\前端笔记\笔记截图\snipaste20220321_152526.png)

###### window.localStorage

![snipaste20220321_153523](C:\Users\俞子青\Desktop\前端笔记\笔记截图\snipaste20220321_153523.png)



### jquery

###### 为什么要有jquery？

对js语法的进一步简化

###### 什么是jQuery？

是一个js库

###### 什么是JavaScript库？

简单理解： 就是一个JS 文件，里面对我们原生js代码进行了封装，存放到里面。这样我们可以快速高效的使用这些封装好的功能了。

###### jQuery的下载

官网地址： https://jquery.com/

###### jQuery的使用

1. 引入 jQuery 文件

2. 使用即可

######  jQuery 的入口函数

$(function () {   
    ...  // 此处是页面 DOM 加载完成的入口
 }) ;

为什么要有入口函数？

因为要等网页html和css加载完之后才开始执行js，假设没加载完就执行js，那怎么可能会出效果啊

###### $=jQuery=window

###### DOM 对象与 jQuery 对象之的相互转换

![snipaste20220309_144835](C:\Users\俞子青\Desktop\前端笔记\笔记截图\snipaste20220309_144835.png)

###### DOM对象类型和jQuery对象类型

###### jQuery 选择器（获取元素的方法）

 jQuery 选择器

![snipaste20220309_145237](C:\Users\俞子青\Desktop\前端笔记\笔记截图\snipaste20220309_145237.png)

![snipaste20220309_145307](C:\Users\俞子青\Desktop\前端笔记\笔记截图\snipaste20220309_145307.png)

![snipaste20220309_145452](C:\Users\俞子青\Desktop\前端笔记\笔记截图\snipaste20220309_145452.png)

###### ：checked

![snipaste20220310_201721](C:\Users\俞子青\Desktop\前端笔记\笔记截图\snipaste20220310_201721.png)

![snipaste20220310_202040](C:\Users\俞子青\Desktop\前端笔记\笔记截图\snipaste20220310_202040.png)

###### jQuery 筛选方法

![snipaste20220309_145625](C:\Users\俞子青\Desktop\前端笔记\笔记截图\snipaste20220309_145625.png)

###### 隐式迭代

简单理解：给匹配到的所有元素进行循环遍历，执行相应的方法，而不用我们再进行循环，简化我们的操作，方便我们调用。

![snipaste20220313_150912](C:\Users\俞子青\Desktop\前端笔记\笔记截图\snipaste20220313_150912.png)

######  jQuery 里面的排他思想

$(this).css(“color”,”red”);
$(this).siblings(). css(“color”,””);

##### 设置或获取元素属性值 

###### 设置或获取元素固有属性值

所谓元素固有属性就是元素本身自带的属性，比如 <a> 元素里面的 href ，比如 <input> 元素里面的 type。 

![snipaste20220310_192404](C:\Users\俞子青\Desktop\前端笔记\笔记截图\snipaste20220310_192404.png)

###### 设置或获取元素自定义属性值

用户自己给元素添加的属性，我们称为自定义属性。 比如给 div 添加 index =“1”。 

![snipaste20220310_192451](C:\Users\俞子青\Desktop\前端笔记\笔记截图\snipaste20220310_192451.png)

###### 数据缓存 data()

![snipaste20220310_203308](C:\Users\俞子青\Desktop\前端笔记\笔记截图\snipaste20220310_203308.png)

##### 元素操作

###### 创建元素

**1.创建一个不依附于其他元素的元素（独立元素）**

![snipaste20220314_135540](C:\Users\俞子青\Desktop\前端笔记\笔记截图\snipaste20220314_135540.png)

* 这个使用场景是什么？是在你需要一个**<li></li>**，在往这个li中添加内容的时候才有用；如果单纯是想向一个盒子（比如一个div）中添加一个li,肯定不会用这种方式，这种方式多麻烦。先要创建一个元素，还要用append方法或者html方法向div中添加这个元素。这种情况直接向html中写一个字符串就好了，html会自动识别标签的。代码示例如下：

  ![snipaste20220317_132236](C:\Users\俞子青\Desktop\前端笔记\笔记截图\snipaste20220317_132236.png)

**1.创建一个依附于其他元素的元素**

* html()
* append/prepend/before/after

######  增

![snipaste20220314_135634](C:\Users\俞子青\Desktop\前端笔记\笔记截图\snipaste20220314_135634.png)

* 这也能添加字符串，能添加对象，也能识别标签，还不会覆盖原来的内容。

![snipaste20220314_135658](C:\Users\俞子青\Desktop\前端笔记\笔记截图\snipaste20220314_135658.png)

**3.html()**

**4.上述方法的主要区别**

html会覆盖原有数据，其他的不会

###### 删除

![snipaste20220314_135809](C:\Users\俞子青\Desktop\前端笔记\笔记截图\snipaste20220314_135809.png)

remove哪个元素调用它，哪个元素本身就被删除了，别提里面的元素了；

emty哪个元素调用它是把它里面的子元素给删除，自己本身并不受影响；

######  改/查

![snipaste20220311_204145](C:\Users\俞子青\Desktop\前端笔记\笔记截图\snipaste20220311_204145.png)

* **html()中只能放一个对象，两个对象都不行**见示例：

  ![snipaste20220316_204831](C:\Users\俞子青\Desktop\前端笔记\笔记截图\snipaste20220316_204831.png)

* **虽然语法规定是html('内容')，但li是一个对象，就不用加引号**,见示例代码

  ![snipaste20220316_204919](C:\Users\俞子青\Desktop\前端笔记\笔记截图\snipaste20220316_204919.png)

* html()会完全覆盖原有的内容

* html可进行增删改查操作

* 即使你原先是数字型，但你一放进之后就变字符串了

![snipaste20220311_204228](C:\Users\俞子青\Desktop\前端笔记\笔记截图\snipaste20220311_204228.png)

* 表单有哪些你要清楚，不清楚就看html的笔记

* 表单不通过这个方法是根本拿不到值的

###### 总结

* 似乎数字只要是加入盒子中再取出来就会变成字符串形式，不管你是用apped,还是html

##### 遍历元素

###### $('元素').each

![snipaste20220314_084418](C:\Users\俞子青\Desktop\前端笔记\笔记截图\snipaste20220314_084418.png)

能够遍历数组

第二个参数是dom对象，不是jQuery对象，想要用jQuery方法的话要转成jQuery对象

###### $.each

![snipaste20220314_084700](C:\Users\俞子青\Desktop\前端笔记\笔记截图\snipaste20220314_084700.png)

也能遍历数组

###### for in 

是什么？

​	是一个遍历对象的工具

数组不太好遍历

怎么用？

 	for(var k in obj) { 
 	//k 得到的是属性名
 	//obj是所遍历的对象
 	//obj[k] 得到是属性值
 	}

具体的执行过程：

```
        var datas = [{
            name: '魏璎珞',
            subject: 'JavaScript',
            score: 100
        }, {
            name: '弘历',
            subject: 'JavaScript',
            score: 98
        }, {
            name: '傅恒',
            subject: 'JavaScript',
            score: 99
        }, {
            name: '明玉',
            subject: 'JavaScript',
            score: 88
        }, {
            name: '大猪蹄子',
            subject: 'JavaScript',
            score: 0
        }];

```

假设有这么一个数组，用for in来遍历它，for(var k in datas[i]) { }

首先它会便利第一个对象，即data是[0],也就是{
            name: '魏璎珞',
            subject: 'JavaScript',
            score: 100
        }

然后再遍历这个对象当中的属性，依次为name，subject，score

上述过程执行完之后，再按上述过程遍历第二个对象

注：我觉得遍历一次是一次大循环和三次小循环的组合

```
            for (var k in datas[i]) { //k是属性，datas[i][k]得到的是k属性对应的属性值
                var tmp = datas[i][k]; //得到了属性
                console.log(tmp);
                console.log('hello');
            }
            
            
```

得到的结果：

![snipaste20220309_134650](C:\Users\俞子青\Desktop\前端笔记\笔记截图\snipaste20220309_134650.png)

也就是说我遍历一个对象，因为里面有三个属性，所以我对每个属性遍历一次，每个属性遍历一次就得到一个hello

##### 操作css方法

![snipaste20220309_191945](C:\Users\俞子青\Desktop\前端笔记\笔记截图\snipaste20220309_191945.png)

###### 设置类样式方法

![snipaste20220309_192126](C:\Users\俞子青\Desktop\前端笔记\笔记截图\snipaste20220309_192126.png)

注：原生 JS 中 className 会覆盖元素原先里面的类名。
jQuery 里面类操作只是对指定类进行操作，不影响原先的类名。

##### jQuery 尺寸操作

![snipaste20220315_135335](C:\Users\俞子青\Desktop\前端笔记\笔记截图\snipaste20220315_135335.png)

##### jQuery 位置操作

类比于原生的offset系列、client系列和scroll系列

![snipaste20220315_135815](C:\Users\俞子青\Desktop\前端笔记\笔记截图\snipaste20220315_135815.png)

![snipaste20220315_140010](C:\Users\俞子青\Desktop\前端笔记\笔记截图\snipaste20220315_140010.png)

![snipaste20220315_140131](C:\Users\俞子青\Desktop\前端笔记\笔记截图\snipaste20220315_140131.png)

##### 事件注册

###### 单个事件注册

![snipaste20220316_192742](C:\Users\俞子青\Desktop\前端笔记\笔记截图\snipaste20220316_192742.png)

###### 多个事件注册

![snipaste20220316_193443](C:\Users\俞子青\Desktop\前端笔记\笔记截图\snipaste20220316_193443.png)

###### 可以事件委派操作+可以给动态生成的元素绑定事件 

![snipaste20220316_193819](C:\Users\俞子青\Desktop\前端笔记\笔记截图\snipaste20220316_193819.png)

![snipaste20220316_205604](C:\Users\俞子青\Desktop\前端笔记\笔记截图\snipaste20220316_205604.png)

![snipaste20220319_101219](C:\Users\俞子青\Desktop\前端笔记\笔记截图\snipaste20220319_101219.png)

* 注意这个this指向的是del，不是tb
* 在事件委托的时候要加上委托的元素（del）