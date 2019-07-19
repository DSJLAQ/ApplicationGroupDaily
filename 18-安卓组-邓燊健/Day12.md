[toc]
## Day12
### 一、多线程的通讯
#### A、等待唤醒机制
> 
* 1、wait():将线程等待，释放CPU执行权，同时将线程对象存储到线程池中  
* 2、notify():唤醒线程池中的一个等待的线程，若线程池有多个等待的线程，则任意唤醒一个  
* 3、notifyAll():唤醒线程池中所有的等待中的线程  
* 4、注意：  
> ①：这三个方法都要使用在同步中，因为要对持有锁的线程进行操作（比如：A锁上的线程被wait后，那么这个线程就进入了A锁的线程池中，只能被A锁的notify唤醒，不能被不同锁的其他线程唤醒）  
> ②：这三个方法要使用在同步中，因为只要同步才具有锁（锁的对象是任意的，所以这三个方法定义在Object中）  
代码：
```
package com.demo1;

//多线程的通讯等待唤醒机制
class Res
{
	String name;
	String sex;
	boolean flag=false; 	//等待唤醒机制
}

class Input implements Runnable
{
	private Res r;
	Input(Res r)
	{
		this.r=r;
	}
	public void run()
	{
		int x=0;
		while(true)
		{
			synchronized(r)	//等待和唤醒，是同一个锁
			{
				if(r.flag)	
					try
					{
						r.wait();
					}
					catch(Exception e)
					{
							System.out.println("出错啦！");
					}
					if(x==0)
					{
						this.r.name="Mike";
						this.r.sex="man";
					}
					else
					{
						this.r.name="丽丽";
						this.r.sex="女";
					}
				x=(x+1)%2;
				r.flag=true;
				r.notify();
			}
		}
	}
}

class Output implements Runnable
{
	private Res r;
	Output(Res r)
	{
		this.r=r;
	}
	public void run()
	{
		
		while(true)
		{
			synchronized(r) //等待和唤醒，是同一把锁
			{
				if(!r.flag)	//等待唤醒机制
					try
					{
						r.wait();//线程等待，进入线程池
					}
				catch(Exception e)
					{
						System.out.println("出错啦！");
					}
				System.out.println(r.name+" "+r.sex);
				r.flag=false;	//唤醒等待机制
				r.notify();
			}
		}
		
	}
}
public class InputOutDemo 
{
	public static void main(String[] args)
	{
		
		Res r=new Res();	//创建一个Res对象
		
		Input in=new Input(r);	//创建一个Input的对象
		Output out=new Output(r);	//创建一个Output的对象
		
		Thread t1=new Thread(in);
		Thread t2=new Thread(out);
		
		t1.start();
		t2.start();
	}
}
```
#### B、停止线程
* 1、定义循环结束标记  
> ①：因为线程运行代码一般都是循环的，只要控制了循环即可  
* 2、使用interrupt（中断）方法  
> ①：该犯法是结束线程的冻结状态，使线程回到运行状态中来  
注意：stop方法已经过时  
* 3、如何停止线程？  
> 只有一种方法：run方法结束（开启多线程运行，运行代码通常是循环结构，只要控制住循环，就可以让run方法结束，也就是线程结束  
* 4、特殊情况：  
> 当线程处于冻结状态，就不会读取标记，那么线程就不会结束  
* 5、解决方法：  
> 当没有指定的方式让冻结的线程恢复到运行状态时，这时需要对冻结进行清除，强制让线程恢复到运行状态中来，这样子可以操作标记让线程结束  
代码：
```
package com.demo1;

class ttopThread implements Runnable
{
	private boolean flag=true;
	public synchronized void run()
	{
		while(flag)
		{
			try
			{
				wait();
			}
			catch(InterruptedException e)
			{
				System.out.println(Thread.currentThread().getName()+"....Exception");
				flag=false;
			}
			System.out.println(Thread.currentThread().getName()+"....ran");
		}
	 }
}
public class StopThread 
{
	public static void main(String[] args)
	{
		ttopThread st=new ttopThread();
		Thread t1=new Thread(st);
		Thread t2=new Thread(st);
		
		t1.start();
		t2.start();
		
		int num=0;
		 while(true)
		 {
			 if(num++==60)
			 {
				 t1.interrupt();
				 t2.interrupt();
				 break;
			 }
			 System.out.println(Thread.currentThread().getName()+"...."+num);
		 }
		 System.out.println("over");
	}
}
```
#### C、守护线程（setDaemon）：
* 1、格式：public final void setDaemon(boolean on)
* 2、作用：将该线程标记为守护线程或用户线程，当正在运行的线程都是守护线程时，Java虚拟机退出
* 3、用法：该方法首先调用该线程的checkAccess方法，且不带任何参数，这可能抛出SecurityException（在当前线程中）
*** 
### 二、String类
* A、字符串是一个特殊的对象
* B、字符串一旦初始化就不可以被改变  
代码：
```
class StringDemo
{
	public static void main(String[] args)
	{
		String s1="abc";	//s1是一个类类型的变量，"abc"是一个对象
		String s2=new String("abc");
		System.out.println(s1.equals(s2));  //输出结果为：true
	}
}
```
* C、s1和s2有什么区别
> 1、s1内存中有一个对象  
2、时内存中有两个对象

*D、String类适用于描述字符串事物，它提供多个方法对字符串进行操作
***
