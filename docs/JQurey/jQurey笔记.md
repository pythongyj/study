## JQuery
###  jQuery优点
+ 轻量级
+ 隐式迭代
    > 遍历内部DOM元素的过程
    > 简单理解：给匹配到的所有元素进行循环遍历，执行相应的方法，而不用我们再进行循环，简化我们的操作，方便我们调用。
+ 链式编程
+ 兼容性好
+ 支持插件扩展
+ 开源  免费


### 说出DOM对象和jQuery对象的区别

+ DOM对象只能使用js的属性和方法
+ jq只能使用jq的属性和方法

+ 互相转换
    + DOM对象转jq对象${DOM对象}
    + jq对象转DOM对象$('div')[index] index是索引 || $('div').get(index)


### jQurey选择器
+ ${'选择器'}//直接写css选择器

+ 筛选选择器

    $('ls:[first||last||eq(n)||odd||even]') odd索引为奇数 even索引为偶数
+ 筛选方法（重点）
    对象.方法（）
    对象.parent()父级||.parents()父级||.children([参数])子集||.find([参数])后代||.sibings([参数])兄弟，不包含自己||.nextAll()后面的||.prevAll()前面的
    判断是否有某个类名$('div').hasClass('aaa')

    + 添加事件  show([speed,[easing],[fn]])显示hide()隐藏toggle()切换index()获取索引值
    + 
### jQurey样式操作

+ 使用.css([参数])可以是键值对，也可以是对象
+ 设置类样式
    + .addClass('类名');
    + .removeClass()
    + .toggleClass()

### 入口函数

+ 优点 DOM节点渲染完毕即可执行内部代码  不必等到外部资源加载完成
```js
//第一种  jQuery封装   推荐使用
$(function () {   
...  // 此处是页面 DOM 加载完成的入口
}) ;
//第二种    把DOM对象转换为jQUery对象
$(document).ready(function(){
  //  此处是页面DOM加载完成的入口
});    
```

## 重点
### 动画
#### 基本
> show([speed,[easing],[fn]])【显示】
> hide([speed,[easing],[fn]])【隐藏】
> toggle([speed,[easing],[fn]])【切换】

#### 滑动

> slideDown([speed,[easing],[fn]])【下滑效果】
> slideUp([speed,[easing],[fn]])【上滑效果】
> slideToggle([speed,[easing],[fn]])【切换效果】

#### 淡入淡出

> fadeIn([speed,[easing],[fn]])【淡入】
> fadeOut([speed,[easing],[fn]])【淡出】
> fadeToggle([speed,[easing],[fn]])【切换】
> fadeTo([[speed],opacity,[easing],[fn]])【到大某个位置】必须写[speed]参数必须写,opacity 0~1 之间

#### 自定义动画  animate

> animate(params,[speed],[easing],[fn])
> params: 想要更改的样式属性,以对象形式传递，必须写

### jq属性
#### 固有
> 设置或获取元素固有属性值 prop()  元素本身自带的属性
> 获取语法：prop(''属性'')
> 设置属性语法:prop(''属性'', ''属性值'')

#### 自定义  

> 设置或获取元素自定义属性值 attr()
> attr(''属性'')   // 类似原生 getAttribute()
> attr(''属性'', ''属性值'')   //类似原生 setAttribute()

#### 数据缓存 data()【了解】

> 当做变量存储 
> data() 方法可以在指定的元素上存取数据，并不会修改 DOM 元素结构，所以元素上无法查看。一旦页面刷新，之前存放的数据都将被移除
>  附加数据语法: data(''name'',''value'')   // 向被选元素附加数据   
> 获取数据语法: date(''name'')   //   向被选元素获取数据 

### 事件切换

+ hover(fn1,fn2)即hover([over,]out)
+ 如果只写一个函数，则鼠标经过和离开都会触发它

### 停止动画

+.stop()  用于停止动画或效果

### 文本内容值

#### .html()

> 普通元素内容 html()**（相当于原生inner HTML)
> 获取：html()   // 获取元素的内容
> 设置：html(''内容'')   // 设置元素的内容

#### .text()

> 普通元素文本内容 text()   (**相当与原生** innerText**)**
> 获取：text()   // 获取元素的文本内容
> 设置：text(''文本内容'')   // 设置元素的文本内容

#### .val()

> 表单的值 val()**（ 相当于原生value)**
> 获取：val()   // 获取表单的值
> 设置：val(''内容'')  // 设置表单的值

## 元素操作

> 主要是遍历、创建、添加、删除元素操作

### **遍历元素**

jQuery 隐式迭代是对同一类元素做了同样的操作。如果想要给同一类元素做不同操作，就需要用到遍历。

