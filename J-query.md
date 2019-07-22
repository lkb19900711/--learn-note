# jquery第一天
## jquery引入
```html
<body>
    <script src="js/utils.js"></script>
    使用  jquery 必须在引入之后
    <script src="js/jquery-3.4.1.min.js"></script>
    <script>
        // add(3, 5);

        console.log($);
    </script>
</body>
```
## onload
```html
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <meta http-equiv="X-UA-Compatible" content="ie=edge">
    <title>Document</title>
    <script src="js/jquery-3.4.1.min.js"></script>
    <script>
        window.onload = function () {
            alert('123')
        }
        window.onload = function () {
            alert('456')
        }
        window.onload  事件覆盖

        $(document).ready(function () {
            alert('567');
        })
        $(document).ready(function () {
            alert('7');
        })
         不会覆盖
        简写
        $(function () {
            alert('123')
        });
    </script>
```
## jquery处理事件
```html
<div class="box">
        不凡学院
    </div>
    <script src="js/jquery-3.4.1.min.js"></script>
    <script>
        var box = document.getElementsByClassName('box');
        // box[0].onclick = function () {
        //     this.style.color = 'red';
        // }
        console.log(box);
        原生 dom 元素  (原生dom)

        jquery 如何实现

        获取事件源(jq对象)  绑定事件   书写处理程序
        var $box = $('.box');
        绑定事件
        // .click()
        $box.click(function () {
            回调函数  函数作为参数时
            再回电函数中 this 的指向 通常会发生改变,慎用this
             jquery  强行修改了this的指向,所以这里他才能指向 $box的 原声都没对象

            修改样式 .css()
            console.log(this); // 原声 dom对象   不具备 jquery的方法
            dom对象 转 jq对象
            $(this).css('color', 'blue');
        });
    </script>
```
## 获取jq对象(事件源)
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

        /* 新增css 选择器 */
        /* + > */
        /* .li3的下一个兄弟li标签 */
        .li3+li {
            color: red;
        }

        /* .li3的后边所有兄弟 li */
        .li3~li {
            background-color: pink;
        }

        .wrap {
            width: 200px;
            height: 200px;
            background-color: red;
        }

        .w1 {
            width: 150px;
            height: 150px;
            background-color: green;
        }

        .w2 {
            width: 100px;
            height: 100px;
            background-color: orange;
        }

        /* 后代选择器 */
        .wrap .w {
            background-color: pink;
        }

        /* 子代选择器 */
        /* 亲儿子 */
        .wrap>.w {
            background-color: blue;
        }
    </style>
</head>

<body>
    <ul>
        <li>li1</li>
        <li>li2</li>
        <li class="li3">li3</li>
        <li>li4</li>
        <li>li5</li>
    </ul>
    <div class="wrap">
        我是w
        <div class="w w1">
            我是w1
            <div class="w w2">
                我是w2
            </div>
        </div>
    </div>
    <p id="p1">不凡学院</p>
    <span>天气很好</span>
    <div class="box">
        我是一个box
        <div class="inner-box">
            我是内部盒子
        </div>
    </div>
    <div class="inner-box active">
        我是内部盒子2
    </div>
    <script src="js/jquery-3.4.1.min.js"></script>
    <script>
        通过 class 选择器 获取
        id 选择器获取
        标签选择器获取

        后代选择器获取
        并集选择器获取
        交集选择其获取
        $('.box').css('color', 'red');
        $('#p1').css('color', 'blue');
        $('span').css('color', 'green');
        $('.box .inner-box').css('color', 'pink');
        $('.inner-box.active').css('backgroundColor', 'red');
        子代
        $('.wrap>.w').css('backgroundColor', 'black')
        兄弟
        $('.li3+li').css('color', 'blue');
        $('.li3~li').css('backgroundColor', 'orange');
    </script>
</body>
```
## 过滤选择器
```html
<body>
    <ul>
        <li>li1</li>
        <li>li2</li>
        <li>li3</li>
        <li class="li4">li4</li>
        <li>li5</li>
        <li>li6</li>
        <li>li7</li>
        <li>li8</li>
    </ul>

    <script src="js/jquery-3.4.1.min.js"></script>
    <script>
        // :eq(index) index从0开始
        $('li:eq(4)').css('background-color', 'red');
        // :gt()   大于这个序号
        $('li:gt(2)').css('background-color', 'blue');
        // :lt()  小于这个序号
        $('li:lt(2)').css('background-color', 'orange');
        // :odd 序号为奇数
        $('li:odd').css('background-color', 'pink');
        // :even  偶数
        $('li:even').css('background-color', 'red');
        // fisrt
        $('li:first').css('background-color', 'black');
        // last
        $('li:last').css('background-color', 'green');
    </script>
</body>
```
## 属性选择器
```html
<body>
    <a href="https://www.baidu.com/" class="item" title="不凡学院">跳到百度</a>
    <a href="https://www.baidu.com/" class="item">跳到百度2</a>
    <a href="https://www.baidu.com/" class="item" title="你好">跳到百度3</a>
    <a href="https://www.baidu.com/" class="item" title="你好学">跳到百度4</a>
    <a class="item" title="你好">跳到百度5</a>





    <script src="js/jquery-3.4.1.min.js"></script>
    <script>
        // 具有title属性的 a标签
        $('a[title]').css('color', 'black');
        // title属性 是 '你好
        $('a[title="你好"]').css('color', 'red');
        // title 属性值 不是你好 包含没有title 属性的
        $('a[title!="你好"]').css('color', 'green');
        // title属性  以 不 开头
        $('a[title^="不"]').css('color', 'orange');
        // title 属性值  以  院  结尾
        $('a[title$="院"]').css('color', 'pink');
        // 属性值 包含 学 这个字符
        $('a[title*="学"]').css('color', 'black');
        // 有href属性 并且title属性值为 你好   符合多个规则
        $('a[href][title="你好"]').css('color', 'blue');
    </script>
</body>
```
## 关系查找
```html
<body>
    <ul>
        <li>li_1</li>
        <li>li_2</li>
        <li>li_3</li>
        <li class="li3">li_4</li>
        <li>li_5</li>
        <li>li_6</li>
        <li>li_7</li>
        <li>li_8</li>
        <li>li_9</li>
        <li>li_10</li>
    </ul>

    <div class="box">
        <div class="d1">
            我是d1
            <div class="d2">
                我是d2
            </div>
        </div>
        <p class="p1">
            我是p1
        </p>
    </div>
    <script src="js/jquery-3.4.1.min.js"></script>
    <script>
        $('.box').find('.p1').css('width', '200px');
        children()  直接子元素
        $('.box').children().css('backgroundColor', 'red');
        所有兄弟元素(不包括自己)
        $('.li3').siblings().css('color', 'blue');
        父元素
        $('.d2').parent().css('width', '50px');

        eq(index) 查找指定元素的第index个元素，index是索引号，从0开始
        $('li').eq(3).css('color', 'red');
    </script>
