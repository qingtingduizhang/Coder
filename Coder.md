```java
Be a Coder，任职要求
```

```
黑马130期JAVA学员李鸣飞
微信：leem97_
有任何问题可与我联系，与学妹学弟一起成长！
【本人使用本材料面试结果：2/8（25%）,1家甲方（1 offer，17k13薪），1家外包（1 offer，20k13薪）】20210927
后续会继续更新
```



### Java

#### JAVA基础扎实

##### JavaBasis:

**什么是面向对象？**

- 与面向过程对比阐述（面试官面试我/面试官.提问（）+我.回答（））

  -  面向过程只是针对于自己来解决问题。面向过程的操作是以程序的基本功能实现为主，实现之后就完成了，也不考虑修改的可能性 

- 特性：
  - **封装**（外部调用无需关心内部实现并且不能修改，`Mybatis`封装`JDBC`）
  
  - **继承**（子类拥有父类方法&属性，扩展个性化需求）
  
  - **多态**（只能调用父类中有的方法/方法重写，如果想要调用子类的特有方法需要进行强转，父类类型 变量名=new 子类对象；变量名.子类方法名（），new不同的子类对象时，这个对象又是子类又是父类，体现了多种形态）
    
    - **最直接的体现是当我们对一个父类数组进行遍历时，子类是允许加入这个数组的，这个适合遍历的变量就是多态的，因为它会针对性的遍历子类和父类不一样的数据，而此时，这种既可以输出子类的数据，又可以输出父类的数据，我们称为多态绑定，该变量则是多态的。**
    - ![1662518185118](asserts\1662518185118.png)
    
  - **抽象**，核心是代码的一个复用，对本质上相同的代码做一个抽取成为一个抽象类，抽象类就是为了继承而存在的
    
    - 抽象的类是用来被继承的，而final修饰的类是无法继承的，所以final无法修饰抽象类
    
    -  外部抽象类不允许使用static声明，而内部的抽象类运行使用static声明。使用static声明的内部抽象类相当于一个外部抽象类，继承的时候使用“外部类.内部类”的形式表示类名称。 
    
      - ```java
        package com.wz.abstractdemo;
        
        abstract class A{//定义一个抽象类
        	
        	static abstract class B{//static定义的内部类属于外部类
        		public abstract void print();
        	}
        	
        }
        
        class C extends A.B{
        	
        	public void print(){
        		System.out.println("**********");
        	}
        }
        public class TestDemo {
        
        	public static void main(String[] args) {
        		A.B ab = new C();//向上转型
        		ab.print();
        	}
        
        }
        
        
        ```
    
    - 抽象可以帮助我们在对相同父类的子类进行集体操作时，方便的调用抽象类的方法并进行区别性的输出，即不同的抽象实现，并且输出不同的内容。
    
      - ![1662535630628](asserts\1662535630628.png)

**为什么java没有多继承？**

-  假设我们有类B和类C，它们都继承了相同的类A。另外我们还有类D，类D通过多重继承机制继承了类B和类C。 这时候，因为D同时继承了B和C，并且B和C又同时继承了A，那么，D中就会因为多重继承，继承到两份来自A中的属性和方法。

  这时候，在使用D的时候，如果想要调用一个定义在A中的方法时，就会出现歧义。

  因为这样的继承关系的形状类似于菱形，因此这个问题被形象地称为菱形继承问题。

  而C++为了解决菱形继承问题，又引入了**虚继承**。

  因为支持多继承，引入了菱形继承问题，又因为要解决菱形继承问题，引入了虚继承。而经过分析，人们发现我们其实真正想要使用多继承的情况并不多。

-  ![img](asserts\16145019571199.jpg) 

**成员变量和局部变量的区别**

- 在类中的位置不同
  - 成员：类中方法上
  - 局部：方法定义中或方法声明上
- 在内存中的位置不同
  - 成员：在堆中
  - 局部：在栈中
- 生命周期不同
  - 成员：随着对象的创建而存在，随着对象的创建而消失
  - 局部：随着方法的调用而存在，随着方法的调用完毕而消失
- 初始化值不同
  - 成员：有默认值
  - 局部：没有默认值，必须定义赋值后，才能使用

**static关键字的注意点**

- 可以修饰类、方法、成员变量
- 不可以修饰局部变量
- 用于创建类级别的变量和方法： 使用static关键字修饰的成员变量和成员方法属于类，而不是属于对象。这意味着可以**通过类名直接访问这些变量和方法，而无需创建类的实例**。
- 用于共享变量： 由于static变量属于类，因此在**类的所有实例中都共享这个变量**。这可以用来在**多个对象之间共享状态或数据**。
- 用于代码块： 静态代码块是在类加载时执行的，它可以用来执行类级别的初始化代码。

**理解private、public、protected关键字**

- 在顶级（类或接口等），类可以用public修饰，对所有类可见；没有修饰符，默认为package-private，它只在自己的包中可见【public、package-private】
- 在成员级别，private指定该成员只能在自己的类中访问；protected指定该成员只能在当前类、子类和同一个包中访问 （子类不一定非要是同一个包下）
-  另外，需要注意的是，尽管使用private关键字可以隐藏类的实现细节，但**如果在类的方法中暴露了private成员变量的getter和setter方法，仍然可以在类的外部访问这些成员变量**。因此，使用private关键字并不意味着完全防止对成员变量的访问。 

**理解transient关键字**

transient：瞬态的，在Java中，transient是一个关键字，用于修饰类的成员变量，它的作用是告诉Java虚拟机在序列化该对象时，这个成员变量不需要被序列化。

具体来说，当一个对象被序列化时，它的所有成员变量都会被序列化，并写入序列化流中。但是，有些成员变量可能不希望被序列化，例如缓存数据、临时状态等。在这种情况下，可以使用transient关键字修饰这些成员变量，这样它们就不会被序列化，而是在反序列化时被赋予默认值。

需要注意的是，transient关键字只能修饰成员变量，不能修饰方法或类。此外，被transient修饰的成员变量不能被静态修饰符所修饰，因为静态成员变量是类级别的，它们不能被序列化或反序列化。

 **序列化和反序列化大多数在哪些场景用到 ？**

1. 网络传输：将Java对象序列化成字节流，在网络上传输，接收方再将字节流反序列化成Java对象。
2. 缓存存储：将Java对象序列化成字节流，存储在缓存中，读取时再将字节流反序列化成Java对象。
3. 消息队列：将Java对象序列化成字节流，发送到消息队列，消费者从消息队列中取出字节流，再反序列化成Java对象进行处理。
4. 分布式存储：将Java对象序列化成字节流，存储在分布式存储系统中，需要时再反序列化成Java对象。
5. 远程调用：将Java对象序列化成字节流，通过远程调用协议传输，接收方再将字节流反序列化成Java对象。

这些场景中，序列化和反序列化是将Java对象与字节流进行转换的重要手段，以实现跨网络、跨进程、跨节点等数据传输和存储的需求。

 **private static final long serialVersionUID = 1L;是什么意思** 

在Java中，Serializable接口是一个标记接口，用于表示一个类可以被序列化和反序列化，但它并没有包含任何方法。当一个类实现了Serializable接口后，Java的序列化机制就可以对这个类的实例进行序列化和反序列化操作。

**而serialVersionUID是一个序列化版本号，用于标识类的不同版本。在进行序列化和反序列化时，JVM会使用该版本号来确定类的版本是否一致**。如果版本号不同，则会抛出InvalidClassException异常。

一般情况下，如果一个类实现了Serializable接口，则应该给该类添加一个名为serialVersionUID的静态常量，用于指定该类的序列化版本号。如果没有指定，则系统会根据类的结构自动生成一个版本号。**如果在后续修改了该类的结构，需要重新生成该类的序列化版本号，以保证兼容性**。

 假设有一个Person类，代码如下： 

```java
public class Person implements Serializable {
    private static final long serialVersionUID = 1L;
    private String name;
    private int age;
}
```

 假设这个类已经被使用了一段时间，而后又对该类进行了修改，增加了一个字段`address`，代码如下： 

```java
public class Person implements Serializable {
    private static final long serialVersionUID = 2L;
    private String name;
    private int age;
    private String address;
}
```

由于类的定义发生了变化，因此我们需要手动递增`serialVersionUID`的值，这里将`serialVersionUID`的值从1L改为了2L。

这样做的好处是，当老版本的对象被反序列化成新版本的对象时，新版本中新增的字段会被初始化为默认值，而不会导致反序列化失败。但是需要注意，如果对类的修改破坏了类的兼容性，那么手动递增`serialVersionUID`的值也无法避免反序列化失败的问题。

**基本数据类型字节数？【新核云】**

-  Java 的基本数据类型字节数在不同操作系统或版本上是一致的，这是由 **Java 虚拟机规范所定义**的。Java 中的基本数据类型（如 int、long、float、double 等）的大小是固定的，例如 int 类型是 4 个字节，double 类型是 8 个字节。这些**数据类型的大小不会因为操作系统或版本的变化而改变**。 
- 1个字节=8位，1 byte=8 bit

- ![1649731872247](asserts\1649731872247.png)

**创建对象的方式有哪些？【新核云】**

- 使用**new创建**

- 使用**反射机制创建**

  - 可以使用class类的newInstance方法调用无参构造创建对象
  - 使用Constructor类的newInstance方法

- 使用**clone方法**

  - 无论何时我们调用一个对象的clone方法，jvm就会创建一个新的对象，将前面对象的内容全部拷贝进去。用clone方法创建对象并不会调用任何构造函数

- 使用**反序列化**（需要原有类实现Serializable接口）

  - ```java
    ObjectInputStream Obji = new ObjectInputStream(new FileInputStream("Object1.txt"));
            Teacher t =(Teacher) Obji.readObject();
            System.out.println(t.getName()+t.getAge());
    ```

- 使用**工厂的方法创建对象**，不需要考虑new时候那种对象的具体类型、构造函数参数和个数，直接就可返回一个对象， 可以降低耦合度，提高代码的灵活性和可扩展性，并且java中对象池一般都利用了对象的复用，避免频繁创建和销毁对象，提高了系统的性能和扩展性。 

  - ```java
    public class Person {
        private String name;
        private int age;
    
        public Person(String name, int age) {
            this.name = name;
            this.age = age;
        }
    
        // getter and setter methods
    
        @Override
        public String toString() {
            return "Person{" +
                    "name='" + name + '\'' +
                    ", age=" + age +
                    '}';
        }
    }
    
    public class PersonFactory {
        public static Person createPerson(String name, int age) {
            return new Person(name, age);
        }
    }
    
    public class Main {
        public static void main(String[] args) {
            Person person = PersonFactory.createPerson("John", 20);
            System.out.println(person);
        }
    }
    ```

**如何正确退出一个多层嵌套循环？【新核云】**

  - 在最外层通过一个标签进行标记，然后通过break 标签名;退出

**深拷贝与浅拷贝的区别？【新核云】**

- 拷贝的概念其实有涉及到引用拷贝和对象拷贝的概念

  - 引用拷贝，就比如我new一个teacher1，然后我再new一个teacher2等于它，这就是引用拷贝，底层是teacher1和teacher2从栈区对堆的new的对象的引用

  - 对象拷贝，是clone出来一个新的对象，底层是两个引用指向不同的堆内存

    - 浅拷贝，指的是拷贝的对象比如student1和student2分别指向了不同的对象，但是这两个对象里面引用的共同对象teacher，还是指的是同一个堆，并没有变成两个新的对象

    - <img src="asserts\20200830152336282.png" alt="在这里插入图片描述" style="zoom: 25%;" />

    - 深拷贝，深拷贝是一个整个独立的对象拷贝，深拷贝会拷贝所有的属性,并拷贝属性指向的动态分配的内存。当对象和它所引用的对象一起拷贝时即发生深拷贝。深拷贝相比于浅拷贝速度较慢并且花销较大，**可以通过重写clone方法实现简而言之，深拷贝把要复制的对象所引用的对象都复制了一遍**


**在Java中，3*0.1==0.3的结果？**

- int：整数，double：小数，这种运算的场景是会产线精度丢失的，但是处于一个不确定的状态

**什么是内存溢出和内存泄漏？【新核云】**

- 内存泄漏：一个无用的对象，应该被回收，却因为某种原因一直未被回收，**内存泄漏是导致内存溢出的其中原因中的一种**

- 内存溢出：JVM的堆无法存储应该活着的对象了（列举几个内存溢出的原因）

  - 内存泄漏：这是导致内存溢出的主要原因之一，当程序中的某些对象不再使用时，却没有被垃圾回收器回收，这些对象将一直占用着内存空间，最终导致内存不足。
  - 内存申请过多：如果程序中频繁申请大量的内存，而没有及时释放已经使用过的内存，也会导致内存溢出的发生。
  - 堆空间过小：如果为Java虚拟机分配的堆空间过小，无法满足程序的内存需求，也可能导致内存溢出的发生。
  - 内存波动：如果程序中的内存需求不稳定，而系统没有足够的缓冲空间，就可能导致内存溢出的发生。
  - 代码中存在缺陷：如果程序中存在缺陷或者bug，可能会导致程序在运行时产生大量的临时对象，从而导致内存溢出的发生。

- ```java
  内存溢出：
  public class MemoryOverflowExample {
      public static void main(String[] args) {
          List<Integer> list = new ArrayList<Integer>();
          while (true) {
              list.add(1);
          }
      }
  }
  内存泄漏：
  public class MemoryLeakExample {
      private static List<Integer> list = new ArrayList<Integer>();
  
      public static void main(String[] args) {
          while (true) {
              list.add(1);
          }
      }
  }
  ```

**类与对象与实例的概念**

  - 类是指我们定义的Java类，指某一类型
  
  - 对象指我们去new创建出来的类的对象，我们通过对象名找到这个对象，这个对象与自己类的关系是，这个对象是它所属类的一个实例
  
    - 类在实例化时，类里面的成员变量如果没有初始值，将默认处于0，0.0，false，null及□
  
  - 实例并不一定就等于对象，在多态场景下，对象是部分实例化的形态
  
  - ```
    //Child extends Person
    Person person = new Child();部分实例化
    Child child = new Child();实例化
    ```

**Java程序是解释执行还是编译执行？**

  - **既有解释执行，也有编译执行**，java语言的执行顺序是首先通过javac工具将java文件转换成.class字节码文件，这类文件被称为IR（Intermediate Representation），即中间表达式，这些class文件需要通过JVM进行加载转换成二进制机器语言，才能够被CPU识别加载，而类加载的这样的过程，就是解释执行，这个我们可以通过反编译很直观的看到；当某一方法调用次数达到即时编译定义的阈值时，就会触发即时编译，这时即时编译器会将IR进行优化，并生成这个方法的机器码，后面再调用这个方法，就会直接调用机器码执行，这个就是编译执行的过程
  
    - 注意点，达到次数的机器码会存储在`CodeCache`中，`CodeCache`指堆外内存区
  
  - ```
    // javap -c JITDemo2.class
    
    Compiled from "JITDemo2.java"
    public class com.example.demo.jitdemo.JITDemo2 {
      public com.example.demo.jitdemo.JITDemo2();
        Code:
           0: aload_0       
           1: invokespecial #1                  // Method java/lang/Object."<init>":()V
           4: return        
    
    
      public static void main(java.lang.String[]);
        Code:
           0: getstatic     #2                  // Field java/lang/System.out:Ljava/io/PrintStream;
           3: ldc           #3                  // String Hello World
           5: invokevirtual #4                  // Method java/io/PrintStream.println:(Ljava/lang/String;)V
           8: return        
    }
    ```

**`JDK`、`JRE`、`JVM`的区别和联系？**

`JDK`包括`JRE`+`java`工具（`javac`+`java`），`JRE`包括`JVM`；

**在不重写对象的toString()方法时，直接打印对象名是内存地址吗？**

不是，这个对象名是基于对象的hashcode和对象名生成的一个字符串

**==和equals的区别**

  - ==是内存地址值
  - equals也是，但是可以重写，然后比较内容值
    - 值得注意的点是，如果你在class里new两个对象（基于相同类），里面属性的值是一样的，你去重写hashcode方法，让这两个对象的hashcode相等，这个时候这两个对象并不会指向同一个堆内存空间，在实际意义上，这两个对象还是相互独立的，拥有独立的堆内存空间，所以这个时候你去equals比较这两个对象的时候，还是false，堆内存地址是不一样的，debug可以看到这个状况
  

 **为什么要重写hashcode方法?** 

在 Java 中，对象的 `hashCode()` 方法用于获取对象的哈希码值，这个哈希码值通常会在基于哈希的数据结构中使用，例如 `HashMap`、`HashSet` 等。哈希码可以看作是一个对象的身份证号码，可以用来快速比较对象是否相等。

如果你想要将一个对象插入到基于哈希的数据结构中，并且希望它能够正确地插入和查找，那么你需要确保两个相等的对象返回相同的哈希码值。因此，当我们重写一个类的 `equals()` 方法时，通常也需要重写 `hashCode()` 方法，以确保相等的对象具有相等的哈希码值。

如果没有正确实现 `hashCode()` 方法，那么可能会导致哈希冲突，即两个不同的对象返回了相同的哈希码值。当这种情况发生时，它们将被放入同一个哈希桶中，这可能导致基于哈希的数据结构性能下降。

因此，重写 `hashCode()` 方法是为了确保对象在基于哈希的数据结构中能够正确地插入和查找，从而提高代码的性能。

 **java中哪些数据结构是基于哈希的，以及阐述一下，使用哈希结构的好处与坏处** 

Java中常用的基于哈希的数据结构有 HashMap、HashSet、Hashtable、LinkedHashMap、LinkedHashSet等。

基于哈希的数据结构主要依赖于对象的哈希码来进行查找、插入、删除等操作，从而使这些操作的时间复杂度达到常数级别，具有较高的效率。在使用哈希结构时，通过哈希函数将对象的键映射到一个数组下标上，然后将对象存储在该下标的链表或红黑树中。由于哈希函数的设计需要考虑均匀性和碰撞概率等因素，因此优秀的哈希函数能够减少哈希冲突的概率，提高基于哈希的数据结构的性能。

基于哈希的数据结构的优点包括：

- 查找、插入、删除等操作的时间复杂度都是常数级别，具有高效性；
- 可以实现快速的数据去重和数据集合运算（如求交集、并集等）；
- 可以通过哈希函数进行对象的快速定位。

基于哈希的数据结构的缺点包括：

- 哈希函数设计不合理会导致哈希冲突，影响性能；
- 由于哈希函数是不可逆的，因此基于哈希的数据结构不能直接支持范围查询；
- 在使用链表解决哈希冲突时，会造成额外的空间浪费和链表遍历的性能问题；
- 基于哈希的数据结构在并发环境下存在线程安全问题，需要进行额外的同步处理。

**final的理解**

- 修饰类：不能被继承，修饰方法：方法不能被重写，但是可以重载，修饰变量：变量一旦赋值就不可以更改值
- 修饰成员变量定义时需要直接赋值，修饰局部变量定义时不用，但是使用时要赋值，后续值不可更改
- 修饰引用类型的变量，不能再指向另一个堆地址，但是里面的值可更改

**为什么局部内部类和匿名内部类只能访问局部final变量？**

- 外部类运行结束后会对局部变量进行销毁，Java对其进行了copy使得内部类可以使用，但是在使用初衷是不希望局部变量进行改变的，所以加个final进行约定，不允许再更改

**`String`、`StringBuilder`及`StringBuffer`的区别**

- `StringBuilder`>`StringBuffer`>`String`，`StringBuilder` `stringBuilder` = new `StringBuilder`("`wuman`");
- `StringBuffer`被synchronized修饰，线程安全，性能稍差，String每次new新对象，性能最差

- 多线程使用共享的变量时使用`StringBuffer`，其他场景优先使用`StringBuilder`
  
- 重载和重写的区别？
  - 重载只和参数有关，参数必须不同
  - 重写子类返回值和异常范围小于父类，访问修饰符范围大于父类，子类无法重写父类中**private**的方法

- 接口和抽象类的区别？【新核云】
  - 抽象类有构造方法，接口没有；接口成员变量只能是常量；接口方法`jdk`1.7以前只能是抽象的，`jdk`1.8后可以写default和static开头的方法
    - 抽象类有构造方法，那它可以被实例化吗？
      - 不能被实例化，抽象类定义出来就是被继承的，因为抽象类里面的方法都是Abstract的，需要去重写实现
      - 普通类里是不能定义抽象方法的，定义时会直接`CheckedException`
  - 类与类只能单继承或多层继承，类与接口可以多实现，接口与接口可以多继承
  - 抽象类里面定义的都是一个继承体系中的共性内容（代码复用，现有子类，提取共用代码），接口是功能的集合,是一个体系额外的功能，是暴露出来的规则；
    - 继承是针对事物本质的抽象（is a），接口是对行为的抽象；
  
- List和Set的区别
  - List有序可重复，Set无序不可重复，可以get下标或者迭代器
  - List可以多null，Set只允许一个null，只能迭代器

- `HashCode`与equals的区别？

  - equals是比较两个对象是否相等的方法，默认是比较堆中的地址
  - `HashCode`是Java给每个对象内置的`hashcode`()返回的哈希码（int），通过哈希吗确定该对象的索引位置，快速找到所需要的对象
  - `Hashcode`相同，对象不一定相同；对象相同，`HashCode`一定相同

- `ArrayList`和`LinkedList`的区别？

  - `ArrayList`底层动态数组（有序），拥有扩容机制，查快增删慢，但是可以通过提前预估容量和尾插法来解决此问题，甚至可以超过`LinkedList`（`LinkedList`在增删时快生成对应的node对象，消耗性能）
  - `LinkedList`底层链表（无序），查慢增删快，只能使用iterator，使用for或者`indexOf`直接遍历整表，太消耗性能

- `HashMap`和`HashTable`有什么区别？底层实现？

  - `HashMap`方法没有synchronized修饰，线程非安全，`HashTable`线程安全

  - `HashMap`允许key和value为null，而`HashTable`不允许

  - 底层实现：数组+链表+红黑树（`jdk1.8`后加入）实现

    - hash数组的初始length是16

      - 一定保证length是2的次幂，源码规则，`hashmap`在判断元素需要进入哪一个桶的时候，需要对key的hash值进行取模【hash值%length】（二次），但是取模的操作是比较重的，消耗性能，当数组的length总是2的n次方时，用hash值和（数组的length-1）进行&运算（位与运算）的结果和取模是一样的，相比而来取模需要二进制转化成十进制进行，但是&直接进行操作

      - 为什么要进行二次hash，二次hash是将需要保存的key进行高地位信息的集中，更加避免哈希冲突

        ```java
        static final int hash(Object key) {
            int h;
            return (key == null) ? 0 : (h = key.hashCode()) ^ (h >>> 16);
        }
        ```

    - 在数组占用量达到16*0.75=12时，会主动进行翻倍扩容

    - 计算key的hash值，二次hash对数组长度取模，对应到数组下标

    - 如果没有产生哈希冲突，则直接创建node存入数组

    - 如果出现哈希冲突，先进行equal比较，相同则取代该元素，不相同则判断链表高度插入链表，`jdk8`后，当链表高度超过8并且数组长度超过64时，链表转为红黑树，当高度小于6时，退化成链表结构，6-8源码解释泊松分布得出

    - key为null，存在下标0的位置

- `ConcurrentHashMap`原理，`jdk7`和8的区别？(了解)

  - `jdk1.7`，segment分段锁（锁进行了优化）+`HashEntry`
  - `jdk1.8`，synchronized+`CAS`+node+红黑树

- 什么是字节码？采用字节码的好处是什么？

  - 我们的`app`运行是面向`jvm`虚拟机的，产生的class文件在`jvm`里面运行后，由其转成可供计算机运行的二进制代码
  - 好处就是`java`代码可以通过`jvm`实现跨平台的运行，可移植

- Java的类加载器有哪些？

  - `BootStrapClassLoader`，加载全局变量下的jar包和class文件
  - `ExtClassLoader`，加载全局变量下ext包下的jar包和class文件
  - `AppClassLoader`，加载我们自己写的代码，`classpath`下的文件

- 什么是双亲委派模型？

  -  ![img](asserts\watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L2NvZGV5YW5iYW8=,size_16,color_FFFFFF,t_70) 
  - 好处：安全性，避免人员编写相同功能类进行替换；避免重复加载，可通过类加载器的不同来区分
  
- Java中的异常体系？

  - 所有异常来自顶级父类`Throwable`；
  - `Throwable`有两个子类：Exception和Error；
  - Error，程序无法处理的错误，`OOM`（内存溢出）
  - `Exception：RunTimeException`，`CheckedException`（`IDE`自动检测出来，比如语法错误）


##### JavaWeb：

- Cookie和Session的区别？
  - cookie数据存放在客户的浏览器上，session数据放在服务器上 
  - cookie不是很安全，别人可以分析存放在本地的cookie并进行cookie欺骗，考虑到安全应当使用session
  - session会在一定时间内保存在服务器上，当访问增多，会比较占用你服务器的性能，考虑到减轻服务器性能方面，应当使用cookie
- Get和Post请求的区别？
  - get是用来从服务器上获取数据，而post是用来向服务器传递数据
  - get是不安全的，因为在传输过程中，数据是被放在请求的URL中;而post的所有操作对用户来说都是不可见的
  - get传输的数据量小，这主要应为受`url`长度限制;而post可以传输大量的数据，所有上传文件只能用post提交
- 转发（Forward）和重定向（Redirect）的区别？
  - Forward一个请求，Redirect两个请求
  - Forward转发的页面直接可以共享request的数据，Redirect不能共享数据
- 四大域对象？
  - `pageContext`：作用整个页面，跳转后，则失效
  - request：作用当次请求
  - session：作用当次登录
  - application：作用整个应用
