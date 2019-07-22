# 数组
```html
    <script>
        创建数组 字面量
        var arr = [1, 2, 3, 4];
        数组下标  从0 开始
        arr 对应的下标   0 ,1,2,3

        new 

        var arr1 = new Array();
        console.log(arr1)
        数组通过索引(下标) 获取元素
        console.log(arr[2]);
        console.log(arr[0]);

        console.log(arr[4]); // undefined

        添加元素  通过下标
        arr1[0] = 10;
        arr1[1] = 20;
        arr1[2] = 30;
        arr1[4] = 50;
        console.log(arr1);

         修改元素 
        arr[0] = 10;
        console.log(arr);

        length属性  数组元素的个数
        console.log(arr.length); // 4个元素
        console.log(arr1.length); // 5

        var arr2 = [15, 25, 35];
        arr2.length = 6;
        console.log(arr2);
        var arr3 = [1, 2, 3, 4, 5];
        arr3.length = 3;
        console.log(arr3);
    </script>
```
# 遍历数组元素
```html
    <script>
        遍历数组 for循环
        var arr = [3, 7, 4, 6, 9];
        下标从0 开始 ,arr.length-1
        for (var i = 0; i < arr.length; i++) {
            // console.log(arr[i]);
            if (arr[i] < 5) {
                console.log(arr[i]);
            }
        }

        for (var i = arr.length - 1; i >= 0; i--) {
            console.log(arr[i]);
        }

        for in 通常用来 遍历对象
        for (var key in arr) {
            console.log(arr[key]);
        }
    </script>
```
# 数组的基本方法
```html
      <script>
        添加元素 push()  从后添加
        var arr = [2, 4, 6, 8];
        在arr 后边 追加元素 10
        var a = arr.push(10);
        // arr.push(10)
        console.log(a);
        console.log(arr); // 修改了原数组

        function add(x, y) {
            x + y;
        }
        add(3, 5);

        pop()：删除数组中的最后一个元素，返回结果为被删除的元素。
        var arr1 = [1, 3, 5, 7];
        var b = arr1.pop();
        // arr1.pop();
        console.log(b);
        console.log(arr1); // 修改了原数组

        unshift()：在数组最前面插入一个或多个元素，返回结果为该数组新的长度。
        var arr3 = [1, 4, 6, 8];
        arr3.unshift(10);
        console.log(arr3); // 改变原数组

        shift()：删除数组中的第一个元素，返回结果为被删除的元素。

        var arr4 = [2, 3, 4, 5];
        arr4.shift();
        console.log(arr4); // 修改原数组

        concat()：连接两个或多个数组，返回结果为新的数组。（不会改变原数组）

        var newArr = arr3.concat(arr4); // 
        console.log(arr3)
        console.log(newArr);

        join()：将数组转换为字符串，返回结果为转换后的字符串（不会改变原来的数组）。
        var nameArr = ['张三', '李四', '王五'];
        // var nameArrStr = nameArr.join();
        var nameArrStr = nameArr.join('@');

        console.log(nameArrStr);

        split()：通过指定分隔符，如果省略，默认以逗号分隔，将字符串分割为字符串数组。
        var email = "abc@163.com;cc@126.com;frg@qq.com";
        var emialArr = email.split(';');
        // console.log(email)
        console.log(emialArr);
    </script>
```
# 数组求平均值
```html
     <script>
        var arr = [24, 36, 2, 8];
        // 数组求和
        var sum = 0;
        for (var i = 0; i < arr.length; i++) {
            sum = sum + arr[i];
            // 简写
            // sum+=arr[i];
            // sum  24  24+36  24+36+2  24+36+2+8
        }
        var arg = sum / arr.length;
        console.log(arg);
    </script>
```
# 冒泡排序(重要)
```html
    <script>
        var arr = [12, 8, 4, 24, 10];
        从小到大的排序
        排序 : 冒泡排序  选择排序   快速排序   希尔排序

        第一轮
        for (var i = 0; i < arr.length - 1; i++) {
            // arr[i] arr[i+1]
            if (arr[i] > arr[i + 1]) {
                // 交换位置  找第三方
                var temp = arr[i];
                arr[i] = arr[i + 1];
                arr[i + 1] = temp;
            }
        }
        console.log(arr);
        第二轮
        for (var i = 0; i < arr.length - 1; i++) {
            // arr[i] arr[i+1]
            if (arr[i] > arr[i + 1]) {
                // 交换位置  找第三方
                var temp = arr[i];
                arr[i] = arr[i + 1];
                arr[i + 1] = temp;
            }
        }
        console.log(arr);

        第三轮

        for (var i = 0; i < arr.length - 1; i++) {
            // arr[i] arr[i+1]
            if (arr[i] > arr[i + 1]) {
                // 交换位置  找第三方
                var temp = arr[i];
                arr[i] = arr[i + 1];
                arr[i + 1] = temp;
            }
        }
        console.log(arr);

        第四轮
        for (var i = 0; i < arr.length - 1; i++) {
            // arr[i] arr[i+1]
            if (arr[i] > arr[i + 1]) {
                // 交换位置  找第三方
                var temp = arr[i];
                arr[i] = arr[i + 1];
                arr[i + 1] = temp;
            }
        }
        console.log(arr)
    </script>
```
# 冒泡排序优化
```html
    <script>
        var arr = [12, 8, 4, 24, 10];
        从小到大的排序
        排序 : 冒泡排序  选择排序   快速排序   希尔排序

        第一轮
        for (var i = 0; i < arr.length - 1; i++) {
            // arr[i] arr[i+1]
            if (arr[i] > arr[i + 1]) {
                // 交换位置  找第三方
                var temp = arr[i];
                arr[i] = arr[i + 1];
                arr[i + 1] = temp;
            }
        }
        console.log(arr);


        for (var j = 0; j < arr.length - 1; j++) {
            // 外层循环 控制 轮数
            for (var i = 0; i < arr.length - 1 - j; i++) {
                // 内层循环  负责  找出本轮最大值
                // arr[i] arr[i+1]
                if (arr[i] > arr[i + 1]) {
                    // 交换位置  找第三方
                    var temp = arr[i];
                    arr[i] = arr[i + 1];
                    arr[i + 1] = temp;
                }
            }
            console.log(arr);
        }
        console.log(arr);
    </script>
```
# 找因数
```html
    <script>
        var num = 48;
        for (var i = 1; i <= 48; i++) {
            if (num % i === 0) {
                console.log(i);
            }
        }
    </script>
```
# 报7
```html
    <script>
        for (var i = 1; i <= 60; i++) {
            // 安全数条件
            // 对7取余不等于0   并且 个位数不为7
            if (i % 7 !== 0 && i % 10 !== 7) {
                console.log(i)
            }

        }
    </script>
```
# 水仙花数
```html
    <script>
        for (var i = 100; i <= 999; i++) {
            // 获取个位
            var ge = i % 10;
            // 获取十位
            var shi = Math.floor(i % 100 / 10);
            // 获取百位
            var bai = Math.floor(i / 100);
            if (Math.pow(ge, 3) + Math.pow(shi, 3) + Math.pow(bai, 3) === i) {
                console.log(i)
            }
        }
    </script>
```
# 1-100的和
```html
    <script>
        var sum = 0;
        for (var i = 1; i <= 100; i++) {
            sum = sum + i;
        }
        console.log(sum)
    </script>
```
# 阶乘
```html
    <script>
        var jc = 1;
        for (var i = 1; i <= 6; i++) {
            jc = jc * i;
        }
        // jc  1*1*2*3*4*5*6
        console.log(jc)
    </script>
```
# 因数个数
```html
    script>
        var num = 48;
        // 计数器
        var count = 0;
        for (var i = 1; i <= 48; i++) {
            if (num % i === 0) {
                console.log(i);
                // count = count + 1;
                count++;
            }
        }
        console.log(count)
    </script>
```
# 判断质数
```html
     <script>
        var num = 1;
        // 计数器
        var count = 0;
        for (var i = 1; i <= 48; i++) {
            if (num % i === 0) {
                console.log(i);
                // count = count + 1;
                count++;
            }
        }
        if (count === 2) {
            alert(num + '是一个质数');
        } else {
            alert(num + '不是一个质数')
        }

        var a = 17;
        var isZhi = true;
        for (var i = 2; i < a; i++) {
            if (a % i === 0) {
                isZhi = false;
                break;
            }
        }
        if (isZhi) {
            alert(a + '是质数');
        } else {
            alert(a + '不是质数');
        }
    </script>
```
# 函数
```html
    <script>
        function foo() {
            console.log('你好');
            console.log('不凡学院');
            console.log('天气很好');
        }
        不调用就不会执行
        函数名()  调用函数
        foo();


        创建函数的方式一(具名函数)
        function 关键字
        函数的命名规则 同变量命名一样
        function bar() {

        }

        匿名函数 表达式
        var a = function () {

        }
        a();

        a,b是这个函数的形参  给实参占位置
        声明形参就相当于在函数内部声明了对应的变量，但是并不赋值。
        function sum(a, b) {
            console.log(a + b)
        }
        5,6 函数的实际参数
        实际参数和形式参数的个数，要相同。
        实参将会赋值给函数中对应的形参。
        函数的实参可以是任意的数据类型。
        sum(5, 6);
        sum('你好', '不凡学院');

        实参数量多于形参
        sum(3, 5, 7);

        实参数量小于形参
        sum(3); // NaN   另外一个数是undefind,所以运算结果是NaN

        通常实际参数和形式参数的个数，要相同。
    </script>
```
# 函数的返回值
```html
    <script>
        function sum(a, b) {
            return a + b;
            // 需要把计算的结果返回出去
            // return 返回
            console.log(10);
        }
        求任意两个数的和,并返回结果
        return 后的值将会作为函数的执行结果返回
        通常需要用一个变量来接收 函数的返回值

        在函数中 return 后的语句都不会执行（函数在执行完 return 语句之后停止并立即退出）

        如果 return 语句后不跟任何值，就相当于返回一个 undefined

        如果函数中不写 return，则也会返回 undefined

        返回值可以是任意的数据类型，可以是对象，也可以是函数。
        var a = sum(5, 6);
        console.log(a);
    </script>
```
# 函数的作用域
```html
     <script>
        console.log(window);
        变量的作用范围
        全局作用域(全局变量)  和  函数作用域(局部变量)
        全局作用域中的变量都是全局变量，在页面的任意的部分都可以访问的到。
        var a = 24;

        function foo() {
            var b = 12;

            // b的作用范围 只是 foo函数内
            console.log(b);

            console.log(a); // 27
        }
        foo();
        console.log(b); // 报错
        console.log(a);
        在全局作用域中 

        创建的变量都会作为 window 对象的属性保存。

        创建的函数都会作为 window 对象的方法保存。


        函数作用域
        如果一个变量在函数体内部声明，则该变量的作用域为整个函数体，在函数体外不可引用该变量。
    </script>
    <script>
        console.log(a);
    </script>
```
# 作用域的上下级关系
```html
     <script>
        var a = 12; // 全局变量

        function foo() {
            var x = 10; // 局部变量 foo内部

            function bar() {
                var y = 20; // 局部变量 bar
                var a = 200;
                console.log(a); // 200
                console.log(x); // 10
            }

            function sum() {
                var b = 100; // 局部变量 sum
                在某个地方想使用变量时
                console.log(a); // 向上查找 在全局找到了变量a
                console.log(c); // is not defined
            }
            sum();
            bar();
            全局变量 a  和 bar 函数内部的变量a 是独立的  不冲突
        }
        foo();
        作用域查找规则
        就近原则
        当在函数作用域操作一个变量时，它会先在自身作用域中寻找，如果有就直接使用（就近原则）。如果没有则向上一级作用域中寻找，直到找到全局作用域；
        如果全局作用域中依然没有找到，则会报错 ReferenceError。
    </script>
```
# 变量和函数的声明提升
```html
    <script>
        先声明后使用

        var声明变量的时候存在一个  声明提升 的特性
        console.log(a); // undefined  说明 变量a 存在 只是没有赋值
        var a = 24;


        实际顺序
        var a;
        console.log(a);
        a = 24;

        function foo() {
            // 声明提升
            console.log(b);
            var b = 12;
        }
        foo();


        函数也存在声明提升
        只有function 关键字声明函数 才具备这个特性
        add(3, 5);
        bar();

        function add(x, y) {
            console.log(x + y);
        }
        var bar = function () {
            console.log(1);
        }
    </script>
```
# 函数封装
```html
    <script>
        封装冒泡排序
        function bubbleSort(arr) {
            for (var j = 0; j < arr.length - 1; j++) {
                // 外层循环 控制 轮数
                for (var i = 0; i < arr.length - 1 - j; i++) {
                    // 内层循环  负责  找出本轮最大值
                    // arr[i] arr[i+1]
                    if (arr[i] > arr[i + 1]) {
                        // 交换位置  找第三方
                        var temp = arr[i];
                        arr[i] = arr[i + 1];
                        arr[i + 1] = temp;
                    }
                }
                // console.log(arr);
            }
        }
        var arr1 = [3, 2, 1];
        var arr2 = [4, 6, 2, 7, 8];
        bubbleSort(arr1);
        bubbleSort(arr2);
        console.log(arr1);
        console.log(arr2);
    </script>
```


