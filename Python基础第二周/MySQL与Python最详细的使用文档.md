## MySQL数据库

### 1.1 MySQL简介

- Mysql是最流行的RDBMS(Relational Database Management System：关系数据库管理系统)，特别是在WEB应用方面。
- 数据库（Database）是按照数据结构来组织、存储和管理数据的仓库，
- 每个数据库都有一个或多个不同的API用于创建，访问，管理，搜索和复制所保存的数据。
- 所谓的关系型数据库，是建立在关系模型基础上的数据库，借助于集合代数等数学概念和方法来处理数据库中的数据。
- RDBMS即关系数据库管理系统(Relational Database Management System)的特点：
  - 1.数据以表格的形式出现
  - 2.每行为各种记录名称
  - 3.每列为记录名称所对应的数据域
  - 4.许多的行和列组成一张表单
  - 5.若干的表单组成database
- 在我们开始学习MySQL 数据库前，让我们先了解下RDBMS的一些术语：

```
    数据库: 数据库是一些关联表的集合。.
    数据表: 表是数据的矩阵。在一个数据库中的表看起来像一个简单的电子表格。
    列: 一列(数据元素) 包含了相同的数据, 例如邮政编码的数据。
    行：一行（=元组，或记录）是一组相关的数据，例如一条用户订阅的数据。
    冗余：存储两倍数据，冗余降低了性能，但提高了数据的安全性。
    主键：主键是唯一的。一个数据表中只能包含一个主键。你可以使用主键来查询数据。
    外键：外键用于关联两个表。
    复合键：复合键（组合键）将多个列作为一个索引键，一般用于复合索引。
    索引：使用索引可快速访问数据库表中的特定信息。索引是对数据库表中一列或多列的值进行排序的一种结构。类似于书籍的目录。
    参照完整性: 参照的完整性要求关系中不允许引用不存在的实体。与实体完整性是关系模型必须满足的完整性约束条件，目的是保证数据的一致性。
```

##### SQL：

- SQL: 结构化查询语言(Structured Query Language)简称SQL,是最重要的关系数据库操作语言.
- 有上百种数据库产品都支持SQL，如：MySQL、DB2、ORACLE、INGRES、SYBASE、SQLSERVER...
- 结构化查询语言包含6个部分：

```
    1. 数据查询语言（DQL:Data Query Language）：SELECT
    2. 数据操作语言（DML：Data Manipulation Language）：INSERT，UPDATE和DELETE
    3. 事务处理语言（TPL）：BEGIN TRANSACTION，COMMIT和ROLLBACK
    4. 数据控制语言（DCL）：GRANT（授权）或REVOKE（回收权限）
    5. 数据定义语言（DDL）：CREATE、ALTER和DROP
    6. 指针控制语言（CCL）：DECLARE CURSOR，FETCH INTO和UPDATE WHERE CURRENT用于对一个或多个表单独行的操作
```

- 在本节中，会让大家快速掌握Mysql的基本知识，并轻松使用Mysql数据库。

### 1.2 mysql数据库的安装：

**① 先到MySQL的官方网站进行下载，这里的版本用的是5.7。**

​	版本：5.7.28

​	网址：https://dev.mysql.com/downloads/mysql/5.7.html#downloads下载。

![1573444553779](/Users/yhhang/Desktop/Python3.0课程体系研发/录播大课/产出物/文档/Python基础第二周/image/1573444553779.png)

![1573449820959](/Users/yhhang/Desktop/Python3.0课程体系研发/录播大课/产出物/文档/Python基础第二周/image/1573449820959.png)

**② 下载完成之后，进行安装。**

- mysql使用协议，同意协议，并进行下一步

![1573450268185](/Users/yhhang/Desktop/Python3.0课程体系研发/录播大课/产出物/文档/Python基础第二周/image/1573450268185.png)

- 选择安装的类型
  - Developer Default   默认安装，会安装mysql-server以及mysql-client中的一部分东西。
  - Server only 安装mysql-server，mysql核心程序，生成管理数据库实例，数据库实例任务调度线程之类，并提供相关接口供不同客户端调用【命令行】
  - Client only 安装mysql-client，其中包括MySQL外壳、MySQL路由器、MySQL工作台、MySQL连接器、以及一系列的插件。【图形化界面，以及其他的一些工具，这些工具我们基本上使用不到的，所以安装是比较多余的，下面会推荐一个更加方便可视化界面。】
  - Full  全部安装，包括mysql-server和mysql-client。
  - Custom，自定义安装。
- 这里我们安装Server only即可。下面会推荐一个更加好用的可视化界面供同学们使用，所以这里我们选择 Server only即可。

![1573451495182](/Users/yhhang/Desktop/Python3.0课程体系研发/录播大课/产出物/文档/Python基础第二周/image/1573451495182.png)

- 安装应用包

![1573451804740](/Users/yhhang/Desktop/Python3.0课程体系研发/录播大课/产出物/文档/Python基础第二周/image/1573451804740.png)

- 产品配置，我们只选则了mysql-server，所以直接进行下一步即可

![1573451951665](/Users/yhhang/Desktop/Python3.0课程体系研发/录播大课/产出物/文档/Python基础第二周/image/1573451951665.png)

- 高扩展性的选用

![1573452172529](/Users/yhhang/Desktop/Python3.0课程体系研发/录播大课/产出物/文档/Python基础第二周/image/1573452172529.png)

- 配置类型的选择

![1573452300352](/Users/yhhang/Desktop/Python3.0课程体系研发/录播大课/产出物/文档/Python基础第二周/image/1573452300352.png)