</body>
```
## 变色模拟hover效果
```html
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <meta http-equiv="X-UA-Compatible" content="ie=edge">
    <title>Document</title>
    <style>
        /* .box:hover {
            color: red;
        } */
        .box {
            color: green;
            width: 100px;
            height: 100px;
            background-color: orange;
        }

        p {
            width: 50px;
            height: 50px;
            background-color: pink;
        }
    </style>

</head>

<body>

    <div class="box">
        <p>不凡学院</p>
    </div>
    <script src="js/jquery-3.4.1.min.js"></script>
    <script>
        var $box = $('.box');
        var colorBefore;
        ，mouseenter 鼠标经过的时候只会触发一次
        $box.mouseenter(function () {
            鼠标进入,先获取原来的颜色
            colorBefore = $(this).css('color');
            // this.style.color='red';
            $(this).css('color', 'red');
            console.log(1)
        })
        离开时 变回原来的颜色 思考原来的颜色如何获取 ?
        $box.mouseleave(function () {
            $(this).css('color', colorBefore);
            console.log(2)
        })


        每遇到一个子元素就会触发一次
        $box.mouseover(function () {
            鼠标进入,先获取原来的颜色
            colorBefore = $(this).css('color');
            this.style.color='red';
            $(this).css('color', 'red');
            console.log(1);
        })

        $box.mouseout(function () {
            $(this).css('color', colorBefore);
            console.log(2)
        })
    </script>
</body>
```
## dom对象和jq对象的转换
```html
<body>
    <div class="box">
        woshi box

        <div class="inner-box">
            wsohi innerbox
        </div>
    </div>
    <div class="box">
        我是box1
    </div>
    <script src="js/jquery-3.4.1.min.js"></script>
    <script>
        dom 对象
        var box = document.getElementsByClassName('inner-box')[0];
        console.log(box)
        jq对象 类数组
        var $box = $('.inner-box');
        console.log($box);
        将jq 对象  转换为了 dom 对象  进行原生js操作
        console.log($box[0]);
        console.log($box.get(0));


        dom对象 转换为 jq 对象  才能使用jq的方法
        console.log($(box));

        $('.box').click(function () {
            alert('123');
        })
    </script>
