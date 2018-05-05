<notice>教程读者请不要直接阅读本文件，因为诸多功能在此无法正常使用，请移步至[程谱 coderecipe.cn](https://coderecipe.cn/learn/2)学习完整教程。如果您喜欢我们的教程，请在右上角给我们一个“Star”，谢谢您的支持！</notice>
循环
======

🌟你已经到到第四章啦，继续加油吧~

在很多时候，只执行代码一次是没有办法达到目的的。而要多次执行代码，一次次的复制粘贴无疑是最傻的一件事情。于是，我们还需要循环结构来帮我们快速地重复执行代码。

for循环
-----
for循环的用法如下：
```java
for(初始条件;终止条件;更新语句){
  ...//循环内容
}
```
for的运行方式是：

a)先运行初始条件，然后测试终止条件，如果终止条件不符合（false）则跳出循环继续执行;

b)如果终止条件符合（true）则继续运行，执行循环内容，然后运行更新语句;

c)重复执行b)直到循环结束。

说了for循环的代码格式和运行原理，我们就来用一个实例试一下吧！

e.g.
```java
for( int i = 1; i < 5;I ++){
	System.out.print(i + “ ”);
}
```
上面的代码会输出"1 2 3 4 "。

while循环
-----
while循环的运行原理和for循环大抵相同，但在写法上有一定差异。while循环的写法如下：
```java
while(测试条件){
  ...//循环内容
}
```
while循环会先判断条件，如果符合（true）就会继续执行循环内容，不符合就会跳出循环执行下面的内容，执行完循环内容后会返回来判断条件，如果符合的话接着执行循环内容，一直重复知道条件不符合（false）为止。所以说，我们如果想要像上例一样输出"1 2 3 4 "，可以这么写代码：
```Java
int i = 1;
while(i < 5){
  System.out.print(i + " ");
  i = i + 1;
}
```

for-each循环
-----
这种代码用于循环访问一个数组或者集合中的所有元素。用法如下：
```java
for(SomeType element : collection){
  ...//循环内容
}
```
注意： for-each 循环不能被用来替换或删除元素，同时不显示index。

关于这一块的内容，此处现行略写，请大家学习到后面“数组与数组列表”时再进行学习。

continue下一循环和break停止循环
-----
在循环中，我们有两种操作可以停止当前的循环。这就需要用到关键字continue和break。这两者的区别是，break的作用是跳出当前循环块（for、while、do while）或程序块（switch）并执行循环块或程序块外的代码，而continue用于结束循环体中其后语句的执行，并跳回循环程序块的开头执行下一次循环，而不是立刻循环体。

我们可以配合实例来看一下：
```Java
    for (int i = 1; i <= 5; i++) {
          if (i == 3) continue;
          System.out.print(i + " ");
    }
    System.out.println("");
    for (int n = 1; n <= 5; n++) {
          if (n == 3) break;
          System.out.println(n + " ");
    }
```
输出结果会是“1 2 4 5  \n  1 2”。怎么样，是不是和你想的一样呢？

同样的，我们也会把这节课学到的内容放进lab。大家可以运行来试试，修改其中的内容，探究循环的奥秘。

