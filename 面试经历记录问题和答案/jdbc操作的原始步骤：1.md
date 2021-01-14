**jdbc操作的原始步骤：**1.加载驱动，建立连接，创建preparestatement  执行SQL语句，处理结果集，释放资源

**statement 和preparestatement的区别：**

答：Statement用于执行静态sql语句，在执行时，必须指定一个事先准备好的sql语句。

PrepareStatement是预编译的sql语句对象，可以有效的防止SQL注入，被预编译并保存在对象中。被封装的sql语句代表某一类操作，语句中可以包含动态参数“?”，在执行时可以为“?动态设置参数值，提高效率

1.PreparedStatement继承自Statement，两者都是接口。
2.内部都要建立类似于Sockt连接，效率都不是特别高。

> \**#{}**表示一个占位符号 相当于 `jdbc`中的 **?** 符号
> \#{}实现的是向prepareStatement中的预处理语句中设置参数值，sql语句中#{}表示一个占位符即?

> 2、#{}将传入的数据都当成一个字符串，会对**自动传入的数据加一个双引号**。如：`select * from user where id= #{user_id}`，如果传入的值是11,那么解析成sql时的值为`where id="11"` ，

**预编译 ：**   **所谓预编译就是将一些灵活的参数值以占位符?的形式给代替掉，我们把参数值给抽取出来，把SQL语句进行模板化**。让MySQL服务器执行相同的SQL语句时，不需要在校验、解析SQL语句上面花费重复的时间

**SQL注入：**Sql注入指的是程序解析时会将你传入的参数作为原来SQL语句的一部分，打乱原来SQL的结构，而通常我们只是需要传入一个参数而已.

  ${} where后面的条件，根据SQL的规制来拼接一些where后面的条件是true

$ {}将传入的数据直接显示生成在sql中。如：`select * from user where id= $ {user_id}`，如果传入的值是11,那么解析成sql时的值为`where id=11`





object为啥能接受int类型： 自动装箱成integer类型，









事务：

保存点：相当于打一个标记，回滚的保存点