- 端口号的选择，mysql的默认端口为3306，但是本机的3306被占用，所以，改为3307

![1573452567328](/Users/yhhang/Desktop/Python3.0课程体系研发/录播大课/产出物/文档/Python基础第二周/image/1573452567328.png)

- 进行数据库密码设置

![1573452648180](/Users/yhhang/Desktop/Python3.0课程体系研发/录播大课/产出物/文档/Python基础第二周/image/1573452648180.png)

- 服务名称

![1573452891335](/Users/yhhang/Desktop/Python3.0课程体系研发/录播大课/产出物/文档/Python基础第二周/image/1573452891335.png)

- 应用配置加载

![1573452990408](/Users/yhhang/Desktop/Python3.0课程体系研发/录播大课/产出物/文档/Python基础第二周/image/1573452990408.png)

![1573453058969](/Users/yhhang/Desktop/Python3.0课程体系研发/录播大课/产出物/文档/Python基础第二周/image/1573453058969.png)

- 产品配置介绍

![1573453137129](/Users/yhhang/Desktop/Python3.0课程体系研发/录播大课/产出物/文档/Python基础第二周/image/1573453137129.png)

- 安装完成

![1573453213281](/Users/yhhang/Desktop/Python3.0课程体系研发/录播大课/产出物/文档/Python基础第二周/image/1573453213281.png)

③ 测试安装

![1573453607110](/Users/yhhang/Desktop/Python3.0课程体系研发/录播大课/产出物/文档/Python基础第二周/image/1573453607110.png)

![1573453685713](/Users/yhhang/Desktop/Python3.0课程体系研发/录播大课/产出物/文档/Python基础第二周/image/1573453685713.png)

④ 有些计算的服务在安装完成之后，没有启动需要我们手动开启。

![1573453872616](/Users/yhhang/Desktop/Python3.0课程体系研发/录播大课/产出物/文档/Python基础第二周/image/1573453872616.png)

![1573453935672](/Users/yhhang/Desktop/Python3.0课程体系研发/录播大课/产出物/文档/Python基础第二周/image/1573453935672.png)

![1573453965590](/Users/yhhang/Desktop/Python3.0课程体系研发/录播大课/产出物/文档/Python基础第二周/image/1573453965590.png)

![1573454267841](/Users/yhhang/Desktop/Python3.0课程体系研发/录播大课/产出物/文档/Python基础第二周/image/1573454267841.png)

- 上面的这些步骤，每次使用数据库之前都要进行服务的开启，这是比较麻烦的，我们可以配置一些设置，来启动服务。
- 在mysql中的bin的同级目录下，创建my.ini，写入配置


```
[mysql]
# 设置mysql客户端默认字符集
default-character-set=utf8 
[mysqld]
#设置3306端口
port = 3306 
# 设置mysql的安装目录
basedir=E:/mysql-5.7.12-winx64
# 设置mysql数据库的数据的存放目录
datadir=E:/mysql-5.7.12-winx64/data
# 允许最大连接数
max_connections=200
# 服务端使用的字符集默认为8比特编码的latin1字符集
character-set-server=utf8
# 创建新表时将使用的默认存储引擎
default-storage-engine=INNODB
```

- 以管理员身份打开cmd，使用cd切换到bin目录下，执行安装命令mysqld install
- 成功之后输入激活命令 mysqld --initialize-insecure --user=mysql

![1573117607502](/Users/yhhang/Desktop/Python3.0课程体系研发/录播大课/产出物/文档/Python基础第二周/image/1573458033845.png)

- 配置环境变量

![1573117680251](/Users/yhhang/Desktop/Python3.0课程体系研发/录播大课/产出物/文档/Python基础第二周/image/1573457807878.png)

![1573117705312](/Users/yhhang/Desktop/Python3.0课程体系研发/录播大课/产出物/文档/Python基础第二周/image/1573457837980.png)

![1573117740922](/Users/yhhang/Desktop/Python3.0课程体系研发/录播大课/产出物/文档/Python基础第二周/image/1573457959295.png)

- 命令行直接启动mysql

![1573117856333](/Users/yhhang/Desktop/Python3.0课程体系研发/录播大课/产出物/文档/Python基础第二周/image/1573458154302.png)

#### 1.3 连接测试

- 这里使用的是SQLyog(小海豚)，mysql-client，一种简单易用的数据库图形化工具。

- 现在我们的mysql中创建一个数据库


![1573455071207](/Users/yhhang/Desktop/Python3.0课程体系研发/录播大课/产出物/文档/Python基础第二周/image/1573455071207.png)

- 连接数据库

![1573455295968](/Users/yhhang/Desktop/Python3.0课程体系研发/录播大课/产出物/文档/Python基础第二周/image/1573455295968.png)

#### 1.4 mysql的卸载

- **直接卸载会有mysql残留，所以需要使用命令行。**

- 以**管理员身份运行CMD**，执行net stop mysql命令停止MySQL服务，然后在执行mysqld -remove命令卸载服务，最后删除整个mysql目录即可。


```
net stop mysql -- 命令停止MySQL服务
mysqld -remove /或者/ sc delete 服务名称 -- 命令卸载服务

```

- mariadb的卸载与mysql是一样的，只需要注意服务名称不同。
- mysql的配置繁琐，易错，建议使用mariadb。
- 一定要注意，在卸载时，就mysql的文件卸载干净，否则在下次安装使用时，会出现一系列的bug！

### 1.5 SQL的基本操作

##### 数据库操作：

