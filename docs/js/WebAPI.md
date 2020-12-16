# WebAPI
## DOM document object model 文档对象模型

  + 把整个网页当做一个对象
  + dom树：浏览器把文档转换为dom树   每个节点都是一个对象  称为节点对象
  + 节点对象分类：文档   元素  文本  属性  注释等

## 获取元素

  + document.body 获取body标签
  + document.getElementById('id名');通过id获取标签   获取一个
  + document.getElementByTagName('标签名');通过标签名获取标签 可以获取多个
  + document.querySelector('选择器');通过选择器获取相同选择器的第一个标签
  + document.querySelectorAll('选择器');通过选择器获取一组标签   返回的是伪数组

## 事件-->与用户进行交互的动作

### 事件三要素

**事件源   事件类型  事件处理程序(this：指向当前事件源)**

### 注册事件：

  + 语法：事件源.事件类型=function(){事件处理程序}
  + 事件源：触发事件的元素
  + 事件类型：本质是给事件源的某个事件属性  将要出发的事件类型
  + 事件处理程序：事件函数   本质是将事件函数赋值给事件源上的某个事件属性

## 操作元素属性

本质：改变属性
  + 获取：元素.属性
  + 设置：元素.属性=值

## innerHTML与innerText的区别

  + innerHTML:若有子标签,会包含文本和子标签
  + innerText：仅仅包含文本  若有子标签  会被当成字符串渲染


## 表单属性

  + checked true选中  false不选中
  + disabled true禁用   false不禁用
  + selected true默认选中  false不选中

## 自定义属性  两种方式

### 标签上添加

  + 获取属性：元素.自定义属性名
  + 设置属性：元素.自定义属性=值

### 在原型（DOM树）上添加

  + 获取属性：元素.getAttribute()
  + 设置属性：元素.setAttribule()
  + 移除属性：元素.removeAttribute()


## 样式属性操作

  + 两种方式
    + 行内样式
      + 元素.style.样式属性=值
    + 修改类名
      + className
        + 元素.className='类名' 
        + 会覆盖原来的类，即清除所有类  加上添加的类
      + classList
        + 添加类
          + 元素.classList.add('类名');
        + 删除类
          + 元素.classList.remove('类名');
        + 切换类
          + 元素.classList.toggle('类名');类名存在就移除  不存在就添加


## 排他思想

**先使用for循环将所有样式清除，在设置当前(单独、独立)的样式**

## 节点层级

  + 父节点  parentNode(当前节点)返回元素父节点
  + 子节点  
    + 元素.children返回元素节点
    + 元素.childNode返回所有节点
    + 元素.firstElementChild(父节点) 返回第一个节点
    + 元素.lastElementChild(父节点)返回最后一个节点
  + 兄弟节点
    + 元素.NextElementSibling(当前节点)下一个兄弟节点
    + 元素.previousElementSibling(当前节点)上一个兄弟节点

## 节点属性

  + nodeType：节点类型  返回值：元素-->1  文本-->3
  + nodeName：节点名称  返回值：元素-->打写的标签名  文本-->#text
  + nodeValue：节点值   返回值：元素-->null  文本-->文本的内容

## 创建元素

  + 需求  场景：需要往页面动态添加元素时

  + 三种创建方式
    + innerHTML创建页面元素
      + 语法：元素.innerHTML='内容'

    + createElement()创建页面元素
      + document.createElement("标签名")返回一个新的元素对象
    + document.write() 了解 不用  因为会重绘页面

    + *比较*：innerHTML在追加多个元素时执行速度慢，性能差，不推荐使用。根本原因在于**字符串的不可变性**
    + createElement方法执行速度快，性能高，在实际开发中**推荐使用**

## 追加元素

  + 父元素.appendChild(子元素)

## 删除元素

  + 父元素.removeChild(子元素)

## 插入元素

  + 父节点.insertBefore(新的节点，旧的子节点)

## 替换元素

  + 父节点.replaceChild(新的节点，旧的子节点)

