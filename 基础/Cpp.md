# Cpp

>
>``
>
>
>




## 基础介绍






C++ STL 四大类：
- 算法
- 容器
- 仿函数
- 迭代器







### g++

```yaml
g++:
    -o: # 指定输出文件名
    --std: # C++标准库版本
```



## 核心内容
```yaml
std:
    <algorithm>: # 算法库
        sort(): # 排序
    <any>:
    <array>: # c数组封装
        array:
            iterator:
            []:
                set(): # 修改元素
            at():
            begin():
            fill():
    <atomic>: # 原子库
        atomic_ref(): # 原子引用
    <barrier>:
    <bit>:
    <bitset>:
    <charconv>:
    <chrono>:
    <codecvt>:
    <compare>:
    <complex>:
    <concepts>:
    <condition_variable>:
    <coroutine>:
    <deque>:
    <exception>:
    <execution>:
    <filesystem>:
    <format>:
    <forward_list>:
    <fstream>:
    <functional>:
    <future>:
    <initializer_list>:
    <iomanip>:
    <ios>:
    <iostream>:
    <istream>:
    <iterator>:
    <latch>:
    <limits>:
    <list>:
    <locale>:
    <map>:
    <memory>:
    <mutex>:
    <num>:
    <numeric>:
    <optional>:
    <ostream>:
    <queue>:
    <random>: # 随机数
    <ranges>:
    <ratio>:
    <regex>:
    <semaphere>:
    <set>:
    <shared_mutex>:
    <span>: # 简单序列
        span:
    <sstream>:
    <stack>:
    <stdexcept>:
    <stop_token>:
    <streambuf>:
    <string>: # 字符串
        basic_string<T>:
        string:
            iterator: # 迭代器
            npos: # -1索引位置
            append():
            at():
            back():
            begin(): # 起始迭代器
            c_str():
            capacity():
            clear():
            compare():
            contains():
            data(): # c型字符串
            empty():
            end(): # 结束迭代器
            ends_with():
            erase():
            find(): # 字符串查找（）
            front():
            insert():
            length(): # 字符串长度
            max_size():
            push_back():
            replace():
            reserve():
            resize():
            shrink_to_fit():
            size(): # 字符串大小
            starts_with():
            substr(): # 获取子串
        stof(): # 字符串转浮点数
        stoi(): # 字符串转整型
        to_string(): # 转换为字符串
    <string_view>: # string字符串只读复制，不会申请新内存
        basic_string_view<>:
        string_view:
            data():
            remove_prefix():
        wstring_view:
    <syncstream>:
    <system_error>:
    <thread>: # 线程库
    <tuple>:
    <typeindex>:
    <typeinfo>:
    <type_traits>:
    <unodered_map>:
    <unordered_set>:
    <utility>:
    <variant>:
    <vector>: # 动态数组
        vector:
            clear(): # 清空
            empty(): # 为空判断
            pop_back(): # 尾部删除
            push_back(): # 尾部添加
            resize(): # 扩/缩容
            size(): # 数组长度
    <version>:
```
### 数据类型
```yaml
Data Types:
    long long: # 64位整型
    uintptr_t:
```


#### string

字符串


#### struct

结构体


#### array

静态大小数组、c数组封装




#### vector
```c++
// 初始化长度为100，初始值为0的数组
vector<int> arr(100, 0);


```

动态数组，大小可变


#### set


#### map



#### stack



#### queue







### 流程控制
```yaml
Control Flow:
    <=>:
    for ...: # 循环遍历、增强for循环
```

太空船运算符`<=>`



#### Exception Handler

#### Attibute

- `[[likely]]`：分支预测判断









### 面向对象






### 智能指针



### 并发



### 模板

#### Concept

概念

泛型约束



