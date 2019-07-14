## Day7
### 一、匿名对象：匿名对象是对象的简化形式
匿名对象使用情况：  
* a、当对对象方法仅进行一次调用时  
* b、匿名对象可以作为实际参数进行传递  
代码：
```
class Car
{
	
	//描述对象
	String color="红色";
	//描述轮胎数
	int num=4;
	//运行行为
	void run()
	{
		System.out.println(color+"..."+num);
	}
}
```
①匿名对象调用对象方法
```
public class Class 
{
	public static void main(String[] args)
	{
		//Car c=new Car();
		//c.run();
		new Car().num=5;   
		//匿名对象中调用属性没有意义
		new Car().color="blue";
		//匿名对象中调用属性没有意义
		new Car().run();    
		//匿名对象对对象方法只调用一次时，可以通过匿名对象来完成，这样写比较简化
	}
	
}
```
***
②匿名对象作为实际参数进行传递
```
public class Class 
{
	public static void main(String[] args)
	{
		//Car Q=new Car();
		show(new Car());
		
	}
	public static void show(Car c)
	{
		c.num=5;
		c.color="blue";
		c.run();
	}
	
}
```
***
### 二、封装（Encapsulation）
###### a、封装定义：
指隐藏对象的属性和实现细节，仅对外提供公共访问方式
###### b、优点：
* 1、将变化隔离
* 2、便于使用
* 3、提高代码重用性
* 4、提高安全性
###### c、封装原则：
* 1、将不需要对外提供的内容都隐藏起来
* 2、把属性都隐藏，提供公共方法对其访问
```
class Person
{
	private int age;
	//在类中定义一个私有型的属性，只能在Person本类中访问
	public void SetAge(int a)  //public类型的可以被外界访问
	{
		age=a;
	}
	public int GetAge()
	{
		return age;
	}
	void showperson()
	{
		System.out.println("age="+age);
	
	}
}
public class PersonDemo 
{
	public static void main(String[] args)
	{
		Person p=new Person();
		//主函数中创建一个Person类的对象
		p.SetAge(20);
		p.showperson();
	}
}
```
### 三、构造函数
* a、构造函数特点：  
 1、函数名和类名相同  
 2、不用定义返回值类型  
 3、不用写return语句  