- 什么是`Servlet`？
  - Java语言中处理客户端请求的顶级接口
  - 处理客户端请求的组件
- HTTP与`HTTPS`的区别？
  - 安全性上，`HTTPS`是安全超文本协议，在HTTP基础上有更强的安全性。简单来说，`HTTPS`是使用`TLS`/`SSL`加密的HTTP协议
  - 传输协议上, HTTP是超文本传输协议，明文传输；`HTTPS`是具有安全性的 `SSL` 加密传输协议
  - 连接方式与端口上，HTTP的连接简单，是无状态的，端口是 80； `HTTPS` 在HTTP的基础上使用了`SSL`协议进行加密传输，端口是 443

#### 对JVM原理有一定的了解

- 能简单介绍一下JVM吗？

  - JVM是Java语言的核心，当我们写好这些.java的文件后，我们会先把它编译成.class文件，编译好之后我们的JVM会把这些.class文件载入到它里面进行运行，JVM内部主要分为四个部分，首先是.class文件进入的部分，**类加载器**，用于加载解析这些生成的.class文件，然后加载到**运行时数据区**，也就是JVM运行时所管理的**内存**，编译完的.class文件机器是不能识别的，所以我们要将这些文件通过JVM的第三个主要部分，**执行引擎**，来将这些文件转化成机器可识别的二进制文件交给CPU处理器去执行，这部分也说明了Java语言能够跨平台，通过这样的方式，Java代码最终都可以转化成机器语言，最后一部分叫做**本地方法接口**（JNI，Java Native Interface），用于调用那些基于其他语言的类库，比如CAS的底层是没有方法体的，方法都是用native修饰的

