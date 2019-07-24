[toc]
## Day17
### 一、Map集合
#### A、特点
* 1、Map集合将键映射到值的对象，一个映射不能包含重复的键
* 2、每个键最多只能映射一个值
* 3、Map接口和Collection接口的不同
> ①Map是双列的，Collection是单列的  
②Map的键唯一，Collection的子体系Set是唯一的。Set集合底层依赖的是Map集合  
③Map集合的数据结构只针对键有效，跟值无关 Collection集合的数据结构是针对元素有效
#### B、基本功能
* 1、增加  
①put(k key,value)：添加元素时，如果出现添加时相同的键，那么后面添加的值会覆盖原有键的对应值，put会返回原来的值  
②putAll(Map< extends k,extends v> m
* 2、删除
> ①clear()：移除所有的键值对元素  
②remove()：根据键删除键值元素，并把值返回
* 3、判断
> ①containsValue(Object value)：判断集合是否包含指定的值  
②containsKey(Object Key)：判断集合是否包含指定的键  
③isEmpty()：判断集合是否为空
* 4、获取  
①get(Object key)  
②size()  
③values()  
④entrySet()  
⑤keyset()

* 代码例子：
```
package package1;

import java.util.Map;
import java.util.HashMap;
import java.util.Collection;

public class MapTest 
{
	public static void main(String[] args)
	{
		Map<String,String> map=new HashMap<String,String>();
		
		//添加元素
		map.put("01","zhangsan1");
		map.put("02","zhangsan2");
		map.put("03","zhangsan3");
		
		//判断元素
		System.out.println("判断containsKey："+map.containsKey("02"));
		System.out.println("判断containsKey："+map.containsKey("022"));
		
		//获取某个指定的元素
		System.out.println("get："+map.get("023"));
		System.out.println("get："+map.get("02"));
		
		//获取map集合所有数据，不获取键名
		Collection<String> coll=map.values();
		System.out.println(coll);
		
		//获取map集合中的所有数据，包括键名
		System.out.println(map);
		
		//获取集合map的数据个数
		System.out.println(map.size());
	}
}
```
运行结果：  
![image](https://note.youdao.com/yws/public/resource/e36083821fb446484249f2a3cecc2908/xmlnote/7C26AA28E38A4B4D99A2828BE13AD311/1148)
 
#### C、map集合的两种取出方式
* 1、KeySet
#### D、子类对象
* 1、Hashtable：底层是哈希表数据结构，不可以存入null键和null值，该线程是同步的（效率低）
* 2、HashMap：底层是哈希表数据结构，允许使用null键和null值，该集合是不同步的（效率高）
* 3、TreeMap：底层是二叉树数据结构，线程不同步。可以用于给Map集合中的键进行排序

