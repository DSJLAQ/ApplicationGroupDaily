## Day8
### 一、单例设计模式
* a、首先知道：设计模式：解决某一类问题最行之有效的方法
* b、Java中有23种设计模式
* c、单例设计模式：解决一个类在内存只存在一个对象
* e、设计思路：
>1、第一步：为了避免其他程序过多建立该类对象，先禁止其他程序建立该类对象  
2、第二步：为了让其他程序可以访问到该类对象，只好在本类中，自定义一个对象  
3、第三步：为了方便其他程序对自定义对象的访问，可以对外提供一些访问方式
* f、通过代码实现设计思路：
>1、第一步：将类中的构造函数私有化  
2、第二步：在类中创建一个本类对象  
3、第三步：提供一个方法可以获取到该类对象
* g、定义单例设计模式的方式：（最好使用饿汉式）
>1、饿汉式  
2、懒汉式  
* 代码：第一种方式
```
//单例设计模式过程
class TypeTest
{
	//第一步：在本类中创建一个私有类型的构造函数
	private TypeTest()	
	{
		
	}
	//第二步：在本类中创建一个该类的对象
	static TypeTest student=new TypeTest();
	private static String Name;
	
	public static void setName(String name)
	{
		Name=name;
	}
	//第三步：提供访问方法来获取该类对象
	public static TypeTest Student()
	{
		return student;
	}
	public static void show()
	{
		System.out.println("Name="+Name);
	}
}
public class Type 
{
	public static void main(String[] args)
	{
		TypeTest s=TypeTest.Student();
		s.setName("大帅");
		s.show();
	}
}
```
* 第二种方式：懒汉式（对象方法被调用时，才开始初始化）
```
class typeTest
{
	private typeTest()
	{
		
	}
	private static typeTest student=null;
	private static String Name;
	public static void setName(String name)
	{
		Name=name;
	}
	//懒汉式代码核心
	public static typeTest Student()
	{
		if(student==null)
			student=new typeTest();
		return student;
	}
	public static void show()
	{
		System.out.println("Name2="+Name);
	}
	
}
public class Type 
{
	public static void main(String[] args)
	{
		typeTest s2=typeTest.Student();
		s2.setName("小帅");
		s2.show();
	}
}
```
***
### 二、继承
* a、继承的概述
>1、提高代码的复用性  
2、让类和类之间产生关系，有了这个关系，才有了多态的特性  
3、Java只支持单继承，不支持多继承  
4、多继承会带来安全隐患、子类对象不确定要运行哪一个  
5、Java支持多层继承，也就是一个继承体系
* b、使用一个继承体系的功能步骤：
>1、想要使用体系，首先查阅体系父类的描述，因为父类中定义的是该体系中共性功能  
2、通过了解共性功能，就可以知道该体系的基本功能  
3、此时体系已经可以基本使用
* c、具体调用时，创建最子类对象的原因：
>1、父类可能不能创建对象  
2、创建子类对象可以使用更多的功能，包括基本的也包括特有的
* d、构造函数  
>1、变量：如果子类中出现非私有的同名成员变量时，有两种访问方式：  
①子类要访问本类中的变量，用this  
②子类要访问父类的变量，用super  
2、this和super的用法  
①this代表的是本类对象的引用  
②super代表的是父类对象的引用
* 代码：
```
class Parent	//父类
{
	int num=5;	//定义一个num变量
}
class Son extends Parent  //子类，通过关键字extends来继承父类
{
	int num=4;  //定义一个num变量
	public void show()
	{
		//通过super关键字来访问父类成员num
		System.out.println("通过super关键字来访问父类成员num:"+super.num);
		//通过this关键字来访问本类成员num
		System.out.println("通过this关键字来访问本类成员num:"+this.num);
	}
}
public class inherit1 
{
	public static void main(String[] args)
	{
		Son s=new Son(); //创建一个Son的对象s
		s.show();
	}

}
```
运行结果：  
![image](http://note.youdao.com/yws/public/resource/ad4fc9c0144435fffff31abef2eded3a/xmlnote/2A16A12AC0BD4078BD55A47A283D9F06/655)
 * e、子父类中的函数
>1、当子类出现和父类一模一样的函数时，当子类对象调用该函数，会运行子类函数的内容，如同父类的函数被覆盖一样（这种情况是函数的另一个特性：重写（覆盖））  
2、当子类继承父类，沿袭了父类的功能，到子类中，但是子类虽然具备该功能，但是功能的内容却和父类不一致，这时，没有必要定义新功能，而是使用覆盖特殊，保留父类的功能定义，并重写功能内容  
3、覆盖注意事项：  
①：子类覆盖父类，必须保证子类权限大于或者等于父类权限，这样子才可以覆盖，否则编译失败  
②：静态只能覆盖静态
* f、重写和重载：
> 1、重写：只看同名函数的参数列表  
2、重载：字父类方法一模一样  
* 代码：
```
class Parent	//父类
{
	int num=5;	//定义一个num变量
	public void show()
	{
		System.out.println("show1");
	}
}
class Son extends Parent  //子类，通过关键字extends来继承父类
{
	int num=4;  //定义一个num变量
	public  void show()
	{
		System.out.println("show2");
	}
}
public class inherit1 
{
	public static void main(String[] args)
	{
		Son s=new Son(); //创建一个Son的对象s
		s.show();
	}

}
```
运行结果：  
![image](http://note.youdao.com/yws/public/resource/ad4fc9c0144435fffff31abef2eded3a/xmlnote/C7064B17881A43F6A59E9C4E17BB9DEC/667)
 

* h、字父类中的构造函数
> 1、在对子类对象进行初始化时，父类的构造函数也会运行  
2、原因：子类的构造函数默认第一行有一条隐式的语句：super();  
3、子类一定要访问父类中的构造函数的原因：父类中的数据子类可以直接获取，所以子类对象在建立时，需要先查看父类是如何对这些数据进行初始化的  
4、如果要访问父类中指定的构造函数，可以通过手动定义super语句的方式来指定（super语句一定定义在子类构造函数中的第一行）  
5、结论：  
①：子类中的所有构造函数，默认都会访问父类中空参数的构造函数  
②：子类中每一个构造函数内的第一行都有一句隐式super();  
③：当父类中没有空参数的构造函数时，子类必须手动通过super语句形式来指定要访问父类中的构造函数  
④：子类的构造函数第一行也可以手动指定this语句来访问本类中的构造函数  
⑤：子类中至少会有一个构造函数会访问父类中的构造函数
```
class Parent	//父类
{
	int num=5;	//定义一个num变量
	Parent()
	{
		System.out.println("Parent");
	}
}

class Son extends Parent  //子类，通过关键字extends来继承父类
{
	int num=4;  //定义一个num变量
	Son()
	{
		//省略super();语句
		System.out.println("1");
	}
	Son(int Num)
	{
		//省略 super();语句
		System.out.println("Son");
	}
}
public class inherit1 
{
	public static void main(String[] args)
	{
		Son S=new Son();
		Son s=new Son(88); //创建一个Son的对象s
	}

}
```
* i、final关键字
> 1、final可以修饰类、方法、变量  
2、final修饰的类不可以被继承  
3、final修饰的方法不可以被覆盖  
4、final修饰的变量是一个常量，只能被覆盖一次  
5、内部类只能访问被final修饰的局部变量
* j、抽象
> 1、产生：当多个类中出现相同功能，但是功能主体不同，这时可以进行向上抽取，而只能抽取功能定义，而不能抽取功能主体  
2、抽象类的特点：  
①：抽象方法一定在抽象类中  
②：抽象方法和抽象类都必须被abstract关键字修饰  
③：抽象类不可以用new创建对象，因为调用抽象方法没有意义  
④：抽象类中的方法要被使用，必须由子类复写起所有的抽象方法后，建立子类对象调用（如果子类只覆盖了部分抽象方法，那么该子类还是一个抽象类）  
⑤：抽象类和一般类的最大区别：抽象类比一般类多了个抽象函数、抽象类不可以实例化  
⑥：抽象类中可以不定义抽象方法，这样做仅仅是使类不创建对象
* 代码：
```
abstract class dd	//定义一个抽象类
{
	abstract void Study();//抽象方法在抽象类中
}
class BaseStudent extends dd	//继承抽象类dd
{
	void Study()  //复用并改写抽象方法Study
	{
		System.out.println("Base Study");
	}
}
class AdvancedStudent extends dd  //继承抽象类dd
{
	void Study()	//复用并改写抽象方法Study
	{
		System.out.println("Advanced Study");
	}
}
public class AbstractTest 
{
	public static void main(String[] args)
	{
		BaseStudent s1=new BaseStudent();
		s1.Study();
		AdvancedStudent s2=new AdvancedStudent();
		s2.Study();
	}

}
```
* K、模板方法设计模式  
>模板设计模式的定义：在定义功能时，功能的一部分是确定的，但是有一部分是不确定的，而确定的部分在使用不确定的部分，那么这时候就将不确定的部分暴露出去，由该类的子类去完成
***
### 三、接口  
（初期理解，可以认为接口是一种特殊的抽象类）
* a、格式：interface{ }
* b、接口中的成员修饰符是固定的（接口中的成员都是public类型的）
> 1、成员变量：public  static  final  
2、成员函数：public  abstract
* c、接口的出现将“多继承”通过另一种形式体现出来，即“多实现”
* d、因为接口有抽象方法，因此接口是不可以创建对象的
* e、接口需要子类去实现，子类对接口的抽象方法全部覆盖后，子类才可以实例化，否则子类是一个抽象类
* 代码：
```
interface Inter		//创建一个名为Inter的接口
{
	//在接口中，变量的定义必须是：Public static final 变量类型  变量名称;
	public static final int X=3;
	//在接口中，方法的定义必须是：Public abstract 函数返回类型  函数名(……);
	public abstract void Show();
}
//通过implements关键字来创建子类，实现接口的功能
class Test implements Inter 	
{
	public void Show()	//子类对接口中的抽象方法进行覆盖
	{
		
	}
}
public class Interface 
{
	public static void main(String[] args)
	{
		Test t=new Test(); //创建一个子类的对象
		System.out.println(t.X); //可以通过子类中创建的对象调用接口中的成员
		System.out.println(Test.X); //可以通过子类的类名来调用接口中的成员
		System.out.println(Inter.X);  //可以通过接口的名称来调用接口中的成员
	}
}
```
运行结果：  
![image](http://note.youdao.com/yws/public/resource/ad4fc9c0144435fffff31abef2eded3a/xmlnote/B10F85977AF9435BBF764524989DD34A/694)
* f、类、接口之间的关系
>1、类和类之间是属于继承关系  
2、类和接口之间是属于实现关系  
3、接口和接口之间是属于继承关系
* d、接口可以进行多个接口的继承
* 代码：
```
interface InterA	//创建一个名为InterA的接口
{
	//在接口中，变量的定义必须是：Public static final 变量类型  变量名称;
	public static final int X=3;
	//在接口中，方法的定义必须是：Public abstract 函数返回类型  函数名(……);
	public abstract void Show1();
}
interface InterB
{
	public static final int Y=4;
	public abstract void Show2();
}
//接口之间可以进行多继承，接口InterC继承了接口InterA和InterB
interface InterC extends InterA,InterB
{
	public static final int Z=5;
	public abstract void Show3();
}
//通过implements关键字来创建子类，实现接口的功能
//并且子类Test必须覆盖上面的接口抽象方法
class Test implements InterC
{
	public void Show1()	//子类对接口中的抽象方法进行覆盖
	{
		System.out.println("第一个接口的抽象方法代码主体");
	}
	public void Show2() //子类对接口中的抽象方法进行覆盖
	{
		System.out.println("第二个接口的抽象方法代码主体");
	}
	public void Show3() //子类对接口中的抽象方法进行覆盖
	{
		System.out.println("第三个接口的抽象方法代码主体");
	}
	public static void Show()
	{
		System.out.println("X="+X+" Y="+Y+" Z="+Z);
	}
}
public class Interface 
{
	public static void main(String[] args)
	{
		Test t=new Test(); //创建一个子类的对象
		t.Show1();
		t.Show2();
		t.Show3();
		t.Show();
	}
}
```
运行结果:  
![image](http://note.youdao.com/yws/public/resource/ad4fc9c0144435fffff31abef2eded3a/xmlnote/3D990DB8023343249BAAAFD0865DED4E/705)
* e、接口的特点：
>1、接口是对外暴露的规则  
2、接口是程序的功能扩展  
3、接口可以用来实现  
4、类与接口之间是是实现关系，而且类在继承一个类的同时可以实现多个接口  
5、接口之间可以有继承关系
* 代码：
```
interface InterA	//创建一个名为Inter的接口
{
	//在接口中，变量的定义必须是：Public static final 变量类型  变量名称;
	public static final int X=3;
	//在接口中，方法的定义必须是：Public abstract 函数返回类型  函数名(……);
	public abstract void Show1();
}
interface InterB
{
	public static final int Y=4;
	public abstract void Show2();
}
class Test1
{
	public void Show()
	{
		System.out.println("小帅");
	}
}
class Test2 extends Test1 implements InterA,InterB
{
	public void Show1()	//子类对接口中的抽象方法进行覆盖
	{
		System.out.println("第一个接口的抽象方法代码主体");
	}
	public void Show2() //子类对接口中的抽象方法进行覆盖
	{
		System.out.println("第二个接口的抽象方法代码主体");
	}
	
}
```
***