</body>
```
## 淘宝作业
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

        .box {
            width: 380px;
            height: 250px;
            margin: 100px auto;
        }

        .left {
            float: left;
        }

        img {
            float: left;
        }


        .right {
            float: left;
            margin-left: -39px;
        }

        .box .li-item {
            width: 50px;
            height: 20px;
            line-height: 20px;
            text-align: center;
            margin-top: 4px;
        }

        .box .li-item:hover {
            background-color: red;
        }
    </style>
</head>

<body>
    <div class="box">
        <ul class="left">
            <!-- <li class="li-item ">冬裙</li> -->
        </ul>
        <img src="images/冬裙.jpg" alt="" srcset="">
        <ul class="right">
            <!-- <li class="li-item">男包</li> -->
        </ul>
    </div>
    <script src="data/data.js"></script>
    <script src="js/jquery-3.4.1.min.js"></script>
    <script>
        initPro($('.left')[0], product[0]);

        $('.left .li-item').mouseenter(function () {
            var index = $(this).index();
            console.log(index);
            $('img')[0].src = 'images/' + product[0][index].img;
        })

        function initPro(el, arr) {
            str = '';
            for (var i = 0; i < arr.length; i++) {
                str += '<li id="li-' + i + '" class="li-item"> ' + arr[i].text + ' </li>';
            }
            el.innerHTML = str;
            // 表示str是el的内部结构
        }

        initPror($('.right')[0], product[1]);
        $('.right .li-item').mouseenter(function () {
            var index = $(this).index();
            console.log(index);
            $('img')[0].src = 'images/' + product[1][index].img;
        })


        function initPror(el1, arr1) {
            str1 = '';
            for (var i = 0; i < arr1.length; i++) {
                str1 += '<li id="li-' + i + '" class="li-item r"> ' + arr1[i].text + ' </li>';
            }
            el1.innerHTML = str1;
            // 表示str是el的内部结构
        }
    </script>
</body>
```
# jquery第二天
## css操作
```html
<body>
    <div class="box">
        不凡学院
    </div>
    <script src="js/jquery-3.4.1.min.js"></script>
    <script>
        $('.box').click(function () {
            console.log($(this).css('height')); // 获取对应的属性值
            $(this).css('color', 'red'); //  设置css样式
            $(this).css({
                'height': '30px',
                backgroundColor: 'blue',
                lineHeight: '30px'
            })
        })
    </script>
</body>
```
## attr操作
```html

    <div title="天气很好" class="box">
        不凡学院
    </div>
    <div title="下雨了" class="inner-box">
        xiyule
    </div>
    <script src="js/jquery-3.4.1.min.js"></script>
    <script>
        setAttribute getAttribute removeAttribute
        $('.box').click(function () {
            console.log($(this).attr('title'));
            $(this).attr('id', 'd1');
        })
        有则添加,无则删除 title属性
        $('.inner-box').click(function () {
            if ($(this).attr('title')) {
                $(this).removeAttr('title')
            } else {
                $(this).attr('title', 'henhao')
            }
        })
    </script>
```
## 内容操作
```html
<body>
    <p>不凡学院</p>
    <div class="box">
        box
    </div>
    <input type="text">
    <button>获取/设置输入框的值</button>
    <script src="js/jquery-3.4.1.min.js"></script>
    <script>
        // text()  innerText
        // html()   innerHTML
        // val()      value

        可以获取  可以设置
        $('p').mouseenter(function () {
            console.log($(this).text())
            $('p').text('今天天气很好');
        })
        $('.box').click(function () {
            console.log($(this).html());
            $(this).html('<p>我是一个盒子</p>');
        })
        $('button').click(function () {
            alert($('input').val());
            $('input').val('张三');
        })
    </script>
</body>
```
## 操作类
```html
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <meta http-equiv="X-UA-Compatible" content="ie=edge">
    <title>Document</title>
    <style>
        .strong {
            font-weight: bolder;

        }

        .em {
            font-style: italic;
        }

        .danger {
            color: red;
        }
    </style>
</head>

<body>
    <p>不凡学院</p>
    <button class="btn1">添加strong</button>
    <button class="btn2">添加danger</button>
    <button class="btn3">删除strong</button>
    <button class="btn4">切换em</button>
    <button class="btn5">是否存在danger</button>



    <script src="js/jquery-3.4.1.min.js"></script>
    <script>
        $('.btn1').click(function () {
            $('p').addClass('strong');
        })
        $('.btn3').click(function () {
            $('p').removeClass('strong')
        })
        $('.btn4').click(function () {
            $('p').toggleClass('em');
        })
        toggleClass追加一个类名
        $('.btn5').click(function () {
            // false  true
            alert($('p').hasClass('danger'));
            // alert($('p').hasClass());

        })
    </script>
</body>
```
## dom查找
```html
<body>
    <ul>
        <li class="li_1">li1</li>
        <li class="li_2">li2</li>
        <li class="li_3">li3</li>
        <li class="li_4">li4</li>
        <li class="li_5">li5</li>
        <li class="li_6">li6</li>
        <li class="li_7">li7</li>
        <li class="li_8">li8</li>
    </ul>
    <div class="box">
        <div class="inner-box">
            <p>bufanxueyuan</p>
        </div>
    </div>
    <script src="js/jquery-3.4.1.min.js"></script>
    <script>
        siblings()  所有兄弟
        parent()  父亲
        find()  所有后代
        children()
        eq()


        下一个兄弟  next()
        	nextUntil()	后面所有的兄弟直到…  不包含结束的节点
        // nextAll()
        $('.li_3').click(function () {
            $(this).next().css('color', 'red');
            $(this).nextAll().css('color', 'orange');
            $(this).nextUntil('.li_6').css('color', 'green');
        })
        	prev()	前面的兄弟
        	prevAll()		前面所有的兄弟
        	prevUntil()	

        	parents()		所有的父节点
        console.log($('p').parents()); // inner-box  box body html
        console.log($('p').parentsUntil('body')); // inner-box  box
    </script>
</body>
```
## jq动画
```html
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <meta http-equiv="X-UA-Compatible" content="ie=edge">
    <title>Document</title>
    <style>
        .box {
            display: none;
            width: 200px;
            height: 200px;
            background-color: red;
        }
    </style>
</head>

<body>
    <div class="box">
        不凡
    </div>
    <button class="btn1">显示</button>
    <button class="btn2">隐藏</button>
    <button class="btn3">滑入</button>
    <button class="btn4">滑出</button>
    <button class="btn5">滑入/滑出</button>
    <button class="btn6">淡入</button>
    <button class="btn7">淡出</button>
    <button class="btn8">淡入/滑出</button>
    <button class="btn9">fadeTo</button>





    <script src="js/jquery-3.4.1.min.js"></script>
    <script>
        // show()  hide()
        $('.btn1').click(function () {
            // $('.box').css('display', 'block');
            参数一  动画持续时间  毫秒  slow/normal/fast
            参数二  回调函数,动画执行结束后  做什么
            $('.box').show(2000, function () {
                $(this).text('下雨了');
                $(this).css('backgroundColor', 'orange')
            });
        })
        $('.btn2').click(function () {
            $('.box').hide('slow', function () {
                alert('动画结束了')
            })
        })

        1滑入动画效果
        $(xx).slideDown(speed,callback);
        注意：省略参数或者传入不合法的字符串，那么则使用默认值：400毫秒（同样适用于fadeIn/slideDown/slideUp）
        $(xx).slideUp();

        2滑入滑出切换动画效果
        // $(xx).slideToggle(speed,callback);
        $('.btn3').click(function () {
            $('.box').slideDown('fast', function () {
                console.log('动画结束了');
            })
        })
        $('.btn4').click(function () {
            $('.box').slideUp('normal', function () {
                console.log('动画结束了');
            })
        })
        $('.btn5').click(function () {
            $('.box').slideToggle('normal', function () {
                console.log('动画结束了');
            })
        })

        1 淡入动画效果
        $(xx).fadeIn(speed, callback);

        2 淡出动画效果
        $(xx).fadeOut(1000);

        3淡入淡出切换动画效果
        // $(xx).fadeToggle('fast',function(){});
        $('.btn6').click(function () {
            $('.box').fadeIn(1000, function () {
                console.log('动画结束了');
            })
        })
        $('.btn7').click(function () {
            $('.box').fadeOut(5000, function () {
                console.log('动画结束了');
            })
        })
        $('.btn8').click(function () {
            $('.box').fadeToggle(1500, function () {
                console.log('动画结束了');
            })
        })

        4改变透明度到某个值
        作用：调节匹配元素的不透明度 
        $(xx).fadeTo(1000, .5); //  0全透，1全不透
        $('.btn9').click(function () {
            $('.box').fadeTo(1500, .2, function () {
                console.log('动画结束了');
            })
        })
    </script>
</body>
```
## 自定义动画
```html
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <meta http-equiv="X-UA-Compatible" content="ie=edge">
    <title>Document</title>
    <style>
        .box {
            position: absolute;
            left: 0;
            top: 0;
            width: 200px;
            height: 200px;
            background-color: red;
        }

        .btn1 {
            position: fixed;
            left: 0;
            bottom: 100px;
        }

        .btn2 {
            position: fixed;
            left: 0;
            bottom: 60px
        }
    </style>
</head>

<body>
    <div class="box">
        不凡学院
    </div>

    <button class="btn1">动画开始</button>
    <button class="btn2">动画停止</button>

    <script src="js/jquery-3.4.1.min.js"></script>
    <script>
                2.4	自定义动画
        注意：所有能够执行动画的属性必须只有一个数字类型的值。
        语法：$(selector).animate(styles,speed,easing,callback)
        	第一个参数表示：要执行动画的CSS属性（必选）
         	第二个参数表示：执行动画时长（可选）
        	第三个参数表示：动画执行完后立即执行的回调函数（可选）

        $('.btn1').click(function () {
            opacity  透明度  0-1
            $('.box').animate({
                width: 300,
                left: '800px',
                opacity: .2
             linear表示线性运动,直线
            }, 2000, 'linear', function () {
                // $('.box').animate({
                //     left: '100px'
                // }, 1000)
            })
            上边动画结束,才会执行下边的动画
            $('.box').animate({
                left: '100px'
            }, 1000)
        })


        1.stop()
        作用：停止当前正在执行的动画
        为什么要停止动画？如果多个动画同时作用于一个单位上面，那么多个动画会进入排队。后一个动画的执行必须等前面的执行完毕。
        $('.btn2').click(function () {

            $('.box').stop(true, true);
        })

        2.stop(stopAll,goToEnd);
        stopAll  是否全部停止，默认false 停止队列中所有的动画
        goToEnd  是否将停止的动画  停止在当前动画的最后一个状态  
    </script>
```
## 节点操作
```html
<body>
    <div class="box">

    </div>
    <ul>
        <li></li>
        <li></li>
        <li class="li3"></li>
        <li class="li4">李</li>
        <li></li>
        <li></li>
    </ul>
    <button class="btn1">插入节点append</button>
    <button class="btn2">给多个元素append</button>
    <button class="btn3">after</button>
    <button class="btn4">删除节点</button>

    <script src="js/jquery-3.4.1.min.js"></script>
    <script>
        创建节点
        var $node = $('<p>不凡学院</p>');
        插入节点
        在元素的最后一个子元素后面追加元素：append($node或者标签字符串)
        注意存在 剪切效果
        $('.btn1').click(function () {
            $('.box').append($node);
            // appendTo
            // $node.appendTo($('.box'));
        })
        如果是给多个目标追加元素，那么方法的内部会复制多份这个元素，然后追加到多个目标里面去。
        $('.btn2').click(function () {
            $('li').append('<span>wspan</span>');
        })

        appendTo()
        作用：把$(selector)追加到node中去
        $(selector).appendTo(node);

         prepend()
        作用：在元素的第一个子元素前面追加内容或节点



        区分

        after()
        作用：在被选元素之后，作为兄弟元素插入内容或节点
        $(selector).after(node);

         before()
        作用：在被选元素之前，作为兄弟元素插入内容或节点
        // $(selector).before(node);
        $('.btn3').click(function () {
            $('.li3').after('<p>不凡</p>')
        })
        删除节点
        $(selector).empty(); 被选节点里边的内容
        $(selector).html(“”);
        $(selector).remove();  //会把对象也干掉
        $('.btn4').click(function () {
            // $('.li4').empty();
            // $('.li4').html('');
            $('.li4').remove()
        })
        复制节点
        console.log($('.box').clone()); // jq对象
    </script>
</body>
```
## 表单
```html
<body>
    男:<input class="men" type="radio" name="sex">
    女:<input class="women" type="radio" name="sex">
    爱好:
    足球: <input class="foot" type="checkbox" name="like">
    蓝球: <input class="basket" type="checkbox" name="like">
    <button class="btn1">获取状态</button>
    <button class="btn2">选中足球</button>

    <script src="js/jquery-3.4.1.min.js"></script>
    <script>
        获取单选框 或者 多选框的 状态  prop()
        $('.btn1').click(function () {
            console.log('单选框状态:男', $('.men').prop('checked'));
            console.log('单选框状态:女', $('.women').prop('checked'));
            console.log('多选框状态:足球', $('.foot').prop('checked'));
            console.log('多选框状态:篮球', $('.basket').prop('checked'));
        })
        $('.btn2').click(function () {
            $('.foot').prop('checked', true);
        })
    </script>
</body>
```
## bom相关
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
            position: relative;
            width: 200px;
            height: 300px;
            background-color: red;
            margin: 20px;
            border: 5px solid #333;
            padding: 20px;
        }

        .inner-box {
            position: absolute;
            left: 20px;
            top: 20px;
            width: 50px;
            height: 50px;
            background-color: blue;
        }

        .main {
            height: 1000px;

        }

        .footer {
            height: 1000px;
            background-color: red;
        }

        .top {
            position: fixed;
            right: 10px;
            bottom: 20px;
        }
    </style>
