# CMake

## 基础介绍


library库文件管理、include头文件管理
生成库、生成可执行文件
配置阶段、生成阶段








### cmake
```yaml
cmake:
    -B: # 指定build构建目录
    -D: # 手动设置option变量
    -E: # 执行命令脚本
        cat:
        copy:
        copy_if_different:
        echo:   
        make_directory:
        md5sum:
        remove:
        rename:
        rm:
    -G: # 指定生成器
        MinGW Makefiles:
    -P: # 运行cmake脚本
    -S: # 指定源文件目录 CMakeLists.txt所在目录
    --build: # 执行构建，生成可执行文件
        -j: # 多线程
        --target: # 指定目标
    --help:
    --install: # 安装执行，执行cmake_install.cmake安装脚本，依赖CMAKE_INSTALL_PREFIX作为安装根目录
        --prefix: # 安装路径
    --version: # 版本
```

#### CMakeLists.txt
```yaml
CMakeLists.txt:
    cmake_variables: # ${xxx} 内置变量
        BUILD_SHARED_LIBS: # 是否构建动态库
        CMAKE_BUILD_TYPE: # 构建类型
        CMAKE_COMMAND: # cmake命令
        CMAKE_CXX_STANDARD: # cpp语法版本
            11:
            14:
            17:
        CMAKE_CXX_STANDARD_REQUIRED: # 必须指定cpp语法版本
        CMAKE_CURRENT_BINARY_DIR: # 当前项目二进制目录，子CMakeLists.txt所在目录
        CMAKE_CURRENT_SOURCE_DIR: # 当前项目根目录，子CMakeLists.txt所在目录
        CMAKE_GENERATOR: # cmake生成器
        CMAKE_HOST_WIN32: # win32平台判断
        CMAKE_INSTALL_PREFIX: # install安装目录
        CMAKE_PREFIX_PATH:
        CMAKE_PROJECT_NAME: # 项目名
        CMAKE_ARCHEIVE_OUTPUT_DIRECTORY: # 静态库文件输出目录
        CMAKE_LIBRARY_OUTPUT_DIRECTORY: # so文件输出目录
        CMAKE_MODULE_PATH: # 模块搜索路径
        CMAKE_RUNTIME_OUTPUT_DIRECTORY: # dll、exe二进制文件输出目录
        CMAKE_TOOLCHAIN_FILE: # 工具链文件
        CPACK_RESOURCE_FILE_LICENSE:
        CPACK_SOURCE_GENERATOR: # 打包生成格式
            TGZ:
        EXECUTABLE_OUTPUT_PATH: # 可执行文件保存目录
        LIBRARY_OUTPUT_PATH: # 可执行文件保存目录
        MINGW: # mingw编译器判断
        PROJECT_BINARY_DIR: # 项目build二进制目录
        PROJECT_SOURCE_DIR: # 项目根目录，CMakeLists.txt所在目录
        USE_MYMATH:
        XXX_DIR: # 第三方模块XXX的位置
        XXX_VERSION_MAJOR: # 项目版本号
        XXX_VERSION_MINOR:
    cmake_generator: # $<x:y> 条件生成表达式变量，表达式、简化手动判断，生成阶段起作用
        AND:
        BOOL:
        BUILD_INTERFACE:
        COMPILE_LANG_AND_ID:
        IN_LIST:
        INSTALL_INTERFACE:
        JOIN:
        PATH:
            IS_ABSOLUTE:
        STREQUAL:
    add_compile_options():
    add_custom_command(): # 添加、执行自定义命令、脚本
        COMMAND: # 自定义命令，执行的命令
        DEPENDS: # 依赖目标
        OUTPUT: # 输出文件
        POST_BUILD: # 应用时期
        TARGET: # 应用目标
    add_custom_target(): # 创建自定义目标
        COMMAND: # 自定义命令
        COMMENT:
        WORKING_DIRECTORY:
    add_dependencies(): # 添加依赖
    add_executable(): # 创建可执行文件目标、添加源文件
    add_library(): # 创建库文件目标、添加源文件
        INTERFACE: # 接口库，虚拟库，用于封装库操作选项
        MODULE:
        SHARED: # 动态库
        STATIC: # 静态库
    add_subdirectory(): # 添加子目录（子CmakeLists.txt），文件夹名
    add_test(): # 添加测试
        COMMAND: # 测试运行指令
        Name: # 测试目标名称
    aux_source_directory(): # 自动扫描目录，找到所有的源文件并将其添加到指定的变量中，不会递归
    check_cxx_source_compile(): # 测试源码编译，常用于检测编译特性
    cmake_host_system_information(): # 系统信息查询
        QUERY:
            OS_NAME:
        RESUTLT:
    cmake_minimum_required():
        VERSION: # 指定CMAKE版本
    cmake_parse_arguments(): # 函数参数解析
    cmake_path(): # 路径操作
        GET:
            FILENAME:
            PARENT_PATH:
            STEM:
        NORMAL_PATH:
    configure_file(): # 根据模板，复制文件生成（模板文件中可访问cmake脚本变量）
        COPYONLY:
    configure_package_config_file(): # 生成模块Config.cmake配置文件
        INSTALL_DESTINATION:
    define_property(): # 自定义属性
    enable_testing(): # 开启测试
    file(): # 文件操作、赋值变量、递归查找
        APPEND: # 文件追加
        GLOB: # 模糊匹配查找文件
        MAKE_DIRECTORY: # 创建目录
        READ: # 获取文件内容
            LIMIT:
            OFFSET:
        REAL_PATH: # 获取文件绝对路径
        REMOVE: # 删除文件
        WRITE: # 文件写入
    find_library(): # 查询库文件
    find_package(): # 导入第三方模块，CMAKE_MODULE_PATH
        COMPONENTS: # 只使用其中部分组件
        CONFIG: # 配置模式 <PackageName>Config.cmake
        EXACT: # 精确匹配
        PATHS: # 手动指定查找路径
        REQUIRED: # 必须包
    foreach(): # 循环遍历
        RANGE:
        endforeach():
        return():
    function(): # 函数定义
        ARGC:
        ARGN:
        ARGV:
        endfunction():
    get_cmake_property():
    get_filename_component():
    get_property(): # 获取属性
    if(): # 条件分支执行，使用option变量
        elseif():
        else():
        endif():
        AND:
        DEFINED: # 定义了
        EQUAL: # 相等
        EXISTS: # 文件存在
        IN_LIST:
        MATCHS: # 正则
        NOT:
        OR:
    include(): # 引入外部模块(预定义模块)，增强cmake特性
        CheckCXXSourceCompiles:
        CMakePackageConfigHelpers:
        CPack: # 打包模块
        InstallRequiredSystemLibraries:
    include_directories(): # 引入头文件目录，默认对所有目标可见
    install(): # 安装，生成目标文件移动
        CODE: # 执行自定义cmake命令
        COMPONENT:
        DESTINATION: # 安装的目标目录
        DIRECTORY: # 想要安装的目录
        EXPORT: # 导出模块.cmake文件
        FILE:
        FILES: # 要安装的具体文件，文件移动
        PERMISSIONS: # 设置文件权限
        TARGETS: # 想要安装的CMake目标（例如，库或可执行文件）
    link_directories(): # 库文件目录，默认对所有目标可见
    list(): # 列表操作
        APPEND: # 追加
        FILTER:
            INCLUDE:
        GET:
        INSERT:
        JOIN:
        LENGTH:
        POP_BACK:
        POP_FRONT:
        REMOVE_ITEM:
        REVERSE:
        SORT:
        TRANSFORM:
    macro(): # 宏定义
        endmacro():
    mark_as_advanced():
    math(): # 数学运算
        EXPR: # 表达式
        OUTPUT_FORMAT:
    message(): # 调试信息输出
        FATAL_ERROR: # 异常错误、停止
        SEND_ERROR: # 生成异常错误，不停止
        STATUS:
    option(): # 创建开关布尔变量，ON/OFF
    project(): # 项目名
        DESCRIPTION: 
        VERSION: # 项目版本号
    set(): # 设置变量，${xxx}使用，$ENV{XXX} 访问环境变量
        CACHE:
        ENV: # 设置环境变量
        FORCE:
            BOOL: # 变量类型
            FILEPATH:
            PATH:
            STRING:
        PARENT_SCOPE: # 修改父级作用域的变量
    set_property(): # 设置变量属性
        CACHE:
        PROPERTY:
            STRINGS:
    set_target_properties(): # 设置目标的属性
    set_tests_properties(): # 设置测试目标属性
        PROPERTIES:
            PASS_REGULAR_EXPRESSION:
    string(): # 字符串操作
        APPEND: # 尾部追加
        COMPARE:
            LESS:
        CONCAT: # 字符串拼接
        FIND: # 子字符串查找
            REVERSE:
        JOIN:
        LENGTH:
        MD5:
        PREPEND:
        RANDOM:
        REGEX: 
            MATCH: # 正则匹配
            REPLACE:
        REPEAT:
        REPLACE: # 字符串替换
        SPLIT: # 字符串分隔
        STRIP:
        TIMESTAMP:
        TOLOWER:
        TOUPPER:
    target_compile_definitioins(): # 添加预编译define宏
        PRIVATE:
    target_compile_features(): # 给指定目标 添加编译特性
        INTERFACE:
            cxx_std_11:
    target_compile_options(): # 给指定目标 添加编译选项
    target_include_directories(): # 给指定目标 引入头文件目录
        INTERFACE: # 该project不需要，提供给依赖该project的项目
        PRIVATE: # 只提供给该project
        PUBLIC: # 该project需要、依赖该project也提供
    target_link_directories(): # 链接库目录
    target_link_libraries(): # 给指定目标 链接库
    target_sources(): # 给指定目标添加 源文件
    time(): # 获取当前时间
    unset(): # 取消变量
    while(): # 循环语句
        break():
        continue():
        endwhile():
    write_basic_package_version_file(): # 生成模块ConfigVersion.cmake版本信息文件
```

