## Day10
### 一、多线程
* a、进程
> 1、进程定义：是一个正在执行的程序  
2、每一个进程执行都有一个执行顺序，该顺序是一个执行路径，或者叫一个控制单元
* b、线程
> 1、定义：进程中的一个独立的控制单元，线程在控制着进程的执行（一个进程中至少有一个线程）  
2、Java VM 启动的时候会有一个进程Java.exe，该进程中至少一个线程负责Java程序的执行，而且这个线程运行的代码存在于main方法中，该线程称为主线程  
3、扩展：其实更细节说明JVM，JVM启动不止一个线程，还有负责垃圾回收机制的线程
* c、多线程存在的意义：使多个程序同时进行
* d、如何自定义一个线程：  
步骤：
> 1、定义类继承Thread类  
2、复写类Thread类中的run方法  
3、调用线程的start方法（该方法有两个作用：启动线程、调用run方法）  
代码：
```
package Package3;

//继承Thread类
class Demo extends Thread
{
	public void run()
	{
		for(int x=0;x<60;x++)
		{
			System.out.println("demo run--"+x);
		}
	}
}
public class dd 
{
	public static void main(String[] args)
	{
		Demo d=new Demo();
		d.start();  //开启线程并且执行该线程的run方法
		for(int i=0;i<60;i++)
		{
			System.out.println("Hello World!=="+i);
		}
	}
}
```
* e、线程中发现每一次运行结果都不同，因为多个线程都获取CPU的执行权。CPU执行谁，谁就运行；明确一点的是，在某个时刻，只能有一个程序在运行（可以把多线程的运行行为在互相抢夺CPU的执行权）
* f、为什么要覆盖run方法：将自定义的代码存储在run方法中，让线程执行代码
> 1、Thread类用于描述线程，该类就定义了一个功能，用于存储线程要运行的代码，该存储功能就是run方法
* g、线程有自己的默认名称：Thread-编号 该编号从0开始
* h、几种常用的线程方法：
> 1、static Thread currentThread(); 获取当前线程对象  
2、getName(); 获取线程名称  
3、setName或者构造函数可以设置线程名称
***
### 二、实现Runnable接口
* a、子类覆盖接口中的run方法	
> 1、通过Thread类创建线程，并将实现了Runnable接口的子类对象作为参数传递给Thread类的构造函数  
2、Thread类对象调用start方法开启线程
* b、Thread类中run()和start()方法区别：
> 1、run()方法：在本线程内调用该Runnable对象的run()方法，可以重复多次调用  
2、start()方法：启动一个线程，调用该Runnable对象的run()方法，不能多次启动一个线程
* c、两种进程创建方式比较
* 1、第一种方式：
> ①优点：创建方式比较简单  
②缺点：不能再继承其他类（Java但继承）、同份资源不共享
```
class A extends Thread
{
}
```
* 2、第二种方式：
> ①优点：多个线程共享一个目标资源，适合多线程处理同一份资源、该类还可以继承其他类，也可以实现其他接口
```
Class A implements Runnable
{
}
```
***
### 三、线程的生命周期
* a、Thread类内部有个public的枚举Thread.state，里边将线程的状态分为：
> 1、new ：新建状态，至今尚未启动的线程处于这种状态  
2、Runnable：运行状态，正在Java虚拟机中执行的线程处于这种状态  
3、Blocked：阻塞状态，受阻塞并等待某个监视器的线程处于这种状态  
4、Waiting：冻结状态，无限期地等待另一个线程来执行某一特定操作的线程处于这种状态  
5、Time_Waiting：等待状态，等待另一个线程来执行取决于指定等待时间的操作的线程处于这种状态  6、Terminated：已退出的线程处于这种状态
***