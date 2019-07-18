[toc]
## Day11
### 一、多线程的运行出现了安全问题
#### a、问题的原因：
> 当多条语句在操作同一个线程共享数据时，一个线程对多条语句只执行了一部分，还没有执行完，另一个线程参与进来执行，导致共享数据的错误
#### b、解决办法：
> 1、对多条操作共享数据的语句，只能让一个线程都执行完，在执行过程中，其他线程不能参与执行  
2、Java中对于多线程的安全问题提供了专业的解决方式，就是同步代码块  
格式如下：
```
	Synchronized(对象)
{
	需要被同步的代码
}
```
#### c、注意：
> 1、对象如同锁，持有锁的线程可以在同步中执行  
2、没有持有锁的线程即使获得cup执行权，也进不去，因为没有获取锁  
3、同步前提：  
①：必须要有两个或者两个以上的线程  
②：必须是多个线程使用同一个锁  
4、同步的优点和缺点  
①：优点：解决了多线程的安全问题  
②：缺点：多个线程需要判断锁，需要消耗资源
#### d、如何找问题
> 1、明确哪些代码是多线程运行代码  
2、明确共享数据  
3、明确多线程运行代码中哪些语句是操作共享数据的
##### e、同步函数用的是锁是this：函数同步需要对象调用，那么函数都有一个所属对象引用 即this
* 代码：
```
package Package3;

class Ticket implements Runnable
{
	private   int tick=100;
	Object obj=new Object();
	public void run()
	{
		
			while(true)
			{
				synchronized(obj)
				{
					if(tick>0)
					{
						try{Thread.sleep(10);}catch(Exception e){ }
						System.out.println(Thread.currentThread().getName()+"sale："+tick--);
					}
				}
			}
	}
}
public class TicketDemo 
{
	public static void main(String[] args)
	{
		Ticket t=new Ticket();
		Thread t1=new Thread(t);
		Thread t2=new Thread(t);
		Thread t3=new Thread(t);
		Thread t4=new Thread(t);
		t1.start();
		t2.start();
		t3.start();
		t4.start();		
	}
}
```
#### f、静态的同步方法：使用的锁是：所在类的字节码文件对象（类名.class）
#### g、单例设计模式中通常使用饿汉式
> 1、如果需要进行单例设计模式对象延迟创建，则使用饿汉式创建对象
* 代码：
```
package Package3;

//饿汉式
class Single
{
	int b;
	private static final Single s=new Single();
	private Single()
	{
		
	}
	public static Single getInstance()
	{
		return s;
	}
	public void set(int a)
	{
		b=a;
		System.out.println("饿汉式方法："+b);
	}
}
//懒汉式：单例设计模式对象加载延迟
class Single1
{
	int b;
	private static Single1 s1=null;
	private Single1()
	{
		
	}
	public static Single1 getInstance1()
	{
		if(s1==null)
		{
			//实现同步
			synchronized(Single.class)
			{
				if(s1==null)
					s1=new Single1();
			}
		}
		return s1;
	}
	public void set1(int a)
	{
		b=a;
		System.out.println("懒汉式方法："+b);
	}
}
public class LanHan 
{
	public static void main(String[] args)
	{
		//创建饿汉式对象
		Single s1=Single.getInstance();
		s1.set(2);
		//创建懒汉式对象
		Single1 s2=Single1.getInstance1();
		s2.set1(3);
	}
}
```
***
### 二、线程间的通讯
#### a、定义：
> 多个线程在操作同一个资源，但是操作的动作不同
#### b、wait()、notifyAll()用来操作线程为什么要定义在Object类中？
>1、这些方法存在于同步中  
2、使用这些方法时必须要标识所属的同步的锁  
3、锁可以是任意对象，所以任意对象调用的方法一定定义Object类中
#### c、wait()、sleep()有什么区别？
> 1、wait()：释放资源，释放锁  
2、sleep()：释放资源，但是不释放锁
*** 