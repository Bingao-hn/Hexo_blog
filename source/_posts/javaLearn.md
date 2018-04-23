---
title: java学习，记录一些零碎的知识点~
date: 2018-04-19 08:16:39
tags: java
categories: Java
---

# 命名规范

> 1.包名所有字母一律小写，如cn.test.test
>
> 2.类名和接口名每个单词 的首字母都要大写，如ArrayList，Iterrator。
>
> 3.常量名所有字母都大写，单词之间用下划线连接，例如DAY_OF_MONTH。
>
> 4.在程序中，尽量使用有意义的英文单词来定义标识符，使得程序便于阅读。如使用userName表示用户名，passWord表示密码等。

# TIPS

> 1.对于浮点数常量，分为float和double两种类型，单精度在数字后面加上f或F，双精度在数字后面加上d或D，<font color=red>默认不加后缀的时候为双精度</font>
>
> 2.java采用的是Unicode字符集，Unicode字符集以\u开头，空白字符在Unicode码表中对应的值为'\u0000'
>
> 3.整形类型变量
>
> | 类型名 | 占用空间 | 取值范围 |
> | - | :-: | :-: |
> | byte | 8位（1个字节） | -2^7 ~ 2^7-1 |
> | short | 16位（2个字节） | -2^15 ~ 2^15-1 |
> | int | 32位（4个字节） | -2^31 ~ 2^31-1 |
> | long | 64位（8个字节） | 2^63 ~ 2^63-1 |
>
> 4.表达式类型自动提升
>
> > byte b1 = 3;
> >
> > byte b2 = 4;
> >
> > byte b3 = b1 + b2;	//此句会报错，原因是在b1+b2进行运行期间，变量b1 b2都被自动提升为int型，结果也自然成了int型，所以会报错，需要强制类型转换
> >
> > //byte b3 =(byte)( b1 + b2 ); //right
>
> 5.与c++的一个区别：
>
> > java中，不可以在{}中重复定义变量，而c++中可以,下面这段代码java会报错，而c++则不会
> >
> > int x =5;
> >
> > {
> >
> > ​	int x =6;
> >
> > ​	System.out.printf("%d\n",x);
> >
> > }
> >
> > System.out.printf("%d\n",x);
>
> 6.+= -= *= /=等运算符会自动强制类型转换
>
> >short s =3;
> >
> > int i =5;
> >
> > //s = i;    //错误: 不兼容的类型: 从int转换到short可能会有损失
> >
> > s += i;     //在使用+= *=等运算符时，会自动强制类型转换
>
> 7.异常处理

```java
try {
            int result = divide(4,0);
            System.out.println(result);
        } catch (Exception e) {
            System.out.println("Exception is :"+e.getMessage());
            return;
        }finally{ //无论程序是否发生异常，这里的语句都要执行
            //有一种情况finally不会执行，那就是try...catch...中执行了System.exit(0),表示退出当前Java虚拟机，虚拟机都退出了，后面的代码自然也不会执行了
            System.out.print("after return ,run to here!");
        }
        System.out.print("run to here!");//发生异常后，这里不会打印
```

> 8.垃圾回收，除了等待Java虚拟机进行自动垃圾回收，也可以通过调用System.gc()方法来通知Java虚拟机立即进行垃圾回收。当一个对象在内存中被释放时，它的finalize()方法会被自动调用，因此可以在类中通过定义finalize()方法来观察对象何时被释放。

```java
class Person{
    //下面定义的finalize方法会在垃圾回收前被调用
    public void finalize(){
        System.out.println("对象将被作为垃圾回收...");
    }
}
public class GarbageCollection{
    public static void main(String[] args){
        Person p1 = new Person();
        Person p2 = new Person();
        //指针置null,让对象成为垃圾
        p1 = null;
        p2 =null;
        System.gc();    //调用方法进行垃圾回收
        for(int i=0;i<1000000;i++){}//延长程序运行时间，以便更好的看到垃圾回收过程，如果不加可能只看到一次或看不到输出  
    }
}
```

> 9.

​      
