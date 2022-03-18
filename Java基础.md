## Java基础

来自于**疯狂的Java讲义精粹**

## 一：Java语言概述

## 二：数据类型和运算符

本章要点：

- 注释的重要性和用途
- 单行注释语法和多行注释语法
- 文档注释的语法与常用的javadoc标记
- javadoc命令的用法
- 掌握查看API文档的方法
- 数据类型的两大类
- 8个基本类型及其各自的注意点
- 自动类型转换
- 强制类型转换
- 表达式类型的自动提升
- 直接量的类型和赋值
- Java提供的基本运算符
- 运算符的结合性和优先级

**Java是一门强类型语言**

强类型包含俩方面的含义：

1. 所有变量必须先申明、后使用
2. 制定类型的变量只能接受类型与之匹配的值

强类型优点在于，可以在编译过程中发现源代码的错误，从而保证程序更加健壮。

### 2.1注释

注释是什么:

- 编写程序的时候，用以说明某段代码的作用，或者说明某个类的用途、某个方法的功能，以及该方法的参数和返回值的数据类型与意义等

为什么添加注释，做出以下三点考虑：

1. 不要过于相信自己的理解力
2. 可读性第一，效率第二 
   - 软件开发是团队协作，沟通十分重要，需要写的代码能够被别人理解
3. 代码即文档

Java提供了三中类型注释：

- 单行注释；
- 多行注释
- 文档注释；

#### 2.1.1 单行注释和多行注释

单行注释：在程序中注释一行代码，将 // 放在需要注释的内容之前

多行注释：一次性将程序中多行代码注释，使用 /* 和*/ 将需要注释的内容包含起来

例子：

```java
public class CommentTest{
    /*
   	这里面的内容都是多行注释
   	这里也是
    */
    public static void main(String[]args){
        //这是简单注释
        System.out.println("Hello,World!");
        //System.out.println("这行代码被注释了，不会被编译、执行");      
    }
}
```

除此之外，添加注释也是调试程序的一个重要方式。

通过将有问题的代码注释起来分别调试进行来判断代码的错误

#### 2.1.2文档注释

文档注释的作用：

- 如果编写Java源代码时添加了文档注释，然后通过JDK提供的javadoc工具可以将源代码里的文档注释提取成一份系统的API文档

文档注释生成API文档的特点：

- javadoc工具默认只处理以public和protected修饰的类、接口、方法、Field、构造器和内部类之前的文档注释

  **原因**：由于文档注释是用于生成API文档，而API文档用于说明类、方法、Field的功能，并且只有public和protected修饰的内容才是希望暴露的

文档注释使用：以/** 开始，以 */ 结尾，中间部分会被提取到API文档中

**略：不想写了 了解即可**



### 2.2标识符和关键字







































## 三：流程控制和数组

## 四：面向对象（上）

本章要点：

- 定义类、Field和方法
- 创建并使用对象
- 对象和引用
- 方法必须属于类和对象
- Java方法的参数传递机制
- 递归方法
- 方法的重载
- 实现良好的封装
- 使用package和import
- 构造器的作用和构造器重载
- 继承的特点和用法
- 重写父类方法
- super关键字的用法
- 继承和多态
- 向上转型和强类型转换
- 继承和组合的关系
- 使用组合来实现复用
- 构造器和初始化块的作用和区别
- 静态初始化块

### 4.1类与对象

面相对象的程序设计有俩个重要概念：

- 类（Class）
- 对象（Object，也被称为实例，instance）

类是某一批对象的抽象，类是一种概念，对象才是具体存在的实体

Java是面向对象的程序设计语言，类和对象是面向对象和核心

定义类

```java
[修饰词] class类名{

	零到多个构造器定义
	零到多个Field
	零到多个方法
}
```

修饰词：

- public
- final
- abstract

类三中常见的成员：

- 构造器

  - 类创建的根本途径

    没有系统自带，写了就系统自带的没有

  - 格式：

    ```java
    [修饰符] 构造器名(形参列表){
    //执行体
    }
    ```

  - 修饰符

  - 构造器名：和类名一样

  - 形参列表

  构造器不能定义返回值类型，也不能使用void定义构造器没有返回值

- Field

  - Field用于定义该类或该类的实例所包含的状态数据

  - 格式：

  ```java
  [修饰词] Field类型 Field名 [= 默认值];
  ```

  - 修饰词：可以省略，public、protected、private、static、final，其中public、protected、private只能出现一个，可以组合修饰Field
  - Field类型：Field类型可以是Java语言允许的任何数据类型，包括基本数据类型和现在介绍的引用类型
  - Field名：Field合法标识符就行，**小驼峰最好**
  - 默认值：定义Field可以制定一个默认值

