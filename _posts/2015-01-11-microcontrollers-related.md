---
title: "Microcontrollers related"
layout: page
tags: [microcontrollers, related]
---

使用`Ctrl+F`来查找关键字	

## 中断服务程序 (ISR, Interrupt Service Routines)

> 该寄存器用于存放正在被服务的所有中断级,包括尚未服务完而中途被别的中断打断了的中断级。
>
> 所谓中断是指当CPU正在处理某件事情的时候，外部发生的某一事件（如一个电平的变化，一个脉冲沿的发生或定时器计数溢出等）请求CPU迅速去处理，于是CPU暂时中止当前的工作，转去处理所发生的事件。中断服务处理完该事件以后，再回到原来被中止的地方继续原来的工作。(via: baike.baidu.com)

## 快速中断请求（Fast Interrupt Request，FIQ)
>在ARM中，FIQ模式是特权模式中的一种，同时也属于异常模式一类。用于高速数据传输或通道处理，在触发快速中断请求（FIQ）时进入。
>
>FIQ和IRQ(外部中断模式)之间有很大的区别。FIQ模式必须尽快处理，处理结束后离开这个模式；IRQ模式可以被FIQ模式中断，但IRQ不能中断FIQ模式；为使FIQ模式响应更快，FIQ模式具有更多的影子（Shadow）寄存器。FIQ模式必须禁用中断；如果一个中断例程必须重新启用中断，应使用IRQ模式而不是FIQ模式。(via: baike.baidu.com)

在Cortex-M3里面取消了FIQ，利用"嵌套"中断来实现

## 不可屏蔽中断 (NMI, Non Maskable Interrupt)

> NMI (Non Maskable Interrupt)——不可屏蔽中断(即CPU不能屏蔽)无论状态寄存器中 IF 位的状态如何,CPU收到有效的NMI必须进行响应;NMI是上升沿有效;中断类型号固定为2;它在被响应时无中断响应周期.不可屏蔽中断通常用于故障处理(如:协处理器运算出错,存储器校验出错,I/O通道校验出错等).
>
> IF = Interrupt Flag(中断状态) (via: baike.baidu.com)

## 存储器保护单元 (MPU, Memory Protection Unit)

> MPU 有很多玩法。最常见的就是由操作系统使用 MPU，以使特权级代码的数据，包括操作系统
本身的数据不被其它用户程序弄坏。MPU 在保护内存时是按区管理的(“区”的原文是 region，以
后不再中译此名词——译注)。它可以把某些内存 region 设置成只读，从而避免了那里的内容意外
被更改；还可以在多任务系统中把不同任务之间的数据区隔离。一句话，它会使嵌入式系统变得更
加健壮，更加可靠（很多行业标准，尤其是航空的，就规定了必须使用 MPU 来行使保护职能——译
注）。(via: 《Cortex-M3 权威指南》)

