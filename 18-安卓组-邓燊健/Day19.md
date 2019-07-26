[toc]
## Day19
### 一、Arrays数组工具类
#### A、常见的方法
* 1、Arrays.toString(arr)：把数组arr变成集合
> ①数组变集合的好处：可以使用集合的思想来来操作数组  
②注意：数组转换的集合中不可以使用增删的方法
* 2、Arrays.asList(arr)：把数组转换成ArrayList集合
* 3、Array.sort(arr)：对数组进行排序
* 4、Arrays.binarySearch(arr,s)：在数组arr中对s进行查找
* 5、Arrays.copyOf(str,str.length)：把数组str拷贝到另一个数组中
* 6、Arrays.copyOfRange(str,1,3)：指定数组下标元素，把它们拷贝到另一个数组
* 7、Arrays.equals(str1,str2)：判断两个数组的每一个对应的元素是否相等
* 8、Array.fill(str,s)：把s填充在数组中
#### B、集合转换成数组
* 1、转换代码：
```java
ArrayList<String> al=new ArrayList<String>();
String [] arr=al.toArray(newString[al.size()]);
```
* 2、指定类型的数组到底要定义多长
> ①当指定类型的数组长度小于了集合的size时，那么该方法内部会创建一个新的数组，长度为集合的size  
②当指定类型的数组长度大于集合的size时，就不会创建数组，而是使用传递进来的数组
* 3、集合变成数组的原因
> 为了限定对元素的操作，不需要进行增删了
***
### 二、增强for循环
#### A、格式
* 1、for(数据类型 变量名:被遍历的集合(Collection)或者数组){  }
#### B、增强for循环的作用
* 1、只能获取集合元素，但是不能对集合进行操作
#### C、增强for循环和迭代器的区别
* 1、迭代器处了遍历外，还可以进行remove集合中的元素操作
* 2、如果使用到ListIterator，还可以在遍历过程中进行增删改查的操作
* 运行代码：
```
package package2;

import java.util.ArrayList;

public class forTest
{
	public static void main(String[] args)
	{	
		ArrayList<String> list=new ArrayList<String>();
		
		list.add("ddd");
		list.add("dgeg");
		
		
		for(String s:list)
		{
			System.out.println(s);
		}

	}
}
```
运行结果：  
![image](https://note.youdao.com/yws/public/resource/e36083821fb446484249f2a3cecc2908/xmlnote/05261F60C822488E9D8A057D911AD6E8/1217)
 
***
### 三、集合中的可变参数
#### 、可变参数定义
* 1、可变参数其实就是上一种数组参数的简写形式，不用每一次手动的建立数组对象，只要将要操作的元素作为参数传递即可，隐式将这些参数封装成了数组
* 2、注意：可变参数一定要定义在参数列表最后面
* 代码测试：
```
package package2;

public class Test
{
	public static void main(String[] args)
	{	
		int arr[]={5,2,0,9,7,6,3};
		show("haha",7,25,5,6,7);
		
	}
	public static void show(String str,int...arr)
	{
		System.out.println("数组长度："+arr.length);
		System.out.println("下标为1的元素:"+arr[1]);
		
	}
}
```
运行结果：  
![image](https://note.youdao.com/yws/public/resource/e36083821fb446484249f2a3cecc2908/xmlnote/1EE785CE70B74739A42183712974E2A4/1219)
 
***
### 四、静态导入（staticImport）
```
package package2;

//导入的是Arrays这个类中所有静态成员
import static java.util.Arrays.*;
public class Test
{
	public static void main(String[] args)
	{	
		int arr[]={5,2,0,9,7,6,3};
		sort(arr);//导入Arrays的静态成员后可以省略Arrays.
	}
	public static void show(String str,int...arr)
	{
		System.out.println("数组长度："+arr.length);
		System.out.println("下标为1的元素:"+arr[1]);
		
	}
}
```
***
### 五、System类
#### A、System类中常用方法
* 1、out：标准输出，默认是控制台
* 2、in：标准输入，默认是键盘
* 3、Properties prop=System.getProperties();
> ①Properties是Hashtable的子类，也就是Map集合的一个子类对象，可以通过Map方法来获取出该集合中的元素  
②该集合存储的都是字符串，没有泛型定义  
③在系统中自定义一些特有信息  
④在jvm启动时，动态加载一些属性信息
* 代码例子：
```
package package2;

import java.util.*;
public class Test
{
	public static void main(String[] args)
	{
		
		Properties prop=System.getProperties();
		//获取所有属性信息
		for(Object obj:prop.keySet())
		{
			String value=(String)prop.get(obj);
			System.out.println(obj+"  "+value);
		}
		
		//在系统中自定义一些特有信息
		System.setProperty("mykey","myvalue");
		//获取指定属性信息
		String value=System.getProperty("os.name");
		System.out.println("value"+value);
		
		//jvm启动时，动态加载一些属性信息
		String v=System.getProperty("haha");
		System.out.println("v="+v);
		
	}
}
```
***
### 六、Runtime类
#### A、定义
* 1、Runtime类没有提供构造函数，说明不可以创建新的对象，那么会直接想到该类中的方法都是静态的，发现该类中还有非静态方法，说明该类中肯定会提供了方法获取本类对象，而且该方法是静态的，并且返回值类型是本类类型
* 2、该类使用了单例设计模式
* 代码例子：
```
package package2;

import java.util.*;
public class Test
{
	public static void main(String[] args)throws Exception
	{
		Runtime r=Runtime.getRuntime();
		//打开一个可运行的程序
		r.exec("TypeEasy.exe");	
	}
}
```
***
### 七、Date类
#### A、常用方法
* 1、SimpleDateFormat：对象指定输出格式  
SimpleDateFormat sdf=new SimpleDateFormat("yyyy年MM月dd日E hh:mm:ss")  
2、format：获取时间  
Sdf.format(Date d);
* 代码例子：
```
package package2;

import java.util.Date;
import java.text.*;
public class Test
{
	public static void main(String[] args)
	{
		Date d=new Date();
		//输出当前日期Fri Jul 26 16:36:07 CST 2019
		System.out.println(d);
		//将模式封装到SimpleDateFormat对象中
		SimpleDateFormat sdf=new SimpleDateFormat("yyyy年MM月dd日E hh:mm:ss");
		
		//调用format方法让模式格式化指定Date对象
		
		String time=sdf.format(d);
		
		System.out.println("time="+time);
		
	}
}
```
运行结果：  
![image](https://note.youdao.com/yws/public/resource/e36083821fb446484249f2a3cecc2908/xmlnote/F6CFBC4AE03B4DA5BBE6BDB473A7D898/1221)
 
#### B、Calendar
* 1、Calendar中get的用法
* 2、Calendar中set的用法
* 3、Calendar中add的用法
* 代码例子：
```
package package2;

import java.util.*;

import java.text.*;
public class Test
{
	public static void main(String[] args)
	{
		Calendar c=Calendar.getInstance();
		System.out.println(c);
		
		//1、Calendar中get的用法
		System.out.println(c.get(Calendar.YEAR));
		System.out.println(c.get(Calendar.MONTH));
		
		//2、Calendar中set的用法
		c.set(2008,11,20);
		
		System.out.println(c.get(Calendar.YEAR));
		System.out.println(c.get(Calendar.MONTH));
		//3、Calendar中add的用法
		c.add(Calendar.YEAR, 5);
		System.out.println(c.get(Calendar.YEAR));
		
	}
}
```
运行结果：  
![image](https://note.youdao.com/yws/public/resource/e36083821fb446484249f2a3cecc2908/xmlnote/2A674B10F2BB48B5AA1B13112D821218/1223)
***
### 八、Math类
#### A、常见方法
* 1、Math.abs(x)：返回一个数的绝对值
* 2、Math.copySign(x,y)：返回第一个参数的值和第二个参数的符号
* 3、Math.signnum(x)：判断x的大小（大于0返回1、等于0返回0、小于0返回-1）
* 4、Math.exp(x)：e的x次幂
* 5、Mathi.scalb(x,y)：x*(2的y次幂)
* 6、Math.ceil(x)：返回大于x的最小整数
* 7、Math.floor(x)：返回小于x的最大整数
* 8、Math.hypot(x,y)：返回x和y平方的二次方根
* 9、Math.sqrt(x)：返回x的二次方根
* 10、Math.cbrt(x)：返回x的立方根
* 11、Math.log(x)：以x为底的对数
* 12、Math.max(x,y)：返回x和y中的最大值
* 13、Math.min(x,y)：返回x和y中的最小值
* 14、Math.pow(x,y)：x的y次幂
* 15、Math.random()：返回[0,1)之间的无符号的double类型的值
* 16、Math.rint(x)：返回最接近x的值，如果该数集中，则取偶数
* 17、Math.round(x)：与rint相似，返回值为long类型
***
### 九、IO（Input Output）流
#### A、定义
* 1、IO流用来处理设备之间的数据传输
*2、Java对数据的操作是通过流的方式
* 3、Java用于操作流的对象都在IO包中
* 4、流按操作数据分为两种：字节流和字符流
* 5、流按流向分为：输入流、输出流
#### B、IO流常用基类
* 1、字节流的抽象基类  
InputStream、OutputStream
* 2、字符流的抽象基类  
* Reader、Writer
* 3、注意：这四个类派生出来的子类名称都是以其父类名作为子类名的后缀  
> 如：InputStream的子类FileInputStream  
如：Reader的子类FileReader
