#表达式

####算术运算符

Lua的算术运算符如下表所示：

| 算术运算符   | 说明   |
|:-----------:| -----:|
| + | 加法 |
| - | 减法 |
| * | 乘法 |
| / | 除法 |
| ^ | 指数 |
| % | 取模 |

>示例代码：test1.lua

```lua
print(1 + 2)       -->打印 3
print(5 / 10)      -->打印 0。 整数相除的结果是向下取整
print(5.0 / 10)    -->打印 0.5。 浮点数相除的结果是浮点数
-- print(10 / 0)   -->注意除数不能为0，计算的结果会出错
print(2 ^ 10)      -->打印 1024。 求2的10次方

local num = 1357
print(num%2)       -->打印 1
print((num % 2) == 1)) -->打印 true。 判断num是否为奇数
print((num % 5) == 0)  -->打印 false。判断num是否能被5整数
```

####关系运算符

| 关系运算符   | 说明   |
|:-----------:| -----:|
|   <    | 小于     |
|   >    | 大于     |
|   <=   | 小于等于  |
|   >=   | 大于等于  |
|   ==   | 等于     |
|   ~=   | 不等于   |

>示例代码：test2.lua

```lua
print(1 < 2)    -->打印 true
print(1 == 2)   -->打印 false
print(1 ~= 2)   -->打印 true
local a, b = true, false
print (a == b)  -->打印 false
```

**注意：Lua语言中不等于运算符的写法为：~=**

>在使用“==”做等于判断时，要注意对于table,userdate和函数，Lua是作引用比较的。也就是说，只有当两个变量引用同一个对象时，才认为它们相等。可以看下面的例子：

```lua
local a = { x = 1, y = 0}
local b = { x = 1, y = 0}
if a == b then
  print("a==b")
else
  print("a~=b")
end

---output:
a~=b
```


####逻辑运算符

| 逻辑运算符   | 说明  |
|:-----------:| ----:|
|   and   | 逻辑与    |
|   or    | 逻辑或    |
|   not   | 逻辑非    |

>示例代码：test3.lua

```lua
local c = nil
local d = 0
local e = 100
print(c and d)  -->打印 nil
print(c and e)  -->打印 nil
print(d and e)  -->打印 100
print(c or d)   -->打印 0
print(c or e)   -->打印 100
print(not c)    -->打印 true
print(not d)    -->打印 false
```

**注意：所有逻辑操作符将false和nil视作假，其他任何值视作真，对于and和or，“短路求值”，对于not，永远只返回true或者false**

####优先级

Lua操作符的优先级如下表所示(从高到低)：

| 优先级      |
|:----------:|
|   ^        |
|   not &emsp; #&emsp;-  |
|   * &emsp; / &emsp; %    |
|   + &emsp; -      |
|   ..       |
|   <&emsp;>&emsp;<=&emsp; >= &emsp;==&emsp; ~=   |
|   and      |
|   or       |

>示例：

```lua
local a, b = 1, 2
local x, y = 3, 4
local i = 10
local res = 0
res = a + i < b/2 + 1  -->等价于res =  (a + i) < ((b/2) + 1)
res = 5 + x^2*8        -->等价于res =  5 + ((x^2) * 8)  
res = a < y and y <=x  -->等价于res =  (a < y) and (y <= x)
```

**若不确定某些操作符的优先级，就应显示地用括号来指定运算顺序。这样做还可以提高代码的可读性。**
