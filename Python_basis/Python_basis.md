## 第一章 基础

### Python基础

#### 数据类型

##### 数字

> **类型转换**

```python
int(),bin(),oct(),hex()

int(string,para)第二个参数可以指定字符串所表示数字的进制

进制转换前后输出的前缀：
bin : 0b
hex : 0x
用切片不带前缀输出
```

> **运算**

除法运算：

<img src="https://raw.githubusercontent.com/ZhangYiwei-SZU/Pic/main/1715570519353.jpg" alt="1715570519353" style="zoom:50%;" />

多重赋值：

<img src="https://raw.githubusercontent.com/ZhangYiwei-SZU/Pic/main/1715570580992.jpg" alt="1715570580992" style="zoom:50%;" />

##### 字符串

> **支持切片**

> **引号**
>
> 单引号 **'** 和双引号 **"** 在大多数情况下是等效的，都用于表示字符串。你可以根据个人偏好选择使用其中的一种

> **方法(函数)**

```python
- 单个字符
  - 字符转ASCII函数：ord（ordinal）
  - ASCII转字符函数：chr（character）
- 字符串查找和替换
  - find(self,start,end) index(self,start,end) 作用：返回第一次出现的位置
  - replace(old,new,count) 参数：count指定替换次数
- 大小写转换
  - upper():将字符串大写 
    captialize():字符串的第一个字母大写，其他字母小写
    title():单词的首个字母大写
- 字符串分割和连接
  - split(separator,count):分隔符划分子串,返回列表 join(iterable):将可迭代对象中的字符串连接起来，返回字符串
- 字符串去除字符（默认为空白）
  - strip(chars)：去除字符串开头和结尾的指定字符（默认为空白字符）
- 字符串检查
  - isalpha()：检查字符串是否只包含字母字符。
  isdigit()：检查字符串是否只包含数字字符。
  isalnum()：检查字符串是否只包含字母和数字字符。 
  isupper():检查字符串中的所有字符是否都是大写字母 
  islower():检查字符串中的所有字符是否都是小写字母
```

##### 列表

> **列表推导式**
>
> [expression for item in iterable]

> **列表和迭代器的区别**
>
> <img src="https://raw.githubusercontent.com/ZhangYiwei-SZU/Pic/main/1715570904373.jpg" alt="1715570904373" style="zoom:50%;" align = "left"/>

> **列表解包**

```python
num = [1,2]
n1,n2 = num

n1, n2 = num 将列表 num 中的第一个元素 1 赋值给变量 n1，将列表 num 中的第二个元素 2 赋值给变量 n2。
```

> **列表传递给函数**
>
> 在Python中，列表是可变对象，这意味着当列表作为参数传递给函数时，函数内部对列表的修改会影响原始列表

> **方法**

```python
- append(element)  # 在列表末尾添加一个元素。参数 element 是要添加到列表的元素
- extend(iterable) # 将可迭代对象中的元素逐个添加到列表末尾。参数 iterable 是一个可迭代对象，如列表、元组或字符串
- insert(index, element) # 在指定位置插入一个元素。参数 index 是要插入元素的位置（索引），element 是要插入的元素
- remove(element) # 从列表中移除第一个匹配的指定元素。参数 element 是要移除的元素
- pop(index=-1) # 移除并返回指定位置的元素。参数 index 是要移除的元素的索引，默认为 -1，表示移除列表的最后一个元素
- index(element, start=0, end=len(list)) # 返回列表中第一个匹配的指定元素的索引。参数 element 是要查找的元素，start 和 end 是可选参数，用于指定搜索的起始位置和结束位置
- sorted(list,key,reverse) # 对列表进行排序，key表示排序的关键字，reverse表示降序排序
  - key参数
    - 在Python中，元组是一种有序的、不可变的数据类型，可以包含多个元素。当使用元组作为排序的关键字时，Python会按照元组中元素的顺序依次比较。如果第一个元素相等，则比较第二个元素，依此类推。这种方式称为元组排序
    - 元组排序 样例：key = lambda x:(x[0],x[1])
  - 排序规则：字典序
- count(element) # 返回列表中指定元素出现的次数。参数 element 是要计数的元素
- reverse() # 反转列表中的元素顺序
```

##### 元组

> 类似于列表，但是元组是不可变的，意味着一旦创建，就不能修改其内容。元组可以包含任意数量的元素，且元素可以是不同的数据类型。

##### 集合

> **无序且元素唯一的数据类型**

> **方法**

```python
方法
	set()                                # 创建一个空的集合。
	add(elem)                            # 向集合中添加元素 elem。
	remove(elem)                         # 从集合中移除元素 elem，如果元素不存在会引发 KeyError 错误。
	discard(elem)                        # 从集合中移除元素 elem，如果元素不存在不会引发错误。
	pop()                                # 随机移除并返回集合中的一个元素。
	clear()                              # 清空集合中的所有元素。
	copy()                               # 返回集合的副本。
	union(other_set) 或 |                # 返回两个集合的并集。
	intersection(other_set) 或 &         # 返回两个集合的交集。
	difference(other_set) 或 -           #  返回两个集合的差集。
	symmetric_difference(other_set) 或 ^ # 返回两个集合的对称差集。
	issubset(other_set) 或 <=            # 检查集合是否为另一个集合的子集。
	issuperset(other_set) 或 >=          # 检查集合是否为另一个集合的超集。
	isdisjoint(other_set)                # 检查两个集合是否没有交集。
```

##### 字典

> **字典推导式**
>
> {key_expression: value_expression for item in iterable}
> alpha = {chr(i):0 for i in range(ord('A'), ord('Z') + 1) } ：生成值为0的字母表

> **方法**

```python
- fromkeys(iterable, value=None)
  - 参数： iterable：可迭代对象，用作字典的键。 
  value：可选参数且位置参数，指定字典中所有键对应的初始值，默认为 None。 
  功能：创建一个新字典，使用 iterable 中的元素作为键，如果提供了 value 参数，则所有键的初始值都为 value。
- len(d) # 返回字典中键值对的数量。
- d[key] # 返回键对应的值，如果键不存在，会引发 KeyError 异常。
- d[key] = value # 将指定键的值设为指定值，如果键不存在，会添加新的键值对。
- del d[key] # 删除指定键值对。
- key in d # 检查指定键是否在字典中，返回 True 或 False。
- key not in d # 检查指定键是否不在字典中，返回 True 或 False。
- d.keys() # 返回一个包含字典所有键的视图。
- d.values() # 返回一个包含字典所有值的视图。
- d.items() # 返回一个包含所有键值对的列表，每个键值对以元组形式返回。
- d.pop(key, default=None) # 删除指定键的键值对，并返回其值，如果键不存在，则返回默认值。
- d.popitem() # 随机删除并返回一个字典的键值对。
- d.clear() # 清空字典，移除所有的键值对。
```

#### 面向过程

##### 函数

> 功能函数

```python
#输出函数
print
#映射函数 返回可迭代对象 注意返回的不是列表
map(function, iterable) 
#匿名函数
lambda
#example : 
lambda x,y:x+y 等价于
def(x,y):      
return x+y
#最大值函数：用于返回给定可迭代对象中的最大值
max()
#最小值函数：返回给定可迭代对象中的最小值
min()
#求和函数：返回给定可迭代对象中所有元素的总和
sum()
- 表达式解析函数：eval()
  - eval() 是一个内置函数，用于执行存储在字符串中的表达式或代码，并返回结果。它可以将字符串中的有效Python表达式作为输入，并将其解析和执行为实际的Python对象或执行语句。 将一个包含数字的字符串传递给 eval()，它将返回一个数字（整数或浮点数）
  - eval() 函数在字符串时会将其解释为进制数字转换为十进制整数
```

