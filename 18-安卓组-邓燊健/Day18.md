[toc]
## Day18
### 一、map集合的两种取出方式
#### A、keySet：将map中所有的键存入到Set集合
* 1、作用原理：Set具备迭代器，所以可以迭代方式取出所有的键，在根据get方法，获取每一个对应的键（Map集合转成Set集合，然后再迭代器中输出）
* 2、代码例子：
```
package Package1;

import java.util.Map;
import java.util.HashMap;
import java.util.Set;
import java.util.Iterator;

public class keySetTest 
{
	public static void main(String[] args)
	{
		Map<String,String> map=new HashMap<String,String>();
		
		map.put("04","zhangsan4");
		map.put("01","zhangsan1");
		map.put("02","zhangsan2");
		map.put("03","zhangsan3");
		
		//先获取map集合的所有键的Set集合，keySet()
		Set<String> keySet=map.keySet();
		
		//有了Set集合，就可以获取其迭代器
		Iterator<String> it=keySet.iterator();
		
		while(it.hasNext())
		{
			String key=it.next();
			
			//有了键可以通过map集合的get方法获取其对应的值
			String value=map.get(key);
			
			System.out.println("key:"+key+"...value:"+value);
			
			
		}
	}
}
```
运行结果：  
![image](https://note.youdao.com/yws/public/resource/e36083821fb446484249f2a3cecc2908/xmlnote/61285DF91B034E9DB394BAAAB747CEE7/1165)
 
 
#### B、entrySet
* 1、格式： Set<Map.Entry<k,v>> entrySet=Map.entrySet();
* 2、作用：将Map集合中的映射关系取出，存入Set集合中

* 3、代码例子：
```
package Package1;

import java.util.Map;
import java.util.HashMap;
import java.util.Set;
import java.util.Iterator;

public class entyrSetTest 
{
	public static void main(String[] args)
	{
		Map<String,String> map=new HashMap<String,String>();
		
		map.put("04","zhangsan4");
		map.put("01","zhangsan1");
		map.put("02","zhangsan2");
		map.put("03","zhangsan3");
		
		//将Map集合的映射关系取出，存入Set集合中
		Set<Map.Entry<String,String>> entrySet=map.entrySet();
		
		Iterator<Map.Entry<String, String>> it=entrySet.iterator();
		
		while(it.hasNext())
		{
			Map.Entry<String, String> me=it.next();
			
			String key=me.getKey();
			String value=me.getValue();
			
			System.out.println("key:"+key+"  value:"+value);
		}
	}
}
```
运行结果:  
![image](https://note.youdao.com/yws/public/resource/e36083821fb446484249f2a3cecc2908/xmlnote/EBB54BF1E4C64A2B958F67E2F78B8763/1167)
 
* C、keySet和entrySet的代码测试：
```
//Map集合两种取出方法的测试
package Package1;

import java.util.HashMap;
import java.util.Set;
import java.util.Iterator;
import java.util.Map;

class Student implements Comparable<Student>
{
	private String name;
	private int age;
	
	Student(String name,int age)
	{
		this.name=name;
		this.age=age;
	}
	
	public String Getname()
	{
		return this.name;
	}
	
	public int Getage()
	{
		return this.age;
	}
	
	public int compareTo(Student s)
	{
		int num=new Integer(this.age).compareTo(new Integer(s.age));
		
		if(num==0)
			return this.name.compareTo(s.name);
		
		return num;
		
	}
	
	//获取哈希值
	public int hashCode()
	{
		return name.hashCode()+age*34;
	}
	
	//和hashCode配套使用
	public boolean equals(Object obj)
	{
		if(!(obj instanceof Student))
			throw new ClassCastException("类型不匹配");
		
		Student s=(Student)obj;
	
		return this.name.equals(s.name)&&this.age==s.age;
	}
	
	
	public String toString()
	{
		return this.name+"  "+this.age;
	}
}
public class StudentTest 
{
	public static void main(String[] args)
	{
		HashMap<Student,String> hm=new HashMap<Student,String>();
		
		hm.put(new Student("zhangsan01",11),"北京市");
		hm.put(new Student("zhangsan03",13),"上海市");
		hm.put(new Student("zhangsan02",12),"广州市");
		hm.put(new Student("zhangsan04",14),"杭州市");
		
		//1、keySet的使用
		System.out.println("1、keySet的使用");
		Set<Student> keySet=hm.keySet();
		
		Iterator<Student> it=keySet.iterator();
		
		while(it.hasNext())
		{
			Student s=it.next();
			String address=hm.get(s);
			
			System.out.println(s+"  "+address);
		}
		
		//2、entrySet的使用
		System.out.println("2、entrySet的使用");
		Set<Map.Entry<Student,String>> entrySet=hm.entrySet();
		
		Iterator<Map.Entry<Student,String>> it1=entrySet.iterator();
		
		while(it1.hasNext())
		{
			Map.Entry<Student, String> s1=it1.next();
			
			Student student=s1.getKey();
			String  assress=s1.getValue();
			
			System.out.println(student+"....."+assress);
		}
	}
}
```
运行结果：  
![image](https://note.youdao.com/yws/public/resource/e36083821fb446484249f2a3cecc2908/xmlnote/8EA86AB507134F97959D4457AEEE698C/1169)
 
* D练习：字符在字符串"sdfgzxcvasdfxcvdf"中出现的次数  
思路：  
* 1、将字符串转换成字符数组，因为要对每一个字母进行操作  
* 2、定义一个Map集合，因为打印结果的字母有顺序，所以使用TreeMap集合  
* 3、遍历字符数组
 > ①将每一个字母作为键去查map集合  
②如果返回null，该字母和1存入到map集合中  
③如果返回不是null，说明该字母子map集合已经存在并且有对应的次数  
③那么久获取该次数并进行自增，然后将该字母和自增后的次数存入到map集合中，覆盖调用原有键所对应的值
* 代码例子：
```
package Package1;

import java.util.Set;
import java.util.Map;
import java.util.Iterator;
import java.util.TreeMap;
public class Test
{
	public static void main(String[] args)
	{
		String s=charCount("sdfgzxcvasdfxcvdf");
		System.out.println(s);
	}
	
	public static String charCount(String str)
	{
		//字符串转换成字符数组类型
		char [] chs=str.toCharArray();
		
		//创建一个TreeMap对象
		TreeMap<Character,Integer> tm=new TreeMap<Character,Integer>();
		for(int x=0;x<chs.length;x++)
		{
			//运用字母作为键去查找数据
			Integer value=tm.get(chs[x]);
			
			//字符查找为空的话，则将字符和1存进集合
			if(value==null)
			{
				tm.put(chs[x], 1);
			}
			//不存在数据的话
			else
			{
				value=value+1;
				tm.put(chs[x],value);
			}
		}
		
		StringBuilder sb=new StringBuilder();
		
		Set<Map.Entry<Character,Integer>> entrySet=tm.entrySet();
		
		Iterator<Map.Entry<Character,Integer>> it=entrySet.iterator();
		
		while(it.hasNext())
		{
			Map.Entry<Character, Integer> me=it.next();
			Character ch=me.getKey();
			Integer value=me.getValue();
			sb.append(ch+"（"+value+"）");
		}
		
		return sb.toString();
		
	}
}
```
运行结果：  
![image](https://note.youdao.com/yws/public/resource/e36083821fb446484249f2a3cecc2908/xmlnote/0BF557363F2D47298CE05B9989093DC4/1171)
  
### 二、Map子类对象
#### A、Hashtable
1、作用原理：  
>底层是哈希表数据，不允许存入null键和null值，该集合线程是同步的，效率低
#### B、HashMap
1、作用原理：  
底层是哈希表数据结构，允许使用null键和null值，该集合线程是不同步的，将Hashtable替代，效率够高
#### C、底层是二叉树数据结构。线程不同步，可以用于给Map集合中的键进行排序

### 三、集合框架的工具类collections
#### A、基本功能
* 1、Collections.sort(list)：对list集合进行元素的自然顺序排序
* 2、Collections.sort(list,new ComparatorByLen)：按照指定的比较器进行排序
* 3、Collection.max(list)：返回list中字典顺序的最大的元素
* 4、int index=collections.binarySearch(list,”zz”)：二分查找，返回角标
* 5、Collections.reverseOrder()：逆向反转排序
* 6、Collections.swap(list,1,2)：将集合list中下标为1和下标为2的元素进行交换
#### B、Collection和Collections的区别
* 1、Collections是java.util下的类，是针对集合类的一个工具类，提供一系列静态方法，实现对集合的查找、排序、替换、线程安全化（将非同步的集合转换成同步的）等操作
* 2、Collection是java.util下的接口，它是各种集合结构的父接口，继承于它的接口主要是Set和List，提供了关于集合的一些操作，如插入、删除、判断、遍历等
