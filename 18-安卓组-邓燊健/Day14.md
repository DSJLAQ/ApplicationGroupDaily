[toc]
## Day14
#### 一、StringBuffer类
##### A、StringBuffer对象的初始化：
* 1、StringBuffer对象的初始化不像String类的初始化一样，Java提供的有特殊语法，而通常情况下一般使用构造函数进行初始化
* 2、代码例子：
> StringBuffer s=new StringBuffer();
* 3、解析：这样初始化的StringBuffer对象是一个空的对象，如果需要创建一个带有字符串"helloworld"内容的对象，则可以使用：StringBuffer str=new StringBuffer("helloworld");
* 4、StringBuffer和String属于不同的类型，也不能直接进行强制类型转换，但可以通过已下代码转换：
```
package com.demo;

public class StringBufferTest 
{
	public static void main(String[] args)
	{
		String str1="hellojava";
		
		StringBuffer str2=new StringBuffer("helloworld");
		
		
		//String类型转换为StringBuffer类型
		StringBuffer str3=new StringBuffer(str1);
		System.out.println(str3);
		
		//StringBuffer类型转换成String类型
		String str4=str2.toString();
		System.out.println(str4);
	}
	
}
```
运行结果：  
![image](https://note.youdao.com/yws/public/resource/1da981c35d273ef9855cbc9af3dd08c2/xmlnote/69C5B74A377745C9931171ECE74A531A/896)
 
##### B、StringBuffer的常用方法
> StringBuffer类中的方法主要偏重于对字符串的变化，例如追加、插入、和删除等，这是StringBuffer和String类的主要区别
* 1、append方法
> ①、作用：追加内容到当前StringBuffer对象的末尾，类似于字符串的连接，调用该方法后，StringBuffer对象的内容也发生了变化  
②、代码例子：
```
package com.demo;

public class StringBufferTest 
{
	public static void main(String[] args)
	{
		StringBuffer str1=new StringBuffer("hellojava");
		
		
		StringBuffer str2=new StringBuffer("helloworld");
		
		//将两个或者多个字符串连接起来
		str2.append(str1);
		
		System.out.println(str2);
		
	}
	

}
```
运行结果：  
![image](https://note.youdao.com/yws/public/resource/1da981c35d273ef9855cbc9af3dd08c2/xmlnote/AAC90EB4AF824DBBA8C42F8D05A885BE/898)
 
* 2、deleteCharAt方法
> ①、作用：该方法的作用是删除指定位置的字符串，然后将剩余的内容形成新的字符串  
②、代码例子：
```
package com.demo;

public class StringBufferTest 
{
	public static void main(String[] args)
	{
		StringBuffer str1=new StringBuffer("hellojava");
		
		//删除字符串中下标为1的字符e
		str1.deleteCharAt(1);
		System.out.println(str1);
		
		StringBuffer str2=new StringBuffer("helloworld");
		
		//删除字符串中下标为5到9字符
		str2.delete(5, 10);
		System.out.println(str2);
		
	}
	
}
```
运行结果：  
![image](https://note.youdao.com/yws/public/resource/1da981c35d273ef9855cbc9af3dd08c2/xmlnote/F30A2A5488544459863F47A9DE697B72/900)
 
* 3、insert方法
> ①、作用：StringBuffer对象中插入内容，然后形成新的字符串  
②、代码例子：
```
package com.demo;

public class StringBufferTest 
{
	public static void main(String[] args)
	{
		StringBuffer str1=new StringBuffer("hellojava");
		
		//插入的字符串下标为9
		str1.insert(9,"I Love You");
		
		System.out.println(str1);
	}
	
}
```
运行结果：  
![image](https://note.youdao.com/yws/public/resource/1da981c35d273ef9855cbc9af3dd08c2/xmlnote/2B63B1EDCAB24FDC8ACF93A102B9FC22/902)
 
* 4、reverse方法
> ①、作用：将StringBuffer对象中的内容反转，然后形成新的字符串  
②、代码例子：
```
package com.demo;

public class StringBufferTest 
{
	public static void main(String[] args)
	{
		StringBuffer str1=new StringBuffer("123456789");
		
		//使StringBuffer对象的内容反转
		str1.reverse();
		
		System.out.println(str1);
	}
	
}
```
运行结果：  
![image](https://note.youdao.com/yws/public/resource/1da981c35d273ef9855cbc9af3dd08c2/xmlnote/4740A4A5258D4D8FADFD3B3DE7A469BB/904)
 
* 5、setCharAt方法
> ①、作用：修改对象中索引值为index位置的字符为新字符  
②、运行代码：
```
package com.demo;

public class StringBufferTest 
{
	public static void main(String[] args)
	{
		StringBuffer str1=new StringBuffer("123456789");
		
		//修改字符串中下标为4的字符5为X
		str1.setCharAt(4,'X');
		
		System.out.println(str1);
	}
	
}
```
运行结果：  
![image](https://note.youdao.com/yws/public/resource/1da981c35d273ef9855cbc9af3dd08c2/xmlnote/5AE2A30E54E64540B560AADACDFDB583/906)
***

 