> 递归
>
> - 核心：大问题分解为小问题          
>
>   ​		  判断小问题的返回结果
>
> - 分析和代码
>
>   - 设定结束条件
>   - 正确接收返回值

> if 语句
>
> if语句中可以添加多个and或者or：
> if condition1 and condition2 and condition3
>
> `if __name__ == "__main__"`
>
>
> 使用 if __name__ == "__main__": 条件语句。直接运行脚本时，__name__ 的值会被设置为 "__main__"，因此测试代码会被执行。而当我们将该脚本作为模块导入时，__name__ 的值会是模块的名称，因此测试代码不会被执行。
>
> 这种做法有助于保持代码的整洁性和可维护性，使得我们可以在开发过程中方便地进行测试和调试，而不会影响其他模块的正常使用。
>
> `is 和 ==`
>
> - is 运算符用于比较两个对象的身份，即检查两个对象是否是同一个对象。具体来说，is 判断的是对象的内存地址是否相同，即两个对象是否在内存中存储的是同一块内存空间。 相反逻辑用is not
> - == 运算符用于比较两个对象的值，即检查两个对象是否具有相同的值。具体来说，== 判断的是对象的值是否相等，而不关心对象的内存地址。 相反逻辑用 !=

> for 语句
>
> - 通过range()函数生成数值序列进行遍历
>   - \- for i in range(5) - for i in range(0:10) - for i in range(10:0:-1)
> - 遍历列表、元组、集合等可迭代对象
>   - for item in my_list
> - 遍历字典的键
>   - for key in my_dict:
>   - 默认遍历字典的key
> - 遍历字典的键值对
>   - for key, value in my_dict.items()

#### 输入输出

**输入**

>**input()**
>
>- 使用方法：var = input("string") #string以提示符的方式显示在终端
>
>- 注意：input()函数返回的是一个字符串，经常需要类型转换= input("string") num = int(input("string"))

> **sys.stdin**
>
> - 优点： 在ACM比赛中，应该尽量避免使用input()函数读取大量输入，而应该考虑使用更快速的方法，如sys.stdin.readline()
>
> - 常用技巧：一行输入包含多个变量，用split()方法将其拆分为单独的变量，再转换为需要的格式

**输出**

> **格式化输出**
>
> - %输出
>   - 和C语言类似的语法
> - F字符串
>   - 小数点位数
>     - print(f"{num:.2f}") 
>   - 宽度
>     - (f"{string:10}") 
>   - 填充
>     - f"{text:*<10}"   
>       - 右侧填充*,默认填充0
>       - < 表示文本左对齐 
>       - 10 表示宽度 
>
> **快速输出多个变量**
>
> - 用逗号隔开
>
> **写入文件**
>
> - with open("test.txt",'w') as f:    f.write("this is a test") #已可写的方式打开文件

## 第二章 入门经典

### 简单模拟

 **1091促销计算**