<lab lang="java" parameters="filename=Hello.java">
<notice>练习环境在此无法显示，请移步至[程谱 coderecipe.cn](https://coderecipe.cn/learn/2)查看。</notice>
public class Hello {
  public static void main(String[] args) {
    for( int i = 1; i < 5;I ++){
      System.out.print(i + “ ”);
    }
    int a = 1;
    while(a < 5){
      System.out.print(a + " ");
      a = a + 1;
    }
    for (int b = 1; b <= 5; b++) {
          if (b == 3) continue;
          System.out.print(b + " ");
    }
    System.out.println("");
    for (int n = 1; n <= 5; n++) {
          if (n == 3) break;
          System.out.println(n + " ");
    }
  }
}
</lab>

小练习
-----
1. Refer to the following code segment.
```java
/** Compute the mean of integers 1 .. N.
* N is an integer >= 1 and has been initialized. */
int k = 1;
double mean, sum = 1.0;
while (k < N){
  /* loop body */
}
mean = sum / N;
```
What is the precondition for the while loop?

(A) k ≥ N, sum=1.0

(B) sum=1+2+3+... +k

(C) k<N, sum=1.0

(D) N ≥ 1, k=1, sum=1.0

(E) mean=sum/N

下面的内容要按一下才会显示：
<cr type="hidden"><notice>隐藏内容功能在此无法正常显示，请移步至[程谱 coderecipe.cn](https://coderecipe.cn/learn/2)查看。</notice>D</cr>

2. Refer to the following method.
```java
/**Precondition: aandbareinitializedintegers. */
public static int mystery(int a, int b){
  int total = 0, count = 1; while (count <= b){
    total += a;
    count++;
  }
  return total;
}
```
What is the postcondition for method mystery?

(A) total = a+b

(B) total = a^b

(C) total = b^a

(D) total = a*b

(E) total = a/b

下面的内容要按一下才会显示：
<cr type="hidden"><notice>隐藏内容功能在此无法正常显示，请移步至[程谱 coderecipe.cn](https://coderecipe.cn/learn/2)查看。</notice>D</cr>

3.【2015年AP CS第17题】

Consider the following method.

```java
//* Precondition: num > 0 */
public static int doWhat(int num)
{
  int var = 0;

  for (int loop = 1; loop <= num; loop = loop + 2)
  {
    var += loop;
  }

  return var;
}
```

Which of the following best describes the value returned from a call to doWhat ?

(A) num

(B) The sum of all integers between 1 and num, inclusive

(C) The sum of all even integers between 1 and num, inclusive

(D) The sum of all odd integers between 1 and num, inclusive

(E) No value is returned because of an infinite loop.

4.【2015年AP CS第25题】

Consider the following code segment.

```java
int count = 0;

for (int x = 0; x < 4; x++)
{
  for (int y = x; y < 4; y++)
  {
    count++;
  }
}

System.out.printIn(count);
```

What is printed as a result of executing the code segment?

(A) 4

(B) 8

(C) 10

(D) 16

(E) 20

5. Consider the following code segment.

```java
  int value = 15;
  while(value > 28) {
    System.out.println(value);
    value++;
  }
```

What are the first and last numbers output by the code segment?

(A) First: 15, Last: 28

(B) First: 15, Last: 29

(C) First: 15, Last: 15

(D) First: 16, Last: 19

(E) No value will be printed.

<cr type="hidden"><notice>隐藏内容功能在此无法正常显示，请移步至[程谱 coderecipe.cn](https://coderecipe.cn/learn/2)查看。</notice>E</cr>


3.【2015年AP CS第17题】

Consider the following method.

```java
//* Precondition: num > 0 */
public static int doWhat(int num)
{
  int var = 0;

  for (int loop = 1; loop <= num; loop = loop + 2)
  {
    var += loop;
  }

  return var;
}
```

Which of the following best describes the value returned from a call to doWhat ?

(A) num

(B) The sum of all integers between 1 and num, inclusive

(C) The sum of all even integers between 1 and num, inclusive

(D) The sum of all odd integers between 1 and num, inclusive

(E) No value is returned because of an infinite loop.

4.【2015年AP CS第25题】

Consider the following code segment.

```java
int count = 0;

for (int x = 0; x < 4; x++)
{
  for (int y = x; y < 4; y++)
  {
    count++;
  }
}

System.out.printIn(count);
```

What is printed as a result of executing the code segment?

(A) 4

(B) 8

(C) 10

(D) 16

(E) 20

5. Consider the following code segment.

```java
 int value = 15;
		while(value > 28) {
			System.out.println(value);
			value++;
		}
```

What are the first and last numbers output by the code segment?

            First                     Last

(A)          15                        28

(B)          15                        29

(C)          15                        15

(D)          16                        19

(E)          No value will be printed.