



# 多维数组

```
注意 int[] x,y[]; //x为一维数组 y为二维数组
```



## 一、二维数组的使用



### 1.二维数组的和

```java
*1.初始化

*2.记录总和

*3.两层for循环嵌套*/
	for(int i=0;i<arr.length;i++){//行数
		for(int j=0;j<arr[i].length;j++){//列数
		sum+=arr[i][j];
		}	
	}
```

### 2.使用二维数组打印一个10行杨辉三角

![image-20211128143030254](C:\Users\Lenovo\AppData\Roaming\Typora\typora-user-images\image-20211128143030254.png)

```java
public class YangHuiTest{
	public static void main(String[] args){
	//1.声明并初始化数组
	int[][] yangHui=new int[10][];
	//2.赋值
	for(int i=0;i<yangHui.length;i++){
		yangHui[i]=new int[i+1];
		//2.1给首末元素赋值
		yangHui[i][0]=1;
		yangHui[i][i]=1;
		//2.2给每行的非首末元素赋值
		if(i>1){
			for(int j=1;j<yangHui[i].length-1;j++){
				yangHui[i][j]=yangHui[i-1][j-1]+yangHui[i-1][j];
			}
		}
		
	}
	//3.遍历
	
	}

}
```

## 二、数组中涉及的常见算法

### 	1.数组元素的赋值(杨辉三角、回形数等) 

### 	2.求数值型数组中元素的最大值、最小值、平均数、总和等

### 	3.数组的复制、反转、查找(线性查找、二分法查找)

注：字符串反转 reverse()方法

```java
public static void main(String[] args){
	String[] arr=new String[]{"JJ","DD","MM","BB","GG","AA"};
	//数组的复制(区别于数组变量的赋值:arr1=arr)
	String[] arr1=new String[arr.length];
	for(int i=0;i<arr1.length;i++){
		arr1[i]=arr[i];
	}
	
	//数组的反转
	//方法一
	for(int i=0;i<arr1.length/2;i++){
		String temp=arr[i];
		arr[i]=arr[arr.length-i-1];
		arr[arr.length-i-1]=temp;
	}

	//方法二
	for(int i=0,J=arr.length-1;i<j;i++;j--){
		String temp=arr[i];
		arr[i]=arr[j];
		arr[j]=temp;
	}
	//遍历
	
	//线性查找:
	String dest="BB";
	boolean isFlag=true；
	for(int i=0;i<arr.length;i++){
		if(dest.equals(arr[i])){
			System.out.println("找到了指定的元素，位置为："+i);
			isFlag=false;
			break;
		}
	}
	if(isFlag)
	System.out.println("很遗憾没有找到");
	//二分查找
	//前提，所要查找的数组必须有序
	int[] arr2=new int[]{-98,-34,45,86,79,48,11,55,66,88};
	int dest1=-34;
	int head=0;//初始首索引
	int end=arr2.length-1;//初始末索引
	boolean isFlag1 =true;
	while(head<=end){
		int middle=(head+end)/2;
		if(dest1==arr2[middle]){
			System.out.println("找到了指定的元素，位置为："+middle);
			isFlag1=false;
			break;
		}else if(arr2[middle]>dest1){
			end=middle-1;
		}else{//arr2[middle]<dest1
			head=middle+1;
		}
	}
	if(isFlag1){
		System.out.println("很遗憾，没有找到");
	}
	
}
```



### 	4.数组元素的排序算法

#### 十大内部排序算法

##### （1）选择排序

###### 		直接选择排序

###### 		堆排序

##### （2）交换排序

###### 		冒泡排序

```java
public static void main(String[] args){
	int[] arr=new int[]{43,32,76,-98,0,64,33,-21,32,99};
	
	//冒泡排序
	for(int i=0;i<arr.length-1;i++){
		for(int j=0;j<arr.length-1-i;j++){
			if(arr][j]>arr[j+1]){
				int temp=arr[j];
				arr[j]=arr[j+1];
                arr[j+1]=temp;
			}
		}
	}

}
```

###### 		快速排序

