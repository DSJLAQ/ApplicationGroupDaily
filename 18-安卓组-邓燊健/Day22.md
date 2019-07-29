[toc]
## Day22
### 一、GUI（图形用户界面）
#### A、定义
> Graphical User Interface（图形用户接口），用图形的方式，来显示计算机操作的界面，这样更方便直观
#### B、GUI对象
> 存在java.Awt和javax.Swing两个包中
* 1、Awt与Swing
> ①java.Awt：Abstract Window ToolKit（抽象窗口工具包），需要调用本地系统方法实现功能，属重量级控件  
②javax.Swing：在AWT的基础上，建立的一套图形界面系统，其中提供了更多的组件，而且完全有Java实现，增强了移植性，属轻量级控件

#### C、GUI中继承关系图
![image](https://note.youdao.com/yws/public/resource/e36083821fb446484249f2a3cecc2908/xmlnote/0CE8821A4E3A4DFE8E555CF70C9F6CBC/1299)
* 1、Container：一个容器，是一个特殊的组件，该组件中可以通过add方法添加其他组件进来
#### D、布局管理器
* 1、布局：容器中的组件排放方式
* 2、常见的布局管理器
> ①FlowLayout（流式布局管理器）  
特点：  
a、从左到右的顺序排列  
b、Panel默认的布局管理器  
②BorderLayout（边界布局管理器）  
特点：  
a、东、南、西、北、中  
b、Frame默认的布局管理器  
③GridLayout（网格布局管理器）  
特点：  
a、规则的矩阵  
④CardLayout（卡片布局管理器）  
特点：  
选项卡  
⑤、GridBagLayout（网络包布局管理器）  
特点：非规则的矩阵
#### E、建立一个简单的窗体
* 1、Container常用子类：Window、Panel（面板，不能单独存在）
* 2、Window常用子类：Frame、Dialog
* 3、简单的窗体创建过程
```
        Frame f=new Frame("my window");
		f.setLayout(new FlowLayout());
		f.setSize(500,400);//设置窗体大小
		f.setLocation(300,200);//设置窗体出现在屏幕的位置
		f.setVisible(true);//设置窗体显示
```

#### F、事件监听机制
* 1、事件源（组件）  
Awt包或者Swing包中的那些图形界面组件
* 2、事件（Event）  
每一个事件源都有自己特有的对应事件和共性事件
* 3、监听器（Listener）  
> 将可以触发某一个事件的动作（不只是一个动作）都已经封装到了监听器中
* 4、事件处理（引发事件后处理方式）
事件监听机制流程图：  
![image](https://note.youdao.com/yws/public/resource/e36083821fb446484249f2a3cecc2908/xmlnote/B8921D9088EC42FF82761C2927915B64/1301)
* 代码例子：
```
package package3;

import java.awt.*;
import java.awt.event.*;

public class FrameTest
{
	//定义该图形中所需的组件的引用
	private Frame f;
	private Button but;
	
	FrameTest()
	{
		init();
	}
	
	public void init()
	{
		f=new Frame("my frame");
		
		//对frame进行基本的设置
		f.setBounds(300,100,600,500);
		f.setLayout(new FlowLayout());
		
		but=new Button("my button");
		
		//将组件添加到frame中
		f.add(but);
		//加载一下窗体上事件
		myEvent();
		
		//显示窗体
		f.setVisible(true);
	}
	
	private void myEvent()
	{
		f.addWindowListener(new WindowAdapter()
		{
			public void windowclosing(WindowEvent e)
			{
				System.exit(0);
			}
		});
		//让按钮具备退出程序的功能
		but.addActionListener(new ActionListener()
				{
					public void actionPerformed(ActionEvent e)
					{
						System.out.println("退出，按钮干的");
						System.exit(0);
					}
				});
	}
	public static void main(String[] args)
	{
		new FrameTest();
	}
	
}
```
*** 