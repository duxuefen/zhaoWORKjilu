http请求：

  session：

  cookie：

  servlet:继承httpServlet

  **servlet生命周期：** 

答：servlet的生命周期是指servlet从加载、初始化、服务到销毁的一个过程。

​         初始化阶段  调用init（）方法

​          响应客户端请求阶段 调用service（）方法

​           终止阶段 调用destroy（）方法

**get 和post请求的区别：**

  请求：put,delete

  GET：最常见的一种请求方式，当客户端要从服务器中读取文档时，当点击网页上的链接或者通过在浏览器的地址栏输入网址来浏览网页的，使用的都是GET方式。 

POST：POST方法可以允许客户端给服务器提供信息较多。POST方法将请求参数封装在HTTP请求数据中，以**名称/值**的形式出现，可以传输大量数据。使用表单提交基本都用POST方式

  **jsp的九大内置对象：** request，response，session，application，out，pagecontext，config，page，exception

**jsp的执行原理：** 在一个JSP文件第一次被请求时，JSP引擎把该JSP文件转换成为一个Servlet。而这个引擎本身也是一个Servlet

![image-20201015104600024](C:\Users\du\AppData\Roaming\Typora\typora-user-images\image-20201015104600024.png)



**静态包含和动态包含的区别（https://blog.csdn.net/panjieer/article/details/80465953）：**    *静态包含：* 先合并后翻译，

​                         *动态包含：*先翻译后合并

**session 会话开启和结束的标志：** *开启：*

**Resquest和Response的区别**：*Request 对象:*用于接收客户端浏览器提交的数据，

​                                                     *Response 对象:*的功能则是将服务器端的数据发送到客户端浏览器。

**转发和重定向的区别：** *重定向(response.sendRedirect(""))：*客户端的行为，需要客户端至少向服务器发送两次请求，在路径栏上显示的应该是重定向的路径，可以观察到页面地址的

​           redirect 重定向；重新发生

​                                      *请求转发（request.getRequestDispatch("")）：*服务端的行为，客户端发起的一次请求可以被多次传递无论这个请求尽力过多少个处理程序，始终是同一个请求,请求中的数据经历过的每一个处理程序都可以使用。中间传递的是自己容器的request，地址栏没有变化，请求转发客户端只做了一次请求

 dispatch  发出；发生

**final,finally,finalize的区别：** *final修饰符（关键字）：*被final修饰的类，就意味着不能再派生出新的子类，不能作为父类而bai被子类继承。因此一个类不能既被abstract声明，又被final声明。将变量或方法声明为final，可以保证他们在使用的过程中不被修改。

​                                                   *finally是在异常处理时提供finally块来执行任何清除操作。*最终都会被执行

​                                                 *finalize是方法名：*java技术允许使用finalize方法在垃圾收集器将对象从内存中清除出去之前做必要的清理工作



**throw和throws的区别：**

答：常见的异常：RuntimeException 运行时的异常 

​       catch中的**return语句**，用于结束当前的方法，后边的语句就不会执行了，而finally语句还会执行

​       throws：在方法后面使用throws关键字对外声明该方法可能有的异常，调用者在调用的时候必须进行异常处理。

​      throw：在方法中声明抛出异常的实例对象，**需要使用try.....catch语句对抛出的异常进行处理，或者在方法上使用throws抛出异常**。

常见的异常：

1） java.lang.NullPointerException 空指针异常；出现原因：调用了未经初始化的对象或者是不存在的对象。

2） java.lang.ClassNotFoundException 指定的类找不到；出现原因：类的名称和路径加载错误；通常都是程序 试图通过字符串来加载某个类时可能引发异常。

3） java.lang.NumberFormatException 字符串转换为数字异常；出现原因：字符型数据中包含非数字型字符。4）java.lang.IndexOutOfBoundsException 数组角标越界异常，常见于操作数组对象时发生。

5）java.lang.IllegalArgumentException 方法传递参数错误。

6） java.lang.ClassCastException 数据类型转换异常。

