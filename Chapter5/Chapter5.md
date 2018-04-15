<notice>教程读者请不要直接阅读本文件，因为诸多功能在此无法正常使用，请移步至[程谱 coderecipe.cn](https://coderecipe.cn/learn/2)学习完整教程。如果您喜欢我们的教程，请在右上角给我们一个“Star”，谢谢您的支持！</notice>
数学计算
======
🌟你已经到到第五章啦，继续加油吧~

数学函数和常量的使用
-----
函数（方法）在数学上的概念是数的一一对应。在计算机科学上，我们可以把函数的调用过程理解成传入一个或者多个参数，执行某些指令，再返回一个值（这个值可以是Object）的过程。

因此，在计算机科学中，函数其实和方法是一样的东西。比如我们经常使用的输出函数"System.out.println()"就是一个函数。它的作用在于输出指定的内容，然后换行。

不止这些内置的函数，我们也可以自己定义一些函数，用于未来的调用执行。函数的定义方法如下：
```Java
public static int func(){
  ...//代码
}
```
public指的是对于其他类也能调用，与private相对应，不只是本类的本个实例。static等概念就涉及到类比较深了，大家学类的时候再看。

一个函数是由函数的名字和参数所决定的。因此，即使两个函数拥有一样的名字，只要他们返回值不同，Java还是会区分它们为两个函数，并都可以调用。如这个例子所示：
```Java
public static int func(){
  ...//代码
}
public static int func(int a,int b){
  ...//代码
}
func();//调用的是没有参数的第一个函数，没有使用返回值
System.out.println(func(1,2));//调用的是有参数的第二个函数，使用了返回值
```
大家可以在下面的lab中填入想要执行的代码，试着调用一下这两个同名函数。

<lab lang="java" parameters="filename=Hello.java">
<notice>练习环境在此无法显示，请移步至[程谱 coderecipe.cn](https://coderecipe.cn/learn/2)查看。</notice>
public class Hello {
  public static void main(String[] args) {
    public static int func(){
      ...//代码
    }
    public static int func(int a,int b){
      ...//代码
    }
    func();//调用的是没有参数的第一个函数，没有使用返回值
    System.out.println(func(1,2));//调用的是有参数的第二个函数，使用了返回值
  }
}
</lab>

为了方便我们在Java中使用数学方法和常量，Java专门开发了java.math类。如果我们需要，可以直接调取。常数主要有e和圆周率PI两个，调用方法如下：
```Java
Math.PI;
Math.E;
```
至于数学方法，java.math类中有非常多，我们摘录一些常用的在这里：
```Java
Math.abs //求绝对值
Math.sin //正弦函数
Math.asin //反正弦函数
Math.cos //余弦函数
Math.acos //反余弦函数
Math.tan //正切函数
Math.atan //反正切函数
Math.toDegrees //弧度转化为角度
Math.toRadians //角度转化为弧度
Math.ceil //得到不小于某数的最大整数
Math.floor //得到不大于某数的最大整数
Math.IEEEremainder //求余
Math.max //求两数中最大
Math.min //求两数中最小
Math.sqrt //求开方
Math.pow //求某数的任意次方
Math.sqrt(x) //平方根
Math.pow(x,y) //x的y次方
Math.exp //求e的任意次方
Math.log10 //以10为底的对数
Math.log //自然对数
Math.rint //求距离某数最近的整数，返回double型（可能比某数大，也可能比它小）
Math.round //同上，返回int型或者long型
```

随机数的产生
-----
通过java.math类，我们也可以生成随机数。生成随机数的方法如下：
```java
math.random();
```
这样可以随机生成一个0到1之间的double类型的数。如果你觉得0到1这个范围不符合你的要求，也可以使用数学方法去调整。比如这样：
```java
math.random() * 10; //大于0小于10的随机数
math.random() + 1; //大于1小于2的随机数
```

小练习
-----
1. 请定义一个函数使其有1个返回值，并调用这个函数。
2. 请生成一个范围为6-21的double型随机值。

<lab lang="java" parameters="filename=Hello.java">
<notice>练习环境在此无法显示，请移步至[程谱 coderecipe.cn](https://coderecipe.cn/learn/2)查看。</notice>
public class Hello {
  public static void main(String[] args) {
    //请在此输入你的代码
  }
}
</lab>