```java
/**
 * 快速排序
 * 通过一趟排序将待排序记录分割成独立的两部分，其中一部分记录的关键字均比另一部分关键字小，
 * 则分别对这两部分继续进行排序，直到整个序列有序。
 */
public class QuickSort {
	private static void swap(int[] data, int i, int j) {
		int temp = data[i];
		data[i] = data[j];
		data[j] = temp;
	}

	private static void subSort(int[] data, int start, int end) {
		if (start < end) {
			int base = data[start];
			int low = start;
			int high = end + 1;
			while (true) {
				while (low < end && data[++low] - base <= 0)
					;
				while (high > start && data[--high] - base >= 0)
					;
				if (low < high) {
					swap(data, low, high);
				} else {
					break;
				}
			}
			swap(data, start, high);
			
			subSort(data, start, high - 1);//递归调用
			subSort(data, high + 1, end);
		}
	}
	public static void quickSort(int[] data){
		subSort(data,0,data.length-1);
	}
	
	
	public static void main(String[] args) {
		int[] data = { 9, -16, 30, 23, -30, -49, 25, 21, 30 };
		System.out.println("排序之前：\n" + java.util.Arrays.toString(data));
		quickSort(data);
		System.out.println("排序之后：\n" + java.util.Arrays.toString(data));
	}
}

```



##### （3）插入排序

###### 		直接插入排序、折半插入排序、Shell排序

##### （4）归并排序

##### （5）桶式排序

##### （6）基数排序

#### 各种内部排序方法性能比较 

![image-20211128161623666](C:\Users\Lenovo\AppData\Roaming\Typora\typora-user-images\image-20211128161623666.png)



##### (1)从平均时间而言

快速排序最佳。但在最坏情况下时间性能不如堆排序和归 并排序。

##### (2)从算法简单性看

由于直接选择排序、直接插入排序和冒泡排序的算法比较 简单，将其认为是简单算法。对于Shell排序、堆排序、快速排序和归并排序 算法，其算法比较复杂，认为是复杂排序。 

##### (3)从稳定性看

直接插入排序、冒泡排序和归并排序时稳定的；而直接选择排 序、快速排序、 Shell排序和堆排序是不稳定排序 

##### (4)从待排序的记录数n的大小看

n较小时，宜采用简单排序；而n较大时宜采 用改进排序。

## 三、Arrays工具类

java.util.Arrays类即为操作数组的工具类，包含了用来操作数组（比 如排序和搜索）的各种方法。

![image-20211128162139033](C:\Users\Lenovo\AppData\Roaming\Typora\typora-user-images\image-20211128162139033.png)



# 面向对象（上）

## 一、属性(成员变量)vs局部变量

### 1.相同点

#### 1.1定义变量的格式

数据类型   变量名 = 变量值

#### 1.2先声明,后使用

#### 1.3变量都有其对应的作用域

### 2.不同点

#### 2.1在类中声明的位置的不同

属性:直接定义在类的一对{得}内

局部变量:声明在方法内、方法形参、代码块内、构造器形参、构造器内部的变量

#### 2.2关于权限修饰符的不同

属性:可以在声明属性时，指明其权限,使用权限修饰符。

常用的权限修饰符: private、public、缺省、protected --->封目前,大家声明属性时,都使用缺省就可以了。

局部变量:不可以使用权限修饰符。

#### 2.3默认初始化值的情况

属性:类的属性，根据其类型，都有默认初始化值。

整型( byte、 short、int、 long) :,0 

浮点型(float. double) :,0.0

字符型(char) : (或'\u0000')布尔型( boolean) , false

引用数据类型(类、数组、接口)， null

**局部变量没有默认的初始化值。**

​	意味着，我们在调用局部变量之前，一定要显示赋值。

​	特别地：形参在调用时，我们赋值即可。

#### 2.4在内存中的加载位置

属性：加载到堆空间中（非static）

局部变量：加载到栈空间

## 二、匿名对象的使用

### 1.理解

我们创建的对象，没有显式的赋给一个变量名。即为匿名对象

### 2.特征

匿名对象只能调用一次。

### 3.使用

*new 类名称();*

## 三、方法的重载（overload) loading.. .

### 1.定义

在同一个类中，允许存在一个以上的同名方法，只要它们的参数个数或者参数类型不同即可。

“两同一不同":同一个类、相同方法名。

参数列表不同:参数个数不同，参数类型不同。

### 2.举例:

Arrays类中重载的sort() / binarySearch()

### 3.判断是否是重载:

跟方法的权限修饰符、返回值类型、形参变量名、方法体都没有关系!

### 4.在通过对象调用方法时，如何确定某一个指定的方法:

方法名- -->参数列表

## 四、封装性的体现，需要权限修饰符来配合

### 1.Java规定的4种权限

（从小到大排列): private、缺省、protected . public

![image-20211128170834020](C:\Users\Lenovo\AppData\Roaming\Typora\typora-user-images\image-20211128170834020.png)

### 2.4种权限可以用来修饰类及类的内部结构

属性、方法、构造器、内部类

### 3.具体的，4种权限都可以用来修饰类的内部结构:属性、方法、构造器、内部类

修饰类的话，只能使用:缺省、public

