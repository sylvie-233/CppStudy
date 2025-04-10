# C++

>
>``
>
>
>




## 基础介绍


左值（Lvalue）：表示可以被取地址的对象，通常是可以在内存中持久存储的对象，如变量。
右值（Rvalue）：表示临时的、无法取地址的对象，通常是一个临时对象或字面值





C++ STL 四大类：
1. 容器 (Containers)： 容器是用来存储和管理数据的对象，它们定义了数据结构的形式。例如，std::vector、std::list、std::map、std::unordered_map 等。
    - 顺序容器：如 std::vector、std::deque、std::list 等，数据的存储顺序与插入顺序一致。
    - 关联容器：如 std::map、std::set、std::unordered_map、std::unordered_set 等，存储数据时会自动进行排序或哈希。
    - 无序容器：如 std::unordered_map、std::unordered_set，数据存储顺序无关，使用哈希表优化查找速度。
2. 算法 (Algorithms)： STL 提供了大量的算法，用来处理容器中的数据，算法不依赖于容器类型，但会通过迭代器来访问容器中的元素。例如，排序（std::sort）、查找（std::find）、变换（std::transform）等。
3. 迭代器 (Iterators)： 迭代器是 STL 中用于遍历容器的对象，提供了容器元素的访问和操作接口。迭代器可以与算法结合使用，从而在容器上执行操作而不暴露容器的具体实现。
    - 常见的迭代器类型包括 input_iterator、output_iterator、forward_iterator、bidirectional_iterator 和 random_access_iterator。
4. 函数对象和适配器 (Function Objects and Adapters)： 函数对象是可调用的对象，可以像函数一样使用。STL 中有许多标准的函数对象，例如 std::less、std::greater 等，它们通常与算法一起使用。
    - 适配器用于对容器、迭代器等进行封装，以便提供额外的功能。例如，std::stack 是容器适配器，std::priority_queue 是一个基于堆的容器适配器



支持自定义字面量





### gcc
```yaml
gcc:

```



### g++
```yaml
g++:
    -c: # 编程生成中间文件(.o)
    -o: # 编译可执行文件(.exe)，指定输出文件名
    -I: # 头文件位置
    --std: # C++标准库版本
```