</head>

<body>
    <div class="box">
        不凡学院
        <div class="inner-box">

        </div>
    </div>
    <div class="main">

    </div>
    <div class="footer">

    </div>

    <button class="btn1">设置宽高</button>
    <button class="btn2">设置offset</button>
    <button class="btn3">设置position</button>
    <button class="btn4">获取scrollTop</button>
    <div class="top">
        回到顶部
    </div>



    <script src="js/jquery-3.4.1.min.js"></script>
    <script>
        height()  和  width()
        备选元素的 高度 和 宽度  num 类型
        可以获取  也可以 设置
        console.log($('.box').width());
        console.log($('.box').height());
        $('.btn1').click(function () {
            $('.box').width(500);
            $('.box').height(200);
        })

        offset() 
        作用：获取或设置元素相对于文档的位置
        对象  可以获取 left 和top 属性
        num 类型(设置获取)
        console.log('offset.left', $('.box').offset());
        $('.btn2').click(function () {
            $('.box').offset({
                left: 300,
                top: 100
            })
        })

        position() 
        作用：获取相对于其最近的具有定位的父元素的位置。
         注意  只能获取  不能设置
        console.log($('.inner-box').position());
        // $('.btn3').click(function () {
        //     $('.inner-box').position({
        //         left: 50,
        //         top: 50
        //     })
        // })


        scrollTop() 
         网页 被卷进去的高度
        作用：获取或者设置元素垂直方向滚动的位置
        $('.btn4').click(function () {
            document 本身 就是一个dom'对象
            console.log($(document.documentElement).scrollTop());
        })
        $('.top').click(function () {
            // $(document).scrollTop(0);
            $(document.documentElement).animate({
                scrollTop: 0
            }, 400)
        })
    </script>
```
## 手风琴
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
            width: 1000px;
            height: 400px;
            margin: 100px auto;
            overflow: hidden;
        }

        .box .img {
            float: left;
            width: 200px;
            height: 100%;
        }
    </style>
</head>

<body>
    <div class="box">
        <div class="img">
            <img src="img/m1.jpg" alt="">
        </div>
        <div class="img">
            <img src="img/m2.jpg" alt="">
        </div>
        <div class="img">
            <img src="img/m3.jpg" alt="">
        </div>
        <div class="img">
            <img src="img/m4.jpg" alt="">
        </div>
        <div class="img">
            <img src="img/m5.jpg" alt="">
        </div>
    </div>
    <script src="js/jquery-3.4.1.min.js"></script>
    <script>
        先实现基本功能
        优化   分析bug  产生的原因
        防抖
        var currentLi;
        var timer;
        $('.img').mouseenter(function () {
            清除之前没有开始的定时器
            clearTimeout(timer);
            // currentLi = this;
            var $that = $(this);
            鼠标停留200ms  才会触发动画
            延迟hover
            timer = setTimeout(function () {
                currentLi = $that;
                $that.siblings().animate({
                    width: 100
                }, 400);
                $that.animate({
                    width: 600
                }, 400)
            }, 200)
        })
        $('.box').mouseleave(function () {
            clearTimeout(timer);
            $(currentLi).animate({
                width: 200
            }, 400)
            $(currentLi).siblings().animate({
                width: 200
            }, 400);
        })
    </script>
</body>
```
## 表格案例
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

        .modal {
            display: none;
            position: fixed;
            left: 0;
            top: 0;
            width: 100%;
            height: 100%;
            background-color: rgba(0, 0, 0, .5);
        }

        .modal .form {
            position: absolute;
            left: 50%;
            top: 50%;
            /* transform:translate(-50%,-50%); */
            margin-left: -150px;
            margin-top: -200px;
            width: 300px;
            height: 400px;
            padding: 20px;
            background-color: #fff;
        }
    </style>
</head>