```mysql
mysql> show databases;                              --查看当前用户下的所有数据库
mysql> create database  数据库名 charset=utf8;    --创建数据库
mysql> use test;                                 --选择进入test数据库
mysql> show create database 数据库名\G               --查看建数据库语句 
mysql> select database();                           --查看当前所在的数据库位置 
mysql> drop database [if exists] 数据库名;           --删除一个数据库
```

##### 数据表操作：

```mysql
mysql> show tables;             --查看当前库下的所有表格
mysql> desc tb1;                  --查看tb1的表结构。
mysql> show create table 表名\G  --查看表的建表语句。
mysql> create table demo(        --创建demo表格
    -> name varchar(16) not null,
    -> age int,
    -> sex enum('w','m') not null default 'm');
Query OK, 0 rows affected (0.05 sec)

mysql> show columns from demo;  --查看表结构
mysql> desc demo;                  --查看表结构
+-------+---------------+------+-----+---------+-------+
| Field | Type          | Null | Key | Default | Extra |
+-------+---------------+------+-----+---------+-------+
| name  | varchar(16)   | NO   |     | NULL    |       |
| age   | int(11)       | YES  |     | NULL    |       |
| sex   | enum('w','m') | NO   |     | m       |       |
+-------+---------------+------+-----+---------+-------+
3 rows in set (0.00 sec)

mysql>drop table if exists mytab;  -- 尝试删除mytab表格
```

##### 数据操作：

```
    --添加一条数据
    mysql> insert into demo(name,age,sex) values('zhangsan',20,'w');
    Query OK, 1 row affected (0.00 sec)

    --不指定字段名来添加数据
    mysql> insert into demo values('lisi',22,'m'); 
    Query OK, 1 row affected (0.00 sec)

    --指定部分字段名来添加数据
    mysql> insert into demo(name,age) values('wangwu',23); 
    Query OK, 1 row affected (0.00 sec)

    --批量添加数据
    mysql> insert into demo(name,age,sex) values('aaa',21,'w'),("bbb",22,'m');
    Query OK, 2 rows affected (0.00 sec)
    Records: 2  Duplicates: 0  Warnings: 0

    mysql> select * from demo; --查询数据

    mysql> update demo set age=24 where name='aaa';  --修改
    Query OK, 1 row affected (0.02 sec)
    Rows matched: 1  Changed: 1  Warnings: 0

    mysql> delete from demo where name='bbb';  --删除
    Query OK, 1 row affected (0.00 sec)
```

### 1.6  MySQL数据结构类型及操作：

##### MySQL的数据类型分为三个类：数值类型、字串类型、日期类型 。 还有一个特殊的值：NULL。

```
1 数值类型：
    *tinyint(1字节) 0~255  -128~127
    smallint(2字节)
    mediumint(3字节)
    *int(4字节)
    bigint(8字节)
    *float(4字节)   float(6,2)
    *double(8字节)  
    decimal(自定义)字串形数值

2 字串类型
    普通字串
    *char    定长字串        char(8)  
    *varchar 可变字串 varchar(8)

    二进制类型
    tinyblob
    blob
    mediumblob
    longblob

    文本类型
    tinytext
    *text      常用于<textarea></textarea>
    mediumtext
    longtext

    *enum枚举
    set集合

3 时间和日期类型：
    date  年月日
    time  时分秒
    *datetime 年月日时分秒
    timestamp 时间戳
    year 年

4 NULL值
    NULL意味着“没有值”或“未知值”
    可以测试某个值是否为NULL
    不能对NULL值进行算术计算
    对NULL值进行算术运算，其结果还是NULL
    0或NULL都意味着假，其余值都意味着真
```

##### MySQL的运算符：

```
    算术运算符：+ - * / % 
    比较运算符：= > < >= <= <> != 
    数据库特有的比较：in，not in, is null,is not null,like, between and 
    逻辑运算符：and or not
```

##### 表的字段约束：

```
    unsigned 无符号(正数)
    zerofill 前导零填充
    auto_increment 自增
    default    默认值
    not null  非空
    PRIMARY KEY 主键 （非null并不重复）
    unique 唯一性   （可以为null但不重复）
    index 常规索引
```

##### 建表语句格式：

```
 create table 表名(
   字段名 类型 [字段约束],
   字段名 类型 [字段约束],
   字段名 类型 [字段约束],
   ...
  );
mysql> create table stu(
    -> id int unsigned not null auto_increment primary key,
    -> name varchar(8) not null unique,
    -> age tinyint unsigned,
    -> sex enum('m','w') not null default 'm',
    -> classid char(6)
    -> );
Query OK, 0 rows affected (0.05 sec)


mysql> desc stu;
+---------+---------------------+------+-----+---------+----------------+
| Field   | Type                | Null | Key | Default | Extra          |
+---------+---------------------+------+-----+---------+----------------+
| id      | int(10) unsigned    | NO   | PRI | NULL    | auto_increment |
| name    | varchar(8)          | NO   | UNI | NULL    |                |
| age     | tinyint(3) unsigned | YES  |     | NULL    |                |
| sex     | enum('m','w')       | NO   |     | m       |                |
| classid | char(6)             | YES  |     | NULL    |                |
+---------+---------------------+------+-----+---------+----------------+
5 rows in set (0.00 sec)

mysql> show create table stu\G  --查看建表的语句
*************************** 1. row ***************************
       Table: stu
Create Table: CREATE TABLE `stu` (
  `id` int(10) unsigned NOT NULL auto_increment,
  `name` varchar(8) NOT NULL,
  `age` tinyint(3) unsigned default NULL,
  `sex` enum('m','w') NOT NULL default 'm',
  `classid` char(6) default NULL,
  PRIMARY KEY  (`id`),
  UNIQUE KEY `name` (`name`)
) ENGINE=MyISAM DEFAULT CHARSET=utf8
1 row in set (0.00 sec)
```

