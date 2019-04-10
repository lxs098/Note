### 简单查询
    
    #查询全部
    select * from 表名；
    # 比较运算
    # 根据WHERE条件查找数据: = > < >= <= !=
    select * from 表名 where 条件;
    # 逻辑判断
    # AND : 指定多个条件，所有条件必须满足
    select * from 表名 where 条件 and 条件;
    # OR ： 指定多个条件，满足任意一个条件即可
    select * from 表名 where 条件 or 条件;
    # NOT：不满足指定条件，
    select * from 表名 where not 条件;
    
### 模糊查询

    # 模糊查询 like
    # % ： 代表任意多个的任意字符
    select * from 表名 where 字段 like "%内容%";
    
    # _ ： 代表一个任意字符，如果多个_ 则表示多个任意字符
    select *from 表名 where 字段 like "_内容_";
    
### 固定范围查询

    # 范围查询： IN 表示查询的值指定的集合内;
    select *from 表名 where 字段 in (30, 45);
    # 范围查询：NOT IN 表示查询的字符不在指定的集合内
    select *from 表名 where 字段 not in (30, 45);
    
### 区间范围查询

    # BETWEEN AND:查询的数据在指定的范围区间内，满足条件即可
    select *from 表名 where 字段 between 30 and 40;
    # NOT BETWEEN AND查询的数据不在指定的范围区间内，满足条件即可
    select *from 表名 where 字段  not between 30 and 40;
    
### 空值查询

    # IS NULL :表示查找数据为空的数据
    select *from 表名 where 字段 is null;
    # IS NOT NULL： 表示查找非空的数据
    select *from 表名 where 字段 is  not null;
    
### 聚合函数

    # count ：统计个数，
    select count(*) from 表名 where 条件;
    # max：统计某个列里的最大值，比如age
    select max(age) from 表名 where 条件;
    # min：统计某个列里的最小值
    select min(age)  from 表名 where 条件;
    # sum: 统计某一列的数据之和，as 可以给查出的数据列起别名
    select sum(age)  from 表名 where 条件;
    # avg：统计某一列数据的平均值
    select avg(age)  from 表名 where 条件;
    
    
### GROUP BY 分组操作

    1. 单独使用：直接对数据进行分组（单独使用没有任何意义）
    select * from 表名 group by 字段;
    2. GROUP_CONCAT：对数据进行分组，并通过GOURP_CONCAT() 将指定列数据拼接到一起
    select 字段, group_concat(字段) from t_hero GROUP BY 字段;
    
    
    3. 聚合函数：对数据进行分组，分组后的数据根据查询语句的聚合函数来统计指定的数据
    SELECT 字段, sum(字段) FROM t_hero GROUP BY 字段;
    
    
    4. HAVING : 限制输出结果（对select 查询的结果进行限制输出）：
    # having是对最后select 的结果进行限制输出，having的字段必须在select查询的字段里
    SELECT 字段, count(字段)  FROM 表名 GROUP BY 字段 HAVING 条件;
    SELECT 字段, count(字段)  FROM 表名 GROUP BY 字段 HAVING 条件;
    
### 排序：ORDER BY

    #　order by 对指定的列进行排序，
    # 默认是升序(从小到大), ASC （ascend)
    select * from 表名 ORDER BY id;
    select * from 表名 ORDER BY 字段 ASC;
    
    # DESC 指定为降序（从大到小）
    select * from 表名 ORDER BY 字段 DESC;
    
    # 配合where条件进行排序
    select * from 表名 where 条件 and 条件 ORDER BY 字段 DESC;
    
### 分页查询： limit

    # limit 后的参数：第一个表示 起始位置(下标从0开始)，第二个参数是显示的个数(表示本次基于起始位置显示多少个)
    select * from 表名 limit 0,3
    
    # 结合where条件：只显示state不为null 的结果
    select * from 表名 where 字段 is not null limit 0,20
    
    
### 内连接

    1. 内连接：INNER JOIN ON
    #连接查询：表示查询所有数据的非NULL部分
    #默认是内连接
    select * from t_book, t_bookType where t_book.bookTypeId = t_bookType.id;
    # 给每张表起别名用：as
    
### 显示连接

    # 显式连接
    SELECT tb.bookName, tb.price, tby.bookTypeName
    FROM t_book as tb
    INNER JOIN t_bookType as tby
    ON tb.bookTypeId = tby.id;
    
    交集： 属于A集合，也 属于B集合 的数据， A & B
    并集： 属于A集合 和 属于B 的数据的全部集合， A | B（重复数据只保留一个）
    
### 左连接

    2. 左连接 ： LEFT JOIN    ON
    # 两张表连接查询，无论二者是否有数据缺失，一定会把左边的表数据全部显示出来
    SELECT *
    FROM t_book
    LEFT JOIN t_bookType
    ON t_book.bookTypeId = t_bookType.id
    
### 右链接

    3. 右连接： RIGHT JOIN    ON
    # 两张表连接查询，无论二者是否有数据缺失，一定会把右边的表数据全部显示出来
    SELECT *
    FROM t_book
    RIGHT JOIN t_bookType
    ON t_book.bookTypeId = t_bookType.id
    
    SELECT tb.bookName, tb.price, tb.author, tby.bookTypeName
    FROM t_book as tb
    RIGHT JOIN t_bookType as tby
    ON tb.bookTypeId = tby.id
    
### 全连接

    4. 全连接： UNION ：
    # 两张表连接查询，无论二者是否有数据缺失，一定会都显示表数据全部显示出来
    
    SELECT tb.bookName, tb.price, tb.author, tby.bookTypeName
    FROM t_book as tb
    LEFT JOIN t_bookType as tby
    ON tb.bookTypeId = tby.id
    UNION
    SELECT tb.bookName, tb.price, tb.author, tby.bookTypeName
    FROM t_book as tb
    RIGHT JOIN t_bookType as tby
    ON tb.bookTypeId = tby.id
    
    SELECT tb.bookName,tb.author,tby.bookTypeName FROM t_book tb,t_bookType tby WHERE tb.bookTypeId=tby.id AND tb.price>30;


### 子查询

    1. 子查询： IN
    #在  select 语句的返回值的集合里里查找，复合集合里的数据的部分，才会匹配成功。
    SELECT *
    FROM t_book
    WHERE bookTypeId
    IN (SELECT id FROM t_bookType);
    
    
    2. 子查询： NOT IN：
    #　和  in相反，不在集合里的数据，才会匹配成功
    SELECT *
    FROM t_book
    WHERE bookTypeId
    NOT IN (SELECT id FROM t_bookType);
    
    
    3. 子查询：EXISTS 返回Bool值，如果子查询语句里查询成功，则返回True，否则返回False
    SELECT *
    FROM t_book
    WHERE EXISTS
    (SELECT * FROM t_bookType);
    
    4. 子查询：NOT EXISTS： 对子查询语句返回的结果取反。
    
    SELECT *
    FROM t_book
    WHERE NOT EXISTS
    (SELECT * FROM t_bookType);
    
    