<body>
    <table border="2" cellspacing=10 cellpadding=10>
        <!-- <tr><th>姓名</th><th>年龄</th><th>性别</th><th>操作</th></tr> -->
        <!-- <tr><td>张三</td><td>18</td><td>男</td><td><button class="edit">编辑</button><button class="del">删除</button></td></tr> -->
    </table>
    <div class="modal">
        <div class="form">
            姓名: <input class="username" type="text"> <br>
            年龄: <input class="age" type="text"> <br>
            性别: <br>
            男: <input class="sex men" type="radio" name="sex" value="1">
            女: <input class="sex women" type="radio" name="sex" value="0">
            <br>
            <button class="save" onclick="save()">确定</button>
            <button onclick="cancel()" class="cancel">取消</button>

        </div>
    </div>
    <script src="js/jquery-3.4.1.min.js"></script>
    <script>
        var users = [{
                name: '张三',
                age: 18,
                sex: '男'
            },
            {
                name: '王五',
                age: 22,
                sex: '男'
            },
            {
                name: '赵六',
                age: 26,
                sex: '男'
            },
            {
                name: '小红',
                age: 22,
                sex: '女'
            }
        ];
        动态生成表格
        initTable($('table'), users);
        var $currentTr;

        function initTable($el, arr) {
            var str = '<tr><th>姓名</th><th>年龄</th><th>性别</th><th>操作</th></tr>';
            for (var i = 0; i < arr.length; i++) {
                str +=
                    '<tr><td>' + arr[i].name + '</td><td>' + arr[i].age + '</td><td>' + arr[i].sex +
                    '</td><td><button class="edit" onclick="edit(this)">编辑</button><button class="del" onclick="del(this)">删除</button></td></tr>'
            }
            $el.html(str);
        }

        删除操作
        function del(obj) {
            把这个按钮所在的这一行突然删掉
            $(obj).parent().parent().remove();
        }
        编辑操作
        function edit(obj) {
            打开弹窗
            // $('.modal').css('display', 'block');
            $('.modal').show(400);
             填充表单
            $currentTr = $(obj).parent().parent();
            var children = $(obj).parent().parent().children();
            $('.username').val(children.eq(0).text());
            $('.age').val(children.eq(1).text());
            children.eq(2).text() == '男' ? $('.sex.men').prop('checked', true) : $('.sex.women').prop('checked', true)
        }

        取消
        function cancel() {
            // $('.modal').css('display', 'none');
            $('.modal').hide(400);
            清空表单
            $('.username').val('');
            $('.age').val('');
            $('.sex').prop('checked', false);
        }

        确定
        function save() {
            获取表单新的填入内容
            var username = $('.username').val();
            var age = $('.age').val();
            var sex = $('.sex:checked').val() == 0 ? '女' : '男';

            console.log(sex)
            更新表格
            $currentTr.children().eq(0).text(username);
            $currentTr.children().eq(1).text(age);
            $currentTr.children().eq(2).text(sex);
            调用cancel
            cancel();
        }
    </script>
</body>
```
# jquery第三天
## on方式绑定事件
```html
<body>
    <div class="box">
        不凡学院
    </div>
    <button class="btn">off解绑</button>
    <script src="lib/jquery-3.4.1.min.js"></script>
    <script>
        // $('.box').click(function () {

        // })

        $('.box').on('click', function () {
            事件处理程序
            console.log('天气很好')
        })
        $('.box').on('mouseenter', function () {
            事件处理程序
            console.log('天气')
        })

        on方式绑定,off解绑事件
        $('.btn').click(function () {
            取消了 box上的所有事件
            // $('.box').off();
            $('.box').off('click');

        })
    </script>
</body>
```
## 事件委托
```html
<body>
    <div class="box">
        <p>不凡学院</p>
    </div>
    <div class="btn">添加一个p标签</div>
    <script src="lib/jquery-3.4.1.min.js"></script>
    <script>
        $('.btn').click(function () {
            $('.box').append('<p>不凡学院1</p>');
        })
        // $('p').click(function () {
        //     console.log('天气很好')
        // })
        想实现 后来添加的元素也具备点击事件
        事件委托
        $('.box').on('click', 'p', function () {
            console.log('天气很好');
        })
    </script>
</body>
```
## 事件对象
```html
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <meta http-equiv="X-UA-Compatible" content="ie=edge">
    <script src="lib/jquery-3.4.1.js"></script>
    <title>Document</title>
    <style>
        .box {
            width: 100px;
            height: 100px;
            background-color: red;
        }

        .inner-box {
            width: 50px;
            height: 50px;
            background-color: green;
        }
    </style>
</head>

<body>
    <div class="box">
        <div class="inner-box">

        </div>
    </div>
    <button>触发box点击事件</button>

    <input type="text">
    <p class="text"></p>
    <script>
        事件触发时,给你的附加信息
        $('.box').click(function (event) {
            console.log('我是外部盒子');
            console.log(event)
            console.log('this', this);
            currentTarget   this  指向一样 事件绑定的对象
            target  实际触发的对象
            console.log('target', event.target);
            console.log('currentTarget', event.currentTarget);
        })
        $('input').keyup(function () {
            监听到 你按下的是哪个  按键
            console.log(event.keyCode);
            if (event.keyCode === 13) {
                var val = $(this).val();
                $('p').text(val);
            }
            敲回车时 ,更新text
        })
    </script>
</body>
```
## 阻止冒泡和默认
```html
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <meta http-equiv="X-UA-Compatible" content="ie=edge">
    <title>Document</title>
    <style>
        .box {
            width: 100px;
            height: 100px;
            background-color: red;
        }

        .inner-box {
            width: 50px;
            height: 50px;
            background-color: #fff;
        }
    </style>
</head>

<body>
    <div class="box">
        我是外部盒子
        <div class="inner-box">
            我是内部盒子
        </div>
    </div>
    <a target="_blank" href="https://www.baidu.com/?tn=44004473_1_oem_dg">百度</a>
    <script src="lib/jquery-3.4.1.min.js"></script>
    <script>
        $('.box').click(function () {
            console.log('外部盒子')
        })
        $('.inner-box').click(function (event) {
            阻止冒泡
            event.stopPropagation();
            console.log('内部盒子');
        })
        $('a').click(function () {
            不想触发磨人的事件
            阻止默认事件
            event.preventDefault();
            console.log('a标签');
        })
    </script>
</body>
```
## 事件触发
```html
<body>
    <div class="box">
        不凡学院
    </div>
    <button class="btn">触发box的点击事件</button>
    <script src="lib/jquery-3.4.1.min.js"></script>
    <script>
        $('.box').click(function () {
            console.log('点击了')
        })
        $('.btn').click(function () {
            触发box的点击事件
            $('.box').click();
            // $('.box').trigger('click');
            // $('.box').triggerHandler('click');
        })
    </script>
