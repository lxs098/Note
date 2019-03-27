> insert插入

    全列插入：值的顺序与表中字段的顺序对应
    insert into 表名 values(...)
    例：
    insert into students values(0,'郭靖',1,'蒙古','2015-1-2');
    部分列插入：值的顺序与给出的列顺序对应
    insert into 表名(列1,...) values(值1,...)
    例：
    insert into students(name,hometown,birthday) values('黄蓉','桃花岛','2015-3-2');
    上面的语句一次可以向表中插入一行数据，还可以一次性插入多行数据，这样可以减少与数据库的通信
    全列多行插入：值的顺序与给出的列顺序对应
    insert into 表名 values(...),(...)...;
    例：
    insert into classes values(0,'python'),(0,'linux'),(0,'mysql'),(0,'js');
    insert into 表名(列1,...) values(值1,...),(值1,...)...;
    例：
    insert into students(name) values('杨康'),('杨过'),('小龙女');
    
> delete 删除

    delete from 表名 where 条件
    例：
    delete from students where id=5;

> update 修改

    update 表名 set 列1=值1,列2=值2... where 条件
    例：
    update students set gender=0,hometown='古墓' where id=5;