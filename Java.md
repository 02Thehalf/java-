



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

### 2．举例:

Arrays类中重载的sort() / binarySearch()

### 3.判断是否是重载:

跟方法的权限修饰符、返回值类型、形参变量名、方法体都没有关系!

### 4．在通过对象调用方法时，如何确定某一个指定的方法:

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

## 五.java.lang.object类的理解

1.如果我们没显式的声明一个类的父类的话，则此类继承于java.lang.object类
2.所的java类（除java.lang.object类之外都直接或间接的继承于java.lang.object类3．意味着，所的java类具java.lang.object类声明的功能。