##### 修改表结构:

```mysql
格式： alter table 表名 action（更改选项）;
 更改选项：
    1. 添加字段：alter table 表名 add 字段名信息
        例如：
            -- 在user表的最后追加一个num字段 设置为int not null
            mysql> alter table user add num int not null;

            -- 在user表的email字段后添加一个age字段，设置int not null default 20；
            mysql> alter table user add age int not null default 20 after email;

            -- 在user表的最前面添加一个aa字段设置为int类型
            mysql> alter table user add aa int first;

    2. 删除字段：alter table 表名 drop 被删除的字段名
        例如：-- 删除user表的aa字段
             mysql> alter table user drop aa;

    3. 修改字段：alter table 表名 change[modify] 被修改后的字段信息
        其中：change可以修改字段名， modify 不修改
        例如：
        -- 修改user表中age字段信息（类型），（使用modify关键字的目的不修改字段名）
        mysql> alter table user modify age tinyint unsigned not null default 20;
        -- 修改user表的num字段改为mm字段并添加了默认值（使用change可以改字段名）
        mysql> alter table user change num mm int not null default 10;

    4. 添加和删除索引
        -- 为user表中的name字段添加唯一性索引，索引名为uni_name;
        mysql> alter table user add unique uni_name(name);
        -- 为user表中的email字段添加普通索引，索引名为index_eamil
        mysql> alter table user add index index_email(email);
        -- 将user表中index_email的索引删除
        mysql> alter table user drop index index_email;

    5. 更改表名称：
        ALTER TABLE 旧表名 RENAME AS 新表名

    6. 更改AUTO_INCREMENT初始值:
        ALTER TABLE 表名称 AUTO_INCREMENT=1

    7. 更改表类型：
        ALTER TABLE 表名称 ENGINE="InnoDB"

MySQL数据库中的表类型一般常用两种：MyISAM和InnoDB
区别：MyISAM类型的数据文件有三个frm(结构)、MYD（数据）、MYI（索引）
      MyISAM类型中的表数据增 删 改速度快，不支持事务，没有InnoDB安全。

      InnoDB类型的数据文件只有一个 .frm
      InnoDB类型的表数据增 删 改速度没有MyISAM的快，但支持事务，相对安全。
```

### 1.7 数据的DML操作：添加数据，修改数据，删除数据

##### 添加数据：

```
    格式： insert into 表名[(字段列表)] values(值列表...);

    --标准添加（指定所有字段，给定所有的值）
    mysql> insert into stu(id,name,age,sex,classid) values(1,'zhangsan',20,'m','lamp138');
    Query OK, 1 row affected (0.13 sec)

    mysql>
    --指定部分字段添加值
    mysql> insert into stu(name,classid) value('lisi','lamp138');
    Query OK, 1 row affected (0.11 sec)

    -- 不指定字段添加值
    mysql> insert into stu value(null,'wangwu',21,'w','lamp138');
    Query OK, 1 row affected (0.22 sec)

    -- 批量添加值
    mysql> insert into stu values
        -> (null,'zhaoliu',25,'w','lamp94'),
        -> (null,'uu01',26,'m','lamp94'),
        -> (null,'uu02',28,'w','lamp92'),
        -> (null,'qq02',24,'m','lamp92'),
        -> (null,'uu03',32,'m','lamp138'),
        -> (null,'qq03',23,'w','lamp94'),
        -> (null,'aa',19,'m','lamp138');
    Query OK, 7 rows affected (0.27 sec)
    Records: 7  Duplicates: 0  Warnings: 0
```

##### 修改操作：

```
    格式：update 表名 set 字段1=值1,字段2=值2,字段n=值n... where 条件 

    -- 将id为11的age改为35，sex改为m值
    mysql> update stu set age=35,sex='m' where id=11;
    Query OK, 1 row affected (0.16 sec)
    Rows matched: 1  Changed: 1  Warnings: 0

    -- 将id值为12和14的数据值sex改为m，classid改为lamp92
    mysql> update stu set sex='m',classid='lamp92' where id=12 or id=14 --等价于下面
    mysql> update stu set sex='m',classid='lamp92' where id in(12,14);
    Query OK, 2 rows affected (0.09 sec)
    Rows matched: 2  Changed: 2  Warnings: 0
```

##### 删除操作:

```
    格式：delete from 表名 [where 条件]

    -- 删除stu表中id值为100的数据
    mysql> delete from stu where id=100;
    Query OK, 0 rows affected (0.00 sec)

    -- 删除stu表中id值为20到30的数据
    mysql> delete from stu where id>=20 and id<=30;
    Query OK, 0 rows affected (0.00 sec)

    -- 删除stu表中id值为20到30的数据（等级于上面写法）
    mysql> delete from stu where id between 20 and 30;
    Query OK, 0 rows affected (0.00 sec)

    -- 删除stu表中id值大于200的数据
    mysql> delete from stu where id>200;
    Query OK, 0 rows affected (0.00 sec)
```

### 1.8 数据的DQL操作：数据查询

##### 格式：

```
    select [字段列表]|* from 表名
    [where 搜索条件]
    [group by 分组字段 [having 子条件]]
    [order by 排序 asc|desc]
    [limit 分页参数]
```

##### 各种查询：

