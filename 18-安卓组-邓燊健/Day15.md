[toc]
## Day15
### 一、基本数据类型对象包装类
#### A、基本数据类型及其对应的对象类


<table>
    <tr>
       <th>----</th>
       <th>基本数据类型</th>
       <th>对象</th>
   <tr>
       <th>1</th>
       <th>byte</th>
       <th>Byte</th>
    </tr>
    <tr>
       <th>2</th>
       <th>short</th>
       <th>Short</th>
    </tr>
    <tr>
       <th>3</th>
       <th>int</th>
       <th>Integer</th>
    </tr>
     <tr>
       <th>4</th>
       <th>long</th>
       <th>Long</th>
    </tr>
     <tr>
       <th>5</th>
       <th>boolean</th>
       <th>Boolean</th>
    </tr>
    <tr>
       <th>6</th>
       <th>float</th>
       <th>Float</th>
    </tr>
    <tr>
       <th>7</th>
       <th>double</th>
       <th>Double</th>
    </tr>
    <tr>
       <th>8</th>
       <th>char</th>
       <th>Character</th>
    </tr>
</table>


#### B、基本数据类型对象包装类最常见作用
* 1、基本数据类型转成字符串：
> String  str=基本数据类型.toString(基本数据类型值)  
* 代码例子：
```Java
package Demo.com;

public class type 
{
	public static void main(String[] args)
	{
		//将整数123转成字符串"123"
		String str=Integer.toString(123);
		System.out.println(str);
	}
}
```
* 2、字符串转成基本数据类型   
> 基本数据类型(xxx)  a=基本数据类型对象(Xxx) .parseXx(字符串)
* 代码例子：
```Java
package Demo.com;

public class type 
{
	public static void main(String[] args)
	{
		//字符串"148"转化成整型数字
		int a=Integer.parseInt("148");
	
		System.out.println(a);
		
		
		//字符串"12.36"转化成double类型数据
		double b=Double.parseDouble("12.36");
		
		System.out.println(b);
		
		//字符串"true"转化成boolean类型
		
		boolean c=Boolean.parseBoolean("true");
		
		System.out.println(c);
	}
}
```
运行结果：  
![image](https://note.youdao.com/yws/public/resource/a852e5a0fa9d9340366672570a588b7e/xmlnote/7B0D0EAC54EF46F585B69C608CDCF20A/976)
 
#### C、进制转换
* 1、十进制转换成二进制、八进制、十六进制
> ①、十进制转换成二进制：  toBinaryString();  
②、十进制转换成八进制：  toOctalString();  
③、十进制转换成十六进制：toHexString();
* 代码例子：
```Java
package Demo.com;

public class type 
{
	public static void main(String[] args)
	{
		//十进制数6转化成二进制数
		String a=Integer.toBinaryString(6);
		System.out.println(a);
		
		//十进制数20转化成八进制数
		String b=Integer.toOctalString(20);
		System.out.println(b);
		
		//十进制数60转化成十六进制数
		String c=Integer.toHexString(60);
		System.out.println(c);
	}
}
```
* 2、其他进制转换成十进制
> ParseInt(String,radix)  
String为对应的进制字符串、radix为相应的进制数
```Java
package Demo.com;

public class type 
{
	public static void main(String[] args)
	{
		//二进制数110转化成十进制数
		int a=Integer.parseInt("110",2);
		System.out.println(a);
		
		//八进制数24转化成十进制数
		int b=Integer.parseInt("24",8);
		System.out.println(b);
		
		//十六进制数转化成十进制数
		int c=Integer.parseInt("3c",16);
		System.out.println(c);
	}
}
```
***
### 二、集合类
#### A、出现集合类的原因
> 面向对象语言对事物的体现都是以对象的形式，所以为了方便对多个对象的操作，就对对象进行存储，集合就是存储对象最常用的一种方式
#### B、数组和集合类同是容器，有什么区别
* 1、数组的特点：
> ①、只能存储同一种数据类型的数据  
②、一旦初始化，长度固定  
③、数组中的元素与元素之间的内存地址是连续的  
注意：Object类型的数组可以存储任意类型的数据
* 2、集合是存储对象数据的集合容器
> ①、集合可以存储任意类型的对象数据  
②、集合的长度是会发生变化的
#### C、为什么会出现这么多容器
* 1、Collection：单例集合的根接口
> ①、List：如果是实现了List接口的集合类  
特点：有序、可重复  
a、ArrayList：底层维护了一个Object数组实现的  
特点：查询速度快，增加和删除慢  
b、LinkedList：底层是使用了链表数据结构实现的  
特点：查询速度慢，增加删除块  
c、Vector：底层也是维护了一个Object的数组实现的，实现与ArrayList是一样的，但是Vector是线程安全的，操作效率低  
②、Set：如果是实现了Set接口的集合类  
特点：无序，不可重复  
a、HashSet 底层是使用了哈希表来支持的  
特点：存取速度块  
b、TreeSet 如果元素具备自然顺序的特性，那么就按照元素自然顺序的特性进行排序存储
* 2、Collection中包含的  
> Collection（List<ArrayList、LinkedList、Vector>、Set<HashSet、TreeSet>）  
因为每一个容器对数据的存储方式都有不同，这个存储方式称之为数据结构（数据在内存中的构造形式）

#### D、Collection方法摘要
* 1、增加的方法
> ①c.add(E e)：	在集合c中添加一个元素  
②c.add(Collection c1)：在集合c中添加另一个集合c1中的所有元素
* 代码例子：
```Java
package Demo.com;
import java.util.ArrayList;
import java.util.Collection;

public class type 
{
	public static void main(String[] args)
	{
		Collection c=new ArrayList();
		//向集合c中增加对象
		c.add("张三");
		c.add("李四");
		c.add("王五");
		System.out.println("集合c中的对象有："+c);
		System.out.println("增加对象成功了吗？ "+c.add("赵六"));
		System.out.println("集合一个对象后集合c中的对象有："+c);
		
		
		Collection c1=new ArrayList();
		//向集合c1中增加对象
		c1.add("小明");
		c1.add("小东");
		c1.add("小帅");
		System.out.println("集合中c1中的对象有："+c1);
		System.out.println("增加一个集合成功了吗？ "+c1.add(c));
		System.out.println("增加一个集合后集合c中含有的对象有："+c1);
	}
}
```
运行结果：  
![image](https://note.youdao.com/yws/public/resource/a852e5a0fa9d9340366672570a588b7e/xmlnote/4A0E56DE15194013A9F2EA3900523141/978)
 
* 2、删除的方法
> ①c.clear()：清空集合c中的所有元素  
②c.remove()：删除集合c中的指定元素  
③c.removeAll(Collection c1)：删除集合c和集合c1中交集的元素  
④c.retainAll(Collection c2)：保留集合c和集合c2中的交集元素，其他的元素一并删除
* 代码例子：
```Java
package Demo.com;
import java.util.ArrayList;
import java.util.Collection;

public class type 
{
	public static void main(String[] args)
	{
		Collection c=new ArrayList();
		//1、向集合c中增加元素
		c.add("张三");
		c.add("李四");
		c.add("王五");
		c.add("赵六");
		System.out.println("集合c中的元素有："+c);
		
		//2、删除集合c中指定的元素
		c.remove("张三");
		System.out.println("1、(c.remove(\"张三\"))删除后的集合："+c);
		
		//3、清空集合c中的所有元素
		c.clear();
		System.out.println("2、(c.clear)清空集合c后 c="+c);
		
		//4、重新向集合c中增加元素
		c.add("张三");
		c.add("李四");
		c.add("王五");
		c.add("赵六");
		System.out.println("重新增加元素后集合c中的元素有："+c);
		
		
		Collection c1=new ArrayList();
		//5、向集合c1中增加元素
		c1.add("小明");
		c1.add("小东");
		c1.add("小帅");
		c1.add("赵六");
		System.out.println("集合中c1中的对象有："+c1);
		
		//6、删除集合c和集合c1中有交集的元素，删除赵六
		c.removeAll(c1);
		System.out.println("3、删除c和c1中有交集的元素赵六后：c="+c);
		System.out.println("c1="+c1);
		
	}
}
```
运行结果：  
![image](https://note.youdao.com/yws/public/resource/a852e5a0fa9d9340366672570a588b7e/xmlnote/81CC3295C66F4530937A9BA5118629BB/980)
 
* 3、查看的方法
> c.size()：查看集合的长度
* 代码例子：
```Java
package Demo.com;
import java.util.ArrayList;
import java.util.Collection;

public class type 
{
	public static void main(String[] args)
	{
		Collection c=new ArrayList();
		//1、向集合c中增加元素
		c.add("张三");
		c.add("李四");
		c.add("王五");
		c.add("赵六");
		System.out.println("集合c中的元素有："+c);
		//查看集合c的长度（也就是集合c中元素的个数）
		System.out.println("集合c的长度为："+c.size());
	}
}
```
运行结果：  
![image](https://note.youdao.com/yws/public/resource/a852e5a0fa9d9340366672570a588b7e/xmlnote/C46BD3682D6045BE9609B6763EEEF596/982)
 
* 4、判断
> ①c.isEmpty()：判断集合c是否为空  
如果为空的话，返回true，不为空的话，返回false  
②c.contains(Object c1)：判断集合c是否包含元素c1  
如果包含的话，返回true，不包含的话，返回false  
③c.containsAll(Collection c2)：判断集合c是否包含集合c2中的所有元素  
如果包含的话，返回true，不包含的话，返回false
* 代码例子：
```Java
package Demo.com;
import java.util.ArrayList;
import java.util.Collection;

public class type 
{
	public static void main(String[] args)
	{
		//创建集合c
		Collection c=new ArrayList();
		//1、向集合c中增加元素
		c.add("张三");
		c.add("李四");
		c.add("王五");
		c.add("赵六");
		System.out.println("集合c中的元素有："+c);
		//2/判断集合c中是否存在元素
		boolean a=c.isEmpty();
		System.out.println("1、集合c为空吗？"+a);
		
		//判断集合c中是否包含某个元素
		boolean b=c.contains("王五");
		System.out.println("2、集合c中包含王五这个元素吗？"+b);
		
		//创建集合c1
		Collection c1=new ArrayList();
		c1.add("李四");
		c1.add("王五");
		c1.add("赵六");
		System.out.println("集合c1中的元素有："+c1);
		
		//判断集合c中是否包含集合c1中的元素
		boolean d=c.containsAll(c1);
		System.out.println("3、集合c中包含集合c1中的所有元素吗？"+d);
		
	}
}
```
运行结果：  
![image](https://note.youdao.com/yws/public/resource/a852e5a0fa9d9340366672570a588b7e/xmlnote/82E57155D8B34797B56BA5B18EA5BA43/984)
 
* 5、迭代
> ①toArray()
* 代码例子：
```Java
package Demo.com;
import java.util.ArrayList;
import java.util.Arrays;
import java.util.Collection;


class Person
{
	int id;
	String name;
	public Person(int id,String name)
	{
		this.id=id;
		this.name=name;
	}
	
	public String toString()
	{
		return "{编号："+this.id+"姓名："+this.name+"}";
	}
	
}
public class type 
{
	public static void main(String[] args)
	{
		Collection c=new ArrayList();
		c.add(new Person(110,"大帅"));
		c.add(new Person(111,"小帅"));
		c.add(new Person(112,"帅哥"));
		
		//把集合中的所有元素都存储到一个Object的数组中
		Object [] arr=c.toArray();
		
		for(int i=0;i<arr.length;i++)
		{
			Person p=(Person) arr[i];
			System.out.println(p);
		}
		
		
	}
}
```
运行结果：  
![image](https://note.youdao.com/yws/public/resource/a852e5a0fa9d9340366672570a588b7e/xmlnote/C838370543E8419F873FEF7B3AE5B7D2/986)
 
> ②itertator()  
a、迭代器的作用：用于抓取集合中的元素  
b、迭代器的方法：  
hasNext()：判断集合中是否有元素可以遍历，如果有元素可以遍历，则返回true，否则返回false  
next()：获取元素  
remove()：移除迭代器最后一次返回的元素
* 代码例子：
```Java
package Demo.com;
import java.util.ArrayList;
import java.util.Collection;
import java.util.Iterator;

public class type 
{
	public static void main(String[] args)
	{
		Collection c=new ArrayList();
		c.add("大帅");
		c.add("小帅");
		c.add("帅哥");
		c.add("张三");
		c.add("李四");
		
		//iterator()方法返回的是一个接口类型
		Iterator it=c.iterator();
		
		//利用迭代法打印集合c中所有的元素
		while(it.hasNext())
		{
			System.out.println(it.next());
		}
		
	}
}
```
运行结果：  
![image](https://note.youdao.com/yws/public/resource/a852e5a0fa9d9340366672570a588b7e/xmlnote/336F7CC5A398454C9822BCCA5949E397/988)
***
 