- 方法

  - 方法用于定义该类或该类的实例的行为特征或功能实现

  - 格式：

    ```java
    [修饰词] 方法返回值类型 方法名(形参列表){
    	
    	//由零到多条可执行性语句组成的方法体
    }
    ```

  - 修饰词：可以省略，public、protected、private、static、final，其中public、protected、private只能出现一个，可以组合修饰Field

  - 方法返回值类型：返回值类型可以是允许的任何数据类型，包括基本类型和引用类型

  - 方法名：建议动词开头

  - 形参列表：用，隔开的一个个数据定义

特别的：static是一个特殊的关键字，用于修饰方法、Field等成员，表示属于类本身，不属于实例。

**静态成员不能直接访问非静态成员**

static修饰的成员不能访问没有static修饰的成员

**Field：成员变量**

#### 4.1.2 对象的产生和使用

创建对象的根本途径是构造器，使用new关键字调用某个类构造器可以创建实例

static修饰的方法和Field，既可以通过类调用，也可以通过实例调用；没有static修饰的普通方法和Field，只能通过实例调用

#### 4.1.3 对象、引用和指针

```java
Person p = new Person();
```

创建了一个Person实例，Person对象，赋给了p变量。

引用变量存放的只是一个引用，他指向实际的对象，p就是引用变量

真正的Person对象存放在堆（heap）内存中，栈内存里面的引用变量没有存储对象的Field数据，对象的Field数据实际存放在堆内存中，引用变量只是指向堆内存里的对象

Java不允许直接访问堆内存的对象，只能通过对象的引用操作对象

**如果堆内存里的对象没有任何变量指向，那么程序无法访问该对象，对象就变成了垃圾，Java的垃圾回收机制将回收对象，释放对象所占的内存，因此，把引用变量赋值为null，对象就变成了垃圾**

#### 4.1.4 对象的this引用

this关键字指向调用该方法的对象。

根据出现位置不同，this作为对象的默认引用两种情形：

- 构造器中引用构造器正在初始化的对象
- 方法中引用调用该方法的对象

情形一：

```java
public class Dog {
    public void jump(){
        System.out.println("jump方法");
    }
    public void run(){
        Dog dog = new Dog();
        dog.jump();
        System.out.println("run方法");
    }

    public static void main(String[] args) {
        Dog d = new Dog();
        d.run();
        //有俩个Dog对象
    }  
}
```

- 修改后，使用this指向现在所在的对象

```java
public class Dog {
    public void jump(){
        System.out.println("jump方法");
    }
    public void run(){
        this.jump();
        System.out.println("run方法");
    }
}
```

- 省略this

```java
public class Dog {
    public void jump(){
        System.out.println("jump方法");
    }
    public void run(){
        jump();
        System.out.println("run方法");
    }
}
```

static修饰的方法而言，无法使用this关键字，因为找不到指向的对象，static是属于类

**由于static修饰的方法不能使用this引用，所以static修饰的方法不能访问不使用static修饰的普通成员，所以Java语法规定：静态变量不能直接访问非静态成员**

省略this，但是要知道有this的存在，也要思考上面的原因

注意：

- 虽然可以使用对象来访问static修饰的Field，但是不太好，所以Java编程时，不要使用对象调用static修饰的Field、方法，而是使用类去调用static修饰的Field、方法



this的第二种出现：

- 大多数时候都无需使用，但是如果局部变量和Field同名，程序需要在方法里面访问这个被覆盖的Field，还有构造器里的局部变量 

  详情见默认的set方法和变量的构造器

在方法里面写

```java
return this;
//和构造器相似，返回该对象
```

### 4.2方法详解

Java方法都必须定义在类中，方法在逻辑上要么属于类，要么属于对象

#### 4.2.1 方法的所属性

Java语言是静态的，一个类定义完成后，只要不在重新编译这个类文件，类和该类的对象所拥有的的方法是固定的

方法都应该以 “类.方法”和“对象.方法“的形式来调用，

常见的直接调用方法：

- 同一个类的一个方法调用另一个方法时，如果被调用的方法是普通方法，默认使用this作为调用者；

  如果是静态方法，默认使用类作为调用者。也就是说，表面上看起来某些方法可以被独立执行，但是实际上还是使用this或者类来作为调用者。

