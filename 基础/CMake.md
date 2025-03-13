# CMake

## 基础介绍

### cmake
```yaml
cmake:
    --install: # 执行cmake_install.cmake安装脚本，依赖CMAKE_INSTALL_PREFIX作为安装根目录
    --version: # 版本
```

#### CMakeLists.txt
```yaml
CMakeLists.txt:
    _builtin: # ${xxx} 内置变量
        CMAKE_COMMAND:
        CMAKE_INSTALL_PREFIX:
        CMAKE_PREFIX_PATH:
        CMAKE_PROJECT_NAME: # 项目名
        CMAKE_TOOLCHAIN_FILE: # 工具链文件
        EXECUTABLE_OUTPUT_PATH: # 可执行文件保存目录
        LIBRARY_OUTPUT_PATH: # 可执行文件保存目录
        PROJECT_SOURCE_DIR: # 项目根目录
    add_custom_command(): # 添加自定义命令、脚本
        TARGET: # 应用目标
        POST_BUILD: # 应用时期
        COMMAND: # 自定义命令
    add_executable(): # 创建可执行文件、添加源文件
    add_library(): # 创建库文件、添加源文件
        MODULE:
        SHARED:
        STATIC:
    aux_source_directory(): # 自动扫描目录，找到所有的源文件并将其添加到指定的变量中，不会递归
    cmake_minimum_required():
        VERSION: # 指定CMAKE版本
    file(): # 文件操作、赋值变量、递归查找
        GLOB: # 模糊匹配查找文件
        MAKE_DIRECTORY: # 创建目录
        READ: # 获取文件内容
        REAL_PATH: # 获取文件绝对路径
        REMOVE: # 删除文件
    find_library(): # 查询库文件
    find_package(): # 查询第三方模块
        COMPONENTS: # 只使用其中部分组件
        CONFIG: # 配置模式 <PackageName>Config.cmake
        PATHS: # 手动指定查找路径
        REQUIRED: # 必须包
    foreach(): # 循环遍历
        endforeach():
        return():
    function(): # 函数定义
        endfunction():
    get_filename_component():
    if(): # 条件分支执行
        elseif():
        else():
        endif():
        AND:
        EQUAL: # 相等
        NOT:
        OR:
    include(): # 引入外部模块
    include_directories(): # 引入头文件目录，默认
    install(): # 安装
        CODE: # 执行自定义cmake命令
        COMPONENT:
        DESTINATION: # 安装的目标目录
        DIRECTORY: # 想要安装的目录
        EXPORT:
        FILES: # 要安装的具体文件
        PERMISSIONS: # 设置文件权限
        TARGETS: # 想要安装的CMake目标（例如，库或可执行文件）
    macro(): # 宏定义
        endmacro():
    math(): # 数学运算
    message(): # 调试信息输出
    project(): # 项目名
    set(): # 设置变量
    set_target_properties(): # 设置目标的属性
    string(): # 字符串操作
        CONCAT: # 字符串拼接
        FIND: # 子字符串查找
        REGEX MATCH: # 正则匹配
        REPLACE: # 字符串替换
        SPLIT: # 字符串分隔
        TOLOWER:
        TOUPPER:
    target_compile_features(): # 给指定目标 添加编译选项
    target_include_directories(): # 给指定目标 引入头文件目录
    target_link_libraries(): # 给指定目标 链接库
    time(): # 获取当前时间
    while(): # 循环语句
        endwhile():
```


## 核心内容

### Config.cmake

- 设置库的路径（例如，头文件路径、库文件路径）
- 提供库的相关编译选项、链接选项、版本信息等
- 使得其他 CMake 项目能够轻松地找到并使用你的库


### cmake_install.cmake

控制安装路径：`CMAKE_INSTALL_PREFIX`


### find_package

查找和配置外部依赖库流程：
- 用户定义的路径：CMAKE_PREFIX_PATH
- CMake内建的模块：CMAKE_MODULE_PATH、例如FindBoost.cmake，FindSDL.cmake等
- 配置文件：一些库提供了CMake配置文件（<LibraryName>Config.cmake）
- 系统默认路径

`CMAKE_PREFIX_PATH`: 指定查找包路径
`Find<PackageName>.cmake`
`<PackageName>Config.cmake`


