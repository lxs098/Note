>  数据库操作
    
    #创建数据库
    create database 库名 charset utf8;
    
    #切换数据库
    use db_sanguo
    
    #查看所有存在的数据库
    show databases;
    
    查看当前选择的数据库
    select database();
    
    #MySQL数据库默认编码是Latin1，如果在创建数据库忘记指定字符集为utf8，可以通过下面方法修改
    alter database 表名 charset utf8;
    
    删除数据库
    drop database 数据库名;
    
> 数据表操作

    查看当前数据库中所有表
    show tables;
    
    查看表结构
    desc 表名;
    
    auto_increment表示自动增长
    
    create table 表名(列 类型 约束,...);
    
    create table classes(
    id int unsigned auto_increment primary key not null,
    name varchar(10),
    isdelete bit default 0
    );
    
    修改表-添加字段
    alter table 表名 add 列名 类型;
    
    修改表-修改字段：重命名版
    alter table 表名 change 原名 新名 类型及约束;
    
    修改表-修改字段：不重命名版
    alter table 表名 modify 列名 类型及约束
    
    修改表-删除字段
    alter table 表名 drop 列名;
    
    删除表
    drop table 表名;
    
    #数据清空
    让数据表ID从零开始
    方法1：
    truncate table 你的表名
    //这样不但将数据全部删除，而且重新定位自增的字段
    方法2：
    delete from 你的表名
    dbcc checkident(你的表名,reseed,0) 
    //重新定位自增的字段，让它从1开始
        
    