Java方法的所属性主要体现在以下方面：

- 方法不能独立定义，方法只能在类体定义
- 逻辑意义上，方法要么属于类，要么属于该类的一个对象
- 永远不能独立执行方法，执行方法必须使用类或者对象作为调用者

**对象调用类方法，本质还是实例所属的类调用类方法**

#### 4.2.2 方法的参数传递机制

如果声明方法包含了形参声明，则调用方法必须给这些形参制定参数值，调用方法实际传给形参的参数值叫做实参

Java参数传递方式：

- 值传递：就是将实际参数值得副本（复制品）传入方法，参数本身不会受到影响

Java对待引用类型的参数传递，一样采用的是值传递

#### 4.2.3 形参个数可变的方法

jdk1.5之后，java允许定义形参个数可变的参数，从而为方法指定数量不确定的参数，在最后一个形参后面增加三个点（...），则表明可以接受多个参数值，多个参数值被当成数组传入

```java
public statc void test(int a,String... books){
    for (String tmp :books){
        System.out.println(tmp);
    }
}
```

与传入String[]不同，这样可以传入多个String参数

#### 4.2.4 递归方法

一个方法的方法体再次调用了方法本身，就是递归方法，递归一定要向已知方法递归

#### 4.2.5 方法重载

只要形参列表不同，允许一个类里定义多个同名方法，这称为方法重载。

### 4.3 成员变量和局部变量

Java中，根据定义变量的位置不同，将变量分为俩大类：

- 成员变量
- 局部变量

机制有很大差异，做出详细介绍

#### 4.3.1 成员变量和局部变量

- 成员变量
  - 实例Field（不以static修饰）
  - 类Field（以static修饰）
- 局部变量
  - 形参（方法签名中定义的变量）
  - 方法局部变量（在方法内定义）
  - 代码块局部变量（在代码块内定义）

**变量应该小驼峰命名**

成员变量分为类Filed和实例Field，生命周期

- 类Field（有static）从这个类的准备阶段起就存在，直到系统完全销毁这个类，类Field的作用域与这个类的生存范围相同
- 实例Field（无static）从类的实例被创建开始，直到系统完全销毁这个实例，实例的作用域与对应实例的生存范围相同























## 五：面向对象（下）

## 六：Java集合







本章要点：

- 集合的概念和作用
- Java的集合体系
- Collection集合的常规用法
- 使用Iterator和foreach循环遍历Collection集合
- HashSet、LinkedHashSet的用法
- TreeSet的用法
- EnumSet的用法
- List集合的用法
- ArrayList和Vector
- 固定长度的List结合
- Queue接口和Deque接口
- PriorityQueue的用法
- ArrayDeque的用法
- LinkedList集合的用法
- Map的概念和常规用法
- HashMap和HashTable
- TreeMap的用法
- 几种特殊的Map实现类
- Hash算法对HashSet、HashMap性能的影响
- Collections工具类的用法
- Enumeration迭代器的用法

简述：Java集合类是一种特别有用的**工具类**，用于存储数量不等的多个对象，并可以实现常用的数据结构，如栈、队列等。除此之外，Java集合还用于保存具有映射关系的关联数组。

java集合大致可以分为 Set、List和Map体系

- Set表无序、不可重复的集合；
- List代表有序、重复的集合；
- Map代表具有映射关系的集合。
- Java5以后，增加了Queue体系集合，代表一种队列集合实现。

java集合就像一种容器，我们把多个对象（实际是对象的引用）放入容器中。在java5之前，java集合会丢失容器的对象数据类型，把所有对象都当成Object类型处理；从Java5增加了泛型之后，java集合可以记住容器中对象的数据类型。

本章目的：

详细介绍Java的4种集合体系的常规功能，深入介绍各集合实现类所提供的独特功能，深入分析各实现类的实现机制，以及用法上的细微差别，并给出不同应用场景选择哪种集合实现类。

### 6.1 Java集合概述

为什么需要集合类：

- 为了保存数量不确定的数据，以及保存具有映射关系的数据（也称作关联数组），Java提供了集合类

集合类作用：

- 负责保存、盛装其他数据，集合类也被称为容器类。

  所有的集合类都位于java.util包下，为处理多线程下的并发安全问题，java 5 在java.util.concurrent 包下提供了一些多线程支持的集合类

集合类与数组差异：

- 数组类型既可以是基本类型，也可以是对象（实际保存的是对象的引用变量）；
- 集合里只能保存对象（实际只是保存对象的引用变量，通常习惯上认为是集合里保存的是对象）

