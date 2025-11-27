# CMake

## 基础介绍

核心功能：
1. include头文件管理
2. library库文件管理
3. 生成库
4. 生成可执行文件


一个CMake模块的核心文件：
- `<PackageName>.cmake`:
- `<PackageName>Version.cmake`:
- `<PackageName>Targets.cmake`:



- 没必要切到bulid目录，然后`cmake ..`，推荐使用`cmake -S . -B build`
- set定义变量、`${var}`引用变量
- add_subdirectory添加子cmake项目
- 函数作用域PRIVAE私有(依赖模块不可见)、PUBLIC共有(依赖模块可见)
- find_package查找第三方库，查询`<Package>Config.cmake`文件并执行
- vscode CMake Tools插件会在build目录下自动生成 compile_commands.json 和配置 IntelliSense


### 项目结构
```yaml
/build: # MinGW Makefiles compile
    ./cmake:
    /CMakeFiles:
        /3.26.3: # cmake版本
        /app.dir:
    /vcpkg_installed: # vcpkg安装的第三方包
        /<triplets>: # 对应的平台
            /bin:
            /debug:
            /include:
            /lib:
            /share:
    cmake_install.cmake: # cmake --install安装此项目执行的脚本
    CMakeCache.txt:
    compile_commands.json:
    Makefile:
    vcpkg-manifest-install.log:
/build: # visual studio compile
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
CMakeLists.txt: # 核心配置文件
CMakePresets.json: # 用户预设配置文件
```

#### 安装目录
```yaml
cmake:
    
```

#### cmake_install.cmake
```yaml
cmake_install.cmake:
```



#### settings.json
```yaml
settings.json:

```



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
        Unix Makefiles:
    -P: # 运行cmake脚本
    -S: # 指定source源文件目录 CMakeLists.txt所在目录
    --build: # 执行构建，生成可执行文件（用于替代make命令）
        -j: # 多线程
        --target: # 指定目标
    --help:
    --install: # 指定构建目录，查询cmake_install.cmake文件
        --prefix: # 指定安装路径 CMAKE_INSTALL_PREFIX
    --preset: # 生成配置文件 CMakePresets.json、使用指定的preset预设配置
    --version: # 版本
```

#### cmake-gui

cmake gui程序

#### CMakeLists.txt
```yaml
CMakeLists.txt:
    cmake_variables: # ${xxx} 内置变量
        BUILD_SHARED_LIBS: # 是否构建动态库
        CMAKE_ARCHEIVE_OUTPUT_DIRECTORY: # 静态库文件输出目录
        CMAKE_BINARY_DIR: # 输出目录
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
        CMAKE_LIBRARY_OUTPUT_DIRECTORY: # so文件输出目录
        CMAKE_MODULE_PATH: # 模块搜索路径（给find_package使用）
        CMAKE_PREFIX_PATH:
        CMAKE_PROJECT_NAME: # 项目名
        CMAKE_RUNTIME_OUTPUT_DIRECTORY: # dll、exe二进制文件输出目录
        CMAKE_SOURCE_DIR: # 源代码目录
        CPACK_RESOURCE_FILE_LICENSE:
        CPACK_SOURCE_GENERATOR: # 打包生成格式
            TGZ:
        CMAKE_TOOLCHAIN_FILE: # 工具链文件
        EXECUTABLE_OUTPUT_PATH: # 可执行文件保存目录
        LIBRARY_OUTPUT_PATH: # 可执行文件保存目录
        MINGW: # mingw编译器判断
        PROJECT_BINARY_DIR: # 项目build二进制目录
        PROJECT_NAME: # 项目名称
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
    FetchContent_Declare(): # 下载第三方源码
    FetchContent_MakeAvailable(): # 
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
        COPY: # 文件拷贝
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
        TARGETS: # 配置安装的CMake目标（库或可执行文件）
            EXPORT: # 导出模块.cmake文件，生成一个 CMake target 导出文件，用于 find_package 识别库
            ARCHIVE: # 静态库 (.a 或 .lib) 安装目录
            LIBRARY: # 动态库 (.so / .dll / .dylib)安装目录
            RUNTIME: # 可执行程序安装目录
            INCLUDES: # 头文件安装目录
                DESTINATION: # 安装的目标目录
        DIRECTORY: # 文件拷贝
        CODE: # 执行自定义cmake命令
        COMPONENT:
        FILE:
        FILES: # 要安装的具体文件，文件移动
        PERMISSIONS: # 设置文件权限
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


#### CMakePresets.json
```yaml
CMakePresets.json:
    version:
    cmakeMinimumRequired:
    configurePresets:
        name:
        displayName:
        inherits: # 配置继承
        condition: # 条件触发
        toolchainFile: # 第三方工具链集成
        generator: # 生成器配置（makefile、ninja）
        binaryDir:
        installDir:
        cacheVariables:
            CMAKE_INSTALL_PREFIX:
            CMAKE_C_COMPILER:
            CMAKE_CXX_COMPILER:
            CMAKE_BUILD_TYPE:
    buildPresets: # make构建配置
        configurePreset: # 引用configurePresets
    testPresets:
```

CMake统一构建配置中心（简化cmake命令行配置）



#### CMakeCache.txt
```yaml
CMakeCache.txt:

```