#### 生成目录
```yaml
/build:
    /CmakeFiles:
        /xxx.dir: # 不同的target有不同的dir目录、makefile
    ALL_BUILD.vcxproj:
    ALL_BUILD_vcxproj.filters:
    cmake_install.cmake:
    CMakeCache.txt:
    XXX.sln:
    XXX.vcxproj:
    XXX.vcxproj:
    XERO_CHECK.vcxproj.filters:
    XERO_CHECK.vcxproj.filters:
```

### ctest
```yaml
ctest:
    -V: # 详细信息
```

测试运行


### cpack
```yaml
cpack:
    -G: # 指定生成器
```



## 核心内容

### CMake Generator Expression

生成器表达式变量，用于简化条件判断
生成阶段执行


### Config.cmake
```yaml
/MyLibrary:
    /CMake:
        MyLibraryConfig.cmake: # CMake 配置文件
    /lib:
        MyLibrary.lib:        # 静态库文件
    /include:
        /MyLibrary:
            MyLibrary.h:      # 头文件
```

第三方包配置文件
- 设置库的路径（例如，头文件路径、库文件路径）
- 提供库的相关编译选项、链接选项、版本信息等
- 使得其他 CMake 项目能够轻松地找到并使用你的库

`XXX_LIBRARIES`、`XXX_INCLUDE_DIRS`、`XXX_FOUND`

