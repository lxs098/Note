> 数据查询   
   
    db.collection.find()  #查询所有数据
    db.collection.find().pretty() #json格式显示
    db.collection.find().count() #查询数量
    
    db.collection.find().sort({"key":-1});#按照sort里面key的值排序，1为正序，-1为倒序
    $lt <, $lte <=, $gt >, $gte >=
    db.collection.find({"key": {"$gte": 18,"$lte": 30}})#年龄大于等于18 and 小于等于30
    db.collection.find({"key":  {"$in": [725， 542， 390]}})
    db.collection.find({“key”: {“$not”: {“$mod”: [5, 1]}}})
    #正则查询  abC表示正则，  i 表示不区分大小写，等同于下一条查询
    db.collection.find( { key: { $regex: 'abC', $options: 'i'}})
    db.collection.find( { key: /adC/i } ); 
    db.collection.find({“id_num”: {“$mod”: [5, 1]}})#$mod代表python中的%，取余
    db.collection.find({"key":"value"})  #条件查询
    db.collection.find({"key":"value","key":"value"}) #多条件查询，代表python中的and
    db.collection.find({$or:[{"key":"value"},{"key":"value"}]}) #多条件查询，代表python中的or
    db.collection.findOne()  #查询单条数据