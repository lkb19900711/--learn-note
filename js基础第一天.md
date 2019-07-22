# js引入输出方式
```html
    <head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <meta http-equiv="X-UA-Compatible" content="ie=edge">
    <script>
         单页面加载完成时候在执行
    </script>
    <title>Document</title>
</head>

<body>
    内嵌式
    外链式

    书写位置
    添加到所有标签之后
    <script src="test.js"></script>
    <script>
        js代码
        js输出方式
        网页当中弹出警告框
        alert('不凡学院');
        alert('天气很好');

        控制台输出信息
        用它来调试代码
        console.log('不凡学院');

        prompt()：用户输入语句
        var a = prompt('请输入您的年龄');
        console.log(a);
    </script>
</body>
```
# js的变量
```html
    <script>
        字面量
        alert('不凡学院');
        console.log(1255522255544111);
        1255522255544111+455222222+45545
        通常不直接使用字面量
        而是通过变量去使用它,变量是储存字面量的容器
        var a = 1255522255544111;
        console.log(a);

        如何去定义变量(声明变量)
        通过 var 关键字 (具有一些特殊功能的短语 或者 单词)
        var b;
        = 该符号是赋值操作,等号右边的值赋给左边的变量
        b = '不凡学院';
        console.log(b);

        推荐写法
        声明变量的同时 给他一个初始值
        var c = '你好';


        注意
        变量必须 先声明 后使用
        console.log(d);

        变量的命名规范
        1. 字母数字下划线 $
        var e;
        var e1;
        var e_d;
        var e$;
        2,不能以数字开头
        var 2e; 错误写法

        3.不能使用关键字 ,保留字
        top name 保留字 

        4.严格区分大小写
        var f = 0;
        var F = 0;
        5. 建议使用驼峰命名
        var firstName;
        var navItem;

        6.见名知意
    </script>
```
#变量的数据类型
```html
    <script>
        数据类型: 原始数据类型(简单/基本数据类型)  引用数据类型(复杂数据类型)

        原始数据类型: string类型(字符串) number类型(数字) boolean类型(true和false) undefined null

        引用数据类型: Object(对象类型)  数组  函数

        string类型 字符串
        字符串需要使用引号引起来，使用双引号或单引号都可以，但是不要混着用。
        引号不能嵌套：双引号里不能再放双引号，单引号里不能再放单引号。但是单引号里可以嵌套双引号。
        var str = '不凡学院';
        var str1 = "不凡学院";
        var str2 = '不凡学院";  错误写法
        var str3 = '不'凡'学院'; 错误
        var str3 = '不"凡"学院';
        转义字符：在字符串中我们可以使用\作为转义字符，当表示一些特殊符号时可以使用\进行转义。
        console.log('不\'凡\'学院');

        number类型  数字(整数和小数(浮点数))

        var num = 1;
        console.log(num);
        var num1 = 12.96;
        console.log('1');
        console.log(Number.MAX_VALUE * 99999999999); // Infinity
        无穷大（正无穷）：Infinity
        无穷小（负无穷）：-Infinity

        NaN：是一个特殊的数字，表示 Not a Number，非数值。比如：
        console.log('abc' * 18); //NaN
        isNaN() :任何不能被转换为数值的值，都会让这个函数返回 true。
        console.log(isNaN(12 * 'abc')); // true
        console.log(isNaN('123abc')); // true
        浮点数的运算
        console.log(0.1 + 0.2); //0.30000000000000004


        boolean类型  布尔值  true 和  false
        常用来做逻辑判断
        var a = true;
        var b = false;

        undefined 类型
        声明了一个变量，但是没有赋值（例如：var a;），此时它的值就是 undefined。
        var c;
        console.log(c); // undefined

        null 空值  专门用来表示一个为空的对象
        var d = null;


        如何判断变量的数据类型
        typeof 变量名 
        console.log(typeof str); // string
        console.log(typeof num); //number
        console.log(typeof a); //boolean
        console.log(typeof c); //undefined
        用 typeof 检测 null 的时候  返回 object
        console.log(typeof d); // object


        对象类型: object
        封装信息 
        key:value 这种键值对  的  无序集合
        属性值  可以是任意的数据类型
        var obj = {
            属性名:属性值,
            属性名:属性值,
            ...
            name: '张三',
            age: 12,
            sex: '男',
            children: {
                name: '小明',
                age: 12
            }
        }


        数组  array
        Array 数组是一组按顺序排列的集合，集合的每个值称为元素。
        每个元素之间逗号隔开
        JavaScript 的数组可以包括任意数据类型。但是通常用来表示某一类数据的集合。
        var arr = [1, 2, 4, 5, '不凡学院', true, undefined, [1, 2], {
            name: '张三'
        }];
        var arr1 = [1, 2, 3, 4];


        函数 function
        通常用来封装功能
        function foo() {

        }

        console.log(typeof obj);
        console.log(typeof arr); // object
        console.log(typeof foo); // function
    </script>
```
# 变量值的传递
```html
    <script>
        var a = 1;
        var b = 2;
        var c = 3;
        a = b + c; // 5
        b = c - a; // -2
        c = a * b; // -10
        console.log(a); // 5
        console.log(b); // -2
        console.log(c); // -10
    </script>
```
# 变量数据类型的转换(很重要)
```html
    <script>
        其它数据类型====> string
        每一行代码 用分号来结尾
        方法一：变量+"" 或者 变量+"abc"
        var a = 123;
        console.log(a);
        a = a + '';
        console.log(a);

        方法二：调用 toString()方法
        变量.toString()
        var b = true;
        console.log(b.toString()); // string类型
        var c = 123;
        console.log(c.toString(2));
        注意：null 和 undefined 这两个值没有 toString()方法，
        所以它们不能用方法二。如果调用，会报错。
        console.log(null.toString());


        隐式转换 采用的是这个规则  记忆
        方法三：使用 String()函数
        String(变量)
        console.log(String(null)); // string类型
        console.log(String(123)); // string类型


        其它数据类型 ==>   number 类型(重点,需要记住)

        隐式转换 使用这个规则   记忆
        方式一：使用 Number()函数
                情况一：字符串 --> 数字

        1.如果字符串中是纯数字，则直接将其转换为数字。

        2.如果字符串中有非数字的内容，则转换为 NaN。（此处可以看到 Number()函数的局限性）

        3.如果字符串是一个空串或者是一个全是空格的字符串，则转换为 0。

        console.log(Number('123')); // number类型
        console.log(Number('ab123')); // NaN
        console.log(Number(' ')); // 0
        console.log(Number('')); // 0

        情况二：布尔 --> 数字
        console.log(Number(true)); // 1
        console.log(Number(false)); //0

        null --> 数字  0
        console.log(Number(null)); // 0
        undefined ==>  数字   NaN
        console.log(Number(undefined)); // NaN

        方式二：parseInt()：字符串 -> 整数【重要】
        console.log(parseInt('5'));
        console.log(parseInt("  2019在公众号上写了6篇文章")); // 2019
        console.log(parseInt("2019.01在公众号上写了6篇文章")); // 2019
        console.log(parseInt("aaa2019.01在公众号上写了6篇文章")); // NaN
        转换规则: 从第一个非空白字符（空格、换行、tab）开始转换，直到遇到一个非数字字符为止。

        取整 不四舍五入
        var d = parseInt(5.8) + parseInt(4.7);
        console.log(d); // 9


        如果对非 String使用 parseInt()或 parseFloat()，它会先将其转换为 String然后再操作。
        隐式转换 
        console.log(parseInt(true)); //打印结果：NaN （因为是先将a转为字符串"true"，然后然后再操作）

        console.log(parseInt(null)); //打印结果：NaN  （因为是先将b转为字符串"null"，然后然后再操作）

        console.log(parseInt(undefined)); //打印结果：NaN  （因为是先将b转为字符串"undefined"，然后然后再操作）

        var e = 168.23;
        console.log(parseInt(e)); //打印结果：168  （因为是先将c转为字符串"168.23"，然后然后再操作）

        parseFloat()：字符串 --> 浮点数（小数）
        console.log(parseFloat('128.3')); // 128.3
        console.log(parseFloat('12.98px')); // 12.98

        其它数据类型 转换成  boolean类型
        Boolean()
        console.log(Boolean(12)); //true
        console.log(Boolean(0)); //false
        console.log(Boolean(NaN)); //false

        console.log(Boolean(null)); //false
        console.log(Boolean(undefined)); //false

        console.log(Boolean('不凡学院')); // true
        console.log(Boolean('')); // false
        console.log(Boolean(' ')); // true

        console.log(Boolean({})); // true

        什么情况下  转换为false
        null undefined 0  NaN 空字符串(重点,常用,必须记住)
    </script>
```
# 算术运算符
```html
    <script>
        + 还有一个拼接字符串的功能
        console.log(5 % 2); // 取余 1


        当对非 Number 类型的值进行运算（包括+、-、*、/）时，会将这些值转换为 Number 然后再运算。
        （注：字符串 + Number、字符串 + 字符串是特例）

        console.log(true + 1); // 2
        console.log(null + 1); // 1
        任何数和 NaN  做运算  都得 NaN
        console.log(undefined + 1); // NaN
        console.log(100 - '11'); // 89
        console.log(100 - '11a'); // NaN

        + 号特殊  ,有一方是字符串的时候 ,拼接作用
        任何的值和字符串做加法运算，都会先转换为字符串，然后再做拼串操作
        console.log(12 + '12'); // '1212'
        console.log(true + '123'); // 'true123'


        任何值做-、*、/运算时都会自动转换为 Number。
        console.log(100 - '12'); // 88
    </script>
```
# 赋值运算符(重要)
```html
    <script>
        var a = 5;
        a = a + 5; // 10
        可以简写成:
        a += 5; // 15
        console.log(a); // 15

        var b = 10;
        b = b - 2;
        简写成: b-=2;

        同理还有  *=  /=

        var c = 10;
        c = c + 1;
        简写: c+=1;
        还可以简写为 c++; 或者 ++c;
        c++;
        ++c;
        console.log(c);

        同理 还有 c--;

        自增1
        ++c  和  c++  的 区别
        相同的地方    都让c  实现了 +1
        var d = 20;
        先赋值  ,再++
        var n = d++;
        console.log(n); // 20
        console.log(d); // 21

        var e = 30;
        先++,在赋值
        var n2 = ++e;
        console.log(e); // 31
        console.log(n2); // 31
    </script>
```
# 比较运算符(重要)
```html
    <script>
         >    <   ==  >=   <=   !=(不等于)
        比较运算符  只有两个结果  true(符合条件)   false(不符合条件)
        console.log(5 > 3); // true
        console.log(3 > 5); // false
        console.log(3 <= 5); // true
        console.log(10 == 10); // true
        console.log(5 != 10); // true


        非数值  比较
        有一方 是  数字
        对于非数值进行比较时，会将其转换为数字然后再比较。
        console.log(1 > false); // 1>0  true
        console.log(2 < null); // 2<0  false
        凡是和 NaN  作比较  结果都是 false
        console.log(2 < undefined); // 2<NaN  false

        console.log(10 > '12'); // 10>12  false
        console.log(10 > '12a'); // 10>NaN  false

        特殊情况：如果符号两侧的值都是字符串时,不会把字符串 变成数字 比较
        而是比较的是字符串的Unicode 编码 
        比较字符编码时，是一位一位进行比较。如果两位一样，则比较下一位，所以借用它可以来对英文进行排序。
        console.log('56' > '123'); //  true
        console.log('abc' > '123'); // 97>1 true


        重点!!!!
        console.log('不凡学院' == '不凡学院'); // true
        console.log(true == 1); // 1==1  true
        ==这个符号并不严谨，会将不同类型的东西，转为相同类型进行比较（大部分情况下，都是转换为数字）。例如：
        console.log(true == '1'); //  1==1  true
        console.log(6 == '6'); // true
        console.log(null == 0); // 打印结果：true
        特殊
        console.log(undefined == null); // true
        console.log(NaN == NaN); //false

        != 不等于  == 的反面

        ==  存在很多隐式转换
        ===  严格相等
        先比较数据类型 数据类型不一致  返回 false
        数据类型一致  那就比较
        console.log(6 === '6'); // false
        console.log(6 == '6'); // true
        !== 严格不等于   ===  的 反面
    </script>
```