## 克隆元素

  + 元素.cloneChild(true/false) 参数代表是否返回所有内容，默认只返回元素盒子

## 注册事件  两种方式

  + 元素(事件源).onXXX=function(){事件处理程序}
    + 区别：只能添加一个相同事件，否则下面的时间会覆盖上面的事件
  + 元素(事件源).addEventListener(事件类型不加on，function(){事件处理程序},捕获)
    + 区别：可以添加多个事件  不会覆盖  而是同时触发

  + 事件移除
    + 元素.onXXX=null;
    + 元素.removeEventListener('事件类型不加on',事件处理程序名称)

## 事件流

  + 事件触发的流程
  + 三个状态
    + 捕获：从document到目标阶段的过程  也叫反冒泡
    + 目标：
    + 冒泡：从目标阶段到document的过程  叫做冒泡  也就是事件会逐层传递  直到document结束
    + 注意：事件触发，三个阶段始终存在，但触发后，捕获和冒泡仅仅只能启用一个

## 事件对象

  + 在事件触发后，在事件处理程序中所获取并操作的对象   储存事件发生时的相关信息的对象(Event e)
  + 获取事件对象
    + 事件源.事件类型=function(e){第一个形参e就是事件对象}
  + 鼠标事件对象相关属性-->获取鼠标的位置
    + 相对于浏览器的坐标：事件对象.clientX/事件对象.cliebtY
    + 相对于文档的坐标：事件对象.pageX/事件对象.pageY
    + 相对于当前的元素：事件对象.offsetX/事件对象.offsetY
  + 事件
    + 键盘事件
      + 键盘按下事件  onkeydown
      + 键盘弹起事件  onkeyup
    + 键盘事件相关属性
      + 事件对象.keyCode 获取按键键码值
      + 事件对象.altKey  是否按下alt建  返回布尔值
      + 事件对象.shiftKey
      + 事件对象.ctrlKey
    + 鼠标事件
      + oninput  输入事件
      + onmousedown 鼠标按下事件
      + onmouseup  鼠标抬起事件
      + onmousemove 鼠标移动事件
      + onmouseover(支持事件冒泡)onmouseenter(不支持事件冒泡)
      + onmouseout(支持事件冒泡)onmouseleave(不支持事件冒泡)
  + 事件对象的公共属性和方法
    + 事件对象.target  获取最先触发的元素
    + 和this的区别
      + this在事件处理程序中始终代表事件源
      + e.target代表不一定是事件源  代表的是从目标阶段-->document最先触发的元素
    + 方法：
      + 事件对象.preventDefault();阻止默认行为
      + 事件对象.stoPropagation();停止事件传播

