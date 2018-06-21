# ***知识点***

## **前端**
### 1.javascript中字符串方法
```js
1.转成字符串
    var num=19;     //19
    1).var str=num.toString();  //"19"
    2).var str=num+"";  //"19"
    3).var str=String(num); //"19"

2.字符串分割
    var myStr = "I,Love,You,Do,you,love,me";
    var substrArray = myStr .split(",");    // ["I", "Love", "You", "Do", "you", "love", "me"]
    var arrayLimited = myStr .split(",", 3);    // ["I", "Love", "You"] split()的第二个参数，表示返回的字符串数组的最大长度

3.字符串的长度
    var str=mystr.length;

4.查询子字符串
    第一个函数：indexOf()，它从字符串的开头开始查找，找到返回对应坐标，找不到返回-1。如下：
    var myStr = "I,Love,you,Do,you,love,me";
    var index = myStr.indexOf("you"); // 7
    第二个函数：lastIndexOf()，它从字符串的末尾开始查找，找到返回对应坐标，找不到返回-1。如下：
    var myStr = "I,Love,you,Do,you,love,me";
    var index = myStr.lastIndexOf("you"); // 14
    //以上两个函数同样接收第二个可选的参数，表示开始查找的位置。

5.字符串替换
  replace
    var myStr = "I,love,you,Do,you,love,me";
    var replacedStr = myStr.replace("love","hate"); //"I,hate,you,Do,you,love,me"
  regex
    var myStr = "I,love,you,Do,you,love,me";
    var replacedStr = myStr.replace(/love/g,"hate"); //"I,hate,you,Do,you,hate,me"

6.查找给定位置的字符或其字符编码值
    var myStr = "I,love,you,Do,you,love,me";
    var theChar = myStr.charAt(8);// "o",同样从0开始
    var myStr = "I,love,you,Do,you,love,me";
    var theChar = myStr.charCodeAt(8); //111 ASCII

7.字符串连接
    var str1 = "I,love,you!";
    var str2 = "Do,you,love,me?";
    var str3 = str1 + str2 + "Yes!";
    var str4 =str1.concat(str2);    //"I,love,you!Do,you,love,me?Yes!"

    var arr=new Array("l","love","you");
    arr.join(' '); //l love you

8.字符串切割和提取
    有三种可以从字符串中抽取和切割的方法，如：
    第一种，使用slice():
    var myStr = "I,love,you,Do,you,love,me";
    var subStr = myStr.slice(1,5);//",lov"
    第二种，使用substring():
    var myStr = "I,love,you,Do,you,love,me";
    var subStr = myStr.substring(1,5); //",lov"
    第三种，使用substr():
    var myStr = "I,love,you,Do,you,love,me";
    var subStr = myStr.substr(1,5); //",love"
    //与第一种和第二种不同的是，substr()第二个参数代表截取的字符串最大长度，如上结果所示。

9.字符串大小写转换
    常用的转换为大写或者小写字符串函数，如下：
    var myStr = "I,love,you,Do,you,love,me";
    var lowCaseStr = myStr.toLowerCase();
    //"i,love,you,do,you,love,me";
    var upCaseStr = myStr.toUpperCase();
    //"I,LOVE,YOU,DO,YOU,LOVE,ME"

10.字符串匹配
    字符串匹配可能需要你对正则表达式有一定的了解，先来看看match()函数：
    var myStr = "I,love,you,Do,you,love,me";
    var pattern = /love/;
    var result = myStr.match(pattern);//["love"]
    console.log(result .index);//2
    console.log(result.input );//I,love,you,Do,you,love,me
   //match()函数在字符串上调用，并且接受一个正则的参数。来看看第二个例子，使用exec()函数：
    var myStr = "I,love,you,Do,you,love,me";
    var pattern = /love/;
    var result = pattern .exec(myStr);//["love"]
    console.log(result .index);//2
    console.log(result.input );//I,love,you,Do,you,love,me
    //仅仅是把正则和字符串换了个位置，即exec()函数是在正则上调用，传递字符串的参数。对于上面两个方法，匹配的结果都是返回第一个匹配成功的字符串，如果匹配失败则返回null.
    再来看一个类似的方法search(),如：
    var myStr = "I,love,you,Do,you,love,me";
    var pattern = /love/;
    var result = myStr.search(pattern);//2
    仅返回查到的匹配的下标，如果匹配失败则返回-1.

11.字符串比较
比较两个字符串，比较是规则是按照字母表顺序比较的，如：
    var myStr = "chicken";
    var myStrTwo = "egg";
    var first = myStr.localeCompare(myStrTwo); // -1
    first = myStr.localeCompare("chicken"); // 0
    first = myStr.localeCompare("apple"); // 1

12.自定义方法
    function getSuffix(fileName){
        return file.slice(file.lastIndexOf(".") + 1,fileName.length); 
    }
    function isContain(str,substr){
        return new RegExp(substr).test(str);
    }
     //以下ES6
     
13.for..of 字符串的遍历器接口
    for (let codePoint of 'foo') {
        console.log(codePoint)
    }
// "f"
// "o"
// "o"

14.at() 返回指定索引处的字符
    'abc'.at(0) // "a"
    '𠮷'.at(0) // "𠮷"

15.startWith(),endWith(),include()
    返回布尔值，表示是否找到了参数字符串。这三个方法都支持第二个参数，表示开始搜索的位置。
    var s = 'Hello world!';
    s.startsWith('world',6) // true
    s.endsWith('Hello',5) // true
    s.includes('Hello',6) // false

16.repeat()
    'x'.repeat(3) // "xxx"
    'hello'.repeat(2) // "hellohello"
    'na'.repeat(0) // ""

17.padStart(),padLeft() 字符串补全长度
    padStart和padEnd一共接受两个参数，第一个参数用来指定字符串的最小长度，第二个参数是用来补全的字符串。
    'x'.padStart(5, 'ab') // 'ababx'
    'x'.padStart(4, 'ab') // 'abax'
    'x'.padEnd(5, 'ab') // 'xabab'
    'x'.padEnd(4, 'ab') // 'xaba'
    如果原字符串的长度，等于或大于指定的最小长度，则返回原字符串。
    'xxx'.padStart(2, 'ab') // 'xxx'
    'xxx'.padEnd(2, 'ab') // 'xxx'
    如果用来补全的字符串与原字符串，两者的长度之和超过了指定的最小长度，则会截去超出位数的补全字符串。
    'abc'.padStart(10, '0123456789') //0123456abc
    如果省略第二个参数，默认使用空格补全长度。
    'x'.padStart(4) // '   x'
    'x'.padEnd(4) // 'x   '
```
<!-- ![tpa](/img/tpaIntro.png) -->
### 2.数组的方法
### 3.ajax和json
### 4.前端导出excel
### 5.post如何提交表单
### 6.promise原理？jquery中的ajax返回的是promise?
### 7.如何获取UA?
### 8.postion属性？absolute和relative区别？
### 9.CSS3中transiform和transition区别？
### 10.restful协议规范？怎么获取？js有几种模式创建对象的方式？
### 11.JS三座大山分别指：原型与原型链，作用域及闭包，异步和单线程。
### 12.个人账号登录后的本地存储的知识