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
        accumulate():
        binary_search():
        copy():
        count():
        equal_range():
        fill():
        find():
        is_sorted():
        lower_bound(): # 找到第一个>= value的位置
        max_element():
        min_element():
        next_permutation():
        nth_element():
        partial_sort():
        prev_permutation():
        remove():
        replace():
        reverse():
        rotate():
        shuffle():
        sort(): # 排序
        stable_sort():
        upper_bound(): # 找到第一个>value的位置
        unique():
    <any>:
    <array>: # c固定数组封装
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
        bitset: # 二进制位，重载位运算操作
            all():
            any():
            flip():
            none():
            reset():
            set():
            test():
            to_string():
            to_ullong():
            to_ulong():
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
    <fstream>: # 文件流
        ifstream: # 输入文件流
        ofstream: # 输出文件流
    <functional>:
        placeholders: # 函数绑定占位符
            _1:
            _2:
            _3:
        bind(): # 函数绑定
        equal_to():
        greater(): # 比较器，仿函数
        greater_equal():
        hash(): # 哈希运算
        less():
        less_equal():
        logical_and():
        logical_not():
        modulus():
        not_equal_to():
        plus():
    <future>:
    <initializer_list>:
    <iomanip>: # 格式化输出
        boolalpha: # bool布尔字符显示
        fixed: # 以固定小数点格式显示
        left: # 左对齐 
        right: # 右对齐 
        scientific: # 科学计数法
        setfill(): # 填充字符
        setprecision(): # 设置小数精度
        setw(): # 指定输出的最小宽度，不足时填充空格
    <ios>:
    <iostream>:
        cerr: # 标准异常流
        cin: # 标准输入流
            clear():
            get():
            ignore():
            tie(): # 用于解绑cin与cout，提高输入输出性能
        cout: # 标准输出流
            flush():
        flush:
        ios:
            sync_with_stdio(): # 关闭C和 C++ 标准流同步，提高效率
        getline(): # 读取一行
    <istream>:
    <iterator>:
    <latch>:
    <limits>:
    <list>:
    <locale>:
    <map>: # 映射
        map:
            iterator: # 迭代器，可运算
                first:
                second:
            begin():
            clear():
            count():
            empty():
            end():
            erase():
            find():
            size():
    <memory>:
    <mutex>:
    <num>:
    <numeric>:
    <optional>:
    <ostream>:
    <priority_queue>:
        priority_queue:
            pop():
            push():
            top():
    <queue>: # 队列
        queue:
            back():
            empty():
            front():
            pop():
            push():
            size():
    <random>: # 随机数
    <ranges>:
    <ratio>:
    <regex>:
    <semaphere>:
    <set>: # 集合
        iterator: # 迭代器，可运算
        begin():
        clear():
        count():
        empty():
        end():
        erase():
        find():
        insert():
        size():
    <shared_mutex>:
    <span>: # 简单序列
        span:
    <sstream>:
    <stack>: # 栈
        stack:
            empty():
            pop():
            push():
            size():
            top():
    <stdexcept>:
    <stop_token>:
    <streambuf>:
    <string>: # 字符串
        basic_string:
        string: # 字符串
            iterator: # 迭代器
            npos: # 结束索引位置，-1
            append():
            at():
            back():
            begin(): # 起始迭代器
            c_str(): # c风格字符串
            capacity():
            clear():
            compare():
            contains():
            data(): # c型字符串
            empty():
            end(): # 结束迭代器
            ends_with():
            erase():
            find(): # 字符串查找
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
            substr(): # 字符串截取
        stof(): # 字符串转浮点数
        stoi(): # 字符串转整型
        stol():
        stoll():
        to_string(): # 转换为字符串
    <string_view>: # string字符串只读复制，不会申请新内存
        basic_string_view<>:
        string_view: # 字符串视图
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
            back(): # 尾元素
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




### 函数






### 面向对象






### 智能指针



### 并发



### 模板

#### Concept

概念

泛型约束