## 核心内容
```yaml
std:
    <algorithm>: # 算法库
        accumulate():
        binary_search(): # 二分查找，(begin, end, val)
        copy():
        count(): # 出现次数
        count_if():
        equal_range():
        fill():
        find(): # 查找，(begin, end, val)
        find_if(): # 条件查找，(begin, end, pred)
        for_each(): # 迭代遍历，(begin, end, func)
        is_sorted():
        lower_bound(): # 找到第一个>= value的位置
        max():
        max_element():
        merge(): # 
        min():
        min_element(): # 最小元素迭代器
        next_permutation():
        nth_element():
        partial_sort():
        prev_permutation():
        remove():
        replace(): # 元素替换，(begin, end, old, new)
        replace_if():
        reverse(): # 反转元素顺序   
        rotate():
        set_difference():
        set_intersection():
        set_union():
        shuffle():
        sort(): # 排序,(begin, end, comp)
        stable_sort():
        transform(): # 元素转换，(begin, end, out, func)
        upper_bound(): # 找到第一个>value的位置
        unique(): # 去重,去除相邻重复（返回新末尾）
    <any>: # 动态，任意类型
        any: # 任意类型
            has_value():
            reset(): # 清空值
            type():
        bad_any_cast: # any转换异常
        any_cast(): # any转具体类型，抛出bad_any_cas异常
        make_any():
    <array>: # c固定大小数组封装
        array: # 固定大小数组
            iterator: # 迭代器
            at(): # 元素索引
            empty(): # 判空
            back(): # 最后一个元素
            begin():
            data(): # 返回一个指向数组元素的指针（通常用于与 C 风格 API 一起使用）
            end():
            fill(): # 数据填充
            front(): # 第一个元素
            size(): # 大小
    <atomic>: # 原子操作
        atomic: # 原子类
            compare_exchange_strong(): # CAS操作
            exchange():
            fetch_add():
            fetch_sub():
            load():
            store():
        atomic_flag:
            clear():
            test_and_set():
        atomic_ref(): # 原子引用
    <barrier>: # 线程屏障,同步机制
        barrier:
            arrive():
            arrive_and_drop():
            arrive_and_wait(): # 到达，等待
    <bit>: # 位运算库
        bit_ceil(): # 	返回 ≥x 的最小 2 的幂
        bit_floor(): # 返回 ≤x 的最大 2 的幂
        bit_width(): # 	表示 x 用几位能表示（不含符号位）
        byteswap(): # 交换字节顺序
        countl_one(): # 前导 1 的个数
        countl_zero(): # 前导 0 的个数
        countr_one(): # 后缀 1 的个数
        countr_zero(): # 后缀 0 的个数
        has_single_bit(): # 判断是否是 2 的幂
        popcount(): # x 的二进制中 1 的个数
    <bitset>: # 位集合
        bitset: # 位集合，固定大小二进制位，重载位运算操作
            all():
            any(): # 判断是否有任意 1 位
            count(): # 	返回 1 的位数
            flip(): # 翻转某一位
            none():
            reset(): # 将所有位清零
            set(): # 设置某一位的值
            size(): # 返回 bitset 的位数
            test(): # 判断指定位置是否为 
            to_string(): # 转换为字符串表示
            to_ullong():
            to_ulong():
    <charconv>: # 字符与数值转换
        from_chars():
        to_chars():
    <chrono>: # 时间
        clock: # 时间的测量工具
        duration: # 时间的长度或间隔
            count():
        high_resolution_clock: # 提供更高精度的时钟，常用与计算时间差
            now():
        microseconds: # 微秒
        milliseconds: # 毫秒
        minutes(): # 分钟
        seconds: # 秒
            count():
        steady_clock: # 提供不会回退的单调时钟
        system_clock: # 系统时间
            now():
            to_time_t():
        time_point: # 特定的时间点
        duration_cast():
        to_time_t():
    <codecvt>:
    <compare>:
    <complex>:
    <concepts>: # 概念（Concepts），模板参数类型的约束
        floating_point: # 浮动点类型
        integral: # 整数类型
        same_as<>:
        signed_integral:
        unsigned_integral:
    <condition_variable>: # 条件变量，需配合锁机制使用
        condition_variable: # 适用于标准锁 (std::mutex)
            wait():
            wait_for():
            wait_until():
            notify_all():
            notify_one():
        condition_variable_any: # 适用于任意类型的锁（不仅仅是 std::mutex）
    <coroutine>: # 协程，常与future库一切使用
        co_await: # 等待一个异步操作，协程在此暂停，直到操作完成
            await_ready():
            await_resume():
            await_suspend():
        co_return: # 结束协程并返回值
            task: # (约定task任务)
                h: # (约定coroutine_handle协程句柄)
                promise_type: #（约定promise内部处理类型）
        co_yield: # 使协程暂停并返回一个值，之后可以继续执行
        coroutine_handle:
            promise_type: #（约定promise内部处理类型）
                final_suspend():
                get_return_object():
                initial_suspend():
                return_value():
                unhandled_exception():
            destroy():
            done():
            from_promise(): # 创建coroutine_handle,(promise_type是由框架创建的）
            promise(): # 对协程的 promise_type 对象的引用
        coroutine_traits:
        suspend_always: # 用于co_await 协程挂起
        suspend_never:
    <deque>: # 双端队列容器
        deque: # 双端队列容器
            at():
            back():
            front():
            pop_back():
            pop_front():
            push_back():
            push_front():
    <exception>: # 异常
        exception: # 异常基类
            what():
        get_terminate():
        set_terminate():
        set_unexpected():
        terminate(): # 调用中断异常处理
        unexpected(): # 
    <execution>: # 并行执行策略，常配合<alogorithm>使用
        par: # 并行
        seq: # 串行
        par_unseq: # 并行无序
    <filesystem>: # 文件系统
        filesystem: # 文件系统
            directory_iterator: # 目录迭代器
                path():
            filesystem_error: # 文件系统异常
            path: # 路径操作
                extension():
                filename():
                string():
                parent_path():
            create_directories():
            create_directory():
            create_symlink():
            exists():
            file_size():
            is_directory():
            is_regular_file():
            last_write_time():
            remove():
            remove_all():
    <format>: # 格式化字符串，取代printf
        format(): # 字符串格式化
            {}:
                :d:
                :f:
                :x:
                :<:
                :>:
                :^: # 居中
                :+: # 正负号
                :[0][n]: # 填充0，位宽n
        format_to():
        make_format_args():
        vformat(): # 变参 format
    <forward_list>: # 单向链表容器
        before_begin():
        clear():
        emplace_after(): # 地构造并插入（避免复制)   
        erase_after():
        insert_after():
        push_front():
        remove():
    <fstream>: # 文件流，析构函数会自动关闭文件
        filebuf:
        fstream: # 文件流
            close():
        ifstream: # 输入文件流
            close():
        ofstream: # 输出文件流
            close():
    <functional>: # 函数工具库
        function: # 函数封装器
        placeholders: # 函数绑定占位符
            _1:
            _2:
            _3:
        bind(): # 函数绑定，配合placeholders占位符使用
        equal_to():
        greater(): # 比较器，仿函数
        greater_equal():
        hash(): # 哈希函数模板
        less():
        less_equal():
        logical_and():
        logical_not():
        mem_fn(): # 成员函数引用
        modulus():
        not_fn(): # 函数结果取反包装
        not_equal_to():
        plus(): # +加法运算
        ref(): # 函数绑定，引用传参
    <future>: # 异步响应结果future、promise、packaged_task、async()、
        future: # 异步响应结果，co_await能直接取出future中的值
            get(): # 阻塞等待取出
            share():
        future_status:
        launch: # 启动策略
            async: # 立即执行
            deferred: # get()延迟执行
        packaged_task: # 普通函数包装成任务task
            get_future():
        promise: # 异步传参
            get_future():
            set_value():
        shared_future: # 多线程共享future
        async(): # 执行异步函数，返回future
    <initializer_list>: # 大括号初始化列表
        initializer_list: # 初始化列表，可直接赋值给vector
    <iomanip>: # 格式化输出， 局部有效性，当前流式操作后面的局部有效
        boolalpha: # bool布尔字符显示
        fixed: # 以固定小数点格式显示
        left: # 左对齐 
        right: # 右对齐 
        scientific: # 科学计数法
        setfill(): # 填充字符
        setprecision(): # 设置小数精度
        setw(): # 指定输出的最小宽度，不足时填充空格
    <ios>: # 流格式、状态控制
        ios:
    <iostream>: # 输入、输出
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
    <limits>: # 数值范围
        numeric_limits: # 数值字面量范围
            max():
            min():
    <list>:
    <locale>:
    <map>: # 哈希表，映射
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
    <memory>: # 内存管理
        unique_ptr: # 独享指针
        shared_ptr: # 共享指针，引用计数
        weak_ptr: # 弱引用指针，
        make_shared():
        make_unique():
    <mutex>:
    <new>: # 内存分配
        bad_alloc: # 内存分配 异常
        delete(): # 删除内存，可不带括号使用
        delete[]():
        new(): # 开辟内存，可不带括号使用
        new[]():
    <numeric>: # 数学运算
        acumulate():
        gcd():
        iota():
        lcm():
    <optional>: # 空值处理
        nullopt: # 空值
        optional: # 可空类型，通过解引用 * 访问内部值
        make_optional():
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
        mt19937():
        random_device():
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
        stack: # 栈
            empty():
            pop():
            push():
            size():
            top():
    <stdexcept>: # 标准异常
        runtime_error: # 运行时异常
        logic_error: # 逻辑异常
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
        basic_string_view:
        string_view: # 字符串视图
            data():
            empty():
            find():
            length():
            remove_prefix():
            size():
            substr():
        wstring_view:
    <syncstream>:
    <system_error>:
    <thread>: # 线程库
    <tuple>:
    <typeindex>:
    <typeinfo>: # type类型信息
        type_info: # type类型信息
            hash_code():
            name(): # type名称
    <type_traits>: # 编译时执行类型检测
        conditional<>: # <T, U, V>,类型选择工具
        enable_if<>: # 模板特化或者约束模板参数
        is_callable<>:
        is_const<>:
        is_floating_point<>:
        is_integral<>: # 整数类型
        is_pointer<>:
        is_reference<>:
        is_same<>: # 类型相等is_same<T, U>
            value: # 比较结果，bool
        remove_pointer<>: # 移除指针
            type:
        remove_reference<>: # 移除引用
            type:
    <unodered_map>:
    <unordered_set>:
    <utility>: # 工具库
        pair: # 二元组
        make_pair():
        swap():
    <variant>: # 联合类型变体
        bad_variant_access: # 错误变体访问异常
        variant: # 联合类型变体，代替传统 C++联合体union
        get(): # 取值
        holds_alternative(): # 类型判断
    <vector>: # 动态数组
        vector: # 向量
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
    bool:
    char:
    char8_t:
    char16_t:
    char32_t:
    double:
    float:
    int:
    long:
    long double:
    long long: # 64位整型，LL
    short:
    uintptr_t: # 
    unsigned:
    void:
```


