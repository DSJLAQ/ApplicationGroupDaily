[toc]
<font size ="3">
## Day13
### 一、String类
#### A、字符串常见操作：
##### 1、获取（String str）
* 1.1 字符串中的包含字符数，也就是字符串的长度 
> int  str.length():获取长度

* 1.2 根据位置获取位置上某个字符 
> char str.charAt(int index) ：根据字符串中的角标来获取

* 1.3 根据字符获取该字符在字符串中第一次出现的位置
> int str.indexOf(char s)  ：参数s为查找的字符

* 1.4 从指定的角标开始去获取字符出现的位置
> int str.indexOf(char s,int index)：参数s为查找的字符，index为字符串中的角标

* 1.5根据小字符串获取小字符串第一次在大字符串中的位置
> int str.indexOf(String str1)：参数Str1为查找的字符串

* 1.6 从指定的角标去获取小字符串在大字符串中的位置
> int str.indexOf(String str1,int index)：参数str1为查找的字符串、index为字符串中的角标

* 1.7 从后面开始查找字符串的位置

> int str.lastIndexOf(char s):从字符串后面开始查找字符s第一次出现的位置
* 代码：
```
package com.demo1;

public class Test 
{
	public static void main(String[] args)
	{
		//字符串长度为11
		String str="acdegdgeggd";	
		
		//1.1获取字符串的长度   运行结果：11
		System.out.println(str.length());
		
		//1.2根据位置获取位置上的某个字符		运行结果：e
		System.out.println(str.charAt(3));
		
		//1.3根据字符获取该字符在字符串中第一次出现的位置	 运行结果：4
		System.out.println(str.indexOf('g'));
		
		//1.4从指定的角标去获取字符出现的位置		运行结果：10
		System.out.println(str.indexOf('d',8));
		
		//1.5根据字符串获取字符串在字符串中第一次出现的位置	运行结果：5
		System.out.println(str.indexOf("dg"));
		
		//1.6从指定的角标去获取字符串在字符串中出现的位置		运行结果：7
		System.out.println(str.indexOf("eg",5));
		
		//1.7从后面开始查找字符串的位置  从后面开始第一次出现的字符  运行结果：7
		System.out.println(str.lastIndexOf('e'));
		
	}
}
```
运行结果：  
![image](https://note.youdao.com/yws/public/resource/a852e5a0fa9d9340366672570a588b7e/xmlnote/72C935BC58A54505951BF5FF2F8EDBF4/841)

##### 2、判断（String str）

* 2.1 判断字符串是否以某字符串开头
> str.startsWith(String str1)：str为判断的字符串

* 2.2 判断字符串是否以某字符串结尾
> str.endsWith(String str1)：str1为判断的字符串

* 2.3 判断字符串中是否有内容
> tr.isEmpty()：直接返回false或者true值

* 2.4 判断字符串中是否有某个字符串
> str.contains(String str1)：参数str1为查找的字符串

* 2.5 判断两个字符串内容是否相同
> str.equals(String str1)：区分字符串的大小写

* 2.6 判断两个字符串的内容是否相同
> str.equalsIgnoreCase(String str1)：不区分大小写
* 代码：
```
public class Test
{
	public static void main(String[] args)
	{
		String str="ArrayDemo.java";
		String str1="ArrayDemo.jAVA";
		
		//2.1判断字符串是否是以某字符串开头  运行结果：true
		System.out.println(str.startsWith("Array"));  
		
		//2.2判断字符串是否是以某字符串结尾   运行结果	：true
		System.out.println(str.endsWith(".java"));
		
		//2.3判断字符串中是否有内容	 运行结果：false
		System.out.println(str.isEmpty());
		
		//2.4判断字符串中是否有某字符串	运行结果：true
		System.out.println(str.contains("Demo"));
		
		//2.5判断两个字符串内容是否相同，复写了Object类中equals方法	运行结果：false
		System.out.println(str.equals(str1));
		
		//2.6判断两个字符串的内容是否相同，忽略字符串中的大小写	运行结果：true
		System.out.println(str.equalsIgnoreCase(str1));
	}
}
```
运行结果：  
![image](https://note.youdao.com/yws/public/resource/a852e5a0fa9d9340366672570a588b7e/xmlnote/3DE70DF4D6034624863E36B28CF024EF/843)
 

##### 3、转换
* 3.1 将字符数组的所有都转换成字符串
> String str=new String(char[] arr)：arr为字符数组

* 3.2 将字符数组的一部分转换成字符串
> String str =new String(char[] arr,int index,int count)：arr为字符数组、index为转换首角标、count为转换总的数组个数

* 3.3 将字符串String类对象转化成字符数组
> String str;  
Char [] arr=str.toCharArray();
* 代码：
```
public class Test
{
	public static void main(String[] args)
	{
		   char [] arr={'a','b','c','d','e','f','g','h'};
		   String str="I Love You";
		   
		   //3.1将字符数组的所有都转化成字符串
		   //String(char[] arr)
			String s=new String(arr);
			System.out.println("字符数组转换成字符串："+s);
			
			//3.2将字符数组中的一部分转化成字符串
			//String(char[] arr,int offset,int count)
			String s1=new String(arr,1,3);
			System.out.println("将字符数组一部分转换成字符串："+s1);
			
			//3.3将字符串String类对象转换成字符数组
			char [] arr1=str.toCharArray();
			
	        System.out.println("将字符串String类对象转换成字符数组");
			for(int i=0;i<arr1.length;i++)
			{
				if(i==0)
				System.out.print("arr1={'"+arr1[i]+"',");
			    else if(1<=i&&i<arr1.length-1)
				System.out.print("'"+arr1[i]+"',");
				else
				System.out.print("'"+arr1[i]+"'};");
			}
	}
}
```
运行结果：  
![image](https://note.youdao.com/yws/public/resource/a852e5a0fa9d9340366672570a588b7e/xmlnote/8B8A9E0863C34E378215FEB33D72D61E/845)
 

##### 4、替换（String s="Hello java"）

* 4.1 替换字符串中的某个字符
> String s1=s.replace(char s1,char s2) ：s1为需要被替换的字符、s2为替换的字符

* 4.2 替换字符串中的某部分字符串
> String s2=s.replace(String str1,String str2)：str1为需要被替换的字符串、str2为替换的字符串
* 代码：
```
public class Test
{
	public static void main(String[] args)
	{
		String s="Hello java";
		
		//替换字符串中的某个字符
		String s1=s.replace('a', 'b');
		
		//替换字符串中的某部分字符串
		String s2=s.replace("java","World");
		
		System.out.println("原来的字符串   :"+s);
		
		System.out.println("用b替换字符串中所有a   :"+s1);
		
		System.out.println("用字符串World替换字符串java  :"+s2);
	}
	
}
```
运行结果：  
![image](https://note.youdao.com/yws/public/resource/a852e5a0fa9d9340366672570a588b7e/xmlnote/0067C4EFD17D41428E91C22C834D6D17/847)
 

##### 5、切割
* 5.1 将字符串按照某个特定的字符进行切割，把字符串切割成String类型的数组
> String [] str1=str.split(char c): 参数c为特定的字符

* 代码：
```
public class Test
{
	public static void main(String[] args)
	{
		String s="I am a student";
		System.out.println("根据字符串中的空格切割");
		String[] arr=s.split(" ");
		
		for(int i=0;i<arr.length;i++)
		{
			System.out.println(arr[i]);
		}
	}
}
```
运行结果：  
![image](https://note.youdao.com/yws/public/resource/a852e5a0fa9d9340366672570a588b7e/xmlnote/044299D9DD4C45309B43CC80DD625BDF/849)
 


##### 6、子串
* 6.1：获取字符串中的一部分
> String str;  
String str1=str.substring(int index)：当为一个参数时，index属于同这个角标开始获取字符串的部分字符串

* 6.2：按照角标获取字符串中徐选定长度

> String str;  
String str2=str.substring(int index,int count)：count为获取的个数

* 代码：
```
public class Test
{
	public static void main(String[] args)
	{
		String str="ILoveYou";
		
		String str1=str.substring(0);
		System.out.println(str1);
		
		String str2=str.substring(0,5);
		System.out.println("规定获取字符串中字符的个数为5后："+str2);
		
		
	}
}
```

运行结果：  
![image](https://note.youdao.com/yws/public/resource/a852e5a0fa9d9340366672570a588b7e/xmlnote/374377F01E5C4BD8914C1E7CEEAFE4F7/853)
 
##### 7、转换、去除空格、比较

* 7.1 将字符串全部都转换成小写
> String str;  
String str1=str.toLowerCase();

* 7.2 将字符串全部都转换成大写  
> String str;  
String str2=str.toUpperCase();

* 7.3 去除空格
> String str;  
String str3=str.trim();
* 代码：
```
public class Test
{
	public static void main(String[] args)
	{
		String str="   Hello  World!  !  ";
		
		String str1=str.toLowerCase();
		
		System.out.println("字符串全部转换成小写  :"+str1);
		
		String str2=str.toUpperCase();
		
		System.out.println("字符串全部转换成大写  :"+str2);
		
		String str3=str.trim();
		System.out.println("去掉字符串前后的空格  :"+str3);
		
	}
}
```
运行结果：  
![image](https://note.youdao.com/yws/public/resource/a852e5a0fa9d9340366672570a588b7e/xmlnote/38351BE3A39242FEB6D256503B6436DD/851)
***