##  第四次面试题  

**MySQL数据类型：**

   数据数值类型：整数类型：tinyint  1byte    -128,127

​                                                 smallint 2byte   -32768,32767

​                                                 mediumint  3byte

​                                                 int(integer)  4byte

​                                                 bigint 8byte

​                      浮点小数类型：float 4byte

​                                                 double 8byte

                      定点小数类型：decimal（m,d）m是表示有效数字数的精度。 m范围为1〜65。
                      D是表示小数点后的位数。 D的范围是0~30。MySQL要求D小于或等于(<=)m。

 日期和时间类型：date   3 byte  

​                                 time 3  byte   时间值或持续的时间

​                                  year  1byte  

​                                  datetime 8byte 混合日期和时间值

​                                  timestamp  4byte  根据时区进行保存成一个UTC时间

1、在存储时间戳数据时，先将本地时区时间转换为UTC时区时间，再将UTC时区时间转换为INT格式的毫秒值(使用UNIX_TIMESTAMP函数)，然后存放到数据库中。

  2、在读取时间戳数据时，先将INT格式的毫秒值转换为UTC时区时间(使用FROM_UNIXTIME函数)，然后再转换为本地时区时间，最后返回给客户端。

字符串类型：char  0-255 bytes  定长字符串

​                       varchar 0-65535bytes 变长字符串

​                        tinyblob  0-255 bytes 不超过255个字符的二进制数据

​                        tinytext   0-255 bytes   短文本字符串

​                        blob         0-65535 bytes 二进制形式的长文本数据

​                        text           0-65535 bytes  长文本数据