聚合类型：data class


#### struct

结构体


#### string
```c++
std::string str = R"(
    原生字符串，可用于多行字符串
)";
```
字符串




#### array
```c++
std::array<int, 5> arr = {1, 2, 3, 4, 5};

// 使用循环访问并打印元素
for (int i = 0; i < arr.size(); ++i) {
    std::cout << arr[i] << " ";
}
```

静态大小数组、c数组封装
用于替代传统的 C 风格数组


#### list

链表，容器



#### forward_list

单向链表容器



#### vector
```c++
// 初始化长度为100，初始值为0的数组
vector<int> arr(100, 0);


```

动态数组，容器，大小可变



#### stack

栈，容器适配器

#### queue

队列，容器适配器


#### priority_queue

优先队列，容器适配器


#### deque

双端队列容器
支持随机访问




#### bitset


#### set


#### map



#### enum








### 流程控制
```yaml
Control Flow:
    <=>:
    auto: # 自动类型推断，常用于lambda、函数指针
    const: # 常量
    concept: # 自定义概念，模板参数约束
        requires():
    constexpr: # 常量表达式，编译时就计算某些常量的值，可定义常量表达式函数
    constinit:
    constval:
    final: # 标记不允许重写、不允许继承
    noexcept: # 标记方法无异常
    override: # 标记重写
    thread_local: # 线程局部对象
    typedef: # 类型别名
    alignas(): # 位对齐
    alignof(): # 
    const_cast():
    decltype(): # 获取type类型，编译时
    dynamic_cast():
    reinterpret_cast():
    sizeof():
    static_assert(): # 编译时断言
    static_cast():
    typeid(): # 获取type id，运行时
    using: # 命名空间引入、类型别名
    if ... else if ... else ...: # 条件判断，支持初始化语句
    for ...: # 循环遍历、增强for循环
```

