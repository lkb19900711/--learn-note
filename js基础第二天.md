# Date对象(重要)
```html
    <script>
        var obj = {
            name: '张三',
            sex: '男',
            age: 24,
            say: function () {
                alert('你好')
            }
        }

        获取对象的属性  对象名.xx
        console.log(obj.name);
        console.log(obj.sex);
        console.log(obj.say);


        对象的属性值  是 函数的话 咱们就把它成为对象的方法
        调用对象的方法  对象名.xx()
        函数执行  函数名()
        obj.say();

        属性  :   小狗的 颜色  体重  身高
        方法:  小狗跑  跳  叫  


        js的内置对象  Date   Math
        使用:

        构造函数 创建了  Date 这个构造函数的 实例对象
        var date = new Date(); // 这句代码执行时: 当前 的  时间对象
        console.log(date); // Fri Jul 05 2019 09:40:06 GMT+0800 (中国标准时间)

        "2017/09/06 09:00:00
        var date1 = new Date('2017/09/06 09:00:00');
        console.log(date1); // Wed Sep 06 2017 09:00:00 GMT+0800 (中国标准时间)

        获取当前时间 的   年   月   日   时  分  秒  毫秒
        var year = date.getFullYear();
        console.log(year);
        var month = date.getMonth() + 1; // getMonth() 值  0---11
        console.log(month); // 6  代表 7月

        var day = date.getDate();
        console.log(day);

        var weekDay = date.getDay();
        console.log(weekDay);

        var hour = date.getHours();
        var min = date.getMinutes();
        var second = date.getSeconds();
        毫秒  1s == 1000ms
        var mSecond = date.getMilliseconds();

        console.log(hour);
        console.log(min);
        console.log(second);
        console.log(mSecond);

        '2019年7月5日 9时50分45秒'
        var str = year + '年' + month + '月' + day + '日 ' + hour + '时' + min + '分' + second + '秒';
        无脑用加号拼接字符,空白字符有没有无所谓
        var str = '' + year + '年' + month + '月' + day + '日 ' + hour + '时' + min + '分' + second + '秒';
        console.log(str)

        时间戳
        var stamp = date.getTime();
        console.log(stamp); // 1562291948129
        从格林威治标准时间的1970年1月1日，0时0分0秒到当前日期所花费的毫秒数（1 秒 = 1000 毫秒）
    </script>
```
# Math对象
```html
    <script>
        Math 一些 数学方法的 工具库
        .ceil()  向上  取整  (天花板函数)
        var a = Math.ceil(19.28);

        console.log(a);

        console.log(Math.ceil(19.99)); // 20

        console.log(Math.ceil(-19.28)); // -19

        .floor()  向下取整  地板函数
        console.log(Math.floor(19.28)); // 19
        console.log(Math.floor(-19.28)); // -20

        .max()  取 多个数的  最大值

        console.log(Math.max(9, 19, 23)); // 23

        .min()   取最小
        console.log(Math.min(5, 9, 23)); // 5

        .pow(x,y)  x的 y次方

        console.log(Math.pow(2, 8)); // 256

        Math.random()	生成 0-1 之间的随机数  [0,1)
        console.log(Math.random())

        生成 [1,10]  范围的随机数  整数
        [0,9] + 1
        Math.floor(Math.random() * 10) + 1;
        console.log(Math.floor(Math.random() * 10) + 1);
        [5,10]
        [0,5]+5
        console.log(Math.floor(Math.random() * 6) + 5);

        规律: Math.floor(Math.random()*个数)+最小值


        Math.round()	四舍五入取整（正数四舍五入，负数五舍六入）
        console.log(Math.round(2.4)); // 2
        console.log(Math.round(2.9)); // 3
        console.log(Math.round(2.4999999999)); // 2
        console.log(Math.round(2.499999999999999999999999999999999999)); // 3
        // 存在误差
        console.log(2.499999999999999999999999999999999999); // 2.5
    </script>
```
# 逻辑运算符(重要)
```html
    <script>
        && 与(且) 两个真 才为真

        ||或 有一个真 即为 真
        !非 取反

        判断一个人的年龄是否在 18-60 岁之间
        var age = prompt('请输入年龄');
        var age = 20;
        18<age<60 没有这种写法
        大于18  并且  小于60
        console.log(age > 18 && age < 60); // 

        短路运算
        && 果第一个值为 false，则不会看第二个值
        true && alert("看我出不出来！！"); // 弹出
        false && alert("看我出不出来！！"); // 没有弹出
        // && 遇到 false 就返回


        || 短路运算 遇到true 就返回
        true || alert('第二个值');
        false || alert('第二个值');

        如果对非布尔值进行 非运算， 则会先将其转换为布尔值， 然后再操作。 举例：
        var a = 10;
        a = !a;

        console.log(a); // false
        console.log(typeof a); // boolean

        非布尔值的 与 或  运算【重要】
        非布尔值进行与或运算时，会先将其转换为布尔值，然后再运算，但返回结果是原值。比如说：
        var result = 5 || 6; // 
        console.log(result); // 5

        console.log(5 && 6); // 6

        console.log('' || 8); // 8
    </script>
```
3 if语句
```html
     <script>
        var age = 17;
        条件判断  如果 在 18-60 之间  弹出 你可以考驾照
        if (age > 18 && age < 60) {
             符合条件就执行 true
            alert('可以考驾照');
        }

        不符合条件  告诉  它 不和条件

        条件分支语句

        if (条件表达式) {
            条件为真时，做的事情
        } else {
            条件为假时，做的事情
        }
        if (age > 18 && age < 60) {
            alert('可以考驾照');
        } else {
             不符合条件时 执行
            alert('不可以考驾照')
        }

        多分支条件语句
        if (条件表达式1) {
            // 条件1为真时，做的事情
        } else if (条件表达式2) {
            // 条件1不满足，条件2满足时，做的事情
        } else if (条件表达式3) {
            // 条件1、2不满足，条件3满足时，做的事情
        } else {
            // 条件1、2、3都不满足时，做的事情
        }

            根据BMI（身体质量指数）显示一个人的体型。
        BMI指数，就是体重、身高的一个计算公式。公式是：
        BMI =体重÷身高的平方

        比如，老师的体重是81.6公斤，身高是1.71米。
        那么老师的BMI就是  81.6 ÷ 1.712     等于 27.906022365856163

        过轻：低于18.5
        正常：18.5-24.99999999
        过重：25-27.9999999
        肥胖：28-32
        非常肥胖, 高于32

        用JavaScript开发一个程序，让用户先输入自己的体重，然后输入自己的身高（弹出两次prompt框）。
        计算它的BMI，根据上表，弹出用户的身体情况。比如“过轻” 、 “正常” 、“过重” 、 “肥胖” 、“非常肥胖”。
        var w = prompt('请输入体重,单位kg');
        var h = prompt('请输入身高,单位M');
        var BMI = w / (h * h);
        console.log(BMI)
        if (BMI <= 18.5) {
            alert('过轻')
        } else if (BMI < 25) {
            暗含了 不满足上边的条件
            alert('正常')
        } else if (BMI < 28) {
            alert('GUOZHONG')
        } else if (BMI < 32) {
            alert('肥胖')
        } else {
            alert('非常肥胖')
        }
    </script>
```
# if语句嵌套
```html
    <script>
        一个加油站为了鼓励车主多加油，所以加的多有优惠。
        92号汽油，每升6元；如果大于等于20升，那么每升5.9；
        97号汽油，每升7元；如果大于等于30升，那么每升6.95
        编写JS程序，用户输入自己的汽油编号，然后输入自己加多少升，弹出价格。
        var type = prompt('请输入汽油编号(92或者97):');
        var num = prompt('请输入加油的数量:');
        var price;
        if (type === '92') {
            if (num >= 20) {
                price = num * 5.9;
                alert(price);

            } else {
                price = num * 6;
                alert(price);
            }
        } else if (type === '97') {
            if (num >= 30) {
                price = num * 6.95;
                alert(price);
            } else {
                price = num * 7;
                alert(price);
            }
        } else {
            alert('请输入正确的汽油编号');
        }
    </script>
```
# 三元运算符
```html
    <script>
        表达式?如果表达式结果为 true 执行这里的代码:如果表达式结果为 false 执行冒号后面的代码;
        var a = 5 > 3 ? 5 : 3; // 5
        console.log(a)
        var num = 30;
        var price = num > 20 ? 5.9 : 6; // 5.9

        if (num > 20) {
            price = 5.9;
        } else {
            price = 6;
        }
    </script>
```
# 代码调试
```html
    <script>
        var type = '97';
        var num = 30;
        var price;
        if (type === '92') {
            if (num >= 20) {
                price = num * 5.9;
                alert(price);

            } else {
                price = num * 6;
                alert(price);
            }
        } else if (type === '97') {
            if (num >= 30) {
                price = num * 6.95;
                alert(price);
            } else {
                price = num * 7;
                alert(price);
            }
        } else {
            alert('请输入正确的汽油编号');
        }
    </script>
```
# switch语句
```html
 <script>
        还是 条件分支语句
        switch(表达式) {
            case 值1：
                    语句体1;
                break; 结束switch语句


            case 值2：
                语句体2;
                break;

            ...
            ...

            default：
                语句体 n+1;
                break;
        }
        var num = 1;
        switch (num) {
            case 0:
                alert('星期日');
                break;
            case 1:
                alert('星期一');
                break;
            case 2:
                alert('星期二');
                break;
            case 3:
                alert('星期三');
                break;
            case 4:
                alert('星期四');
                break;
            case 5:
                alert('星期五');
                break;
            case 6:
                alert('星期六');
                break;
            default:
                alert('错误');
                break;
        }
    </script>
```
# for循环(重要)
```html
    <script>
        循环结构  循环执行某一部分代码
        控制台输出100 个1
        for (var i = 1; i <= 100; i++) {
            console.log(1);
        }
        执行流程
        var i=1 设置循环变量

        i<100  判断循环条件

        i++

        打印 0---100 整数
        for (var i = 0; i <= 100; i++) {
            console.log(i);
        }
        // 0  1  2     99 100

        for (var i = 1; i < 13; i = i + 4) {
            console.log(i);
        }
        // 1  5 9

        for (var i = 1; i < 10; i = i + 3) {
            i = i + 1;
            console.log(i);
        }
        // 2 6 10

        for (var i = 1; i <= 10; i++) {

        }
        console.log(i); // 11

        for (var i = 1; i < 7; i = i + 3) {}
        console.log(i); // 7

        for (var i = 1; i > 0; i++) {
            console.log(i);
        }
        1 2  死循环
    </script>
```
# while循环
```html
    <script>
        var num = 10;
        while (num > 0) {
            console.log(num);
            num--;
            if (num === 7) {
                break;
            }
        }

        // 10 9 8 7 6 5 4 3 2 1
        // 10 9 8

        var count = 10;
        do {
            console.log(count);
            count--;
        } while (count > 0)

        // 10 9 8 7 6 5 4 3 2 1

                这两个语句的功能类似，不同的是：

        while 是先判断后执行，而 do...while 是先执行后判断。
        也就是说，do...while 可以保证循环体至少执行一次，而 while 不能。

        var a = -1;
        do {
            console.log(a);
            a--;
        } while (a > 0)
        // -1

        while (a > 0) {
            console.log(a);
            a--;
        }

        /*
         * 假如投资的年利率为5%，试求从1000块增长到5000块，需要花费多少年
         *
         * 1000 1000*1.05
         * 1050 1050*1.05
         */

        var year = 0;
        var money = 1000;
        while (money < 5000) {
            money = money * 1.05;
            year++;
        }
        console.log(year);
        console.log(money);
    </script>
```
# break和continue
```html
    <script>
        for (var i = 0; i < 5; i++) {
            if (i === 3) {
                // 停止循环 或者 说 退出循环
                break;
                // 本次循环后边的代码也不会在执行了
            }
            console.log("i的值:" + i);
        }

        for (var i = 0; i < 5; i++) {
            console.log("i的值:" + i);
            if (i === 2) {
                continue;
                // 跳出循环
            }
            console.log('abc');
            console.log('edf');
            console.log('hhh');

        }
    </script>
```