>  语法1：$("div").each(function(index, domEle) { xxx; }）  主要用DOM处理。 each 每一个
>
>  语法2：$.each(object，function(index, element){ xxx;}）主要用于数据处理，比如数组，对象

### **创建**元素

> 语法：**$(' \<li><\/li> ')**; 

### **添加**元素

#### **内部添加**

  + element.append(''内容'') [把内容放入匹配元素内部最后面，类似原生 appendChild。]
  + element.prepend(''内容'') 把内容放入匹配元素内部最前面。

#### **外部添加**

  + element.after(''内容'') // 把内容放入目标元素后面
  + element.before(''内容'')    //  把内容放入目标元素前面 

#### 注意：

  + 内部添加元素，生成之后，它们是父子关系。
  + 外部添加元素，生成之后，他们是兄弟关系。

### **删除元素**

> - element.remove()   //  删除匹配的元素（本身）[元素就不在了]
> - element.empty()    //  删除匹配的元素集合中所有的子节点[内容删除，元素依旧存在]
> - element.html('''')   //  清空匹配的元素内容

#### **注意** ：①remove 删除元素本身。

>   - ②empt() 和  html('''') 作用等价，都可以删除元素里面的内容，只不过 html 还可以设置内容。

## **jQuery** **尺寸、位置操作**

### **jQuery 尺寸**    元素本身的大小

> width()、height()【只算width和height】
>
> innerWidth()、innerHeight()【包含padding+width】
>
> outerWidth()、outerHeight()【包含padding、border、width】
>
> outerWidth(true)、outerHeight(true)【包含padding、border、margin、width】

### **jQuery 位置**

> 位置主要有三个： offset()、position()、scrollTop()/scrollLeft();
>
#### **offset()设置或获取元素偏移**
>   - ①offset() 方法设置或返回被选元素相对于**文档**的偏移坐标，跟父级没有关系。
>   - ②该方法有2个属性 left、top 。offset().top  用于获取距离文档顶部的距离，offset().left 用于获取距离文档左侧的距离。
>   - ③可以设置元素的偏移：offset({ top: 10, left: 30 });
#### **position()** 获取元素偏移**
>   - ①position() 方法用于返回被选元素相对于**带有定位的父级**偏移坐标，如果父级都没有定位，则以文档为准。
>   - ②该方法有2个属性 left、top。position().top 用于获取距离定位父级顶部的距离，position().left 用于获取距离定位父级左侧的距离。
>   - **注意**：该方法只能获取
#### **scrollTop()、scrollLeft()设置**或获取元素被卷去的头部和**左侧**
>   - ①scrollTop() 方法设置或返回被选元素被卷去的头部。
>   - ②不跟参数是获取，参数为不带单位的数字则是设置被卷去的头部。
>   - scroll事件：滚动事件，（谁有滚动条加给谁）

## **jQuery** **事件**

### 目标：

1. 能够说出4种常见的注册事件
2. 能够说出 on 绑定事件的优势
3. 能够说出 jQuery 事件委派的优点以及方式
4. 能够说出绑定事件与解绑事件

### **jQuery**事件

#### 直接绑定
>
>    + 语法：element.事件(function(){})     $(“div”).click(function(){  事件处理程序 })  	
>    + 其他事件和原生基本一致。
>    + 比如mouseover、mouseout、blur、focus、change、keydown、keyup、resize、scroll 等
>
### **事件处理** **on()** **绑定事件**
>
>    + on() 方法在匹配元素上绑定一个或多个事件的事件处理函数
>    + 语法：element.on(events,[selector],fn)
>      + 1. events:一个或多个用空格分隔的事件类型，如"click"或"keydown" 。
>      + 2. selector: 元素的子元素选择器 。 即要委托的目标元素
>      + 3. fn:回调函数 即绑定在元素身上的侦听函数。 
>
#### **on() 方法优势**
>
>    1. 可以绑定多个事件，多个处理事件处理程序。 
>    2. 可以事件委派操作。事件委派的定义就是，把原来加给子元素身上的事件绑定在父元素身上，就是把事件委派给父元素。
>    3. 动态创建的元素，click()没有办法绑定事件，on() 可以给动态生成的元素绑定事件
>
#### **事件处理** **off()** **解绑事件**
>
>    1. off() 方法可以移除通过 on() 方法添加的事件处理程序。
>       1. $("p").off() // 解绑p元素所有事件处理程序
>       2. $("p").off( "click")  // 解绑p元素上面的点击事件 后面的 foo 是侦听函数名
>       3. $("ul").off("click", "li");   // 解绑事件委托
>    2. 如果有的事件只想触发一次， 可以使用 one()来绑定事件。
>
#### **自动触发事件trigger()**
>
>    1. element.click()  // 第一种简写形式
>
>    2. element.trigger("type")//第二种自动触发模式   type表示事件的类型
>
>    3. element.triggerHandler(type)  // 第三种自动触发模式
>
>       > 区别：triggerHandler模式不会触发元素的默认行为，这是和前面两种的区别。

### **jQuery**事件对象

事件被触发，就会有事件对象的产生。【event==》事件对象】

> 语法： element.on(events,[selector],function(event){}) 
>
> 阻止默认行为：event.preventDefault()   或者 return  false 
>
> 阻止冒泡： event.stopPropagation() 
