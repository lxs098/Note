> 数据修改

    #如果有多条语句，只修改第一条，会覆盖原有数据
    db.collection.update({"name":"张三"},{"name":"张三丰"});
    db.collection.update({"22":"女"},{"name":"张三丰"});
    db.collection.update({"name":"张三"},{$set:{"name":"张无忌"}});#只想改某个key的value使用set
    db.collection.update({"name":"王五"},{$set:{"name":"张无忌"}},{multi:true});#把所有的记录都改了
    