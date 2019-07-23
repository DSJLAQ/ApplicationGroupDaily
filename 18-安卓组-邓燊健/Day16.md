[toc]
## Day16
### 一、List
#### A、特点：元素是有序的、可以重复（因为List的元素有索引）
#### B、特有方法
* 1、增加
> ①c.add(index,element)：指定角标中增加元素（类似于插入）  
②c.addAll(index,Collection)：
* 2、删除
> ①c.remove(index)：删除指定角标的元素
* 3、修改
> ①c.set(index,element)：修改指定角标的元素
* 4、查找
> ①c.get(index)：获得指定角标的元素  
②c.subList(startindex,endindex)：获取两个角标之间的元素
* 代码例子：
```
package demo1;
import java.util.ArrayList;
import java.util.Iterator;

public class ListTest 
{
	public static void main(String[] args)
	{
		ArrayList a=new ArrayList();
		
		//增加元素
		a.add("张三");
		a.add("李四");
		a.add("小明");
		a.add("小黄");
		
		//查看原有集合的所有元素
		System.out.println("集合a="+a);
		
		//向集合a中按照指定角标的方式增加元素
		a.add(2,"小帅");
		System.out.println("1、把小帅添加到集合中角标为2的位置：a="+a);
		
		//从集合a中删除角标为4的元素
		a.remove(4);
		System.out.println("2、把角标为4的小黄元素删掉：a="+a);
		
		//把集合a中角标为1的元素进行修改
		a.set(1, "大帅");
		System.out.println("3、把角标为1的李四修改成大帅：a="+a);
		
		//查看集合中角标为2的元素
		System.out.println("4、查看集合中角标为2的元素："+a.get(2));
		
		//获取集合a中所有的元素
		System.out.println("5、通过循环的方法获取集合中所有元素");
		for(int i=0;i<a.size();i++)
		{
			System.out.println("a<"+i+">="+a.get(i));
		}
		
		//通过iterator()方法获取集合中的所有元素
		Iterator it=a.iterator();
		
		System.out.println("6、通过iterator()来获取所有元素");
		while(it.hasNext())
		{
			System.out.println(it.next());
		}
		
		//通过subString()来获取集合中的部分元素
		System.out.println("7、通过subString()来获取集合中的角标1~3的元素："+a.subList(1, 3));
		
		ArrayList a1=new ArrayList();
		a1.add("qq");
		a1.add("hh");
		a.add(2,a1);
		
		//把集合a1中的所有元素添加到集合a中的角标2中
		System.out.println("8、把集合a1中的所有元素添加到集合a中的角标2中");
		System.out.println("集合a="+a);
	}
}
```
运行结果：  
![image](https://note.youdao.com/yws/public/resource/e36083821fb446484249f2a3cecc2908/xmlnote/2AC02AD3D9064A62A82E93F1C4035C0F/1053)

 
#### C、List中特有的ListIterator()
> 1、特点：可以在迭代的过程中进行增删改查
* 代码例子：
```
①增加
while(La.hasNext())
		{
			//增加元素
			if(La.next()=="李四")
				La.add("小帅");
		}
```
```
②修改
while(La.hasNext())
		{
			//增加元素
			if(La.next()=="李四")
				La.set("小帅");
		}
```
```
③删除
while(La.hasNext())
		{
			//增加元素
			if(La.next()=="李四")
				La.remove();
		}
```
***
### 二、List的子类对象
#### A、List的子类对象
* 1、ArrayList：底层的数据结构使用的是数组结构
> ①特点：查询速度快、增删稍慢、线程不同步
* 2、LinkedLIst：底层使用的数据结构是链表数据结构
> ①特点：查询速度慢、增删速度很快  
②特有方法：  
a、addFirst():把元素增加在集合的第一位置  
b、addLast():把元素增加在集合的最后位置  
c、getFirst():获取集合中的第一个元素  
d、getLast():获取集合中的最后一个元素  
e、removeFirst():获取并删除第一个元素  
f、removeLast():获取并删除最后一个元素
* 代码例子：
```
package demo1;

import java.util.LinkedList;
public class LInkedListTest1
{
	public static void main(String[] args)
	{
		LinkedList link=new LinkedList();
		
		//1、LinkedList中特有增加方法
		link.addFirst("java01");
		link.addFirst("java02");
		link.addFirst("java03");
		link.addFirst("java04");
		System.out.println("1、特有增加方法：link="+link);
		//2、LinkedList中特有增加方法
		link.addLast("java05");
		System.out.println("2、特有增加方法：link="+link);
		
		//3、LinkedList中特有查看方法
		System.out.println("3、获取集合中第一个元素："+link.getFirst());
		
		//4、LinkedList中特有查看方法
		System.out.println("4、获取集合中最后一个元素："+link.getLast());
		
		//5、删除集合中的第一个元素
		link.removeFirst();
		System.out.println("5、删除集合中第一个元素：link="+link);
		
		//6、删除集合中最后一个元素
		link.removeLast();
		System.out.println("6、删除集合中最后一个元素：link"+link);
		
	}
}
```
运行结果：  
![image](https://note.youdao.com/yws/public/resource/e36083821fb446484249f2a3cecc2908/xmlnote/0505A0B7CCAA4E1FA55ABDC1D2746517/1055)  
③LinkedList模拟一个栈堆或者一个队列  
a、栈堆：先进后出   如同一个杯子  
b、队列：先进先出   如同一条水管
* 代码例子：
```
package demo1;

import java.util.LinkedList;

//模拟数据结构中的队列：先进先出（像一条水管）
class DuiLie
{
	private LinkedList link;
	
	DuiLie()
	{
		link=new LinkedList();
	}
	
	public void myAdd(Object obj)
	{
		link.addFirst(obj);
	}
	
	public Object myGet()
	{
		//从集合后面开始返回元素，并且删除元素
		//这是属于队列link.removeLast()
		return link.removeLast();


		//这是属于栈堆link.removeFirst()
		return link.removeFirst();
	}
	public boolean isNull()
	{
		//判断集合是否为空
		return link.isEmpty();
	}
}
public class LinkedListTest2 
{
	public static void main(String[] args)
	{
		DuiLie dl=new DuiLie();
		dl.myAdd("java01");
		dl.myAdd("java02");
		dl.myAdd("java03");
		dl.myAdd("java04");
		
		while(!dl.isNull())
		{
			System.out.println(dl.myGet());
		}
	}
}
```
运行结果：  
栈堆：  
![image](https://note.youdao.com/yws/public/resource/e36083821fb446484249f2a3cecc2908/xmlnote/F9A3F0E8F42448149C57BB838F2F3271/1057)
 
队列：  
![image](https://note.youdao.com/yws/public/resource/e36083821fb446484249f2a3cecc2908/xmlnote/FAAA0CD2931F4027A44F93F30A2064AB/1059)
 
* 3、Vector：底层的数据结构是数组结构
> 特点：查询和增删的速度都比较慢，线程同步（被ArrayList取代了）  
①枚举就是Vector特有的取出方式，枚举和迭代器是一样的
* 代码例子：
```
package demo1;

import java.util.Vector;
import java.util.Enumeration;

public class VectorTest1 
{
	public static void main(String[] args)
	{
		Vector v=new Vector();
		v.add("小帅");
		v.add("大帅");
		v.add("小明");
		
	Enumeration en=v.elements();
	
	while(en.hasMoreElements())
	{
		System.out.println(en.nextElement());
	}
	}
}
```
***
### 三、Set的子类对象
#### A、HashSet：底层数据结构是哈希表,线程时非同步的
* 1、HashSet元素唯一性的原理
> 通过元素的两个方法，hashcode和equals来完成  
①如果元素的hashcode值相同，才会判断equals是否为true  
②如果元素的hashcode值不同，不会调用equals  
注意：对于判断元素是否存在，以及删除元素等操作，依赖方法是元素的hashCode()和equals
* 代码例子：
```
package demo1;

import java.util.HashSet;
import java.util.Iterator;
class Person
{
	private String name;
	private int age;
	public Person(String name,int age)
	{
		this.name=name;
		this.age=age;
	}
	public String toString()
	{
		return this.name+"..."+this.age;
	}
	
	
	//获取对象的哈希值
	public int hashCode()
	{
		System.out.println(this.name+"...hashcode");
		return name.hashCode()+age;
	}
	
	//如果对象之间的哈希值相同的话，则通过equals来判断两个对象的内容是否相同
	public boolean equals(Object obj)
	{
		if(!(obj instanceof Person))
		{
			return false;
		}
		Person p=(Person)obj;
		System.out.println(this.name+"....equals....."+p.name);
		return this.name.equals(p.name)&&this.age==p.age;
	}
}
public class HashTest
{
	public static void main(String[] args)
	{
		HashSet HS=new HashSet();
		HS.add(new Person("lisi01",11));
		HS.add(new Person("lisi02",12));
		HS.add(new Person("lisi03",13));
		HS.add(new Person("lisi04",14));
		HS.add(new Person("lisi01",11));
		Iterator it=HS.iterator();
		
		while(it.hasNext())
		{
			Person p=(Person)it.next();
			System.out.println(p);
		}
	}
}
```
运行结果：  
![image](https://note.youdao.com/yws/public/resource/e36083821fb446484249f2a3cecc2908/xmlnote/7CAD344C8F9E4ED6BB83036D766BF935/1061)

#### B、TreeSet
* 1、原理：可以对Set集合中的元素进行排序
* 2、底层数据结构是二叉树
* 3、保证元素唯一性的依据：compareTo方法 return 0 
* 4、TreeSet排序的第一种方式：让元素自身具备比较性，元素需要实现Comparable接口，覆盖compareTo方法（也称为元素排序的自然方式）
* 代码例子：
```
package demo1;

import java.util.TreeSet;

import java.util.Iterator;

//该接口让Student类具有比较性
class Student implements Comparable
{
	private String name;
	private int age;
	
	Student(String name,int age)
	{
		this.name=name;
		this.age=age;
	}
	public String toString()
	{
		return this.name+"..."+this.age;
	}
	
	public int compareTo(Object obj)
	{
		if(!(obj instanceof Student))
			throw new RuntimeException("不是学生对象");
		Student s=(Student)obj;
		
		System.out.println(this.name+".....equals...."+s.name);
		if(this.age>s.age)
			return 1;
		if(this.age==s.age)
		{
			return this.name.compareTo(s.name);
		}
		return -1;
	}
}
public class TreeSetTest1
{
	public static void main(String[] args)
	{
		TreeSet ts=new TreeSet();
		
		ts.add(new Student("Java001",15));
		ts.add(new Student("Java01",18));
		ts.add(new Student("Java05",9));
		ts.add(new Student("Java09",9));
		ts.add(new Student("Java10",10));
		
		Iterator it=ts.iterator();
		
		while(it.hasNext())
		{
			Student s=(Student)it.next();
			
			System.out.println(s);
		}
	}
}
```
运行结果：  
![image](https://note.youdao.com/yws/public/resource/e36083821fb446484249f2a3cecc2908/xmlnote/4DF3E78AC9DC4BF2A390F8C37AE990CE/1063)
***
### 四、泛型
#### A、起源：
JDK1.5版本以后出现新特性，用于解决安全问题，是一个类型安全机制
#### B、优点：
* 1、将运行时期出现问题classCastException，转移到编译时期，方便程序员解决问题，让运行事情问题减少，更加安全
* 2、避免了强制转换麻烦
#### C、泛型格式：通过<>来定义要操作的引用数据类型
#### D、何时使用泛型：集合框架中经常使用，只要见到<>就要定义泛型
* 代码例子：
```
package demo1;
import java.util.TreeSet;
import java.util.Iterator;
import java.util.Comparator;

class Lencomparator implements Comparator
{
	public int compare(Object o1,Object o2)
	{
		String s1=(String)o1;
		String s2=(String)o2;
		
		int num=new Integer(s1.length()).compareTo(new Integer(s2.length()));
		if(num==0)
			return s1.compareTo(s2);
		
		return num;
	}
}


public class CommonTest 
{
	public static void main(String[] args)
	{
		//泛型指定集合接收类型为字符串
		TreeSet<String>ts=new TreeSet<String>(new Lencomparator());
		
		ts.add("abbc");
		ts.add("anded");
		ts.add("de");
		ts.add("x");
		
		//如果没有运用泛型的话,则需要(String)it.next()来强制转换类型
		Iterator<String>it=ts.iterator();
		
		while(it.hasNext())
		{
			String s=it.next();
			
			System.out.println(s);
		}
		
	}

}
```
运行结果：  
![image](https://note.youdao.com/yws/public/resource/e36083821fb446484249f2a3cecc2908/xmlnote/4D0C5DF67D204234B026FBB6E67C0D0A/1065)
 
#### E、泛型可以使用在
* 1、类上
* 2、方法上
> a、为了让不同的方法可以操作不同类型，而且类型还不确定，那么可以将泛型定义在方法上
* 代码例子：
```
package demo1;

//使用泛型使得方法可以接收多种类型的数据
class Demo
{
	//在方法中定义泛型
	public <T> void show(T t)
	{
		System.out.println("show："+t);
	}
	
	//在方法中定义泛型
	public <Q> void Print(Q q)
	{
		System.out.println("print："+q);
	}
}
public class CommonTest2
{
	public static void main(String[] args)
	{
		Demo d=new Demo();
		d.show("hahahaha");
		d.show(new Integer(4));
		d.Print(8);
	}

}
```
运行结果：  
![image](https://note.youdao.com/yws/public/resource/e36083821fb446484249f2a3cecc2908/xmlnote/8F9EB18812A54872BCD8607EAFEC8528/1067)
 
* 3、静态方法不可以访问类定义的泛型，如果静态方法操作的应用数据类型不确定，可以将泛型定义在方法上
* 代码例子：
``` 
public static <Q> void Print(Q q)
	{
		System.out.println("print："+q);
	}
 ```
* 4、泛型在接口上
* 代码例子：
```
package demo1;

interface Inter<T>
{
	void show(T t);
}
//使用泛型使得方法可以接收多种类型的数据
class Demo<T> implements Inter<T>
{
	//在方法中定义泛型
	public void show(T t)
	{
		System.out.println("show："+t);
	}
	
	//在方法中定义泛型
	public static <Q> void Print(Q q)
	{
		System.out.println("print："+q);
	}
}
public class CommonTest2
{
	public static void main(String[] args)
	{
		Demo<Integer> d=new Demo<Integer>();
		d.show(new Integer(4));
		d.Print("dd");
	}

}
```
运行结果：  
![image](https://note.youdao.com/yws/public/resource/e36083821fb446484249f2a3cecc2908/xmlnote/86031FC1F2A24A51B0D64315C2A9494F/1070)
 
