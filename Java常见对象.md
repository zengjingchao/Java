## Object类
```java
getClass()
Demo d = new Demo();
Class clazz1 = d.getClass();                //返回对象的运行时类
Class clazz2 = Demo.class;
System.out.println(clazz1 == clazz2);
hashCode()

Demo d = new Demo();
int hashCode = d.hashCode();
System.out.println(hashCode);
toString()

Demo d = new Demo();
System.out.println(d);              //当对对象的引用打印时,会默认调用对象的toString方法,如果
System.out.println(d.toString());   //该对象所属的类中没有toString方法,会调用Object类中(父类)

int[] arr = new int[5];             //数组的父类也是Object
System.out.println(arr);
System.out.println(arr.toString());
equals()
public boolean equals(Object obj) {
return (this == obj);
}
==号和equals方法的区别
1,==号是一个符号,比较运算符,equals是一个方法
2,==号既可以比较基本数据类型,也可以比较引用数据类型,比较基本数据类型比较的是值,比较引用数据类型比较的是地址值
  equals方法在没有重写之前(Object类中的定义的)其实与==比较引用数据类型是一样的,但是我们在自定义类如果想比较对象中
属性,就需要重写equals方法,其实equals方法主要是用来比较对象的属性
equals方法只能比较引用数据类型 
finalize()

class DemoA {
    @Override
    public void finalize(){
        System.out.println("垃圾被清扫了");
    }

}
```