## 四、JavaBean

一种java语言写成的可重用组件

所谓JavaBean，是指符合如下标准的Java类:

> 类是公共的

> 有一个无参的公共的构造器

> 有属性，且有对应的get、 set方法

用户可以使用JavaBean将功能、处理、值、数据库访问和其他任何可以用Java代码创造的对象进行打包，并且其他的开发者可以通过内部的JSP页面、Servlet、其他JavaBean、applet程序或者应用来使用这些对象I用户可以认为JavaBean提供了一种随时随地的复制和粘贴的功能，而不用关心任何改变。

# 面向对象（中）

![image-20211128180300567](C:\Users\Lenovo\AppData\Roaming\Typora\typora-user-images\image-20211128180300567.png)

## —、继承性的好处:

（1）减少了代码的冗余，提高了代码的复用性

（2）便于功能的扩展

（3）为之后多态性的使用，提供了前提

## 二、继承性的格式:

​	class A extends B{}

​	A:子类、派生类、subclass

​	B:父类、超类、基类、superclass

## 三、子类继承父类以后有哪些不同

3.1体现：一旦子类A继承父类B以后，子类A中就获取了父类B中声明的所有的属性和方法。

特别的，父类中声明为private重属性或方法，子类继承父类以后，仍然认为获取了父类中私有的结构。只有因为封装性的影响,使得子类不能直接调用父类的结构而已。

3.2子类继承父类以后，还可以声明自己特有的属性或方法：实现功能的拓展。

子类和父类的关系，不同于子集和集合的关系。

extends:延展、扩展

## 四、Java中继承性的说明

1.一个类可以被多个子类继承。

2.Java中类的单继承性:一个类只能有一个父类

3.子父类是相对的概念。

4.子类直接继承的父类，称为:直接父类。间接继承的父类称为:间接父类

5.子类继承父类以后，就获取了直接父类以及所间接父类中声明的属性和方法

## 五、java.lang.object类的理解

1.如果我们没显式的声明一个类的父类的话，则此类继承于java.lang.object类
2.所的java类（除java.lang.object类之外都直接或间接的继承于java.lang.object类3．意味着，所的java类具java.lang.object类声明的功能。

## 六、方法重写

### 1.重写

子类继承父类以后，可以对父类中同名同参数的方法，进行覆盖操作

### 2.应用

重写以后，当创建子类对象以后，通过子类对象调用子父类中的同名同参数的方法时，实际执行的是子类重写父类的方法

### 3．重写的规定

```java
方法的声明:权限修饰符 返回值类型 方法名(形参列表) throws 异常的类型{
			//方法体
			}
```

约定俗称:子类中的叫重写的方法，父类中的叫被重写的方法。

（1）子类重写的方法的方法名和形参列表与父类被重写的方法的方法名和形参列表相同。

（2）子类重写的方法的权限修饰符不小于父类被重写的方法的权限修饰符。

> **特殊情况:子类不能重写父类中声明为private权限的方法**

（3）返回值类型:

> 父类被重写的方法的返回值类型是void，则子类重写的方法的返回值类型只能是void

> 父类被重写的方法的返回值类型是A类型（如object），则子类重写的方法的返回值类型可以是A类或A类的子类

> 父类被重写的方法的返回值类型是基本数据类型(比如:double)，则子类重写的方法的返回值类型必须是相同的基本数据类型（必须也是double）

（4）子类重写的方法抛出的异常类型不大于父类被重写的方法抛出的异常类型。

（5）子类和父类中的同名同参数的方法要么都声明为非static的（考虑重写），要么都声明为static的（不是重写）

## 七、super关键字的使用

### 1.理解

super可理解为父类的

### 2.调用

可用来调用属性、方法、构造器

### 3.super的使用（属性、方法）

3.1我们可以在子类的方法或构造器中。通过使用"super.属性“或"super.方法"的方式，显式的调用父类中声明的属性或方法。但是，通常情况下，我们习惯省略"super."

3.2特殊情况:当子类和父类中定义了同名的属性时，我们要想在子类中调用父类中声明的属性，则必须显式的使用"super.属性"的方式，表明调用的是父类中声明的属性。

3.3 特殊情况:当子类重写了父类中的方法以后，我们想在子类的方法中调用父类中被重写的方法时，则必须显式的使用"super.方法"的方式,表明调用的是父类中被重写的方法。

### 4.super调用构造器

4.1我们可以在子类的构造器中显式的使用"super(形参列表)"的方式，调用父类中声明的指定的构造器

4.2 "super(形参列表)"的使用，必须声明在子类构造器的首行!