### Install.cmake

控制安装路径：`CMAKE_INSTALL_PREFIX`


### #cmakedefine

`#define`扩展，对于0值、OFF值、undefined值不会生成定义

### configure_file()


### find_package()

Config.cmake、ConfigVersion.cmake
XXX_DIR模块路径






查找和配置外部依赖库流程：
- 用户定义的路径：CMAKE_PREFIX_PATH
- CMake内建的模块：CMAKE_MODULE_PATH、例如FindBoost.cmake，FindSDL.cmake等
- 配置文件：一些库提供了CMake配置文件（<LibraryName>Config.cmake）
- 系统默认路径

`CMAKE_PREFIX_PATH`: 指定查找包路径
`Find<PackageName>.cmake`
`<PackageName>Config.cmake`

基于`XXX_DIR`去寻找指定的XXX模块


CMake 模块包括两种常见形式：
- Find模块 `Find<PackageName>.cmake`，适用于不使用 CMake 构建的第三方库。
- Config模块 `<PackageName>Config.cmake`，适用于使用 CMake 构建并支持 CMake 配置的库。

#### Find Module
```bash
# FindMyLibrary.cmake
# 1. 指定默认的查找路径
find_path(MyLibrary_INCLUDE_DIR
  NAMES MyLibrary.h
  PATHS
    "C:/libs/MyLibrary/include"
    "/usr/local/include"
    PATH_SUFFIXES MyLibrary
)

find_library(MyLibrary_LIBRARY
  NAMES MyLibrary
  PATHS
    "C:/libs/MyLibrary/lib"
    "/usr/local/lib"
)

# 2. 如果找到了库，设置相关变量
if(MyLibrary_INCLUDE_DIR AND MyLibrary_LIBRARY)
  set(MyLibrary_FOUND TRUE)
  set(MyLibrary_INCLUDE_DIRS ${MyLibrary_INCLUDE_DIR})
  set(MyLibrary_LIBRARIES ${MyLibrary_LIBRARY})
endif()

# 3. 如果没有找到库，报告错误
if(NOT MyLibrary_FOUND)
  message(FATAL_ERROR "MyLibrary not found!")
endif()



# 使用模块 MyLibrary
# 设置查找路径
set(CMAKE_MODULE_PATH "${CMAKE_SOURCE_DIR}/cmake" ${CMAKE_MODULE_PATH})

# 查找库
find_package(MyLibrary REQUIRED)

# 使用找到的库
if(MyLibrary_FOUND)
  include_directories(${MyLibrary_INCLUDE_DIRS})
  target_link_libraries(MyTarget ${MyLibrary_LIBRARIES})
endif()
```