集合类的派生（根接口）：

- Collection

  - Set 无法记得添加这个元素的顺序
  - List 像数组，记住添加元素的顺序
  - Queue

  <img src="file:///D:\qq\1633697855\Image\C2C\4C36B8F98F1D28A181246828F053F639.png" alt="img" style="zoom: 67%;" />

- Map：保存的每项数据都是ket-value对

  <img src="file:///D:\qq\1633697855\Image\C2C\C31E76728DDD5E257477678F42FC13C9.png" alt="img" style="zoom:67%;" />

  



访问List集合的元素，可以通过元素的索引来访问

访问Map集合的元素，可以根据元素的key来访问value

访问Set集合的元素，只能根据元素本身来访问

常见实体类：HashSet、TreeSet、ArrayList、ArrayDeque、LinkedList、HashMap、TreeMap等

### 6.2 Collection接口和Iterator接口

Collection接口是List、Set和Queue接口的父接口，该接口里的方法可以操作这三个。

Collection接口方法：

- boolean  add(Object o)：增加元素
- boolean  addAll(Collection c)：将c中所有的元素添加到指定的元素李
- void  clear()：清除集合里面的所有元素，将元素长度变为0
- boolean  contains()：返回集合里是否包含指定元素
- boolean  containsAll(Collection c)：返回集合里面是否包含集合c中的所有元素
- boolean isEmpty()：返回集合是否为空
- Iterator  iterator：返回一个Iterator对象，用于遍历集合里的元素
- boolean  remove(Object o)：删除集合中的指定元素o，包含一个或多个o时，元素都将被删除
- boolean  removeAll(Collection c)：从集合中删除集合c里包含的所有元素
- boolean  retainAll(Collection c)：从集合中删除集合c里不包含的元素
- int  size()：返回集合里元素的个数
- Object[]  toArray()：将集合变成一个数组，所有的集合元素变成对应的数组元素

##### 6.2.1使用Iterator接口遍历集合元素

Iterator接口也是Java集合框架的成员，Iterator用于遍历Collection集合中的元素，Iterator对象也被称作迭代器。

Iterator接口隐藏了Collection实现类的底层细节，有以下三个方法：

- boolean  hasNext()：如果被迭代的集合元素还没有被遍历，则返回true
- Objcet next()：返回集合里的下一个元素
- void  remove()：删除集合里上一次next返回的元素

例子：

```java
public class IteratorTest{
    public static void main(String[]args){
        Collection books = new HashSet();
        books.add("a");
        books.add("b");
        books.add("c");
        books.add("d");
        Iterator it = books.iterator();
        //获得迭代器
        while(it.hasNext()){
            
            //需要强制转换，取出的是Object
            String book = (String)it.next();
            System.out.println(book);
            if(book.equals("a")){
                //除去上一次next的元素
                it.remove();
            }
            //不会改变集合
            book = "测试字符串"；
        }
        System.out.println(books);
    }
}
```



使用Iterator对集合元素进行迭代时，Iterator并不是把集合元素本身进行了迭代变量，而是把集合元素的值传给了迭代元素，所以修改迭代元素的值对集合元素本身没有影响

使用Iterator对集合元素进行迭代时，只有使用Iterator的remove方法删除上一次next方法返回的集合元素才可以，不能使用集合的方法改变集合

Iterator迭代器采用的是快速失败机制，一旦在迭代过程中检测到集合已经被修改（被其他线程修改），程序立即抛出ConcurrentModificationException异常，避免共享资源产生的潜在问题

##### 6.2.2使用foreach来遍历集合元素

```java

Collection books = new HashSet();
for(Object obj :books){
    
}

```

使用foreach循环迭代访问集合元素时，也不是访问元素本身，而是把集合元素的值赋予给了迭代变量，该集合也不能被改变，否则抛异常

### 6.3 Set集合

实际上Set就是Collection，只是Set不允许有重复元素

Set的特点：

- Set集合不允许包含相同的元素，添加相同元素会操作失败，add返回false

判断相同的依据：

- Set判断两个对象不是使用==运算符，**而是equals方法**。

#### 6.3.1 HashSet类

HashSet就是Set接口的典型实现，大多数时候使用Set集合时就是使用这个实现类。

**HashSet按Hash算法来存储集合中的元素，因此具有很好的存取和查找性能**

HashSet特点：

