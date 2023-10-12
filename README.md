# 程序设计基础 上机4 函数程序设计
一、实验目的及要求

1、掌握C程序中函数的定义和调用方法。

2、掌握函数间数据传递的方式。

3、掌握函数的嵌套调用方法。

4、了解函数的递归调用方法。

5、掌握局部变量、全局变量和静态变量、动态变量的使用。

二、实验设备（环境）及要求

1、CodeBlocks集成开发环境

2、PTA程序设计类实验辅助教学平台www.pintia.cn

三、实验内容与步骤

1、求n个数的平均数

（1）题目

本题要求实现一个函数，可求n个数的平均值。

### 函数接口定义：

 ```c
 float aver ( float b[], int n );
 ```

其中 `b` 和 `n` 都是用户传入的参数。 `n` 的值不超过`int`的范围； 函数须返回 `b` 数组元素的平均值，保留小数点后2位。

### 裁判测试程序样例：

```c
#include <stdio.h>
float aver(float [ ] , int);

int main()
{
    float ave , a[10000] ;
    int i,n;
    scanf("%d",&n);
    for (i=0 ; i<n ; i++ )
        scanf ("%f", &a[i] ) ;
    ave =aver (a , n ) ;
    printf ("%.2f\n", ave);
    return 0;
}

/* 请在这里填写答案 */
```

（2）源代码

 ```c
 float aver(float b[], int n) {
     float Sum = 0;
     for (int i = 0; i < n; i++)
         Sum += b[i];
     return Sum / n;
 }
 ```

（3）运行结果截屏

2、求两个数的最大公约数

（1）题目

 本题要求实现一个函数，可求两个数的最大公约数，例如，12和8的最大公约数为4，则该函数应该返回4。

### 函数接口定义：

```c
int gcd ( int u, int v );
```

其中 `u` 和 `v` 都是用户传入的参数。 `u`和`v` 的值均不超过`int`的范围，函数须返回 `u` 和 `v` 的最大公约数。

### 裁判测试程序样例：

```c
在这里给出函数被调用进行测试的例子。例如：
#include <stdio.h>

int gcd(int,int);

int main()
{
  int a,b,x; 
  scanf("%d%d",&a,&b);
  x=gcd(a,b);
  printf("%d\n",x);
  return 0;
}

/* 请在这里填写答案 */
```

（2）源代码

 ```c
 int gcd(int u, int v) {
     int i = 9999999;
     while (1)
     {
         i--;
         if (u % i == 0 && v % i == 0)
             return i;
     }
 }
 ```

（3）运行结果截屏

3、数字金字塔

（1）题目

 本题要求实现函数输出n行数字金字塔。

### 函数接口定义：

```c++
void pyramid( int n );
```

其中`n`是用户传入的参数，为[1, 9]的正整数。要求函数按照如样例所示的格式打印出`n`行数字金字塔。注

意每个数字后面跟一个空格。

### 裁判测试程序样例：

```c++
#include <stdio.h>

void pyramid( int n );

int main()
{    
    int n;

    scanf("%d", &n);
    pyramid(n);
    
    return 0;
}

/* 你的代码将被嵌在这里 */
```

（2）源代码

 ```c
 void pyramid(int n) {
     int i, j;
     for ( i = 1; i <=n; i++)
     {
         for (j = 1; j <= n - i; j++)
             printf(" ");
         for ( j = 1; j <=i; j++)
         {
             printf("%d ", i);
         }
         printf("\n");
     }
 
 }
 ```

（3）运行结果截屏

4、解一元二次方程函数

（1）题目

 ```c
 #include<stdio.h>
 void deta1(int a,int b,int c) //求deta大于0时方程的根
 {}
 void deta2(int a,int b,int c) //求deta等于0时方程的根
 {}
 void deta3(int a,int b,int c) //求deta小于0时方程的根
 {}
 int main()
 {
 int a,b,c;
 while(1)
 {printf("请输入一元二次方程的三个参数(a b c):\n");
 scanf("%d%d%d",&a,&b,&c);
 if(a==0) printf("输入不合法，a不能为零!重新输入\n");
 else break;
 }
 if(b*b-4*a*c>0)  ________; //调用deta1函数
 else if(b*b-4*a*c==0)  __________;//调用deta2函数
 else deta3(a,b,c);//调用deta3函数
 return 0;
 }
 ```

（2）源代码

 ```c
 #include <stdio.h>
 #include<stdio.h>
 #include <math.h>
 // #define int float 
 void deta1(int a,int b,int c) //求deta大于0时方程的根
 {
     float x1, x2;
     x1 = (-b + sqrt(b*b-4*a*c) / (2*a));
     x2 = (-b - sqrt(b*b-4*a*c) / (2*a));
     printf("方程有两个实根x1=%.2f,x2=%.2f\n",x1,x2);
 }
 void deta2(int a,int b,int c) //求deta等于0时方程的根
 {
     float x;
     x= -b / (2*a);
     printf("方程有两个相等的实根x1=x2=%.2f\n",x);
 }
 void deta3(int a,int b,int c) //求deta小于0时方程的根
 {
     float p,q;
     p=-b /(2*a);
     q= sqrt(4*a*c-b*b) / (2 *a);
     if (q>=0)
         printf("方程有两个共轭复根x1=%.2f+%.2fi,x2=%.2f-%.2fi\n",p,q,p,q);
     else
         printf("方程有两个共轭复根x1=%.2f-%.2fi,x2=%.2f+%.2fi\n",p,q,p,q);
 }
 
 int main()
 {
     int a,b,c;
     while(1)
     {printf("请输入一元二次方程的三个参数(a b c):\n");
         scanf("%d%d%d",&a,&b,&c);
         if(a==0) printf("输入不合法，a不能为零!重新输入\n");
         else break;
     }
     if(b*b-4*a*c>0) deta1(a,b,c);
     else if(b*b-4*a*c==0) deta2(a,b,c);
     else deta3(a,b,c);//调用deta3函数
     return 0;
 }
 ```

（3）运行结果截屏

四、收获与体会

无

五、额外

部分代码是提取图片或者存在问题，自行检查、调通，应该问题不大？