兼容第三方库
`Find<PackageName>.cmake` 模块适用于第三方库未提供 CMake 配置文件的情况。在这种情况下，你需要编写一个查找该库的CMake脚本，该脚本告诉 CMake 如何找到库的头文件和库文件，并配置相关的编译选项。
- XXX_INCLUDE_DIR：指定头文件目录
- XXX_LIBRARY_DIR：指定库文件目录
- XXX_FOUND：指定该模块配置成功


#### Config Module
```bash
# MyLibraryConfig.cmake
set(MyLibrary_INCLUDE_DIRS "C:/libs/MyLibrary/include")
set(MyLibrary_LIBRARIES "C:/libs/MyLibrary/lib/MyLibrary.lib")

# 设置其他可能的变量
set(MyLibrary_FOUND TRUE)



# 使用模块MyLibrary
# 设置查找路径
set(CMAKE_PREFIX_PATH "C:/libs/MyLibrary/lib/cmake")

# 查找 MyLibrary
find_package(MyLibrary REQUIRED)

# 使用找到的库
if(MyLibrary_FOUND)
  include_directories(${MyLibrary_INCLUDE_DIRS})
  target_link_libraries(MyTarget ${MyLibrary_LIBRARIES})
endif()
```

原生cmake管理库
`<PackageName>Config.cmake` 模块适用于库已经使用 CMake 构建，并且提供了CMake配置文件的情况。CMake 配置文件通常位于安装路径的 lib/cmake/ 目录下，并包含库的相关设置。用户通过 find_package() 来查找并使用这些设置
- XXX_INCLUDE_DIR：指定头文件目录
- XXX_LIBRARY_DIR：指定库文件目录
- XXX_FOUND：指定该模块配置成功

使用configure_package_config_file()和write_basic_package_version_file()内置API直接生成Config.cmake和ConfigVersion.cmake文件，不需要手动创建

生成Config.cmake需要模板文件



### function()

函数创建