太空船运算符`<=>`
支持结构化绑定：解构，可用于结构体





#### Type Cast
```c++
```

类型转换
- static_cast：常规类型转换（整数、浮点数、类之间转换）	，编译时检查，不进行运行时检查
- dynamic_cast：多态类型之间的转换（父类与子类），运行时检查，转换不安全时返回 nullptr 或抛出异常
- const_cast：去除或添加const限定符，只改变常量属性，不改变对象类型
- reinterpret_cast：强制类型转换，低级别内存操作，不进行类型检查，直接进行内存级别的转换




#### Exception Handler
```c++
try {
    throw std::invalid_argument("Invalid argument!");
} catch (const std::invalid_argument& e) {
    std::cout << "Caught exception: " << e.what() << std::endl;
}
```

- try
- catch
- throws






#### RValue Reference
```c++
int&& x = 10;  // x 是一个右值引用，绑定到右值 10
```

右值引用
- && 主要用于实现 移动语义（Move Semantics） 和 完美转发（Perfect Forwarding）
- 允许程序员操作右值（临时对象）并优化资源管理

用于需要区分左值、右值的情况


#### Attibute

- deprecated:
- fallthrough:
- likely: 分支预测判断
- maybe_unused:
- nodiscard:
- noreturn:




### 函数