```
    mysql> select * from stu;
    +----+----------+-----+-----+---------+
    | id | name     | age | sex | classid |
    +----+----------+-----+-----+---------+
    |  1 | zhangsan |  20 | m   | lamp138 |
    |  2 | lisi     |  20 | m   | lamp138 |
    |  3 | wangwu   |  21 | w   | lamp138 |
    |  4 | zhaoliu  |  25 | w   | lamp94  |
    |  5 | uu01     |  26 | m   | lamp94  |
    |  6 | uu02     |  28 | w   | lamp92  |
    |  7 | qq02     |  24 | m   | lamp92  |
    |  8 | uu03     |  32 | m   | lamp138 |
    |  9 | qq03     |  23 | w   | lamp94  |
    | 10 | aa       |  19 | m   | lamp138 |
    | 11 | sad      |  35 | m   | lamp94  |
    | 12 | tt       |  25 | m   | lamp92  |
    | 13 | wer      |  25 | w   | lamp94  |
    | 14 | xx       |  25 | m   | lamp92  |
    | 15 | kk       |   0 | w   | lamp94  |
    +----+----------+-----+-----+---------+
    15 rows in set (0.00 sec)

    1. where条件查询
    1. 查询班级为lamp138期的学生信息
    mysql> select * from stu where classid='lamp138';

    2. 查询lamp138期的男生信息（sex为m）
    mysql> select * from stu where classid='lamp138' and sex='m';

    3. 查询id号值在10以上的学生信息
    mysql> select * from  stu where id>10;

    4. 查询年龄在20至25岁的学生信息
    mysql> select * from stu where age>=20 and age<=25;
    mysql> select * from stu where age between 20 and 25;

    5. 查询年龄不在20至25岁的学生信息
    mysql> select * from stu where age not between 20 and 25;
    mysql> select * from stu where age<20 or age>25;

    6. 查询id值为1,8,4,10,14的学生信息
    select * from stu where id in(1,8,4,10,14);
    mysql> select * from stu where id=1 or id=8 or id=4 or id=10 or id=14;

    7. 查询lamp138和lamp94期的女生信息
    mysql> select * from stu where classid in('lamp138','lamp94') and sex='w';
    mysql> select * from stu where (classid='lamp138' or classid='lamp94') and sex='w
```

### 1.9 数据库授权、备份和恢复

##### 授权：

```
    格式：grant 允许操作 on 库名.表名 to 账号@来源 identified by '密码';

    --实例：创建zhangsan账号，密码123，授权lamp61库下所有表的增/删/改/查数据,来源地不限
    mysql> grant select,insert,update,delete on lamp61.* to zhangsan@'%' identified by '123';
    mysql> grant all on *.* to zhangsan@'%' identified by '123';
    Query OK, 0 rows affected (0.00 sec) 

    -- 授权一个用户（zhangsan）密码123，可以对所有的库，所有的表做所有操作。
    mysql> grant all on *.* to zhangsan@'%' identified by '123';
    Query OK, 0 rows affected (0.17 sec)

    --刷新生效，否则就要重启MySQL服务才可以。
    mysql> flush privileges;
    Query OK, 0 rows affected (0.00 sec)

    --浏览当前MySQL用户信息
    mysql> select user,host,password from mysql.user;
    +----------+-----------------+-------------------------------------------+
    | user     | host            | password                                  |
    +----------+-----------------+-------------------------------------------+
    | root     | localhost       | *23AE809DDACAF96AF0FD78ED04B6A265E05AA257 |
    | root     | 127.0.0.1       |                                           |
    |          | localhost       |                                           |
    | zhangsan | %               | *23AE809DDACAF96AF0FD78ED04B6A265E05AA257 |
    | admin    | 192.168.112.132 | *23AE809DDACAF96AF0FD78ED04B6A265E05AA257 |
    +----------+-----------------+-------------------------------------------+
    5 rows in set (0.00 sec)

    -- 移除一些权限
    -- revoke:只删除了用户权限，但没有删除这个用户
    mysql> revoke insert,delete on *.* from admin@192.168.112.132 identified by'123';

    -- 查看指定用户的权限信息
    mysql> show grants for xbb@localhost;
    +------------------------------------------------------------------------------------------------------------+
    | Grants for xbb@localhost                                                                                   |
    +------------------------------------------------------------------------------------------------------------+
    | GRANT USAGE ON *.* TO 'xbb'@'localhost' IDENTIFIED BY PASSWORD '*23AE809DDACAF96AF0FD78ED04B6A265E05AA257' |
    +------------------------------------------------------------------------------------------------------------+

    --drop user:删除了整个用户及其权限（包括数据字典中的数据）
    mysql> drop user 'xbb'@'localhost';
    Query OK, 0 rows affected (0.00 sec)

    mysql> select user,host from mysql.user;
    +------------------+-----------+
    | user             | host      |
    +------------------+-----------+
    | root             | 127.0.0.1 |
    | debian-sys-maint | localhost |
    | root             | localhost |
    | root             | wangxg    |
    +------------------+-----------+
    4 rows in set (0.00 sec)
```

##### 备份与恢复（导入和导出）

```
-- 将lamp138库导出
D:\>mysqldump -u root -p lamp138 >lamp138.sql
Enter password:

---- 将lamp138库中的stu表导出
D:\>mysqldump -u root -p lamp138 stu >lamp138_stu.sql
Enter password:

-- 将lamp138库导入
D:\>mysql -u root -p lamp138<lamp138.sql
Enter password:

-- 将lamp138库中stu表导入
D:\>mysql -u root -p lamp138<lamp138_stu.sql
Enter password:
```

### 1.10 MySQL的多表联查

- 表之间的关系有：1对1  1对多  多对多

