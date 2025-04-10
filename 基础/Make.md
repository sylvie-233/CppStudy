# Make

`从零开始学Makefile：P32`

## 基础介绍


C++ 构建命令行工具

基于 目标依赖 构建
```Makefile
目标: 依赖
    执行方法
    ...
```

Makeile的最终目标只能由一个
依赖发送变化时触发重新生成
默认第一行为最终目标
支持多目标写法：独立多目标、组合多目标&



| 有序依赖：依赖变化不触发更新
依赖列表中可定义局部变量
依赖中使用的变量是立即展开的
支持依赖延迟添加、静态模式匹配::、




### make
```yaml
make:
    -f: # 指定Makefile
    -C: # 执行指定目录下的Makefile
    --file:
    --version:
```



## 核心内容
```yaml
Makefile:
    #: # 注释
    -: # 忽略命令错误，继续向下执行
    =: # 变量定义，延迟展开，支持函数定义（$1, $2）
    :=: # 变量定义，立即展开
    ?=: # 变量定义，未定义时定义
    +=: # 变量内容追加
    !=: # 获取命令执行结果，赋值变量
    $$: # 转义$符
    $(): # 变量引用，内置函数调用
        1,2,3: # 函数参数
        :: # 变量内容替换
        %: # 
        @: # 目标名称
            D: # 目录
            F: # 文件
        *: # 目标名称，去除后缀
        <: # 第一个依赖名称
        ?: # 有改动的依赖名称
        ^: # 所有依赖，不包含特殊依赖
        +: # 所有依赖，不包含特殊依赖
        \|: # 所有有序依赖 
        abspath: # 绝对路径
        addprefix: # 添加前缀
        addsuffix: # 添加后缀
        and: # 所有不为空，返回最后一个
        basename: # 无后缀文件名
        call: # 函数调用，支持自定义函数
        dir: # 获取目录名
        error: # 错误信息提示、中断make
        eval: # 动态生成Makefile文本内容
        file: # 文件操作
            \>: # 覆盖
            \>>: # 追加
            <: # 读 
        filter: # 文本过滤
        filter-out: # 文本排除过滤
        firstword: # 第1项
        findstring: # 字符串查找
        flavor: # 查看变量定义方式
        foreach: # 列表项转换
        if: # 条件判断
        info: # 函数， 信息输出
        intcmp: # 整数比较
        join: # 列表合并拼接
        lastword: # 最后一项
        let: # 列表变量解构
        notdir: # 获取文件名
        or: # 第一个不为空的条件
        origin: # 变量定义来源
        patsubst: # 模式文本替换
        realpath: # 文件绝对路径
        shell: # 执行shell脚本，获取返回值
        sort: # 字典序排序
        strip: # 去除两边空白
        subst: # 文本替换
        suffix: # 文件后缀名
        value: # 查看变量定义、变量值
        warning: # 警告信息，不会中断make
        wildcard: # 文件模糊搜索
        word: # 取出第n项
        wordlist: # 取出子列表
        words: # 项数
        AR: # 归档命令
        CC: # c语言编译命令
        CPP:
        CXX: # c++语言编译命令
        CXXFLAGS:
        LDFLAGS: # 链接命令参数
        LDLIBS: # 链接库
        MAKE: # make命令
        RM:
        SHELL: # 当前shell脚本命令
        VPATH: # 依赖文件搜索路径
    .DEFAULT_GOAL: # 最终目标
    .ONESHELL: # 所有命令在同一个shell进程中执行（默认每条命令都不同）
    .PHONY: # 伪目标
    .SECONDEXPANSION: # 依赖列表变量延迟展开，默认立即展开
    .SILENT: # 关闭指定目标的命令回显
    define ... endef: # 定义多行字符串变量
    export: # Makefile变量导入子项目
    ifdef ... else ifdef ... else ... endif: # 条件判断变量定义
    ifeq: # 相等判断
    ifneq: # 不等判断
    include: # 引入其它Makefile
    override: # 强制使用变量，不会被覆盖
    undefine: # 删除变量
    unexport:
    vpath: # 指定匹配依赖文件的搜索路径
```