使用 auto 支持函数类型后置



#### Lambda
```c++
// 基础lambda声明
auto greet = []() {
    std::cout << "Hello, Lambda!" << std::endl;
};

// 捕获所有变量的引用
auto sumByReference = [&]() {
    std::cout << "Sum by reference: " << a + b << std::endl;
};

// 可变捕获 mutable
auto modifyX = [x]() mutable {  // 使用 mutable 允许修改捕获的副本
    x += 5;
    std::cout << "Modified x: " << x << std::endl;
};
```

匿名函数
- 按值捕获所有变量：`[=]`
- 按引用捕获所有变量：`[&]`


#### Auto Function
```c++
auto add(int a, int b) -> int {
    return a + b;  // 返回类型会被推导为 int
}
```

可实现函数类型后置




### 面向对象


#### Constructor
```c++
class MyClass {
public:
    MyClass() {
        std::cout << "Default constructor called!" << std::endl;
    }

    MyClass(int x) {
        std::cout << "Constructor with parameter: " << x << std::endl;
    }

    MyClass(const MyClass& other) {
        std::cout << "Copy constructor called!" << std::endl;
    }

    MyClass(MyClass&& other) noexcept {
        std::cout << "Move constructor called!" << std::endl;
    }
};
```


构造函数：
- 默认构造函数 (Default Constructor)
- 带参数构造函数 (Parameterized Constructor)
- 拷贝构造函数 (Copy Constructor)
- 移动构造函数 (Move Constructor)

构造函数的调用顺序： 当创建一个对象时，构造函数的调用顺序为：
1. 基类构造函数（如果有继承关系）。
2. 成员对象的构造函数。
3. 当前类的构造函数


支持构造函数初始化列表
触发移动构造：`MyClass obj2 = std::move(obj1);`

using继承构造函数


#### Destructor
```c++
class MyClass {
private:
    int* data;
public:
    MyClass() {
        data = new int[100];  // 动态分配内存
    }

    ~MyClass() {
        delete[] data;  // 在析构函数中释放内存
    }
};
```

析构函数


默认析构函数
如果没有显式定义析构函数，C++ 编译器会自动生成一个默认的析构函数。默认析构函数会销毁类的成员变量，但不会释放动态分配的资源，因此如果类使用了动态内存管理（如 new），则必须显式定义析构函数



#### Extends
```c++
class Base {
public:
    Base(int x) {
        std::cout << "Base constructor with value: " << x << std::endl;
    }
};

class Derived : public Base {
public:
    Derived(int x) : Base(x) {  // 使用初始化列表调用基类构造函数
        std::cout << "Derived constructor" << std::endl;
    }
};
```

继承的访问控制：
- public：基类的 public 和 protected 成员会保持原有访问权限，而 private 成员不可访问
- protected：基类的 public 和 protected 成员会变为 protected，private 成员不可访问
- private：基类的 public 和 protected 成员会变为 private，private 成员不可访问


支持多重继承


支持 虚拟继承，用于解决多重继承中出现的 菱形继承 问题，即多个派生类共享同一个基类时，避免基类成员被重复继承




#### Virtual
```c++
class Base {
public:
    virtual void show() {  // 声明为虚函数
        std::cout << "Base class show function" << std::endl;
    }
};

class Derived : public Base {
public:
    void show() override {  // 重写基类的虚函数
        std::cout << "Derived class show function" << std::endl;
    }
}
```


虚函数，提供重写override，可以有默认实现
C++没有接口

