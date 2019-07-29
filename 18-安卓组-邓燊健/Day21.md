[toc]
## Day21
### 一、装饰设计模式
#### A、定义  
当想要对已有的对象进行功能增强时，可以定义类，将已有对象传入，基于已有功能，并提供加强功能，那么自定义的该类称为装饰类
* 1、装饰类和继承的关系
> 装饰模式比继承要灵活，避免了继承体系臃肿，而且降低了类与类之间的关系
* 2、装饰类的特点
> 装饰类因为增强已有对象，具备的功能和已有的是相同的，只不过提供了更强功能，所以装饰类和被装饰类通常是都属于一个体系中的
* 代码例子：
```
package package3;

//装饰设计模式

class Person
{
	public void chifan()
	{
		System.out.println("吃饭");
	}
}

//定义装饰类
class SuperPerson
{
	private Person p;
	SuperPerson(Person p)
	{
		this.p=p;
	}
	public void Superchifan()
	{
		System.out.println("开胃酒");
		p.chifan();
		System.out.println("甜品");
		System.out.println("来一根");
	}
}

public class ZhuangshiClass
{
	public static void main(String[] args)
	{
		Person p=new Person();
		
		SuperPerson sp=new SuperPerson(p);
		
		sp.Superchifan();
	}
}
```
运行结果：  
![image](https://note.youdao.com/yws/public/resource/e36083821fb446484249f2a3cecc2908/xmlnote/FAF37D8088C648A6AADD14C920B32F6D/1297)
***
### 二、Reader子类对象
#### A、LineNumberReader子类对象
* 代码例子：
```
package package3;
//LineNumberReader 测试
import java.io.*;

public class LineNumberReaderTest 
{
	public static void main(String[] args) throws IOException
	{
		//创建一个读取流对象
		FileReader fr=new FileReader("G:\\Test2.java");
		
		//创建一个LineNumberReader对象，以fr为构造函数的实参
		LineNumberReader lnr=new LineNumberReader(fr);
		
		String Line=null;
		
		lnr.setLineNumber(20);
		//setLineNumber()方法设置输出的行号，从21行开始
		while((Line=lnr.readLine())!=null)
		{
			System.out.println(lnr.getLineNumber()+"："+Line);
			//getLineNumber()方法用来获取行号
		}
		
	}
lnr.close();
}
```
***
### 三、字节流
#### A、字节流基类  
OutputStream、InputStream
#### B、字节流子类
* 1、FileOutputStream、FileInputStream
* 代码例子：
```
package package3;

//字节流子类对象测试
import java.io.*;
public class StreamTest 
{
	public static void main(String[] args) throws IOException
	{
		Writer();
		Reader();
	}
	
	public static void Reader() throws IOException
	{
		//创建字节流对象FileInputStream读取数据
		FileInputStream fis=new FileInputStream("G:\\demo1.txt");
		
		//available文件字节的长度
		byte[] buf=new byte[fis.available()];
		//定义一个刚好的缓冲区，不用再进行循环
		
		fis.read(buf);
		
		System.out.println(new String(buf));
		
		fis.close();
		
		
	}
	public static void Writer() throws IOException
	{
		//创建字节流对象FileOutputStream写入数据
		FileOutputStream fos=new FileOutputStream("G:\\demo1.txt");
		
		//写入数据格式
		fos.write("abcde\r\nfgh".getBytes());
		
		fos.close();
	
	}
}
```
* 3、字节流中的缓冲区  
BufferedOutputStream、BufferedInputSteam
***