- 不能保证元素的排列顺序，顺序有可能发生变化
- HashSet不是同步的，如果多个线程同时访问一个HashSet，假设有两个或者两个以上线程同时修改HashSet集合时，必须通过代码来实现其同步
- 集合元素可以是null

HashSet的存入过程：

- 当向HashSet集合中存入一个元素中时，HashSet会调用对象的hashCode()方法来获得对象的hashCode值，然后根据该HashCode值决定该对象在HashSet中的存储位置。如果有两个元素通过equals()方法返回true，但是他们的hashCode()方法返回值不相等，HashSet将会把它们存储在不同的位置，依然可以添加成功

  简单来说，HashSet集合判断两个元素相等的标准是两个对象通过equals()方法比较相等，并且两个对象的hashCode()方法返回值也相等

注意：

- 因为添加进HashSet中需要判断equals和hashCode，所以任何时候**需要重写对应类的equals()方法都也应该重写其hashCode()方法**。规则是：如果两个对象通过equals()方法返回true，这俩个对象的hashCode值也应该相同

弊端：

- equals返回ture，hashCode不同
  - 导致HashSet会把这两个对象保存在Hash表的不同位置，有出入
- hashCode相同，equals不同
  - 因为hashCode相同，HashSet将试图把它们保存在同一个位置，但是不行，会使用链式结构来保存多个对象；而HashSet访问集合时也是根据元素的HashCode值来快速定位的，**如果HashSet中两个以上的元素，性能会下降**

HashSet内核特色：

- HashSet每个能存储元素的"槽位"通常称为桶

重写hashCode()方法的基本规则：

- 在程序运行过程中，同一个对象多次调用hashCode()方法应该返回相同的值
- 当两个对象通过equals()方法比较返回true时，这两个对象的hashCode()方法应该返回相同的值
- 对象中用作equals()方法比较标准的Field，都应该计算hashCode值





































## 七：泛型

集合有一个缺点，就是当我们把一个对象放进集合中后，会"忘记"这个对象的数据类型，再次取出该对象后，百衲衣类型变成了Object类型（运行类型没变）

设计集合的时候希望能保存任何类型的对象，具有好的通用性，带来俩个问题：

- 集合对元素类型没有限制，引发问题，会把俩种类型的对象放入容器
- 取出元素后需要进行强制类型转换，增加复杂度，引发ClassCastException异常

### 7.1.1编译不检查类型的异常



## 八：异常

## 九：注释

## 十：输入/输出

## 十一：多线程

## 十二：网络编程

## 十三：类加载机制和反射

本章要点：

- 类加载
- 类连接的过程
- 类初始化的过程
- 类加载器以及实现机制
- 继承ClassLoader实现自定义类加载器
- 使用URLClassLoader
- 使用Class对象
- 动态创建Java对象
- 动态调用方法
- 访问并修改Java对象的属性值
- 使用反射操作数组
- 使用Proxy和InvocationHandler创建动态代理
- AOP入门
- Class类的泛型
- 通过反射获取泛型类型

本章将会深入介绍Java类的加载、连接和初始化知识

重点介绍java.lang.reflect包下的接口和类，包括Class、Method、Field、Construcotor和Array等，Java可以使用这些类动态地创建Java对象，动态地调用Java方法，访问并修改指定对象的Field值。

### 13.1 类的加载、连接和初始化

加载、连接和初始化

#### 13.1.1 JVM和类

当我们调用Java命令运行某个Java程序时，命令将会启动一个Java虚拟机进程，不管Java程序有多么复杂，线程都在Java虚拟机进程里，

只有出现以下几种情况下，JVM进程将被终止：

- 程序进行到最后正常结束
- 程序运行使用System.exit()或 Runtime.getRuntime().exit()代码结束程序
- 程序执行过程中遇到未捕获的异常或错误而结束
- 程序所在平台强制结束了JVM进程

两次运行Java程序处于两个不同的JVM进程中，两个JVM之间并不会共享数据

#### 13.1.2 类的加载

程序主动使用某个类，类还没加载到内存，系统会通过**加载、连接、初始化**三个步骤来进行初始化。

所以把这三个步骤叫做类加载或类初始化

类加载指的是将类的class文件读入内存，并为之创建一个java.lang.Class 对象，使用任何类时，系统都会为之建立一个java.lang.Class对象

>  事实上系统的所有的类也是实例，他们都是java.lang.Class的实例

类的加载由类加载器完成，类加载器通常由JVM提供，JVM提供的这些类加载器叫做系统类加载器，类加载器是程序运行的基础。

继承ClassLoader基类可以创建自己的类加载器