- 能说下JVM的内存组成吗？（**运行时数据区**）

  -  ![在这里插入图片描述](asserts\watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3FxXzQxMTcwMTAy,size_16,color_FFFFFF,t_70) 

  - 方法区和堆，属于线程共享的区域，生命周期和JVM相同，JVM启动时，这两个区域即创建

    - 方法区，用于存储解析.class文件产生的（Klass对象，可以理解成Java类在虚拟机内部的表示）【class part】+（静态变量+常量+注解+方法计数器等）【non-class part】，jdk1.8以前，方法区被称为永久代（Perm），1.8后经过优化，被称为元数据空间（MetaSpace），可导致OOM（加载的class文件太多了），还有就是StringTable被迁移至Heap中，而方法区被实现为MetaSpace替代，并且使用的是系统的本地内存，这些区别都是基于Oracle Open JDK的Hot Spot版本JVM如下图

    - ![1667288391477](asserts\1667288391477.png)
  
      - ```
        class part 被称作 Compressed Class Space，这个名字会有点怪，因为 Klass 本身其实没有使用压缩技术，而是引用它们的指针被压缩了
        
        class part的由来：
        在 64 位平台上，HotSpot 使用了两个压缩优化技术，Compressed Object Pointers (“CompressedOops”) 和 Compressed Class Pointers
        
        压缩指针，指的是在 64 位的机器上，使用 32 位的指针来访问数据（堆中的对象或 Metaspace 中的元数据）的一种方式。这样有很多的好处，比如 32 位的指针占用更小的内存，可以更好地使用缓存，在有些平台，还可以使用到更多的寄存器
        
        
        当使用了 compressed class pointers，这个引用是 32 位的值，为了找到真正的 64 位地址，需要加上一个 base 值
        
        
        这项技术对 Klass 的分配带来的问题是：由于 32 位地址只能访问到 4G 的空间，所以最大只允许 4G 的 Klass 地址。这项限制也意味着，JVM 需要向 Metaspace 分配一个连续的地址空间
        
        
        为了复用已有的 Metaspace 空间，使用了一个小技巧：
        
        在 Class Space 和 Non-Class Space 中，分别都有 VirtualSpaceList 和 ChunkManager 两个结构。
        
        ```
  
    但是对于 Class Space，既然我们需要一个连续的空间我们不能使用一个链表来存放所有的 Node，所以这个链表退化为只有一个节点，并且不能扩展。这个 Node 就是 compressed class space，和 Non-Class Space 中的 Node 相比，它可是巨大无比
        ```
  
      - <img src="asserts\metaspace-classspace-duality.png" alt="alt text" style="zoom:50%;" />
  
      - ![alt text](asserts\metaspace-compressed-class-ptr.png)
      ```
    
      ```
  
  - 堆，即**Java堆内存**，Java中内存最大的区域，-Xms java堆启动时内存，-Xmx java堆可扩展的最大内存，可导致OOM（引用对象溢出），GC的主要场所，几乎存储了Java中所有的对象的地方，是线程共享的，需要考虑线程安全的问题，每个 Java 对象，在它的头部，有一个引用指向 Metaspace 中的 Klass 结构
  
  - 什么时候分配MetaSpace空间
  
      - ![Metadata lifecycle - Allocation](asserts\metaspace-lifecycle-allocation.png)
  
  - **虚拟机栈、本地方法栈和程序计数器属于线程私有的区域**，不同线程之间互相也不能访问对方的这三块区域
  
    - **虚拟机栈**，就是我们常说的**栈内存**，是用于存储方法的内存模型，栈，即先进后出，杯装模型，每当在我们的Java代码里，你要调用一个方法的时候，咱们这个JVM都会把你的这个方法用一个对象进行封装，这个对象叫做栈帧，栈帧里存储了很对数据，其中比较重点的有一个叫做本地变量表的数据，它是用来存储我们方法中的局部变量的，栈帧入栈了，就代表这个方法被执行了
    - 虚拟机栈可导致OOM和栈深度溢出（方法无限递归）
    - 本地方法栈（Native），运行原理和虚拟机栈基本一致，虚拟机栈是针对Java方法的栈，本地方法是针对其它的语言设置的方法栈，用于其它语言的运行
    - **程序计数器（也称pc寄存器）**，记录当前线程字节码执行到哪了，记录这个的原因，是因为我们Java语言多于多线程的执行机制采取的是抢占式的，线程互相之间都在抢时间片，当某个线程执行到某个位置然后程序需要切换去执行别的线程时，线程需要挂起并通过程序计数器提交自己的执行位置，待下次抢夺到时间片时，JVM可以知道此线程从哪里开始继续执行，这个区域是不会发生内存溢出的，主要是因为只是记录了线程运行的地址，占用的空间几乎可以忽略不计，即使是死循环也无法导致OOM
    
  -  StringTable，即串池,1.8后被移至堆，原因是串池使用频繁，需要进行GC，而1.6之前在老年代里的串池触发GC的条件苛刻，串池使用如此频繁应该处于及时可以GC的区域，故转移至堆
  
     -  常量池中的字符串仅是符号，第一次用到时才变为对象
     -  利用串池的机制，来避免重复创建字符串对象
     -  字符串变量拼接的原理是StringBuilder（1.8）
     -  字符串常量拼接的原理是编译器优化
     -  可以使用intern方法，主动将串池中还没有的字符串对象放入串池
        -  1.8将这个字符串对象尝试放入串池，如果没有则并不会放入，如果没有则放入串池，会把串池中的对象返回（有的话不会放入，但是返回串池里面有的对象 ）
  
- StringTable性能调优

  - 调整：-XX:StringTableSize=桶个数
  - 考虑将字符串是否入池

- Direct Memory（直接内存）

  - 常见NIO操作中，用于数据缓冲区，即ByteBuffer使用的缓冲区空间就是直接内存，大大的优于普通IO
    - bytebuffer.allocateDirect()底层主动对分配的直接内存，通过unsafe.freeMemory()进行了释放
      - ByteBuffer的实现类内部，使用了Cleaner（虚引用）来监测ByteBuffer对象，一旦ByteBuffer对象被垃圾回收，那么就会由ReferenceHandler线程通过Cleaner的clean方法调用freeMemory来释放直接内存
        - 有一个值得注意的点是，当我们显示关闭gc时，即使得system.gc()方法失效，由于gc失效导致bytebuffer对象不被回收，而Cleaner触发直接内存释放的条件就是通过referencehandler线程监听bytebuffer对象被回收时才调用unsafe进行回收，故关闭显示gc时，在代码里我们需要反射创建unsafe对象主动释放直接内存
          - 显示关闭gc的原因是，system.gc()会触发老年代和年轻代的整体回收，大大的影响了程序的运行时间，有些程序员乱使用
        - ![1667460062080](asserts\1667460062080.png)
    - <img src="asserts\1667453138745.png" alt="1667453138745" style="zoom:50%;" />
    - <img src="asserts\1667455274357.png" alt="1667455274357" style="zoom:50%;" />
  - 分配回收成本较高，但读写性能高
  - 属于系统内存，不受JVM内存回收管理

- GC（垃圾回收）机制
  - 可作为GC Root的对象？
    - 栈帧所引用的对象（正在执行中的方法中引用的对象）
    - 方法区中类静态属性引用的对象
    - 方法区中类引用的常量对象
  
- `GC`如何判断对象可以被回收？

  - 引用计数法：每个对象有一个引用计数属性，新增一个引用时计数+1，引用释放时-1，计数为0时可以回收（`JVM`不适用此方法）
    - 循环引用直接GG，早期Python是这个
  - 可达性分析法：从`GC` Roots开始向下搜索，搜索过的路径称为引用链，当一个对象到`GC` Roots没有任何引用链相连时，则证明此对象是不可用的，那么`JVM`就判断是可回收对象

- 四种引用

  - 强引用
    - 只有所有GC Roots对象都不通过【强引用】引用该对象，该对象才能被垃圾回收
  - 软引用（SoftReference）
    - 仅有软引用引用该对象时，在垃圾回收后，内存仍不足时会再次触发垃圾回收，回收软引用对象
    - 可以配合引用队列来释放软引用自身
  - 弱引用（WeakReference）
    - 仅有弱引用引用该对象时，在垃圾回收时，无论内存是否充足，都会回收弱引用对象
    - 可以配合引用队列来释放弱引用自身
  - 虚引用（PhantomReference）
    - 必须配合引用队列使用，主要配合ByteBuffer使用，被引用对象回收时，会将虚引用入队，由Referenece Handler线程调用虚引用相关方法释放直接内存
  - 终结器引用（FinalReference）
    - 无需手动编码，但其内部配合引用队列使用，在垃圾回收时，终结器引用入队（被引用对象暂时没有被回收），再由Finalizer线程通过终结器引用找到被引用对象并调用它的finalize方法，第二次GC时才能回收被引用对象
      - 所以效率极低，不推荐重写对象的finalize方法来进行垃圾回收

- 垃圾回收是否涉及栈内存？

  - 不涉及，栈帧对应着每一个调用的方法，调用完以后出栈即自动回收，而垃圾回收机制是针对JVM中堆内存设计的回收机制

- 栈内存分配越大越好吗？

  - 不是的，越大反而会影响多线程的线程上限，使得运行效率降低，每个栈即每个线程都是独立的，分配得越大越会使机器可运行的线程上限变少，分配大的栈内存除了可以用来做更多的方法递归操作外没有什么其他意义

- 方法内的局部变量是否线程安全？

  - 如果方法内局部变量没有逃离方法的作用访问，它是线程安全的

- 线程诊断示例

  - linux中用top指令定位哪个进程对cpu的占用过高
  - ps H -eo pid,tid,%cpu|grep 进程id（用ps命令进一步定位是哪个线程引起的cpu占用过高）
  - jstack 进程id
    - 可以根据线程id（上述步骤的线程id需要进行十进制👉十六进制转换，并且对应的是nid而不是tid，因为此时上述找到的线程id是指的操作系统下的线程id（即本地id），nid即native（意为本地的） id，tid是java运行下的线程id）找到有问题的线程，进一步定位到问题代码的源码行号

- 堆内存诊断

  - jps 查看当前系统中有哪些java进程
  - jmap 查看堆占用情况，jmap -heap 进程id
  - jconsole工具 图形界面的，多功能的监测工具，可以连续监测
  - jvisualvm工具 dump对快照进行分析，找到问题对象

- 垃圾收集算法
  - 主流的GC机制大都采用分代收集算法，垃圾回收最主要的区域是对于堆内存的对象进行回收，Java对于堆内存的对象回收进行了分代，即年轻代和老年代
    - 年轻代代表的是创建完后线程运行完绝大部分都被回收掉的对象，采用的基础算法是复制算法，在年轻代内存中，Java加入了Eden和Survivor的概念，其实是一种**对复制算法的改进**，Java把复制算法中的正常运行区叫做Eden（伊甸园），把用于存储存活对象的内存存储区叫做Survivor（幸存者区），关于Survivor中值得注意的是，Java对于这个存储区的改进是把这个存储空间准备了两份，我就先叫它Survivor To和Survivor From，但是这个To和From是相对的，**程序运行时，当Eden中的对象装满之后，年轻代的`GC`（MinorGC）会被触发，JVM会将Eden中标记的存活对象复制到From里，然后清理Eden区，等到下次Eden装满触发年轻代`GC`（MinorGC），JVM会同时对Eden区及From区进行check，将Eden和From里标记的存活的对象复制到To中，然后清理Eden区，再触发年轻代`GC`（MinorGC）时，Survivor的角色就发生了转变，即JVM会去check Eden和To的内存，然后进行复制到From区的操作，如此反复来达成年轻代`GC`******（MinorGC）****，**这种改进把降低了原有复制算法内存的浪费**
    - 老年代，**在年轻代的GC（MinorGC）中，每个对象会有一个GC Age的年龄计数器，每次GC，存活对象的Age就会+1，我们可以设置这样的Age阈值，默认是15，存活次数达到15时，JVM会将此对象移至老年代存储区，当老年代区域内存装满时，会触发老年代GC（MajorGC），采用的算法是清楚算法和整理算法，当老年代GC（MajorGC）后，对象还是装不下，就会产生OOM**
      - 老年代的晋升方式
        - 除了通过Age，还存在分配担保的方式，具体情况就是当需要移至幸存者的对象大小已经溢出了幸存者的剩余空间时，这个时候JVM会执行分配担保的策略，直接将其存储至老年代
        - 还有就是可以设置对象阈值，即设置Eden的运行对象大小假如超过此阈值，即直接晋升至老年代
      
      - 复制算法，相对来说是比较浪费空间的算法，它的原理是有两个空间，一个空间专门用于存储复制的不可回收的对象，一个空间用于运行，针对我们运行后的对象进行追踪，当运行后的对象与栈帧仍然保持联系，对这些对象进行标记，视其为不可回收对象，复制进用于存储这些对象的空间并指定地址顺序，然后对运行空间进行整体回收，这样做的好处是解决了清楚算法内存碎片的问题
      - 标记清除算法，即对运行空间中需要回收的对象进行标记，然后回收，但是会产生内存碎片的问题，，**当需要分配较大对象时，由于找不到合适的空闲内存而不得不再次触发垃圾回收动作**
      - 标记整理算法，先搜索存储对象，对可存储对象进行排序，再GC
  
- 什么情况下需要开始类加载呢？
  - 在遇到 new、putstatic、getstatic、invokestatic 字节码指令时，如果类尚未初始化，则需要先触发初始化。
    - new User();当对static属性进行获取或者赋值的时候
  - 对类进行反射调用时，如果类还没有初始化，则需要先触发初始化
  - 初始化一个类时，如果其父类还没有初始化，则需要先初始化父类
  - 虚拟机启动时，用于需要指定一个包含 main() 方法的主类，虚拟机会先初始化这个主类
  
- 类的加载过程
  - 加载（Loading）→验证（Verification）→准备（Preparation）→解析（Resolution）→初始化（Initialization）
    - 第一阶段，类加载器读到我们的.class文件得到二进制的流
    - 第二阶段，验证阶段，检查当前文件是否虚拟机的加载要求，检查是不是class文件，检查语法、版本等
    - 第三阶段，准备阶段，在方法区为class文件及静态变量开辟好内存
    - 第四阶段，解析过程，将符号引用转为直接引用
    - 第五阶段，初始化阶段，对类里的静态变量进行真正的赋值，初始化静态代码块
  
- JVM性能监控与故障处理
  - 如何排除内存溢出的问题
    - 可视化监控平台Jconsole查看内存使用状况
    - 使用Jmap生成堆转储快照，.hprof文件
    - 与Jmap的文件搭配，使用Jprofiler处理.hprof文件，路由到问题类，然后处理
    - 与Jconsole搭配，使用Jstack指令追踪堆栈异常状况，找到指定异常线程
  
- JVM相关VM参数

  - 堆初始大小 -Xms
  - 堆最大大小 -Xmx或-XX:MaxHeapSize=size
  - 新生代大小 -Xmn(初始和最大同时指定)或（-XX:NewSize=size+ -XX:MaxNewSize=size）
  - 幸存区比例（动态） -XX:InitialSurvivorRatio=ratio和 -XX:+UseAdaptiveSizePolicy
  - 幸存区比例 -XX:SurvivorRatio=ratio（ratio是8，伊甸园占8，剩下的一份From一份To）
  - 晋升阀值 -XX:MaxTenuringThreshold=threshold
  - 晋升详情 -XX:+PrintTenuringDistribution
  - GC详情 -XX:+PrintGCDetails -verbose:gc
  - FullGC前先进行MinorGC -XX:+ScavengeBeforeFullGC

- 当多线程情况下导致堆内存溢出异常时，主线程会因此暂停吗？

  - 不会，不影响

- 关于垃圾回收器的选择【Serial其实就是串行的英语，Parallel是并行的英语】

  - 串行【Serial，Serial Old】
    - 单线程，堆内存较小，适合单人电脑
  - 吞吐量优先的并行（吞吐量只GC占运行时间的比例，GC时间越少，吞吐量越高）【 Parallel Scavenge 】
    - 多线程，堆内存较大，多核cpu
    - 让单位时间内，STW的时间最短
  - 响应时间优先的并行【CMS（concurrent并发，mark标记，sweep清除），G1，ZGC】
    - 多线程，堆内存较大，多核cpu
    - 尽可能让单次STW的时间最短（stop the world，GC时需要停止所有线程的这一行为的术语）
      - CMS需要与ParNew+Serial Old搭配使用，由于是标记清除，所以会产生内存碎片，积累多了以后会导致并发失败，这时候就需要ParNew+SerialOld配合进行一次标记整理，但标记整理是很耗时的，这就和CMS初衷的响应时间优先直接矛盾，也是CMS最大的缺点，所以此GC后面被新的G1取代了
  - G1垃圾回收器
    - 同时注重吞吐量和低延迟
    - 超大堆内存，会将堆划分成多个大小相等的区域
    - 整体上是标记+整理算法，两个区域之间是复制算法
  -  ![img](asserts\watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L2l2YV9icm90aGVy,size_16,color_FFFFFF,t_70) 

- JVM调优小结（目前只能说自己了解过）

- ```
  JVM参数调优实际上没有具体的答案，要根据不同的实战场景进行对应的设置，还需要不断的调试和磨合，设置的不好，JVM不断执行Full GC，导致整个系统变得很慢，网站停滞时间能达10秒以上，这种情况如果没隔几分钟就来一次，自己都受不了。这种停滞在测试的时候看不出来，只有网站pv达到数十万/天的时候问题就暴露出来了。
  所以对于JVM调优的话术，我们可以这么说，结合我们公司之前的经验，对于JVM调优我们可以从下面方向进行分析：
  互联网项目   64 Linux Centos6.5  8GB
  
  1：如果服务器硬件性能足够，建议采用64位操作系统，Linux下64位的jdk比32位jdk要慢一些，但是吃得内存更多，吞吐量更大。
  
  
  2：XMX和XMS设置一样大，MaxPermSize和MinPermSize设置一样大，这样可以减轻伸缩堆大小带来的压力。
  
  
  3:  -Xmn年轻代的大小，      并行：吞吐量       并发：低延迟  
  	-XX:NewRadio年轻代和年老代的比值，
  	Sun建议 年轻代与年老代的比例：3/8
  	
  	
  4:  垃圾回收器的选择：
  		      
  	响应时间优先的应用:并发收集器 ParNew + CMS（老年代）     或者 G1 
  	                                + Serial Old (STW)
  	
  	吞吐量优先的应用：并行收集器  Parallel Scavenge + Parallel Old
  	使用并发收集器，肯定就是追求最小的响应时间，所以应该减少年轻代，加大年老代，这样可以利用年老代的并发CMS收集器来减少响应时间。
  	使用并发收集器，一般是最求吞吐量优先的应用，会加大年轻代，缩小年老代。这样可以在年轻代回收掉大部分短期对象，减少中期对象，而老年代只存少部分长时间存活的对象。
  	（年老代的并发收集器使用标记,清除算法,所以不会对堆进行压缩.当收集器回收时,他会把相邻的空间进行合并,这样可以分配给较大的对象.但是,当堆空间较小时,运行一段时间以后,就会出现"内存碎片",如果并发收集器找不到足够的空间,那么并发收集器将会停止,然后使用传统的标记,清除方式进行回收.如果出现"碎片",可能需要进行如下配置:
  -XX:+UseCMSCompactAtFullCollection:使用并发收集器时,开启对年老代的压缩.
  -XX:CMSFullGCsBeforeCompaction=0:上面配置开启的情况下,这里设置多少次Full GC后,对年老代进行压缩
  ）
  
  5：调试的时候设置一些打印参数
  	如：	-XX:+PrintClassHistogram 
  		 -XX:+HeapOnOutOfMerroryError
  		 -XX:+PrintGCDetails 
  		 -XX:+PrintGCTimeStamps 
  		 -XX:+PrintHeapAtGC 
  		 -Xloggc:log/gc.log
     这样可以让jvm虚拟机打印出类加载的情况，堆转储的快照，GC的详细回收日志 等等日志信息
  	
  6：当系统发生停顿的时候可能是GC的问题也可能是程序的问题，还有内存飙高，系统响应慢的时候，多利用jvm的监控工具实时注意jvm虚拟机的情况。 如可以通过jmap转储堆内存情况，通过jstack可以打印出线程的快照，在通过JProfiler或者JVisoulVM的分析工具进行分析。  -- 这里可以加入JVM调优案例
  
  7：仔细了解自己的应用，如果用了缓存，那么年老代应该大一些
  
  8：垃圾回收时promotion failed是个很头痛的问题，一般可能是两种原因产生
  第一个原因是救助空间不够，救助空间里的对象还不应该被移动到年老代，但年轻代又有很多对象需要放入救助空间；第二个原因是年老代没有足够的空间接纳来自年轻代的对象；这两种情况都会转向Full GC，网站停顿时间较长。
  第一个原因我的最终解决办法是去掉救助空间，
  设置-XX:SurvivorRatio=65536 -XX:MaxTenuringThreshold=0即可
  
  第二个原因我的解决办法是设置CMSInitiatingOccupancyFraction为某个值（假设70），这样年老代空间到70%时就开始执行CMS，年老代有足够的空间接纳来自年轻代的对象。
  ```

- ```
  服务器： centos 6.4    linux64位操作系统   8G内存：   70~80 
  
  B/S   低延迟    并发垃圾收集   CMS 
  
  每日百万PV，无压力：   
  
  $JAVA_ARGS .= " -Dresin.home=$SERVER_ROOT 
  -server  
  -Xms6000M    //堆初始值内存  
  -Xmx6000M    //堆的最大内存     8G   70%
  -Xmn500M     //新生代内存    CMS 老年代    3 / 8
  -XX:PermSize=500M    //永久代初始值 M 
  -XX:MaxPermSize=500M //永久代最大值 
  -XX:SurvivorRatio=65536 //新生代救助区和Eden区比值这么设置实际上是去掉救助区
  -XX:MaxTenuringThreshold=0  //新生代对象晋升老年的代年龄，设置0
  -Xnoclassgc  //不开启class收集
  -XX:+DisableExplicitGC  //禁止 System.gc()显示调用，防止手残党-----------------------------------------------
  -XX:+UseParNewGC       //年轻代垃圾收集器  ParNewGC
  -XX:+UseConcMarkSweepGC   //年老代垃圾收集器 CMS
  // ParNew + CMS (老年代)   +   Serial Old (担保)   STW
  // CMS 无法收集时 会使用串行收集器  
  // 标记 清除  会产生内存碎片  
  -XX:+UseCMSCompactAtFullCollection  //开启内存压缩功能   
  -XX:CMSFullGCsBeforeCompaction=0  // 几次FullGC后出发碎片清理
  -XX:+CMSClassUnloadingEnabled   //开启永久代回收
  -XX:-CMSParallelRemarkEnabled 
  -XX:CMSInitiatingOccupancyFraction=80  //老年代占用多少时 进行老年代回收
  // 调优参数的打印
  -XX:+PrintClassHistogram  //打印class加载信息 ------------------------------------------------------------  
  -XX:+PrintGCDetails  //打印GC详细信息 
  -XX:+PrintGCTimeStamps  //打印GC时间戳信息
  -XX:+PrintHeapAtGC   //打印GC 堆的信息-----------------------------------------------------------------
  -Xloggc:log/gc.log "; // GC的日志的地址------------------------------------------------------------------
  
  
  综合浏览量（PV）：即Page View, 即页面浏览量或点击量，用户每次刷新即被计算一次。
  并发连接数 = PV / 统计时间 * 页面衍生连接次数 * http响应时间 * 因数 / web服务器数量
  页面衍生连接次数: 一个HTML页面可能会请求好几次http连接，如外部的css, js,图片等,可以估算一下，或者用10,可根据实际情况改变
  http响应时间: 可以使用1秒或更少,可根据实际情况改变
  因数: 一般使用5即可,可根据实际情况计算后推出
  web服务器数量: web服务器数量
  
  (1000000PV / 86400秒 * 5个派生连接数 * 2秒内响应 * 5倍峰值) / 1台Web服务器  约 600左右并发~1000
  ```

#### 熟练使用Spring、SpringBoot、SpringCloud、Mybatis、RabbitMQ、Kafka框架

##### Spring：

- 什么是Spring？
  
  - 一个替代了重量级开发框架EJB的面向企业级应用开发的轻量级的解决方案，解决了EJB的运行环境苛刻（环境收费且闭源无法拓展功能，weblogic，websphere）、代码移植性差（运行需要实现相应环境的接口并且只能运行在对应的环境）的问题，轻就轻在这两点
  
- **Spring的优点**
    - Spring在开发方面给java开发中分层开发的不同层级提供了解决方案，controller提供了springmvc，service层提供了aop技术，dao层整合了mybatis

    - 整合了众多设计模式：工厂、代理、模板、策略

- 列举一些Spring的重要模块？

  - Spring JDBC：数据库连接；Spring ORM：整合ORM框架；Spring Test：Junit单元测试；Spring Aop：面向切面编程的实现；Spring Core：核心组件，IOC/DI

- Spring常用注解

  - @RestController
  - @Service
  - @Mapper

- @Autowired和@Resource的区别
  - @Autowired是Spring的注解，@Resource是JDK的注解
  - @Autowired是基于类型导入Bean，@Resource是基于名称导入
  - @Autowired（required=false）可以搭配@Qualifier实现基于名称导入

- @Controller和@RestController的区别

  - 一个共同的特点是这两个注解都包裹了@Component注解，即为了告诉开发者，当前使用此注解标注的类是代码API的Controller层
  - @RestController包含了@Controller和@Responsebody
  - @Controller的返回值是页面，更适合老旧的前后端一体式返回页面的开发
  - @RestController中的@Responsebody使得方法可以返回前后端分离所需的json或者对象等信息

- @Controller、@Service、@Respository注解的意义以及为什么DAO层不适用@Respository

  @Controller、@Service、@Respository是Spring为了让开发者知晓当前标注类是用于开发层的哪一个位置作用的标识，本质上都是@Component，只不过变个别名用于区分

  @Respository为什么不使用在Dao层是因为，Spring在整合Mybatis时，已经通过动态代理将我们DAO层定义的接口的实例进行生成了，也就是说，我们没有机会去在那个动态生成的类上进行标注，因为是动态的，配置即yml里针对DAO层进行的配置，如下图，Spring会自动进行映射然后通过namespace进行动态生成

  ![1676450382129](C:\Users\dell\Desktop\asserts\1676450382129.png)

- @Component和@Bean的区别

  @Component （@Controller @Service @Respository）作用于类上，只有在我们的SpringBoot应用程序启用了组件扫描并且包含了被注解的类时才有效。通过组件扫描，Spring将扫描整个类路径，并将所有@Component注释类添加到Spring Context，这里有的不足就是会把整个类当成bean注册到spring 容器上，如果这个类中并不是所有方法都需要注册为bean的话，会出现不需要的方法都注册成为bean，这时候必须确保这些不需要的方法也能注册为bean或者在扫描中加filter 过滤这些不需要的bean,否者spring将无法成功启动。

  @Bean相对来说就更加灵活了，它可以独立加在方法上，按需注册到spring容器，而且如果你要用到第三方类库里面某个方法的时候，你就只能用@Bean把这个方法注册到spring容器，因为用@Component你需要配置组件扫描到这个第三方类路径而且还要在别人源代码加上这个注解，很明显是不现实的。

- SpringMVC的运行流程

- ![1655803796760](asserts\1655803796760.png)

- Bean的生命周期

  - > **spring 容器中的bean的完整生命周期一共分为十一步完成。**

    > **1.bean对象的实例化**
    >
    > ​	有有参构造则通过有参构造创建，没有则通过无参构造创建

    > **2.封装属性，也就是设置properties中的属性值**
    >
    > ​	set注入属性

    > **3.如果bean实现了BeanNameAware，则执行setBeanName方法,也就是bean中的id值**

    > **4.如果实现BeanFactoryAware或者ApplicationContextAware ，需要设置setBeanFactory或者上下文对象setApplicationContext**

    > **5.如果存在类实现BeanPostProcessor后处理bean，执行postProcessBeforeInitialization，可以在初始化之前执行一些方法**

    > **6.如果bean实现了InitializingBean接口，则执行afterPropertiesSet，执行属性设置之后的操作**

    > **7.调用<bean　init-method="">执行指定的初始化方法**

    > **8.如果存在类实现BeanPostProcessor则执行postProcessAfterInitialization，执行初始化之后的操作**

    > **9.执行自身的业务方法**
    >
    > ​	从这里开始的后面两步，是针对单例模式的，针对于多例模式的Bean，IOC容器不做管理

    > **10.如果bean实现了DisposableBean接口，则执行spring的的销毁方法**

    > **11.调用<bean　destory-method="">执行自定义的销毁方法。**

- Bean的覆盖

  - 默认情况: 同一个配置文件中出现id相同的bean会报错

    ​                 不同的配置文件出现id相同的bean  后加载的bean会将先加载的bean覆盖掉

    ​	          称为bean的覆盖

    bean的覆盖不会报错，但可能影响我们的项目 ， 可以通过属性设置 不允许bean的覆盖

    **allowBeanDefinitionOverriding**设置为false

- Bean的作用域有哪些？

  - ![1649732557216](C:\Users\dell\AppData\Roaming\Typora\typora-user-images\1649732557216.png)

- 两个bean互相依赖，会产生循环依赖问题吗？

  - 如果对象都是多例对象 会报循环依赖异常
  - 如果是单例对象:
  - ​          如果是通过构造器依赖的属性, 会报循环依赖异常
  - ​          如果是通过属性依赖产生的循环依赖, 默认允许循环依赖
    - 其实就是利用一个早期对象的概念，将早期还没有装配的对象导入需要的类中实现DI，装配前这个早期对象会存储在二级缓存中
      - 为什么是三级而不是二级，二级是可以解决的，三级是为了处理一些不是原生的类似拥有事务的方法，考虑更多的使用场景
  - ​          设置allowCircularReferences为false 会报循环依赖异常

- 谈谈自己对于IOC和`AOP`的理解

- ```
  答题技巧：以一个总分的结果来回答
  总：当前问题回答的是哪些具体的点
  分：以1,2,3,4,5的方式具体分细节去描述相关的知识点，如果有哪些点不清楚，直接忽略过去
  在聊的时候突出一些技术名词（核心概念，接口，类，关键方法）
  ```

  - ```
    总：
    SpringIOC，主要涉及的是两个概念
    IOC：Inversion Of Control，控制反转思想，原来的对象是由使用者来进行控制，有了Spring之后，可以把整个对象交给Spring来帮我们进行管理
    	DI：Denpendency Injection，依赖注入，把对应的属性的值注入到具体的对象中，例如通过@Autowired，populateBean完成属性值的注入
    容器：存储对象，使用Map结构存储，在Spring中一般存在三级缓存，例如一个使用场景更普遍的Map集合singletonObjects存放完整的bean对象，整个Bean的生命周期，从创建到使用到销毁的过程全部都是由容器来管理【这里会带出一个Bean的生命周期的概念，可以体现个人的技术优势】
    分：
    1.一般聊IOC容器的时候要涉及到容器的创建过程（BeanFactory，DeafultListableBeanFactory），容器的创建是通过实现BeanFactory这个顶级接口来进行的，实际的调用过程中使用的最普遍的就是一个叫做DeafaultListableBeanFactory的核心容器实现类，DefaultListableBeanFactory中有两个Map属性，一个负责存放Bean的描述信息，就是对象是怎么定义的，一个是存放Bean的实例对象的集合
    
    2.加载解析Bean对象，准备要创建的Bean对象的定义对象beanDefinition（XML，或者注解的解析过程）
    
    3.这个时候如果咱们的Bean实现了BeanFactoryPostProcessor接口，这个接口是Spring留给我们来进行扩展的
    	BeanFactoryPostProcessor允许我们在实例化Bean之前读取元数据进行修改，比如讲其从singleton改成prototype，也可以实现多个，通过order属性来控制执行的顺序，内置的实现类有例如ConfigurationClassPostProcessor
    	
    4.BeanPostProcessor接口，如果实现了，可以在spring容器实例化bean之后，在执行bean的初始化方法前后，扩展一些功能
    	》1初始化方法可以通过bean实现了InitializingBean接口，执行了afterPropertiesSet，这个方法是执行属性设置之后的操作
    	》2或者在定义时直接指定Bean的初始化方法
    	BeanPostProcessor的after的方法是会在这两个方法执行后再执行
    	
    5.然后执行Bean的业务
    
    6.如果bean实现了DisposableBean接口，则执行spring的的销毁方法
    	或者在配置文件中类似初始化的方法一样实现一个destroy方法
    	
    ```
    
    - Spring解决循环依赖问题
    - A实例化（）→B实例化→A半实例对象→B实例（含有A半实例对象）→A实例（B实例）
    
  - 控制反转，将创建和管理对象的事情交给Spring工厂，反射创建对象，解除耦合，满足开闭原则（打开扩展，关闭修改），配置Bean的方式有两种，分别是基于注解的`AnnotationConfigApplicationContext`和基于Xml的`ClassPathXmlApplicationContext`，	获取Bean实例是通过`DefaultListableBeanFactory`这个核心的`BeanFactory`实现类，`DefaultListableBeanFactory`中有两个Map属性，一个负责存放Bean的描述信息，就是对象是怎么定义的，一个是存放Bean的实例对象的集合

    - 基于Xml进行DI，是需要在`ClassPath`文件夹下创建applicationContext.xml，并在其中进行我们要放入IOC容器的<bean>标签的配置
      
      - 注意点，<scope>配置Bean属性为单例（singleton，每次获得对象都是这一个）还是原型（prototype）
    - 基于配置类导入，可以创建一个配置类，然后通过`AnnotationConfigApplicationContext`载入
      - 注意点，基于注解可以进行配置scope属性等
      - 上图中是不会允许destory的方法执行的，因为创建了多例就不归容器管了，只有单例才能控制destory进行执行
      
      - 父容器的概念是为了扩展的，整合框架时不同的框架引用不同的Bean，然后子容器可以访问父容器的Bean，但是父容器不能访问子容器的Bean
      - 为什么会提前初始化单例对象，是因为单例对象需要一直维护，毕竟我们每次使用的时候都是原来的对象
    
  - 面向切面，在已有的业务代码的基础上做前后的功能加强，基于动态代理实现

    - 使用方式？
      
      - 定义切面类，@Aspect`@Component`
      - 定义切入点表达式
      - 定义通知：前置，后置，异常，最终，环绕
      
    - 使用场景

      - 日志收集
      - 数据库读写分离，如果是读类型的sql，切换到读库，如果是写类型的sql，切换到写库

    - 动态代理主要指两种代理方式，JDK动态代理以及`Cglib`动态代理，JDK动态代理是基于接口实现的，Cglib则是基于原类是否可以被继承来实现

    - 静态代理的问题是，随着开发项目的扩大，数量成倍增长，不利于管理，导致额外功能维护性差，修改复杂麻烦

    - 
      
    - ```
      //jdk动态代理，都需要目标类实现接口
      public interface UltraManSell {
          float UltraManSell(int amount);
      }
      //目标类，定义里面的方法
      public class UltraFactory implements UltraManSell {
          @Override
          public float UltraManSell(int amount) {
              System.out.println("奥特曼工厂发送了一个奥特曼给商店");
              return 25.0f;
      }
      /**
       * jdk动态代理实现代理功能的关键类，InvocationHandler
       */
      public class ShopHandler implements InvocationHandler {
          //定义一个Object来实现动态代理任何目标类
          private Object target;
          //创建Target的构造方法，用于InvocationHandler的invoke导入代理的目标类
          public ShopHandler(Object target) {
              this.target = target;
          }
          /**
           *
           * @param proxy jdk创建的代理对象，无需赋值，不需要你管
           * @param method 目标类的方法
           * @param args 目标类的方法的参数
           * @return
           * @throws Throwable
           */
          @Override
          public Object invoke(Object proxy, Method method, Object[] args) throws Throwable {
              Object ret = method.invoke(target, args);
              if(ret!=null){
                  System.out.println("商家进行了加价");
                  Float price = (Float) ret;
                  price=price+5;
                  ret=price;
              }
              return ret;
          }
      }
      /**
       * main
       */
      public class Leem {
          public static void main(String[] args) {
              System.out.println("准备买个奥特曼");
              UltraManSell ultraFactory = new UltraFactory();
              ShopHandler shopHandler = new ShopHandler(ultraFactory);
              UltraManSell dynamicProxy = (UltraManSell) Proxy.newProxyInstance(ultraFactory.getClass().getClassLoader(), ultraFactory.getClass().getInterfaces(), shopHandler);
              float v = dynamicProxy.UltraManSell(1);
              System.out.println("买了一个奥特曼，价格："+v);
          }
      }
      ```

- 事务的失效场景
  - 数据库引擎不支持事务
  - 没有被Spring管理
    - Spring注解没加
  - *方法不是Public的
  - *自身调用问题
    - 没有加事务的方法调用了加了事务的方法，事务是不会生效的，事务的生效要Spring帮忙创建代理对象，没有加事务Spring没办法帮忙
  - 数据源未配置事务管理（TransactionManager）
  - 传播行为中设置了不支持事务
  - *异常被捕获掉（重点☆☆）
    - 事务捕获的异常默认的是RunTimeException，但是我们抛的是Exception不属于运行时异常，比运行时异常要大，这个时候事务就无法捕获这个异常
    - 所以我们往往会在事务注解中配置捕获异常的范围（rollbackFor = Exception.class）
  - *异常错误类型，默认捕获RuntimeException异常

- 事务的传播行为（7种，只需记REQUIRED和REQUIRED_NEW）

| 传播行为                     | 含义                                                         |
| ---------------------------- | ------------------------------------------------------------ |
| **PROPAGATION_REQUIRED**     | 表示当前方法必须运行在事务中。如果当前事务存在，方法将会在该事务中运行。否则，会启动一个新的事务 |
| **PROPAGATION_SUPPORTS**     | 表示当前方法不需要事务上下文，但是如果存在当前事务的话，那么该方法会在这个事务中运行 |
| PROPAGATION_MANDATORY        | 表示该方法必须在事务中运行，如果当前事务不存在，则会抛出一个异常 |
| **PROPAGATION_REQUIRES_NEW** | 表示当前方法必须运行在它**自己的事务中**。一个新的事务将被启动。如果存在当前事务，在该方法执行期间，当前事务会被挂起。 |
| PROPAGATION_NOT_SUPPORTED    | 表示该方法不应该运行在事务中。如果存在当前事务，在该方法运行期间，当前事务将被挂起。如果使用JTATransactionManager的话，则需要访问TransactionManager |
| PROPAGATION_NEVER            | 表示当前方法不应该运行在事务上下文中。如果当前正有一个事务在运行，则会抛出异常 |
| PROPAGATION_NESTED           | 表示如果当前已经存在一个事务，那么该方法将会在嵌套事务中运行。嵌套的事务可以独立于当前事务进行单独地提交或回滚。如果当前事务不存在，那么其行为与PROPAGATION_REQUIRED一样。注意各厂商对这种传播行为的支持是有所差异的。可以参考资源管理器的文档来确认它们是否支持嵌套事务 |

- 什么是事务及事务的特性？

  - 事务 指的是对数据库进行一系列操作的sql语句，要么全部成功，要么全部失败，需要满足ACID四个特性。
    在数据库中，指的是一个操作由一系列`spl`组成，这些`spl`看成一个整体，要么全部成功，要么全部失败。

    数据库中的事务满足ACID的特性
    原子性（Atomicity），操作这些指令时，要么全部执行成功，要么全部不执行。
    一致性(Consistency)，一致性是指事务必须使数据库从一个一致性状态变换到另一个一致性状态。

    持久性（Durability），一个事务一旦被提交了，那么对数据库中的数据的改变就是永久性的。

    隔离性(Isolation) ，比如操作同一张表时，事务不能被其他事务的操作所干扰，多个并发事务之间要相互隔离。

    - 读未提交，什么都不能解决

    - 读已提交，解决脏读（**脏读就是A和B查看一个数据，A修改了，在提交这个数据前，B读取了这个数据，与提交后的数据产生了不一致**）

    - 可重复读，解决脏读和不可重复读（**不可重复读是指在事务1内，读取了一个数据，事务1还没有结束时，事务2也访问了这个数据，修改了这个数据，并提交。紧接着，事务1又读这个数据。由于事务2的修改，那么事务1两次读到的的数据可能是不一样的，因此称为是不可重复读。**）

    - 串行化，要求所有事务串行处理，不能并行，解决脏读、不可重复读和幻读（**所谓幻读，指的是当某个事务在读取某个范围内的记录时，另外一个事务又在该范围内插入了新的记录，当之前的事务再次读取该范围的记录时，会产生幻行。InnoDB存储引擎通过多版本并发控制（MVCC）解决了幻读的问题**）
    
      - **注意：不可重复读和幻读的区别是：前者是指读到了已经提交的事务的更改数据（修改或删除），后者是指读到了其他已经提交事务的新增数据。**
        **对于这两种问题解决采用不同的办法，防止读到更改数据，只需对操作的数据添加行级锁，防止操作中的数据发生变化；而防止读到新增数据，往往需要添加表级锁，将整张表锁定，防止新增数据（oracle采用多版本数据的方式实现）。**
    
    - | 隔离级别                                   | 含义                                                         |
      | ------------------------------------------ | ------------------------------------------------------------ |
      | ISOLATION_DEFAULT（可重复读）              | 使用后端数据库默认的隔离级别                                 |
      | ISOLATION_READ_UNCOMMITTED                 | 最低的隔离级别，允许读取尚未提交的数据变更，可能会导致脏读、幻读或不可重复读 |
      | ISOLATION_READ_COMMITTED                   | 允许读取并发事务已经提交的数据，可以阻止脏读，但是幻读或不可重复读仍有可能发生 |
      | ISOLATION_REPEATABLE_READ（Mysql默认级别） | 对同一字段的多次读取结果都是一致的，除非数据是被本身事务自己所修改，可以阻止脏读和不可重复读，但幻读仍有可能发生 |
      | ISOLATION_SERIALIZABLE                     | 最高的隔离级别，完全服从ACID的隔离级别，确保阻止脏读、不可重复读以及幻读，也是最慢的事务隔离级别，因为它通常是通过完全锁定事务相关的数据库表来实现的 |
    

##### SpringBoot：

- 自动装配：

  - ```java
    @SpringBootApplication：引入此注解开启动一个SpringBoot项目
    ↓点进去
    @SpringBootConfiguration
    	@Configuration：说明启动类也是个配置类
    		@Component：说明配置类也是Spring的一个组件
    @EnableAutoConfiguration：自动配置
    ↓点进去
    @AutoConfigurationPackage：自动配置包
    	@Import(AutoConfigurationPackages.Registrar.class)：自动配置包注册器
    @Import(AutoConfigurationImportSelector.class)：自动配置导入选择器
    ↓点进去
    getAutoConfigurationEntry()：获取自动配置项
    ↓调用同级方法
    getCandidateConfigurations()：获取核心配置
    ↓引用SpringFactoriesClassLoader的方法
    loadFactoryNames()：加载工厂名称
    ↓内置方法
    loadSpringFactories(ClassLoader classLoader)：加载Spring工厂
    ↓具体加载项
    ClassLoader.getSystemResources(FACTORIES_RESOURCE_LOCATION)：加载META-INF/spring.factories信息，实现自动装配
    	public static final String FACTORIES_RESOURCE_LOCATION = "META-INF/spring.factories";
    loadProperties(resource)：路径封装成Properties遍历导入达成条件的配置类
    
    点击spring.factories里的value：
    @ConditionalOnClass({ CqlSession.class, ReactiveCassandraTemplate.class, Flux.class })：通过添加注解判断是否满足再自动注入.
    ```

  - 

  - <img src="asserts\watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L20wXzU2MzU2OTkz,size_16,color_FFFFFF,t_70" alt="img"  />
  
  - 自定义Starter
    
    - Configuration+Spring.factories

##### SpringSecurity：

 Shiro与SpringSecurity的区别？
  - Shiro 本身是⼀个⽼牌的安全管理框架，有着众多的优点，例如轻 量、简单、易于集成、可以在JavaSE境中使⽤等。不过，在微服 务时代，Shiro 就显得⼒不从⼼了，在微服务⾯前和扩展⽅⾯，⽆法充分展示⾃⼰的优势。

  - Spring Security,作为spring 家族的⼀员，在和 Spring 家族的其他成员如 Spring Boot Spring Clond等进⾏整合时，具有其他框架⽆可⽐拟的优势，同时对 OAuth2 有着良好的⽀持，再加上Spring CloudSpring Security的不断加持（如推出 Spring Cloud Security )，让Spring Securiy 不知不觉中成为微服务项⽬的⾸选安全管理⽅案。

 SpringSecurity的整体架构？

  - ![1654914068711](asserts\1654914068711.png)

    - **AuthenticationManager**接口负责了SpringSecurity的认证功能，AuthenticationManager 主要实现类为 ProviderManager，在 ProviderManager 中管理了众多 AuthenticationProvider 实例。在⼀次完整的 认证流程中，Spring Security 允许存在多个 AuthenticationProvider ，⽤来 实现多种认证⽅式，这些 AuthenticationProvider 都是由 ProviderManager 进⾏统⼀管理的。

    - Authentication认证以及认证成功的信息主要是由 Authentication的实现类进⾏保存的，其 

      接⼝定义为![1654914425150](asserts\1654914425150.png)

      - getAuthorities 获取⽤户权限信息
      - getCredentials 获取⽤户凭证信息，⼀般指密码
      - getDetails 获取⽤户详细信息
      - getPrincipal 获取⽤户身份信息，⽤户名、⽤户对象等
      - isAuthenticated⽤户是否认证成功

    - **SecurityContextHolder**⽤来获取登录之后⽤户信息。Spring Security会将登录⽤户数据保存在Session 中。但是，为了使⽤⽅便,Spring Security在此基础上还做了⼀些改进，其中最主要的⼀个变化就是线程绑定。当⽤户登录成功后,Spring Security会将登录成功的⽤户信息保存到 SecurityContextHolder中。SecurityContextHolder中的数据保存默认是通过ThreadLocal来实现的，使⽤ThreadLocal创建的变量只能被当前线程访问，不能被其他线程访问和修改，也就是⽤户数据和请求线程绑定在⼀ 起。当登录请求处理完毕后，Spring Security 会将 SecurityContextHolder 中 的数据拿出来保存到 Session 中，同时将 SecurityContextHolder 中的数据清 空。以后每当有请求到来时，Spring Security 就会先从 Session中取出⽤户登录数据，保存到SecurityContextHolder 中，⽅便在该请求的后续处理过程中使⽤，同时在请求结束时将 SecurityContextHolder 中的数据拿出来保 存到 Session中，然后将Security SecurityContextHolder中的数据清空。这⼀策略⾮常⽅便⽤户在 Controller、Service层以及任何代码中获取当前登录⽤户数据。

    - **AccessDecisionManager** (访问决策管理器)，用来决定此次访问是否被允许

    - **AccessDecisionVoter** (访问决定投票器)，投票器会检查⽤户是否具备应 

      有的⻆⾊，进⽽投出赞成、反对或者弃权票。AccesDecisionVoter 和 AccessDecisionManager 都有众多的实现类，在 AccessDecisionManager中会换个遍历 AccessDecisionVoter，进⽽决定是否允许⽤户访问，因⽽ AaccesDecisionVoter 和 AccessDecisionManager 两者的关系类似于AuthenticationProvider 和 ProviderManager 的关系。

    - **ConfigAttribute**，在 Spring Security 中，⽤户请求⼀个资源(通常是⼀个接⼝或者⼀个Java⽅法)需要的⻆⾊会被封装成⼀个 ConfigAttribute 对象，在ConfigAttribute 中 只有⼀个 getAttribute⽅法，该⽅法返回⼀个 String 字符串，就是⻆⾊的名称。⼀般来说，⻆⾊名称都带有⼀个 ROLE_ 前缀，投票器 AccessDecisionVoter 所做的事情，其实就是⽐较⽤户所具各的⻆⾊和请求某个资源所需的 ConfigAtuibute 之间的关系。
    

SpringSecurity的原理？

  - 在 Spring Security 中 认证、授权等功能都是基于**过滤器**完成的

  - Spring Security 提供了 30 多个过滤器。默认情况下Spring Boot在对 Spring Security 进⼊⾃动化配置时，会创建⼀个名为SpringSecurityFilerChain 的过滤器，并注⼊到 Spring 容器中，这个过滤器将负责所有的安全管理，包括⽤户认证、授权、重定向到登录⻚⾯等。具体可以参考WebSecurityConfiguration的源码:![1654929502848](asserts\1654929502848.png)

    ![1654929535535](asserts\1654929535535.png)

  - 在引入SpringSecurity时，**SpringBootWebSecurityConfiguration**是默认对所有请求进行拦截的

    - ![1654929708530](asserts\1654929708530.png)

  - 涉及认证登录页面时，SpringSecurity会加载默认的登录页面并加载默认的用户数据，即通过**UserDetailService**通过刚才源码分析也能得知 UserDetailService 是顶层⽗接⼝，接⼝中loadUserByUserName ⽅法是⽤来在认证时进⾏⽤户名认证⽅法，默认实现 使⽤是**内存实现**，如果想要修改数据库实现我们只需要⾃定义UserDetailService 实现，最终返回 UserDetails 实例即可。默认情况下都会满⾜，此时**Spring Security**会提供⼀个**InMemoryUserDetailManager **实例

    ![1654932081563](asserts\1654932081563.png)

    ![1654932120975](asserts\1654932120975.png)

    **这就是默认⽣成** user **以及** uuid **密码过程**! **另外看明⽩源码之后，就知道只** 

    **要在配置⽂件中加⼊如下配置可以对内存中⽤户和密码进⾏覆盖。**

    ![1654932150158](asserts\1654932150158.png)


 什么是自定义认证？如何进行？

  - 自定义认证就是现在网站通用的认证，都是自定义的，SpringSecurity内置的登录界面无法达成企业的需要和定制化的返回一些信息，所以大多数企业采用自定义认证的方式进行登录认证
  - **一般自定义会从登录界面、权限规则、成功失败处理、数据源以及验证码功能等方面进行自定义**

 SpringSecurity中有对密码安全的解决方案吗？

  - 内置PassWordEncoder，采用Bcrypt等单向自适应函数算法来保证密码安全，这种⾃适应单向函数在进⾏密码匹配时，会**有意占⽤⼤量系统资源**（例如CPU、内存等），这样可以**增加**恶意⽤户攻击系统的**难度**。

什么是OAuth2?Spring Security支持吗？
  - 一个用于**解决小型企业与用户之间的信任协议**，即我们登录一些小的app或网站时可以通过微信进行登录或者是微博进行登录

  - 支持的，对其进行了整合，通用的场景是结合JWT一起实现第三方登录

如何保证JWT的token令牌不被篡改? (或token的组成)

- `json` web token由header（加密算法+token类型）+`payLoad`（失效时间+用户信息）+**signature**签名组成（加密算法(header + "." + `payLoad`+秘钥) == 签名     防止token被篡改）

JWT的token令牌能否保证数据安全?

- 不保证 `http`==>`https`

理解认证和授权？

- 认证和授权，就像是一个国家的众多领导人一样，有一个册子里面，记录了领导人的姓名，类似通过核对领导人的姓名来证明用户的行为，就是认证，即对方是否为合法的领导人，而授权，则是针对领导人职务的不同，对应享有的权力则不同，即授权下的用户的可访问的相应资源

##### Kafka:

- 介绍一下Kafka？
  - 是一个Apache开源的消息中间件，与`RabbitMQ`&`RocketMQ`齐名，Scale语言开发
- Kafka的应用场景是什么？有什么作用？
  - 应用解耦（需要处理的消息存放在队列中，微服务故障或扩展处理方便）
  - 异步通信（将返回不需要等待结果的消息异步处理，提升效率）
  - 流量削峰（将服务器无法承载的消息存储在队列中，维持服务高可用）
  - 消息分发（针对性的对服务器分发有需要的消息，避免资源的浪费）
- Kafka如何保证高可用？
  - 搭建Kafka分布式集群
  - 对不同的Topic消息在多个服务器里分配多个分区来增加其伸缩性
  - 对各个分区进行副本备份，leader&follower，主分区宕机选择副分区为leader保证高可用
- Kafka如何保证消息的顺序消费？
  - 首先要保证消息发送时至少指定了分区或者key，因为不指定，消息发送就会轮询
    - 指定分区后，因为分区里面的消息默认是有序的，这样就实现顺序消费
    - 指定key也可以，通过key进行hash运算对分区数量取模，得到分区下标
- Kafka如何保证消息的可靠性？
  - 首先确保生产者把消息发送到了服务器
    - 同步发送：效率慢，有重试机制；异步发送：效率快，失败不重试
    - 消息发送确认机制（`acks`），在消息发送后Kafka会给生成者响应一个消息
      - `acks`=0，队列不给生成者响应，这样不具备可靠性，消息丢失不知道，可靠性最低，效率最高
      - `acks`=1，队列的主分区收到消息即给生成者进行响应，可靠性居中，效率居中
      - `acks`=all，队列的所有分区收到消息后才给生成者响应，可靠性最高，效率较低
  - 再确保服务器不丢失消息
    - Kafka会将消息持久化到磁盘中，7天
    - 为了保证效率，Kafka默认先存放在内存中，然后刷盘进磁盘，可以通过设置刷盘效率来提高可靠性（减少刷盘前宕机丢失的消息数），但是性能也会变低
  - 最后确保消费者消费到了消息
    - 关闭Kafka的消费者自动提交偏移量机制，进行手动提交，自动提交会产生重复消费和消息丢失的问题
      - 重复消费：当消费者拉取了10个数据进行消费，消费到第5个宕机了，这时候消费者重平衡，新的消费者还会从第一个开始消费
      - 消息丢失：当提交偏移量的时间到了但是消息还没消费完的时候，此时消费者宕机，下一个消费者会丢失那些未完成的消息
    - 手动提交分为同步和异步，采用项目运行`ok`时同步来保证效率，异常时采用异步来保证可靠性
- Kafka如何保证消息的幂等性？
  - 基于`redis`解决：
    - 处理消息之前，先查询`redis`查看该消息是否被处理过
    - 没处理过，处理消息，并为其生成一个唯一的token
    - 处理过，不再处理该消息
- 如何处理消息积压的问题？
  - 将堆积的消息通过消费者重新发送到新建的多个分区（依可分配的机器数量而定）中，再创建多个临时消费者（依可分配的机器数量而定）来快速消费这些消息
  - 如果涉及消息的延时及过期，只能搜索历史记录重新导入再消费
- Kafka Streams？
  - 一个大数据的处理技术，处理存放在kafka中的消息，以想要的业务的数据格式的方式输出
  - 时间窗口的概念
    - 在处理流数据时，多久去处理这些数据就是时间窗口，项目中默认使用的是翻滚时间窗口，kafka支持四种时间窗口：翻滚、跳跃、滑动和会话

##### RabbitMq：

- RabbitMq如何保证消息的高可用
  - 普通集群模式(不算分布式，高可用，因为只是在别的节点那里有实际数据的地址而已)
  - 镜像集群模式（高可用，不是分布式的）
    - 开启就是在管理后台开启一个策略，并选择同步消息到所有节点即可
- 什么是延时队列？应用场景？
  - 顾名思义，延迟队列就是进入该队列的消息会被延迟消费的队列。而一般的队列，消息一旦入队了之后就会被消费者马上消费
    - 用户生成订单之后，需要过一段时间校验订单的支付状态，如果订单仍未支付则需要及时地关闭订单
    - 用户注册成功之后，需要过一段时间比如一周后校验用户的使用情况，如果发现用户活跃度较低，则发送邮件或者短信来提醒用户使用
    - 延时重试
- RabbitMq如何保证消息的可靠性？
  - 通过事务来保证，发送数据前开启事务（channel.txSelect），回滚事务（channel.txRollback），提交事务（channel.txCommit），但是这样的机制是阻塞的，不适合高并发场景
  - 通常都使用confirm模式，每次写消息都会分配唯一id，发送成功会传回ack，不成功nack，接收失败也可以重试
  - 发送到rabbitmq中，可以开启磁盘持久化存储消息
    - 两种方式，创建queue的时候设置为持久化，但是这样的方式只会持久化元数据，不会持久化实际数据
    - 发送消息时将deliveryMode（发送模式）设置为2，这种模式就是磁盘存储的方式
  - ack提交采用手动提交，关闭自动提交
- RabbitMq如何保证消息的顺序性？
  - 添加多个queue并将需要顺序消费的消息添加至一个queue中

##### Mybatis：

- Spring如何整合Mybatis（核心3类）【普适导航】

  - 1.MapperScannerConfigurer实现了beanDefinitionRegistryPostProcessor的postProcessBeanDefinitionRegistry方法

    从指定的 basePackage的目录递归搜索接口，将它们注册为MapperFactoryBean

  - 2.SqlSessionFactoryBean实现了InitializingBean的afterPropertiesSet，在其中创建了Mybatis的SqlSessionFactory

    实现了FactoryBean的getObject 返回创建好的sqlSessionFactory

  - 3.MapperFactoryBean实现了InitializingBean的afterPropertiesSet方法，将mapper接口设置到mybatis的配置中

    实现了FactoryBean的getObject 方法，调用了sqlSession.getMapper，返回mapper对象

- Mybatis一级缓存和二级缓存的概念【新核云】

  - 一级缓存：一级缓存的范围是同一个SqlSession对象，当我们使用SqlSession对象进行查询时mybatis会帮我们把查询的数据存入到内存中，当我们在这个SqlSession中再一次执行同样的查询操作时，我们就可以直接去缓存中获取数据
  - 二级缓存：二级缓存是mapper级别的缓存，多个SqlSession共享，其作用域是mapper的同一个namespace，不同的SqlSession两次执行相同的namespace下的sql语句，且向sql中传递的参数也相同，即最终执行相同的sql语句，则第一次执行完毕会将数据库中查询的数据写到缓存（内存），第二次查询时会从缓存中获取数据，不再去底层数据库查询，从而提高查询效率

- Mybatis分页插件的原理【新核云】

  - 基于PageHelper实现分页， 就是在StatementHandler之前进行拦截，对MappedStatement进行一系列的操作（大致就是拼上分页sql）

##### GateWay：

```yaml
server:
  port: 6001
spring:
  application:
    name: leadnews-admin-gateway
  cloud:
    nacos:
      discovery:
        server-addr: 192.168.200.130:8848
    gateway:
      globalcors:
        cors-configurations:
          '[/**]': # 匹配所有请求
            allowedOrigins: "*" #跨域处理 允许所有的域
            allowedMethods: # 支持的方法
              - GET
              - POST
              - PUT
              - DELETE
      routes:
        # 平台管理
        - id: admin
          uri: lb://leadnews-admin
          predicates:
            - Path=/admin/**
          filters:
            - StripPrefix= 1
        - id: user
          uri: lb://leadnews-user
          predicates:
            - Path=/user/**
          filters:
            - StripPrefix= 1
        - id: wemedia
          uri: lb://leadnews-wemedia
          predicates:
            - Path=/wemedia/**
          filters:
            - StripPrefix= 1
```

Feign:

```java
@FeignClient(
        //对应的服务
        value = "leadnews-admin",
        //服务降级类
        fallbackFactory = AdminFeignFallback.class,
        //Feign配置类，打印异常日志
        configuration = HeimaFeignAutoConfiguration.class
)
public interface AdminFeign {
    @GetMapping("/api/v1/channel/channels")
    ResponseResult<List<AdChannel>> selectAllChannel();
}
```



#### 熟悉关系数据库原理，熟练使用关系型数据库Mysql，及 Nosql 数据库 MongoDB、Redis、ES（调优）

##### Mysql：

- Mysql的工作模式？
  
  - 运行时，在系统的内存中建立一个mysql server服务端，执行sql语句时，从硬盘中查询数据并加载到内存中（磁盘IO），磁盘IO是非常消耗性能的，如何降低IO的次数就是优化的关键
  
- Mysql的索引的底层数据结构？

  - 主要是基于hash（个别的引擎使用，缺点是受hash冲突影响，并且只能用于单行数据的查询）和B+Tree（我们常用的引擎，InnoDb+MYISAM）

- 为什么要使用B+Tree，不使用其它的数据结构比如二叉树呢？`BTree`呢？

  - 二叉树每个节点只能存一个数据并且只有两个叉，会因为数据量的递增不断变高，变高就意味着磁盘IO次数增多的可能性不断增多，所以我们对于Mysql的索引结构，我们需要它产生一颗矮胖的树，而不是瘦高的树
  - `BTree`中拥有Degree（度）和自平衡的概念，度代表了`BTree`中每个节点可以存放的索引数，**度越大则索引树就越矮胖**，并且`BTree`中数据和索引是放在一起的，而**B+Tree**的思想，是将叶子节点中的数据全部存储在最底层，磁盘在IO时，硬件的扇区扫描树的节点，在节点中没有了数据之后，度的空间就会更大，树会更加矮胖，IO次数也更低，在最底层存储的数据B+Tree还引入了顺序指针，使得底部的数据是有序的

- MYISAM和InnoDB的区别？

  - |          |   MyISAM   | innoDB         |
    | -------- | :--------: | -------------- |
    | 事务     |   不支持   | 支持           |
    | 外键     |   不支持   | 支持           |
    | 锁       |    表锁    | 行锁           |
    | 缓存     |  缓存索引  | 缓存索引和数据 |
    | 索引实现 | 非聚簇索引 | 聚簇索引       |

  - 理解聚簇与非聚簇

    - MYISAM在创建数据库时，索引和数据是分开存储的，MYD（data）和MYI（index），索引中记录磁盘地址，通过磁盘地址去磁盘中找到数据
    - 聚簇是直接存的数据，并且，当我们生成表时，即使不指定主键，也没有索引，InnoDB也会生成一个隐藏的row_id来生成一颗B+Tree，当不指定索引时但是有主键时，会根据主键默认生成一颗B+Tree，当指定了多个非主键索引时，会相应产生多颗树，但是相对的，最终的查询是落在主键索引上的，其它的索引数挂的值，是主键索引的id
    
  - 什么是索引？
  
    - 一种数据结构，帮我们提升查询数据的效率
  
  - 索引为什么能够提升查询效率？
  
    - 采用了B+Tree的数据结构，降低查询数据时的磁盘IO次数
  
  - 索引的分类
  
    - 普通索引，给某个字段建立一个普通的索引，也就是建立一颗B+Tree，功能是加速查找
    - 唯一索引，分为主键索引（唯一且不为空）和唯一索引（唯一，可以为空）
    - 联合索引，对几个字段建立一个共同的索引
    - 全文索引，用于检索很长的文章，但是性能比不上ES（在海量的数据检索场景下）
  
  - 怎么创建索引？
  
    - 客户端设计表添加索引
    - CREATE 什么类型的 INDEX 索引名 ON 表名（字段（长度））
    - 有一个注意点就是，索引的创建最好在设计表之初就决定，因为如果等到我们的数据增加到百万级别以上，我们再去为某个表的某些字段创建索引时，就要等到很久，因为这个时候Mysql需要去为每个数据创建索引，这是很耗费时间的
  
  - 怎么查看索引？
  
    - SHOW INDEX FROM 表名
  
  - 删除索引？
  
    - DROP INDEX（索引名） ON 表名
  
  - 最左匹配原则是什么？
  
    - 最左匹配原则是针对联合索引的一个规范，我们在建立索引时，索引的字段从左到右，是123，我们查询的条件中只要都存在这三个条件，那就可以生效，但是如果条件是13或者31，在123中从最左的1开始往右匹配时2是不存在的，则3失效，同理23或者32，都失效，因为从左开始的1不存在
    - 有一个注意点就是最左匹配原则中，如果我们查询的索引进行了范围查询，那么这个索引本身是生效的，但是其右侧的所有索引会失效
  
  - 索引的缺点？
  
    - 索引文件会占用物理空间
    - 对表的数据进行增删改时，索引也需要动态维护，降低了数据的维护速度
  
  - 什么样的字段适合建立索引？哪些不适合？
  
    - 适合的：主键，频繁作为查询条件的字段，与其它表关联的字段，排序的字段，分组的字段
    - 不适合的：数据量少的表，查询用不到的字段，经常增删改的表，数据重复多的字段，字段特别大的字段
  
  - 如何进行sql性能优化？
  
    - 主要使用Explain来分析sql的执行情况
  
      - 得到**表的查询顺序**（id）、**访问类型**（type）、**索引名**、**额外信息**（extra）等信息，检查表查询顺序看是不是小表驱动大表，分析sql的业务场景对访问类型处于index和all的查询进行优化
  
      -  访问类型排列	
  
        结果值:(最好到最差) system > const > eq_ref > ref > range > index > ALL（没有用到索引必须要优化），最好能够优化到range以上，但是有些场景我们只查询了索引键，索引就只能是index的访问类型
  
        **我们可以借助于查询全部索引来建立小表，然后基于这个小表查询大表，来达到sql优化的目的**
  
      - extra：额外信息字段
  
        - Using where:using tempory - > group by，分组未指定索引，需要建立临时表存储数据
    - Using where:using filesort - >order by，排序未指定索引，需要建立临时表存储数据
      
      - 当数据量大时，耗时
      
    - 也借助Mysql的慢查询日志功能，超过我们设置的查询时长的语句会出现在日志中，这个日志都会在可视化的页面里进行追踪和查看
  
  - union关键字的使用
  
    - 可以将查询结果合并成一个表，但前提是两个或多个查询的字段要一致
  
  - 如何避免索引失效？
  
    - 最左匹配原则+范围条件右边的索引失效
    - 不在索引上做任何操作
    - 使用（!=,<,>）致索引失效
    - is not null无法使用索引
    - like以通配符开头（'%x'）索引失效
    - 字符串不加引号索引失效
    - or连接不是索引的字段导致索引失效
    - 尽量使用覆盖索引
  
  - 有过索引优化的经验么？
  
    - 嗯有的，但是也没写过太多复杂的sql语句，我们做的都是微服务，我之前有用覆盖索引和给排序字段建立索引的方式，简单的优化了一下当时我们从几百万的用户里面检索一些用户信息的场景，就之前公司有近三个月的用户信息做抽检统计的需求。相当于从第几十万条那边抽检几十条的操作，然后那个时候之前的同事的sql脚本每次检索都要`13s`左右，我看了一下发现条件上没用到索引，然后尝试使用**覆盖索引+给排序字段索引**优化了到`1s`左右，感觉还可以，但是实现方式很简单
    - 关联查询时，一定要用**小表驱动大表**的操作，left join左边的表是驱动表，right join右边的表是驱动表
    - select聚合函数时，尽量使用索引字段作处理
  
  - 表的优化？
  
    - 选择表合适存储引擎
    - 尽量设计所有字段都得有默认值,尽量避免null值导致索引失效。
    - 字段类型采用尽可能小的类型，例如身份证号或者邮政编码这种长度是固定的字段类型可以由varchar(255)改成char(6)【char不可变长度，varchar可变长度】
  
  - 事务的并发问题
  
    - 1、脏读：事务A读取了事务B更新的数据，然后B回滚操作，那么A读取到的数据是脏数据
    - 2、不可重复读：事务 A 多次读取同一数据，事务 B 在事务A多次读取的过程中，对数据作了更新并提交，导致事务A多次读取同一数据时，结果 不一致。
    - 3、幻读：系统管理员A将数据库中所有学生的成绩从具体分数改为ABCDE等级，但是系统管理员B就在这个时候插入了一条具体分数的记录，当系统管理员A改结束后发现还有一条记录没有改过来，就好像发生了幻觉一样，这就叫幻读。
  
  - 锁的分类
  
    - ```java
      按操作分
      	读锁(共享锁)
      		加了读锁,   其他的进程也可以进行读操作，但写操作会阻塞，所以称为共享锁，是悲观锁
      	写锁(排它锁)
      		加了写锁，  其他的进程读操作和写操作都会进入阻塞状态	
      按粒度分
      	表锁
      		加锁特点：开销小、加锁快，不会出现死锁；锁粒度大，锁冲突高，并发低
      		加锁方式：
      			lock table tableName read; //读锁
      			lock table tableName write; //写锁
      		解锁方式:
      			unlock tables;//释放全部锁
      	行锁
      		开销大，加锁慢；会出现死锁；锁定粒度最小，发生锁冲突的概率最低，并发度也最高。 
      		加锁方式：
      			select * from table where id=1 lock in share mode; //读锁
      			select * from table where id=1 for update; //写锁
      		注意点：加锁的字段必须要是索引字段，不然会自动升级为表锁
      		解锁方式:
              	commit; //提交事务即解锁
      	页锁
      		介于上面两个之间，不用特意阐述
      从思想的层面:
      	悲观锁：
      	看待事情比较悲观， 认为别人会修改它的数据，需要上锁来保证数据的安全
      	
      	select * from employee where id = 1 for update
      	
      	update -- 
      	
      	
      	乐观锁（没有加锁，只是加了个版本号CAS里ABA问题的解决方案）：
      	看待事情比较乐观， 
      	
      	id   name  salary version 
      	1     老王   500     1
      	
         客户端1   
         select * from employee where id = 1    version = 1  
         update employee set salary=2000,version=version+1 where id=1 and version = 1
         
         客户端2   
         select * from employee where id = 1    版本 = 1
         // 修改时1.一定要给版本号+1    2.条件中一定要有版本条件 
         update employee set salary=500,version=version+1 where id=1 and version = 1
         
         
         读操作多 选乐观锁
         写操作多 选悲观锁
      ```
  
    - sql的书写和执行顺序
  
    - ```java
      -- 编写顺序
      select  distinct  查询字段
      from  表名
      JOIN 表名
      ON  连接条件
      where 查询条件
      group by 分组字段
      having 分组后条件
      order by  排序条件
      limit 查询起始位置, 查询条数
      
      ```

##### Seata

- 什么是分布式事务？

  - 在分布式架构中，一个操作可能横跨多个微服务，多个数据库，传统的本地事务无法解决，需要使用分布式事务来解决。

- 什么是CAP？

  - 一个分布式系统里面，节点组成的网络本来应该是连通的。然而可能因为一些故障，使得有些节点之间不连通了，整个网络就分成了几块区域。数据就散布在了这些不连通的区域中。这就叫**分区**。

    当你一个数据项只在一个节点中保存，那么分区出现后，和这个节点不连通的部分就访问不到这个数据了。这时分区就是无法容错的（**P**artition tolerance）。

    提高分区容错性的办法就是一个数据项复制到多个节点上，那么出现分区之后，这一数据项就可能分布到各个区里。容忍性就提高了。

    然而，要把数据复制到多个节点，就会带来一致性（**C**onsistency）的问题，就是多个节点上面的数据可能是不一致的。要保证一致，每次写操作就都要**等待**全部节点写成功，而这等待又会带来可用性（**A**vailability）的问题。

    总的来说就是，数据存在的节点越多，分区容忍性越高，但要复制更新的数据就越多，一致性就越难保证。为了保证一致性，更新所有节点数据所需要的时间就越长，可用性就会降低。

  - CAP无法全部保证，通常只能根据业务选择`CP`或AP的方案，**P**是必须保证的，因为网络故障不可能不发生。

- 什么是BASE理论？

  - 一个`eBay`架构师提出的CAP的理论实现，核心思想就是在保证高可用的同时，根据具体的业务以合适的方式来做到数据的最终一致性，允许过程中出现数据不一致的现象。

- 你们的项目是如何解决分布式事务的问题的？

  - 解决方案：采用了阿里的一个开源的一站式分布式事务框架`seata`

    - `seata`的解决方案：

      - 刚性事务：基于`XA`的二阶段提交（预提交→提交），TC（事务协调者）管着RM（事务参与者，数据表），强一致性且执行时是阻塞的，不适合高并发
      - 柔性事务：
        - `TCC`（try confirm cancel），SAGA（长事务），类似`TCC`，但是只有confirm和cancel两个方法，代码实现不依赖数据库，效率高但侵入性太强；
        - `MQ`+本地消息表+定时器（`xxljob`）+`Redis`，队列存储消息异步执行，效率高（企业优选），但是代码实现复杂且复用性差；
        - **AT**：**无侵入的分布式解决方案，对`TCC`的一种优化，`seata` server+undo_log** **√**

    - Seata管理分布式事务的流程：

      - **TC**：**Transaction Coordinator**，事务协调者。管理全局的分支事务的状态，用于全局性事务的提交和回滚。

      - **TM**：**Transaction Manager**，事务管理者。用于开启、提交或回滚事务。

      - **RM**：**Resource Manager**，资源管理器。用于分支事务上的资源管理，向 **TC** 注册分支事务，上报分支事务的状态，接收 **TC** 的命令来提交或者回滚分支事务。

      - <img src="C:\Users\limingfei\AppData\Roaming\Typora\typora-user-images\image-20210910155622245.png" alt="image-20210910155622245" style="zoom:80%;" />

      - 服务A中的 **TM** 向 **TC** 申请开启一个全局事务，**TC** 就会创建一个全局事务并返回一个唯一的 **XID**

        服务A中的 **RM** 向 **TC** 注册分支事务，然后将这个分支事务纳入 **XID** 对应的全局事务管辖中

        服务A开始执行分支事务

        服务A开始远程调用B服务，此时 **XID** 会根据调用链传播

        服务B中的 **RM** 也向 **TC** 注册分支事务，然后将这个分支事务纳入 **XID** 对应的全局事务管辖中

        服务B开始执行分支事务

        全局事务调用处理结束后，**TM** 会根据有误异常情况，向 **TC** 发起全局事务的提交或回滚

        **TC** 协调其管辖之下的所有分支事务，决定是提交还是回滚

    - 采用AT模式的原因：

      - `java`项目`jdbc`，与项目符合
      - 可实现原子性事务，要么全部成功，要么全部失败
      - 性能比`XA`高很多
      - 侵入性非常低

  - 使用方式：

    - 1.先部署`seata` server服务端（支持集群），事务相关数据存放在数据库中（全局事务表、分支事务表、全局锁表）
    - 2.微服务整合`seata`，抽取了一个通用配置（数据源代理，配置服务端的连接地址）
    - 每个设计分布式事务的数据库，都要创建一个undo_log日志表
    - 在发起分布式事务的方法上，加上@`GlobalTransactional`注解 开启代码的全局事务

- `seata`的工作原理？

  - AT模式采用二阶段提交：
    - @`GlobalTransactional`开启全局事务，实现`AOP`方法的增强，会调用服务端创建一条全局事务数据
    - 第一阶段，执行每个事务：当我们的业务`sql`被执行前，会先注册一个分支事务，将我们的业务`sql`+业务`sql`对应生成回滚信息，在一个本地事务中执行，回滚信息会存放在undo_log中
    - 第二阶段：
      - 情况一：一阶段全部成功→根据全局事务id及分支事务id异步的删除所有相关的回滚日志undo_log日志
      - 情况二：一阶段失败→根据全局事务id及分支事务id，查询对应的回滚日志，根据回滚日志的内容生成反向的`sql`，进行数据的回滚

- `seata`的回滚原理？

  - 执行`sql`时，`seata`会解析`sql`语句，`seata`会查询你修改前的数据，存储为→before image前置镜像
  - 执行业务`sql`后，`seata`会查询你修改完毕的数据，存储为→after image后置镜像
  - 需要回滚时，查询到对应的回滚日志，先根据后置镜像，进行数据的校验，如果当前数据库数据和后置镜像不一致，说明数据被`seata`以外的操作修改了，那么回滚将失败，`seata`会不断重试回滚
  - 如果当前数据库数据和后置镜像一致，会根据前置镜像的数据内容，生成一条反向的`sql`语句，进行数据回滚

##### Redis:

- Redis的5种数据类型和应用场景
  - String，用于简单的kv缓存，设置过期时间key，协助Mysql创建主键唯一的Id
  - hash，类似map结构用于存储对象，购物车然后订单信息
  - list，有序列表，朋友圈点赞有序
  - set，无序去重，黑白名单，访问量去重
  - z-set，有序去重，热搜排序

- Redission的分布式锁会导致锁失效吗？【普适导航】

  - 不会，LUA脚本实现原子性（支持可重入锁）

- 为什么你的项目要使用缓存？
  - 高性能
    - 当我们的数据在一段时间内不发生改变，随着用户量访问次数的增多，我们在第一次查询后就将这样的数据放入缓存，以此来提升整体查询的性能，1000个用户访问都很慢和1个用户访问慢+999个用户访问很快在服务体验上有很大区别
      - 当数据发生改变，只需要同步数据库的同时更新缓存即可
  - 高并发（大厂使用缓存的原因）
    - 内存是天然支持高并发的，可以减轻数据库面对并发的压力，减少磁盘IO

- `Redis`支持事务吗？常用指令有哪些？

  - 支持，常用的指令

  - ```java
    #开启事务
    multi
    #添加命令
    sadd user:1001:follow 1002
    sadd user:1002:follow 1001
    
    sadd user:1001:fans 1002
    sadd user:1002:fans 1002
    #执行事务
    exec
    # 取消事务
    discard
    ```
    
  - 在使用SpringBoot整合Redis并使用事务时，需要在RedisConfig中开启事务配置

  - ```java
    //开启redis事务控制
    redisTemplate.setEnableTransactionSupport(true);
    ```

- `Redis`的缓存穿透与雪崩？击穿？如何解决？
  
  - 缓存穿透是指查询一个一定不存在的数据，由于缓存不命中，接着查询数据库也无法查询出结果，因此也不会写入到缓存中，这将会导致每个查询都会去请求数据库，造成缓存穿透
    - 缓存空对象，当存储层不命中后，即使返回的空对象也将其缓存起来，同时会设置一个过期时间，之后再访问这个数据将会从缓存中获取，保护了后端数据源
    - 或者使用谷歌的bloomfilter对其进行过滤
  - 缓存雪崩是指，由于缓存层承载着大量请求，有效的保护了存储层，但是如果缓存层由于某些原因整体不能提供服务，于是所有的请求都会达到存储层，存储层的调用量会暴增，造成存储层也会挂掉的情况
    - `Nginx`或者`GateWay`限流
    - 数据预热，预先更新缓存
    - 在缓存失效后，通过加锁或者队列来控制读数据库写缓存的线程数量。比如对某个key只允许一个线程查询数据和写缓存，其他线程等待。相同的key，设置不同的过期时间，让缓存失效的时间点尽量均匀。
  - 缓存击穿是指Redis中的一些热点数据过期了，然后大量的数据请求进来，直接访问数据库，对数据库造成并发压力甚至导致数据库崩溃
    - 后台定义一个定时任务，专门用于更新缓存数据
  
- Redis的线程模型是什么？

  - Redis的单线程模型是一种基于Reactor模式的文件事件处理器，主要由多路复用+队列+文件分派器+请求处理器，可以监听多个客户端的socket请求，并且将请求存放于队列中原子性的执行
  
- 为什么Redis单线程还能支撑高并发？

  - 效率快
    - 磁盘操作设计IO，内存是现成的
  - 核心是基于非阻塞的IO多路复用
  - 单线程反而避免了多线程频繁的上下文切换问题
    - 上下文切换是指，多线程执行期间线程的不断切换，会造成CPU的消耗

- `Redis`的持久化方式？
  - `RDB`：RDB持久化是指在指定的时间间隔内将内存中的数据集快照写入磁盘，实际操作过程是fork一个子进程，先将数据集写入临时文件，写入成功后，再替换之前的文件，用二进制压缩存储，文件后缀名.rdb。

    - 保存快照的指令，Redis默认是bgsave，异步保存，还有一个是save，同步保存，这个在保存的时候Redis会阻塞，不会执行任何命令

  - `AOF`：AOF持久化以日志的形式记录服务器所处理的每一个写、删除操作，查询操作不会记录，以文本的方式记录，可以打开文件看到详细的操作记录。

    - `AOF`方式需要手动开启，修改`redis.conf`

    - ```java
      # 是否开启AOF，默认为no
      appendonly yes
      
      #设置AOF文件名称
      appendfilename  appendonly.aof
          
      #保存的文件格式
      appendonly.aof
      ```

    - `AOF`的重写优化：当`AOF`文件体积超过阈值时，则会触发`AOF`文件重写，`Redis`会开启子线程创建一个新的`AOF`文件替代现有`AOF`文件。 新的`AOF`文件不会包含任何浪费空间的冗余命令，只存在恢复当前`Redis`状态的最小命令集合

      - 重写的相关参数配置，比如文件多大时进行重写，文件大小超过上次重写的多少时重写，在redis.conf里进行配置

      - ```java
        #当前aof文件大小超过上一次aof文件大小的百分之多少时进行重写。如果之前没有重写过，以
        启动时aof文件大小为准
        auto-aof-rewrite-percentage 100
        
        #限制允许重写最小aof文件大小，也就是文件大小小于64mb的时候，不需要进行优化
        auto-aof-rewrite-min-size 64mb
        ```

- Redis如何保证高可用？
  - 主从复制，读写分离，主库宕机，需要手动修改从库状态，指令slaveof no one
  - 哨兵模式，全自动监控redis服务器状态，哨兵也是一个redis服务器，但是不用来缓存数据，发现异常时，可以通过API向运维人员发送信息并且进行自动故障迁移，但是由于哨兵单独占用服务器，存储能力有限
    - 值得注意的点是，哨兵并且是单数，因为哨兵里面存着一个主管判断和客观判断的机制，即一个redis哨兵发现某个主库宕机时，这个时候的判断只是当前的哨兵的主管判断，真正重新设置主库，是基于半数机制的客观判断来决定的，即一半以上的哨兵认为某个主库宕机，此时才会进行主库的重新设定，单独的哨兵的判断存在哨兵本身有问题的可能
  - 分片集群，去中心化的高可用方案，采用哈希槽来处理数据和实例之间的映射关系，一个集群共有0~16383,16384个槽
    - 存储原理是，根据键值对的 key，按照`CRC16` 算法计算一个 16 bit 的值，再用这个 `16bit` 值对 16384 取模，得到 0~16383 范围内的模数
    - 分片集群支持动态扩容和缩容，但是需要手动修改槽给新的扩容的服务器
  
- Redis中key是怎么删除的？
  - 惰性删除，没有用到的key不删除，一直等到用的时候再去确认其过期时间
  - 定期删除，默认每秒扫描10次部分待过期的key，每次默认20个key，删除这里面过期的key，如果这20个里面过期key的比例超过0.25，就再次扫描
  
- 针对Redis的key删除策略产生的问题，Redis还设置了内存淘汰策略
  - **lru：**Least Recently Used，它是以**时间**为基准，删除最近**最久**未被使用的key。
  
  - **lfu：**Least Frequently Used，它是以**频次**为基准，删除最近**最少**未被使用的key。
  
  - ```
    手写LRU，Java简易版
    public class LRUCache<K, V> extends LinkedHashMap<K, V> {
        
    private final int CACHE_SIZE;
    
        // 这里就是传递进来最多能缓存多少数据
        public LRUCache(int cacheSize) {
            super((int) Math.ceil(cacheSize / 0.75) + 1, 0.75f, true); // 这块就是设置一个hashmap的初始大小，同时最后一个true指的是让linkedhashmap按照访问顺序来进行排序，最近访问的放在头，最老访问的就在尾
            CACHE_SIZE = cacheSize;
        }
    
        @Override
        protected boolean removeEldestEntry(Map.Entry eldest) {
            return size() > CACHE_SIZE; // 这个意思就是说当map中的数据量大于指定的缓存个数的时候，就自动删除最老的数据
        }
    
    }
    ```
  
  - 

##### ElasticSearch：

- ES的分布式架构原理能说一下么（ES是如何实现分布式的）
  -  ![img](https://img-blog.csdnimg.cn/20190527155325909.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3dlaXhpbl8zODExODAxNg==,size_16,color_FFFFFF,t_70) 

#### 熟练运用集合、`NIO`、多线程等技术

##### 集合：

![这里写图片描述](https://img-blog.csdn.net/2018091021233175?watermark/2/text/aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L2hlZmVuZ2xpYW4=/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70)

- 介绍一下HashMap（哈希散列表）？

  - HashMap如何计算索引下标？

    - 路由寻址公司：（table.length-1）&node.hash=index

      - &：二进制位运算，有0则0，无0则1

      - ```java
         static final int hash(Object key) {
                int h;
                return (key == null) ? 0 : (h = key.hashCode()) ^ (h >>> 16);
            }
        key的hashcode与key的hashcode的高16位进行运算，让原hashcode的低16位具有了高16位的信息，参与运算index
             * 0b 0010 0101 1010 1100 0011 1111 0010 1110   = h  
             * 0b 0010 0101 1010 1100 0011 1111 0010 1110
             * ^
             * 0b 0000 0000 0000 0000 0010 0101 1010 1100   = h >>> 16
             * => 0010 0101 1010 1100 0001 1010 1000 0010   = 参与路由寻址的hashcode
            这样操作的原因是hashmap的初始长度不长，（table.length-1）&key.hashcode的结果很容易产生哈希冲突形成链表降低散列表的查询效率，这样做可以在长度不长的情况下让key的hashcode的高16位也能参与运算来降低哈希冲突的产生，让数据在散列表中尽量避免链表形式存储
            0000 0000 0000 0000 0000 0000 0001 0000 = 16
            0000 0000 0000 0000 0000 0000 0000 1111 = 15
            0000 0000 0000 0000 0000 0000 0010 0000 = 32
            0000 0000 0000 0000 0000 0000 0001 1111 = 31
        ```

        - ^：二进制异或运算，相同则0，不同则1
    
  - HashMap如何添加一个元素？

    - ```java
      JDK官方说明：
          HashMap（哈希散列表）是基于哈希表实现的Map接口。这个实现提供了所有可选的map操作，【并允许null值和null键】
          这个类不保证映射的顺序【映射顺序的保证是选择LinkedHashMap】
          特别是，它不能保证顺序随时间保持不变【即当产生扩容场景时，数据的顺序将由于路由寻址的公式进行重排】
          如果你在使用HashMap时注重其查询的性能，那么【不要将初始容量（initial capacity）设得过高，或者将负载因子（load factor）设置得过低】
          HashMap的实例有两个参数会影响其性能，初始容量（initial capacity）和负载因子（load factor），【当哈希表中的条目数量超过负载因子和当前容量的乘积时，哈希表将resize (即重新构建内部数据结构)，因此哈希表的bucket数量大约是当前的两倍】
      
      
      
      
      //约定，hashmap（即散列表）的实现基于一些基本的约定（jdk官方）
      //将散列表的数组单元称为bucket，即桶
      //将散列表的链表或树中的数据称为bin，即箱子
      
      
      
      
      //hash,key,value指当前你将添加至散列表的【异或后的key的hashcode，key，value】
      //onlyIfAbsent是boolean类型的变量，默认是false，API意为->如果onlyIfAbsent为true，则不改变现有值
      //evict是boolean类型的变量，API意为->如果为false，则表处于创建模式，推断其是用于表达hashmap在创建中添加不了值的意思
      final V putVal(int hash, K key, V value, boolean onlyIfAbsent,
                         boolean evict) {
          //tab指散列表
          //p指当前你将存储至散列表的新数据的node临时变量，用于进行比较（因为在你进行添加时你不知道你的key的对应的散列表节点中是否已经有数据存在）
          //n指散列表的长度
          //i指通过(n - 1) & hash算出来的你将存储至散列表的路由结果
              Node<K,V>[] tab; Node<K,V> p; int n, i;
          //如果散列表是null或者散列表长度为0，则调用resize进行扩容
              if ((tab = table) == null || (n = tab.length) == 0)
                  n = (tab = resize()).length;
          //如果p为null，则直接对该节点添加新数据
              if ((p = tab[i = (n - 1) & hash]) == null)
                  tab[i] = newNode(hash, key, value, null);
              else {
                  //e指p.next，此环节进入链表结构或者树结构的对比，需要使用到新的变量来代表遍历出的下一个变量
                  //k用来代表一个临时的用于比较的key变量
                  Node<K,V> e; K k;
                  //p不为null时，如果p的hash、key、堆地址和要存储的新数据hash、key、堆地址完全一样，则直接将e变量指向p（在方法最后会对e变量进行value的添加及oldValue的返回），这里的逻辑是定义的临时变量e指向了p的堆内存，并且在方法的最后有了对e的value的值的添加（也就是用要添加的value替换了原有的oldValue），完成对新数据的更新操作
                  if (p.hash == hash &&
                      ((k = p.key) == key || (key != null && key.equals(k))))
                      e = p;
                  //如果p所处的结构是树，嵌入树的逻辑进行处理
                  else if (p instanceof TreeNode)
                      e = ((TreeNode<K,V>)p).putTreeVal(this, tab, hash, key, value);
                  //如果p所处的结构为链表，对于key的堆地址比较需要进行遍历，即将e赋值为p.next进行遍历比较
                  else {
                      for (int binCount = 0; ; ++binCount) {
                          //如果没有堆地址相同的value，尾插法添加新数据
                          if ((e = p.next) == null) {
                              p.next = newNode(hash, key, value, null);
                              if (binCount >= TREEIFY_THRESHOLD - 1) // -1 for 1st
                                  treeifyBin(tab, hash);
                              break;
                          }
                          //如果有堆地址相同的value，e=p.next，同理指向p.next的堆地址，并在方法的最后通过e对堆地址的值进行更新，即替换
                          if (e.hash == hash &&
                              ((k = e.key) == key || (key != null && key.equals(k))))
                              break;
                          //将e又赋值为p，以进行下一次的遍历
                          p = e;
                      }
                  }
                  //针对put方法中的e=p语句，将堆内存中的值进行更新，并返回旧值
                  if (e != null) { // existing mapping for key
                      V oldValue = e.value;
                      if (!onlyIfAbsent || oldValue == null)
                          e.value = value;
                      afterNodeAccess(e);
                      return oldValue;
                  }
              }
          //modCount统计node元素修改的次数，替换不计入，transient修饰，外部类无法调用此结果
              ++modCount;
          //添加元素size+1，触发扩容
              if (++size > threshold)
                  resize();
              afterNodeInsertion(evict);
              return null;
          }
      ```
      
    
  - HashMap如何进行动态扩容？

    - ```java
       final Node<K,V>[] resize() {
           //oldTab指扩容前的散列表
              Node<K,V>[] oldTab = table;
           //oldCap指table数组容量，这里进行了判断，如果扩容前为null，那容量就是0，不为则oldTab.length
              int oldCap = (oldTab == null) ? 0 : oldTab.length;
           //oldThr指扩容之前的扩容阈值，触发本次扩容的阈值
              int oldThr = threshold;
           //newCap指扩容之后，新table数组容量
           //newThr指扩容之后，下次触发扩容的阈值
              int newCap, newThr = 0;
           //条件如果成立说明hashmap的散列表已经初始化过了，这是一次正常扩容
              if (oldCap > 0) {
                  //当oldCap >= 1 << 30时
                  if (oldCap >= MAXIMUM_CAPACITY) {
                      //直接将oldCap的阈值设置为阈值最大值2147483647
                      threshold = Integer.MAX_VALUE;
                      //返回oldTab，因为已经达到上限，无法在扩容了，但是这种场景很少发生，因为容量已经够大了
                      return oldTab;
                  }
                  //oldCap左移一位实现数值翻倍，并且赋值给newCap， newCap 小于数组最大值限制 且 扩容之前的容量oldCap >= 16
                  //扩容之前的容量即oldCap，你需要确认它是 >= 16的，也就是 >= 默认散列表的初始值，才能触发扩容 
                  //这种情况下，则下一次扩容的阈值等于当前阈值翻倍
                  else if ((newCap = oldCap << 1) < MAXIMUM_CAPACITY &&
                           oldCap >= DEFAULT_INITIAL_CAPACITY)
                      newThr = oldThr << 1; // double threshold
              }
           //当oldCap=0时
              else if (oldThr > 0) // initial capacity was placed in threshold
                  newCap = oldThr;
              else {               // zero initial threshold signifies using defaults
                  newCap = DEFAULT_INITIAL_CAPACITY;
                  newThr = (int)(DEFAULT_LOAD_FACTOR * DEFAULT_INITIAL_CAPACITY);
              }
              if (newThr == 0) {
                  float ft = (float)newCap * loadFactor;
                  newThr = (newCap < MAXIMUM_CAPACITY && ft < (float)MAXIMUM_CAPACITY ?
                            (int)ft : Integer.MAX_VALUE);
              }
              threshold = newThr;
              @SuppressWarnings({"rawtypes","unchecked"})
                  Node<K,V>[] newTab = (Node<K,V>[])new Node[newCap];
              table = newTab;
              if (oldTab != null) {
                  for (int j = 0; j < oldCap; ++j) {
                      Node<K,V> e;
                      if ((e = oldTab[j]) != null) {
                          oldTab[j] = null;
                          if (e.next == null)
                              newTab[e.hash & (newCap - 1)] = e;
                          else if (e instanceof TreeNode)
                              ((TreeNode<K,V>)e).split(this, newTab, j, oldCap);
                          else { // preserve order
                              Node<K,V> loHead = null, loTail = null;
                              Node<K,V> hiHead = null, hiTail = null;
                              Node<K,V> next;
                              do {
                                  next = e.next;
                                  if ((e.hash & oldCap) == 0) {
                                      if (loTail == null)
                                          loHead = e;
                                      else
                                          loTail.next = e;
                                      loTail = e;
                                  }
                                  else {
                                      if (hiTail == null)
                                          hiHead = e;
                                      else
                                          hiTail.next = e;
                                      hiTail = e;
                                  }
                              } while ((e = next) != null);
                              if (loTail != null) {
                                  loTail.next = null;
                                  newTab[j] = loHead;
                              }
                              if (hiTail != null) {
                                  hiTail.next = null;
                                  newTab[j + oldCap] = hiHead;
                              }
                          }
                      }
                  }
              }
              return newTab;
         }
       ```
       
    - 

- 介绍一下LinkedList？【莫比嗨客】
  - LinkedList的特性

    - `LinkedList` 集合底层实现的数据结构为双向链表
      - 双向链表的优点：加快了查询，可以利用index和size/2来决定从头部查找更快还是尾部
    - `LinkedList` 集合中元素允许为 null
    - `LinkedList` 允许存入重复的数据
    - `LinkedList` 中元素存放顺序为存入顺序
    - `LinkedList` 是非线程安全的，如果想保证线程安全的前提下操作 `LinkedList`，可以使用 `List list = Collections.synchronizedList(new LinkedList(...));` 来生成一个线程安全的 `LinkedList`
    - 每个节点上有三个字段：当前节点的数据字段（data）,指向上一个节点的字段（prev），和指向下一个节点的字段（next）

##### 并发编程：

- 什么是JMM模型？
  
  - java的内存模型，是一种抽象的概念，简单来说，就是说我们在定义一个变量时，这个变量会在主内存中进行存储，当我们使用线程对其进行调用的时候，并不是直接对其进行加载，而是在线程中有一个工作内存的概念，把主内存中的这个共享变量进行拷贝，然后储存在工作内存中，形成一个副本的共享变量进行使用，这个过程不是原子性的，所以在并发场景下会产生并发问题
  -  ![img](https://p3-juejin.byteimg.com/tos-cn-i-k3u1fbpfcp/754c7ccb02c7455b8c75e54ed8fc2d35~tplv-k3u1fbpfcp-zoom-in-crop-mark:1304:0:0:0.awebp) 
  
- 如何停止一个线程？

  - 不推荐使用stop()方法，因为这是暴力抛出异常的停止，在并发过程中会导致数据的不一致，这个方法目前已经被弃用
  - 搭配isInterrupted();interrupt();break;使用，通过interrupt()标记中断点，通过isInterrupted()拿到中断状态，break手动停止线程

- 如何保证线程的顺序执行？

  - 可以通过join()方法来保证线程的执行顺序

  - ```
    a.join(c);a线程在执行时会运行c线程的插入，也就是让c先执行，等c执行完了a再执行
    ```

- 线程的生命周期？

  - wait是会释放锁，但是sleep是抱着锁睡觉
  - 实现线程的四种方式？
    - 继承Thread类、实现Runnable接口、实现Callable接口、交给线程池管理线程
  
- 并发编程三大特性？

  - 原子性：某个共享变量的操作同一时刻只能允许一个线程进行

    - synchronized的底层实现

      - synchronized在调用时必须给它一个对象才能实现，这是因为JVM对于这个机制的底层实现是基于一个monitor的对象监视器实现的，每个对象在JVM中运行时会有一个monitor与它进行关联，线程在进入此对象时会查看对象头里锁的状态，然后获得锁时，monitor会进行计数，从0记成1，如果其他线程再尝试去进入，必须等这个线程出来才行，以此来实现修饰的代码块的原子性

        - 为什么必须给一个对象才能实现，是因为在对象里会存储锁的一个状态，对象除了我们看到的方法和属性，在内存中一共由三部分组成，通过对象头线程可以进行monitor锁状态的确认

          - ```
            对象头                    
              GC年龄
              	此对象的存活年龄，即逃脱了几次垃圾回收
              		
            Klass Word（class指针）
            	指向当前对象所属于的类的地址，可以通过这个地址获取到它的元数据信息
            	
            Mark Word（锁）: 
            	记录monitor的状态，0/1，获得了锁的线程的ID
            	
            数组长度（如果对象是个数组）
              
            对象实例
              你创建的方法及属性
              		
            对齐填充
              所谓补齐区域是指Java对象的存储是存在内存中的，Java希望对象的大小是整齐的，如果对象总大小不是4字节的整数倍，会填充上一段内存地址使之成为整数倍
            ```

        - 锁的互斥，synchronized修饰的方法所属的对象是同一个时，当我们去调用这个对象的方法a时，其他的被synchronized修饰的方法是无法调用的，即锁是同一个对象的锁，会产生互斥

          - 注意点，当方法的属性是static修饰时，synchronized监视的对象是当前对象的类的class对象
          - 注意点，尽量不要用包装类和字符串作为锁的对象，正确的加锁是创建一个对象并用final关键字来修饰

        - 锁的嵌套，即方法内有两把或者多把synchronized锁修饰的方法相互调用，这种时候就有可能发生死锁

      - 锁的升级原理

        - Synchronized锁有四种状态，**无锁，偏向锁，轻量级锁，重量级锁**，这几个状态会随着竞争状态逐渐升级，锁可以升级但不能降级，但是偏向锁状态可以被重置为无锁状态
  
- 可见性：当主内存中的共享变量被一个A线程修改时，B线程始终加载的是之前的工作内存的主内存的共享变量的副本，无法见到这次修改
  
- 有序性：单线程执行代码时，JVM有一个执行优化的概念，即JVM会自主判断在不影响你的代码的执行结果的情况下选择最优的代码执行顺序，但这样的自主优化情况在并发环境下有可能会导致线程安全问题
  
  - 解决可见性和有序性的方案：volatile
      - volatile修饰的共享变量当被修改时，其他线程会立刻得到修改之后的结果，这个修改也会同时被虚拟机强制同步刷新到主内存中，并且当一个线程用到被vilatile修饰的值的时候，JVM会强制要求它从主内存中读取
      - volatile会对其修饰的代码进行屏蔽指令重排序
  
- Synchronized关键字用法

  - 修饰方法
  - 修饰代码块
    - 修饰的代码块越精确越有助于性能的提升
  - 修饰一个静态的方法
  - 修饰一个类

- 在Spring中，默认的Bean是线程安全的吗？（不管什么作用域）如何解决？

  -  spring 管理的 bean 的线程安全跟 bean 的创建作用域和 bean 所在的使用环境是否存在竞态条件有关，spring 并不能保证 bean 的线程安全
  -  解决方式是在导入bean时，使用volatile关键字修饰，解决多线程环境下bean创建的双检索问题
     -  双检索指多线程环境下对单例bean的调用时，会进行两次判断，第一次判断对象是否创建，没有的话创建前再进行一次判断，判断对象是否存在，然后创建bean的逻辑需要synchroniced锁防止并发问题

- list数组去重

  - contains判断，set集合去重（前提是重写equals方法）

  - ```java
    ArrayList<Object> list1 = new ArrayList<>();
            list1.add(list.get(0));
            for (int i = 0; i <list.size(); i++) {
    
                boolean contains = list1.contains(list.get(i));
                if (!contains) {
                    list1.add(list.get(i));
                }
            }
    ```

  - stream().distinct()（前提是重写equals）

  - ```java
    list.stream().distinct().collect(Collectors.toList());
    ```


- `CAS`与悲观锁的应用场景？

  - `CAS`适合低并发的场景，高并发时，自旋量不断增大会直接造成CPU消耗，从而影响服务器的性能
  - 悲观锁会有阻塞队列存取这样的线程

- 死锁与饥饿的区别

  - 死锁：是指两个或两个以上的进程（或线程）在执行过程中，因争夺资源而造成的一种互相等待的现象，若无外力作用，它们都将无法推进下去
  - 饥饿：一个或者多个线程因为种种原因无法获得所需要的资源，导致一直无法执行的状态

- Lock锁与Synchronized的区别？

  - Lock更加灵活，在无法获取锁时可以安排做一些其他的事（tryLock()方法），而Synchronized只会一直死等
  - Lock可以实现读写锁，即读操作多线程可以并行，但是写操作只能串行
  - Lock是个借口，Synchronized是Java内置的关键字
  - Lock只能修饰代码块，Synchronized可以修饰代码块，也可以修饰方法
  - Lock必须主动释放不然会造成死锁lock.unlock()，Synchronized会自动释放
  - Lock可以通过其读写锁的功能提供读操作的效率
  - 并发场景下，Lock比Synchronized的性能大很多，并发量小的时候两者性能差不多

- ThreadLocal底层是如何实现的？
  - ThreadLocal是一个共享的变量，会将你想要共享的信息存储在底层的一个ThreadLocalMap里，是一个键值对形式的entry的集合，每个线程都会有属于自己的ThreadLocalMap，我们可以将变量比如用户信息存储在里面
    - 注意点，这个局部线程变量属于弱引用，随着保存数据的增多，容易造成数据泄露，需要调用remove方法清除数据
    - <img src="https://p1-jj.byteimg.com/tos-cn-i-t2oaga2asx/gold-user-assets/2020/7/26/1738b45487065b90~tplv-t2oaga2asx-watermark.awebp" alt="img" style="zoom:67%;" />
  
- 为什么需要线程池？

  - 面对多个需要执行的任务，new线程和销毁线程是耗费时间和性能的，这个时候就需要线程池技术来解决多任务的执行
  - 使用线程池的时候数量是根据当前计算机的CPU配置而定的，不多不少，防止CPU执行线程时来回切换影响性能

- 多线程的应用场景？

  - 处理并发，618大促
  - 异步处理
  - 分布式计算、分片下载、断点续传

- 继承Thread类和实现Runnable接口哪种方式更好？

  - Runnable，继承只能单继承，而Runnable是接口可以多实现也可以继承其他类

- Callable和Runnable的区别？

  - Callable可以返回线程执行的结果，注意点是实现Callable接口时，需要Callable<T>里定义返回结果的类型T
  - 在使用Callable执行线程前需要FutureTask对其进行包装，返回结果通过ft.get()返回
  
- 守护线程是什么？

  - 是线程的一个概念，我们正常的程序在执行时，真正执行任务的是用户线程，还有一部分用于守护这些线程进行运行的线程，就是守护线程，当用户线程执行完毕，系统会直接连通守护线程进行关闭

  - ```
    线程实例.setDaemon(true);来设置创建的线程成为守护线程
    ```

- 简单介绍一下线程池？

  - 用于执行多线程的工具，顶级接口Executor（Runnable）;定义线程池类的时候通常会实现ExecutorService子接口，核心实现类ThreadPoolExecutor，Executors工具包

  - ```java
    int corePoolSize,核心线程数量，状态是阻塞的，运行完任务后不会关闭,程序这需编写executor.shutdown()待任务执行完关闭/executor.shutdownNow()立刻关闭，来让其运行后关闭，可以通过手动设置允许超时，这时就根据存活时间来存活了 executor.allowCoreThreadTimeOut(true);
    int maximumPoolSize,最大线程数量（核心线程+临时线程数），当核心线程满了并且队列中存满了任务时，系统判断最大线程数还未达到，这个时候会创建临时线程来执行任务
    long keepAliveTime,存活时间，设置了只对临时线程有效，处于空闲状态时开始计时
    TimeUnit unit,单位
    BlockingQueue<Runnable> workQueue,任务队列，当核心线程数满了时，后续线程先存储在队列中，待队列满了再调用非核心线程执行任务
    ThreadFactory threadFactory,创建线程工厂对象
    RejectedExecutionHandler handler 拒绝策略，当核心线程满了→任务队列满了→最大线程数满了后，根据拒绝策略来处理后续到来的任务，
        new ThreadPoolExecutor.AbortPolicy()，丢弃任务，抛出异常
        new ThreadPoolExecutor.CallerRunsPolicy()，不抛弃任务，调用主线程帮助执行任务
        new ThreadPoolExecutor.DiscardOldestPolicy()，抛弃最先加在队列的任务来获得最新的任务，不抛异常
        new ThreadPoolExecutor.DiscardPolicy()，抛弃最新加在队列的任务来获得最新的任务，不抛异常
    ```

- Executors可以创建几种常用的线程池？

  - CachedThreadPool，可缓存的线程池，只用临时线程完成任务，核心和队列大小都是0
  - FixedThreadPool，固定长度的线程池，只用固定的核心线程执行任务
  - SingleThreadPool，单例线程池，只用一个核心线程来完成任务
    - 三者都基于ThreadPoolExcetor实现，内部new此类
  - ScheduledThreadPool，可调度的线程池，可添加延时参数或者定时参数
    - 继承自ThreadPoolExcetor
  
- 线程是如何执行的？

  - 首先线程的执行是需要看CPU的配置的，几核几线程代表其可并行执行多少条线程，在不为线程配置1~10的优先级属性时，默认采取的是抢占式的争夺CPU为下一个线程执行预留的时间片，但是优先级也不是绝对的，只是增加了线程拿到运行权的概率
  
  - ```
    线程实例.setPriority(10);来设置创建的线程执行优先级为最大
    ```
  
  - 值得注意的是，多线程并不代表着效率高，多线程的效率和CPU的配置息息相关，加入CPU不行，开启多线程则是会降低线程的效率
  
- 什么是线程的上下文切换？


    - 因为以下一些原因导致 cpu 不再执行当前的线程，转而执行另一个线程的代码 

- ReentrantLock相对sychronized具备哪些特点？


    - 可中断 
    - 可以设置超时时间 
    - 可以设置为公平锁 
    - 支持多个条件变量 

<img src="C:\Users\dell\AppData\Roaming\Typora\typora-user-images\1650097375500.png" alt="1650097375500" style="zoom: 80%;" />

- 理解ReentrantLock

    -  **支持重入性，表示能够对共享资源能够重复加锁，即当前线程获取该锁再次获取不会被阻塞** 
    - 公平锁vs非公平锁
        - 公平锁每次获取到锁为同步队列中的第一个节点，**保证请求资源时间上的绝对顺序**，而非公平锁有可能刚释放锁的线程下次继续获取该锁，则有可能导致其他线程永远无法获取到锁，**造成“饥饿”现象**。
        - 公平锁为了保证时间上的绝对顺序，需要频繁的上下文切换，而非公平锁会降低一定的上下文切换，降低性能开销。因此，ReentrantLock默认选择的是非公平锁，则是为了减少一部分上下文切换，**保证了系统更大的吞吐量**。

- 指令重排有什么解决方案？

    - 在希望不进行指令重排的语句的最后使用到的成员变量上加volatile关键字来解决可见性问题

- 怎么解决count++的线程安全性问题？

  - 累加方法加 synchronized/ Lock 同步锁；
  - 使用 AtomicInteger/ AtomicLong 原子类；
  - **使用 LongAdder 原子类（推荐使用）；**

- LongAdder的原理？

  - **LongAdder中的Cell 数组相当于一个分段的概念，把 AtomicXXX 中的一个值分成了多个值进行管理，当 CAS 更新失败时不再当前循环重试，而是尝试获取其他的资源锁，这样就降低了对于 AtomicXXX 中间是单个资源的竞争，所以 LongAdder 的性能更高。**

  - **LongAdder的底层cell类（Cell数组的子类）上应用了防止缓存行伪共享的@Contended注解，为每个对象cell的不同缓存行之间加了空隙，这样就保证了不会因为其中一个缓存行失效导致其他的缓存行都失效了**

    - 虽然 LongAdder 性能更好，那有没有缺点呢？

      LongAdder 带来了良好的性能，代价肯定也是有的，既然维护了 Cell 数组，也就意味着要占用更多的内存空间，以空间换时间，也是值得的。

  -  ![img](https://img-blog.csdnimg.cn/img_convert/7f7ea11177706f450a426bc6bef4cdcb.png) 

- 如何解决多任务的顺序执行？
  - 如果没有返回结果，可以使用CountDownLatch这个类，在线程池每个任务完成时进行提交，并在最后任务都执行完时，进行await()，来保证任务的顺序执行
    - 注意点：**countdownlatch不能被重用**，可以使用CyclicBarrier代替
    - <img src="C:\Users\dell\AppData\Roaming\Typora\typora-user-images\1650261333228.png" alt="1650261333228" style="zoom:80%;" />
    - 原因是如果线程数与任务数不一致，到时候Cyclic判定任务完成就会有冲突，假设线程数是3，那么完成一次cyclic的判定就从原来的task1，task2变成了task1，task2，task1，同时可运作三个任务，这样就达不到想要的效果了
  - 有返回结果，使用Future来获得，通过线程池可以传给主线程
    - ![1650253765339](C:\Users\dell\AppData\Roaming\Typora\typora-user-images\1650253765339.png)

- Thread的start方法与run方法发区别？
  - 直接调用run是在主线程中执行了run，没有启动新的线程
  - 使用 start 是启动新的线程，通过新的线程间接执行 run 中的代码 

##### NIO：

- 什么是NIO/BIO？

  - NIO指非阻塞IO，分为同步非阻塞与异步非阻塞

    - 同步：线程自己去获取结果（一个线程）
    - 异步：线程自己不去获取结果，而是由其它线程送结果（至少两个线程）

    * 阻塞 IO

      ![](C:/Users/dell/Desktop/Netty网络编程/讲义/img/0039.png)

    * 非阻塞  IO

      ![](C:/Users/dell/Desktop/Netty网络编程/讲义/img/0035.png)

    * 多路复用

      ![](C:/Users/dell/Desktop/Netty网络编程/讲义/img/0038.png)

    * 信号驱动

    * 异步 IO

      ![](C:/Users/dell/Desktop/Netty网络编程/讲义/img/0037.png)

    * 阻塞 IO vs 多路复用

      ![](C:/Users/dell/Desktop/Netty网络编程/讲义/img/0034.png)

      <img src="C:\Users\dell\AppData\Roaming\Typora\typora-user-images\1649735547937.png" alt="1649735547937" style="zoom: 80%;" />

- 什么是零拷贝？

  - <img src="C:\Users\dell\AppData\Roaming\Typora\typora-user-images\1649735807752.png" alt="1649735807752" style="zoom:80%;" />
  - java 调用 transferTo 方法后，要从 java 程序的**用户态**切换至**内核态**，使用 DMA将数据读入**内核缓冲区**，不会使用 cpu
  - 只会将一些 offset 和 length 信息拷入 **socket 缓冲区**，几乎无消耗
  - 使用 DMA 将 **内核缓冲区**的数据写入网卡，不会使用 cpu

  整个过程仅只发生了一次用户态与内核态的切换，数据拷贝了 2 次。所谓的【零拷贝】，并不是真正无拷贝，而是在不会拷贝重复数据到 jvm 内存中，零拷贝的优点有

  * 更少的用户态与内核态的切换
  * 不利用 cpu 计算，减少 cpu 缓存伪共享
  * 零拷贝适合小文件传输

- 通信编程三大组件

  - ​	channel&buffer

    - channel 有一点类似于 stream，它就是读写数据的**双向通道**，可以从 channel 将数据读入 buffer，也可以将 buffer 的数据写入 channel，而之前的 stream 要么是输入，要么是输出，channel 比 stream 更为底层

  - selector

    - selector 的作用就是配合一个线程来管理多个 channel，获取这些 channel 上发生的事件，这些 channel 工作在非阻塞模式下，不会让线程吊死在一个 channel 上。适合连接数特别多，但流量低的场景（low traffic）

    - ```mermaid
      graph TD
      subgraph selector 版
      thread --> selector
      selector --> c1(channel)
      selector --> c2(channel)
      selector --> c3(channel)
      end
      ```

    - 调用 selector 的 select() 会阻塞直到 channel 发生了读写就绪事件，这些事件发生，select 方法就会返回这些事件交给 thread 来处理

##### Netty：

- 为什么Netty要异步？

  - 单线程没法异步提高效率，必须配合多线程、多核 cpu 才能发挥异步的优势
  - 异步并没有缩短响应时间，反而有所增加
  - 合理进行任务拆分，也是利用异步的关键

- Netty的常见组件有哪几个？分别有什么作用？

  - Eventloop

    - EventLoop 本质是一个单线程执行器（同时维护了一个 Selector），里面有 run 方法处理 Channel 上源源不断的 io 事件

  - channel

    - close() 可以用来关闭 channel
    - closeFuture() 用来处理 channel 的关闭
      * sync 方法作用是同步等待 channel 关闭
      * 而 addListener 方法是异步等待 channel 关闭
    - pipeline() 方法添加处理器
    - write() 方法将数据写入
    - writeAndFlush() 方法将数据写入并刷出

  - Handler & Pipeline

    - ChannelHandler 用来处理 Channel 上的各种事件，分为入站、出站两种。所有 ChannelHandler 被连成一串，就是 Pipeline

      * 入站处理器通常是 ChannelInboundHandlerAdapter 的子类，主要用来读取客户端数据，写回结果
      * 出站处理器通常是 ChannelOutboundHandlerAdapter 的子类，主要对写回结果进行加工

      打个比喻，每个 Channel 是一个产品的加工车间，Pipeline 是车间中的流水线，ChannelHandler 就是流水线上的各道工序，而后面要讲的 ByteBuf 是原材料，经过很多工序的加工：先经过一道道入站工序，再经过一道道出站工序最终变成产品

  - ByteBuf

    - 是对字节数据的封装

- 如何解决粘包或半包？

  - 现在大多数是通过在pipeline里加一个预设长度解码器，提前规定好双方通信的协议，来解决

- @Sharable注解是什么意思？有什么作用？

  -  用来说明ChannelHandler是否可以在多个channel直接共享使用 

##### Nginx：

- 什么是Nginx？

  - Nginx（“engine x”）一个具有高性能的【HTTP】和【反向代理】的【WEB服务器】，同时也是一个【POP3/SMTP/IMAP代理服务器】

    - WEB服务器也叫网页服务器，英文名叫Web Server，主要功能是为用户提供网上信息浏览服务。

    - HTTP是超文本传输协议的缩写，是用于从WEB服务器传输超文本到本地浏览器的传输协议，也是互联网上应用最为广泛的一种网络协议。HTTP是一个客户端和服务器端请求和应答的标准，客户端是终端用户，服务端是网站，通过使用Web浏览器、网络爬虫或者其他工具，客户端发起一个到服务器上指定端口的HTTP请求。

    - POP3(Post Offic Protocol 3)邮局协议的第三个版本，

      SMTP(Simple Mail Transfer Protocol)简单邮件传输协议，

      IMAP(Internet Mail Access Protocol)交互式邮件存取协议，

      通过上述名词的解释，我们可以了解到Nginx也可以作为电子邮件代理服务器。

    - 正向代理与反向代理的区别？

      - **正向代理( Forward Proxy )：是一个位于客户端和原始服务器之间的服务器，为了从原始服务器取得内容， 客户端向代理发送一个请求并指定目标(原始服务器)，然后代理向原始服务器转交请求并将获得的内容返回给客户端。客户端才能使用正向代理。**

        **反向代理( Reverse Proxy )：是指以代理服务器来接受 Internet 上的连接请求，然后将请求转发给内部网络上的服务器，并将从服务器上得到的结果返回给 Internet 上请求连接的客户端，此时代理服务器对外就表现为一个反向代理服务器。**

        接下来我提炼一下各自的特点：

        正向代理：
        代理客户。
        隐藏真实的客户，为客户端收发请求，使真实客户端对服务器不可见。
        一个局域网内的所有用户可能被一台服务器做了正向代理，由该台服务器负责 HTTP 请求。
        意味着同服务器做通信的是正向代理服务器。

        反向代理：
        代理服务器。
        隐藏了真实的服务器，为服务器收发请求，使真实服务器对客户端不可见。
        负载均衡服务器，将用户的请求分发到空闲的服务器上。
        意味着用户和负载均衡服务器直接通信，即用户解析服务器域名时得到的是负载均衡服务器的 IP。

        共同点：
        都是做为服务器和客户端的中间层。
        都可以加强内网的安全性，阻止 Web 攻击。
        都可以做缓存机制，提高访问速度。

        **区别：**
        **正向代理其实是客户端的代理，反向代理则是服务器的代理。**
        **正向代理中，服务器并不知道真正的客户端到底是谁;而在反向代理中，客户端也不知道真正的服务器是谁。**

        **作用不同。正向代理主要是用来解决访问限制问题;而反向代理则是提供负载均衡、安全防护等作用。**

      -  ![在这里插入图片描述](https://img-blog.csdnimg.cn/20201103133317742.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3FxXzQ5Mjk2Nzg1,size_16,color_FFFFFF,t_70#pic_center) 

- Nginx的优点？

  - 响应请求速度快，并发高，底层采用了**多进程和I/O多路复用(epoll)**实现

    - 多进程就是充分利用计算机的cpu，一般worker数量与cpu保持一致。 因为更多的worker只会导致进程之间相互竞争cpu，从而带来不必要的上下文切换。 

      - 什么是线程的上下文切换？

        - Linux是一个多任务的操作系统，它支持远大于CPU数量的任务同时运行，当然，这些任务实际上并不是真正的在同时运行，而是系统在很短的时间内，将CPU轮流分配给他们，给用户造成很多任务同时运行的错觉。

          在每个任务运行前， CPU 都需要知道任务从哪里加载，又从哪里开始运行。也就是说，需要系统事先给他设置好 CPU 寄存器和程序计数器（Program Counter,PC）

          - CPU 寄存器：是 CPU 内置的容量小、但速度极快的内存

          - 程序计数器：是用来存储 CPU 正在执行的指令位置、或者即将执行的下一条指令位置

          综上所述，我们就有答案了

          什么是上下文：

          我们通常说的上下文又叫CPU上下文，是CPU运行任何任务前，必须依赖的环境，包括CPU 寄存器和程序计数器

          上下文切换：就是先把前一个任务的 CPU 上下文（也就是 CPU 寄存器和程序计数器）保存起来，然后加载新任务的上下文到这些寄存器和程序计数器，最后再跳转到程序计数器所指的新位置，运行新任务。

        - ```java
          上下文切换详细介绍
          根据CPU切换运行任务的不同，又可以分为进程上下文切换、线程上下文切换、中断上下文切换
          
          我们先了解下面2个上下文切换涉及的知识点系统调用、进程运行态
          
          进程的运行态：
          
          Linux 按照特权等级，把进程的运行空间分为内核空间和用户空间 。在这两种空间中运行的进程状态分别称为内核态和用户态。
          
          内核空间(Ring 0)：具有最高权限，可以直接访问所有资源（读取文件，）
          
          分配内存、IO操作、创建子进程……都是内核操作。这也表明，当IO操作频繁时，System参数会很高。
          
          用户空间(Ring 3)：只能访问受限资源，不能直接访问内存等硬件设备，必须通过系统调用进入到内核中，才能访问这些特权资源
          
          典型的用户态空间程序有：Shells、数据库、web服务器、PHP程序、Java程序……
          
          在linux系统使用top命令查看cpu时，能看到user和system两项，对应的就是用户态和内核态占用的cpu资源
          
          如上，我们的web服务是运行在用户态下的，对文件的io没有权限，当需要读取文件时，就涉及到系统调用了
          
          系统调用：
          
          从用户态到内核态的转变，需要通过系统调用来完成。比如查看文件时，需要执行多次系统调用：open、read、write、close等。系统调用的过程如下：
          
          把 CPU 寄存器里原来用户态的指令位置保存起来；
          
          为了执行内核代码，CPU 寄存器需要更新为内核态指令的新位置，最后跳转到内核态运行内核任务；
          
          系统调用结束后，CPU 寄存器需要恢复原来保存的用户态，然后再切换到用户空间，继续运行进程；
          
          所以，一次系统调用的过程，其实是发生了两次 CPU 上下文切换。
          
          进程上下文切换？
          进程执行终止，它之前顺颂的CPU就会被释放出来，这时就从就绪队列中取出下一个等待时间片的进程；
          
          当某个进程的时间片耗尽，它就会被系统挂起，切换到其他等待CPU的进程运行；
          
          某个进程因为需要的系统资源比较大(比如内存不足),这时候该进程会被挂起，系统会调度其他进程执行；
          
          当有优先级更高的进程(系统操作进程)需要时间片，为了保证优先级更高的进程能够执行，当前进程会被挂起；
          
          如果当前进程中有sleep函数，他也会被挂起；
          
          线程的上下文切换？
          对操作系统来说，线程是最小的执行单元，进程是最小的资源管理单元。说白了，所谓内核中的任务调用，实际上的调度对象是线程；而进程只是给线程提供了虚拟内存、全局变量等资源。所以，对于现场和进程，我们可以这么理解：
          
          当进程只有一个线程时，可以认为进程就等于线程。
          
          当进程拥有多个线程时，这些线程会共享父进程的资源（即共享相同的虚拟内存和全局变量等资源）。这些资源在上下文切换时是不需要修改的。
          
          另外，线程也有自己的私有数据，比如栈和寄存器等，这些在上下文切换时也是需要保存的。
          
          综上，线程上下文切换有两种情况：
          
          前后两个线程属于不同进程，因为资源不共享，所以切换过程就跟进程上下文切换是一样的；
          
          前后两个线程属于同一个进程，因为虚拟内存是共享的，所以在切换时，虚拟内存这些资源就保持不动，只需要切换线程的私有数据、寄存器等不共享的数据。
          
          中断上下文切换？
          中断处理会打断进程的正常调度和执行。在打断其他进程时，需要将进程当前的状态保存下来，中断结束后，进程仍然可以从原来的状态恢复运行。
          
          中断上下文切换并不涉及到进程的用户态。所以，即便中断过程打断了一个正处在用户态的进程，也不需要保存和恢复这个进程的虚拟内存、全局变量等用户态资源。中断上下文，其实只包括内核态中断服务程序执行所必须的状态，包括 CPU 寄存器、内核堆栈、硬件中断参数等。
          ```

        - **小结**
          **根据Tsuna的测试报告，每次上下文切换都需要几十纳秒到数微妙的CPU时间，这个时间还是相当可观的。**

          **不管是哪种场景导致的上下文切换，你都应该知道：**

          **CPU上下文切换，是保证Linux系统正常工作的核心功能之一，一般情况下不需要我们特别关注。**

          **但过多的上下文切换，会把CPU时间消耗在寄存器、内核栈以及虚拟内存等数据的保存和恢复上，从而缩短进程真正运行的时间，导致系统的整体性能大幅下降。**

  - 配置简单，扩展性强

    - Nginx的设计极具扩展性，它本身就是由很多模块组成，这些模块的使用可以通过配置文件的配置来添加。这些模块有官方提供的也有第三方提供的模块，如果需要完全可以开发服务自己业务特性的定制模块。

  - 高可靠性

    - Nginx采用的是多进程模式运行，其中有一个master主进程和N多个worker进程，worker进程的数量我们可以手动设置，每个worker进程之间都是相互独立提供服务，并且master主进程可以在某一个worker进程出错时，快速去"拉起"新的worker进程提供服务。

  - 热部署

    - 现在互联网项目都要求以7*24小时进行服务的提供，针对于这一要求，Nginx也提供了热部署功能，即可以在Nginx不停止的情况下，对Nginx进行文件升级、更新配置和更换日志文件等功能。

  - 成本低、BSD许可证

    - Nginx本身是开源的，我们不仅可以免费的将Nginx应用在商业领域，而且还可以在项目中直接修改Nginx的源码来定制自己的特殊要求。这些点也都是Nginx为什么能吸引无数开发者继续为Nginx来贡献自己的智慧和青春。OpenRestry [Nginx+Lua]   Tengine[淘宝]

#### 熟悉高并发、高性能的分布式系统的设计、应用及调优

##### 分布式系统：

- 什么是分布式系统？

  - 顾名思义，这个系统是分布式的，区别于一体式的系统，它将每个请求涉及的模块拆分成多个服务，在多个机器上进行部署
- 为什么要对系统进行分布式的拆分？

  - 方便维护，各司其职
- 分布式与微服务的区别？

  - 分布式系统属于微服务体系
  - 但是微服务不一定是分布式的，因为微服务可以直接部署在一台服务器上，而分布式是部署在多台服务器
- Dubbo的工作原理
  -  ![在这里插入图片描述](https://img-blog.csdnimg.cn/20190308103242996.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3lnbDE5OTIwMTE5,size_16,color_FFFFFF,t_70) 
- Dubbo支持哪些负载均衡、高可用以及动态代理的策略？

  - 负载均衡策略
    - 权重随机策略
    - 轮询策略
    - 哈希策略（根据消息id进行hash算出指定消费者的策略）
    - 性能策略（自动感知一下机器性能的高低，针对高低按比例分配消息）

  - 集群容错策略
    - `failover cluster`模式，失败自动切换，默认模式
    - `failfast cluster`模式，一次调用失败就立即失败，常用于写操作
    - `failsafe cluster`模式，出现异常时忽略，常用于不重要的接口调用，比如记录日志
    - `failbackc cluster`模式，失败了后台自动记录请求，然后定时重发，比较适合于写消息队列这种
    - `forking cluster`模式，并行调用多个provider，只要一个成功就立即返回
    - `broadcacst cluster`模式，逐个调用所有的provider

  - 动态代理的策略：默认`javassist`，也可以通过`SPI`机制配置自己的动态代理策略

分布式锁的实现方案列举几个

- 基于数据库的悲观锁for update（行锁），执行时数据库对事务进行阻塞，但是这个操作非常影响数据库的性能，所以大并发的场景下不会使用，大多数的企业也不用，并且很多时候数据不一定存在数据库
- 基于zookeeper的文件系统及通知机制实现分布式锁
  - zookeeper的文件系统相当于linux中/root/node/lock这样创建文件路径的概念，利用这样的节点路径可以进行数据的存储，并且zookeeper中的机制是不允许客户端创建相同的目录的，利用这样的机制，我们可以做很多协调方面的业务
  - zookeeper的分布式锁的概念就是让多个相同的微服务来zookeeper创建微服务，但是约定好当其中一个创建好之后，其他相同的微服务就阻塞等待不能够创建，zookeeper中的通知机制会在这个事务执行完之后删除节点路径后通知到其他正在等待的微服务，然后创建新的分布式锁节点路径，整体上一致性比redis好，但是效率比redis低
- 基于redis实现分布式锁，确保分布式微服务的线程安全，基于setnx（set if not exist）、setex（set expire value）实现
  - setnx创建锁即如果没有这个key就创建并获得锁，setex设置超时时间，防止获得锁的线程挂了导致锁一直无法被其他线程拿到
  - 但是redis的指令多条执行无法保证原子性，所以真正实现锁是基于LUA脚步实现的，这个脚步可以保证多条指令在redis中执行时的原子性，实现的锁的数据结构是hash结构（key：锁名，field：客户端id=uuid+线程id，value：加锁的次数）
  - 默认生成的锁，不去指定失效时间时，具有自动续约的功能，但是指定了就没有了，自动续约是指线程执行超过失效时间时，只要线程不是挂掉，会自动重新按失效时间计时来保证任务的线程安全
  - redis自动续约的实现基于watch dog这个调度线程，这个线程每隔10s执行1次来确认你的线程是否超时或宕机，如果超时，为正在执行的线程重置失效时间

##### xxljob:

为什么不使用Spring Task？

- Spring Task只针对单服务进行定时，分布式的不满足

`xxljob`的使用过程？

- 首先在分布式任务的调度中心进行执行器的编写
  - 同步在微服务端编写好执行器，注意点是执行器需要定义端口号，执行器名称与调度中心的一致
  - 执行器的执行针对不同微服务，有很多可选的路由策略（轮询、随机、分片广播）
- 然后针对不同的执行器编写不同的定时任务
  - 为执行任务的方式编写cron时间表达式，秒（/*5，每隔`5s`触发一次） 分 时 天 月 周几（1（周日）-7） 年（可选）
  - 在要执行任务单方法上打上@XxlJob的注解，（）里填写任务名
  - 任务的执行针对单个执行器，多个任务的执行可以有不同的方式（串行、丢弃）

- 什么是`SaaS`系统？
  - 以多层租赁、服务及可扩展特性为主的互联网的开发系统，供应商将应用软件部署在自己的服务器上，客户可以根据需求向供应商订购所需的服务，不需要考虑服务的实现与维护，这样的服务是可复用的，这些客户在共享供应商的数据存储层的同时，他们的数据又是互相隔离的

- - 

#### 物联网：

##### MQTT：

- MQTT协议

MQTT（Message Queuing Telemetry Transport，消息队列遥测传输协议），是一种基于发布/订阅（publish/subscribe）模式的“轻量级”通讯协议，该协议构建于TCP/IP协议上，由IBM在1999年发布。

MQTT最大优点在于，用极少的代码和有限的带宽，为连接远程设备提供实时可靠的消息服务。

作为一种低开销、低带宽占用的即时通讯协议，使其在物联网、小型设备、移动应用等方面有较广泛的应用。

- MQTT协议特点

 MQTT是一个基于**客户端-服务器**的消息发布/订阅传输协议 ， MQTT 与 HTTP 一样，MQTT 运行在传输控制协议/互联网协议 (TCP/IP) 堆栈之上。 

 <img src="https://img-blog.csdnimg.cn/img_convert/7ff1df03602f5b4e430826a91d7a9387.png" alt="img" style="zoom:50%;" /> 

- MQTT OSI

`MQTT`使用的发布/订阅消息模式，它提供了一对多的消息分发机制，从而实现与应用程序的解耦。

这是一种消息传递模式，**消息不是直接从发送器发送到接收器**（即点对点），而是由`MQTT server`（或称为 MQTT Broker）分发的。

 <img src="https://img-blog.csdnimg.cn/img_convert/6ba6b542f625f4a4df2376600f53c00f.png" alt="img" style="zoom: 50%;" /> 

一个简单的MQTT应用场景：

- 光伏发电站是发布者（Publisher）。

- 主要主题（Topic）级别是"PV"，这个工厂发布两个子级别"sunshine"和"data"；

- "PV/sunshine"是一个布尔值（true/false，也可以是 1/0），充电站需要它来知道是否应该装载电动汽车（仅在阳光普照时 :)）。

- 充电站（EVSE）是订阅者，订阅"PV/sunshine"从服务器获取信息。

- "PV/data" 另一方面，以 kW 为单位传输工厂产生的瞬时功率，并且该主题可以例如通过计算机或平板电脑订阅，以生成一天内传输功率的图表。

 <img src="https://img-blog.csdnimg.cn/img_convert/6d78e85dcf57728a8ca2a991371a34c3.png" alt="img" style="zoom: 67%;" /> 

- 概述

  MQTT是IBM开发的一个即时通讯协议，有可能成为物联网的重要组成部分。该协议支持所有平台，几乎可以把所有联网物品和外部连接起来，被用来当做传感器和制动器之间通信的桥梁。

  MQTT协议是为大量计算能力有限，且工作在低带宽、不可靠的网络的远程传感器和控制设备通讯而设计的协议。有以下特点：

  - 使用发布/订阅消息模式，提供一对多的消息发布
  - 使用TCP/IP提供网络连接
  - 小型传输，开销很小（固定长度的头部是 2 字节），协议交换最小化，以降低网络流量，传输的内容最大为256MB。
  - 使用 Last Will 和 Testament 特性通知有关各方客户端异常中断的机制。

- 协议格式

MQTT协议控制报文的格式包含以下三个部分，以固定报头，可变报头和有效载荷，其中固定报文头是所有的控制报文都有， 可变报头和有效载荷都是部分控制报文包含。

固定报头

固定报头是由两字节组成，其格式组成如下:

 <img src="https://img-blog.csdnimg.cn/20191208205426570.png" alt="img" style="zoom:80%;" /> 

控制报文类型

第一个字节的二进制位7-4无符号整数表示控制报文的类型，具体类型对应的值为

 <img src="https://img-blog.csdnimg.cn/20191208205707460.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3FxXzQxMzM4MjQ5,size_16,color_FFFFFF,t_70" alt="img" style="zoom:80%;" /> 

标志

第一个字节的二进制位3-0包含每个MQTT控制报文类型特定的标志， 控制报文中的标志为必须按照如下表格进行设置，如果设置有问题，则接收者必须断开连接。

 <img src="https://img-blog.csdnimg.cn/2019120820580576.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3FxXzQxMzM4MjQ5,size_16,color_FFFFFF,t_70" alt="img" style="zoom:80%;" /> 

剩余长度

第二个字节表示当前报文剩余部分的字节数，包括可变报头和有效载荷。剩余长度不包括用于编码剩余长度字段本身的字节数。剩余长度字段使用一个变长度编码方案，对小于128的值使用单字节编码，超过128的值，最高有效未用于指示是否有更多的字节，因此每个字节可以编码128个数值和一个延续位，剩余长度字段最大4个字节。 举例：十进制64被编码为一个字节，十六进制表示为Ox40。十进制数字321编码为两个字节，最低有效位在前，第一个字节65+128=193，第二个字节为2。 剩余长度最大为256M的报文，而且报文是不支持分包处理的，所以MQTT协议并不适合一些数据量特别大的场景，比如视频直播等数据包比较大的场景。

可变报头

可变报头介于固定报头和有效载荷中间。不同的控制报文有着不同的可变报头，其中PacketId是一个在多个控制报文中存在一个报文。 PacketId包含两个字节，现在包含该字段的控制报文有，PUBLISH(Qos>0), PUBACK, PUBREC, PUBREL,PUBCOMP,SUBSCRIBE,SUBACK, UNSUBSCRIBE, UNSUBACK。

具体包含情况如下:
 <img src="https://img-blog.csdnimg.cn/20191208210731435.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3FxXzQxMzM4MjQ5,size_16,color_FFFFFF,t_70" alt="img" style="zoom:80%;" /> 

有效荷载

有效载荷即为应用消息。

- 实现方式

MQTT系统由与服务器通信的客户端组成，通常称服务器为“代理Broker”。客户可以是信息发布者Publish或订阅者Subscribe。每个客户端都可以连接到代理。

信息按主题层次结构组织。当发布者具有要分发的新数据时，它会将包含数据的控制消息发送到连接的代理。然后，代理将信息分发给已订阅该主题的任何客户端。发布者不需要有关于订阅者数量或位置的任何数据，而订阅者又不必配置有关发布者的任何数据。

MQTT传输的消息分为：主题（Topic）和负载（payload）两部分： （1）Topic，可以理解为消息的类型，订阅者订阅（Subscribe）后，就会收到该主题的消息内容（payload）； （2）payload，可以理解为消息的内容，是指订阅者具体要使用的内容。

- MQTT协议中的术语

订阅（Subscription）

订阅包含主题筛选器（Topic Filter）和最大服务质量（QoS）。订阅会与一个会话（Session）关联。一个会话可以包含多个订阅。每一个会话中的每个订阅都有一个不同的主题筛选器。

会话（Session）

每个客户端与服务器建立连接后就是一个会话，客户端和服务器之间有状态交互。会话存在于一个网络之间，也可能在客户端和服务器之间跨越多个连续的网络连接。

主题名（Topic Name）

连接到一个应用程序消息的标签，该标签与服务器的订阅相匹配。服务器会将消息发送给订阅所匹配标签的每个客户端。 系统主题：通过定义$SYS开头的主题可以查看一些系统信息，如客户端连接数量等， 详细介绍：github.com/mqtt/mqtt.g…

主题筛选器（Topic Filter）

一个对主题名通配符筛选器，在订阅表达式中使用，表示订阅所匹配到的多个主题。 多级匹配符 # 单级匹配符 + 

负载（Payload）

消息订阅者所具体接收的内容。

- 保留消息和最后遗嘱

保留消息 Retained Messages

MQTT中，无论是发布还是订阅都不会有任何触发事件。 1个Topic只有唯一的retain消息，Broker会保存每个Topic的最后一条retain消息。 发布消息时把retain设置为true，即为保留信息。每个Client订阅Topic后会立即读取到retain消息。如果需要删除retain消息，可以发布一个空的retain消息，因为每个新的retain消息都会覆盖最后一个retain消息。

最后遗嘱 Last Will & Testament

MQTT本身就是为信号不稳定的网络设计的，所以难免一些客户端会无故的和Broker断开连接。 当客户端连接到Broker时，可以指定LWT，Broker会定期检测客户端是否有异常。 当客户端异常掉线时，Broker就往连接时指定的topic里推送当时指定的LWT消息。

- 消息服务质量

 至多一次 

 <img src="https://img-blog.csdnimg.cn/20191208212246399.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3FxXzQxMzM4MjQ5,size_16,color_FFFFFF,t_70" alt="img" style="zoom:80%;" /> 

消息发布完全依赖底层TCP/IP网络。会发生消息丢失或重复。这一级别可用于如下情况，环境传感器数据，丢失一次读记录无所谓，因为不久后还会有第二次发送

至少一次

 <img src="https://img-blog.csdnimg.cn/20191208212310586.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3FxXzQxMzM4MjQ5,size_16,color_FFFFFF,t_70" alt="img" style="zoom:80%;" /> 

PUBACK消息是对QoS级别为1的PUBLISH消息的响应.PUBACK消息由服务器发送以响应来自发布端的PUBLISH消息，订阅端也会响应来自服务器的PUBLISH消息。当发布端收到PUBACK消息时，它会丢弃原始消息，因为它也被服务器接收（并记录）。

如果一定时间内，发布端或服务器没有收到PUBACK消息，则会进行重发。这种方式虽然确保了消息到达，但消息重复可能会发生。

只有一次
 <img src="https://img-blog.csdnimg.cn/20191208212337843.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3FxXzQxMzM4MjQ5,size_16,color_FFFFFF,t_70" alt="img" style="zoom:80%;" /> 

PUBREC消息是对QoS级别为2的PUBLISH消息的响应。它是QoS级别2协议流的第二个消息。 PUBREC消息由服务器响应来自发布端的PUBLISH消息，或订阅端响应来自服务器的PUBLISH消息。发布端或服务器收到PUBREC消息时，会响应PUBREL消息。

PUBREL消息是从发布端对PUBREC的响应，或从服务器对订阅端PUBREC消息的响应。 这是QoS 2协议流中第三个消息。当服务器从发布者收到PUBREL消息时，服务器会将PUBLISH消息发送到订阅端，并发送PUBCOMP消息到发布端。 当订阅端收到来自服务器的消息PUBREL时，使得消息可用于应用程序并将PUBCOMP消息发送到服务器。

PUBCOMP消息是服务器对来自发布端的PUBREL消息的响应，或订阅者对来自服务器的PUBREL消息的响应。 它是QoS 2协议流程中的第四个也是最后一个消息。当发布端收到PUBCOMP消息时，它会丢弃原始消息，因为它已经将消息发给了服务器。

在一些要求比较严格的计费系统中，可以使用此级别。在计费系统中，消息重复或丢失会导致不正确的结果。这种最高质量的消息发布服务还可以用于即时通讯类的APP的推送，确保用户收到且只会收到一次。

最后我们上代码（服务器端)

```java
/**
 * Created by Administrator on 17-2-10.
 */
 
import org.eclipse.paho.client.mqttv3.MqttClient;
import org.eclipse.paho.client.mqttv3.MqttConnectOptions;
import org.eclipse.paho.client.mqttv3.MqttDeliveryToken;
import org.eclipse.paho.client.mqttv3.MqttException;
import org.eclipse.paho.client.mqttv3.MqttMessage;
import org.eclipse.paho.client.mqttv3.MqttPersistenceException;
import org.eclipse.paho.client.mqttv3.MqttTopic;
import org.eclipse.paho.client.mqttv3.persist.MemoryPersistence;
/**
 *
 * Title:Server
 * Description: 服务器向多个客户端推送主题，即不同客户端可向服务器订阅相同主题
 * @author admin
 * 2019年12月8日下午17:50:15
 */
public class ServerMQTT {
 
    //tcp://MQTT安装的服务器地址:MQTT定义的端口号
    public static final String HOST = "tcp://0.0.0.0:61613";
    //定义一个主题
    public static final String TOPIC = "topic11";
    //定义MQTT的ID，可以在MQTT服务配置中指定
    private static final String clientid = "server11";
 
    private MqttClient client;
    private MqttTopic topic11;
    private String userName = "admin";
    private String passWord = "password";
 
    private MqttMessage message;
 
    /**
     * 构造函数
     * @throws MqttException
     */
    public ServerMQTT() throws MqttException {
        // MemoryPersistence设置clientid的保存形式，默认为以内存保存
        client = new MqttClient(HOST, clientid, new MemoryPersistence());
        connect();
    }
 
    /**
     *  用来连接服务器
     */
    private void connect() {
        MqttConnectOptions options = new MqttConnectOptions();
        options.setCleanSession(false);
        options.setUserName(userName);
        options.setPassword(passWord.toCharArray());
        // 设置超时时间
        options.setConnectionTimeout(10);
        // 设置会话心跳时间
        options.setKeepAliveInterval(20);
        try {
            client.setCallback(new PushCallback());
            client.connect(options);
 
            topic11 = client.getTopic(TOPIC);
        } catch (Exception e) {
            e.printStackTrace();
        }
    }
 
    /**
     *
     * @param topic
     * @param message
     * @throws MqttPersistenceException
     * @throws MqttException
     */
    public void publish(MqttTopic topic , MqttMessage message) throws MqttPersistenceException,
            MqttException {
        MqttDeliveryToken token = topic.publish(message);
        token.waitForCompletion();
        System.out.println("message is published completely! "
                + token.isComplete());
    }
 
    /**
     *  启动入口
     * @param args
     * @throws MqttException
     */
    public static void main(String[] args) throws MqttException {
        ServerMQTT server = new ServerMQTT();
 
        server.message = new MqttMessage();
        server.message.setQos(1);
        server.message.setRetained(true);
        server.message.setPayload("hello,topic11".getBytes());
        server.publish(server.topic11 , server.message);
        System.out.println(server.message.isRetained() + "------ratained状态");
    }
}
```

 客服端 

```java
/**
 *
 * Description:
 * @author admin
 * 2019年12月8日下午17:50:15
 */
 
import java.util.concurrent.ScheduledExecutorService;
import org.eclipse.paho.client.mqttv3.MqttClient;
import org.eclipse.paho.client.mqttv3.MqttConnectOptions;
import org.eclipse.paho.client.mqttv3.MqttException;
import org.eclipse.paho.client.mqttv3.MqttTopic;
import org.eclipse.paho.client.mqttv3.persist.MemoryPersistence;
 
public class ClientMQTT {
 
    public static final String HOST = "tcp://0.0.0.0:61613";
    public static final String TOPIC = "topic11";
    private static final String clientid = "client11";
    private MqttClient client;
    private MqttConnectOptions options;
    private String userName = "admin";
    private String passWord = "password";
 
    private ScheduledExecutorService scheduler;
 
    private void start() {
        try {
            // host为主机名，clientid即连接MQTT的客户端ID，一般以唯一标识符表示，MemoryPersistence设置clientid的保存形式，默认为以内存保存
            client = new MqttClient(HOST, clientid, new MemoryPersistence());
            // MQTT的连接设置
            options = new MqttConnectOptions();
            // 设置是否清空session,这里如果设置为false表示服务器会保留客户端的连接记录，这里设置为true表示每次连接到服务器都以新的身份连接
            options.setCleanSession(true);
            // 设置连接的用户名
            options.setUserName(userName);
            // 设置连接的密码
            options.setPassword(passWord.toCharArray());
            // 设置超时时间 单位为秒
            options.setConnectionTimeout(10);
            // 设置会话心跳时间 单位为秒 服务器会每隔1.5*20秒的时间向客户端发送个消息判断客户端是否在线，但这个方法并没有重连的机制
            options.setKeepAliveInterval(20);
            // 设置回调
            client.setCallback(new PushCallback());
            MqttTopic topic = client.getTopic(TOPIC);
            //setWill方法，如果项目中需要知道客户端是否掉线可以调用该方法。设置最终端口的通知消息
            options.setWill(topic, "close".getBytes(), 2, true);
 
            client.connect(options);
            //订阅消息
            int[] Qos  = {1};
            String[] topic1 = {TOPIC};
            client.subscribe(topic1, Qos);
 
        } catch (Exception e) {
            e.printStackTrace();
        }
    }
 
    public static void main(String[] args) throws MqttException {
        ClientMQTT client = new ClientMQTT();
        client.start();
    }
}
```

 回滚代码 

```java
/**
 *
 * Description:
 * @author admin
 * 2019年12月8日下午17:50:15
 */
 
import org.eclipse.paho.client.mqttv3.IMqttDeliveryToken;
import org.eclipse.paho.client.mqttv3.MqttCallback;
import org.eclipse.paho.client.mqttv3.MqttMessage;
 
/**
 * 发布消息的回调类
 *
 * 必须实现MqttCallback的接口并实现对应的相关接口方法CallBack 类将实现 MqttCallBack。
 * 每个客户机标识都需要一个回调实例。在此示例中，构造函数传递客户机标识以另存为实例数据。
 * 在回调中，将它用来标识已经启动了该回调的哪个实例。
 * 必须在回调类中实现三个方法：
 *
 *  public void messageArrived(MqttTopic topic, MqttMessage message)接收已经预订的发布。
 *
 *  public void connectionLost(Throwable cause)在断开连接时调用。
 *
 *  public void deliveryComplete(MqttDeliveryToken token))
 *  接收到已经发布的 QoS 1 或 QoS 2 消息的传递令牌时调用。
 *  由 MqttClient.connect 激活此回调。
 *
 */
public class PushCallback implements MqttCallback {
 
    public void connectionLost(Throwable cause) {
        // 连接丢失后，一般在这里面进行重连
        System.out.println("连接断开，可以做重连");
    }
 
    public void deliveryComplete(IMqttDeliveryToken token) {
        System.out.println("deliveryComplete---------" + token.isComplete());
    }
 
    public void messageArrived(String topic, MqttMessage message) throws Exception {
        // subscribe后得到的消息会执行到这里面
        System.out.println("接收消息主题 : " + topic);
        System.out.println("接收消息Qos : " + message.getQos());
        System.out.println("接收消息内容 : " + new String(message.getPayload()));
    }
}
```

 服务端控台信息 

 ![img](https://img-blog.csdnimg.cn/20191215201735706.png) 

 客户端信息 

 ![img](https://img-blog.csdnimg.cn/20191215201753727.png) 

 web页面后台信息 

 ![img](https://img-blog.csdnimg.cn/2019121520183059.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3FxXzQxMzM4MjQ5,size_16,color_FFFFFF,t_70) 

topic创建成功

测试成功 

###### EMQ X：

- 单节点部署

  - zip压缩包解压至linux

  - 进入bin目录

  - ```shell
    ./emqx start 运行节点
    显示运行success
    ./emqx_ctl status 查看节点状态
    显示on running
    ```

  - 关闭匿名认证

    - 匿名认证指任何人都可以匿名方式访问EMQ Broker，是很危险及不安全的操作
    - 进入etx目录，找到emqx.conf文件，修改allow_anonymous=false
    - ![1652058965355](C:\Users\dell\AppData\Roaming\Typora\typora-user-images\1652058965355.png)
    - 保存，重新进入bin，./emqx restart，重启节点更新此配置
    - 点击DashBoard工具里的websocket测试工具，连接反馈认证失败，即配置更新成功
    - ![1652059138733](C:\Users\dell\AppData\Roaming\Typora\typora-user-images\1652059138733.png)

  - 登录认证之用户名及密码

    - 注意，认证方式是有多种的

      - EMQ X 支持的认证方式： 

        **内置数据源** 

        Username 认证 

        Cliend ID 认证 

        **使用配置文件与 EMQ X 内置数据库提供认证数据源，通过 HTTP API 进行管理，足够简单轻量。** 

        **外部数据库** 

        LDAP 认证 

        MySQL 认证 

        PostgreSQL 认证 

        Redis 认证 

        MongoDB 认证 

        **外部数据库可以存储大量数据，同时方便与外部设备管理系统集成。** 

        **其他** 

        HTTP 认证 

        JWT 认证 

        **JWT 认证可以批量签发认证信息，HTTP 认证能够实现复杂的认证鉴权逻辑。** 

        **更改插件配置后需要重启插件才能生效，部分认证鉴权插件包含 ACL 功能** 

        **认证结果** 

        任何一种认证方式最终都会返回一个结果： 

        认证成功：经过比对客户端认证成功 

        认证失败：经过比对客户端认证失败，数据源中密码与当前密码不一致忽略认证（ignore）：当前认证方式中未查找到认证数据，无法显式判断结果是成功还是失败，交由认 

        证链下一认证方式或匿名认证来判断

    - **现在开启内部数据源username及password认证功能**，需要去DashBoard先运行emqx_auth_username插件以开启此功能

    - ![1652060359735](C:\Users\dell\AppData\Roaming\Typora\typora-user-images\1652060359735.png)

    - 内部数据源认证emqx提供了两种方式，一种是进入etc/plugins目录，在emqx_auth_username.conf配置中明文添加用户名及密码，这是不安全的，不推荐

      - <img src="C:\Users\dell\AppData\Roaming\Typora\typora-user-images\1652061173230.png" alt="1652061173230" style="zoom:67%;" />

      - 一种是使用http api的形式往内置数据源中添加用户（推荐）

        - ```http
          @hostname = 192.168.0.143
          @port=18083 
          @contentType=application/json
          @userName=admin 
          @password=public 
          #############查看已有用户认证数据############## 
          GET http://{{hostname}}:{{port}}/api/v4/auth_username HTTP/1.1 
          Content-Type: {{contentType}} 
          Authorization: Basic {{userName}}:{{password}}
          ########添加用户认证数据############## 
          POST http://{{hostname}}:{{port}}/api/v4/auth_username HTTP/1.1 
          Content-Type: {{contentType}} 
          Authorization: Basic {{userName}}:{{password}} 
          
          { 
              "username": "user", 
              "password": "123456" 
          }
          ###########更改指定用户名的密码############# 
          PUT http://{{hostname}}:{{port}}/api/v4/auth_username/user HTTP/1.1 
          Content-Type: {{contentType}} 
          Authorization: Basic {{userName}}:{{password}} 
          
          { 
              "password": "user" 
          }
          ###########查看指定用户名信息############# 
          GET http://{{hostname}}:{{port}}/api/v4/auth_username/user HTTP/1.1 
          Content-Type: {{contentType}} 
          Authorization: Basic {{userName}}:{{password}}
          ###########删除指定的用户信息############# 
          DELETE http://{{hostname}}:{{port}}/api/v4/auth_username/user HTTP/1.1 
          Content-Type: {{contentType}} 
          Authorization: Basic {{userName}}:{{password}}
          ```

        - 可以在成功后去DashBoard进行尝试登录，状态显示已连接

          - ![1652063776369](C:\Users\dell\AppData\Roaming\Typora\typora-user-images\1652063776369.png)
          - ![1652064065737](C:\Users\dell\AppData\Roaming\Typora\typora-user-images\1652064065737.png)

        - 登录成功后，亦可使用mqttx客户端来进行登录验证

          - 值得注意的一点是多个客户端可以共用一个用户名和密码，这个用户名和密码在这里更多的是一种认证的象征，即通过此方式来实现你的客户端与EMQ X的连接

    - **现在开启clientId及password认证方式**

      - DashBoard启动emqx_auth_clientid插件

      - 同样的，认证数据的添加分为两种，这里还是推荐使用http api来进行添加

      - ```http
        ####添加clientId和密码##### 
        POST http://{{hostname}}:{{port}}/api/v4/auth_clientid HTTP/1.1 
        Content-Type: {{contentType}} 
        Authorization: Basic {{userName}}:{{password}} 
        
        { 
            "clientid": "emq-client1", 
            "password": "123456" 
        }
        #############获取所有详细信息######## 
        GET http://{{hostname}}:{{port}}/api/v4/auth_clientid HTTP/1.1 
        Content-Type: {{contentType}} 
        Authorization: Basic {{userName}}:{{password}}
        #############更改指定 Client ID 的密码######## 
        PUT http://{{hostname}}:{{port}}/api/v4/auth_clientid/emq-client1 HTTP/1.1 
        Content-Type: {{contentType}} 
        Authorization: Basic {{userName}}:{{password}} 
        
        { 
            "password": "654321" 
        }
        #############获取指定ClientId详细信息######## 
        GET http://{{hostname}}:{{port}}/api/v4/auth_clientid/emq-client1 HTTP/1.1 
        Content-Type: {{contentType}} 
        Authorization: Basic {{userName}}:{{password}}
        #############删除指定的client信息######## 
        DELETE http://{{hostname}}:{{port}}/api/v4/auth_clientid/emq-client1 HTTP/1.1 
        Content-Type: {{contentType}} 
        Authorization: Basic {{userName}}:{{password}}
        ```

    - **现在使用http认证方式**，需要打开emqx_auth_http插件

      - 打开后，需要修改etc/plugins目录下emqx_auth_http.conf，主要是需要去修改其中默认的请求路径前的ip，修改成你将搭建的协助emqx认证的微服务的主机的ip

      - 修改完，创建微服务并配置端口及application name

        - ```yml
          server:
            port: 8991
          spring:
            application:
              name: zenx-emqx
          ```

        - 编写controller，值得注意的是这里黑马的老师是进行了 @PostConstruct项目运行前即初始化了几个账户来用于认证及核对，在正式的应用中，可以导入相关数据库从数据库中查询相关的账户数据来认证，这样也方便与其他系统进行整合对接，还有密码也是应该进行加密处理来存储及认证

        - ```java
          package com.zenx.emq.controller.mqtt;
          
          import org.slf4j.Logger;
          import org.slf4j.LoggerFactory;
          import org.springframework.http.HttpStatus;
          import org.springframework.http.ResponseEntity;
          import org.springframework.util.StringUtils;
          import org.springframework.web.bind.annotation.PostMapping;
          import org.springframework.web.bind.annotation.RequestMapping;
          import org.springframework.web.bind.annotation.RequestParam;
          import org.springframework.web.bind.annotation.RestController;
          
          import javax.annotation.PostConstruct;
          import java.util.HashMap;
          
          /**
           * @author lmf
           * @version 1.0
           * @date 2022/5/9 14:25
           */
          @RestController
          @RequestMapping("/mqtt")
          public class AuthController {
          
              private static final Logger log= LoggerFactory.getLogger(AuthController.class);
          
              private HashMap<String,String> users;
          
              @PostConstruct
              public void init(){
                  users=new HashMap<>();
                  users.put("user","123456");
                  users.put("emq-client2","123456");
                  users.put("emq-client3","123456");
              }
          
              @PostMapping("/auth")
              public ResponseEntity auth(@RequestParam("clientid") String clientid,
                                         @RequestParam("username") String username,
                                         @RequestParam("password") String password){
              log.info("emqx http组件开始调用zenx-emqx微服务进行客户端登录认证，clentid={}，username={}，password={}",clientid,username,password);
                  String value = users.get(username);
                  if (StringUtils.isEmpty(value)) {
                      return new ResponseEntity(HttpStatus.UNAUTHORIZED);
                  }
                  if (!value.equals(password)) {
                      return new ResponseEntity(HttpStatus.UNAUTHORIZED);
                  }
                  return new ResponseEntity(HttpStatus.OK);
              }
          }
          
          ```

    - 接下来要解决的是客户端，此前我们的测试都是用的pc的mqttx客户端来进行，非常方便，但在实际场景中，所谓的客户端指的是那些传递消息的物联网设备，大多数情况下是搭载在设备上的嵌入式设备芯片中的运行的程序来担任客户端的角色，这样的客户端程序即SDK，不同语言的都有，比如C、Java

    - 以Java为例，来编写一个客户端的程序

    - ```java
      package com.zenx.emq.client;
      
      import com.zenx.emq.properties.MqttProperties;
      import org.eclipse.paho.client.mqttv3.*;
      import org.eclipse.paho.client.mqttv3.persist.MemoryPersistence;
      import org.slf4j.Logger;
      import org.slf4j.LoggerFactory;
      import org.springframework.beans.factory.annotation.Autowired;
      import org.springframework.stereotype.Component;
      
      import javax.annotation.PostConstruct;
      
      /**
       * @author lmf
       * @version 1.0
       * @date 2022/5/9 15:29
       */
      @Component
      public class EmqClient {
          private static final Logger log = LoggerFactory.getLogger(EmqClient.class);
          private IMqttClient mqttClient;
      
          @Autowired
          MqttProperties mqttProperties;
      
          @Autowired
          MqttCallback mqttCallback;
      
          @PostConstruct
          public void init(){
              MqttClientPersistence memoryPersistence = new MemoryPersistence();
              try {
                  //TODO clientId此处是固定的，在实际开发场景中，客户端部署在多台机器上，所以应进行生成或指定来确保其唯一性
                  mqttClient=new MqttClient(mqttProperties.getBrokerUrl(),mqttProperties.getClientId(),memoryPersistence);
              } catch (MqttException e) {
                 log.error("初始化客户端mqttClient对象失败，errormsg={},brokerUrl={},clientId={}",e.getMessage(),mqttProperties.getBrokerUrl(),mqttProperties.getClientId());
              }
          }
      
          public void connect(String username,String password){
              MqttConnectOptions options = new MqttConnectOptions();
                  options.setAutomaticReconnect(true);
                  options.setUserName(username);
                  options.setPassword(password.toCharArray());
                  options.setCleanSession(true);
                  mqttClient.setCallback(mqttCallback);
              try {
                  mqttClient.connect(options);
              } catch (MqttException e) {
                  log.error("mqtt客户端连接服务端失败，errormsg={}",e.getMessage());
              }
          }
      }
      ```

    - 编写信息回调函数

    - ```java
      package com.zenx.emq.client;
      
      import org.eclipse.paho.client.mqttv3.IMqttDeliveryToken;
      import org.eclipse.paho.client.mqttv3.MqttCallback;
      import org.eclipse.paho.client.mqttv3.MqttMessage;
      import org.slf4j.Logger;
      import org.slf4j.LoggerFactory;
      import org.springframework.stereotype.Component;
      
      /**
       * @author lmf
       * @version 1.0
       * @date 2022/5/9 16:59
       */
      @Component
      public class MessageCallBack implements MqttCallback {
          private static final Logger log = LoggerFactory.getLogger(MessageCallBack.class);
      
          @Override
          public void connectionLost(Throwable throwable) {
              //资源的清理 重连
              log.info("丢失了对服务端的连接");
          }
      
          @Override
          public void messageArrived(String topic, MqttMessage mqttMessage) throws Exception {
              log.info("订阅者订阅到了消息，topic={},messgaeId={},qos={},payload={}", topic, mqttMessage.getId(), mqttMessage.getQos()
                      , new String(mqttMessage.getPayload()));
          }
      
          @Override
          public void deliveryComplete(IMqttDeliveryToken token) {
              int messageId = token.getMessageId();
              String[] topics = token.getTopics();
              log.info("消息发布完成，messgaeid={},topics={}", messageId, topics);
      
          }
      }
      ```

    - 由于qos是固定是0，1，2，编写一个枚举类来代表

    - ```java
      package com.zenx.emq.enums;
      
      /**
       * @author lmf
       * @version 1.0
       * @date 2022/5/9 16:37
       */
      public enum QosEnum {
          QoS0(0),QoS1(1),QoS2(2);
      
          private final int value;
          QosEnum(int value){
              this.value=value;
          }
          public int value(){
              return this.value;
          }
      }
      
      ```

    - 编写连接服务端需要的配置类MqttProperties

    - ```java
      package com.zenx.emq.properties;
      
      import org.springframework.boot.context.properties.ConfigurationProperties;
      import org.springframework.context.annotation.Configuration;
      
      /**
       * @author lmf
       * @version 1.0
       * @date 2022/5/9 15:33
       */
      @Configuration
      @ConfigurationProperties(prefix = "mqtt")
      public class MqttProperties {
          private String brokerUrl;
          private String clientId;
          private String username;
          private String password;
      
          @Override
          public String toString() {
              return "MqttProperties{" +
                      "brokerUrl='" + brokerUrl + '\'' +
                      ", clientId='" + clientId + '\'' +
                      ", username='" + username + '\'' +
                      ", password='" + password + '\'' +
                      '}';
          }
      
          public String getBrokerUrl() {
              return brokerUrl;
          }
      
          public void setBrokerUrl(String brokerUrl) {
              this.brokerUrl = brokerUrl;
          }
      
          public String getClientId() {
              return clientId;
          }
      
          public void setClientId(String clientId) {
              this.clientId = clientId;
          }
      
          public String getUsername() {
              return username;
          }
      
          public void setUsername(String username) {
              this.username = username;
          }
      
          public String getPassword() {
              return password;
          }
      
          public void setPassword(String password) {
              this.password = password;
          }
      }
      ```

      **利用发布订阅的ACL机制来对客户端的发布订阅主题进行权限控制，这个机制与之前的认证如出一辙并且其配置文件和认证的配置文件是同一个，配置方式就不复制了**

    - ACL规则

      - ACL 是允许与拒绝条件的集合，EMQ X 中使用以下元素描述 ACL 规则： 

      - ```yml
        # Allow-Deny Who Pub-Sub Topic 
         "允许(Allow) / 拒绝(Deny)" "谁(Who)" "订阅(Subscribe) / 发布(Publish)" "主题列表(Topics)"
        ```

      - 修改默认全局配置，类似之前的支持匿名认证，很危险，需要关闭

      - ![1652150492004](C:\Users\dell\AppData\Roaming\Typora\typora-user-images\1652150492004.png)

      - 超级用户的概念指其不受ACL机制限制，直接拥有所有频道的订阅及发布权限

      - 针对频繁会进行发布和订阅并且又想对进行ACL限制的客户端来说，ACL还有个缓存机制，可以在某个客户端命中某条规则后，将规则缓存至内存中，来提高ACL性能

      - ![1652151142435](C:\Users\dell\AppData\Roaming\Typora\typora-user-images\1652151142435.png)

      - ![1652151249657](C:\Users\dell\AppData\Roaming\Typora\typora-user-images\1652151249657.png)

      - 内置ACL的适用场景

      - ![1652151536230](C:\Users\dell\AppData\Roaming\Typora\typora-user-images\1652151536230.png)

      - 除去这种方式还有协同http插件及配置来进行，即通过逻辑，配合emqx_auth_http.conf来编写接口来返回相应的结果，来对权限进行控制

      - ```java
            /**
             * 验证是否为超级用户
             * @param clientid
             * @param username
             * @return
             */
            @PostMapping("superuser")
            public ResponseEntity superuser(@RequestParam("clientid") String clientid,
                                            @RequestParam("username") String username) {
                log.info("emqx 查询是否是超级用户,clientid={},username={}", clientid, username);
                if (clientid.contains("admin") || username.contains("admin")) {
                    log.info("用户{}是超级用户", username);
                    return new ResponseEntity(HttpStatus.OK);
                } else {
                    log.info("用户{}不是超级用户", username);
                    return new ResponseEntity(HttpStatus.UNAUTHORIZED);
                }
            }
        
            /**
             * 客户端订阅or接受权限设定
             * @param access
             * @param username
             * @param clientid
             * @param ipaddr
             * @param topic
             * @param mountpoint
             * @return
             */
            @PostMapping("acl")
            public ResponseEntity acl(@RequestParam("access")int access,
                                      @RequestParam("username")String username,
                                      @RequestParam("clientid")String clientid,
                                      @RequestParam("ipaddr")String ipaddr,
                                      @RequestParam("topic")String topic,
                                      @RequestParam("mountpoint")String mountpoint){
                log.info("emqx 发起客户端操作授权查询请求，access={},username={},clientid={},ipaddr={},topic={},mountpoint={}",access
                ,username,clientid,ipaddr,topic,mountpoint);
                if (username.equals("emq-client2")&&topic.equals("testtopic/#")&&access==1) {
                log.info("客户端{}有权限订阅{}",username,topic);
                return new ResponseEntity(HttpStatus.OK);
                }
                if (username.equals("emq-client3")&&topic.equals("testtopic/123")&&access==2) {
                    log.info("客户端{}有权限订阅{}",username,topic);
                    return new ResponseEntity(HttpStatus.OK);
                }
                 //log.info("客户端{},username={},没有权限对主题{}进行{}操作",clientid,username,topic,access==1?"订阅":"发布");
                
                // return new ResponseEntity(HttpStatus.UNAUTHORIZED);
                return new ResponseEntity(HttpStatus.OK);
            }
        ```

  **接下来需要开发的WebHook功能，即用于emqx与其他微服务之间的整合，通过WebHook监听emqx的相关事件来进行其他系统需要的业务**

  - **有需要注意的就是，首先需要打开这个webhook的插件，并且修改请求到的微服务的路径**

  - ![1652163649848](C:\Users\dell\AppData\Roaming\Typora\typora-user-images\1652163649848.png)

  - 然后需要注意的就是，因为webhook监听事件的不同，其请求体的数据内容也不一样，所以我们在开发api时可以使用hashmap来接收并得到对应的需要的数据，即对应的不同事件的key

  - 编写以监控客户端连接和下线案例的代码

  - ```java
    package com.zenx.emq.controller.mqtt;
    
    import org.slf4j.Logger;
    import org.slf4j.LoggerFactory;
    import org.springframework.web.bind.annotation.*;
    
    import java.util.HashMap;
    import java.util.Map;
    import java.util.Objects;
    
    /**
     * @author lmf
     * @version 1.0
     * @date 2022/5/10 14:30
     */
    @RestController
    @RequestMapping("mqtt")
    public class WebHookController {
        private static final Logger log= LoggerFactory.getLogger(WebHookController.class);
        private Map<String,Boolean> clientStatus = new HashMap<>();
    
        @PostMapping("/webhook")
        public void hook(@RequestBody Map<String, Object> params){
        log.info("emqx 触发 webhook，请求体数据={}",params);
        String action=(String) params.get("action");
        String clientId=(String) params.get("clientid");
            if (action.equals("client_connected")) {
                log.info("客户端{}接入本系统",clientId);
                clientStatus.put(clientId,true);
            }
            if (action.equals("client_disconnected")) {
                log.info("客户端{}下线",clientId);
                clientStatus.put(clientId,false);
            }
        }
    
        @GetMapping("/allStatus")
        public Map getStatus(){
           return this.clientStatus;
        }
    }
    ```

  - 集群部署

    - 为了实现EMQ X的分布式集群，EMQ X 维护了几个与之相关的数据结构：**订阅表，路由表，主题树。**

      **★ 订阅表只存在于订阅者所在的 EMQ X 节点上**

      **★而同一集群的所有节点，都会复制一份主题(Topic) -> 节点(Node) 映射的路由表**

      **★除路由表之外，EMQ X 集群中的每个节点也会维护一份主题树(Topic Trie) 的备份。** 

      **例如下述主题订阅关系**:

      <img src="C:\Users\dell\AppData\Roaming\Typora\typora-user-images\1652172072548.png" alt="1652172072548" style="zoom:67%;" />

      - 方式主要为自动发现和手动，目前有个bug是多ip之间只能两个节点，单ip可以多节点，没有解决

#### 我在开发时遇到的问题及解决方案：

点餐项目购物车操作功能：

- 如何确保库存的一致性？（超卖问题）
  - 超卖问题：当数据库的数据只有一份，这时并发下单，造成多个订单产生的问题
  - 有一个值得注意的地方是，这里对库存数量进行操作采用的是可以对长整型进行原子性操作的`JUC`下的类`AtomicLong`，在32位操作系统中，64位的long 和 double 变量由于会被`JVM`当作两个分离的32位来进行操作，所以不具有原子性。而使用`AtomicLong`能让long的操作保持原子型。这里通过redessionClient来获得这个类，调用里面的incrementandGet()/decrementandGet()，完成自增和自减的原子性操作
    - 原子性操作是指一个或某几个操作只能在一个线程执行完之后，另一个线程才能开始执行该操作，是串行的
    - 底层调用了redis的`DECR`和`INCR`的指令，实现原子计数器

  - 操作购物车时，由于涉及订单的写操作，需要给订单加锁
  - 操作购物车会涉及库存数的相应联动，库存是否>=0，如果不>=0，此前的incr操作需要再执行dcer返回，再抛出异常

```
开发购物车模块时，操作购物车里的商品阶段，当时开发采用了联合锁来进行的实现
在测试阶段也没有问题，但是我发现这个联合锁没有必要加，只需要对订单进行加锁即可
没有必要对库存操作也进行加锁，因为我们当时采用的是AtomicLong这个封装原子类来进行计数
本身实现的操作就是原子性的，当时提出来以后组长同意了这个观点，把锁拿掉了

后面也去深入了解了一下那个时候用的AtomicLong的原理，是基于计数器模式实现的
还挺有用的，我们可以通过这个指令实现一些类似限制用户登录次数，提现次数的功能
----------------------------------------------------------------------------
FUNCTION LIMIT_API_CALL(ip)
ts = CURRENT_UNIX_TIME()
keyname = ip+":"+ts
current = GET(keyname)

IF current != NULL AND current > 10 THEN
    ERROR "too many requests per second"
END

IF current == NULL THEN
    MULTI
        INCR(keyname, 1)
        EXPIRE(keyname, 1)
    EXEC
ELSE
    INCR(keyname, 1)
END

PERFORM_API_CALL()
```

咨询类项目扩展自媒体平台评论管理功能：

```
在自媒体平台能够加载当前自媒体用户发布的文章的所有评论，去进行一个管理
然后查询的时候需要能够拿到用户的id去查询它的自媒体账户的id，然后查到文章的集合
当时尝试了一下用kafka来发，就是从登陆那边进行一个id的发送，但是发现在页面刷新的时候就获取不到了
然后分析了一下最后选择从ThreadLocal去拿，那个时候对这个类的理解不是很深刻，ThreadLocal可以存储当前线程的一些数据
```

### 前端

##### Webpack

**什么是Webpack？**

- 现代 javascript 应用程序的 **静态模块打包器 (module bundler)**，即打包你的前端项目，使其更小。
-  不仅仅是**JavaScript**文件，我们的**CSS**、**图片**、**json文件**等等在webpack中都可以被当做**模块**来使用。 
-  Webpack最初被设计为JavaScript模块打包工具，但现在已经发展成为一种通用的资源打包工具，可以处理各种类型的文件，例如CSS、图像和字体等。 

**实际开发中需要自己配置webpack吗？**

- 实际开发中会使命令行工具（俗称 CLI）一键生成带有 webpack 的项目 
- 开箱即用，所有 webpack 配置项都是现成的！ 
- 我们只需要知道 webpack 中的基本概念即可！

**webpack.config.js文件是用来干嘛的？**

- webpack.config.js 是 webpack 的配置文件。webpack 在真正开始打包构建之前，会先读取这个配置文件， 

  从而基于给定的配置，对项目进行打包。 

**为什么vue创建的项目中没有webpack.config.js，而是vue.config.js？**

- vue创建的项目是通过vue cli的，官方文档里给出了这样的解释（如图），也就是后续打包通过vue.config.js构建即可了
- ![1682392770499](C:\Users\dell\Desktop\asserts\1682392770499.png)
  - 即，创建项目时，已经集成了webpack和webpack-dev-server，图中的@vue/cli-service已经在package.json中，如图
  - <img src="C:\Users\dell\Desktop\asserts\1682392974216.png" alt="1682392974216" style="zoom:50%;" />

##### Vue

**vue创建的项目中的webpack-dev-server作用是什么？**

 Webpack-dev-server 是一个开发服务器，它可以为 Webpack 打包后的应用程序提供服务，使开发人员可以在本地环境中进行开发和测试。它提供了许多有用的功能，如**自动刷新**、**热替换**和**实时重载**等。 

 **vue创建的项目中的babel.config.js 作用是什么？**

babel.config.js 是用来配置 Babel 转译器的文件，它包含了一个 JavaScript 对象，其中定义了 Babel 的配置选项。Babel 可以将 ECMAScript 2015+（ES6+）的代码转换为向后兼容的 JavaScript 代码，以便在现有环境中运行。 

 **vue创建的项目中的jsconfig.js 作用是什么？**

是一个用于配置 JavaScript 语言服务的配置文件，它可以让编辑器（如 VS Code）更好地理解和支持 JavaScript 代码。 

 **vue创建的项目中的package-lock.json作用是什么？package.json作用是什么？这两者有什么区别 ？**

`package.json` 和 `package-lock.json` 都是 Node.js 项目中的重要文件，它们的作用如下：

- `package.json`：用于描述项目的元信息和依赖信息。该文件通常包含项目的名称、版本号、作者、许可证等信息，还包含了项目依赖的第三方库（即所谓的 `dependencies` 和 `devDependencies`）和脚本命令等信息。当执行 `npm install` 命令时，npm 会根据 `package.json` 中的依赖信息安装项目所需的第三方库，并将它们保存到 `node_modules` 目录中。
- `package-lock.json`：用于锁定项目依赖的版本信息。该文件是 npm 5 及以上版本中新增的特性，它会记录当前项目的所有依赖库的精确版本号，包括所有间接依赖库，以确保不同环境中安装的依赖库版本一致。在执行 `npm install` 命令时，npm 会根据 `package-lock.json` 中的版本信息来安装依赖库，以避免出现依赖库版本不一致的问题。

总的来说，`package.json` 用于描述项目的元信息和依赖信息，而 `package-lock.json` 则用于记录依赖库的精确版本号，以确保不同环境中安装的依赖库版本一致。两者的主要区别在于：

- `package.json` 中记录的依赖信息是模糊的（即只指定了依赖库的大版本号），而 `package-lock.json` 中记录的版本信息是精确的，它会指定依赖库的精确版本号。
- `package.json` 是开发者手动维护的文件，而 `package-lock.json` 是 npm 自动生成的文件，它会在执行 `npm install` 命令时自动生成和更新。

 **vue创建的项目中的.browserslistrc是啥 ？**

 `.browserslistrc` 是一个配置文件，用于指定项目的目标浏览器和 Node.js 版本。该文件通常被用于各种前端工具中，例如 Babel、Autoprefixer、eslint-plugin-compat 等，以便这些工具可以根据配置自动将代码转换成目标浏览器或 Node.js 版本兼容的代码。 

 **webpack 默认只能打包处理以 .js 后缀名结尾的模块。其他非 .js 后缀名结尾的模块， webpack 默认处理不了，需要调用 loader 加载器才可以正常打包，这些配置vue cli创建的项目的vue.config.js配置文件不需要去配置loader吗 ？**

是的，Vue CLI 已经内置了一些常用的 loader，并在 `vue.config.js` 中进行了相应的配置。这些配置已经可以满足大部分项目的需求，通常情况下无需对其进行修改。 

 **vue cli创建的vue项目下的开发和生产模式是如何区分的 ?**

Vue CLI创建的Vue项目默认包含两个模式：开发模式和生产模式。在开发模式下，Vue CLI会启动一个开发服务器，该服务器会自动监视你的代码更改，并在保存代码后重新编译和刷新浏览器。此外，开发模式下的应用程序通常包含更多的调试信息和错误提示，以帮助开发人员更容易地调试应用程序。

在生产模式下，Vue CLI会进行一些额外的步骤来优化应用程序的性能和大小。例如，它会自动压缩和混淆代码，删除未使用的代码和资源，并使用缓存来提高应用程序的加载速度。此外，生产模式下的应用程序通常不包含调试信息和错误提示，以减小应用程序的大小。

你可以通过运行`npm run serve`来启动开发模式下的服务器，而生产模式下的应用程序可以通过运行`npm run build`命令来构建。构建后，你将在项目的`dist`目录下找到生成的生产模式代码。

**vue的特性是啥？**

- 数据驱动视图
- 双向数据绑定

**vue的核心原理？**

![1682469775900](C:\Users\dell\Desktop\asserts\1682469775900.png)

 **spring boot是java的应用于后端开发的脚手架，那么vue cli创建的vue项目也可以理解成应用于前端开发的脚手架吗 ？**

是的，您的理解是正确的。Vue CLI创建的Vue项目可以被视为一个用于前端开发的脚手架，类似于Spring Boot是Java应用于后端开发的脚手架。

Vue CLI提供了一些默认配置和插件，以帮助开发者更快地创建和开发Vue.js项目。Vue CLI创建的Vue项目可以包括单页应用程序（SPA）和多页应用程序（MPA），并提供了一些方便的命令行工具，以帮助开发者更轻松地构建、测试和部署应用程序。

类似地，Spring Boot提供了一些默认配置和插件，以帮助开发者更快地创建和开发Java Web应用程序和微服务。Spring Boot提供了一些方便的特性，如自动配置、依赖注入等，以帮助开发者更轻松地处理业务逻辑和构建高效、可靠的应用程序。