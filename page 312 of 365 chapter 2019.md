

##### 边框样式
```
border: 4px solid red
```

---
##### 数据的添加
##### 在flask中修改数据后需要添加事务和提交事务
```
事务: 完整，一致，持久，原子
第一种:保存数据
将数据放入缓存
db.session.add(stu)
将缓存中的数据提交
db.session.commit()
```

##### 在学生表中添加数据
```
@blue.route('/createstu/')
def create_stu():
    s = Student()
    s.s_name = '小花'
    s.s_age = 19
 
    db.session.add(s)
    db.session.commit()
 
    return '添加成功'
    
提交事务，使用commit提交我们的添加数据的操作

```




