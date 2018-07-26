# java反射

java中的三种反射用法

* ReflectMock.class
* Class.forName("ReflectMock")
* object.getClass()

三种方式都可以得到类的结构信息，但是在执行过程中会有一定的区别

示例如下：
1. 新建一个类ReflectMock
```java
public class ReflectMock {
    
    static {
        System.out.println("Static block");
    }
    
    ReflectMock() {
        System.out.println("Construct block");
    }
   
}
```

2. 测试类
```java
public class ReflectTest {
    public static void main(String[] args) throws ClassNotFoundException {
        System.out.println("--------1------------");
        Class clz1 = ReflectMock.class;

        System.out.println("--------2------------");
        Class clz2 = Class.forName("reflect.ReflectMock");

        System.out.println("--------3------------");
        ReflectMock mock = new ReflectMock();
        Class clz3 = mock.getClass();
    }
}
```

3. 结果如下：
```java
--------1------------
--------2------------
Static block
--------3------------
Construct block
```
可以看到，第一种方式不会执行累的static代码块。第二种方式会执行累的static代码块。