</body>
```
## 链式编程
```html
<body>
    <div class="box">
        不凡学院
        <div class="inner-box">
            内部
        </div>
    </div>
    <script src="lib/jquery-3.4.1.min.js"></script>
    <script>
        $('.box').click(function () {
            链式操作
            链式编程原理：return this;  调用”任何”一个方法都是返回了对象本身
            通常情况下，只有设置操作才能把链式编程延续下去。因为获取操作的时候，会返回获取到的相应的值，无法返回 this。
            $(this).css('width', '200px').attr('class', 'title').css('height', '400px').css('backgroundColor',
                'red');
            // $(this).css('width').attr('class', 'title').css('height', '400px').css('backgroundColor',
            //     'red');
        })
        $('.inner-box').click(function (event) {
            event.stopPropagation();
            end(); // 结束当前链最近的一次过滤操作，并且返回匹配元素之前的状态。
            这里的end是结束对父元素的设置
            $(this).css('backgroundColor', 'blue').parent().css('height', '200px').css('background-color',
                'orange').end().attr('title', 'tianqi');
            // $('.box').css()
        })
    </script>
</body>
```
## 隐式迭代
```html
<body>
    <ul>
        <li>1</li>
        <li>2</li>
        <li>3</li>
        <li>4</li>
        <li>5</li>
        <li>6</li>
    </ul>
    <button class="btn">点击获取</button>
    <script src="lib/jquery-3.4.1.min.js"></script>
    <script>
        隐式迭代的意思是：在方法的内部会为匹配到的所有元素进行循环遍历，执行相应的方法；而不用我们再进行循环，简化我们的操作，方便我们调用。
        如果获取的是多元素的值，大部分情况下返回的是第一个元素的值
        $('li').click(function () {
            console.log($(this).text())
        })
        $('.btn').click(function () {
            console.log($('li').html());
            console.log($('li').text());
        })
    </script>
</body>
```
## each
```html
<body>
    <ul>
        <li>li_1</li>
        <li>li_2</li>
        <li>li_3</li>
        <li>li_4</li>
        <li>li_5</li>
        <li>li_6</li>
    </ul>
    <script src="lib/jquery-3.4.1.min.js"></script>
    <script>
            大部分情况下是不需要使用each方法的，因为jQuery的隐式迭代特性。
        如果要对每个元素做不同的处理，这时候就用到了each方法

        // $('li').click(function () {

        // })
        $('li').each(function (index, ele) {
            ele 正在遍历的元素  dom对象
            index  当前遍历元素  的下标
            if (index >= 3) {
                ele.onclick = function () {
                    console.log($(this).text());
                }
            }
        })
    </script>
</body>
```
## 五角星评分
```html
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <meta http-equiv="X-UA-Compatible" content="ie=edge">
    <title>Document</title>
    <style>
        .box {
            font-size: 24px;
            color: orange;
        }

        span {
            cursor: pointer;
        }
    </style>
</head>

<body>
    <div class="box">
        <span>☆</span>
        <span>☆</span>
        <span>☆</span>
        <span>☆</span>
        <span>☆</span>
    </div>

    <script src="lib/jquery-3.4.1.min.js"></script>
    <script>
        $('span.active').text('★').prevAll().text('☆');
        $('span').mouseenter(function () {
            $(this).text('★').prevAll().text('★');
            $(this).nextAll().text('☆');

        })
        $('.box').mouseleave(function () {
            if (!$('span.active')) {
                $('span').text('☆');
            } else {
                $('span.active').text('★').prevAll().text('★');
            }
        })
        // $('span').mouseleave(function () {
        //     $(this).text('☆')
        // })
        $('span').click(function () {
            $(this).addClass('active');
        })
    </script>
</body>
```
## 多库共存
```html
<body>
    <script src="lib/jquery-3.4.1.min.js"></script>
    <script>
        $.noConflict();让jQuery释放对$的控制权，让其他库能够使用$符号，达到多库共存的目的。
        此后，只能使用jQuery来调用jQuery提供的方法
        $.noConflict();
        var $ = 'abc';
    </script>
</body>
```
## jq-color
```html
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <meta http-equiv="X-UA-Compatible" content="ie=edge">
    <title>Document</title>
    <style>
        .box {
            width: 200px;
            height: 200px;
            background-color: rgb(0, 0, 0);
        }
    </style>
</head>

<body>
    <div class="box">

    </div>
    引入依赖库
    <script src="lib/jquery-3.4.1.min.js"></script>
    引入核心库
    <script src="lib/jquery.color.js"></script>
    <script>
        十六进制 预定义颜色  rgb  都可以
        $('.box').click(function () {
            console.log($(this));
            $(this).animate({
                width: 300,
                height: 300,
                backgroundColor: 'rgb(255,255,255)'
            }, 'slow')
        })
    </script>
</body>
```
## lightbox
```html
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <meta http-equiv="X-UA-Compatible" content="ie=edge">
    引入css库(如果有的话)
    <link href="lightbox/css/lightbox.min.css" rel="stylesheet">
    <title>Document</title>
</head>

<body>
    <a href="img/m1.jpg" data-lightbox="roadtrip" data-title="My caption">
        <img src="img/m1.jpg" alt="">
    </a>
    <a href="img/m2.jpg" data-lightbox="roadtrip" data-title="My caption">
        <img src="img/m2.jpg" alt="">
    </a>
    引入依赖库
    <script src="lib/jquery-3.4.1.min.js"></script>
    引入核心库
    <script src="lightbox/js/lightbox.min.js"></script>
    <!-- <script>
        lightbox.option({
            'resizeDuration': 200,
            'wrapAround': true
        })
    </script> -->
</body>
```
## swiper
```html
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <meta http-equiv="X-UA-Compatible" content="ie=edge">
    <link rel="stylesheet" href="css/swiper.min.css">
    <script src="lib/jquery-3.4.1.min.js"></script>
    <script src="lib/swiper.min.js"></script>
    <title>Document</title>
    <style>
        .swiper-container {
            width: 1226px;
            height: 460px;
            margin: 100px auto;
        }

        .swiper-container .swiper-button-prev {
            width: 30px;
            height: 70px;
            left: 0;
            background: none;
        }

        .swiper-container .swiper-pagination-bullet:hover {
            background-color: #007aff;
            opacity: 1;
        }

        .swiper-container .swiper-pagination-bullet {
            width: 16px;
            height: 16px;
            font-size: 12px;
            line-height: 16px;

        }
    </style>
</head>

