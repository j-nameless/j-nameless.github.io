---
title: 关于Java只有值传递
date: 2019-07-28 22:03:14
tags: java
categories: java
---

## 为什么Java只有值传递

关于值传递和引用传递的概念：**按值调用(call by value)表示方法接收的是调用者提供的值，而按引用调用（call by reference)表示方法接收的是调用者提供的变量地址。一个方法可以修改传递引用所对应的变量值，而不能修改传递值调用所对应的变量值**

**Java总是按值传递：方法得到的是所有参数值的一个拷贝，也就是说，方法不能修改传递给它的任何参数变量的内容**
<!--more-->

如下列栗子：

```java
public class Test {

	public static void main(String[] args) {
		// TODO Auto-generated method stub
		Student s1 = new Student("小张");
		Student s2 = new Student("小李");
		Test.swap(s1, s2);
		System.out.println("s1:" + s1.getName());
		System.out.println("s2:" + s2.getName());
	}

	public static void swap(Student x, Student y) {
		Student temp = x;
		x = y;
		y = temp;
		System.out.println("x:" + x.getName());
		System.out.println("y:" + y.getName());
	}
}
```

输出是：

```
x:小李
y:小张
s1:小张
s2:小李
说明在swap方法里x和y的交换没有影响到原s1和s2对象
```