* b、作用：给对象进行初始化
* c、注意：  
1、默认构造函数的特点   
2、多个构造函数是以重载的形式存在  
3、当一个类中没有定义构造函数时，系统会自动构造一个没有参数的构造函数
* d、构造函数和一般函数的区别：  
1、构造函数就是在对象一建立就运行，给对象进行初始化  
2、一般方法就是对象调用才执行，给对象添加对象具备的功能    
3、一个对象建立，构造函数只运行一次  
4、而一般方法可以被该对象调用多次
```
class Person
{
	private String name;
	private int age;
	Person()	//没有参数的构造函数
	{
		System.out.println("A:name="+name+"..."+"age="+age);
	}
	Person(String n)	//含有一个参数的构造函数
	{
		name=n;
		System.out.println("B:name="+name+"..."+"age="+age);
	}
	Person(String n,int Age)	//含有两个参数的构造函数
	{
		name=n;
		age=Age;
		System.out.println("C:name="+name+"..."+"age="+age);
	}
}
public class PersonDemo 
{
	public static void main(String[] args)
	{
		Person p=new Person("小帅",15);
	}
}
```
***
### 四、构造代码块
*a、构造代码块作用：给对象进行初始化
*b、特点：  
1、对象一建立就运行，而且优先于构造函数执行  
2、构造代码块是给所有对象进行统一初始化  
3、构造函数是给对应对象初始化  
4、构造代码块中定义的是不同对象共性的初始化内容
```
class Person
{
	private String name;
	private int age;
	Person()	//没有参数的构造函数
	{
		System.out.println("A:name="+name+"..."+"age="+age);
	}
//构造代码块
	{
		System.out.println("Calulate code");
	}
}
public class PersonDemo 
{
	public static void main(String[] args)
	{
		Person c=new Person();
		Person p=new Person("小帅",15);
	}
}
```
***
### 五、this关键字
* a、this关键字：区分局部变量和成员变量同名的情况
* b、this代表它所在函数所属对象的引用（哪个对象在调用this所在的函数，this就代表哪个对象）
```
//p1调用person类中的compare函数，则this就代表p1这个对象
class Person
{
	private String name;
	private int age;
public boolean Compare(Person p)
	{
		return this.age==p.age;
	}
}

public class PersonDemo 
{
	public static void main(String[] args)
	{
		Person p1=new Person(12);
		Person p2=new Person(99);
		boolean b=p1.Compare(p2);
		System.out.println(b);
	}
}
```
* c、Java中构造函数间调用必须用this关键字
* d、this语句只能定义在构造函数的第一行。因为初始化要先执行  
代码
```
class Ren
{
	private String name;
	private int age;
	Ren(String Name)
	{
		name=Name;
	}
	Ren(String Name,int Age)
	{
		this(Name);  
		//等同于this.name=Name 构造函数间的调用必须使用this关键字
		this.age=Age;
		this.ShowPerson();
	}
	void ShowPerson()
	{
		System.out.print(name+" "+age);
	}
}
public class Person 
{
	public static void main(String[] args)
	{
		Ren person=new Ren("小帅",28);
		
	}
}
```
***
### 六、static（静态）关键字
* a、作用：属于修饰符，用于修饰成员（成员变量和成员函数）
* b、被修饰后的成员具备的特点：  
1、随着类的加载而加载（静态会随着类的消失而消失，说明它的生命周期最长）  
2、优先于对象存在（静态是先存在，对象是后存在）  
3、被所有对象所共享  
4、可以直接被类名调用
* c、注意：  
1、静态方法只能访问静态成员（非静态方法既可以访问静态也可以访问非静态）  
2、静态方法中不可以写this、super关键字  
3、主函数是静态的
* d、什么时候使用静态函数：当功能内部没有访问非静态数据（对象特有数据）    
代码：
```
class Ren
{
	String name; //成员变量、实例变量
	static String country="CN"; //静态的成员变量、类变量
	Ren(String Name,String Country)
	{
		name=Name;
		country=Country;
		show();
	}
	public void show()
	{
		System.out.println("name="+name+"  country="+country);
	}
}
public class Person 
{
	public static void main(String[] args)
	{
		Ren person=new Ren("帅哥","AM");
		System.out.println(Ren.country); 
		//可以通过类名来调用静态变量	
	}
}
```
***
### 七、有关于主函数的知识点
* a、主函数：主函数是一个特殊的函数，作为程序的入口，可以被jvm调用
* b、主函数定义：  
①public: 代表着该函数访问权限是最大的  
②static：代表着主函数随着类的加载就已经存在了  
③void：主函数没有具体的返回值  
④main：不是关键字，但是是一个特殊的单词，可以被jvm识别  
⑤(String[] args)：函数的参数，参数类型是一个数组，该数组中的元素是字符串  
⑥主函数是固定格式的：jvm识别  
⑦jvm在调用主函数时，传入的是new String[0]
***
### 八、静态代码块
* a、格式：
```
static
{
	静态代码块中的执行语句
}
```
* b、特点：随着类的加载而执行，只执行一次，用于给类初始化
```
class StaticCode
{
	static //静态代码块
	{
		System.out.println("a");
	}
}
public class StaticTest 
{
	static  //静态代码块  随着类StaticTest执行而加载进内存，进行执行
	{
		System.out.println("b");
	}
	public static void main(String[] args)
	{
		new StaticCode();
		System.out.println("over");
	}
	static //静态代码块  随着类StaticTest执行而加载进内存，进行执行
	{
		System.out.println("c");
	}
}
```
运行结果：  
![image](http://note.youdao.com/yws/public/resource/ad4fc9c0144435fffff31abef2eded3a/xmlnote/B6963075A7DC482E98F017FA3CB1C66F/605)  
//静态代码块、构造代码块的执行顺序
```
class StaticCo
{
	StaticCode()
	{
		System.out.printlu("d");
	}
	static //静态代码块
	{
		System.out.println("a");
	}
	{
		System.out.println("e");
	}
	StaticCode(int x)
	{
		System.out.println("f");
	}
}
public class StaticTest 
{
	static  //静态代码块  随着类StaticTest执行而加载进内存，进行执行
	{
		System.out.println("b");
	}
	public static void main(String[] args) 
	{
		new StaticCode(8);
		System.out.println("over");
	}
	static //静态代码块  随着类StaticTest执行而加载进内存，进行执行
	{
		System.out.println("c");
	}
}
```
运行结果：  
![image](http://note.youdao.com/yws/public/resource/ad4fc9c0144435fffff31abef2eded3a/xmlnote/C23520CA8B8740B8ACB6FC92C5F39B4E/607)
***
 ### 九、创建对象时的具体操作  
> person p=new person("帅哥","AM");
* a、因为new用到了person.class 所以会先找到person.class文件并加载到内存中
* b、执行该类中的static代码块，如果有的话，给person.class 类进行初始化
* c、在堆内存中开辟空间，分配内存地址
* d、在堆内存中建立对象的特有属性，并进行默认初始化
* e、对属性进行显示初始化
* f、对对象进行构造代码块初始化
* g、对对象进行对应的构造函数初始化
* i、将内存地址赋给内存中的p变量
***