<body>
    <div class="swiper-container">
        <div class="swiper-wrapper">
            <div class="swiper-slide">
                <img src="img/m1.jpg" alt="" srcset="">
            </div>
            <div class="swiper-slide">
                <img src="img/m2.jpg" alt="" srcset="">
            </div>
            <div class="swiper-slide">
                <img src="img/m3.jpg" alt="" srcset="">
            </div>
            <div class="swiper-slide">
                <img src="img/m4.jpg" alt="" srcset="">
            </div>
            <div class="swiper-slide">
                <img src="img/m5.jpg" alt="" srcset="">
            </div>
            <div class="swiper-slide">
                <img src="img/m6.jpg" alt="" srcset="">
            </div>
        </div>
        如果需要分页器
        <div class="swiper-pagination"></div>

        如果需要导航按钮
        <div class="swiper-button-prev">
            <</div> <div class="swiper-button-next">
        </div>

        如果需要滚动条
        <!-- <div class="swiper-scrollbar"></div> -->
    </div>
    导航等组件可以放在container之外

    <script>
        swiper  的实例对象
        var mySwiper = new Swiper('.swiper-container', {
            direction: 'vertical', // 垂直切换选项
            loop: true, // 循环模式选项
            autoplay: {
                delay: 3000, //3秒切换一次
            },
            // effect: 'coverflow',
            // grabCursor: true,
            // centeredSlides: true,
            // slidesPerView: 'auto',
            // coverflowEffect: {
            //     rotate: 50,
            //     stretch: 0,
            //     depth: 100,
            //     modifier: 1,
            //     slideShadows: true,
            // },

            如果需要分页器
            pagination: {
                el: '.swiper-pagination',
                clickable: true,
                renderBullet: function (index, className) {
                    return '<span class="' + className + '">' + (index + 1) + '</span>';
                },
            },

            如果需要前进后退按钮
            navigation: {
                nextEl: '.swiper-button-next',
                prevEl: '.swiper-button-prev',
            },

            如果需要滚动条
            // scrollbar: {
            //     el: '.swiper-scrollbar',
            // },
        })
    </script>