虚函数的执行机制：虚函数的调用由 虚函数表（vtable） 和 虚函数指针（vptr） 实现。
- 虚函数表（vtable）：每个类中如果有虚函数，编译器会为这个类创建一个虚函数表，表中包含了指向虚函数实现的指针。虚函数表是静态的，它在编译时就创建好并存储于内存中。
- 虚函数指针（vptr）：每个对象在运行时都会有一个指向虚函数表的指针，称为 vptr，它指向该对象所属类的虚函数表。通过 vptr，程序可以在运行时找到正确的函数实现。

虚函数的调用首先通过对象的 vptr 找到相应的虚函数表，然后再从虚函数表中查找正确的函数指针进行调用


虚函数与析构函数：
- 如果类中有虚函数，通常也需要将析构函数声明为虚函数。这样，在通过基类指针删除派生类对象时，能够保证派生类的析构函数被调用，防止内存泄漏
- 如果没有虚析构函数，delete 基类指针时，派生类的析构函数不会被调用，从而导致资源泄漏


#### Abstract
```c++
class AbstractClass {
public:
    virtual void show() = 0;  // 纯虚函数
};
```


抽象类
抽象类的定义通过至少包含一个 纯虚函数 来实现。纯虚函数是没有实现的虚函数，必须在派生类中被重写。纯虚函数使用 = 0 进行声明



### 模块



#### NameSpace
```c++
namespace MyNamespace {
    int myVar = 42;
    void myFunction() {
        std::cout << "Hello from MyNamespace!" << std::endl;
    }
}

using namespace MyNamespace;  // 引入 MyNamespace 中的所有成员
std::cout << myVar << std::endl;  // 可以直接使用 myVar
myFunction();  // 也可以直接使用 myFunction()
```

命名空间
- 内联命名空间 inline namespace
- 嵌套命名空间简写
- 匿名命名空间：即没有名字的命名空间，是 C++ 中的一种特殊命名空间，它的作用范围局限于当前文件，因此它常常用于隐藏全局变量或函数，避免它们与其他文件中的标识符发生冲突





### 智能指针


#### Smart Pointer
```c++
    // ptr 超出作用域时，内存自动释放
std::unique_ptr<int> ptr = std::make_unique<int>(10);


// 当 ptr1 和 ptr2 都超出作用域时，内存才会释放
std::shared_ptr<int> ptr1 = std::make_shared<int>(20);
std::shared_ptr<int> ptr2 = ptr1; // 引用计数增1

auto ptr = std::make_unique<int>(10);  // 使用 unique_ptr 管理内存
```


std::unique_ptr、std::shared_ptr 和 std::weak_ptr
- std::unique_ptr：表示对对象的唯一所有权，不能被复制，只有一个 unique_ptr 可以拥有一个对象。当 unique_ptr 被销毁时，它会自动释放内存
- std::shared_ptr：表示共享所有权。多个 shared_ptr 可以指向同一个对象，引用计数机制确保当最后一个 shared_ptr 被销毁时，内存才会被释放
- std::weak_ptr：不改变对象的引用计数，通常用于解决循环引用问题，辅助管理 shared_ptr


#### Move
```c++
class MyClass {
private:
    int* data;
public:
    MyClass(int value) : data(new int(value)) {}
    
    // 移动构造函数
    MyClass(MyClass&& other) noexcept : data(other.data) {
        other.data = nullptr;  // 将原对象的指针设置为 nullptr，避免析构时释放资源
    }

    // 移动赋值运算符
    MyClass& operator=(MyClass&& other) noexcept {
        if (this != &other) {
            delete data;  // 释放当前资源
            data = other.data;
            other.data = nullptr;  // 处理原对象
        }
        return *this;
    }

    ~MyClass() { delete data; }  // 析构函数
};

// 调用移动构造函数
MyClass a(10);    // 创建对象 a
MyClass b = std::move(a);  


// 调用移动赋值运算符
MyClass a(10);
MyClass b(20);
b = std::move(a);  
```

移动