​                        

 ![img](https://iknow-pic.cdn.bcebos.com/d1a20cf431adcbef7008298ba7af2edda3cc9f7a?x-bce-process=image/resize,m_lfit,w_600,h_800,limit_1)



**Where后面跟的条件**：比较：<>(!=)

​                                        确定范围：between---and ---,not between----and---

​                                        确定集合：in ，not in

​                                         空值：is null ，is not  null

​                                         多重条件：and or

**where 后面跟 and 和or  and的优先级大于or 可以用括号改变**

嵌套查询：子查询的语句中不能使用order by 语句，order by 只能对最终结果排序

 **exists 是相关子查询根据外表来和内查询一一匹配**

​                                          

**MySQL** **中有哪几种锁？**

1、表级锁：开销小，加锁快；不会出现死锁；锁定粒度大，发生锁冲突的概率最高，并发度最低。

2、行级锁：开销大，加锁慢；会出现死锁；锁定粒度最小，发生锁冲突的概率最低，并发度也最高。

3、页面锁：开销和加锁时间界于表锁和行锁之间；会出现死锁；锁定粒度界于表锁和行锁之间，并发度一般。

**域：** D={男，女}

**笛卡尔积**：是好几个域相乘，可以看成二维组，每行一个元组，每列对应一个域（字段），就是相乘

**传统的关系运算**：**并，交，差**  **广义笛卡尔积：** 是R*S

**专门的关系运算符**：为数据库引用的特殊运算符，从列的角度来进行。 

​       **选择**：普通的查询

​       **投影**：不仅取消了元关系中的某些列，还可能取消某些元组，还应取消完全相同的行

​       **连接**： 他是从两个关系的笛卡尔积中选取属性间满足一定条件的元组。

​             **等值连接**： 从笛卡尔积中选取A，B属性值相等的元组

​            **自然连接：一种特殊的等值连接**，他要求两个关系中比较的分量必选是相同的，并且要把重复的去掉

**DML数据操作语言：包括插入，修改，删除数据**

插入：insert into  表名（列名） values(‘值’，‘值’)

修改：update 表名 set 列名=‘新值’ where 条件

删除：delete from 表名 where 条件

**SQL优化**

答：1.选取适用的字段属性

​        2.当只要一行数据时使用 limit 1

​        3.选取正确的数据库引擎；Mysql 中有两个引擎 **MyISAM** 和 **InnoDB**，每个引擎有利有弊。

​             **MyISAM**： 适用于一些大量查询的应用，但对于有大量写功能的应用不是很好。甚至你只需要update

​                                一个字段整个表都会被锁起来。而别的进程就算是读操作也不行要等到当前 update 操作完

​                                 成之后才能继续进行。另外，MyISAM 对于 select count(*)这类操作是超级快的。

​            **InnoDB**： 的趋势会是一个非常复杂的存储引擎，对于一些小的应用会比 MyISAM 还慢，但是支持“行

​                               锁”，所以在写操作比较多的时候会比较优秀。并且，它支持很多的高级应用，例如：事物。

​        4. 用 not exists（存在） 代替 not in

​           **Not exists** 用到了连接能够发挥已经建立好的索引的作用，

​           **not in** 不能使用索引。Not in 是最慢的方式要同每条记录比较，在数据量比较大的操作红不建议使用这种方式。

**IN 操作符**  :IN 操作符允许您在 WHERE 子句中规定多个值。

exists: 代表存在量词，带有EXISTS谓词的子查询不返回任何实际数据，只返回逻辑true和false值 

5. ​      对操作符的优化，尽量不采用不利于索引的操作符

​             如：in    not in    is null      is not null         <>      

​      6. 如果某个字段总要拿来搜索，为其建立索引：

​                             Mysql 中可以利用 alter table 语句来为表中的字段添加索引，语法为：alter table 表明

​                           add index (字段名)；

**SQL索引为啥会提高效率**

答：索引指向数据库中数据具体位置，当用户通过索引进行数据查询时，不用遍历所有数据库中的所有数据

**limit 0,10 和limit 10000,10 那个效率会高点**

答：第一个数字是开始的位置 ，第二个是查询的条数

**mysql 中drop,delete和truncate区别**

答：drop（）: 删除表，并且释放空间，将表删的彻底。

​        truncate(截断表）:删除表test里的内容，并释放空间，但不删除表的定义，表的结构还在。

​        delete：删除表内的中内容，保留表的定义，不释放空间。

​        **delete** 命令删除的数据将存储在系统回滚段中，需要的时候，数据可以回滚恢复，而 **truncate** 命令删除的数据是不可以恢复的。

**DQL数据查询语言**

关键字的顺序：from 。。。where ，group by, having  order by (ASC 升序，DESC降序) ，limit 开始位置，条数

列名 **AS** 新的列名。

**MySQL表的连接**

答：

内连接（inner join）：在每个表中找出符合条件的共有记录，**以表1为主，拿表1的每条记录跟表2相比**

​         **关键字**：JOIN连接表  也可以写成 inner join ，ON描述连接条件

自连接：表与自身的连接

外连接：

​        左外连接（left join）：左表(A)的记录将会全部表示出来,而右表(B)只会显示符合搜索条件的记录

​        右外连接 （right join）：右表(B)的记录将会全部表示出来,而表(B)只会显示符合搜索条件的记录

​        全外连接 （full join）：左右两张表都不受限制

### UNION

UNION 操作符用于合并两个或多个 SELECT 语句的结果集。

**MySQL常用的聚合函数**

答：avg（） count（）   having  group by sum() v,max(),min()

**数据库对查询的结果如何去重**

答：用distinct 关键字        adj.清晰的;清楚的;明白的;明显的;截然不同的;有区别的;不同种类的;确定无疑的;确实的;确切的

**数据库事务**

**为啥arraylist查询效率高**

答：因为底层是数组，有下标，可以通过计算直接得到内存地址，找到要查找的。

**spring常用的注解**

答：@Autowired 自动装配

​        @Qualifier （合格的）来指定Bean的名称，结合@AutoWired搭配使用

​        @service

​        @Repository

​        @Component 当组件不好归类的时候，我们可以使用这个注解进行标注。

**springMVC常用注解**

答：@Controller

​        @RequestMapping

​        @PathVariable用于将请求URL中的模板变量映射到功能处理方法的参数上，即取出URL模板中的变量作为参数

​        @ResponseBody 

**springboot常用注解**

答：@springBootApplication

​        @Configuration

**JVM解释一下  string d="dd ";   string d=new String ("dd") 区别**

答：String d="dd": 可能创建一个或者不创建对象，如果”ABC”这个字符串在**java String池**里不存在，会在java String池里创建一个创建一个**String对象(“ABC”)**，然后str1指向这个内存地址，无论以后用这种方式创建多少个值为”ABC”的字符串对象，始终只有一个内存地址被分配，之后的都是String的拷贝，Java中称为**“字符串驻留”**，所有的字符串常量都会在编译之后自动地驻留。

​       String str2 = new String(“ABC”);至少创建一个对象，也可能两个。因为用到new关键字，肯定会在**堆heap**中创建一个**str2的String对象**，它的value是“ABC”。同时如果这个字符串再**java String池里不存在**，会在**string池**里创建这个String对象“ABC”。

 **读写分离的作用：**

答：数据库写入效率要低于读取效率，一般系统中数据读取频率高于写入频率，单个数据库实例在写入的时候会影响读取性能，**为提高了并发吞吐和负载能力**
实现方式主要基于mysql的主从复制，通过路由的方式使应用对数据库的写请求只在master上进行，读请求在slave上进行。

**JVM垃圾回收机制和常见的算法**

答：GC（Garbage Collector）垃圾回收器 ，发现定位无用对象常用的**搜索算法**：

​       **1） 根搜索算法（使用）**

   根搜索算法是通过一些“GC Roots”对象作为起点，从这些节点开始往下搜索，搜索通过的路径成为**引用链（Reference Chain）**，当一个对象没有被 GC Roots 的**引用链**连接的时候，说明这个对象是不可用的。

 ![image-20201030160739054](C:\Users\du\AppData\Roaming\Typora\typora-user-images\image-20201030160739054.png)

**GC Roots 对象包括：**

​    a)  虚拟机栈（栈帧中的本地变量表）中的引用的对象。

​    b)  方法区域中的类静态属性引用的对象。

