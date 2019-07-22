# 对象
```html
<script>
        对象  复杂数据类型
        对象 保存了很多信息,描述事物
        key value  键值对的 无序集合
        var person = {
            // 属性名:属性值,
            name: '张三',
            age: 24,
            sex: true,
            children: {
                name: '小明',
                age: 2
            },
            like: ['篮球', '乒乓球', '足球'],
            say: function () {
                alert('你好');
            },
            sayName: function () {
                alert(this.name);
                // 不调用时 this的指向是不明确的
            }
        }

        对象具有属性 和 方法

        var obj = person; // 这种赋值,只会把栈内存的地址赋值过去
        obj.name = '李四';
        console.log(person);
        person.say();
        person.sayName(); // this 指向调用者(.前边)



        对象的分类:
            内置对象: Math Object Number String Boolean
        宿主对象: DOM BOM console
        开发者自定义的对象
    </script>
```
# 创建对象
```html
<script>
        方式一
        var obj = new Object(); // new 一个 空对象

        console.log(obj);
        方式二
        var obj1 = {};

        想对象追加属性和方法
        追加name 属性
        obj.name = '张三';
        追加 say 方法
        obj.say = function () {
            alert(this.name);
        }
        obj.age = 24;
        console.log(obj);

        获取对象的属性
        console.log(obj.name)
        修改属性值

        删除属性 
        delete obj.age;
        console.log(obj)

        方式三  自定义构造函数 创建对象
        function Person(name, age) {
            this.name = name;
            this.age = age;
            this.say = function () {
                alert(this.name);
            }
        }
        zc 是 new 出来的实例对象
        var zc = new Person('李四', 27);
        console.log(zc);
        zc.say();
        var zc2 = new Person('王五', 12);

        new 到底做了什么?
        1  开辟内存空间创建了一个对象{}
        2  将 构造函数中  this  指向 {}
        3  执行构造函数中的代码
        4  返回 {}

        this的指向?
        以函数的形式调用时，this 永远都是 window。比如fun();相当于window.fun();
        function foo() {
            alert(this);
        }
        foo(); // window.foo() 
        .以方法的形式调用时，this 是调用方法的那个对象
        obj.say(); //  this 指向 obj

        以构造函数的形式调用时，this 是 new 出来的那个实例对象
</script>
```
# 遍历对象
```html
    <script>
        数组遍历for循环
        var arr = [{
                name: '张三',
                age: 27
            },
            {
                name: '李四',
                age: 34
            },
            {
                name: '王五',
                age: 18
            }
        ];
        数组遍历
        arr.forEach(function (item) {
            回调函数 里边的 形参 item 指的就是  数组当中的每一项
            console.log(item);
            item.age = 30;
        })
        console.log(arr);


        对象的遍历
        var obj = {
            name: '张三',
            age: 24,
            sex: true,
            like: ['篮球', '足球']
        }
        for (var key in obj) {
            key 是对象的 每一个 属性名
            为什么 obj.key 是 undefined ?
            obj.key 你获取的是 obj的 key属性,没有这个属性  它的属性值就是undefined
            对象.xx获取属性时.xx 是个变量 ,需要用这种形式获取 obj[xx]
            console.log('属性名' + key + ',属性值' + obj[key] + '');
            // console.log(key + obj[key]);
        }
    </script>
```
# Json
```html
    <script>
        JSON 轻量的数据交换格式  之前 使用 xml
        网络间进行传输 是 文本形式 
        普通对象
        var obj = {
            name: '张三',
            age: 24
        }
        JSON 对象
        var objJson = {
            "name": "李四",
            "age": 36
        }
        console.log(objJson.name);
        console.log(objJson);

        var form = {
            username: '王五',
            password: '1234567',
            sex: '男'
        }

        把对象传给后台,需要转换成Json字符串
        "{username:'王五',password: '1234567',sex:'男'}" 这是一个普通字符串
        var str = "{username:'王五',password: '1234567',sex:'男'}";
        var strJson = JSON.stringify(form); // json字符串
        console.log(strJson); // {"username":"王五","password":"1234567","sex":"男"} 网络间传输的格式
        // console.log(strJson.name)
        后台接收到字符串 要把他变回对象
        "{username:'王五',password: '1234567',sex:'男'}" 这是个普通字符串,无法变回对象
        只有json 字符串 才能转换为   JSON对象
        var objForm = JSON.parse(strJson); // 转换为对象
        console.log(objForm);
        console.log(JSON.parse(str)); // 报错


        解决控制台 打印复杂数据的问题
        var arr = [3, 4, 5, 6, 7];
        console.log(JSON.stringify(arr)); // 想打印的是当前状态
        arr[3] = 200;
        console.log(arr);
    </script>
```