```
1. 嵌套查询:一个查询的结果是另外sql查询的条件：
    如：查询stu表中年龄最大的是谁？
    mysql> select * from stu where age=(select max(age) from stu);
    mysql> select * from stu where age in(select max(age) from stu); --（子查询结果是多条时使用in查询）
    +----+------+------+-----+----------+
    | id | name | age  | sex | classid  |
    +----+------+------+-----+----------+
    | 14 | abc  |   33 | w   | python01 |
    +----+------+------+-----+----------+
    1 row in set (0.01 sec)

2. where关联查询

    已知：员工personnel表和部门department表，其中员工表中的did字段为部门表id主键关联。
          查询所有员工信息，并显示所属部门名称
    要求：显示字段：员工id  部门 姓名
    mysql> select p.id,d.name,p.name from personnel p,department d where p.did = d.id;
        +----+-----------+-----------+
        | id | name      | name      |
        +----+-----------+-----------+
        |  2 | 人事部    | 李玉刚    |
        | 10 | 人事部    | 阿杜      |
        |  4 | 市场部    | 刘欢      |
        。。。。


3. 连接join查询
    左联：left join
    右联：right join
    内联：inner join

已知如下表所示，商品类别信息表（具有两层类别关系，通过pid表示，0表示一级类别）
mysql> select * from type;
+----+-----------+------+
| id | name      | pid  |
+----+-----------+------+
|  1 | 服装      |    0 |
|  2 | 数码      |    0 |
|  3 | 男装      |    1 |
|  4 | 手机      |    2 |
|  5 | 相机      |    2 |
|  6 | 电脑      |    2 |
|  7 | 女装      |    1 |
|  8 | 童装      |    1 |
|  9 | 食品      |    0 |
| 10 | 零食      |    9 |
| 11 | 特产      |    9 |
| 12 | 休闲装    |    1 |
+----+-----------+------+
12 rows in set (0.00 sec)

mysql> desc type;
+-------+------------------+------+-----+---------+----------------+
| Field | Type             | Null | Key | Default | Extra          |
+-------+------------------+------+-----+---------+----------------+
| id    | int(10) unsigned | NO   | PRI | NULL    | auto_increment |
| name  | varchar(16)      | NO   |     | NULL    |                |
| pid   | int(10) unsigned | YES  |     | NULL    |                |
+-------+------------------+------+-----+---------+----------------+
3 rows in set (0.00 sec)

-- 查询二级类别信息，并关联出他们的父类别名称
mysql> select  t1.id,t1.name,t2.name  from type t1,type t2 where t1.pid!=0 and t1.pid=t2.id;
+----+-----------+--------+
| id | name      | name   |
+----+-----------+--------+
|  3 | 男装      | 服装   |
|  4 | 手机      | 数码   |
|  5 | 相机      | 数码   |
|  6 | 电脑      | 数码   |
|  7 | 女装      | 服装   |
|  8 | 童装      | 服装   |
| 10 | 零食      | 食品   |
| 11 | 特产      | 食品   |
| 12 | 休闲装    | 服装   |
+----+-----------+--------+
9 rows in set (0.01 sec)

--统计每个一级类别下都有多少个子类别。
mysql> select t1.id,t1.name,count(t2.id) from type t1,type t2 where t1.pid=0 and t1.id=t2.pid group by t1.id;
+----+--------+--------------+
| id | name   | count(t2.id) |
+----+--------+--------------+
|  1 | 服装   |            4 |
|  2 | 数码   |            3 |
|  9 | 食品   |            2 |
+----+--------+--------------+
3 rows in set (0.00 sec)
```

### 1.11 MySQL的其他操作