​    c)  方法区域中常量引用的对象。
​    d)  本地方法栈中 JNI（Native 方法）的引用的对象。

通过上面的算法搜索到无用对象之后，就是回收过程，**回收算法**如下：

1） 标记—清除算法（Mark-Sweep）（DVM 使用的算法）

1） 复制算法（Copying）

1） 标记—整理算法（Mark-Compact）

1） 分代收集（Generational Collection）



##   10.29的面试题

**索引为什么会提高效率**

答：索引指向数据库中具体数据所在的位置，当用户通过索引查询数据库中的数据时，不需要遍历所有数据库中的所有数据。

**什么情况下索引会失效**

答：1.如果条件中有or，即使其中有条件带索引也不会使用(这也是为什么尽量少用or的原因)，除非两个条件           

​           都有索引

​        2.对于多列索引，不是使用的第一部分，则不会使用索引。

​        3.like查询是以%开头

​        4.如果列类型是字符串，那一定要在条件中将数据使用引号引用起来,否则不使用索引

​        5.如果mysql估计使用全表扫描要比使用索引快,则不使用索引

##  **解释一下Docker，以及常用命令**

- 镜像你可以把它看成Java中的类，而容器可以看做是类的实例化对象。
- 一个类可以有多个对象，同理，一个镜像可以有多个容器。

答：让开发者可以打包他们的**应用以及依赖包**到一个可移植的容器中，然后发布到任何流行的 Linux 机器上，也可以实现虚拟化，容器是完全使用沙箱机制，相互之间不会有任何接口。简言之，就是可以在 Linux 上**镜像使用的这么一个容器** 

docker可以实现虚拟机隔离应用环境的功能，并且开销比虚拟机小，小就意味着省钱了

docker你就可以把开发环境直接封装转移给运维，运维直接部署你给他的docker就可以了。而且部署速度快。

