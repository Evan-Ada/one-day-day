# MD语法入门

#### 1.前面带#号，后面带文字，分别表示h1-h6,只到h6，而且h1下面会有一条横线

# 一级标题
## 二级标题
### 三级标题
#### 四级标题
##### 五级标题
###### 六级标题


#### 无序列表
//形式有三种
+ a
+ b
+ c 

- d
- e
- f

* g
* h
* i

#### 有序列表
//正常形式
1. abc
2. bcd
3. cde
3. fgh
3. ghi
5. hij

#### 嵌套列表
//无序列表嵌套
+ 123
    + abc
    + bcd
    + cde
+ 465
+ 789
1. abcd
    1. abcde
    2. abcde
    3. abcde
2. bcde
3. cdef

#### 代码块

```
asdasdasd
```



#### 链接

* 行内式
  * 链接的文字放在[]中，链接地址放在随后的()中，链接也可以带title属性，链接地址后面空一格，然后用引号引起来
[简书](https://www.jianshu.com "创作你的创作"),
是一个创作社区,任何人均可以在其上进行创作。用户在简书上面可以方便的创作自己的作品,互相交流。   



#### 分割线
- - -
***
---


#### 强调字体
__强调字体__
**qiangdiaozit**
*一颗星星表示斜体*
_一个下划线也表示斜体_

#### 删除线
~~两个~表示删除线~~




---

数据的查询
```

all():查询全部的数据,其结果是一个列表，每一个元素都是一个对象
    students = Student.query.all()
 
过滤查询:
    第一种:filter,结果是baseQuery objects,
    过滤条件的格式:对象.属性==值
    studnets = Student.query.filter(Student.id==1)
    第二种:filter_by,结果是baseQuery objects,可以进行遍历
    students = Student.query.filter_by(id=1)
    第三种:原生sql查询id=1的信息，结果是一个可以遍历的对象
    sql = 'select * from student where id=1;'
    students = db.session.execute(sql)
    
模糊查询:
    语法:filter(模型名.属性.运算符('xx'))
    运算符:
        contains：包含
        startswith：以什么开始
        endswith：以什么结束
        in_：在范围内
        like：模糊
        __gt__: 大于
        __ge__：大于等于
        __lt__：小于
        __le__：小于等于
        
例子:
# 模糊查询，查询姓名中包含小花的学生信息
# django中filter(s_name__contains='小花')
    students = Student.query.filter(Student.s_name.contains('小花'))
    
# 以什么开始
    students = Student.query.filter(Student.s_name.startswith('小'))
    
 # 以什么结束
    students = Student.query.filter(Student.s_name.endswith('1'))
    
# 查询年龄大于等于16的学生信息
    students = Student.query.filter(Student.s_age.__gt__(15))
    
# 查询id在10到20之间的学生的学生信息
    students = Student.query.filter(Student.s_age.in_([10,11,12]))
 
# 查询年龄小于17的学生信息
    Student.query.filter(Student.s_age < 17)
    students = Student.query.filter(Student.s_age.__lt__(17))
        
# 模糊查询，使用like，查询姓名中第二位为花的学生信息
# like '_花%',_代表必须有一个数据，%任何数据
    students = Student.query.filter(Student.s_name.like('_花%'))
        
    
筛选:
 
offset()
    # 跳过3个数据
    stus = Student.query.offset(3)
 
limit()
    # 跳过3个数据，查询5个信息
    stus = Student.query.offset(3).limit(5)
 
order_by()
    # 按照id降序,升序
    students = Student.query.order_by('id')
    students = Student.query.order_by('-id')
 
    students = Student.query.order_by(desc('id'))
    students = Student.query.order_by(asc('id'))
 
    students = Student.query.order_by('id desc')
    students = Student.query.order_by('id asc')
 
get()
    #使用get，获取id=1的学生对象,get()默认接收id
    # 拿不到值不会报错，返回空
    students = Student.query.get(4)
 
first()
    # 获取年龄最大的一个
    stus = Student.query.order_by('-s_age').first()
 
    
逻辑运算
    与
	    and_
	    filter(and_(条件),条件…)
    
    或
    	or_
    	filter(or_(条件),条件…)
    
    非
    	not_
    	filter(not_(条件),条件…)
 
例子：
and_  
    students = Student.query.filter(Student.s_age==16,
                                    Student.s_name.contains('花'))
 
    students = Student.query.filter(and_(Student.s_age==16,
                                    Student.s_name.contains('花')))
 
not_
    students = Student.query.filter(or_(Student.s_age==16,
                                    Student.s_name.contains('花')))
or_
    students = Student.query.filter(not_(Student.s_age==16),
                                    Student.s_name.contains('花'))
 
    
    
注意: 
1. fliter和filter_by的结果可遍历
2. 可以通过对其结果使用all()方法将其转换成一个列表或者first()转换成objects对象。
3. all()获得的是列表，列表没有first()方法
4. fliter和filter_by有flrst()方法，没有last方法

```