4.3我们在类的构造器中，针对于"this(形参列表)"或super(形参列表)"只能二选一，不能同时出现

4.4在构造器的首行，没有显式的声明"this(形参列表)"或"super(形参列表)"，则默认调用的是父类中空参的构造器，super（）**所以只要写构造器就要写空参构造器**

4.5在类的多个构造器中，至少有一个类的构造器中使用了"super(形参列表)"，调用父类中的构造器

## 八、子类对象实例化的全过程

1.从结果上来看：（继承性）

​	子类继承父类以后，就获取了父类中声明的属性或方法。

​	创建子类的对象，在堆空间中，就会加载所有父类中声明的属性。

2．从过程上来看

当我们通过子类的构造器创建子类对象时，我们一定会直接或间接的调用其父类的构造器，进而调用父类的父类的构造器，直到调用了java.lang.object类中空参的构造器为止。正因为加载过所有的父类的结构，所以才可以看到内存中有父类中的结构，子类对象才可以考虑进行调用。

**明确：虽然创建子类对象时，调用了父类的构造器，但是自始至终就创建过一个对象，即为new的子类对象。**

## 九、多态性

### 1.理解多态性

可以理解为一个事物的多种形态。

### 2.何为多态性

对象的多态性:父类的引用指向子类的对象（或子类的对象赋给父类的引用)

### 3.多态的使用

虚拟方法调用：

有了对象的多态性以后，我们在编译期，只能调用父类中声明的方法，但在运行期，我们实际执行的是子类重写父类的方法。总结:编译，看左边;运行，看右边。

### 4.多态性的使用前提

4.1类的继承关系

4.2方法的重写

### 5.对象的多态性

只适用于方法，不适用于属性（编译和运行都看左边）

### 6.向下转型

有了对象的多态性以后，内存中实际上是加载了子类特有的属性和方法的，但是由于变量声明为父类类型，导致编译时，只能调用父类中声明的属性和方法。子类特有的属性和方法不能调用。

```java
//如何才能调用子类特有的属性和方法？
//向下转型，使用强制类型转换符
Penson p2=new Man();//new子类
Man m1=(Man)p2;
//使用强制转换时，可能出现ClassCastException的异常
Woman w1=(Woman)p2;
w1.goShopping();
/*
 *
 *  引出instanceof关键字的使用
 *	a instanceof A:判断对象a是否是类A的实例。
 *	如果是，返回true；如果不是，返回false
 *	使用情境，为了避免在向下转型时出现ClassCastException  的异常，我们在向下转型之前，先进行instanceof的判断，一旦返回true，就进行向下转型，如果返回false，不进行向下转型。
 *	如果a instanceof A返回true，a instanceof B返回true，其中，类B是类A的父类。
 *
 *
 */
if(p2 instanceof Woman){
    Woman w1=(Woman)p2;
    w1.goShopping();
    System.out.println("*******Woman******"); 
}
```

## 十、==和equals()的使用

### ==：运算符

1.可以使用在基本数据类型变量和引用数据类型变量中

2.如果比较的是基本数据类型变量：比较两个变量保存的数据是否相等。(不一定类型要相同)

​	如果比较的是引用数据类型变量：比较两个对象的地址值是否相	同，即两个引用是否指向同一个对象实体

补充: == 符号使用时，须保证符号左右两边的变量类型一致。

```java
int i=10;
int j=10;
double d=10.0;
System.out.println(i==j);//true
System.out.println(i==d);//true

char c=10;
System.out.println(i==c);//true
char c1 = 'A';
char c2 = 65;
System.out.print1n(c1 == c2);/ /true
Customer cust1 = new customer( "Tom",21);
Customer cust2 = new customer("Tom,21);
System.out.println(cust1==cust2); /false
                              
String str1=new String("atguigu");
String str2=new String("atguigu");
System.out.println("---------");
System.out.println("str1.equals(str2)");//true            
```

### equals()方法的使用:

1.是一个方法，而非运算符

2.只能适用于引用数据类型

3.Object类中equals()的定义:

```java
public boolean equals(object obj) {

​	return (this ==obi);

}
```

说明:Object类中定义的equals()和==的作用是相同的：比较两个对象的地址值是否相同.即两个引用是否指向同一个对象实体

4.像String、Date、File、包装类等都重写了Object类中的equals（）方法。重写以后，比较的不是两个引用的地址是否相同，而是比较两个对象的“实体内容”是否相同。

5.通常情况下，我们自定义的类如果使用equals()的话，也通常是比较两个对象的"实体内容"是否相同。那么,我们就需要对Object类中的equals()进行重写。

重写的原则：比较两个对象的实体内容是否相同。