**docker的用处**

答：1.web 应用自动化打包发布，像 tomcat 应用的发布。 

​        2.自动化测试和持续集成、发布 

​        3.在服务型环境中部署和调整数据库或其他的后台应用 

​        4.搭建 paas 环境[平台即服务](https://baike.baidu.com/item/平台即服务/4329761)

**常用命令**

答：查看docker镜像：docker images

​        拉取镜像：docker pull 镜像名称 

​        删除镜像：docker  rmi 镜像 ID 

​        交互式方式创建容器：docker run -it --name=容器名称 镜像名:TAG 标签 /bin/bash

​                                                docker run -di --name=mysql1 -p 33306:3306 -e

​        守护式方式创建容器：docker run -di --name=容器名称 **镜像名**:TAG 标签

​                                            --i：运行容器 

​                                            --name：为容器命名。 

​                                            --t：容器启动会进入命令行。 

​                                            --d：创建一个守护式容器在后台运行

​         容器停止：docker stop 容器名称

​         容器启动：docker start 容器名称

##   **说一下RabbitMQ**

**MQ**：消息队列，解决不同进程之间的问题 包括耦合程度过高，让有先后顺序，必选让他们进行排队，所以有了消息队列。

**工作原理**

![RabbitMQ的工作原理](E:\中软作业\学习资料\网络前沿技术\RabbitMQ（消息处理中间件）资料\RabbitMQ的工作原理.png)

1）Broker（安排，协商） 中间件：消息队列服务进程，此进程包括两个部分：Exchange（交换） 和 Queue（队列）

2）Exchange：消息队列交换机，按一定的规则将消息路由转发到某个队列， 对消息进行过滤

3）Queue：消息队列，存储消息的队列，消息到达队列并转发给指定的消费方。

4）Producer：消息生产者，即生产方客户端，生产方客户端将消息发送到MQ。 

5）Consumer：消息消费方，即消费方客户端，接收 MQ 转发的消息

**---消息发布接收流程：发送消息** 

1）生产者和 Broker 建立 TCP 连接 Connection； 

2）生产者和 Broker 建立通道 Channel； 

3）生产者通过通道将消息发送到 Broker，由 Exchange 将消息进行转发； 

4）Exchange 将消息转发到指定的 Queue 队列。 

---消息发布接收流程：接收消息 

1）消费者和 Broker 建立 TCP 连接 Connection； 

2）消费者和 Broker 建立通道 Channel； 

3）消费者监听指定的 Queue 队列； 

4）当有消息到达 Queue 时 Broker 默认将消息推送给消费者； 

5）消费者接收到消息。

**RabbitMQ 模式**

支持七种模式：生产者消费者模式

![image-20201030090928688](C:\Users\du\AppData\Roaming\Typora\typora-user-images\image-20201030090928688.png)

工作队列模式：两个消费端共同消费同一个队列中的消息，

​               特点：1）一个生产者将消息发送给一个队列；2）多个消费者共同监听一个队列的消息；3）消息不能              

​                              被重复消费；4）采取轮询的方式将消息平均发送给消费者

<img src="C:\Users\du\AppData\Roaming\Typora\typora-user-images\image-20201030090945683.png" alt="image-20201030090945683" style="zoom:67%;" />

发布/订阅模式：特点： 1）一个生产者将消息发送给交换机； 

​                                         2）与交换机绑定的有多个队列，每个消费者监听自己的队列；

​                                         3）生产者将消息发送给交换机，由交换机将消息转发到绑定此交换机的每个队列。

与工作队列模式区别： 

1）发布/订阅模式可以定义一个交换机绑定多个队列，一个消息可以发送给多 个队列； 

2）工作模式无需定义交换机，一个消息一次只能发送给一个队列； 

3）发布/订阅模式比工作队列模式功能更强大，发布/订阅可以将多个消费者监听同一个队列实现工作队列模的功能。

**理由模式、通配符模式、RPC 模式以及发布服务确认模式** 

