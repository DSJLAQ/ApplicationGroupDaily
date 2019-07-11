## Day4
### 1、选择结构
#### ①Switch语句特点：
a、switch语句选择类型只有四种：  
byte、short、int、char  
b、case 之间与default没有顺序，先执行第一个case，完全没有匹配的case则执行default  
c、结束switch语句的两种情况：①遇到break ②执行到switch语句结束
d、如果匹配的case或者default没有对应的break，那么程序会继续向下执行，运行可以执行的语句，直到遇到break或者switch结尾结束  
e、if和switch的使用：  
①语句很像，如果判断的具体数值不多，而是符合byte、short int char这四种类型（switch效率更高）  
②对区间判断，对结果为boolean类型进行判断，使用if范围更加广  
### 2、循环结构
a、while：先判断条件，只有条件满足才执行循环体  
b、do while :先执行循环体，再判断条件，条件满足，再继续执行循环体，至少执行循环体一次  
c、变量有自己的作用域，对于for来讲，如果用于控制循环的增量定义在for语句中，那么该变量只在for语句内有效。for语句执行完毕，该变量在内存中被释放  
d、什么时候运用循环结构：当要对某些语句执行很多次时，就使用循环结构
