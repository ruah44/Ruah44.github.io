---
layout: post
title: 计算机技术笔记 Lv.0
---

{{ page.title }}
================

<p class="meta">20 Jun 2021</p>

# C语言

## C程序设计语言（K&R）~300 pages



## 		Extremely Basic CS

### CS50

（2021-08-04）

#### week 0

二分法查找：步数（计算时间）~Log N 曲线
2^(查找步数)=N

Integer abbreviated int 

Semi-colon ;

= means assignment 赋值, to copy the value on the right side to the left. 

%s, placeholder for string class

Forward slash /

Back slash \ as an escape character 转义字符
\n

int a =4;
a = a +1;
a += 1;
a ++ 1;
一致

```c
for(int i = 0; i < 50; i ++)
{
	string answer = get_string("What's your name?\n");
	printf("Hi, %s", answer);
}
```

用一只手的五根手指可以表示几个正整数？
1+5+（4+3+2+1）+（4+3+2+1）+5+1
等于32？
如果可以用符号几乎可以
理解为2进制
2*2*2*2*2=32
placeholder 占位符
A 65 mapping映射 ASCII
a byte equals 8 bits
2*2*2*2*2*2*2*2=256
unicode e.g. utf-8
1 pixel, 3 bytes for R, G & B. , 0-255
教育无边界字幕组的网站www.edu-infinity.org
hierarchy 
shrink简化 the problem

Pseudo-code 伪代码(p 不发音)
  Function, 
  condition or branches分支 fork岔路
  Boolean expression 真或假问题
  cycle or loop
  Threads 线程 Multiple things at once 
  Events 事件 listen to things happening 
permute 数学、计算机领域的排列
permutable, permutation

Odds are 很有可能 that you can execute these pseudo code. 
Get in the way 造成阻碍

#### week 1

> Clang，一个C编译器前端: The Clang project provides a language front-end and tooling infrastructure for languages in the C language family (C, C++, Objective C/C++, OpenCL, CUDA, and RenderScript) for the LLVM 一个底层虚拟机后端 project. Both a  GCC-compatible compiler driver ( clang ) and an MSVC-compatible compiler driver (clang-cl.exe ) are provided.

compile and run

Input - (algorithm) - output 
Source code - (compiler) - machine code 

源代码经过编译转到二进制程序。

可以用clang[C语言轻量级编译器]对C语言进行编译，输出一个a.out程序，代表编译器的输出；

或者编译输出名为hello的程序代替a.out；

或者用构建工具（build utility）而非编译器的make

``` c
#include <cs50.h>
clang hello.c
./a.out
    
clang -o hello hello.c
./hello
    
clang hello.c -lcs50 
//-l stands for link
//e.g. -lm stands for linking to math.h
./a.out
```

> Terminal
>
> $ make hello
>
> hello.c: 5: 5 error: ..... 表示执行到hello.c文件的第五行第五个字符(一个tab占4个字符)产生了问题...
>
> string不是C语言自带的类型type，可以通过添加 (declare a file called ...)
>
> #include <stdio.h>
>
> stdio (standard I/O)
>
> what does .h mean?
>
> RAM: Random access memory 隨機儲存器，一種暫時性的儲存器
>
> transistor 晶體管
>
> 浮点数精度问题：有限內存（1 float stored in 4 bytes or 32 bits, a double双精度浮点数 stored in 8 bytes: there's always a trade-off）導致浮點數只能表示近似的分數值，在複雜計算中可能會積累一些浮點錯誤。不可用浮點數做計算比較大小。
>
> indent 缩进

```c
// first %: a symbol for placeholder, second %: a math operator.
printf("x mod y = %i\n", x % y);
printf("x / y = %.6f\n", x / y);
// %.6f: a float with 6 decimal places.

//prompt user for answer
char c = get_char("answer: ");
//check answer, "||" means or
if (c == "Y" || c == "y")
{
    printf("yes\n");
}
else if (c == "N" || c == "n")
{
    printf("no\n");
}

// a function with no return and no input value

void cough(void)
{
    printf("cough\n");
}
//put void cough(void); before main() that uses cough()
void cough(int n);
int main(void)
{
    cough(3);
}
void cough(int n)
{
    for (int i = 0; i < n; i++)
    {
        printf("cough\n");
    }
}
//undeclared functions can't be placed before.
```