![image-20211207220223453](C:\Users\Lenovo\AppData\Roaming\Typora\typora-user-images\image-20211207220223453.png)

```java
public boolean equals(Object obj){
    if(this == obj){
        return true;
    }
    if(obj instanceof Order){
        Order order=(Order)obj;
        return this.orderId==order.oderId&&this.orderName.equals(order.name);
    	}
    return false;
	}
}
```

## 十一、Object类中toString()的使用

1．当我们输出一个对象的引用时，实际上就是调用当前对象的toString()

2. object类中toString()的定义:

```java
public String toString(){

	return getclass().getName() + "@"+Integer.toHexString(hashCode());
}
```

3．像String、 Date、File、包装类等都重写了Object类中的toString()方法。

使得在调用对象的toString()时，返回"实体内容"信息

4.自定义类也可以重写toString()方法，当调用此方法时，返回对象的”实体内容“

## 十二、包装类(Wrapper)的使用

![image-20211210212157780](C:\Users\Lenovo\AppData\Roaming\Typora\typora-user-images\image-20211210212157780.png)

![image-20211210212501299](C:\Users\Lenovo\AppData\Roaming\Typora\typora-user-images\image-20211210212501299.png)

1.java提供了8种基本数据类型对应的包装类，使得基本数据类型的变量具有类的特征

2.掌握：基本数据类型、包装类、String三者之间的相互转换

```java
public class WrapperTest{
    //String类型--->基本数据类型、包装类:调用包装类的parseXxx(String s)
    public void test5(){
      	String str1="123";
        //错误的情况：
        //int num1=(int)str1;
        //Integer in1=(Integer)str1;
   		int num2=Integer.parseInt(str1);
        System.out.println(num2+1);
        String str2="true";
        boolean b1=Boolean.parseBoolean(str2);
        System.out.println(b1);
        
    }
    
    //基本数据类型、包装类--->String类型，调用String重载的valueOf(Xxx xxx)
    public void test4(){
    	int num1=10;
        //方式1：连接运算
        String str1=num1+" ";
        //方式2：调用String的valueOf(Xxx xxx)
        float f1=12.3f;
        String str2=String.valueOf(f1);
        Double d1=new Double(12.4);
        String str3=String.valueOf(d1);
        System.out.println(str2);
        System.out.println(str3);
        
    }
    
    
    
    //JDK5.0新特性：自动装箱与自动拆箱
    public void test3(){
        //自动装箱：基本数据类型--->包装类的对象
        int num2=10;
        Integer in1=num2;//自动装箱
        
        boolean b1=true;
        Boolean b2=b1;//自动装箱
        
        //自动拆箱：包装类--->基本数据类型
        System.out.print1n(in1.toString());
        int num3 = in1;//自动拆箱
    }
    
    
    //包装类--->基本数据类型:调用包装类Xxx的xxxValue()
    public void test2(){
        Integer in1=new Integer(12);
        int i1=in1.intValue();
        System.out.println(i1+1);
        Float f1=new Float(12.3);
        float f2=f1.floatValue();
        System.out.println(f2+1);
        
        
    }
    
	//基本数据类型--->包装类，调用包装类构造器
	public void test1(){
		int num1=10;
		//System.out.println(num1.toString());不能调用
		Integer in1=new Integer(num1);
		System.out.println(in1.toString());
        Order order=new Order();
        System.out.println(order.isMale);//false
        System.out.println(order.isFemale);//null
	}

}

class Order{
    boolean isMale;
    Boolean isFemale;
    
}
```

# 面向对象（下）

## 一、static关键字

### **1.static:静态的**

### **2.用来修饰**

属性、方法、代码块、内部类

### **3.使用static修饰3属性**

静态变量（或类变量)

#### 3.1属性

按是否使用static修饰，又分为:静态属性vs非静态属性(实例变量)

​	实例变量:我们创建了类的多个对象，每个对象都独立的拥有一套类中的非静态属性。当修改其中一个对象中的非静态属性时，不会导致其他对象中同样的属性值的修改。

​	静态变量﹔我们创建了类的多个对象，多个对象共享同一个静态变量。当通过某一个对象修改静态变量时，会导致其他对象调用此静态变量时，是修改过了的。

#### 3.2 static修饰属性的其他说明

​	1.静态变量随着类的加载而加载。可以通过"类．静态变量"的方式进行调用

​	2.静态变量的加载要早于对象的创建。

​	3.由于类只会加载一次，则静态变量在内存中也只会存在一份:存在方法区的静态域中。

 4. ​             类变量    实例变量

    类			yes			**no**

​		对象		yes			yes

#### 3.3 静态属性举例

System.out; Math.PI;

