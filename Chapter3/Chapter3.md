<notice>教程读者请不要直接阅读本文件，因为诸多功能在此无法正常使用，请移步至[程谱 coderecipe.cn](https://coderecipe.cn/learn/2)学习完整教程。如果您喜欢我们的教程，请在右上角给我们一个“Star”，谢谢您的支持！</notice>
if语句——选择判断
======

🌟你已经到到第三章啦，继续加油吧~

如果…否则如果…否则…
------
if语句，是Java逻辑中最简单和最常用的一种。它的意义是，当某个条件成立时，执行某个操作；当这个条件不成立时，执行另外一个操作。具体的代码如下：
```java
if (条件1) {
···
//如果条件1为真，则执行，执行完跳出if
} else if(条件2) { //条件1为假才判断
//如果条件2为真，则执行，执行完跳出if
} else { // 前面的条件都不对才判断
···
//如果条件为假，则执行
}
```
我们只能在一个`if`语句里面有一个`else`，但却可以有很多个`else if`语句。

`if...else if...else`语句的功能很大，比如我们成绩的分数段可以这么判断：
```java
int grade = 100;//是一个0-100之间的数值
if(grade >= 90){
  System.out.println("90-100");
}else if(grade >= 80){
  System.out.println("80-90");
}else if(grade >= 70){
  System.out.println("70-80");
}else if(grade >= 60){
  System.out.println("60-70");
}else{
  System.out.println("<60");
}
```
上方就是一个最简单的判断语句的使用方式，如果`grade`大于等于`90`，那么输出`90-100`，如果不是再判断是不是大于等于`80`，有则输出`80-90`，以此类推，如果直到最后发现没有大于等于`60`，那么输出`<60`。

且、或和非
-----
且、或和非统称为逻辑运算符，和上一章介绍的关系运算符一样，都是一种运算符。“且”要求两个陈述同时成立，“或”要求两个陈述至少成立一个，而“非”就是将布尔值转换，把真的变成假的，假的变成真的。接下来我们就来看几个例子吧。

非：
当文件找不到时exist变量的值会是false，此时如果想执行代码可以使用
```java
if(!exist){
  ...
}
```
这段代码等效于下面的代码：
```java
if(exist){
  ...
}
else{
  ...
}
```

且：
```java
if(a && b){
...
}
```
这段代码等效于下面的代码：
```java
if(a){
	if(b){
    ...
  }
}
```
或：
```java
if(a || b){
  ...
}
```
这段代码等效于下面的代码（例外是，如果`a`和`b`都是`true`这个代码不会执行两次，只会执行一次）：
```java
if(a){
  ...
}
if(b){
  ...
}
```
大家也可以在下面的lab中尝试一下，修改其中的逻辑运算符，来感受一下其中的差别。
<lab lang="java" parameters="filename=Hello.java">
<notice>练习环境在此无法显示，请移步至[程谱 coderecipe.cn](https://coderecipe.cn/learn/2)查看。</notice>
public class Hello {
  public static void main(String[] args) {
      boolean a = true;
      boolean b = false;
      if (a || b) {
        System.out.println("aaa");
      } else {
        System.out.println("bbb");
      }
  }
}
</lab>

最小化求值原理
-----
使用电脑的人总是希望电脑可以很快完成任务，设计电脑的工程师当然也是这样想的。因此计算机程序再运行的时候会自动排除一些不可能发生的情况，从而让电脑少算一些值来加快电脑运行的速度，这就是最小化求值原理或者短路求值（short-circuit evaluation）。

比如我们的程序需要判断100是不是等于200并且200是不是等于200，计算机在运算的时候，首先判断100是否等于200，当它发现100已经不等于200的时候，无论后面200是不是等于200，这整个判断都不可能是正确的。因此计算机就跳过了后面的判断，直接以这个判断的结果为不正确来处理。

同样，当我们的程序需要判断100是不是等于100或者200是不是等于300，计算机在运算的时候，首先看100是不是等于100，发现是的，那么无论后面200是不是等于300，整个判断都是对的，因此计算机也跳过了后面的判断，直接以这个判断的结果为正确来处理。

比如当我们程序是这样的时候，无论`a`的数值怎么改变，都不会改变程序最后输出“No”的事实：

<lab lang="java" parameters="filename=Hello.java">
<notice>练习环境在此无法显示，请移步至[程谱 coderecipe.cn](https://coderecipe.cn/learn/2)查看。</notice>
public class Hello {
  public static void main(String[] args) {
    int a = 100;
    if(100 == 200 && a == 200){
      System.out.println("Yes");
    }else{
      System.out.println("No");
    }
  }
}
</lab>

因此计算机在处理的时候就不会去读取`a`这个变量的值，在现在看来好像对我们没有什么影响，可是到了之后学习引用的时候就可以派上很大的用场了，比如它可以用来避免`NullPointerException`异常。而且之后我们学习函数的时候就会发现，在`if(100 == 200 && func() == 200)`这样的语句中，`func`函数根本就不会被执行，这里就可能会造成程序运行效果的不同。

德摩根定律
-----
在计算机里，德摩根定律表示的是两种等价关系：
* `!a && !b <=> !(a || b)`
* `!a || !b <=> !(a && b)`
其中，`<=>`意味着等价，`a`和`b`都是布尔值。

例如，当`a`和`b`都是`true`时，我们看定律中的第一条：

`!a && !b = !true && !true = false && false = false`

`!(a || b) = !(true || true) = !true = false`

两者的值是一样的。

当`a`和`b`都是`true`时，我们看定律中的第二条：

`!a || !b = !true || !true = false || false = false`

`!(a && b) = !(true && true) = !true = false`

两者的值是也一样的。

小练习
-----
1. What will be output by the following statement?
```java
int age = 1;
if(age > 10){
	System.out.println(age);
}
```
(A)1

(B)10

(C)no output

(D)unknown

下面的内容要按一下才会显示：
<cr type="hidden"><notice>隐藏内容功能在此无法正常显示，请移步至[程谱 coderecipe.cn](https://coderecipe.cn/learn/2)查看。</notice>C</cr>

2. What will be output by the following statement?
```java
int i = 7;
if(i>0)
  if(i%2 == 0)
    System.out.println(i);
  else
    System.out.println(i+" is not positive");
    ```
(A)7

(B)1

(C)no output

(D)7 is not positive

下面的内容要按一下才会显示：
<cr type="hidden"><notice>隐藏内容功能在此无法正常显示，请移步至[程谱 coderecipe.cn](https://coderecipe.cn/learn/2)查看。</notice>D</cr>
