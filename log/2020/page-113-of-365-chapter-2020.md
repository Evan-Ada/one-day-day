
#!/usr/bin/python3
### 今天是2020年4月22日 开始复习下python3.0

### Python3 基础语法
- Python中单行注释以 # 开头
- 多行注释可以用多个 # 号，还有 ''' 和 """
- 多行语句：如果语句很长，我们可以使用反斜杠(\)来实现多行语句
- python中数字有四种类型：整数int 、布尔型bool 、浮点数float 和复数complex 

### 字符串的截取

```
#!/usr/bin/python3
 
str='Runoob'
 
print(str)                 # 输出字符串
print(str[0:-1])           # 输出第一个到倒数第二个的所有字符
print(str[0])              # 输出字符串第一个字符
print(str[2:5])            # 输出从第三个开始到第五个的字符
print(str[2:])             # 输出从第三个开始后的所有字符
print(str * 2)             # 输出字符串两次
print(str + '你好')        # 连接字符串
 
print('------------------------------')
 
print('hello\nrunoob')      # 使用反斜杠(\)+n转义特殊字符
print(r'hello\nrunoob')     # 在字符串前面添加一个 r，表示原始字符串，不会发生转义
```