std::move 并不会实际移动对象，而是将对象转换为右值引用，从而触发移动构造函数
- 当一个临时对象（右值）被用于 初始化 新对象时，会调用移动构造函数
- 当一个已存在的对象被 赋值 一个右值（临时对象）时，会调用移动赋值运算符


#### Forward
```c++
// 接受左值引用和右值引用的通用函数
template<typename T>
void wrapper(T&& arg) {
    // 完美转发参数
    process(std::forward<T>(arg));  // 将 arg 完美转发到 process 函数
}

// 接受任意类型的函数
void process(int& i) {
    std::cout << "Lvalue processed: " << i << std::endl;
}

void process(int&& i) {
    std::cout << "Rvalue processed: " << i << std::endl;
}

int x = 10;
wrapper(x);  // 传递左值
wrapper(20); // 传递右值
```

完美转发
将函数参数转发到另一个函数时，保持参数的值类别（左值或右值）
完美转发通常依赖于右值引用（T&&）和 std::forward 来实现

### 并发


#### Thread

线程


#### Coroutine
```c++
struct task {
    struct promise_type {
        task get_return_object() {
            return task{std::coroutine_handle<promise_type>::from_promise(*this)};
        }

        std::suspend_always initial_suspend() {
            return {};  // 协程初始化时挂起
        }

        std::suspend_always final_suspend() noexcept {
            return {};  // 协程结束时挂起
        }

        void return_value(int value) {
            result = value;  // 设置协程返回值
        }

        void unhandled_exception() {
            std::exit(1);  // 异常处理
        }

        int result;  // 协程的返回值
    };

    std::coroutine_handle<promise_type> h;

    task(std::coroutine_handle<promise_type> h) : h(h) {}
    ~task() { h.destroy(); }

    int get() {
        return h.promise().result;  // 获取协程的返回值
    }
};

task example_coroutine() {
    std::cout << "Before await\n";
    co_await std::suspend_always{};  // 挂起协程
    std::cout << "After await\n";
    co_return 42;  // 返回值 42
}


auto task_instance = example_coroutine();
task_instance.h.resume();  // 恢复协程
std::cout << "Returned value: " << task_instance.get() << "\n";
```


协程
task = coroutine_handle + promise_type 
- get_return_object()：在协程开始时调用一次，返回协程的返回对象，通常是封装协程句柄的类型（如 task）。
- initial_suspend()：协程开始时调用，控制协程是否在启动时挂起。
- final_suspend()：协程结束时调用，控制协程是否在结束时挂起。
- return_value()：当协程通过 co_return 返回一个值时调用，用来存储返回值。
- unhandled_exception()：当协程抛出未捕获的异常时调用，用于处理异常。


task仅仅是用于协程状态处理，复杂耗时操作应该定义在协程函数中
coroutine_handle是task处理协程状态的核心
promise_type 是由 C++ 协程框架自动创建的，具体来说，它是 协程 的一部分，在协程的生命周期中由协程框架负责管理

协程对象创建流程：
1. 调用协程函数：当调用协程函数时（如 example_coroutine()），协程框架会为协程创建一个 promise_type 对象。
2. 创建协程句柄：框架通过 get_return_object() 返回一个封装了协程句柄（std::coroutine_handle<promise_type>）的对象（如 task）
3. 初次挂起：协程执行到 initial_suspend()，此时协程会被挂起，等待外部恢复。
4. 恢复执行：外部代码调用 std::coroutine_handle::resume() 恢复协程，协程继续执行。
5. 存储返回值：协程执行到 co_return 时，返回值会存储在 promise_type 对象中，并触发 return_value()。
6. 协程完成：当协程完成时，final_suspend() 会被调用，协程终止，销毁协程句柄和 promise_type 对象。



协程执行顺序：
1. 调用一个协程函数（co_await、co_return）,协程框架会根据协程的定义自动创建一个 promise_type
2. get_return_object() 调用，创建并返回一个 task 对象，task 的构造方法 `task(std::coroutine_handle<my_promise_type> h)` 会接收协程句柄 h，并初始化 task 对象
3. task持有coroutine_handle，处理协程执行状态







#### Atomic

原子操作


