> 数据删除

    db.collection.remove();#删除所有数据
    db.collection.remove({"22":"女"});#按照条件删除
    db.collection.remove({"key":"value"},2);#删除2条