> check parity （尤指薪金或地位）平等；（两国货币的）平价；奇偶校验；奇偶性；宇称 of a integer
>
> char "character"

> declarations 声明 
>
> {}中生成（declare）的变量在{}结束后消失.--局部变量，而非全局变量 
>
> 作用域 scope
>
> 变量可以先创造后赋值

``` c
int get_positive_int(string prompt)
{
	int n;
    do
    {
        n = get_int(prompt)；
    }
    while(n < 1);
    return n;
}

i *= 2 // i = i*2
```

> overflow
>
> e.g. ---:998,999,000,001
>
> underflow
>
> 0001,0000,1111

#### week 2 

``` c
// preprocessing 预处理 with #
// pro-processor directives 预处理指令：
#include <stdio.h> 
//when first running clang, clang looks for a file called stdio.h which has declarations such as:
int printf(const char *format, ...);

// compiling 编译 

// assembling 汇编

// linking 连接其他预写的库library, header file

// make magical number 魔数 as a FIXED global variable全局变量
const int COUNT = 3 //全局用大写，常数加const
```

>troubleshoot this problem, yield the errors 产生报错
>
>重视第一项报错，因为报错经常有级联效应 cascading effect
>
>use "printf" to diagnose problems, especially those without any error message
>
>1. correctness - reach the goal without errors
>2. design - run fast and save space
>3. style - be readible, write comments, make parentheses括号 and curly braces 花括号 line up

>grids on RAM (Random access memory随机存取存储器。不同于硬盘hard drives，固态硬盘solif stste drives；RAM需要通电，不能永久储存，内存小但速度快)
>
>1 array, **Contiguous memory allocation** 连续存储, 1 char字符 1 byte
>
>error: implicit declaration of function 函数的隐式声明 '   ' is invalid in C99 ---- 常见于后行的自定义函数没有提前声明的情况
>
>prototype
>
>avoid copying and pasting code: use a loop, iterate遍历 over the number of points in that array
>
>index into an array
>
>

```c
// pass around arrays as arguments
// int scores[]: arrays in C do not have an inherent length associated with them. Length  = COUNT
void chart(int count, int scores[]);
void chart(int count, int scores[])
{
    for (int i = 0; i < count; i++)
    {
        for (int j = 0; j < scores[i]; j++)
        {
            printf("#");
        }
        printf("\n");
    }
}
chart(COUNT, scores);//?

//for (int i = 0, n = strlen(s); i < n; i++)

string s = get_string("Name: ");
int n=0;
while(s[n]!="\0")
{
    n++;
}
//explicit casting 显式类型转换: ASCII0 
int c = (int)s[i]

//implicit casting 隐式类型转换: 
int c = s[i]  
    
//capitalize, 在C语言中，字符用单引号，字符串用双引号。 在c1=''a;中，'a'是字符常量，必须用单引号。 "a"表示字符串，包含两个字符，一个是'a'，一个是'0'。
if (s[i]>='a' && s[i]<='a')
{
    printf("%c",s[i]-('a'-'A'));
}
else
{
    printf("%c",s[i])
}
```

\0 null character 全零字符放在string末尾 占 1byte







# 嵌入式系统编程 (含RTOS) 

## [Modern Embedded Systems Programming Video Course](https://www.state-machine.com/video-course/) 

40 lessons

Embedded Board: the inexpensive and widely available [**EK-TM4C123GXL board**](https://www.ti.com/tool/ek-tm4c123gxl) from Texas Instruments, also known under the name [**TivaC LaunchPad**](https://www.ti.com/tool/ek-tm4c123gxl). The board is based on the **ARM Cortex-M4 CPU** (处理器 Processor). 

IDE Embedded workbench for ARM,32K Kickstart Edition, Version 9.10 - ARM嵌入式工作台: IAR embedded workbench license number: **9597-840-955-4006** 





## C程序设计语言（K&R）



## HTML & CSS

