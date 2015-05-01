---
title: "Register Operation"
layout: post
tags: [stm32, register]
---

---

{% highlight c %}
#define ON  0
#define OFF 1

#define LED1(a)	if (a)	\
          GPIO_SetBits(GPIOB,GPIO_Pin_0);\
          else		\
          GPIO_ResetBits(GPIOB,GPIO_Pin_0)

#define LED2(a)	if (a)	\
          GPIO_SetBits(GPIOF,GPIO_Pin_7);\
          else		\
          GPIO_ResetBits(GPIOF,GPIO_Pin_7)

#define LED3(a)	if (a)	\
          GPIO_SetBits(GPIOF,GPIO_Pin_8);\
          else		\
          GPIO_ResetBits(GPIOF,GPIO_Pin_8)


#define	digitalHi(p,i)				{p->BSRR=i;}
#define digitalLo(p,i)				{p->BRR	=i;}
#define digitalToggle(p,i)		{p->ODR ^=i;}


#define LED1_TOGGLE		digitalToggle(GPIOB,GPIO_Pin_0)
#define LED1_OFF			digitalHi(GPIOB,GPIO_Pin_0)
#define LED1_ON				digitalLo(GPIOB,GPIO_Pin_0)
{% endhighlight %}