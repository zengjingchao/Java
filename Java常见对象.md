## Object类
getClass()
```java
Demo d = new Demo();
Class clazz1 = d.getClass();                //返回对象的运行时类
Class clazz2 = Demo.class;
System.out.println(clazz1 == clazz2);
```
hashCode()
```java
Demo d = new Demo();
int hashCode = d.hashCode();
System.out.println(hashCode);
```
toString()
```java
Demo d = new Demo();
System.out.println(d);              //当对对象的引用打印时,会默认调用对象的toString方法,如果
System.out.println(d.toString());   //该对象所属的类中没有toString方法,会调用Object类中(父类)

int[] arr = new int[5];             //数组的父类也是Object
System.out.println(arr);
System.out.println(arr.toString());
```
equals()
```java
public boolean equals(Object obj) {
return (this == obj);
}
==号和equals方法的区别
1,==号是一个符号,比较运算符,equals是一个方法
2,==号既可以比较基本数据类型,也可以比较引用数据类型,比较基本数据类型比较的是值,比较引用数据类型比较的是地址值
  equals方法在没有重写之前(Object类中的定义的)其实与==比较引用数据类型是一样的,但是我们在自定义类如果想比较对象中
属性,就需要重写equals方法,其实equals方法主要是用来比较对象的属性
equals方法只能比较引用数据类型 
```
finalize()
```java
class DemoA {
    @Override
    public void finalize(){
        System.out.println("垃圾被清扫了");
    }

}
```
## Scanner&String
```java
一.Scanner
1.创建对象
使用构造函数Scanner(InputStream)传入一个输入流, 该Scanner就可以读取数据了System.in
2.读取各种类型的数据
nextInt() 可以读取一个int
nextLine() 读取一行字符串
3.关闭问题
使用结束后要调用close()方法释放资源
二.String类面试题
1.判断定义为String类型的s1和s2是否相等
String s1 = "abc";
String s2 = "abc";
System.out.println(s1 == s2);
System.out.println(s1.equals(s2));
2.下面这句话在内存中创建了几个对象?
String s1 = new String("abc");
3.判断定义为String类型的s1和s2是否相等
String s1 = new String("abc");
String s2 = "abc";
System.out.println(s1 == s2); ?
System.out.println(s1.equals(s2)); ?
4.判断定义为String类型的s1和s2是否相等
String s1 = "a" + "b" + "c";
String s2 = "abc";
System.out.println(s1 == s2); ?
System.out.println(s1.equals(s2)); ?
5.判断定义为String类型的s1和s2是否相等
String s1 = "ab";
String s2 = "abc";
String s3 = s1 + "c";
System.out.println(s3.equals(s2)); ?
三.构造函数
1.字节数组
byte[] arr = {97,98,99};
String str = new String(byte[])	//解码,让我们看的懂的,通过默认的编码表,将字节数组转换成字符串
String(byte[], String)	//解码,通过指定的编码表,将字节数组转换成字符串
String(byte[], int offset, int length, String)//解码,截取字节数组,offset是开始索引,length是截取的长度
2.字符数组
String(char[])	//将字符数组转换成字符串
String(char[], int offset, int length)	//截取字符数组,offset是开始的索引,length是截取的长度
四.String类的常用方法
1,判断

1.1 boolean equals(Object);	//判断传入的字符串是否与调用的字符串字符序列是否相同,相同就返回true否则false
1.2 boolean equalsIgnoreCase(string);	//判断传入的字符串是否与调用的字符串字符序列是否相同,不区分大小写,相同就返回true否则false
1.3 boolean contains(string);	//判断传入的字符串是否被调用的字符串包含
1.4 boolean startsWith(string);	//判断调用的字符串是否以传入的字符串开头
1.5 boolean endsWith(string);	//判断调用的字符串是否以传入的字符串结尾
1.6 boolean isEmpty();	//判断字符串是否为空
2,获取

2.1 int length();	//获取字符串的长度
2.2 char charAt(index);	//通过索引获取对应的字符
2.3
int indexOf(int ch);	//通过传入int数或者是字符找对应索引
int idnexOf(int ch,fromIndex);	//在指定fromIndex的位置查找传入的字符
2.4
int indexOf(string str);	//通过传入字符串查找字符串所对应的索引
int idnexOf(string str,fromIndex);	//通过指定fromIndex的位置查找传入的字符串
2.5
int lastIndexOf(ch);	//通过传入的字符从后向前找字符的索引值,把从后向前第一次找到的索引值返回
int lastIndexOf(ch,fromIndex):	//通过指定fromIndex的位置,从后向前查找字符,把从后向前第一次找到的索引值返回
2.6
int lastIndexOf(string);	//通过传入的字符串,从后向前查找,将第一次找到字符串中第一个字符的索引返回
int lastIndexOf(string,fromIndex):	//通过指定fromIndex的位置,从后向前查找对应字符串,将第一次找到字符串中第一个字符的索引返回
2.7
String substring(start);	//通过传入的索引值开始向后截取,截取的是索引到length
String substring(start,end);	//通过传入的两个索引值截取,有开始有结尾,包含头不包含尾
3,转换

3.1
byte[] getBytes();	//编码,让计算机看的懂的,用默认的编码表,将字符串转换成字节数组
byte[] getBytes(String)	//用指定的编码表进行编码
3.2 char[] toCharArray();	//将字符串转换成字符数组
3.3
static String copyValueOf(char[]);	//将字符数组转换成字符串
static String copyValueOf(char[] data, int offset, int count);//将字符数组转换字符串,通过offset开始,截取count个
3.4
static String valueOf(char[]);	//将字符数组转换成字符串
static String valueOf(char[] data, int offset, int count);//将字符数组转换字符串,通过offset开始,截取count个
3.5

static String valueOf(int);	//将一个int数转换成字符串
static String valueOf(double);
static String valueOf(boolean); ...
3.6

static String valueOf(object);
和object.toString():结果是一样的。
3.7
String toLowerCase():	//将字符串全部转换为小写
String toUpperCase():	//将字符串全班转换为大写
3.8 "abc".concat("kk");	//将两个字符串相连接,产生新的字符串
4,替换。

4.1 String replace(oldChar,newChar);	//将newChar替换OldChar,如果OldChar不存在,原字符串直接赋值给替换后字符串
4.2 String replace(string,string);
5,切割。

String[] split(regex);	//通过regex切割字符串,切割后会产生一个字符串数组
String s = "金三胖 郭美美 李天一";
String[] arr = s.split(" ");
6,去除字符串两空格。

String trim();
7,比较

String str = "ab";
String str1 = "bc";
int num = str.compareTo(str1);	//如果str比str1大的话,返回的正数
```