### 4.使用static修饰方法:静态方法

​	1.随着类的加载而加载，可以通过"类.静态方法"的方式进行调用

2. 静态方法		非静态方法
   类		yes					no
   对象	yes					yes
   静态方法中，只能调用静态的方法或属性

非静态方法中，既可以调用非静态的方法	或属性，也可以调用静态的方法或属性

### 5.static注意点

5.1 在静态的方法内,不能使用this关键字、super关键字
5.2关于静态属性和静态方法的使用，大家都从生命周斯的角度去理解。

### 6.声明为static

1.开发中,如何确定一个属性是否要声明为static？

>属性是可以被多个对象所共享的，不会随着对象的不同而不同的。

2.开发中，如何确定一个方法是否要声明为static的?

>操作静态属性的方法，通常设置为static的
>工具类中的方法，习惯上声明为static的。比如:Math、Arrays.collections

### 7.单例设计模式

![image-20211211141435047](C:\Users\Lenovo\AppData\Roaming\Typora\typora-user-images\image-20211211141435047.png)

```java
//饿汉式


public class SingletonTest{
	public static void main(String[] args){
		Bank bank1=Bank.getInstance();
        Bank bank2=Bank.getInstance();
        System.out,println(bank1==bank2);
	}

}

class Bank{
    
    //1.私有化类的构造器
    private Bank(){
        
    }
    
    //2.内部创建类的对象
    //4.要求此对象也必须声明为静态的
    private static Bank instance = new Bank();
    //3.提供公共的方法，返回类的对象
    public static Bank getInstance(){
        return instance;
    }
    
}


//懒汉式

public class SingletonTest2{
    public static void main(String[] args){
        Order order1=Order.getInstance();
        Order order2=Order.getInstance();
        System.out.println(order1==order2);
    }
    
}

class Order{
	//1.私有化类的构造器
    private Order(){
        
    }
    //2.声明当前类对象，没有初始化
    //4.此对象也必须声明为static的
    private static Order instance=null;
	
    //3.声明public、static的返回当前类对象的方法
    public static Order getInstance(){
        if(instance==null){
            instance =new Order();
        }

        return instance;
        
        
    }
}
```

单例设计模式:

1.所谓类的单例设计模式，就是采取一定的方法保证在整个的软件系统中，对某个类只能存在一个对象实例。

2.如何实现?

饿汉式Vs 懒汉式

3．区分饿汉式和懒汉式
饿汉式:
	坏处:对象加载时间过长。

​	好处:饿汉式是线程安全的

懒汉式:

​	好处:延迟对象的创建。

​	目前的写法坏处:线程不安全。--->到多线程内容时,再修改

4.应用场景

![image-20211211150505861](C:\Users\Lenovo\AppData\Roaming\Typora\typora-user-images\image-20211211150505861.png)

## 二、main()方法的使用说明

1. main()方法作为程序的入口

2. main()方法也是一个普通的静态方法

3. main()方法可以作为我们与控制台交互的方式。(之前:使用Scanner)

  

## 三、代码块

### 1.代码块的作用

用来初始化类、对象

### 2.代码块修饰

如果有修饰的话只能使用static

### 3.分类

静态代码块vs非静态代码块

### 4.静态代码块

>内部可以有瑜出语句
>
>随着类的加载而执行
>
>作用：初始化类的信息
>
>如果一个类中定义了多个静态代码块，则按照声明的顺序进行
>
>静态代码块的执行要优先于非静态代码块

### 5.非静态代码块

>内部可以有输出语句
>
>随着对象的创建而执行
>
>每创建一个对象，就执行一次非静态代码块
>
>作用:可以在创建对象时，对对象的属性等进行初始化
>
>如果一个类中定义了多个非静态代码块，则按照声明的先后顺序执行
>
>非静态代码块内可以调用静态的属性、静态的方法，或非静态的属性、非静态方法
>

对属性可以赋值的位置:

①默认初始化

②显式初始化/⑤在代码块中赋值

③构造器中初始化

④有了对象以后，可以通过"对象．属性"或"对象.方法"的方式，进行赋值

**执行的先后顺序：**① -②/⑤ -③-④

## 四、final关键字

final:最终的

### 1.final可以用来修饰的结构

类、方法、变量

### 2.final用来修饰一个类

此类不能被其他类所继承。比如:String类、System类、StringBuffer类

### 3.final用来修饰方法

表明此方法不可以被重写。比如:Object类中getClass();

### 4.final用来修饰变量

此时的"变量"就称为是一个常量

#### 	4.1 final修饰属性

可以考虑赋值的位置有;显式初始化、代码块中初始化、构造器中初始化