```
1. MySQL的表复制
    复制表结构
    mysql> create table 目标表名 like 原表名;

    复制表数据
    mysql> insert into 目标表名 select * from 原表名; 

2. 数据表的索引
    创建索引
    CREATE INDEX index_name ON table_name (column_list)
    CREATE UNIQUE INDEX index_name ON table_name (column_list)

    删除索引
    DROP INDEX index_name ON talbe_name

3. mysql视图
    创建视图:
    mysql> create view v_t1 as select * from t1 where id>4 and id<11;
    Query OK, 0 rows affected (0.00 sec)

    view视图的帮助信息:
    mysql> ? view
    ALTER VIEW
    CREATE VIEW
    DROP VIEW

    查看视图:
    mysql> show tables;

    删除视图v_t1:
    mysql> drop view v_t1;

4. MySQL的内置函数
    字符串处理函数
    ---------------------------------------------
    *concat(s1,s2,…Sn) 连接s1,s2..Sn为一个字符串
    insert(str,x,y,instr)将字符串str从第xx位置开始，y字符串的子字符串替换为字符串str
    lower(str)将所有的字符串变为小写
    upper(str)将所有的字符串变为大写
    left(str,x)返回字符串中最左边的x个字符
    rigth(str,y)返回字符串中最右边的x个字符
    lpad(str,n,pad)用字符串pad对str最左边进行填充，直到长度为n个字符串长度
    rpad(str,n,pad)用字符串pad对str最右边进行填充，直到长度为n个字符串长度
    trim(str)  去掉左右两边的空格
    ltrim(str) 去掉字符串str左侧的空格
    rtrim(str) 去掉字符串str右侧的空格
    repeat(str,x)   返回字符串str重复x次
    replace(str,a,b)将字符串的的a替换成b
    strcmp(s1,s2)   比较字符串s1和s2
    substring(s,x,y)返回字符串指定的长度
    *length(str)  返回值为字符串str 的长度    

    数值函数
    -----------------------------------------------------
    *abs(x)    返回x的绝对值
    ceil(x)   返回大于x的最小整数值
    floor(x)  返回小于x的最大整数值
    mod(x,y)  返回x/y的取余结果
    rand()    返回0~1之间的随机数
    *round(x,y)返回参数x的四舍五入的有y位小数的值
    truncate(x,y) 返回x截断为y位小数的结果

    日期和时间函数
    ---------------------------------------------------
    curdate()  返回当前日期,按照’YYYY-MM-DD’格式
    curtime()  返回当前时间,当前时间以'HH:MM:SS' 
    *now()      返回当前日期和时间,
    *unix_timestamp(date) 返回date时间的unix时间戳
    from_unixtime(unix_timestamp[,format])    返回unix时间的时间
    week(date)        返回日期是一年中的第几周
    year(date)      返回日期的年份
    hour(time)      返回time的小时值
    minute(time)    返回日time的分钟值
    monthname(date) 返回date的月份
    *date_fomat(date,fmt) 返回按字符串fmt格式化日期date值
    date_add(date,INTERVAL,expr type) 返回一个日期或者时间值加上一个时间间隔的时间值
    *datediff(expr,expr2)   返回起始时间和结束时间的间隔天数

    //统计时间戳647583423距离当前时间相差天数（生日天数（不考虑年份））
    mysql> select datediff(date_format(from_unixtime(647583423),"2017-%m-%d %h:%i:%s"),now());

    其他常用函数
    ------------------------------------------------------
    *database() 返回当前数据库名
    version()   返回当前服务器版本
    user()        返回当前登陆用户名
    inet_aton   返回当前IP地址的数字表示 inet_aton("192.168.80.250");
    inet_ntoa(num) 返回当前数字表示的ip   inet_ntoa(3232256250);
    *password(str)  返回当前str的加密版本
    *md5(str)      返回字符串str的md5值

5. MySQL的事务处理
    关闭自动提交功能（开启手动事务）
    mysql> set autocommit=0;
    从表t1中删除了一条记录
    mysql> delete from t1 where id=11;
    此时做一个p1还原点:
    mysql> savepoint p1;
    再次从表t1中删除一条记录:
    mysql> delete from t1 where id=10;
    再次做一个p2还原点:
    mysql> savepoint p2;
    此时恢复到p1还原点，当然后面的p2这些还原点自动会失效: 
    mysql> rollback to p1;
    退回到最原始的还原点:
    mysql> rollback;
    回滚

    开启自动事务提交（关闭手动事务）
    mysql> set autocommit=1;

6. MySQL的触发器
    格式：1、触发器的定义：
      CREATE TRIGGER trigger_name trigger_time trigger_event
        ON tbl_name FOR EACH ROW trigger_stmt

      说明：
      # trigger_name：触发器名称
      # trigger_time:触发时间，可取值：BEFORE或AFTER
      # trigger_event：触发事件，可取值：INSERT、UPDATE或DELETE。
      # tb1_name：指定在哪个表上
      # trigger_stmt：触发处理SQL语句。

    示例：
        mysql> delimiter $$
        mysql> create trigger del_stu before delete on stu for each row
            -> begin
            ->  insert into stu_bak values(old.id,old.name,old.sex,old.age,old.addtime);
            -> end;
            -> $$
        Query OK, 0 rows affected (0.05 sec)

        mysql> delimiter ;

7. mysql日志
    开启日志： 在mysql配置文件中开启：log-bin=mysql-bin

    查看bin-log日志:
    mysql>show binary logs;

    查看最后一个bin-log日志:
    mysql>show master status;

    此时就会多一个最新的bin-log日志
    mysql>flush logs;

    查看最后一个bin日志.
    mysql>show master status;

    mysql>reset master;
    清空所有的bin-log日志
    执行查看bin-log日志

    备份数据:
    mysqldump -uroot -pwei test -l -F '/tmp/test.sql'
    其中：-F即flush logs，可以重新生成新的日志文件，当然包括log-bin日志 

    // Linux关闭MySQL的命令
    $mysql_dir/bin/mysqladmin -uroot -p shutdown
    // linux启动MySQL的命令
    $mysql_dir/bin/mysqld_safe &

8、有关慢查询操作：
    开户和设置慢查询时间:
    vi /etc/my.cnf
    log_slow_queries=slow.log
    long_query_time=5
    查看设置后是否生效
    mysql> show variables like "%quer%"; 
    慢查询次数:
    mysql> show global status like "%quer%";

9 数据库的恢复
    1. 首先恢复最后一次的备份完整数据
    [root@localhost mnt]# mysql -u root -p mydemo<mydemo_2017-7-26.sql 
    Enter password: 

    2. 查看bin-log日志
    [root@localhost data]# mysqlbinlog --no-defaults mysql-bin.000009;
      查找到恢复的节点

    3. 执行bin-log日志文件，恢复最后一块的增量数据。 
    [root@localhost data]# mysqlbinlog --no-defaults --stop-position="802" mysql-bin.000009|mys
```

### 2 mariadb — 简洁版MySQL

- 可下载 MariaDB 开源的 https://downloads.mariadb.org**【推荐使用】**

- **mariadb是mysql的一个分支，安装方便，且安装之后可直接使用，其中的操作与mysql也是一致的，所以建议使用mariadb。[安装的所有过程直接next即可。]**
- **注意：mariadb和mysql是虽然可以同时存在，但是由于两个的端口号都是默认3306，所以在命令行启动数据库时，会只启动mariadb，其中他们两个的操作是一致的，所以安装一个就可以了，建议mariadb**
- **安装步骤**

![1573183254751](/Users/yhhang/Desktop/Python3.0课程体系研发/录播大课/产出物/文档/Python基础第二周/image/1573183254751.png)