# 遍历后台传过来的对象
```html
     <script src="douban.js"></script>
    <script>
        console.log(movies);
        打印所有电影名字
        获取 电影数组
        var subjects = movies.subjects;
        for (var i = 0; i < subjects.length; i++) {
            var movieInfo = subjects[i];
            打印电影名字
            console.log(movieInfo.title);
            打印导演信息
            var directorArr = movieInfo.directors;
            console.log(directorArr);
            对directorArr遍历 获取 导演名字

        }
        
    </script>
```
# 数组的高级API
```html
<script src="douban.js"></script>
    API 就是方法
    <script>
        pop() shift() push()  unshift()  join() split()  concat()

        reverse()：反转数组，返回结果为反转后的数组（会改变原来的数组
        var arr = ['a', 'b', 'c'];
        console.log(arr.reverse());
        console.log(arr);

        sort()：对数组的元素进行从小到大来排序（会改变原来的数组） 返回值 是 排序后的数组
        var arr1 = ["e", "b", "d", "a", "f", "c"];

        var result = arr1.sort(); // 将数组 arr1 进行排序

        console.log("arr1 =" + arr1);
        console.log("result =" + result);

        var arr2 = [5, 2, 11, 3, 4, 1];
        arr2.sort();
        console.log(arr2); // [1, 11, 2, 3, 4, 5]

        那如果我想让 arr2 里的数字，完全按照从小到大排序，怎么操作呢？继续往下看
        arr2.sort(function (a, b) {
            return a - b; //从小到大
            返回值<0 不交换位置
            返回值>0  交换位置
            返回值==0 不动

            从大到小排
            return b - a;
        })
        console.log(arr2);

        var subjects = movies.subjects;
        console.log(subjects);
         评分排列
        subjects.sort(function (a, b) {
            if (b.rating.average - a.rating.average == 0) {
                return b.rating.stars - a.rating.stars
            } else {
                return b.rating.average - a.rating.average;
            }
        })
        console.log(subjects)

        slice()：从数组中提取指定的一个或者多个元素，返回结果为新的数组（不会改变原来的数组）
        新数组 = 原数组.slice(开始位置的索引, 结束位置的索引); //注意：包含开始索引，不包含结束索引
        var arr3 = [1, 2, 3, 4, 5, 6];
        var newArr3 = arr3.slice(1, 4); // [2,3,4]
        console.log(newArr3);
        var cloneArr3 = arr3.slice(0); // 没有指定结束索引 截取到到最后 // 克隆数组
        console.log(cloneArr3);
        cloneArr3[0] = 10;
        console.log(arr3);

        indexOf() 和 lastIndexOf()：获取数据的索引
        indexOf(value)：从前往后找，获取 value 在数组中的第一个下标。

        lastIndexOf(value) ：从后往前找，获取 value 在数组中的最后一个下标。
        var arr4 = ['张三', '李四', '王五', '张三', '王五'];
        判断一下 张三 有没有在数组中
        console.log(arr4.indexOf('张三')); //0
        console.log(arr4.indexOf('王五')); // 2

        console.log(arr4.indexOf('赵六')); // -1  说明不存在

        console.log(arr4.lastIndexOf('王五')); // 4
        console.log(arr4.lastIndexOf('张三')); // 3


        splice()：从数组中删除指定的一个或多个元素，返回结果为新的数组（会改变原来的数组，会将指定元素从原数组中删除）。
        新数组 = 原数组.splice(起始索引index, 需要替换的个数, 替换的元素);
        var arr5 = ['a', 'b', 'c', 'd'];
        arr5.splice(1, 2, 'e', 'f'); // 
        arr5.splice(1, 2, 'g'); // ["a", "g", "d"]
        arr5.splice(1, 1); // ["a", "d"]
        console.log(arr5);
    </script>
```
# 字符串的方法
```html
<script>
        var str = 'how are you! aNd you?';
        charAt() 获取相应位置的字符
        console.log(str.charAt(5)); // r
        charCodeAt() 指定位置字符 的 Unicode 编码
        console.log(str.charCodeAt(5)); // 114

        indexOf() 返回字符在字符串中的位置
        lastIndexOf()
        console.log(str.indexOf('o')); // 1
        console.log(str.lastIndexOf('o')); // 18

        concat() 连接字符串
        var str2 = '?????';
        console.log(str.concat(str2));

        slice() 提取字符串的某个部分
        console.log(str.slice(2, 9)); //w are y

        substr() 截取字符串 不会改变原字符串
        console.log(str.substr(2, 9)); //w are you

        toUpperCase()
        console.log(str.toUpperCase());
        toLowerCase()
        var lowerStr = str.toLowerCase();
        console.log(lowerStr);
    </script>
```
# 作业1
```html
 <script src="douban.js"></script>
    <script>
        console.log(movies);
        打印所有电影名字
        获取 电影数组
        var subjects = movies.subjects;
        for (var i = 0; i < subjects.length; i++) {
            var movieInfo = subjects[i];
            打印电影名字
            // console.log(movieInfo.title);
            打印导演信息
            var directorArr = movieInfo.directors;
            // console.log(directorArr);
            var str = '';
            for (var j = 0; j < directorArr.length; j++) {
                str += directorArr[j].name + '/';
            }
            str = str.substr(0, str.length - 1);
            // console.log(str);
            // 对directorArr遍历 获取 导演名字
            console.log('电影名字:' + movieInfo.title + ',导演:' + str + '')
        }
        作业
        打印字符串 '电影名字:西虹市首富,导演:闫飞/彭大魔'
    </script>
```
# 作业2
```html
<body>
    找到数组中每个字母出现的次数["c", "a", "z", "a", "a"]

    <script>
        var arr = ["c", "a", "z", "a", "a"];
        用来保存出现的字母
        var wordArr = [];
        用来保存字母出现的次数
        var countArr = [];
        for (var i = 0; i < arr.length; i++) {
            var index = wordArr.indexOf(arr[i]);
            if (index === -1) {
                wordArr.push(arr[i]);
                countArr.push(1);
            } else {
                countArr[index]++;
            }
        }
        console.log(wordArr);
        console.log(countArr);


        // 一对象的形式来保存
        // {
        //     c:1,
        //     a:3,
        //     z:1
        // }
        var word = {};
        for (var i = 0; i < arr.length; i++) {
            if (word[arr[i]]) {
                word[arr[i]]++;
            } else {
                word[arr[i]] = 1;
            }
        }
        console.log(word);
    </script>
</body>
```
# 作业3
```html
<script>
        如何把一个字符串的大小写取反（ 大写变小写小写变大写）， 例如’ AbC ' 变成 '
         aBc ' 。
        var str = 'AbC';
        var strArr = str.split('');
        for (var i = 0; i < strArr.length; i++) {
            // if (strArr[i].toLowerCase() === strArr[i]) {
            //     strArr[i] = strArr[i].toUpperCase();
            // } else {
            //     strArr[i] = strArr[i].toLowerCase();
            // }
            strArr[i] = strArr[i].toLowerCase() === strArr[i] ? strArr[i].toUpperCase() : strArr[i].toLowerCase();
        }
        str = strArr.join('');
        console.log(strArr);
        console.log(str);
    </script>
```
# 作业4
```html
 <script>
        工资的数组[1500,1200,2000,2100,2100,1800],把工资超过2000的删除

        var arr = [1500, 1200, 2000, 2100, 2100, 1800];
        // a = 1;
        // console.log(a);

        // function foo() {
        //     b = 1; // 声明成了全局变量
        // }
        // foo();
        // console.log(b);
        // console.log(window);


        // for (var i = 0; i < arr.length; i++) {
        //     if (arr[i] > 2000) {
        //         arr.splice(i, 1);
        //         i--;
        //     }
        // }
        // console.log(arr)
        var tempArr = [];
        for (var i = 0; i < arr.length; i++) {
            if (arr[i] <= 2000) {
                tempArr.push(arr[i])
            }
        }
        console.log(tempArr)
    </script>
```
# 作业5
```html
<script>
        请把俩个数组[A1, A2, B1, B2, C1, C2, D1, D2] 和[A, B, C, D]，
        合并为[A1, A2, A, B1, B2, B, C1, C2, C, D1, D2, D]。

        var arr1 = ['A1', 'A2', 'B1', 'B2', 'C1', 'C2', 'D1', 'D2'];
        var arr2 = ['A', 'B', 'C', 'D'];
        // for (var i = 0; i < arr2.length; i++) {
        //     arr2[i] = arr2[i] + '3';
        // }
        // // console.log(arr2);
        // var newArr = arr1.concat(arr2);
        // newArr.sort();
        // for (var i = 0; i < newArr.length; i++) {
        //     if (newArr[i].indexOf('3') !== -1) {
        //         newArr[i] = newArr[i].slice(0, newArr[i].length - 1);
        //     }
        // }
        // console.log(newArr);
        var result = [];
        var temp = arr2[0]; // A
        var j = 0;
        for (var i = 0; i < arr1.length; i++) {
            if (arr1[i].indexOf(temp) !== -1) {
                result.push(arr1[i]);
            } else {
                result.push(temp);
                result.push(arr1[i]);
                temp = arr2[++j];
            }
            if (i === arr1.length - 1) {
                result.push(temp);
            }
        }
        console.log(result);
    </script>
```