#### 	4.2 final修饰局部变量

尤其是使用final修饰形参时，表明此形参是一个常量。当我们调用此方法时，给常量形参赋一个实参。一旦以后，就只能在方法体内使用此形参，但不能进行重新赋值。

**static final 用来修饰属性:全局常量**

## 五、abstract关键字

### abstract:抽象的

1.abstract可以用来修饰的结构:类、方法

2.abstract修饰类:抽象类

>此类不能实例化
>
>抽象类中一定有构造器，便于子类实例化时调用（涉及:子类对象实例化的全过程)
>
>开发中，都会提供抽象类的子类，让子类对象实例化，完成相关的操作



3.abstract修饰方法:抽象方法

>抽象方法只有方法的声明，没有方法体
>
>包含抽象方法的类，一定是一个抽象类。反之，抽象类中可以没有抽象方法的
>
>若子类重写了父类中的所有的抽象方法后，此子类方可实例化
>
>若子类没有重写父类中的所有的抽象方法，则此子类也是一个抽象类，需要使用abstract修饰

![image-20211211215107459](C:\Users\Lenovo\AppData\Roaming\Typora\typora-user-images\image-20211211215107459.png)

![image-20211211215122691](C:\Users\Lenovo\AppData\Roaming\Typora\typora-user-images\image-20211211215122691.png)



### **abstract使用上的注意点**

1.abstract不能用来修饰:属性、构造器等结构

2.abstract不能用来修饰私有方法、静态方法、final的方法、final的类

```java
public class PersonTest{
    public static void main(String[] args){
		method(new student());//匿名对象
		Worker worker = new Worker();
		method1(worker);//非匿名的类非匿名的对象
		method1(new Worker());//非匿名的类匿名的对象
		//创建了一匿名的子类的对象，p
        Person p = new Person(){
		//重写了抽象方法
            @Override
			public void eat(){
            	System.out.println("吃东西");
        	}
			@Override
			public void breath(){
                System.out.println("呼吸");
        	}
        };
        method1(p);
	}
}
public static void method1(Person p){
    p.eat();
    p.breath();
}
```

![image-20211211224516209](C:\Users\Lenovo\AppData\Roaming\Typora\typora-user-images\image-20211211224516209.png)

## 六、接口

举例

![image-20211211230154424](C:\Users\Lenovo\AppData\Roaming\Typora\typora-user-images\image-20211211230154424.png)

1.接口

使用interface来定义

2.Java中,接口和类是并列的两个结构

3.如何定义接口，定义接口中的成员

​	3.1 JDK7及以前:只能定义全局常量和抽象方法

>全局常量:public static final的.但是书写时，可以省略不写>抽象方法:public abstract的
​	3.2. JDK8：除了定义全局常量和抽象方法之外，还可以定义静态方法、默认方法(略)

4.接口中不能定义构造器的！意味着接口不可以实例化

5.Java开发中，接口通过让类去实现(implements )的方式来使用。
如果实现类覆盖了接口中的所有抽象方法，则此实现类就可以实例化。

如果实现类没有覆盖接口中所有的抽象方法，则此实现类仍为一个抽象类

6.Java类可以实现多个接口--->弥补了Java单继承性的局限性
格式:class AA extends BB implements CC,DD, EE

7．接口与接口之间可以继承,而且可以多继承

*******************************
8.接口的具体使用，体现多态性
9.接口．实际上可以看做是—种规范

```java
Computer com=new Computer();
//1.创建了接口的非匿名实现类的非匿名对象
Flash flash=new Flash();
com.transferData(flash);
//2.创建了接口的非匿名实现类的匿名对象
com.transferData(new Printer());
//3.创建了接口的匿名实现类的非匿名对象
USB phone=new USB(){
    //重写方法
}
//4.创建了接口的匿名实现类的匿名对象
com.transferData(new USB()){
    //重写方法
}
```

使用

代理模式/工厂模式(略)

### JDK8中的新特性

