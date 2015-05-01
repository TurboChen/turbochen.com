---
title: MATLAB Help
layout: post
category: [matlab]
tags: [matlab]
---

`abs()` Absolute value and complex magnitude (取绝对值)

`sqrt()` Square root (开平方)

`round()` Round to nearest integer (四舍五入)

`fix()` Round toward zero (取整 \| 舍去小数)

`rat()` Rational fraction approximation (将实数用分数表示)

{% highlight matlab %}
>> x = 1/8
x = 
  0.1250

>> rat(x)
ans = 
  0 + 1/(8)
rats() Rational output (将实数用分数表示)
>> x = 1/8
x =
  0.1250

>> rats(x)
ans =
1/8
{% endhighlight %}


`sign()` Sign of real or complex value (符号函数)

{% highlight matlab %}
% sign([Negative 负数]) 
ans = 
  -1
% sign([Zero 零])
ans = 
  0
% sign([Integer 正数])
ans = 
  1
{% endhighlight %}

`sin()` Sine function (正弦函数)

`cos()` Cosine function (余弦函数)

`tan()` Tangent function (正切函数)

`asin()` Symbolic inverse Sine function (反正弦函数)

`acos()` Symbolic inverse Cosine function (反余弦函数)

`atan()` Symbolic inverse Tangent function (反正切函数)

`sinh()` `cosh()` `tanh()` `asinh()` `acosh()` `atanh()`

`length()` Length of Object (求长度或个数)

`max()` Maximum Value (取最大值)

`min()` Minimun Value (取最小值)

`mean()` Average or mean value of array (求平均值)

`median()` Median value of array (取中位数)

`sum()` Sum of array elements (求和)

`sort()` Sort array elements (进行排序)

`diff()` Differences and Approximate Derivatives (求相邻元素或元组的差)

`prod()` Product of array elements (求相邻元素或元组的乘积)

`cumsum()` Cumulative sum (元组的值，分别顺序累加的值，的元组) @_@

{% highlight matlab %}
y =
 	2     3     9
%
>> cumsum(y)
ans =
 	2     5    14
{% endhighlight %}

`cumprod()` Cumulative product (元组的值，顺序所累积的值，的元组)

{% highlight matlab %}
y =
  2     3     9
%
>> cumprod(y)
ans =
 	2     6    54
{% endhighlight %}

`dot()` Dot product (求内积/点乘)

{% highlight matlab %}
A =
   5     9     7     2
B =
   7     9     9     0
%
>> dot(A,B)
ans =
  179
{% endhighlight %}

`cross()` Cross product (求外积/叉乘)

Two-dimensional array (二维数组/矩阵/二维元组)

{% highlight matlab %}
>> A = [1 2 3 4; 5 6 7 8; 9 10 11 12] % 二维数组的建立
A =
   1     2     3     4
   5     6     7     8
   9    10    11    12
%
>> A(2,3) = -1 % 修改单个元素
A =
   1     2     3     4
   5     6    -1     8
   9    10    11    12
%
>> C(3,2:4) % 表示多个元素
ans =
  10    11    12
A =
   1     2     3     4
   5     6     7     8
   9    10    11    12
%
>> A(:,2) % 表示第二列
ans =
   2
   6
  10
%
>> A(2,:) % 表示第二行
ans =
   5     6     7     8
%
>> A(1:2,:) % 表示一到二行
ans =
   1     2     3     4
   5     6     7     8
%
>> A
A =
   1     2     3     4
   5     6     7     8
   9    10    11    12
%
>>A(:,3) = [] % 删除第三列
A =
   1     2     4
   5     6     8
   9    10    12
%
>> A = [A; 3 2 1] % 插入末行
A =
   1     2     4
   5     6     8
   9    10    12
   3     2     1
A =
   1     2     4
   5     6     8
   9    10    12
   3     2     1
%
>> C = reshape(A,2,5)
  Error using reshape
  To RESHAPE the number of elements must not change.
 	% 元素总数为12个，新矩阵必须匹配
%
>> C = reshape(A,2,6) % 新矩阵默认重新按列来排序
C =
   1     9     2    10     4    12
   5     3     6     2     8     1
%
>> C(:) % 也可以这样
ans =
   1
   5
   9
   3
   2
   6
  10
   2
   4
   8
  12
   1
% 全都堆在一起了
{% endhighlight %}

(关于换行)
一行执行多次操作

{% highlight matlab %}
>> x = 1+2;y = x + 3;
... 三点来换行连写
>> 1...
+2
ans = 
  3
{% endhighlight %}

`who` List variables in workspace

{% highlight matlab %}
>> who
Your variables are:
A    B    C    ans  x    y
{% endhighlight %}

`whos` List variables in workspace, with sizes and types

{% highlight matlab %}
>> whos
  Name      Size            Bytes  Class     Attributes
  A         4x3                96  double              
  B         4x3                96  double              
  C         2x6                96  double              
  ans       1x1                 8  double              
  x         1x3                24  double              
  y         1x3                24  double
{% endhighlight %}

`clear` Remove items from workspace, freeing up system memory (清除指定Workspace或所有)

{% highlight matlab %}
>> clear A
>> who
Your variables are:
B    C    ans  x    y  
>> clear
>> who
% Nothing
{% endhighlight %}

Permanent constants

{% highlight matlab %}
>> pi
	ans =
  3.1416
i,j 基本虚数单位
{% endhighlight %}

`eps` Floating-point(系统的浮点精确度)

`inf` Infinity(无穷大); e.g. 1/0 , nan , NaN : Not a number(非数值); 0/0

`realmax` Largest positive floating-point number (系统能表示的最大数)

`realmin` Smallest positive normalized floating-point number (系统能表示的最小数)

`format` Set display format for output (设置小数位数)

{% highlight matlab %}
>>format long
>>pi
ans =
  3.141592653589793
>>format short
>>pi
ans = 
  3.1416
{% endhighlight %}

Reference: http://blog.csdn.net/lxdfigo/article/details/8279962