```python
# import sys
# price = int(sys.stdin.readline().split()[0])
price = int(input())
if price >= 5000:
        discount_rate = 0.8
elif price >= 3000:
        discount_rate = 0.85
elif price >= 2000:
        discount_rate = 0.9
elif price >= 1000:
        discount_rate = 0.95
else:
        discount_rate = 1

pay = price * discount_rate


print(f"discount={discount_rate}" + ",pay=%g" % pay)
https://noobdream.com/DreamJudge/Issue/page/1091/
```

 **[1133求1到n的和](https://noobdream.com/DreamJudge/Issue/page/1133/#)**

```python
import sys
num = int(sys.stdin.readline().split()[0])
sum = 0
for i in range(num + 1):
        sum += i
print(sum)
```

> 1

```python
1
```



 **[1043 计算Sn](https://noobdream.com/DreamJudge/Issue/page/1043/)**

```python
import sys
input = sys.stdin.readline().split()
sum = 0
temp = 0
num = int(input[0])
count = int(input[1])
for i in range(count):
        temp += num
        num = num * 10
        sum += temp
print(sum)
```

### 进制转换

> 常用函数
>
> - 十进制转其他进制
>
>   - bin()、oct()和hex()函数将十进制数转换为二进制、八进制和十六进制字符串
>
> - 其他进制转十进制
>
>   - 使用int()函数将其他进制的字符串转换为十进制数。需要指定字符串以及其对应的进制数。

 **[1454反序数](https://noobdream.com/DreamJudge/Issue/page/1454/)**

```python
for n in range(1000, 10000):
    reversed_n = int(str(n)[::-1])  # 获取n的反序数
    if n * 9 == reversed_n:
        print(n)

错误代码：
count = 9999
reverse = ""
for i in range(count):
temp = str(i * 9)
for i in temp[::-1]:
    reverse += i
r = int(reverse +  "   ")
if r == temp:
    print(r)


# 范围错误：四位数是1000~10000

# reverse应该在循环内部而不是外部

# r和temp的类型错误，不能用==判断 
```

> 切片步长为负一时
>
>   在切片操作 [start:stop:step] 中，如果 step 参数为负数，则表示从右向左取元素。因此，在 my_list[::-1] 中，step 参数为 -1，表示从右向左取元素。
>
>
>  当 step 参数为负数时，起始索引（start）默认为列表末尾，结束索引（stop）默认为列表开头。因此，my_list[::-1] 实际上是从列表末尾开始，到列表开头结束的切片操作，即逆序输出整个列表。

**[1259十六转十进制](https://noobdream.com/DreamJudge/Issue/page/1259/)**

```python
while True:
    try:
        num = input()
        num = int(num, 16)
        print(num)
    except:
        break
```



### 排版类问题

**[1473 字符菱形](https://noobdream.com/DreamJudge/Issue/page/1473/#)**

```python
n = int(input())

for i in range(1,n + 1):
    print(" " * (n-i) + "*" *(2 * i - 1) )

for i in range(n - 1,0,-1):
    print(" " * (n-i) + "*" *(2 * i - 1) )


# 注意：
#  for循环的细节：

# for i in range(1,n + 1):是从1,2....n-1,n
# for i in range(n - 1,0,-1):是从n-1,n-2....,1
```

**[1062 杨辉三角](https://noobdream.com/DreamJudge/Issue/page/1062/)**

```python
import sys
n = int(input())
if n == 0:
    sys.exit()
triangle = [[1]]
for i in range(1, n):
    row = [1]
    for j in range(1, i):#第0和n位置默认填1
        row.append(triangle[i-1][j-1] + triangle[i-1][j])#中间有i-2个位置需要填数字，数字是i-1的j-1位置和i-1行的j位置之和
    row.append(1)
    triangle.append(row)
for list in triangle:
    for n in list:
        print(str(n),end = " ") 
```

### 日期类问题

**1051 日期计算**

```python
垃圾代码

long_month =  [1,3,5,7,8,10,12]
medium_month = [4,6,9,11]

while(True):
    run_year = False
    ans = 0
    try:
        year, month, day = map(int, (input().split(" ")))
        if(year % 4 == 0 and year % 100 !=0) or year % 400 == 0:#判断闰年
            run_year = True
        for i in range(1,month + 1):
            i -= 1
            if i in long_month:
                ans += 31
            elif i in medium_month:
                if day > 30:
                    print("Input error!")
                    continue
                ans += 30
            elif run_year and i == 2:
                if day > 29:
                    print("Input error!")
                    continue
                ans += 29
            elif run_year == False and i == 2:
                if day > 28:
                    print("Input error!")
                    continue
                ans += 28

​    ans += day
​    if month < 1 or month > 12 or day < 1 or day > 31 or year < 0:
​        print("Input error!")
​        continue
​    else:
​        print(ans)
except:
​    break
```

> 错误：
>
> 良好的编程习惯：
> if __name__ == "__main__":
>                  main()
>
> 多组输入问题需要考虑while True:
>
> year, month, day = map(int, (input().split(" ")))
> 这类输入语句应该放在while内
>
> while内错误信息输出后要加continue
>
> 代码太冗余
>

```python
# 正确代码

record = [0,31,28,31,30,31,30,31,31,30,31,30,31]
def main():
    while True:
        try:
            year,month,day = map(int,(input().split(" ")))
            if year<0 or month > 12 or month < 1 or day > record[month] or day < 1:
                print("Input error!")
                continue
            if year%400==0 or (year%4==0 and year%100!=0):
                record[2] = 29
            ans = 0
            for i in range(0,month):
                ans = ans+record[i]
            print(ans+day)
        except:
            break
if __name__ == '__main__':
    main()
```



**[1410 打印日期](https://noobdream.com/DreamJudge/Issue/page/1410/#)**

```python
record = [0,31,28,31,30,31,30,31,31,30,31,30,31]

while True:
       try:
        year, n = map(int, input().split())
        record[2] = 28
        if year%400==0 or (year%4==0 and year%100!=0):
            record[2] = 29
        for i in range(0,14):
            n = n - record[i]
            if n <= record[i + 1]:
                month = i + 1
                day = n
                print("%d-%02d-%02d" % (year,month,day))
                break
       except:
           break
```

> 错误：
>
> 良好的竞赛习惯：
> while(True):
>   try:
>
>   except:
>       break

**1437 日期加一天**

```python
record = [0,31,28,31,30,31,30,31,31,30,31,30,31]
while True:
    try:
        out = []
        m = int(input())
        for i in range(m):
            year,month,day = map(int,input().split())
            if day + 1 > record[month] and month < 12:
                month += 1
                day = 1
            elif month == 12 and day + 1 > 31:
                year += 1
                month,day = [1,1]
            else:
                 day += 1
            out.append([year,month,day])
        for j in out:
            print("%d-%02d-%02d" % (j[0],j[1],j[2]))
    except:
        break
```



> 错误
>
> - 这里应该用elif，两个if导致else只和第二个if匹配![1715649899060](https://raw.githubusercontent.com/ZhangYiwei-SZU/Pic/main/1715649899060.jpg)
> - 列表新增元素用append
>
> ![1715649949025](https://raw.githubusercontent.com/ZhangYiwei-SZU/Pic/main/1715649949025.jpg)
>
> - 格式化匹配注意符号优先级
>   % 

### 字符串类问题

**[1014AC 加密算法](https://noobdream.com/DreamJudge/Issue/page/1014/)**

```python
while True:
    try:
        str = input()
        text = ""
        for char in str:
            if char.isalpha():
                shift = 3
                if char.islower():
                    start = ord('a')
                else:
                    start = ord('A')
                letter = chr((ord(char) - start + shift) % 26 + start)
                text += letter
            else:
                text += char
        print(text)
    except:
        break
```

[**1240AC 首字母大写**](https://noobdream.com/DreamJudge/Issue/page/1240/)

```python
set = [' ','\n','\t','\r']
while True:
    try:
        all = input()
        result = ""
        for i in range(len(all)):
            if (all[i].isalpha() and all[i-1] in set) or i == 0:
                result += all[i].upper()
            else:
                result += all[i]
        print(result)
    except:
        break
```

**[1394 统计单词](https://noobdream.com/DreamJudge/Issue/page/1394/)**

```python
while True:
    try:
        string = input().replace(".","").split()
        for s in string:
            count = 0
            for char in s:
                if char.isalpha():
                    count += 1
            print(count,end = " ")
        print()
    except:
        break
```

> 错误
>
> - 在 Python 中，字符串是不可变的（immutable），意味着你不能直接修改字符串中的某个字符。因此，代码中的尝试 all[i] = all[i].upper() 会引发错误。 如果你想要将字符串中的某些字母大写，可以使用字符串的切片操作和字符串的拼接来实现。
> - 变量的名字不要和内置函数重名，当str = input()时，str函数不可用
> - 统计长度通常用len即可，不需要用循环遍历元素再累加

### 排序类问题

**[1151 成绩排序](https://noobdream.com/DreamJudge/Issue/page/1151/)**

```python
#正确代码

while True:
    try:
        count = int(input())
        method = int(input())
        info = []
        for i in range(count):
            name, score = input().split()
            info.append((name,score))
        sort_info = sorted(info,key = lambda x:x[1],reverse= method==0)
        for name,score in sort_info:
            print(name,score)

except:
    break





#错误代码

while True:
    try:
        count = int(input())
        method = int(input())
        dict = {}
        for i in range(count):
            name,score = input().split()
            dict[score] = name
        s_list = sorted(list(dict.keys())) #keys返回字典视图，list转化为列表,默认升序
        #sort() 方法会原地排序列表，并且返回值为 None，而不是排序后的列表 这里用sorted更好理解代码
        if method == 1:
            for score in s_list:
                print(f"{dict[score]} {score}")
        else:
            jiangxu = s_list[::-1]
            for score in jiangxu:
                print(f"{dict[score]} {score}")
    except:
        break

# 用字典存入成绩未考虑到成绩相同的情况
```

**[1010 奇偶排序](https://noobdream.com/DreamJudge/Issue/page/1010/)**

```python
while True:
    try:
        n = int(input())
        numbers = input().split()
        if n != len(numbers) or n == 0:
            break
        sorted_numbers = sorted(map(int,numbers))
        odd = []
        even = []
        for num in sorted_numbers:
            if num % 2 == 0:
                even.append(num)
            else:
                odd.append(num)
        nums = odd + even
        print(" ".join(map(str, nums)))
    except:
        break
```

> 错误 简单逻辑出错
>
> - %2=0就是偶，不然就是奇数

**[1159 排序2(classic)](https://noobdream.com/DreamJudge/Issue/page/1159/)**

```python
#用列表保存信息

while True:
    try:
        info = []
        count = int(input())
        if count == 0:
            break
        for i in range(count):
            hao,score = map(int,input().split())
            info.append([hao,score])
       	pre_info = sorted(info,key = lambda x:x[0])
        sorted_info = sorted(pre_info,key = lambda x:x[1])
        #sorted_info = sorted(info, key=lambda x: (x[1], x[0]))  #接收列表，返回元组 先按成绩排序，如果成绩相同再按学号排序
        for data in sorted_info:
            print(data[0],data[1])
    except:
        break

#用字典保存信息并排序(items)

while True:
    try:
        count = int(input())
        d = dict()
        if count == 0:
            break
        for i in range(count):#保持所有学生信息
            hao,score = map(eval,input().split())
            d[hao] = score
        sorted_d = sorted(d.items(),key = lambda x:(x[1],x[0]))
        for key,value in sorted_d:
            print(key,value)
    except:
        break
```



> 错误
>
> - 如果要使用sorted函数对列表中的数字排序，保证列表元素是数字类型，而不是字符串类型
>   字符串类型会根据字典序判断大小
>
> 多轮排序：lambda
>
> sorted(info,key=lambda x: (x[1], x[0])
> 的作用：返回一个元组 (x[1], x[0])，先按x[1]排序，再按x[0]排序

**[1217 国名排序](https://noobdream.com/DreamJudge/Issue/page/1217/)**

```python
while True:
    try:
        n = int(input())
        country = []
        for i in range(n):
            country.append(input())
        sorted_country = sorted(country)
        for c in sorted_country:
            print(c)
    except:
        break
```

**[1255 字符串排序2](https://noobdream.com/DreamJudge/Issue/page/1255/)**

```python
while True:
    try:
        sentence = input()
        letters = ""
        for char in sentence:
            if char.isalpha():
                letters += char
        sort_letters = sorted(letters,key = lambda x:x.lower())
        result = ""
        for c in sentence:
            if c.isalpha():
                result += sort_letters.pop(0)
            else:
                result += c
        print(result)
    except:
        break
```



> 关键：
>
> - sorted函数key参数的使用
>   整体抽取部分，部分再拼回整体的思想
>   开辟新空间
>
> - for循环里面的两个input不是同一个变量
>   对于input的作用要熟悉
>
> ![1715667468080](https://raw.githubusercontent.com/113737038537/Pic/main/undefined1715667468080.jpg)

**[1261 字符串排序3](https://noobdream.com/DreamJudge/Issue/page/1261/)**

```python
while True:
    try:
        string = []
        n = int(input())
        for i in range(n):
            sentence = input()
            if sentence == "stop":
                break
            else:
                string.append(sentence)
        sorted_string = sorted(string,key = lambda x:len(x))
        for s in sorted_string:
            print(s)
    except:
       break
```

**[1294 后缀字符串](https://noobdream.com/DreamJudge/Issue/page/1294/)**

```python
while True:
    try:
        string = input()
        sub_string = []
        for i in range(len(string)):
            sub_string.append(string[i:])
        sorted_string = sorted(sub_string)
        for s in sorted_string:
            print(str(s))
    except:
        break
# 关键：切片的运用
```

**[1338 Excel排序](https://noobdream.com/DreamJudge/Issue/page/1338/)**

```python
while True:
    try:
        num,column = map(int,input().split())
        if num == 0:
            break
        all = []
        for i in range(num):
            info = input().split()
            all.append(info)
        print("Case:")
        if column == 1:
            sorted_xuehao = sorted(all,key = lambda x:x[0])
            for s in sorted_xuehao:
                print(s[0],s[1],s[2])
        elif column == 2:
            sorted_name = sorted(all,key = lambda x: (x[1],x[0]))
            for s in sorted_name:
                print(s[0], s[1], s[2])
        elif column == 3:
            sorted_score = sorted(all, key=lambda x: (int(x[2]),x[0]))
            for s in sorted_score:
                print(s[0], s[1], s[2])
    except:
        break
```

> 错误
>
> - 解包操作符可以作用于迭代器对象
>
> <img src="https://raw.githubusercontent.com/ZhangYiwei-SZU/Pic/main/1715667642751(1).jpg" alt="1715667642751(1)" style="zoom:50%;" align = "left"/>
>
> - 字典序
>
> - 元组排序
>
> <img src="https://raw.githubusercontent.com/ZhangYiwei-SZU/Pic/main/1715667687902.jpg" alt="1715667687902" style="zoom:50%;" />

**[1360 字符串内排序](https://noobdream.com/DreamJudge/Issue/page/1360/)**	

```python
while True:
    try:
        string = input()
        sorted_string = sorted(string)
        print("".join(sorted_string))
    except:
        break
```



**[1399AC 排序 - 华科](https://noobdream.com/DreamJudge/Issue/page/1399/)**

```python
while True:
    try:
        n = int(input())
        numbers = input().split()
        sorted_nums = sorted(numbers,key = lambda x:int(x))
        text = " ".join(sorted_nums)
        print(text)
    except:
       break
```

> 改进
>
> -  不需要map来转换为int再sorted
>    直接在sorted中指定可迭代对象和key
>    sorted返回列表

[1400AC 特殊排序](https://noobdream.com/DreamJudge/Issue/page/1400/)

```python
while True:
    try:
        n = int(input())
        numbers = input().split()
        sorted_nums = sorted(numbers,key = lambda x:int(x))
        max = sorted_nums.pop(-1)
        print(max)
        if sorted_nums == []:
            print(-1)
        else:
            text = " ".join(sorted_nums)
            print(text)
    except:
       break
```

**[1412 大数排序](https://noobdream.com/DreamJudge/Issue/page/1412/)**

- Python没有大整数

### 查找类问题

**[1476AC 查找学生信息2](https://noobdream.com/DreamJudge/Issue/page/1476/)**	

```python
while True:
    try:
        dict = {}
        n = int(input())
        for i in range(n):
            line = input().split()
            num = line[0]
            info = " ".join(line[1:])
            dict[num] = info
        all_xuehao = []
        m = int(input())
        for i in range(m):
            xuehao = input()
            all_xuehao.append(xuehao)
        for xuehao in all_xuehao:
            try:
                print(xuehao,dict[xuehao])
            except KeyError:
                print("No Answer!")

except:
    break
```



> 错误
>
> - 没考虑到No answer的特殊情况
>
> 思路：字典

**[1477AC 动态查找问题](https://noobdream.com/DreamJudge/Issue/page/1477/)**

```python
while True:
    try:
        n = int(input())
        nums = input().split()
        q= int(input())
        for i in range(q):
            x = input()
            if x in nums:
                print("find")
            else:
                print('no')
                nums.append(x)
    except EOFError:
        break
```

**[1177AC 查找潜在朋友](https://noobdream.com/DreamJudge/Issue/page/1177/)**

```python
while True:
        try:
            dict = {}
            n,m = map(int,input().split())
            for i in range(n):
                p = int(input())
                dict[i] = p
            books = list(dict.values())
    

​        friends = {}
​        for key in dict.keys():
​                friends[key] = books.count(dict[key]) - 1
​                if friends[key] != 0:
​                    print(friends[key])
​                else:
​                    print("BeiJu")
​    except:
​        break
```

**[1388AC 查找1](https://noobdream.com/DreamJudge/Issue/page/1388/)**

```python
while True:
    try:
        n = input()
        nums = input().split()
        m = input()
        search = input().split()
        for char in search:
            if char in nums:
                print("YES")
            else:
                print("NO")
    except:
        break
```

**[1387AC 查找-北邮](https://noobdream.com/DreamJudge/Issue/page/1387/)**

```python
def reverse_string(string,order):
    index = int(order[1])
    len = int(order[2])
    str = string[index:index + len]
    if index == 0:
        reverse_str = str[::-1] + string[(index + len):]
    else:
        reverse_str = string[0:index] + str[::-1] + string[(index + len):]
    return reverse_str
def replace_string(string,r):
    index = int(order[1])
    len = int(order[2])
    need_r_string = string[index:index + len]
    replace_str = string.replace(need_r_string,r,1)
    return replace_str
while True:
    try:
        text = []
        string = input()
        n = int(input())
        for i in range(n):
            order = input()
            if order[0] == '0':
                string = reverse_string(string,order)
                text.append(string)
            else:
                r = order[3:]
                string = replace_string(string,r)
                text.append(string)
        for t in text:
            print(t)
    except:
        break
```

**[1383AC 查找第k小的数](https://noobdream.com/DreamJudge/Issue/page/1383/)**

```
while True:
    try:
        n = int(input())
        nums = list(set(input().split()))
        k = int(input())
        sorted_nums = sorted(nums,key = lambda x:int(x))
        print(sorted_nums[k-1])
    except:
        break


```

> -  切片需要注意string[0:index] 到index截止，不包括index 
> -  注意不同type之间用==比较必然返回False

### 贪心类问题

> 1、建立数学模型来描述问题
> 2、把求解的问题分成若干个子问题
> 3、对每一子问题求解，得到子问题的局部最优解；
> 4、把子问题的局部最优解合成原来问题的一个解。

解题思路：往往需要先按照某个特性先排好序，也就是说贪心一般和sort一起使用。

**[1478RE 喝饮料](https://noobdream.com/DreamJudge/Issue/page/1478/#)**

```python
while True:
    try:
        money,n = map(int,input().split())
        if money == -1 and n == -1:
            exit()
        saverge = []
        for i in range(n):
            ml,price = map(int,input().split())
            saverge.append([ml,price])
        sorted_saverge = sorted(saverge,key = lambda x:x[1] / x[0],reverse=True)
        total = 0
        for s in sorted_saverge:
            if money - s[1] >= 0:
                money = money - s[1]
                total = total + s[0]
            else:
                totol = total +  (s[1] * (money / s[0]))
                break
        print(f"{total:.3f}")
    except:
        break
```

**1347 To fill or Not to fill**
（浙大）

```python
import collections
MaxPrice = 10**12  # 设最大油价

用于抽象加油站的信息

PetrolStation = collections.namedtuple('PetrolStation', ['price', 'distance'])
def getNextOptimalStationID(PetrolStationsList, current_station_idx, distance_tank, N):
    currentStation  = PetrolStationsList[current_station_idx]
    # maxRange 表示当前加油站加满之后可以最远到达的位置
    maxRange = currentStation.distance + distance_tank
    idx = current_station_idx + 1  ##########
    minPrice = MaxPrice  ############
    minPrice_idx = current_station_idx + 1  ############
    while idx <= N and PetrolStationsList[idx].distance <= maxRange:
        if PetrolStationsList[idx].price <= currentStation.price:
            return idx # 优先选择行程范围内最近的价格低于当前加油站的下一个加油站
        elif PetrolStationsList[idx].price < minPrice:
            minPrice_idx = idx
            minPrice = PetrolStationsList[idx].price
        idx += 1
    if idx == current_station_idx + 1:
        return -1  # 表示达不到下一加油站
    else:
        return minPrice_idx

def main():
    # 油箱容量, 总距离, 公里每升, 加油站总数
    Cmax, D, Davg, N = map(eval, input().strip().split())
    PetrolStationsList = list()  # 列表类型,用于保存N个加油站

stationsDict = dict()
for i in range(N):
    price, distance = map(eval, input().strip().split())  # 每个加油站的价格和到起点的距离
    if distance in stationsDict:
        if price < stationsDict[distance]:
            stationsDict[distance] = price
    else:
        stationsDict[distance] = price
N = len(stationsDict)
for distance, price in stationsDict.items():
    PetrolStationsList.append(PetrolStation(price,distance))  # 添加到列表
PetrolStationsList.append(PetrolStation(MaxPrice, D))  # 终点也视作是一个加油站
PetrolStationsList.sort(key=lambda x:x.distance)  # 加油站按从近到远排列
distance_tank = Cmax * Davg  # 一整箱油加满后可以行驶的距离
current_station_idx = 0  # 当前所在加油站
cost, petrolRst = 0.0, 0.0  # 当前累计消费, 当前油箱剩余油量
if PetrolStationsList[0].distance > 0.0:  # 表示起点处没有加油站,汽车无法启动,停在起点
    print("The maximum travel distance = {0:.2f}".format(0.0))
    return
while current_station_idx < N:
    nextOptimal_idx = getNextOptimalStationID(PetrolStationsList, current_station_idx, distance_tank, N)
    if nextOptimal_idx == -1:  # 表示无法到达下一个加油站(或者终点)
        print("The maximum travel distance = {0:.2f}".format(
            PetrolStationsList[current_station_idx].distance + distance_tank))
        return
    elif nextOptimal_idx == N:  # 表示下一站直接到终点
        currentStation = PetrolStationsList[current_station_idx]
        cost = cost + \
            ((D - currentStation.distance)/Davg - petrolRst) * currentStation.price
        print("{0:.2f}".format(cost))
        return
    else:
        currentStation = PetrolStationsList[current_station_idx]
        nextStation = PetrolStationsList[nextOptimal_idx]
        need_petrol = (nextStation.distance-currentStation.distance)/Davg  # 开到下一站消耗的油量
        #######################################################
        if currentStation.price > nextStation.price:  # 下一站更便宜
            if need_petrol > petrolRst:  # 油箱余量不够,需要加油
                cost = cost + (((nextStation.distance-currentStation.distance)/Davg-petrolRst)*currentStation.price)
                petrolRst = 0.0
            else:  # 油箱余量充足,不需要加油
                petrolRst = petrolRst - need_petrol
        else:  # 当前站更便宜
            if currentStation.distance + distance_tank >= D:
                cost = cost + (D - currentStation.distance) / Davg * currentStation.price
                print("{0:.2f}".format(cost))
                return
            cost += (Cmax-petrolRst)*currentStation.price
            petrolRst = Cmax - need_petrol
        current_station_idx = nextOptimal_idx

if __name__ == "__main__":
    try:
        while True:
            main()
    except:
        pass
```

## 第三章 数学


## 第五章 数据结构

### 栈的应用

**[括号匹配](https://noobdream.com/DreamJudge/Issue/page/1501/#)**

```python
  while True:
      try:
          string = input()
          stack = list()
          for char in string:
              if len(stack) != 0:
                  now = stack[-1]
                  if (char == ')' and now == '(') or (char == ']' and now == '['):
                      stack.pop()
                  else:
                      stack.append(char)
              else:
                  stack.append(char)
          if len(stack) == 0:
              print("YES")
          else:
              print("NO")
      except:
          break
```

**[1067 优先级括号匹配](https://noobdream.com/DreamJudge/Issue/page/1067/#)**

```python
while True:
    try:
        priority = {"{":4,"[":3,"(":2,"<":1}
        n = eval(input())
        if n == 0:
            break
        text = list()
        for i in range(n):
            stack = list()
            string = list(input())
            for char in string:
                if len(stack) != 0:
                    now = stack[-1]
                    if char == '<' or char == '(' or char == '[' or char == '{':# 若是左括号就进行优先级判断,当优先级大于栈顶元素才入栈，终止循环;否则入栈
                        if priority[char] > priority[now]:
                            break
                        else:
                            stack.append(char)
                    elif (char == '}' and now == '{') or (char == ']' and now == '[') or (char == ')' and now == '(') or (char == '>' and now == '<'):#栈顶元素和当前元素匹配，出栈
                        stack.pop()
                    else:
                        break
                else:
                    if char == '<' or char == '(' or char == '[' or char == '{':#
                        stack.append(char)

​        if len(stack) == 0:
​            text.append("YES")
​        else:
​            text.append("NO")
​    for t in text:
​        print(t)
except:
​    break
```



>  if语句的每个条件都写出来和使用括号组合多个条件 作用一样

### 双端队列

```python
from collections import deque

append(x)：在队列的右侧添加元素 x

appendleft(x)：在队列的左侧添加元素 x。

clear()：清空队列中的所有元素

count(x)：返回队列中元素 x 的个数

pop()：移除并返回队列中的最右侧元素

popleft()：移除并返回队列中的最左侧元素
```



### 哈夫曼树

[1544 合并果子
1382 哈夫曼树](https://noobdream.com/DreamJudge/Issue/page/1544/#)

```python
import bisect
while True:
    try:
        n = eval(input())
        fruits = list(map(eval,input().split()))
        count = 0
        fruits.sort()
        while len(fruits) > 1:
            min_fruits,second_min_fruits = fruits.pop(0),fruits.pop(0)
            node = min_fruits + second_min_fruits
            bisect.insort(fruits,node)
            count += node
        print(count)
    except:
        break
```

```python
# 错误

- 每次插入都排序导致时间复杂度过高
  用bisect模块

思路：贪心
每次最小的两个值
```



### 二叉树

>  对于二叉树涉及到的递归情况，正确的思路是
> 1、用最简单的树情况，比如叶节点
> 2、分析子问题和判断递归结束的条件，再应用到复杂情况
> 而不是一上来就对总问题进行分析

~~~python
#常见方法

#前序遍历（中序、后序同理）

def preorder(root):
    if root is None:  # 递归退出条件
        return []
    result = []
    result.append(root.val)
    result.extend(_preorder(root.left))  # 用extend返回一个扁平的列表，用append会返回一个嵌套的列表，因为递归深处返回的是列表
    result.extend(_preorder(root.right))
    return result

#层次遍历

def leverorder(root):
    result = []
    deque = collections.deque()
    deque.appendleft(root)
    result.append(root.val)
    while len(deque) != 0:
        top = deque.pop()
        if top.left is not None:
            deque.appendleft(top.left)
            result.append(top.left.val)
        if top.right is not None:
            deque.appendleft(top.right)
            result.append(top.right.val)
    return result

#根节点到目标节点路径

def findpath(root,target):
    path = []

```
DFS_find_path(root,target,path)

return path
```

def DFS_find_path(node,target,path):
    if not node:
        return False

path.append(node) #列表记录路径

if node.val == target:
    return True
#在左子树中递归查找路径
if DFS_find_path(node.left,target,path):
    return True
#在右子树中递归查找路径
if DFS_find_path(node.right,target,path):
    return True
#子树中没找到，移除当前节点
path.pop()

return False



#列表传入函数后，函数体内部修改列表，外部的列表同样被修改
~~~



**1109 二叉树的建立和遍历**

```
import collections
class TreeNode:
    def __init__(self, val):
        self.val = val
        self.left = None
        self.right = None

def build_tree(preorder):
    root_val = preorder.pop(0)
    if root_val == '0':
        return None

root = TreeNode(root_val)  # 根左右
root.left = build_tree(preorder)  # 递归到叶节点结束
root.right = build_tree(preorder)

return root

def _preorder(root):
    if root is None:  # 递归退出条件
        return []
    result = []
    result.append(root.val)
    result.extend(_preorder(root.left))  # 用extend返回一个扁平的列表，用append会返回一个嵌套的列表，因为递归深处返回的是列表
    result.extend(_preorder(root.right))
    return result

def inorder(root):  # 中序：左右根
    if root is None:  # 递归退出条件
        return []
    result = []
    result.extend(inorder(root.left))  # 用extend返回一个扁平的列表，用append会返回一个嵌套的列表，因为递归深处返回的是列表
    result.append(root.val)
    result.extend(inorder(root.right))
    return result

def postorder(root):
    if root is None:  # 递归退出条件
        return []
    result = []
    result.extend(postorder(root.left))
    result.extend(postorder(root.right))
    result.append(root.val)
    return result

def leverorder(root):
    result = []
    deque = collections.deque()
    deque.appendleft(root)
    result.append(root.val)
    while len(deque) != 0:
        top = deque.pop()
        if top.left is not None:
            deque.appendleft(top.left)
            result.append(top.left.val)
        if top.right is not None:
            deque.appendleft(top.right)
            result.append(top.right.val)
    return result

def leaves_count(root):
    if root is None:
        return 0
    elif root.left is None and root.right is None:
        return 1
    left_leaves = leaves_count(root.left)
    right_leaves = leaves_count(root.right)
    return left_leaves + right_leaves

while True:
    try:
        preorder = input().split()
        if not preorder:
            break
        root = build_tree(preorder)
        reslut_pre, result_in, result_post, leaves_count = _preorder(root), inorder(root), postorder(
            root), leaves_count(root)
        print(" ".join(reslut_pre))
        print(" ".join(result_in))
        print(" ".join(result_post))
        print(leaves_count)
    except:
        break
```



> 错误
>
> 递归返回列表
>
> - 用extend接受，返回扁平列表
>
>   <img src="https://raw.githubusercontent.com/ZhangYiwei-SZU/Pic/main/1715669031425.jpg" alt="1715669031425" style="zoom:50%;" aling = "left" />
>
> - 用append接收，返回嵌套列表
>
>   <img src="https://raw.githubusercontent.com/ZhangYiwei-SZU/Pic/main/1715669085986(1).jpg" alt="1715669085986(1)" style="zoom:50%;" />
>   
>   

顺序二叉树（投机取巧）

**[1233 二叉树判断公共父节点](https://noobdream.com/DreamJudge/Issue/page/1233/)**

```python
while True:
    try:
        x,y = list(map(eval,input().split()))
        while x != y:
            if x < y:
                y = int(y / 2)
            else:
                x = int(x / 2)
        print(y)
    except:
        break
        
#正确思路

#整数类型较大者除2直到相等
```

> 错误
>
> - 找目标节点的函数错误
>   正确接收递归函数的返回值
>
> - 即便找到了目标节点，但因为没有返回所以最终目标节点没有被利用



错误代码

```python
class TreeNode:
    def __init__(self,val):
        self.val = val
        self.left = None
        self.right = None
        self.parent = None

def bulid_tree(root,last_Node,n): #当前节点和父节点
    if last_Node is None:
        root_val = 1
    elif last_Node.val * 2 > n:
        return None
    elif root is last_Node.left:
        root_val = last_Node.val * 2
    elif root is last_Node.right:
        root_val = (last_Node.val * 2) + 1
    else:
        return None
    root = TreeNode(root_val)
    root.parent = last_Node
    root.left = bulid_tree(root.left,root,n)
    root.right = bulid_tree(root.right,root,n)
    return root

def inorder_find_node(root,weight):

# if root is None:

#     return []

# elif root.val == weight:

#     return root

# result = []

# result.extend(inorder_find_node(root.left, weight))

# result.append(result.val)

# result.extend(inorder_find_node(root.right, weight))

​    if root is None: #叶子节点后的孩子直接返回None
​        return None
​    if root.val == weight:#找到目标节点
​        return root
​    left = inorder_find_node(root.left,weight)#接收左孩子的返回值
​    if left:#找到目标节点
​        return left#返回给上层函数
​    right = inorder_find_node(root.right,weight)#接收右孩子返回值
​    if right:
​        return right
​    return None#子树中没有目标节点，返回None

def find_path(node):
    result = []
    while node.parent:
        result.append(node.parent.val)
        node = node.parent
    return result

while True:
    try:
        x,y = list(map(int,input().split()))
        root = bulid_tree(None,None,max(x,y))
        x_node = inorder_find_node(root,x)
        y_node = inorder_find_node(root,y)
        x_path = find_path(x_node)
        y_path = find_path(y_node)
        intersection = set(x_path) & set(y_path)
        print(max(intersection))
    except:
        break
```

**[1401 前序中序确定二叉树](https://noobdream.com/DreamJudge/Issue/page/1401/#)**

```python
class TreeNode:
    def __init__(self,val):
        self.val = val
        self.left = None
        self.right = None

def BuildTree(preorder,inorder):
    if not preorder or not inorder:
        return None
    root_val = preorder[0] #定义当前为子树根节点结点
    root = TreeNode(root_val)

root_index = inorder.index(root_val) #找到当前节点在中序遍历中的位置,反映了左子树和右子树的结点数量

root.left = BuildTree(preorder[1:root_index + 1],inorder[:root_index]) #左子树前序和后序遍历，注意前序的第一个结点是根，后面root_index是左子树结点数量
root.right = BuildTree(preorder[root_index + 1 :],inorder[root_index + 1:]) #右子树前序和后序遍历
return root

def postorder(root):
    if root is None:
        return []
    result = []
    result.extend(postorder(root.left))
    result.extend(postorder(root.right))
    result.append(root.val)
    return result

while True:
    try:
        preorder = list(input())
        inorder = list(input())
        root = BuildTree(preorder,inorder)
        result = postorder(root)
        print("".join(result))
    except:
        break
```

### 二叉排序树BST

建树代码

<img src="https://raw.githubusercontent.com/ZhangYiwei-SZU/Pic/main/1715669282742.jpg" alt="1715669282742" style="zoom:50%;" align = "left"/>

注意：BST的插入是递归插入，而不是迭代插入

**[1411 二叉排序树建立和遍历](https://noobdream.com/DreamJudge/Issue/page/1411/#)**

```python
class TreeNode:
    def __init__(self,val):
        self.val = val
        self.left = None
        self.right = None

def insert(root,val):
    if not root: #找到插入位置，建立新结点
        return TreeNode(val)
    if val < root.val: #判断插入位置，小于则沿着左子树查找 
        root.left = insert(root.left,val)
    elif val > root.val:
        root.right = insert(root.right,val)
    return root #返回根节点

def BuildBST(order):
    if not order:
        return None
    root = None #第一个结点为空
    for num in order:
        root = insert(root,num) #从根节点开始递归插入
    return root

def preorder(root):
    if root is None:  # 递归退出条件
        return []
    result = []
    result.append(root.val)
    result.extend(preorder(root.left))  # 用extend返回一个扁平的列表，用append会返回一个嵌套的列表，因为递归深处返回的是列表
    result.extend(preorder(root.right))
    return result

def inorder(root):  # 中序：左右根
    if root is None:  # 递归退出条件
        return []
    result = []
    result.extend(inorder(root.left))  # 用extend返回一个扁平的列表，用append会返回一个嵌套的列表，因为递归深处返回的是列表
    result.append(root.val)
    result.extend(inorder(root.right))
    return result

def postorder(root):
    if root is None:
        return []
    result = []
    result.extend(postorder(root.left))
    result.extend(postorder(root.right))
    result.append(root.val)
    return result

while True:
    try:
        n = eval(input())
        order = list(map(int,input().split()))
        root = BuildBST(order)
        result_pre, result_in, result_post = map(str, preorder(root)), map(str, inorder(root)), map(str, postorder(root))
        print(" ".join(result_pre))
        print(" ".join(result_in))
        print(" ".join(result_post))
    except:
        break
```

**[1317 判断BST树是否相同](https://noobdream.com/DreamJudge/Issue/page/1317/#)**

```python
class TreeNode:
    def __init__(self,val):
        self.val = val
        self.left = None
        self.right = None

def insert(root,val):
    if not root: #找到插入位置，建立新结点
        return TreeNode(val)
    if val < root.val: #判断插入位置，小于则沿着左子树查找
        root.left = insert(root.left,val)
    elif val > root.val:
        root.right = insert(root.right,val)
    return root #返回根节点

def BuildBST(order):
    if not order:
        return None
    root = None #第一个结点为空
    for num in order:
        root = insert(root,num) #从根节点开始递归插入
    return root

def preorder(root):
    if root is None:  # 递归退出条件
        return []
    result = []
    result.append(root.val)
    result.extend(preorder(root.left))  # 用extend返回一个扁平的列表，用append会返回一个嵌套的列表，因为递归深处返回的是列表
    result.extend(preorder(root.right))
    return result

def inorder(root):  # 中序：左右根
    if root is None:  # 递归退出条件
        return []
    result = []
    result.extend(inorder(root.left))  # 用extend返回一个扁平的列表，用append会返回一个嵌套的列表，因为递归深处返回的是列表
    result.append(root.val)
    result.extend(inorder(root.right))
    return result

while True:
    try:
        n = eval(input())
        if n == '0':
            exit()
        origin_order = list(input())
        original_root = BuildBST(origin_order)
        original_pre,original_in = preorder(original_root),inorder(original_root)
        text = list()
        for i in range(n):
            order = list(input())
            root = BuildBST(order)
            pre,_in = preorder(root),inorder(root)
            if pre == original_pre and _in == original_in:
                text.append("YES")
            else:
                text.append("NO")
        for t in text:
            print(t)
    except:
        break

```


```python
# 投机取巧失败
def lower_and_greater(order):
      lower = list()
      greater = list()
      for num in order:
          if num < order[0]:
              lower.append(num)
          elif num > order[0]:
              greater.append(num)
      return lower,greater
  while True:
      try:
          n = eval(input())
          if n == 0:
              break
          origin = list(input())
          origin_lower,origin_greater = lower_and_greater(origin)
          text = []
          for i in range(n):
              BST_Order = list(input())
              BST_Order_lower,BST_Order_greater = lower_and_greater(BST_Order)
              if BST_Order_greater == origin_greater and BST_Order_lower == origin_lower:
                  text.append("YES")
              else:
                  text.append("NO")
          for t in text:
              print(t)
      except:
          break
# - 正确思路：通过比较两个树的前序和中序遍历是否相同判断是否相同
```

### Hash算法

**[1329 统计同成绩人数](https://noobdream.com/DreamJudge/Issue/page/1329/#)**

```python
while True:
    try:
        n = int(input())
        if n == 0:
            exit()
        scores = list(map(int,input().split()))
        target = int(input())
        count = 0
        for score in scores:
            if score == target:
                count += 1
        print(count)
    except:
        break
```

[1175 剩下的树](https://noobdream.com/DreamJudge/Issue/page/1175/#)

```python
while True:
    try:
        L,M = list(map(eval,input().split()))
        route = [i for i in range(1,L+1)]
        for i in range(M):
            left,right = list(map(eval,input().split()))
            for index in range(left,right + 1):
                route[index] = -1
        count = route.count(-1)
        print(L - count + 1)
    except:
        break 

设置哨兵
```



## 第六章 搜索

### 暴力枚举

**[1348AC 百鸡问题](https://noobdream.com/DreamJudge/Issue/page/1348/#)**

```python
while True:
    try:
        money = eval(input())
        for x in range(101):
            for y in range(101):
                for z in range(101):
                    if x + y + z == 100 and 5 * x + 3 * y + z * 1 / 3 <= money:
                        print(f"x={x},y={y},z={z}")
    except:
        break
```

**[1165AC abc](https://noobdream.com/DreamJudge/Issue/page/1165/#)**

```python
  for a in range(10):
      for b in range(10):
          for c in range(10):
              if a * 100 + b * 10 + c + b * 100 + c * 10 + c == 532:
                  print(a,b,c)

没有输入的题目不需要加while True
```

### BFS

```python
# 模版
from collections import deque

def bfs(graph, start):
    visited = set()  # 用集合来记录已经访问过的节点
    queue = deque([start])  # 使用双向队列来实现队列，起始节点入队
    visited.add(start)  # 将起始节点标记为已访问

while queue:
    node = queue.popleft()  # 出队一个节点
    print(node)  # 处理当前节点，这里简单打印出来
    for neighbor in graph[node]:  # 遍历当前节点的邻居节点
        if neighbor not in visited:  # 如果邻居节点未被访问过
            queue.append(neighbor)  # 将邻居节点入队
            visited.add(neighbor)  # 将邻居节点标记为已访问
            
#示例图的邻接表表示

graph = {
    'A': ['B', 'C'],
    'B': ['A', 'D', 'E'],
    'C': ['A', 'F', 'G'],
    'D': ['B'],
    'E': ['B'],
    'F': ['C'],
    'G': ['C']
}

#从节点 'A' 开始进行广度优先搜索

bfs(graph, 'A')
```

**[1563Wrong Answer 迷宫](https://noobdream.com/DreamJudge/Issue/page/1563/)**

**[错误代码](https://noobdream.com/DreamJudge/Issue/page/1563/#)**

```
from collections import deque
dx = [-1,1,0,0]#定义方向参数
dy = [0,0,-1,1]
def bfs(maze,start_x,start_y):
    height,weight = len(maze),len(maze[0])
    visited = [[False] * weight for _ in range(height)]
    queue = deque([(start_x,start_y,0)]) #每个坐标有三个参数，横纵坐标和经过时间time,打包成元组
    visited[start_x][start_y] = True

while queue:
    x,y,time = queue.pop()
    if maze[x][y] == "E":
        return time
    for i in range(4):
        nx,ny = x + dx[i],y + dy[i] #向左、右、上、下移动
        if 0 <= nx < weight and 0 <= ny < height:
            queue.appendleft((nx,ny,time + 1))
            visited[nx][ny] = True

while True:
    try:
        H,W = map(eval,input().split())
        if H == 0 and W == 0:
            exit()
        maze = [input() for _ in range(H)]
        for i in range(H):
            for j in range(W):
                if maze[i][j] == 'S':
                    start_x,start_y = i,j
                    break
        time = bfs(maze,start_x,start_y)
        print(time)
    except:
       break
```


​    

[1162 玛雅人的密码](https://noobdream.com/DreamJudge/Issue/page/1162/#)

```python
from collections import deque
def can_unlock(string):
    word = '2012'
    return word in string

def bfs(n,s):
    if can_unlock(s):
        return s

queue = deque([(s,0)]) #存储当前字符串和字符移动次数
visited = set()
visited.add(s)
while queue:
    string,step = queue.pop()
    for i in range(len(string) - 1):
        new_string = string[:i] + string[i + 1] + string[i] + string[i+2:] #移动相邻的两个字母
        if new_string not in visited:
            visited.add(new_string)
            if can_unlock(new_string):
                return step + 1
            queue.appendleft((new_string,step + 1))#把移动一次后的字符串再传入队列移动一次
return -1




  while True:
      try:
          N = eval(input())
          s = input().strip()
          print(bfs(N,s))
      except:
         break
```

### DFS

模板

```python
def dfs(graph, node, visited=None):
    if visited is None:
        visited = set()
    visited.add(node)
    print(node)
    for neighbor in graph[node]:
        if neighbor not in visited:
            dfs(graph,neighbor,visited)
```

## 第七章 图

### 并查集

> 并查集（Disjoint Set）是一种用于处理集合的数据结构。它主要支持两种操作：查找（Find）和合并（Union）。
>
>
> 在并查集中，每个集合通常由一棵树来表示，其中树的每个节点表示集合中的一个元素。树的根节点被视为集合的代表元素。在初始情况下，每个元素都是一个单独的集合，即每个元素都是其自己的根节点。
>
>
> 并查集支持以下操作：
>
> 查找（Find）： 查找操作用于确定元素所属的集合，即找到元素所在树的根节点。这个操作通常用于判断两个元素是否属于同一个集合。
> 合并（Union）： 合并操作用于将两个集合合并为一个集合。它通过将一个集合的根节点连接到另一个集合的根节点来实现。
>
> 并查集的主要应用包括连接问题、集合的合并与查找问题等。它通常用于解决一些不相交集合的合并与查询问题，例如判断图中的连通分量、判断图中的环路、解决最小生成树问题等。
>
>
> 并查集的实现通常使用树结构来表示集合，具体而言，可以使用数组或者树来实现。在实现中，通过优化树的结构（如路径压缩和按秩合并等）可以提高并查集操作的效率。
>

```python
# 基础代码（建立并查集）

class UnionFind:
    def __init__(self, n):
        self.parent = [i for i in range(n)]  # 初始化每个元素的父节点为自身

def find(self, x):
    if self.parent[x] != x:  # 如果当前节点的父节点不是自身，则递归查找父节点
        self.parent[x] = self.find(self.parent[x])  # 路径压缩
    return self.parent[x]

def union(self, x, y):
    root_x = self.find(x)
    root_y = self.find(y)
    if root_x != root_y:  # 如果两个元素不在同一个集合中，则合并它们
        self.parent[root_x] = root_y

# 基础代码（建立并查集，带rank）

class UnionFind:
    def __init__(self,n):
        self.parent = [i for i in range(n)]
        self.rank = [0] * n   #创建一个含有n个0的rank列表

def find(self,x):
    if self.parent[x] == x:#如果父节点是自身，说明就是集合中的代表结点，返回自身
        return self.parent[x]
    else:
        return self.find(self.parent[x]) # 如果当前节点的父节点不是自身，则递归查找（集合中的）代表结点

def union(self,x,y):
    root_x = self.find(x) #查找x的代表结点（即所在集合）
    root_y = self.find(y)
    if root_x == root_y:
        return
    if self.rank[root_x] > self.rank[root_y]:
        self.parent[root_x] = root_y
    elif self.rank[root_x] > self.rank[root_y]:
        self.parent[root_y] = root_x
    else:
        self.parent[root_x] = root_y
        self.rank[root_y] += 1
```



**[1319 畅通工程2](https://noobdream.com/DreamJudge/Issue/page/1319/#)**

```python
class UnionFind:
    def __init__(self,n):
        self.parent = [i for i in range(n+1)]
        self.rank = [0] * (n + 1) #创建一个含有n个0的rank列表

def find(self,x):
    if self.parent[x] == x:#如果父节点是自身，说明就是集合中的代表结点，返回自身
        return self.parent[x]
    else:
        return self.find(self.parent[x]) # 如果当前节点的父节点不是自身，则递归查找（集合中的）代表结点

def union(self,x,y):
    root_x = self.find(x) #查找x的代表结点（即所在集合）
    root_y = self.find(y)
    if root_x == root_y:
        return
    if self.rank[root_x] > self.rank[root_y]:
        self.parent[root_x] = root_y
    elif self.rank[root_x] > self.rank[root_y]:
        self.parent[root_y] = root_x
    else:
        self.parent[root_x] = root_y
        self.rank[root_y] += 1

while True:
    try:
        n, m = map(eval, input().split())
        if n == 0:
            exit()
        uf = UnionFind(n)
        for i in range(m):
            city1,city2 = map(eval,input().split())
            uf.union(city1,city2)
        num_roads = len(set(uf.find(i) for i in range(1,n+1)))
        print(num_roads - 1)
    except:
        break
```



## 第八章 动态规划

### [原理](https://www.zhihu.com/question/23995189/answer/1094101149)

