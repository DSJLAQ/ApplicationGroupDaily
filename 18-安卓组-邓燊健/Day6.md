## Day6
### 一、在数组中查找元素的算法
#### a、顺序查找法：
不用排序，按照顺序查找下去，效率较低
#### b、折半查找法：
需要把数组按照大小排好序，效率较高
```c
public class Array 
	{
public static void main(String[] args)
{
	int[] rr=new int[]{5,12,100,145};
	int A=getIndex(rr,100);
	if(A>0)
		System.out.println("index="+A);
	else
		System.out.println("该元素不在数组中");
}
public static int GetIndex(int[] arr,int pey)
{
	int x;
	for(x=0;x<arr.length;x++)
	{
		if(arr[x]==pey)
		{
			return x;
		}
	}
	return -1;
}
public static int getIndex(int [] arr,int key)
{
	int min,mid,max;
	min=0;
	max=arr.length;
	while(min<=max)
	{
		mid=(min+max)/2;
		if(key>arr[mid])
			min=mid+1;
		else if(key<arr[mid])
			max=mid-1;
		else 
			return mid;
	}
	return -1;
}
}
```
### 二、进制转换
#### a、十进制转换成二进制：十进制数除2取余，然后逆序输出
#### b、十进制转换成八进制：
```c
public class Change {
	public static void main(String[] args)//十进制转换成二进制
	{
		toBinary(7);
	
	}
	public static void toBinary(int num)
	{
	
		StringBuffer prin=new StringBuffer();//存储数据的容器
		while(num>0)
		{
			prin.append(num%2);
			num=num/2;
		}
		System.out.print(prin.reverse());reverse()//起到反转的功能
	}
public static void toHex(int num)//十进制转换成十六进制
	{
		char demp;
		StringBuffer He=new StringBuffer();
		while(num!=0)
		{
			int temp=num&15;//取最低四位，和15进行与运算
			if(temp>9)
				demp=(char)(temp-10+'A');
			else 
				demp=(char)(temp+'0');
				He.append(demp);
			num=num>>>4;//继续去后四位
		}
		System.out.print(He.reverse());
	}

}
```
### 三、数组中的数组：二维数组 [][]
a、格式1：int [][] arr=new int [3][2];  
意义：  
1、定义了名称为arr的二维数组  
2、二维数组中有3个一维数组  
3、每一个一维数组中有2个元素  
4、一维数组的名称分别为：arr[0]、arr[1]、arr[2]  
5、给第一个一维数组1角标位赋值为78的写法是：arr[0][1]=78;  
b、格式2：int[][] arr=new int[3][];  
意义：  
1、二维数组中有3个一维数组  
2、每个一维数组都是默认初始化值null  
3、可以对这三个一维数组分别进行初始化
```c
arr[0]=new int[3];
arr[1]=new int[1];
arr[2]=new int[2];
```
### 四、Java核心部分：面向对象  
需要掌握的知识点：  
a、面向对象概念  
b、类与对象的关系  
c、封装  
d、构造函数  
e、this关键字  
f、static关键字  
g、单例设计模式

#### a、面向对象的概念：
1、面向对象是相对于面对过程而言  
2、面向对象和面向过程都是一种思想  
3、面向过程：强调的是功能行为  
4、面向对象：将功能封装进对象，强调具备了功能的对象  
5、面向对象是基于面向过程  
6、面向对象三个特征：封装、继承、多态
#### b、类和对象的关系：
类就是对现实中的事物的描述；对象就是这类事物，实实在在存在的个体  
例子：
```c
//需求：描述汽车（颜色、轮胎数）。描述事物其实就是在描述事物的属性和行为
package com.demo2;
class Car
{
	
	//描述对象
	public String color="红色";
	//描述轮胎数
	public int num=4;
	//运行行为
	public void run()
	{
		System.out.println(color+"..."+num);
	}
}
public class dd 
{
	public static void main(String[] args)
	{
		Car c=new Car();
		c.run();
	}

}
```