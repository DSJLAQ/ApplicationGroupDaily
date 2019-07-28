[toc]
## Day20
### 一、字符流
#### A、两个基类  
Writer、Reader
#### B、字符流Writer对象创建操作
* 1、创建一个FileWriter对象，该对象一被初始化就必须要明确被操作的文件  
（而且该文件被创建到指定目录下，如果该目录下已有同名文件，则文件会被覆盖）
* 代码：
```
FileWriter fw=new FileWriter(“C://example.txt”)；//明确被操作的文件
```

* 2、调用write方法，将字符串写入到流中
* 代码：
```
fw.write(“abcde”);
```
* 3、调用flush方法，刷新流对象中缓冲中的资源
* 代码：
```
fw.flush();
```
* 4、关闭流资源，但是关闭之前会刷新一次内部的缓冲中的数据
* 代码：
```
fw.close();
```

* 代码例子：
```
package package2;

import java.io.*;

public class IOTest 
{
	public static void main(String[] args) throws IOException
	{
		//1、创建一个FileWriter对象，该对象一被初始化就必须明确被操作的文件
		FileWriter fw=new FileWriter("G:\\demo.txt");
		
		//2、调用write方法，将字符串写到流中
		fw.write("abced");
		//3、刷新流对象中的缓冲中的数据
		fw.flush();
		//4、关闭流资源前会刷新数据
		fw.close();
	}
}
```
#### C、IO异常的处理方式
* 代码例子：
```
package package2;

import java.io.*;

public class IOTest 
{
	public static void main(String[] args) throws IOException
	{
		//使得代码块之间可以进行访问
		FileWriter fw=null;
		try
		{
			//1、创建对象
			fw=new FileWriter("G:\\demo.txt");
			
			//2、写进数据
			fw.write("Fighting!");
			
			//3、刷新数据
			fw.flush();
		}
		catch(IOException e)
		{
			System.out.println("Catch:"+e.toString());
		}
		//finally代码块中执行一定执行的代码
		finally
		{
			try
			{
				//关闭IO流
				if(fw!=null)
					fw.close();
				
			}
			catch(IOException e)
			{
				System.out.println("Catch:"+e.toString());
			}
		}
	}
}
```
#### D、在文档中进行续写
* 1、代码：
```
FileWrite fw=new FileWriter("G:\\demo.txt",true);
```
#### E、字符流对象Reader创建操作
* 1、创建一个文件读取流对象的，并且要指定名称的文件相关联  
* （必须保证该文件是已经存在的，如果不存在的话，会发生异常FileNotFoundException）
* 代码：
```
FileReader fr=new FileReader("G:\\demo.txt");
```
* 2、调用读取流对象的read方法  
> ①第一种代码：对一个字符进行读取
```
int ch;
		while((ch=fr.read())!=-1)
		{
			System.out.println((char)ch);
		}
```
> ②第二种代码：对数组字符进行读取
```
FileReader fr=new FileReader("G:\\demo.txt");
		
		char[] buf=new char[1024];
		
		int num=0;
		while((num=fr.read(buf))!=-1)
		{
			System.out.println(new String(buf,0,num));
		}
```
* 3、将C盘一个文本复制到D盘
> ①原理：将C盘下的文件存储到D盘的文本  
a、在D盘创建一个文件，用于存储C盘文本中的数据  
b、定义读取和C盘文件关联  
c、通过不断的读写完成数据存储  
d、关闭资源
* 代码例子：
```
package package2;

import java.io.*;

public class IOTest 
{
	public static void main(String[] args) throws IOException
	{
		FileWriter fw=new FileWriter("G:\\aaa.java");
		
		FileReader fr=new FileReader("F:\\Test1.java");
		
		int ch=0;
		
		while((ch=fr.read())!=-1)
		{
			fw.write(ch);
		}
		
		fw.close();
		fr.close();
	}
}
```
#### F、字符流的缓冲区
* 1、作用：缓冲区的出现提高了对数据的读写效率
* 2、对应类
> ①BufferedWrite：将文本写入字符输出流，缓冲各个字符，从而提供单个字符、数组和字符串的高效写入  
②BufferedReader：从字符输入流中读取文本，缓冲各个字符，从而实现字符，数组和行的高效读取
* 3、缓冲区要结合流才可以使用
* 4、在流的基础上对流的功能进行增强
* ①写入字符缓冲代码例子：
```
package package2;

import java.io.*;

public class IOTest 
{
	public static void main(String[] args) throws IOException
	{
		//创建一个字符写入流对象
		FileWriter fw=new FileWriter("G:\\aaa.java");
		
		//提高字符写入流效率，加入缓冲技术
		//只需要将被提高效率的流对象作为参数传递给缓冲区的构造函数即可
		BufferedWriter bufW=new BufferedWriter(fw);
		
		for(int x=1;x<5;x++)
		{
			bufW.write("abcde"+x);
			//newLine()是缓冲区特有的换行方式
			bufW.newLine();
			bufW.flush();
		}
		//关闭缓冲区也等于关闭缓冲区中的流对象
		bufW.close();
	}
}
```
* ②读取字符代码缓冲例子：
```
package package2;

import java.io.*;

public class IOTest 
{
	public static void main(String[] args) throws IOException
	{
		//创建一个字符读取流对象
		FileReader fr=new FileReader("G:\\aaa.java");
		
		//提高字符读取流效率，加入缓冲技术
		//只需要将被提高效率的流对象作为参数传递给缓冲区的构造函数即可
		BufferedReader bufR=new BufferedReader(fr);
		
		String Line=null;
		while((Line=bufR.readLine())!=null)
		{
			System.out.println(Line);
		}
		
		//关闭缓冲区也等于关闭缓冲区中的流对象
		bufR.close();
	}
}
```
***