#### Mutex

锁


#### Barrier

<barrier> 是 C++20 引入的头文件，提供了一个线程屏障（barrier）机制，用于协调多个线程在某个同步点等待，直到所有线程都到达该点再继续执行


#### Condition Variable

条件变量
用于线程间同步的一部分，提供了线程等待、通知机制，通常用于实现线程间的协调和通信

允许一个线程等待直到另一个线程发出某种信号（通知）。这种机制在生产者-消费者问题、任务队列等多线程场景中非常常见



### 模板
```c++
// 函数模板
template<typename T>
T add(T a, T b) {
    return a + b;
}

// 类模板
template<typename T>
class Box {
private:
    T value;
public:
    Box(T val) : value(val) {}
    T getValue() { return value; }
};

Box<int> intBox(10);  // int 类型的 Box
```


函数模板、类模板



#### Template Specialization
```c++
template<typename T>
class Printer {
public:
    void print(T value) {
        std::cout << value << std::endl;
    }
};

// 特化版本：当类型为 char 时使用不同的实现
template<>
class Printer<char> {
public:
    void print(char value) {
        std::cout << "Char: " << value << std::endl;
    }
};
```

模板特化
希望为特定类型提供不同的实现。模板特化（Template Specialization）允许我们为特定类型提供特化版本的模板


#### SFINAE
```c++
template<typename T>
typename std::enable_if<std::is_integral<T>::value, void>::type
print(T value) {
    std::cout << "Integer: " << value << std::endl;
}

template<typename T>
typename std::enable_if<!std::is_integral<T>::value, void>::type
print(T value) {
    std::cout << "Non-integer: " << value << std::endl;
}

print(42);  // 调用整数版本
print(3.14);  // 调用非整数版本
```

Substitution Failure Is Not An Error
模板特化进阶版本，自定义条件选择模板

SFINAE 是 C++ 的一项特性，它允许模板在某些情况下失败而不抛出错误，而是选择其他合适的重载。常见的用途包括通过类型特性选择合适的模板



enable_if：给模板加匹配条件、允许基于编译时条件来启用或禁用函数模板或类模板的特化
```c++
template<bool B, class T = void>
struct enable_if;
```
- 如果 B 为 true，enable_if 有一个公有成员 typedef type 等于 T
- 如果 B 为 false，则没有 type 成员


#### Variadic Templates
```c++
template<typename... Args>
void print(Args... args) {
    // 通过递归展开参数包实现打印
    (std::cout << ... << args) << std::endl;
}

// (args op ...)   左折叠
// (... op args)   有折叠
// args...         形参包展开
template<typename T>
void print(T&& t) {
    std::cout << t << " ";
}

template<typename T, typename... Args>
void print(T&& t, Args&&... args) {
    std::cout << t << " ";
    print(std::forward<Args>(args)...);  // 递归展开其余的参数
}

print(1, 2, 3, 4);  // 输出: 1 2 3 4
```


变长模板

支持折叠表达式



#### Concept
```c++
// 要求 T 类型必须能够支持 a + b 的操作，且返回值类型应与 T 相同
template<typename T>
concept Addable = requires(T a, T b) {
    { a + b } -> std::same_as<T>;
};


// 使用Concept进行泛型约束
template<Addable T>
T add(T a, T b) {
    return a + b;
}


// 组合多个Concept
template<std::integral T>
concept IntegralAddable = Addable<T> && std::integral<T>;
```

最终版模板特化

概念、泛型约束
概念可以帮助我们在模板参数上添加约束，从而使得模板更加可读、可维护并且能够在编译时捕捉到错误



#### Template Metaprogramming
```c++
template<int N>
struct Factorial {
    static const int value = N * Factorial<N - 1>::value;
};

template<>
struct Factorial<0> {
    static const int value = 1;
};

std::cout << Factorial<5>::value << std::endl;  // 输出 120
```


模板元编程
模板元编程是 C++ 中通过模板实现的编程方法，允许在编译时进行计算。模板元编程常常用于生成编译时常量或实现某些编译时决策