```java
//知识点1：接口中定义的静态方法，只能通过接口来调用`
CompareA.method1();
//知识点2:通过实现类的对象，可以调用接口中的默认方法。
//如果实现类重写了接口中的默认方法，调用时，仍然调用的是重写以后的方法
s.method2();
//知识点3:如果子类(或实现类)继承的父类和实现的接口中声明了同名同参数的方法，
//那么子类在没有重写此方法的情况下，默认调用的是父类中的同名同参数的方法。-->类优先原则
//知识点4：如果实现类实现了多个接口，而这多个接口中定义了同名参数的默认方法，那么在实现类没有重写此方法的情况下，报错。
//---接口冲突   这就需要我们必须在实现类中重写
s.method3();
```

## 七、内部类

1.Java中允许将一个类A声明在另一个类B中，则类A就是内部类，类B称为外部类。
2.内部类的分类：成员内部类（静态、非静态）VS局部内部类(方法内、代码块内、构造器内）
3.成员内部类：
一方面，作为外部类的成员:

>调用外部类的结构
>
>可以被static修饰
>
>可以被4种不同的权限修饰

另一方面，作为一个类:

> 类内可以定义属性、方法、构造器等
>
> 可以被final修饰，表示此类不能被继承。言外之意，不使用final，就可以被继承
>
> 可以被abstract修饰

4.关注如下的3个问题

​	4.1 如何实例化成员内部类的对象

​	4.2如何在成员内部类中区分调用外部类的结构

​	4.3 开发中局部内部类的使用

```
//创建Dog实例(静态的成员内部类)
Person.Dog dog=new Person.Dog();
dog.show();
//创建Bird实例(非静态的成员内部类)
//Person.Bird bird=new Person.Bird();//错误的
Person p=new Person();
Person.Bird bird=p.new Bird();
bird.sing();
```

## 八、异常处理

![image-20211219223108473](C:\Users\Lenovo\AppData\Roaming\Typora\typora-user-images\image-20211219223108473.png)

### Error

Java虚拟机无法解决的严重问题。如:JVM系统内部错误、资源耗尽等严重情况。比如. StackOverflowError
一般不编写针对性的代码进行处理。

```java
public class ErrorTest{
	public static void main(String[] args){
		//1.栈溢出：java.lang.StackOverflowError
		main(args);
		//2.堆溢出：java.lang.OutOfMemoryError
        Integer[] arr=new Integer[1024*1024*1024];

	}
}
```

### 一、异常体系结构

#### java.lang.Throwable

##### java.lang.Error

##### 一般不编写针对性的代码进行处理。		

##### java.lang.Exception

##### 可以进行异常的处理

###### 				编译时异常(checked)

​						l-----IOException

​							l-----FileNotFoundException

​						l-----ClassNotFoundException

###### 				运行时异常(unchecked)

​						l-----NullPointerException

​						l---ArrayIndexOutOfBoundsException

​						l---ClassCastException
​						l--NumberFormatException

​						l---InputMismatchException

​						l---ArithmeticException

### 二、异常的处理

**抓抛模型**

#### 过程一

"抛"：程序在正常执行的过程中，一旦出现异常，就会在异常代码处生成一个对应异常类的对象。并将此对象抛出。

一旦抛出对象以后，其后的代码就不再执行。



#### 过程二

“抓"：可以理解为异常的处理方式: ①try-catch-finally ②throws

##### ①try-catch-finally的使用

```java
try{
	//可能出现异常的代码
}catch(异常类型1 变量名1){
		//处理异常的方式1
}catch(异常类型2 变量名2){
		//处理异常的方式2
}catch(异常类型3 变量名3){
		//处理异常的方式3
}

.......

finally{

​	//一定会执行的代码

}
```

说明:
	1.finally是可选的。

​	2.使用try将可能出现异常代码包装起来，在执行过程中，一旦出现异常，就会生成一个对应对象类的对象，根据此对象的类型，去catch中进行匹配

​	3.一旦try中的异常对象匹配到某一个catch时，就进入catch中进行异常的处理。一旦处理完成，就跳出当前的try-catch结构(在没有写finally的情况)。继续执行其后的代码。

​	4.catch中的异常类型如果没有子父类关系，则谁声明在上，谁声明在下无所谓。

catch中的异常类型如果满足子父类关系，则要求子类一定声明在父类的上面。否则，报错。

​	5.常用的异常对象处理的方式：①String getMessage() ② printStackTrace()

​	6.在try结构中声明的变量，在出了try结构以后，就不能被调用

**体会1：使用try-catch-finally处理编译时异常，使得程序在编译时就不再报错，但是运行时仍可能报错。相当于我们使用try-catch-finally将一个编译时可能出现的异常，延迟到运行时出现。**

**体会2：开发中，由于运行时异常比较常见，所以我们通常就不针对运行时异常编写try-catch-finally了.**
**针对于编译时异常，一定要考虑异常的处理。**



##### ②throws+异常类型

```java
public void method2 throws FileNotFoundException,IOException{
    method1();
}



public void method1() throws FileNotFoundException,IOException{
    File file=new File("hello.text");
FileInputStream fis=new FileInputStream(file);
int data=fis.read();
while(data!=-1){
	System.out.println((char)data);
    data =fis.read();
}
fis.close;
    
}
```