![1573183308315](/Users/yhhang/Desktop/Python3.0课程体系研发/录播大课/产出物/文档/Python基础第二周/image/1573183308315.png)

![1573183442363](/Users/yhhang/Desktop/Python3.0课程体系研发/录播大课/产出物/文档/Python基础第二周/image/1573183442363.png)

![1573183554164](/Users/yhhang/Desktop/Python3.0课程体系研发/录播大课/产出物/文档/Python基础第二周/image/1573183554164.png)

![1573183869764](/Users/yhhang/Desktop/Python3.0课程体系研发/录播大课/产出物/文档/Python基础第二周/image/1573183869764.png)

![1573184059316](/Users/yhhang/Desktop/Python3.0课程体系研发/录播大课/产出物/文档/Python基础第二周/image/1573184059316.png)

![1573184109437](/Users/yhhang/Desktop/Python3.0课程体系研发/录播大课/产出物/文档/Python基础第二周/image/1573184109437.png)

等待安装完成即可。

- 在安装完成之后再桌面会显示HeidiSQL，此为mariadb的图像化，直接点开直接使用即可。

![1573184271802](/Users/yhhang/Desktop/Python3.0课程体系研发/录播大课/产出物/文档/Python基础第二周/image/1573184271802.png)

- mariadb的操作命令与mysql的操作命令是一样的，直接使用mysql的建库，建表语句即可。

## 3 python数据库支持【扩展】

#### 3.1 什么是 PyMySQL？

- PyMySQL 是在 Python3.x 版本中用于连接 MySQL 服务器的一个库，Python2中则使用mysqldb。
- PyMySQL 遵循 Python 数据库 API v2.0 规范，并包含了 pure-Python MySQL 客户端库。

#### 3.2 PyMySQL安装

- PyMySQL下载地址：https://github.com/PyMySQL/PyMySQL。

##### 3.2.1 使用pip命令进行安装：

```
$ pip install PyMySQL
```

##### 3.2.2 使用 git 命令下载安装包安装(你也可以手动下载)：

```
$ git clone https://github.com/PyMySQL/PyMySQL
$ cd PyMySQL/
$ python3 setup.py install
```

#### 3.3 数据库连接

##### 3.3.1 通过如下代码测试数据库连接

```python
#!/usr/bin/python3

import pymysql

# 打开数据库连接
db = pymysql.connect(host="localhost",user="root",password="",db="mydb",charset="utf8")

# 使用 cursor() 方法创建一个游标对象 cursor
cursor = db.cursor()

# 使用 execute()  方法执行 SQL 查询 
cursor.execute("SELECT VERSION()")

# 使用 fetchone() 方法获取单条数据.
data = cursor.fetchone()

print ("Database version : %s " % data)

# 关闭数据库连接
db.close()
```

##### 3.3.2 执行数据查询：

```python
#!/usr/bin/python3

import pymysql

#打开数据库连接
db = pymysql.connect(host="localhost",user="root",password="",db="mydb",charset="utf8")

#使用cursor()方法创建一个游标对象cursor
cursor = db.cursor()

#定义查询sql语句
#sql = "select * from stu"
sql = "select * from stu where classid='%s'"%("python03")

try:
    # 使用execute()方法执行SQL查询 
    cursor.execute(sql)

    print("本次查询条数：",cursor.rowcount)
    '''
    # 使用fetchone()方法获取单条数据.
    while True:
        data = cursor.fetchone();
        if data == None:
            break;
        print (data)
    '''
    #使用fetchall()获取所有结果
    alist = cursor.fetchall()
    for vo in alist:
        print(vo)

except Exception as err:
    print("SQL执行错误，原因：",err)

# 关闭数据库连接
db.close()
```

##### 3.3.3 执行数据添加

```python
#!/usr/bin/python3

import pymysql

#打开数据库连接
db = pymysql.connect(host="localhost",user="root",password="",db="mydb",charset="utf8")

#使用cursor()方法创建一个游标对象cursor
cursor = db.cursor()

#定义添加sql语句
data = ("uu100",28,'w','python05')
sql = "insert into stu(name,age,sex,classid) values('%s','%d','%s','%s')"%(data)

try:
    # 使用execute()方法执行SQL 
    m = cursor.execute(sql)
    # 事务提交
    db.commit()
    print("成功操作条数：",m)
    #print("成功操作条数：",cursor.rowcount)
except Exception as err:
    #事务回滚
    db.rollback()
    print("SQL执行错误，原因：",err)

# 关闭数据库连接
db.close()
```

##### 3.3.4 执行删除操作

```python
#!/usr/bin/python3

import pymysql

#打开数据库连接
db = pymysql.connect(host="localhost",user="root",password="",db="mydb",charset="utf8")

#使用cursor()方法创建一个游标对象cursor
cursor = db.cursor()

#定义删除sql语句
sql = "delete from stu where id=%d"%(100)

try:
    # 使用execute()方法执行SQL 
    cursor.execute(sql)
    # 事务提交
    db.commit()
    print("成功删除条数：",cursor.rowcount)
except Exception as err:
    #事务回滚
    db.rollback()
    print("SQL执行错误，原因：",err)

# 关闭数据库连接
db.close()
```

#### 3.4 数据库查询操作：

- Python查询Mysql使用 fetchone() 方法获取单条数据, 使用fetchall() 方法获取多条数据。
  - fetchone(): 该方法获取下一个查询结果集。结果集是一个对象，最后返回None结束
  - fetchall(): 接收全部的返回结果行.
- rowcount: 这是一个只读属性，并返回执行execute()方法后影响的行数。

##