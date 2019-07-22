# 选择排序
```html
    <body>
    <p>距离2019年7月12日17:00,还有</p>
    <p class="stamp">00:00:00</p>

    <script>
        var pEl = document.getElementsByClassName('stamp')[0];
        var deadTime = new Date('2019-07-12 18:00');
        setInterval(function () {
            var nowTime = new Date();
            时间差
            var stamp = deadTime - nowTime;
            转换成时分秒
            var hour = Math.floor(stamp / 1000 / 60 / 60);
            var min = Math.floor(stamp / 1000 / 60 % 60);
            var s = Math.floor(stamp / 1000 % 60);

            var HOUR_MS = 60 * 60 * 1000;
            var MIN_MS = 60 * 1000;
            var hour = Math.floor(stamp / HOUR_MS);
            var min = Math.floor(stamp % HOUR_MS / MIN_MS);
            var s = Math.floor(stamp % MIN_MS / 1000);
            var str = '' + wrap(hour) + ':' + wrap(min) + ':' + wrap(s) + '';
            pEl.innerText = str;
        }, 1000)
        辅助函数
        function wrap(n) {
            return n > 9 ? n : '0' + n;
        }
    </script>
</body>
```
# 选择排序优化
```html
    <script>
        var arr = [24, 23, 12, 5, 78, 2];
        从小到大
        第一轮
            [2, 23, 12, 5, 78, 24];
        var minIndex = 0;
        for (var i = 1; i < arr.length; i++) {
            if (arr[minIndex] > arr[i]) {
                minIndex = i;
            }
        }
        交换位置
        var temp = arr[0];
        arr[0] = arr[minIndex];
        arr[minIndex] = temp;
        console.log(arr);

        第二轮
        [2, 5, 12, 23, 78, 24];

        var arr1 = [2, 23, 12, 5, 78, 24];
        var minIndex = 1;
        for (var i = 2; i < arr1.length; i++) {
            if (arr1[minIndex] > arr1[i]) {
                minIndex = i;
            }
        }
        交换位置
        var temp = arr1[1];
        arr1[1] = arr1[minIndex];
        arr1[minIndex] = temp;
        console.log(arr1);


        第三轮
        [2, 5, 12, 23, 78, 24];

        第四轮
        [2, 5, 12, 23, 78, 24];

        第五轮
        [2, 5, 12, 23, 24, 78];
        for (var j = 0; j < arr.length - 1; j++) {
            var minIndex = j;
            for (var i = j + 1; i < arr.length; i++) {
                if (arr[minIndex] > arr[i]) {
                    minIndex = i;
                }
            }
            交换位置
            var temp = arr[j];
            arr[j] = arr[minIndex];
            arr[minIndex] = temp;
            console.log(arr);
        }
       优化:
        function selectSort(arr) {
            for (var j = 0; j < arr.length - 1; j++) {
                var minIndex = j;
                for (var i = j + 1; i < arr.length; i++) {
                    if (arr[minIndex] > arr[i]) {
                        minIndex = i;
                    }
                }
                交换位置
                var temp = arr[j];
                arr[j] = arr[minIndex];
                arr[minIndex] = temp;
                console.log(arr);
            }
        }
    </script>
```
# 立即执行函数
```html
<script>
        具名函数
        function foo() {
            alert('你好')
        }
        匿名函数表达式
        var bar = function () {
            alert('nihao')
        }
        以上两个  调用才会执行
        foo();
        bar();
        立即执行函数
        创建完就会执行 
        (function () {
            alert('自执行函数');
        })();
    </script>
```
# 参数的数据类型
```html
<script>
        var num = 6;
        var a = 10;

        function ins(num) {
            a++;
            num++;
            console.log(num); // 7
        }

        ins(num);
        console.log(num); // 6
        console.log(a); // 11

        基本数据类型 作为参数传递的时候 ,会创建该数据的副本,函数的操作修改的是这个副本,并不会影响原来的数据


        引用数类型 作为参数传递时, 也会创建该数据的副本,但是副本只是引用地址(栈内存)的副本,做的操作  会 修改原数据
        var obj = {
            name: '李四',
            age: 12
        }

        function foo(obj) {
            obj.name = '张三';
        }
        foo(obj);
        console.log(obj); // {name:'张三,age:12}

        基本数据类型 存在 栈内存

        引用数类型 数据本身存在堆内存   栈内存存放的是 指向堆内存数据 的 地址
    </script>
```
# 作业圆
```html
<script>
        function area(r) {
            return Math.PI * r * r;
        }
        console.log(area(2));

        function zc(r) {
            return Math.PI * r * 2;
        }
    </script>
```
# 作业求最大
```html
<script>
        function getMax(x, y) {
            // if (x > y) {
            //     return x
            // } else {
            //     return y
            // }
            return x > y ? x : y;
        }

        console.log(getMax(2, 5));

        function getMax3(x, y, z) {
            var temp = getMax(x, y);
            return temp > z ? temp : z;
        }

        // 求数组当中的最大值 或者 最小值
        function getArrMax(arr) {
            var maxIndex = 0;
            for (var i = 1; i < arr.length; i++) {
                if (arr[maxIndex] < arr[i]);
                maxIndex = i;
            }
            return arr[maxIndex];
        }
        var arr1 = [2, 4, 13, 24, 7, 89];
        console.log(getArrMax(arr1));
    </script>
```
# 作业反转数组
```html
<script>
        var arr = [2, 4, 1, 8];
        // [8,1,4,2]
        function reverse(arr) {
            var temp = [];
            for (var i = 0; i < arr.length; i++) {
                temp.unshift(arr[i]);
            }
            return temp;
        }
        console.log(reverse(arr));


        var arr1 = [2, 3, 4, 5, 1]

        function reverse2(arr) {
            for (var i = 0; i < arr.length / 2; i++) {
                // 0 arr.length-1
                // 1 arr.length-2
                // ...遍历一半
                var temp = arr[i];
                arr[i] = arr[arr.length - 1 - i];
                arr[arr.length - 1 - i] = temp;
            }
            return arr;
        }
        // reverse2(arr1);
        // console.log(arr1);
        console.log(reverse2(arr1));
    </script>
```
# 作业求阶乘
```html
<script>
        var num = 10;

        function jc(num) {
            var jc = 1;
            for (var i = 1; i <= num; i++) {
                jc *= i
            }
            return jc;
        }
        console.log(jc(10));

        6! = 6*5*4*3*2*1
        6! = 6*5!
        5! = 5*4!

        递归 算法
        自己调用了自己
        结果 和 前几次的结果有关系
        注意  递归一定要有跳出条件
        function jc(n) {
            if (n === 1) {
                return 1;
            }
            return n * jc(n - 1);
        }
        // jc(6) ==> 6*jc(5)===>  6*5*jc(4) ==> 6*5*4*jc(3) ==> 6*5*4*3*jc(2) ==>6*5*4*3*2*jc(1)
        console.log(jc(10));
    </script>
```
# 作业求阶乘和
```html
<script>
        function jc(n) {
            if (n === 1) {
                return 1;
            }
            return n * jc(n - 1);
        }

        function jch(n) {
            var sum = 0;
            for (var i = 1; i <= n; i++) {
                sum += jc(i);
            }
            return sum;
        }

        console.log(jch(5)); // 120 24 6 2 1  153
        6的阶乘和 = 6!+5!+4!+3!+2!+1!;


        递归解决
        6的阶乘和 == 5的阶乘和 + 6!
        function jch1(n) {
            跳出条件
            if (n === 1) {
                return 1;
            }
            return jc(n) + jch1(n - 1)
        }
        console.log(jch1(5));

        
    </script>
```
# 不死神兔
```html
<script>
        问题：假设一对初生兔子要一个月才到成熟期，(隔一个月才能繁殖)
        而一对成熟兔子每月会生一对兔子，
        那么，由一对初生兔子开始，12 个月后会有多少对兔子呢？

        1: 1
        2: 1
        3: 2
        4: 3   上个月的数量+ 新生的兔子
        5: 5
        6: 8
        7: 13

        斐波那切数列
        function fb(n) {
            跳出条件
            if (n === 2 || n === 1) {
                return 1;
            }
            return fb(n - 1) + fb(n - 2);
        }
        console.log(fb(7))
    </script>
```
# 求一年当中第几天
```html
 <script>
        2018年10月20日   这是当年的  第几天?
        var monthArr = [31, 28, 31, 30, 31, 30, 31, 31, 30, 31, 30, 31];
        var date = new Date('2018-3-20');
        console.log(date);
        var year = date.getFullYear();
        var month = date.getMonth() + 1;
        var day = date.getDate();
        var totalDay = 0;
        for (var i = 0; i < month - 1; i++) {
            totalDay += monthArr[i];
        }
        totalDay = totalDay + day;
        // 判断是不是闰年?
        // 四年一闰百年不润  
        // 四百年再润
        if (year % 4 === 0 && year % 100 !== 0 || year % 400 === 0) {
            if (month >= 3) {
                totalDay++;
            }
        }
        console.log(totalDay);
    </script>
```
# 面试题
```html
<script>
        var a = {
            value: 0,
            toString: function () {
                return ++a.value
            }
        }
        // var a = 2;
        if (a == 1 && a == 2 & a == 3) {
            console.log(1);
        }
        // a 是什么  才能保证  打印1
    </script>
```