cmake缓存变量


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


### Control Flow
```yaml
Control FLow: # cmake控制流程
    block(): # 代码块定义
        endblock():
    foreach(): # for循环
        IN:
            ITEMS:
            ZIP_LISTS:
        RANGE:
        ---
        endforeach():
    file():
        GLOB:
    function(): # 函数定义
        ARGC:
        ARGV:
        ARG_N:
        ---
        return():
        endfunction():
    if(): # 条件判断
        IN_LIST:
        PATH_EQUAL: # 路径相等
        STREQUAL: # 字符串相等
        ---
        elseif():
        else():
        endif():
    list():
        APPEND:
        GET:
        JOIN:
        LENGTH: # 列表长度
    macro(): # 宏定义
        endmacro():
    math():
        EXPR:
    set(): # 变量定义
        CACHE: # 缓存变量定义
        ---
        unset():
        option(): # 缓存变量定义（带有默认值的 BOOL 类型缓存变量）
    string():
        FIND:
    while(): # while循环
        endwhile():
```

cmake脚本控制流程


#### Function

自定义函数



#### Generator Expression
```yaml
Generator Expression:
    $<AND:expr1,expr2,...>: # 逻辑与
    $<BOOL:expr>: # 将表达式转换为 0/1
    $<C_COMPILER_ID:MSVC>: # 当前 C 编译器是 MSVC
    $<CONFIG:Debug>: # 当前配置为 Debug 返回 1，否则 0
    $<CONFIG:Release>: # 当前配置为 Release 返回 1，否则 0
    $<CXX_COMPILER_ID:GNU>: # 当前 C++ 编译器是 GCC
    $<IF:cond,true,false>: # 条件表达式
    $<LENGTH:list>: # 列表长度
    $<JOIN:list,sep>: # 将列表用分隔符连接成字符串
    $<MAX:a,b>: # 数学操作
    $<NOT:expr>: # 逻辑非
    $<OR:expr1,expr2,...>: # 逻辑或
    $<PLATFORM_ID:Windows>: # 平台是 Windows
    $<STREQUAL:a,b>: # 字符串是否相等
    $<TARGET_FILE:tgt>: # 获取目标文件路径
    $<TARGET_LINKER_FILE:tgt>: # 获取链接器文件路径
    $<TARGET_OBJECTS:tgt>: # 获取目标对象文件列表（object library）
    $<TARGET_PROPERTY:tgt,prop>: # 获取目标 tgt 的属性 prop
```

生成器表达式
生成器表达式是一种在 生成阶段（build system generation）动态计算值 的语法
它允许你在 CMakeLists.txt 中为目标属性、编译选项、链接库等设置 条件化、依赖于配置、平台或目标 的值


### CMake File

#### Config.cmake
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

#### Install.cmake

控制安装路径：`CMAKE_INSTALL_PREFIX`

### CMake Module Config
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



#### CMake Module
```yaml
CMAKE_INSTALL_PREFIX:
    /include:
        /libA:
            xxx.h:
        /libB:
            xxx.h:
    /lib:
        /cmake:
            /<PackageName>: # 包下的三个核心cmake文件
                <PackageName>.cmake: # 告诉 CMake 如何导入你的库，find_package使用，include导入targets.cmake文件
                <PackageName>Version.cmake: # 记录库版本信息，方便 find_package 做版本检查
                <PackageName>Targets.cmake: # 导出库 target 的实际信息(库文件路径、依赖的编译选项、头文件路径)
        xxx.a:
```


#### CMake Module Find
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




### CMake Generator Expression

生成器表达式变量，用于简化条件判断
生成阶段执行

#### #cmakedefine

`#define`扩展，对于0值、OFF值、undefined值不会生成定义


### CMake Function


#### configure_file()


#### find_package()

CMake 模块包括两种常见形式：
- Find模块 `Find<PackageName>.cmake`，适用于不使用 CMake 构建的第三方库。
- Config模块 `<PackageName>Config.cmake`，适用于使用 CMake 构建并支持 CMake 配置的库。


模块搜索路径：
- `<PackageName>_ROOT`
- `<PackageName>_DIR`
- CMAKE_PREFIX_PATH: cmake模块搜索路径前缀

模块查找成功自动设置变量：
- `<PackageName>_FOUND`：找到了就是True,没找到就是未设定
- `<PackageName>_INCLUDE_DIR`：即头文件目录
- `<PackageName>_LIBRARY`：即库文件


Config.cmake、ConfigVersion.cmake
XXX_DIR模块路径



查找和配置外部依赖库流程：
- 用户定义的路径：CMAKE_PREFIX_PATH
- CMake内建的模块：CMAKE_MODULE_PATH、例如FindBoost.cmake，FindSDL.cmake等
- 配置文件：一些库提供了CMake配置文件（`<LibraryName>Config.cmake`）
- 系统默认路径

基于`XXX_DIR`去寻找指定的XXX模块






#### function()

函数创建




### Extension


#### vcpkg

通过`CMAKE_TOOLCHAIN_FILE`变量指定vcpkg.cmake工具文件（find_package能查找vcpkg安装的第三方包）
`cmake -B build -DCMAKE_TOOLCHAIN_FILE=[vcpkg_root]/scripts/buildsystems/vcpkg.cmake`


#### conan
