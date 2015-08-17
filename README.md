#《编写可测试的Javascript代码》中文版 勘误（非官方）
图书豆瓣链接：[link](http://book.douban.com/subject/26348084/)

在此感谢[译者](http://www.cnblogs.com/TomXu/)在翻译此书的过程中的辛勤付出。

个人认为书中有些地方翻译不太妥当，并且中文版并没有按照英文版的勘误修订错误。

并且，在译者博客中也没有找到勘误信息。

故创建此Repo，将个人认为的错误（*可能影响到读者理解的*）之处及修改方案列出。

此为非官方资料，所以若有不妥之处还望指出。

>书籍版本：

>2015年2月第1次印刷

>参考资料：

>1. [英文版勘误](http://www.oreilly.com/catalog/errata.csp?isbn=0636920024699)
2. 英文版PDF
3. wikipedia

##规则
1. 对于每一个勘误项都应使用如下的格式
 - 页码 段落

    译文：

    原文：（可选，英文版内容）

    参考：（可选，其他参考资料内容）

    修改方案：

    备注：（可选，补充内容）
 - 页码 代码块

    代码：

    修改方案：
2. 对于需要修改的语句以及原作中相应的英文，应`标记`出来： `这是翻译不当的语句，需要修改`

##前言：
###P1 第三段
译文：
>这段代码可能很`惊人`，但它唯一能存活的方法就是永远不会产生Bug...

原文：
>The code may be `spectacular`, but the only way it will survive is if it never causes bugs

修改方案：
>这段代码可能十分惊艳（巧妙）

##第1章：
###P4 倒数第二行

 译文：
>TDD希望在编写代码之前先编写测试。这些测试提供了必须遵循预期功能的代码。编写测试失败后（刚开始还没编写代码肯定会失败），接着开始编写代码，以便确保测试能够通过。

 原文：
>These tests provide the expectations to which your code must conform.After you write tests that fail (as there initially is no code to make the tests work), you then start writing code that makes your tests pass.

 修改方案：
>TDD希望在编写代码之前先编写测试，由测试来明确代码所要实现的预期功能。在编写了还未能通过的测试之后（毕竟还没有能让测试工作的代码），再着手编写能够通过测试的代码。

##第2章：
###P14 第二段

 译文：
>理想情况下，函数没有副作用，并且返回值（如果有的话）完全依赖于函数的参数。`虽然代码几乎只存活于方法内，但编写的时候要时刻记住：“我们该如何去测试这个代码？”。`

 原文：
>In an ideal world,functions have no side effects and their return value(s) (if any) are completely dependent on their parameters. `Code rarely gets to live in that world, but it is something to keep in mind while writing code, along with “how am I going to test this thing?”`

 修改方案：
>但在实际中，编写这类函数的机会少之又少，因此，在你编写函数时，你应该时刻想着“我该如何去测试这个函数呢？”。

###P17 第四段

 译文：
>最后一点可以改进，是`将config对象里的每个键都链接到validator函数，以便整个散列对象都在一个中心位置上`

 原文：
>The last bit of niceness would be `to link each key in the config object to its validator function and keep the entire hash in one central location`:

 修改方案：
>最后一个可以改进的地方，是建立config对象的每个属性关联各自validator函数的散列（hash），并将这些散列都放到一个对象中，以便统一管理。

###P17 代码块2

 代码：
```javascript
function configure(values) {
     for (var key in fields) {
         if (typeof values[key] !== 'undefined') {
             fields[key].validator(values[key]);
             config[key] = values[key];
         } else {
             config[key] = fields[key].default;
         }
      }
 	return config; // config没有定义
}
```

 参考：英文版勘误

 修改方案：
```javascript
function configure(values) {
     var config = {}; //定义config
     for (var key in fields) {
         if (typeof values[key] !== 'undefined') {
             fields[key].validator(values[key]);
             config[key] = values[key];
         } else {
         	config[key] = fields[key].default;
         }
      }
 	return config;
}
```

###P24 最后一段

 译文：
 >圈复杂度是表示代码中`独立现行路径`的数量

 原文：
 >Cyclomatic complexity is a measure of the number of `independent paths` through your code.

 参考：[wiki](http://en.wikipedia.org/wiki/Cyclomatic_complexity)
 >The cyclomatic complexity of a section of source code is the number of `linearly independent paths `through this code.

 修改方案：
 >圈复杂度是表示代码中线性独立的路径的数量 （译注：）

 备注：
 >网上所有圈复杂度的中文解释都说独立现行，但是并不存在“独立现行”这种词。关于线性独立的路径的数量，我认为就是指一个函数执行路径的总数。详细的计算公式请大家参看wiki。