## 事件委托(事件代理)

  + 将子孙元素的事件注册，完全交给子元素的上级元素代理
    + 注意：委托  下级元素委托上级元素   没有上级委托下级
  + 实现委托
    + 子孙元素的上级注册事件
    + 在事件处理程序中，使用*事件对象.target*获取最先触发的元素
    + 通过*事件对象.target的nodeName*属性最先触发的是否是指定元素
  + 作用
    + 减少事件的绑定
    + 节省内存
    + 上级元素可以代理未来新动态添加的元素
  + 原理
    + 关键：事件对象.target；可以获取最先触发的元素
    + 原理：因为事件冒泡的存在，可以获取到最先触发的元素[目标阶段-->document]
  + 兼容性
    + 获取事件对象的兼容问题
    + 标准：事件处理程序中的第一个形参
    + IE低版本：window.event
    + 兼容处理：
      + ```js
          document.onclick = function (e) {
        var _e = e || window.event;
        // 在js中，任何数据可以参与任何运算
        // 或运算格式：  左侧数据 || 右侧数据
        // 或运算结果是：左右其中一个数据
        // 运算规则：或运算运算的顺序是自左向右，若左侧是false或者将来能变成false,则输出右侧数据。否则输出左侧数据。
        console.log(_e);
        };  

## 顶级对象-window

### window对象介绍

  > 1. window对象被 称为==顶级对象== 或==全局对象== 
  > 2. 因为全局变量和全局函数本质上都是window对象的属性或方法
  > 3. window对象可以省略

### window中的对话框 

  > 1. alert：弹出框
  > 2. prompt：输入框
  > 3. confirm：确认框

### 定时器

  + 一次性定时器
    + 设置定时器
      + window.setTimeout(callback, time);
      + 延时一段时间执行 仅仅执行一次
      + 返回值是数字
    + 清除定时器
      + window.clearTimeout(定时器的标识);
  + 反复性定时器
    + 设置定时器
      + window.setInterval(callback, time);
      + 没隔一段时间执行一次  重复执行
    + 清除定时器
      + window.clearInterval(定时器的标识)

## location对象  操作浏览器的地址栏

  + 属性
    + ocation.href  设置或获取地址栏地址
  + 方法
    + location.reload(); 刷新页面
    + location.assign()：会产生历史记录
    + location.replace()：不会产生历史记录

## onload事件 入口函数  js代码执行的入口

  + window.onload = function () {} || window.addEventListener('load',function () {})
  + 页面加载完成后  才会执行此函数
  + 优点： 可以将js代码放到任何位置

## 元素的offset系列属性

  > 1. 获取元素大小
    + 标签属性：元素.width
    + CSS属性：元素.offsetWidth / 元素.offsetHeight;  
      + 返回的是数字  大小包含：内容 + padding + border
      + 该属性仅仅只能获取   不能设置
  > 2. 获取元素的位置
    + 元素.offsetLeft  /  元素.offsetTop;
      + 返回的是数字。（参照谁？看定位关系）
    + 元素.offsetParent：获取父元素【获取的是定位父元素】
    + 元素.parentNode：获取父元素【获取的是标签父元素】

## 移动端事件

### 核心知识

  > 1. touch事件（touchstart、touchmove、touchend）
  > 2. touchEvent 事件对象
  > 3. transitionend事件

### touch事件类型

  + touchstart，手指按下事件
  + touchmove，手指移动事件
  + touchend，手指松开事件
    + touch事件要比鼠标事件执行效率高，用户体验好

### touch事件对象

  + 常见的属性
    > 1. 事件对象.touches ：位于屏幕上的所有手指的列表；
    > 2. 事件对象.targetTouches ：位于该元素上的所有手指的列表；
    > 3. 事件对象.changedTouches：被改变的手指列表。  touchstart时包含刚与触摸屏接触的触点，touchend时包含离开触摸屏的触点
    + 区别：
      + touches和targetTouches必须是在屏幕上
      + 而changedTouches可以获取离开屏幕的手指的

### 手指的位置

  + > 1. 手指对象.clientX/Y 手指相对于可视区域   经常使用
    > 2. 手指对象.pageX/Y 手指相对于文档

### 常见手势

  > 1. Tap 点击
  > 2. Double tap 双击
  > 3. Drag 拖拽
  > 4. Flick 轻划
  > 5. Pinch 缩小
  > 6. Spread 放大
  > 7. Press 按压
  > 8. Press and tap 按压点击
  > 9. Press and drag 按压拖拽
  > 10. Rotate 旋转

### transitionend事件   css中过渡结束后检测的行为

  + 谁有过渡效果，这个事件添加给谁【事件监听】

### Zepto  针对现代手机端浏览器的 JavaScript 

  + 使用步骤
    > 1. 引入 zepto.js 核心库。
    > 2. 引入 zepto.touch.js 移动端手势模块。
    > 3. 新建 <script> 标签写业务代码。

### Swiper 轮播图插件

  + Web 插件：就是别人封装好的一个 js 代码 或 css代码
  + 使用步骤
    + > 1. 下载并且引入CSS文件和JS文件
      > 2. 复制内容
      > 3. 设置大小（可以不设置）
      > 4. 复制功能代码
      Swiper插件官网： https://www.swiper.com.cn/ 
