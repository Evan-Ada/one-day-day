

### letter-spacing来设置字与字间距_字符间距离，字体间距css样式
```
letter-spacing:10px;
letter-spacing:1px;
```
---
```
# print('Hello boy!\nWellcom  world!!') #字符串必须用引号引起来,单双引号无区别
# if 3 > 0:
#     print('yes')
#     print("ok")

# print('Are you ok?',1906) #打印多项,用逗号分隔,输出时各项间默认是空格
# print("I am fine,thinks.",1907,sep='***') #设置输出的各项间以***为分隔符

# print("ok" + '123') #字符串只能和字符串拼接用'+'号
# print('And you' + '?') #字符串不能和数字拼接

# #input()输入语句
# user = input('用户名: ')
# print('欢迎',user)
# print('欢迎 ' + user)
# print('欢迎 %s' % user)

#字符串不能做数字运算:
# user = input('username: ') #input读入的一定是字符串
# if user == "csdnak":
#     print("%s 3.8.0 (default, Oct 31 2019, 09:48:38)"%user) #%s是占位符,后面的user内容将会替代它
#     print('Wellcom !!')
#     op = input('Please options: ')
#     if op == 'bc':
#         number1 = input('Please number1: ')
#         number2 = input("Please number2: ")
#         num = int(number1) + int(number2)
#         print("= ",num)
#     elif op == 'help':
#         print('Please input bc')
#     else:
#         print('You can view "help" option')
# else:
#     print("User name error,please re-enter!")

# #变量赋值自右向左进行,将=右边表达式的计算结果赋值给左边的变量
# a = input('Please a number: ')
# print(a)
# b = int(a) + 5
# print(b)
# b += 5
# print(b)
# b -= 10
# print(b)
# b *= 2
# print(b)

##python之禅
#import this




# #运算符
# numa = input('Please number: ')
# numb = int(numa)
# num1 = numb / 2
# print(num1)
# num2 = numb // 2 #只保留商
# print(num2)
# num3 = numb % 3 #求余/模运算
# print(num3)
# divmod(numb,2) #numb除以２,返回商和余数
# a , b = divmod(numb,2) #将商和余数分别赋值给a和b
# 2 ** 3 #2的三次方,幂运算

# #比较运算符
# a = 3 #=是赋值,不是比较
# print(a)
# print(3 == 3) #==比较必须用==表示判断是否相等
# print(10 > 5 > 1) #python支持连续比较
# print(10 > 5 < 30) #相当于20 > 5 and 5 < 30(不推荐,因为可读性差)

# #逻辑运算符,最终结果为True或False(从左到右匹即停止)
# print(10 > 50 and 2 < 5)
# print(10 > 5 and 2 < 5) # and 两边全为True,最终才是True
# print(10 > 50 or 2 < 5) #or两边只要一边为True就是True
# print(2 * 3 ** 2)
# print(2 * (3 ** 2))
# print(not 10 > 50 or 2 < 5) #涉及到可读性差的代码应该加(),让他人和程序可读性增加
# print((not 10 > 50) or 2 < 5)
# print(10 > 3)
# print(not 10 > 3) # not是取反,真变假,假变真

#type判断数据类型
# print(type(1.3))
# print(type('sda'))
# #True和False值福别是1和0
# print(True + 1)
# print(False * 5)

# #python默认使用10进制数表示数字
# #如果以0o/0O开头,表示8进制
# print(0o11)
# print(oct(9)) #将10进制数转为8进制数
# #16进制数以0x开头
# print(0x11)
# print(hex(17)) #10进制转换16进制
# #2进制数以０b开头
# print(0b11)
# print(bin(3)) #将10进制转换为二进制

# #字符串:让每个单词占一行
# test = "hello\nwelcome\ngreet" #\n换行符号
# print(test)
# test2 = """hello
# welcome
# greet""" #"""保留原有格式
# print(test2)
# test3 = """1    2   3"""
# print(test3)

#截取字符串
#从左向右从0开始,从右向左-1开始
# py_str = 'python'
# print(len(py_str)) #计算字符长度
# print(py_str[0])   #截取从左向右第一个字符
# print(py_str[-1])  #截取从右向左第一个字符
# print(py_str[2:4]) #截取切片,起始下标包含,结束下标不包含
# print(py_str[2:])  #从下标为2取到结束
# print(py_str[2:60]) #从下标为2取到60,即使真实长度不到60也可以(不会报错)
# print(py_str[:]) #从头取到未
# print(py_str)   #输出变量值
# print(py_str[::2]) #切片默认步长值为1,改为2
# print(py_str[1::2]) #从下标1开始取步数为2的字符
# print(py_str[::-1]) #反向输出
# print(py_str + 'good') #拼接
# print('*' * 30) #　*号重复30遍
# print(py_str*5) #pyhton重复5遍

# #判断成员是否在字符串中
# print('t' in py_str) # t在字符串里么?(如果在返回True否则False)
# print('th' in py_str) # th在字符串里么?
# print('to'in py_str) # to在字符串里么?
# print('to'not in py_str) # to结果取反

# #列表,与字符串类似,都是序列对象
# alist = [1, 2, 3, 'tom', 'jerry']
# print(len(alist))
# print(alist[0])
# print(alist[3:])
# print(3 in alist)
# print('o' in alist)
# print(alist + [10,20])
# print(alist * 2)
# print(alist.append('bob')) #向列表尾部追加一个字符串
# print(alist)

# #元组:可以认为他是不可变的列表
# atup = (1,2,3,'bob','tom')
# print(len(atup))
# print(atup[0])
# print(atup[3:])
# alist[0] = 10 #列表可变,可以把元素重新赋值
# print(alist)
# atup[0] = 10 #元组不可变,所以不能把它的元素重新赋值(会报错)

# #字典: 采用的是key:value的形式
# adict = {'name': 'tom','age': 20}
# print(len(adict))
# print(adict[0]) #字典是无序的,所以没有下标(会报错)
# print('tom' in adict) #tom是字典的key嚒?
# print(adict['name']) #通过key来找到value

# # 数据类型的特点
# alist = [1,2,3,'zsx','gzl']
# blist = alist
# print(blist)
# blist.append('ak')
# print(blist)
# print(alist) #如此赋值表现alist,blist指向同一个表
# blist = alist[:]
# print(blist)
# blist.append('ak')
# print(blist,"\n",alist) #通过从新创建个容易来装alist表值解决指向同一个表的问题
```
