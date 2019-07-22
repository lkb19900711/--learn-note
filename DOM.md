# DOM第一天
##  事件的三要素
```html
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <meta http-equiv="X-UA-Compatible" content="ie=edge">
    <title>Document</title>
    <style>
        #box {
            width: 200px;
            height: 200px;
            background-color: red;
        }
    </style>
</head>

<body>
    <div id="box">

    </div>
    
    <script>
        事件三要素: 事件源   事件   事件处理程序

         获取事件源
        给事件源绑定 事件(你如onclick ,onmouseover)
        触发点击事件时   做什么事情

        获取事件源
        var boxEl = document.getElementById('box');
        对象.xx
        boxEl.onclick = function () {
            boxEl.style.backgroundColor = 'green';
        }
                DOM 为文档提供了结构化表示，并定义了如何通过脚本来访问文档结构。目的其实就是为了能让 js 操作 html 元素而制定的一个规范。

        DOM 就是由节点组成的。

        HTML 加载完毕，渲染引擎会在内存中把 HTML 文档，生成一个 DOM 树

        节点 元素节点 文本节点(换行空格都是节点) 属性节点 注释节点
    </script>
```
## 获取事件源(元素节点)
```html
<body>
    <div id="box">
        不凡学院
    </div>
    <ul>
        <li class="li-item"></li>
        <li class="li-item"></li>
        <li class="li-item"></li>
    </ul>
    <div class="inner-box">
        你好
    </div>
    <p>不凡学院</p>
    <script>
        方式一   :通过id 获取
        var boxEl = document.getElementById('box');
        console.log(boxEl);

        方式二  通过class 获取 ie678   用不了
        var lis = document.getElementsByClassName('li-item');
        var innerBox = document.getElementsByClassName('inner-box')[0];
        伪数组 具备length属性
        console.log(lis);
        console.log(lis[0]);
        console.log(innerBox);
        // lis.onclick
        innerBox.onclick = function () {
            alert('你好');
        }

        方式三  通过标签名
        var pEl = document.getElementsByTagName('p');
        伪数组
        console.log(pEl);
    </script>
```
## 二维码
```html
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <meta http-equiv="X-UA-Compatible" content="ie=edge">
    <title>Document</title>
    <style>
        .mask {
            display: none;
            position: fixed;
            left: 0;
            top: 0;
            width: 100%;
            height: 100%;
            background: rgba(0, 0, 0, .3) url('img/wx.jpg') no-repeat center;
        }

        .btn {
            width: 100px;
            height: 50px;
            line-height: 50px;
            text-align: center;
            background-color: red;
            border-radius: 8px;
            cursor: pointer;
        }
    </style>
    <script>
        onload事件(图片文本加载完成) 页面加载完成 执行
        window.onload = function () {
            var btn = document.getElementsByClassName('btn')[0];
            var maskEl = document.getElementsByClassName('mask')[0];
            btn.onclick = function () {
                maskEl.style.display = 'block';
                // btn.style.display = 'none';
                this.style.display = 'none';

            }
            maskEl.onclick = function () {
                this.style.display = 'none';
                btn.style.display = 'block';
            }
        }
    </script>
</head>

<body>
    <div class="btn">打开二维码</div>
    <div class="mask">

    </div>
    <script>

    </script>
</body>
```
## 通过节点间的关系获取节点
```html
 <ul>
        <li class="li-item">li1</li>
        <li class="li-item">li2</li>
        <li class="li-item li3">li3</li>
        <li class="li-item">li4</li>
        <li class="li-item">li5</li>
        <li class="li-item">li6</li>

    </ul>
    <script>
        var li1 = document.getElementsByClassName('li-item')[0];
        获取父节点
        // node.parentNode
        var ulEl = li1.parentNode;
        console.log(ulEl);
        获取兄弟节点 
        var li3 = document.getElementsByClassName('li3')[0];
        下一个兄弟节点 
        nextSibling  标准属性
        火狐、谷歌、IE9+版本：都指的是下一个节点（包括标签、空文档和换行节点）
        IE678 版本：指下一个元素节点（标签）。
        console.log(li3.nextSibling); // 换行符

        nextElementSibling：非标准属性 
        火狐、谷歌、IE9+版本：都指的是下一个元素节点（标签）。
        ie678中没有这个属性
        console.log(li3.nextElementSibling); // 下一个元素节点

        兼容写法 (拿到下一个 元素  节点)
        var nextS = li3.nextElementSibling || li3.nextSibling;


        上一个兄弟节点
        li3.previousSibling;
        li3.previousElementSibling;
    </script>
```
## 获取子节点
```html
 <ul>
        <li class="li-item">li1</li>
        <li class="li-item">li2</li>
        <li class="li-item li3">li3</li>
        
        <li class="li-item">li4</li>
        <li class="li-item">li5</li>
        <li class="li-item">li6</li>
    </ul>
    <script>
        var ulEl = document.getElementsByTagName('ul')[0];
        firstChild 和  firstElementChild

        高级浏览器 包括换行符等节点
        ie5678  下一个 元素 节点
        console.log(ulEl.firstChild); // 
        高级  下一个元素节点
        ie5678 不支持
        console.log(ulEl.firstElementChild); // 

        兼容问题
        lastchild  和 lastElementChild


        childNodes  获取所有子节点

        高级  包括 注释 换行符
        console.log(ulEl.childNodes);

        children 获取 所有元素子节点(不包括空格换行符)
        在 IE6/7/8 中包含注释节点（在 IE678 中，注释节点不要写在里面）。
        console.log(ulEl.children);

        兼容 
        function myChildren(el) {
            var children = el.childNodes;
            var result = [];
            for (var i = 0; i < children.length; i++) {
                // children[i]判断是不是元素节点
                // 通过nodeType 来判断 是哪种节点
                // 1 元素节点
                // 3 文本节点
                // 8 注释节点
                if (children[i].nodeType === 1) {
                    result.push(children[i])
                }
            }
            return result;
        }
        var children = myChildren(ulEl);
        console.log(children);
    </script>
```
## 除自己以外所有的兄弟节点
```html
 <ul>
        <li class="li-item">li1</li>
        <li class="li-item">li2</li>
        <li class="li-item li3">li3</li>

        <li class="li-item">li4</li>
        <li class="li-item">li5</li>
        <li class="li-item">li6</li>
    </ul>

    <script>
        除了自己以外的 所有兄弟元素节点
        var li3 = document.getElementsByClassName('li3')[0];

        function getSiblings(el) {
            var elParent = el.parentNode;
            var elChildren = elParent.children;
            var result = [];
            for (var i = 0; i < elChildren.length; i++) {
                // 不具备数组方法
                // console.log(elChildren[i].splice);
                if (elChildren[i] !== li3) {
                    result.push(elChildren[i]);
                }
            }
            return result;
        }
        var siblings = getSiblings(li3);
        console.log(siblings);


        实现 获取 li3 后边的 所有兄弟节点
        倒着 遍历
        function getNextSiblings(el) {
            var elParent = el.parentNode;
            var elChildren = elParent.children;
            var result = [];
            var lock = false;
            for (var i = 0; i < elChildren.length; i++) {
                if (elChildren[i] == li3) {
                    lock = true;
                    continue;
                }
                if (lock) {
                    result.push(elChildren[i]);
                }
                // console.log(1);
            }
            return result;
        }
        console.log(getNextSiblings(li3));
    </script>
```
## 节点属性操作
```html
<div id="d1" class="box"></div>
		<div class="btn">切换类名</div>
		<script>
			var boxEl = document.getElementsByClassName("box")[0];
			var btn = document.getElementsByClassName("btn")[0];
			对象追加属性
			boxEl.title = "不凡学院";

			元素节点.getAttribute("属性名称");
			元素节点.setAttribute(属性名, 新的属性值);
			元素节点.removeAttribute(属性名);

			console.log(boxEl.getAttribute("class"));
			console.log(boxEl.className);
			console.log(boxEl.getAttribute("title"));

			boxEl.setAttribute("id", "d2");
			boxEl.setAttribute("title", "d3");
			boxEl.setAttribute("class", "box2");
			怎么实现添加 class 名
			boxEl.setAttribute('class', 'box2 box3');
			boxEl.setAttribute('class', 'box3');
			var str = "box1 box22";
			添加 box2 这个类名
			console.log(str.indexOf('box2'));//用不了的

			boxEl.removeAttribute("title");

			追加类名
			boxEl.classList.add("box3");
			boxEl.classList.add("box4", "box5");
			删除某一个类名
			boxEl.classList.remove("box2");
			判断指定类名是否存在

			console.log(boxEl.classList.item(1)); //
			console.log(boxEl.classList.contains("box4"));
			有则删除  无则添加
			btn.onclick = function() {
				boxEl.classList.toggle("box4");
			};
			console.log(boxEl);
        </script>
```
## 节点的增删改查
```html
<body>
    <div class="box">
        我是一个盒子
    </div>
    <div class="box2">
        我是box2
        <p>我是一个p标签</p>
    </div>
    <div class="btn1">插入节点</div>
    <div class="btn2">再次插入同个节点</div>
    <div class="btn3">insertBefore</div>
    <div class="btn4">删除节点</div>

    <script>
        新的标签(元素节点) = document.createElement("标签名");
        var imgEl = document.createElement('img');
        var boxEl = document.getElementsByClassName('box')[0];
        var btn1 = document.getElementsByClassName('btn1')[0];
        var btn2 = document.getElementsByClassName('btn2')[0];
        var btn3 = document.getElementsByClassName('btn3')[0];
        var btn4 = document.getElementsByClassName('btn4')[0];



        var box2 = document.getElementsByClassName('box2')[0];
        imgEl.src = 'img/m1.jpg';
        创建节点
        console.log(imgEl);

         必须插入到页面中 才会显示
        插入节点
        父节点.appendChild(新的子节点);
        父节点的最后插入一个新的子节点。
        btn1.onclick = function () {
            boxEl.appendChild(imgEl);
        }
        重复插入 同一个节点 具有 剪切的效果
        btn2.onclick = function () {
            box2.appendChild(imgEl);
        }

        方式二
        父节点.insertBefore(新的子节点, 作为参考的子节点);
        解释：

        在参考节点前插入一个新的节点。
        如果参考节点为 null，那么他将在父节点里面的最后插入一个子节点。
        var p = document.getElementsByTagName('p')[0];
        var pEl = document.createElement('p');
        btn3.onclick = function () {
            box2.insertBefore(pEl, p)
        }

        父节点.removeChild(子节点);
        解释：用父节点删除子节点。必须要指定是删除哪个子节点。
        btn4.onclick = function () {
            box2.removeChild(p);
        }

        如果我想删除自己这个节点，可以这么做：
        node1.parentNode.removeChild(node1);

        复制节点
         要复制的节点.cloneNode(); //括号里不带参数和带参数false，效果是一样的。

        要复制的节点.cloneNode(true);
        console.log(box2.cloneNode());
        console.log(box2.cloneNode(true)); // 深复制
    </script>
</body>
```
## 节点内容操作
```html
<body>
    <div class="box">
        <p>我是一个盒子</p>
    </div>
    <input type="text">
    <button class="btn1">innerText</button>
    <button class="btn2">innerHTML</button>
    <button class="btn3">获取用户名</button>
    <button class="btn4">设置用户名</button>


    <script>
        innerHTML 插入标签
        innerText 插入文本
        字符串
        可以获取  也可以设置
        var box = document.getElementsByClassName('box')[0];
        var btn1 = document.getElementsByClassName('btn1')[0];
        var btn2 = document.getElementsByClassName('btn2')[0];
        var btn3 = document.getElementsByClassName('btn3')[0];
        var btn4 = document.getElementsByClassName('btn4')[0];


        var input = document.getElementsByTagName('input')[0];
        btn1.onclick = function () {
            给 box  重新设置文本内容
            box.innerText = '<p>外边下雨了</p>';
        }
        btn2.onclick = function () {
             假如有标签 会解析标签
            box.innerHTML = '<p>外边下雨了</p>';
             常用来动态生成页面
        }

        输入框  value
        btn3.onclick = function () {
            alert(input.value);
        }
        btn4.onclick = function () {
            input.value = '张三';
        }
    </script>
```
## 相册走廊
```html
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <meta http-equiv="X-UA-Compatible" content="ie=edge">
    <title>Document</title>
    <style>
        * {
            margin: 0;
            padding: 0;

        }

        .box {
            width: 800px;
            height: 300px;
            background-image: url(img/m1.jpg);
            background-repeat: no-repeat;
            background-position: center;
            background-size: 100%;
            margin: 0 auto;
        }

        ul {
            width: 910px;
            height: 80px;
            margin: 0 auto;
            list-style: none;
        }

        ul li {
            float: left;
        }

        ul li.active {
            border: 1px solid red;
        }

        img {
            width: 150px;
            height: 80px;
        }
    </style>
</head>

<body>
    <div class="box">

    </div>
    <ul>
        <!-- <li><img src="img/m1.jpg" alt=""></li> -->
    </ul>
    <script>
        var imgArr = ['m1.jpg', 'm2.jpg', 'm3.jpg', 'm4.jpg', 'm5.jpg', 'm6.jpg'];
        var box = document.getElementsByClassName('box')[0];
        var ul = document.getElementsByTagName('ul')[0];
        var str = '';
        for (var i = 0; i < imgArr.length; i++) {
            str += '<li><img src="img/' + imgArr[i] + '" alt=""></li>';
        }
        console.log(str);
        ul.innerHTML = str;

        // 如何给 这 6个li 绑定 点击事件
        var lis = document.getElementsByTagName('li');
        // 循环绑定点击事件
        // 解决方式一
        // for (var i = 0; i < lis.length; i++) {
        //     lis[i].index = i;
        //     lis[i].onclick = function () {

        //         // console.log(i);// 6
        //         // 获取index属性
        //         // 这里边不能用lis[i],需要使用this
        //         var index = this.index;
        //         box.style.backgroundImage = 'url(img/' + imgArr[index] + ')';
        //     }
        // }
        // 点击时  for循环早已结束

        // 解决方式二
        // 自执行函数解决
        for (var i = 0; i < lis.length; i++) {
            lis[i].onclick = (function (n) {
                return function () {
                    // console.log(n);
                    box.style.backgroundImage = 'url(img/' + imgArr[n] + ')';
                    // 排他思想
                    for (var i = 0; i < lis.length; i++) {
                        // lis[i].style.border = 'none';
                        lis[i].classList.remove('active');
                    }
                    // 添加边框
                    // lis[n].style.border = '1px solid #333';
                    this.classList.add('active');
                    // 但是咱们很少  在js 当中 去修改样式
                    // 结构样式  分离的原则
                }
                // return 函数的时候  会把这个函数所在作用域的变量一块 丢出去(存在背包)
            })(i);
        }
        // 分步
        // lis[0].onclick = function () {
        // 背包里 n是 0
        //     box.style.backgroundImage = 'url(img/' + imgArr[n] + ')';
        // }
        // lis[1].onclick = function () {
        // 背包里 n是1
        //     box.style.backgroundImage = 'url(img/' + imgArr[n] + ')';
        // }
        // lis[2].onclick = function () {
        // 背包里 n是2
        //     box.style.backgroundImage = 'url(img/' + imgArr[n] + ')';
        // }
    </script>
```
## 定时器
```html
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <meta http-equiv="X-UA-Compatible" content="ie=edge">
    <title>Document</title>
    <style>
        .ads {
            width: 800px;
            height: 50px;
            background-color: red;
        }
    </style>
</head>

<body>

    <div class="ads">
        这是一条广告
    </div>
    <script>
        // 定时器
        setTimeout(function () {
            console.log('你好')
        }, 2000);


        // 循环定时器
        // 每隔 2000 ms  执行一次这个function
        var timer = setInterval(function () {
            console.log('我是循环执行')
        }, 2000);


        // 关闭(清除)定时器
        // 4s之后  清除 timer
        // clearInterval()
        // clearTimeout()
        setTimeout(function () {
            clearInterval(timer);
        }, 4000);
        var ads = document.getElementsByClassName('ads')[0];
        setTimeout(function () {
            ads.style.display = 'none';
        }, 5000)
    </script>
</body>
```
## 倒计时
```html
<body>
    <p>距离2019年7月12日17:00,还有</p>
    <p class="stamp">00:00:00</p>

    <script>
        var pEl = document.getElementsByClassName('stamp')[0];
        var deadTime = new Date('2019-07-12 18:00');
        setInterval(function () {
            var nowTime = new Date();
            // 时间差
            var stamp = deadTime - nowTime;
            // 转换成时分秒
            // var hour = Math.floor(stamp / 1000 / 60 / 60);
            // var min = Math.floor(stamp / 1000 / 60 % 60);
            // var s = Math.floor(stamp / 1000 % 60);

            var HOUR_MS = 60 * 60 * 1000;
            var MIN_MS = 60 * 1000;
            var hour = Math.floor(stamp / HOUR_MS);
            var min = Math.floor(stamp % HOUR_MS / MIN_MS);
            var s = Math.floor(stamp % MIN_MS / 1000);
            var str = '' + wrap(hour) + ':' + wrap(min) + ':' + wrap(s) + '';
            pEl.innerText = str;
        }, 1000)
        // 辅助函数
        function wrap(n) {
            return n > 9 ? n : '0' + n;
        }
    </script>
</body>
```
# DOM第二天
## 小米banner轮播
```html
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <meta http-equiv="X-UA-Compatible" content="ie=edge">
    <title>Document</title>
    <style>
        * {
            margin: 0;
            padding: 0;
        }

        a {
            text-decoration: none;
        }

        .banner {
            position: relative;
            width: 1226px;
            height: 460px;
            margin: 100px auto;
        }

        .banner img {
            width: 100%;
            height: 100%;
        }

        .banner .arr {
            position: absolute;
            left: 234px;
            top: 50%;
            margin-top: -35px;
            width: 40px;
            height: 70px;
            line-height: 70px;
            text-align: center;
            color: #333;
            font-size: 24px;
        }

        .banner .arr.arr-r {
            left: auto;
            right: 0;
        }

        .banner .arr:hover {
            background-color: rgba(0, 0, 0, .3);
        }
    </style>
</head>

<body>
    <div class="banner">
        <img src="img/m1.jpg" alt="">
        <a href="javascript:;" class="arr arr-l">
            <</a> <a href="javascript:;" class="arr arr-r">>
        </a>
    </div>

    <script>
        var imgArr = ['m1.jpg', 'm2.jpg', 'm3.jpg', 'm4.jpg', 'm5.jpg', 'm6.jpg']
        var arrL = document.getElementsByClassName('arr-l')[0];
        var arrR = document.getElementsByClassName('arr-r')[0];
        var img = document.getElementsByTagName('img')[0];
        // 计数器
        var count = 0;
        arrR.onclick = function () {
            count++;
            if (count == imgArr.length) {
                count = 0;
            }
            img.src = 'img/' + imgArr[count];
        }
        arrL.onclick = function () {
            count--;
            if (count < 0) {
                count = imgArr.length - 1;
            }
            img.src = 'img/' + imgArr[count];
        }
    </script>
</body>
```
## 轮播优化
```html
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <meta http-equiv="X-UA-Compatible" content="ie=edge">
    <title>Document</title>
    <style>
        * {
            margin: 0;
            padding: 0;
        }

        a {
            text-decoration: none;
        }

        .banner {
            position: relative;
            width: 1226px;
            height: 460px;
            margin: 100px auto;
        }

        .banner img {
            width: 100%;
            height: 100%;
        }

        .banner .arr {
            position: absolute;
            left: 234px;
            top: 50%;
            margin-top: -35px;
            width: 40px;
            height: 70px;
            line-height: 70px;
            text-align: center;
            color: #333;
            font-size: 24px;
        }

        .banner .arr.arr-r {
            left: auto;
            right: 0;
        }

        .banner .arr:hover {
            background-color: rgba(0, 0, 0, .3);
        }
    </style>
</head>

<body>
    <div class="banner">
        <img src="img/m1.jpg" alt="">
        <a href="javascript:;" onclick="swipe(false)" class="arr arr-l">
            <</a> <a href="javascript:;" onclick="swipe(true)" class="arr arr-r">>
        </a>
    </div>

    <script>
        var imgArr = ['m1.jpg', 'm2.jpg', 'm3.jpg', 'm4.jpg', 'm5.jpg', 'm6.jpg']
        var arrL = document.getElementsByClassName('arr-l')[0];
        var arrR = document.getElementsByClassName('arr-r')[0];
        var img = document.getElementsByTagName('img')[0];
        // 计数器
        var count = 0;
        // arrR.onclick = function () {
        //     count++;
        //     if (count == imgArr.length) {
        //         count = 0;
        //     }
        //     img.src = 'img/' + imgArr[count];
        // }
        // arrL.onclick = function () {
        //     count--;
        //     if (count < 0) {
        //         count = imgArr.length - 1;
        //     }
        //     img.src = 'img/' + imgArr[count];
        // }

        // 绑定事件的方式
        // 方式一:
        // arrR.onclick = function(){

        // }
        // 方式二:
        // 在标签里边绑定

        /*
         * isRight :  是否向右切换 判断 点击的 是哪个箭头
         */

        function swipe(isRight) {
            if (isRight) {
                count++;
                if (count == imgArr.length) {
                    count = 0;
                }
            } else {
                count--;
                if (count < 0) {
                    count = imgArr.length - 1;
                }
            }
            img.src = 'img/' + imgArr[count];
        }
    </script>
</body>
```
## 轮播分页器
```html
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <meta http-equiv="X-UA-Compatible" content="ie=edge">
    <title>Document</title>
    <style>
        * {
            margin: 0;
            padding: 0;
        }

        a {
            text-decoration: none;
        }

        .banner {
            position: relative;
            width: 1226px;
            height: 460px;
            margin: 100px auto;
        }

        .banner img {
            width: 100%;
            height: 100%;
        }

        .banner .arr {
            position: absolute;
            left: 234px;
            top: 50%;
            margin-top: -35px;
            width: 40px;
            height: 70px;
            line-height: 70px;
            text-align: center;
            color: #333;
            font-size: 24px;
        }

        .banner .arr.arr-r {
            left: auto;
            right: 0;
        }

        .banner .arr:hover {
            background-color: rgba(0, 0, 0, .3);
        }

        .dots {
            list-style: none;
            position: absolute;
            bottom: 20px;
            right: 100px;
        }

        .dots .dot-item {
            float: left;
            width: 12px;
            height: 12px;
            border: 2px solid #333;
            background-color: gray;
            border-radius: 50%;
            margin-left: 12px;
        }

        .dots .dot-item.active {
            background-color: #fff;
            border: 2px solid gray;
        }
    </style>
</head>

<body>
    <div class="banner">
        <img src="img/m1.jpg" alt="">
        <a href="javascript:;" onclick="swipe(false)" class="arr arr-l">
            <</a> <a href="javascript:;" onclick="swipe(true)" class="arr arr-r">>
        </a>
        <ul class="dots">
            <!-- <li class="dot-item"></li> -->
        </ul>
    </div>

    <script>
        var imgArr = ['m1.jpg', 'm2.jpg', 'm3.jpg', 'm4.jpg', 'm5.jpg', 'm6.jpg'];
        var arrL = document.getElementsByClassName('arr-l')[0];
        var arrR = document.getElementsByClassName('arr-r')[0];
        var img = document.getElementsByTagName('img')[0];
        var ul = document.getElementsByClassName('dots')[0];
        var dotItems = document.getElementsByClassName('dot-item');
        // 计数器
        var count = 0;
        // 生成分页器
        initDots(ul, imgArr);

        // 分页器点击事件
        // for (var i = 0; i < dotItems.length; i++) {
        //     dotItems[i].index = i;
        //     dotItems[i].onclick = function () {
        //         count = this.index;
        //         img.src = 'img/' + imgArr[this.index];
        //         // 排他
        //         for (var i = 0; i < dotItems.length; i++) {
        //             // dotItems[i].style.backgroundColor = 'gray';
        //             // dotItems[i].style.borderColor = '#333';
        //             dotItems[i].classList.remove('active');

        //         }
        //         // 修改分页器样式 和 count 值有关
        //         dotItems[this.index].classList.add('active');
        //     }
        // }
        function go(num) {
            // console.log(num);
            // 同步count
            count = num;
            img.src = 'img/' + imgArr[count];
            // 排他
            for (var i = 0; i < dotItems.length; i++) {
                // dotItems[i].style.backgroundColor = 'gray';
                // dotItems[i].style.borderColor = '#333';
                dotItems[i].classList.remove('active');

            }
            // 修改分页器样式 和 count 值有关
            dotItems[count].classList.add('active');
        }
        /*
         * isRight :  是否向右切换 判断 点击的 是哪个箭头
         */

        // 给分页器 循环绑定点击事件
        function swipe(isRight) {
            if (isRight) {
                count++;
                if (count == imgArr.length) {
                    count = 0;
                }
            } else {
                count--;
                if (count < 0) {
                    count = imgArr.length - 1;
                }
            }
            go(count);
            // img.src = 'img/' + imgArr[count];

            // // 排他
            // for (var i = 0; i < dotItems.length; i++) {
            //     // dotItems[i].style.backgroundColor = 'gray';
            //     // dotItems[i].style.borderColor = '#333';
            //     dotItems[i].classList.remove('active');

            // }
            // // 修改分页器样式 和 count 值有关
            // dotItems[count].classList.add('active');
        }

        function initDots(el, arr) {
            var str = '';
            for (var i = 0; i < arr.length; i++) {
                str += '<li onclick="go(' + i + ')" class="dot-item' + (i === 0 ? ' active' : '') + '"></li>';
            }
            el.innerHTML = str;
        }
    </script>
```
## banner完善
```html
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <meta http-equiv="X-UA-Compatible" content="ie=edge">
    <title>Document</title>
    <style>
        * {
            margin: 0;
            padding: 0;
        }

        a {
            text-decoration: none;
        }

        .banner {
            position: relative;
            width: 1226px;
            height: 460px;
            margin: 100px auto;
        }

        .banner img {
            width: 100%;
            height: 100%;
        }

        .banner .arr {
            position: absolute;
            left: 234px;
            top: 50%;
            margin-top: -35px;
            width: 40px;
            height: 70px;
            line-height: 70px;
            text-align: center;
            color: #333;
            font-size: 24px;
        }

        .banner .arr.arr-r {
            left: auto;
            right: 0;
        }

        .banner .arr:hover {
            background-color: rgba(0, 0, 0, .3);
        }

        .dots {
            list-style: none;
            position: absolute;
            bottom: 20px;
            right: 100px;
        }

        .dots .dot-item {
            float: left;
            width: 12px;
            height: 12px;
            border: 2px solid #333;
            background-color: gray;
            border-radius: 50%;
            margin-left: 12px;
        }

        .dots .dot-item.active {
            background-color: #fff;
            border: 2px solid gray;
        }

        .side {
            position: absolute;
            left: 0;
            top: 0;
            width: 234px;
            height: 420px;
            padding: 20px 0;
            list-style: none;
            background-color: rgba(0, 0, 0, .3);
        }

        .side .col {
            height: 42px;
            line-height: 42px;
            text-indent: 40px;
            cursor: pointer;
        }

        .side .col:hover {
            background-color: orange;
        }

        .side .col:hover .pro-box {
            display: block;
        }

        .side .pro-box {
            display: none;
            position: absolute;
            left: 234px;
            top: 0;
            background-color: rgba(255, 255, 255, .5);
            width: 992px;
            height: 460px;
            z-index: 9;
            list-style: none;
        }

        .side .pro-box li {
            float: left;
            width: 25%;
            height: 60px;
            text-indent: 0;
            margin-bottom: 20px;
        }

        .side .pro-box img {
            float: left;
            width: 30%;
            height: 100%;
        }
    </style>
</head>

<body>
    <div class="banner">
        <ul class="side">
            <!-- <li class="col">手机 电话卡
                <ul class="pro-box">
                    <li><img src="img/m2.jpg" alt="">小米</li>
                </ul>
            </li> -->
        </ul>
        <img src="img/m1.jpg" alt="">
        <a href="javascript:;" onclick="swipe(false)" class="arr arr-l">
            <</a> <a href="javascript:;" onclick="swipe(true)" class="arr arr-r">>
        </a>
        <ul class="dots">
            <!-- <li class="dot-item"></li> -->
        </ul>
    </div>
    <script src="data/data.js"></script>
    <script>
        console.log(proData);
        var imgArr = ['m1.jpg', 'm2.jpg', 'm3.jpg', 'm4.jpg', 'm5.jpg', 'm6.jpg'];
        var arrL = document.getElementsByClassName('arr-l')[0];
        var arrR = document.getElementsByClassName('arr-r')[0];
        var img = document.getElementsByTagName('img')[0];
        var ul = document.getElementsByClassName('dots')[0];
        var dotItems = document.getElementsByClassName('dot-item');
        var side = document.getElementsByClassName('side')[0];
        var proBox = document.getElementsByClassName('pro-box');
        // 计数器
        var count = 0;
        // 生成分页器
        initDots(ul, imgArr);
        initCol(side, colData);
        // initColPro(proBox[0], proData[0]);
        // initColPro(proBox[1], proData[1]);
        // initColPro(proBox[2], proData[2]);
        for (var i = 0; i < proBox.length; i++) {
            initColPro(proBox[i], proData[i]);
        }
        // 动态生成侧边栏
        function initCol(el, arr) {
            var str = '';
            for (var i = 0; i < arr.length; i++) {
                str += '<li class="col">' + arr[i] + '<ul class="pro-box"></ul></li>'
            }
            el.innerHTML = str;
        }
        // 生成侧边栏里边的 产品
        function initColPro(el, arr) {
            var str = '';
            for (var i = 0; i < arr.length; i++) {
                str += '<li><img src="img/' + arr[i].img + '" alt="">' + arr[i].model + 'l</li>';
            }
            el.innerHTML = str;
        }

        function go(num) {
            // console.log(num);
            // 同步count
            count = num;
            img.src = 'img/' + imgArr[count];
            // 排他
            for (var i = 0; i < dotItems.length; i++) {
                // dotItems[i].style.backgroundColor = 'gray';
                // dotItems[i].style.borderColor = '#333';
                dotItems[i].classList.remove('active');

            }
            // 修改分页器样式 和 count 值有关
            dotItems[count].classList.add('active');
        }
        /*
         * isRight :  是否向右切换 判断 点击的 是哪个箭头
         */

        // 给分页器 循环绑定点击事件
        function swipe(isRight) {
            if (isRight) {
                count++;
                if (count == imgArr.length) {
                    count = 0;
                }
            } else {
                count--;
                if (count < 0) {
                    count = imgArr.length - 1;
                }
            }
            go(count);

        }

        function initDots(el, arr) {
            var str = '';
            for (var i = 0; i < arr.length; i++) {
                str += '<li onclick="go(' + i + ')" class="dot-item' + (i === 0 ? ' active' : '') + '"></li>';
            }
            el.innerHTML = str;
        }
    </script>
</body>
```
## 压缩和argument对象
```html
<script>
        只能在函数里边使用
        arguments 对象  : 函数的实参对象  类数组
        function add(x, y, z) {
            console.log(arguments);
            console.log(arguments.length);
            console.log(arguments.callee); // 返回函数本身
            //     ƒ add(x, y, z) {
            //     console.log(arguments);
            //     console.log(arguments.length);
            //     console.log(arguments.callee);
            //     return x + y + z;
            // }
            return x + y + z;
        }
        add(2, 3);

        function fb(n) {
            if (n == 1) {
                return 1;
            }
            // return n * fb(n - 1);
            return n * arguments.callee(n - 1);
        }
        console.log(fb(5))
    </script>
```
## 获取dom元素query
```html
<body>
    <div class="box">
        我是一个外部盒子
        <div class="inner-box">
            我是一个内部盒子
        </div>
    </div>
    <div class="inner-box">
        wo也是一个内部盒子
    </div>
    <ul>
        <li class="li-item">li1</li>
        <li class="li-item active">li2</li>
        <li class="li-item"></li>
        <li class="li-item"></li>
    </ul>
    <script>
        // var box = document.getElementsByClassName('box')[0];
        像使用 css选择器 一样获取 dom元素
        var box = document.querySelector('.box');
        box.style.color = 'red';
        console.log(box);
        后代选择器
        var innerBox = document.querySelector('.box .inner-box');
        console.log(innerBox);

        交集选择器也可以用
        var li2 = document.querySelector('.li-item.active');
        console.log(li2);

        // querySelectorAll
        var lis = document.querySelectorAll('.li-item');
        console.log(lis); // 类数组

        匹配第一个
        var li = document.querySelector('.li-item');
        console.log(li);
    </script>
</body>
```
## addEventListener
```html
<body>
    <div class="box">
        我是一个外部盒子
    </div>
    <div class="inner-box">
        我是innerBox
    </div>
    <button id="btn1">移除onclick</button>
    <div class="w">
        我是w
        <div class="w1">
            我是w1
            <div class="w2">
                我是w2
            </div>
        </div>
    </div>
    <button id="btn2">移除w2的事件</button>
    <script>
        var box = document.querySelector('.box');
        box.onclick = function () {
            alert('123');
        }
        box.onclick = function () {
            alert('456');
        }
        通过 onclick 只能绑定一个点击事件
        var btn1 = document.querySelector('#btn1');
        btn1.onclick = function () {
            移除 box 的onclick事件
            box.onclick = null;
        }

        优点  注册 多个   更精细
        var innerBox = document.querySelector('.inner-box');
        innerBox.addEventListener('click', function () {
            alert('123')
        })
        innerBox.addEventListener('click', function () {
            alert('456')
        })

        var w = document.querySelector('.w');
        var w1 = document.querySelector('.w1');
        var w2 = document.querySelector('.w2');
        第三个参数  是否捕获   true捕获  false/不写  冒泡
        捕获  从外到里
        冒泡  从里到外
        w.addEventListener('click', function () {
            alert('w')
        }, false)
        w1.addEventListener('click', function () {
            alert('w1')
        }, true)
        w2.addEventListener('click', foo, false)
        函数名 foo  代替
        function foo() {
            alert('w2');
        }
        移除事件  removeEventListener
        var btn2 = document.querySelector('#btn2');
        btn2.addEventListener('click', function () {
            移除w2  的事件
            事件类型 ,外部函数  .捕获冒泡   必须同 绑定时  一致
            w2.removeEventListener('click', foo, false)
        })


         <=IE8专用
        target.attachEvent(type, listener); 
        detachEvent(event,function); 
    </script>
</body>
```
# DOM第三天
## argumens对象
```html
<script>
        函数的实参对象
        function add(x, y) {
            console.log(x);
            console.log(arguments);
            伪数组 具备length属性  
            console.log(typeof arguments);
            console.log(arguments instanceof Array); // arguments 不是数组
            console.log(arguments[0]);
            arguments.length;  返回的是实参的个数。    
            console.log(arguments.length)
        }
        add(5, 7, 8);
        instanceof 可以用来检测数组
        var arr = [1, 2];
        console.log(arr instanceof Array); // true  是数组
    </script>
```
## callee
```html
 <script>
        函数的实参对象
        function add(x, y) {
            console.log(arguments.callee)
        }
            arguments.callee;    
         返回的是正在执行的函数。 函数本身
        add(5, 7, 8);
        使用函数递归调用时推荐使用arguments.callee代替函数名本身。 
        function fb(n) {
            跳出条件
            if (n === 1 || n === 2) {
                return 1
            }
            return arguments.callee(n - 1) + arguments.callee(n - 2)
        }
    </script>
```
## 立即执行函数
```html
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <meta http-equiv="X-UA-Compatible" content="ie=edge">
    <title>Document</title>
    <style>
        ul {
            list-style: none;

        }

        li {
            background-color: red;
        }
    </style>
</head>

<body>
    <ul>
        <li class="li-item">1</li>
        <li class="li-item">2</li>
        <li class="li-item">3</li>
        <li class="li-item">4</li>
        <li class="li-item">5</li>
        <li class="li-item">6</li>
    </ul>

    <script>
        var ulEl = document.getElementsByTagName('ul')[0];
        var lis = ulEl.children;

        function foo(n) {
            console.log(n)
        }
        // foo(3);
        var bar = function () {

        };

        立即执行函数
        传参
        (function (num) {
            // console.log(num)
        })(4);

        给 li 循环绑定事件
        for (var i = 0; i < lis.length; i++) {
            闭包 在函数外边  可以使用函数的变量
            lis[i].onclick = (function (n) {
                return function () {
                    console.log(n)
                }
            })(i);
        }
        分解
         lis[0].onclick = function () {
                console.log(n)
            } // 背包里边 n=0

            lis[1].onclick = function () {
                console.log(n)
            } // n=1

            lis[2].onclick = function () {
                console.log(n)
            } // n=2

            lis[3].onclick = function () {
                console.log(n)
            } // n=3
        console.log(i);
        点击拿到当前 i
        1 var 改成 let  
        2. 把i 的值  保存在 li 的 id 属性里边
        利用自执行函数解决
    </script>
</body>
```
## addeventListener
```html
<body>
    <div class="box">
        wohsibocx
        <div class="inner-box">
            我是innerbox
        </div>
    </div>
    <script>
        var box = document.getElementsByClassName('box')[0];
        var innerBox = document.getElementsByClassName('inner-box')[0];

        box.onclick = function () {
            alert('abc')
        }
        box.onclick = function () {
            alert('def')
        }
        .onclick 绑定事件  重复绑定  会 覆盖
        target.addEventListener(type, listener, iscapture]);
        target: 事件源
        type： 字符串， 事件名称， 不含“ on”， 比如“ click”、“ mouseover”、“ keydown” 等。
        listener: 事件处理程序
        box.addEventListener('click', function () {
            alert('abc')
        })
        box.addEventListener('click', function () {
            alert('edf')
        })
        box.addEventListener('click', function () {
            alert('fff')
        }, true)

        iscapture  是否捕获
        true捕获(从外到里)   false冒泡(从里到外)
        innerBox.addEventListener('click', function () {
            alert('我是内部盒子')
        }, true)
          触发顺序问题
    </script>
</body>
```
## 捕获冒泡
```html
<body>
    <ul>
        我是ul
        <li>
            我是li
            <p>
                我是p标签
            </p>
        </li>
    </ul>
    <script>
        var ul = document.getElementsByTagName('ul')[0];
        var li = document.getElementsByTagName('li')[0];
        var p = document.getElementsByTagName('p')[0];
        第三个参数不写  默认 false
        ul.addEventListener('click', function () {
            alert('我是ul')
        }, true)
        li.addEventListener('click', function () {
            alert('我是li')
        }, false)
        p.addEventListener('click', function () {
            alert('我是p')
        }, true)
    </script>
</body>
```
## 解绑事件
```html
<body>
    <div class="box">
        woshibox
    </div>
    <div class="btn">解绑事件</div>
    <script>
        var box = document.getElementsByClassName('box')[0];
        var btn = document.getElementsByClassName('btn')[0];

        box.onclick = function () {
            alert('abc')
        }
        btn.onclick = function () {
            // 解绑事件
            box.onclick = null;
        }
        box.addEventListener('click', foo, false)

        function foo() {
            alert('abc')
        }
        btn.onclick = function () {
            解绑eventListener
            必须同是  冒泡 或者 捕获
            事件类型    处理程序   冒泡捕获   必须  全部一致  才能解除
            box.removeEventListener('click', foo, false)
        }
        ie8  attachEvent  
    </script>
</body>
```
## 定时器
```html
<script>
        5秒之后  打印   100
        延迟执行
        setTimeout(function () {
            console.log(100);

        }, 5000)

        setInterval()  循环执行


        var timer = setInterval(function () {
            console.log('循环执行...')
        }, 1000)


        clearInterval()  清除定时器
        10s 之后 清除循环定时器
        setTimeout(function () {
            用一个变量来接收 定时器
            clearInterval(timer)
        }, 10000)

        clearTimeout(); // 用来清除 setTimeout
        for (var i = 0; i < 10; i++) {
            (function (n) {
                return setTimeout(function () {
                    打印 0-9
                    console.log(n);
                }, n * 1000)
            })(i)
        }

        for (var i = 0; i < 10; i++) {
            setTimeout(function () {
                console.log(i)
                修改  使他  打印 0---9
            })
        }
    </script>
```
## 定时关闭广告
```html
<body>
    <div class="ads">
        这是一条广告
    </div>
    <script>
        var ads = document.getElementsByClassName('ads')[0];
        5秒之后关闭广告
        setTimeout(function () {
            ads.style.display = 'none';
        }, 5000)
    </script>
</body>
```
## 倒计时
```html
<body>
    <p>距离2019年6月17日 17:00,还有</p>
    <p class="stamp"></p>

    <script>
        截止时间
        var oldTime = '2019-06-17 17:00';
        var oldDate = new Date(oldTime);
        var oldTimeStamp = oldDate.getTime();
        var stampStr = '';
        var pEl = document.getElementsByClassName('stamp')[0];
        setInterval(function () {
            var nowDate = new Date();
            var nowTimeStamp = nowDate.getTime();
            时间差 
            var stamp = oldTimeStamp - nowTimeStamp;
            console.log(stamp);
            换算
            var HOUR_MS = 60 * 60 * 1000;
            var hour = Math.floor(stamp / HOUR_MS);
            var MIN_MS = 60 * 1000;
            var min = Math.floor(stamp % HOUR_MS / MIN_MS);
            var mm = Math.floor(stamp % MIN_MS / 1000);
            stampStr = wrap(hour) + ':' + wrap(min) + ':' + wrap(mm);
            pEl.innerText = stampStr;
        }, 1000)

        function wrap(n) {
            return n < 10 ? '0' + n : n;
        }

        for (var i = 0; i < 5; i++) {
            [i]
        }
        setTimeout
    </script>
</body>
```
## 回顾轮播
```html
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <meta http-equiv="X-UA-Compatible" content="ie=edge">
    <title>Document</title>
    <style>
        * {
            margin: 0;
            padding: 0;
        }

        ul {
            list-style: none;
        }

        a {
            text-decoration: none;
        }

        .banner {
            position: relative;
            width: 1226px;
            height: 460px;
            margin: 100px auto;
        }

        .banner img {
            width: 1226px;
            height: 460px;
        }

        .banner .arr {
            position: absolute;
            top: 50%;
            left: 224px;
            width: 40px;
            height: 70px;
            margin-top: -35px;
            font-size: 24px;
            line-height: 70px;
            text-align: center;
            background-color: rgba(0, 0, 0, .3);
        }

        .banner .arr.arr-r {
            left: auto;
            right: 0;
        }

        .dots {
            position: absolute;
            right: 20px;
            bottom: 20px;
        }

        .dots .dot-item {
            float: left;
            width: 10px;
            height: 10px;
            background-color: rgba(0, 0, 0, .8);
            border: 2px solid gray;
            background-clip: content-box;
            margin-left: 10px;
            border-radius: 50%;
        }

        .dots .dot-item.active {
            background-color: #fff;
        }

        .dots .dot-item:hover {
            background-color: #fff;
        }

        .dots .dot-item a {
            display: block;
            width: 100%;
            height: 100%;
        }
    </style>
</head>

<body>
    <div class="banner">
        <img src="img/m1.jpg" alt="">
        <!-- 取消a标签的点击跳转 -->
        <!-- 第二种绑定事件的方式 -->
        <!-- 直接在标签里边写事件 -->
        <a href="javascript:;" class="arr arr-l" onclick='swipe(false)'> '<' </a> <a href="javascript:;"
                onclick='swipe(true)' class="arr arr-r">
                '>' </a>
        <ul class="dots">
            <!-- <li class="dot-item active"><a href="javascript:;"></a></li> -->
        </ul>
    </div>
    <script src="js/util.js"></script>
    <script>
        var imgArr = ['m1.jpg', 'm2.jpg', 'm3.jpg', 'm4.jpg', 'm5.jpg', 'm6.jpg'];
        var ulEl = document.getElementsByClassName('dots')[0];

        var btn = document.getElementsByClassName('arr');

        var btnR = document.getElementsByClassName('arr-r')[0];
        var btnL = document.getElementsByClassName('arr-l')[0];
        var imgEl = document.getElementsByTagName('img')[0];

        initDots(ulEl, imgArr);
        var dotLis = ulEl.children;
        // console.log(dotLis);
        // 计数器 ,记录第几次点击
        var count = 0;

        function swipe(isRight) {
            if (isRight) {
                count++;
                if (count > 5) {
                    count = 0;
                }
            } else {
                count--;
                if (count < 0) {
                    count = 5;
                }
            }
            // imgEl.src = 'img/' + imgArr[count];
            go(count);
        }

        function go(num) {
            count = num;
            imgEl.src = 'img/' + imgArr[count];
            // 排他
            for (var i = 0; i < dotLis.length; i++) {
                delClass(dotLis[i], 'active');
            }
            addClass(dotLis[count], 'active');
        }
        // 动态生成小圆点
        function initDots(el, arr) {
            var str = '';
            for (var i = 0; i < arr.length; i++) {
                str = str + '<li onclick="go(' + i + ')" class="dot-item' + (i === 0 ? ' active' : '') +
                    '"><a href="javascript:;"></a></li>'
            }
            el.innerHTML = str
        }
    </script>
</body>
```