</body>
```
## 表格新增用户
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

        .modal {
            display: none;
            position: fixed;
            left: 0;
            top: 0;
            width: 100%;
            height: 100%;
            background-color: rgba(0, 0, 0, .5);
        }

        .modal .form {
            position: absolute;
            left: 50%;
            top: 50%;
            /* transform:translate(-50%,-50%); */
            margin-left: -150px;
            margin-top: -200px;
            width: 300px;
            height: 400px;
            padding: 20px;
            background-color: #fff;
        }
    </style>
</head>

<body>
    <button class="add">添加</button>
    <table border="2" cellspacing=10 cellpadding=10>
        <!-- <tr><th>姓名</th><th>年龄</th><th>性别</th><th>操作</th></tr> -->
        <!-- <tr><td>张三</td><td>18</td><td>男</td><td><button class="edit">编辑</button><button class="del">删除</button></td></tr> -->
    </table>
    <div class="modal">
        <div class="form">
            姓名: <input class="username" type="text"> <br>
            年龄: <input class="age" type="text"> <br>
            性别: <br>
            男: <input class="sex men" type="radio" name="sex" value="1">
            女: <input class="sex women" type="radio" name="sex" value="0">
            <br>
            <button class="save" onclick="save()">确定</button>
            <button onclick="cancel()" class="cancel">取消</button>

        </div>
    </div>

    <script src="lib/jquery-3.4.1.min.js"></script>
    <script>
        var users = [{
                name: '张三',
                age: 18,
                sex: '男'
            },
            {
                name: '王五',
                age: 22,
                sex: '男'
            },
            {
                name: '赵六',
                age: 26,
                sex: '男'
            },
            {
                name: '小红',
                age: 22,
                sex: '女'
            }
        ];
        动态生成表格
        initTable($('table'), users);
        var $currentTr;
        var isEdit;

        function initTable($el, arr) {
            var str = '<tr><th>姓名</th><th>年龄</th><th>性别</th><th>操作</th></tr>';
            for (var i = 0; i < arr.length; i++) {
                str +=
                    '<tr><td>' + arr[i].name + '</td><td>' + arr[i].age + '</td><td>' + arr[i].sex +
                    '</td><td><button class="edit" onclick="edit(this)">编辑</button><button class="del" onclick="del(this)">删除</button></td></tr>'
            }
            $el.html(str);
        }

        删除操作
        function del(obj) {
            把这个按钮所在的这一行突然删掉,先删td,再删tr
            $(obj).parent().parent().remove();
        }
        编辑操作
        function edit(obj) {
            打开弹窗
            // $('.modal').css('display', 'block');
            $('.modal').show(400);
            isEdit = true;
             填充表单
            $currentTr = $(obj).parent().parent();
            var children = $(obj).parent().parent().children();
            $('.username').val(children.eq(0).text());
            $('.age').val(children.eq(1).text());
            children.eq(2).text() == '男' ? $('.sex.men').prop('checked', true) : $('.sex.women').prop('checked', true)
        }

        取消
        function cancel() {
            // $('.modal').css('display', 'none');
            $('.modal').hide(400);
            清空表单
            $('.username').val('');
            $('.age').val('');
            $('.sex').prop('checked', false);
        }

        确定
        function save() {
            获取表单新的填入内容
            var username = $('.username').val();
            var age = $('.age').val();
            var sex = $('.sex:checked').val() == 0 ? '女' : '男';

            console.log(sex);
            if (isEdit) {
                更新表格
                $currentTr.children().eq(0).text(username);
                $currentTr.children().eq(1).text(age);
                $currentTr.children().eq(2).text(sex);
            } else {
                新增信息
                var str =
                    '<tr><td>' + username + '</td><td>' + age + '</td><td>' + sex +
                    '</td><td><button onclick="edit(this)" class="edit">编辑</button><button onclick="del(this)" class="del">删除</button></td></tr>';
                $('table').append(str);

            }

            调用cancel
            cancel();
        }
        添加数据
        $('.add').click(function () {
            $('.modal').show(400);
            isEdit = false;
        })
    </script>
</body>
```
# jquery第四天
## 乘法表
```html
<body>
	<script>
		for (var i = 1; i < 10; i++) {
			var str ='';
			for (var j = 1; j <=i; j++) {
				str+=''+i+'*'+j+'='+i*j+' ';
			}
			console.log(str);
		}
	</script>
</body>
```
## 南丁格尔图
```html
<body>
    在绘图前我们需要为 ECharts 准备一个具备高宽的 DOM 容器。
    <div id="main" style="width: 600px;height:400px;"></div>
    然后就可以通过 echarts.init 方法初始化一个 echarts 实例并通过 setOption 方法生成一个简单的柱状图，
    <script>
        基于准备好的dom，初始化echarts实例
        var myChart = echarts.init(document.getElementById('main'));
        指定图表的配置项和数据
        var option = {
            title: {
                text: '南丁格尔图',
            },
            backgroundColor: '#2c343c',
            textStyle: {
                color: 'rgba(255, 255, 255, 0.3)'
            },
            visualMap: {
                不显示 visualMap 组件，只用于明暗度的映射
                show: false,
                映射的最小值为 80
                min: 80,
                映射的最大值为 600
                max: 600,
                inRange: {
                    明暗度的范围是 0 到 1
                    colorLightness: [0, 1]
                }
            },
            series: [{
                name: '访问来源',
                type: 'pie',
                radius: '80%',
                roseType: 'angle',
                itemStyle: {
                    设置扇形的颜色
                    color: '#c23531',
                    阴影的大小
                    shadowBlur: 200,
                    阴影水平方向上的偏移
                    shadowOffsetX: 0,
                    阴影垂直方向上的偏移
                    shadowOffsetY: 0,
                    阴影颜色
                    shadowColor: 'rgba(0, 0, 0, 0.5)'
                },
                labelLine: {
                    lineStyle: {
                        color: 'rgba(255, 255, 255, 0.3)'
                    }
                },
                data: [{
                        value: 235,
                        name: '视频广告',
                        itemStyle: {
                            color: '#c23531',
                        }
                    },
                    {
                        value: 274,
                        name: '联盟广告'
                    },
                    {
                        value: 310,
                        name: '邮件营销'
                    },
                    {
                        value: 335,
                        name: '直接访问'
                    },
                    {
                        value: 400,
                        name: '搜索引擎'
                    }
                ]
            }]
        }
        使用刚指定的配置项和数据显示图表。
        myChart.setOption(option);
    </script>
</body>
```
## 折线图
```html
<body>
    在绘图前我们需要为 ECharts 准备一个具备高宽的 DOM 容器。
    <div id="main" style="width: 600px;height:400px;"></div>
    然后就可以通过 echarts.init 方法初始化一个 echarts 实例并通过 setOption 方法生成一个简单的柱状图，
    <script>
        基于准备好的dom，初始化echarts实例
        var myChart = echarts.init(document.getElementById('main'));
        指定图表的配置项和数据
        var option = {
            xAxis: {
                type: 'category',
                data: ['Mon', 'Tue', 'Wed', 'Thu', 'Fri', 'Sat', 'Sun']
            },
            yAxis: {
                type: 'value'
            },
            series: [{
                data: [820, 932, 901, 934, 1290, 1330, 1320],
                type: 'line',
                areaStyle: {

                },
                smooth: true
            }]
        }
        使用刚指定的配置项和数据显示图表。
        myChart.setOption(option);
    </script>
</body>
```
## 散点图
```html
<body>
    在绘图前我们需要为 ECharts 准备一个具备高宽的 DOM 容器。
    <div id="main" style="width: 600px;height:400px;"></div>
    然后就可以通过 echarts.init 方法初始化一个 echarts 实例并通过 setOption 方法生成一个简单的柱状图，
    <script>
        基于准备好的dom，初始化echarts实例
        var myChart = echarts.init(document.getElementById('main'));
        指定图表的配置项和数据
        var option = {
            xAxis: {},
            yAxis: {},
            series: [{
                symbolSize: 60,
                data: [
                    [10.0, 8.04],
                    [8.0, 6.95],
                    [13.0, 7.58],
                    [9.0, 8.81],
                    [11.0, 8.33],
                    [14.0, 9.96],
                    [6.0, 7.24],
                    [4.0, 4.26],
                    [12.0, 10.84],
                    [7.0, 4.82],
                    [5.0, 5.68]
                ],
                type: 'scatter'
            }]
        }
        使用刚指定的配置项和数据显示图表。
        myChart.setOption(option);
    </script>
</body>
```
## 漏斗图
```html
<body>
    在绘图前我们需要为 ECharts 准备一个具备高宽的 DOM 容器。
    <div id="main" style="width: 600px;height:400px;"></div>
    然后就可以通过 echarts.init 方法初始化一个 echarts 实例并通过 setOption 方法生成一个简单的柱状图，
    <script>
        基于准备好的dom，初始化echarts实例
        var myChart = echarts.init(document.getElementById('main'));
        指定图表的配置项和数据
        var option = {
            title: {
                text: '漏斗图',
                subtext: '纯属虚构'
            },
            tooltip: {
                trigger: 'item',
                formatter: "{a} <br/>{b} : {c}%"
            },
            toolbox: {
                feature: {
                    dataView: {
                        readOnly: false
                    },
                    restore: {},
                    saveAsImage: {}
                }
            },
            legend: {
                data: ['展现', '点击', '访问', '咨询', '订单']
            },
            calculable: true,
            series: [{
                name: '漏斗图',
                type: 'funnel',
                left: '10%',
                top: 60,
                //x2: 80,
                bottom: 60,
                width: '80%',
                // height: {totalHeight} - y - y2,
                min: 0,
                max: 100,
                minSize: '0%',
                maxSize: '100%',
                sort: 'descending',
                gap: 2,
                label: {
                    show: true,
                    position: 'inside'
                },
                labelLine: {
                    length: 10,
                    lineStyle: {
                        width: 1,
                        type: 'solid'
                    }
                },
                itemStyle: {
                    borderColor: '#fff',
                    borderWidth: 1
                },
                emphasis: {
                    label: {
                        fontSize: 20
                    }
                },
                data: [{
                        value: 60,
                        name: '访问'
                    },
                    {
                        value: 40,
                        name: '咨询'
                    },
                    {
                        value: 20,
                        name: '订单'
                    },
                    {
                        value: 80,
                        name: '点击'
                    },
                    {
                        value: 100,
                        name: '展现'
                    }
                ]
            }]
        };
        使用刚指定的配置项和数据显示图表。
        myChart.setOption(option);
    </script>
</body>
```
## 条形图
```html
<body>
    在绘图前我们需要为 ECharts 准备一个具备高宽的 DOM 容器。
    <div id="main" style="width: 600px;height:400px;"></div>
    然后就可以通过 echarts.init 方法初始化一个 echarts 实例并通过 setOption 方法生成一个简单的柱状图，
    <script>
        基于准备好的dom，初始化echarts实例
        var myChart = echarts.init(document.getElementById('main'));
        指定图表的配置项和数据
        var option = {
            title: {
                text: 'ECharts 入门示例'
            },
            tooltip: {},
            legend: {
                data: ['销量', '进货量']
            },
            xAxis: {
                data: ["衬衫", "羊毛衫", "雪纺衫", "裤子", "高跟鞋", "袜子"]
            },
            yAxis: {},
            series: [{
                name: '销量',
                type: 'bar',
                data: [5, 20, 36, 10, 10, 20]
            }, {
                name: '进货量',
                type: 'bar',
                data: [20, 40, 86, 90, 30, 40]
            }]
        }
        使用刚指定的配置项和数据显示图表。
        myChart.setOption(option);
    </script>
</body>
```