**为什么使用抽象类**

**对象的克隆（clone()）**：A和B是两个独立的对象，但B的初始值是由对象A确定

  **new和clone的区别**：*new* 是分配内存，然后调用构造方法，一个对象创建完毕，可以把他的引用（地址）发布到外部，在外部就可以使用这个引用操纵这个对
象。  *clone* 也是分配内存，分配的内存和原对象（即调用 clone 方法
的对象）相同，然后再使用原对象中对应的各个域，填充新对象的域，填充完成之后，clone 方法返回，一个新的相同的对象被创建，同样可以把这个新对象的引用发布到外部。

**深拷贝和浅拷贝的区别**：*浅拷贝：*直接将原对象的字段的引用值拷贝给新对象的字段

  *深拷贝：*创建一个新的相同的字符串对象，将新的字符串对象引用付给新拷贝的对象



**wait和sleep的区别：**1.wait来自object类，sleep来自Thread类

​                                       2.最主要是sleep方法没有释放锁，而wait方法释放了锁，使得其他线程可以使用同步控制块或者方法。

​                                       3.wait，notify和notifyAll只能在同步控制方法或者同步控制块里面使用，而sleep可以在任何地方使用（使用范围）

​                                       4.sleep必须捕获异常，而wait，notify和notifyAll不需要捕获异常

​                                        5.sleep是Thread类的静态方法。sleep的作用是让线程休眠制定的时间，在时间到达时恢复。wait是Object的方法，也就是说可以对任意一个对象调用wait方法，调用wait方法将会将调用者的线程挂起，直到其他线程调用同一个对象的notify方法才会重新激活调用者。

**实现线程的方式**：*方式一：继承Thread类的方式*

1. 创建一个继承于Thread类的子类
2. 重写Thread类中的run()：将此线程要执行的操作声明在run()
3. 创建Thread的子类的对象
4. 调用此对象的start():①启动线程 ②调用当前线程的run()方法

*方式二：实现Runnable接口的方式*

1. 创建一个实现Runnable接口的类
2. 实现Runnable接口中的抽象方法：run():将创建的线程要执行的操作声明在此方法中
3. 创建Runnable接口实现类的对象
4. 将此对象作为参数传递到Thread类的构造器中，创建Thread类的对象
5. 调用Thread类中的start():① 启动线程 ② 调用线程的run() --->调用Runnable接口实现类的run()

*方式三：用FutureTask方式，实现callable接口，根据task.get(),可以获取返回值。*

​    1.创建一个实现Callable的接口的类

​     2.run方法可以有返回值。

​     3.新建FutureTask类（new Callable（））

​     Thread t=new Thread (new FutureTask )

**NIO和IO的区别**

答：Java IO面向流意味着每次从流中读一个或多个字节，直至读取所有字节，它们没有被缓存在任何地方。此外，它不能前后移动流中的数据。如果需要前后移动从流中读取的数据，需要先将它缓存到一个缓冲区。 

​       Java NIO的缓冲导向方法略有不同。数据读取到一个它稍后处理的缓冲区，需要时可在缓冲区中前后移动。这就增加了处理过程中的灵活性 nio提供了事件选择器和非阻塞访问

**什么是java序列化，如何实现java序列化？**

序列化版本号 serialVersionUID

答：序列化就是一种用来处理**对象流**的机制，所谓对象流也就是将对象的内容进行流化。可以对流化后的对象进行读写操作，也可将流化后的对象传输于网络之间。序列化是为了解决在对对象流进行读写操作时所引发的问题。 

序列化的实现：将需要被序列化的类实现Serializable接口，该接口没有需要实现的方法，implements Serializable只是为了标注该对象是可被序列化的，然后使用一个**输出流**(如：FileOutputStream)来构造一个**ObjectOutputStream(对象流)对象**，接着，使用ObjectOutputStream对象的**writeObject(Object obj)方法**就可以将参数为obj的对象写出(即保存其状态)，要恢复的话则用输入流。