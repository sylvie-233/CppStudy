# Conan


## 基础介绍

一个流行的 C/C++ 包管理工具，提供了简单高效的方式来管理和集成第三方库

Conan 是用 Python 编写的，所以你可以使用 pip 安装 Conan
`pip install conan`


- cmake集成conan安装的第三方包：`include(${CMAKE_BINARY_DIR}/conan_toolchain.cmake OPTIONAL)`
- 根据conanfile.txt安装第三方包：`conan build . --output-folder=build`




## 项目结构
```yaml
项目结构:
    /.vscode:
    /bulid:
    CMakeLists.txt:
    conanfile.txt:
```



### CONAN_USER_HOME
```yaml
~/.conan2:
    /extensions:
        /plugins:
            /compatibility:
            profile.py:
    /migrations:
    /profiles:
        default:
    global.conf:
    remotes.json:
    settings.yml:
    version.txt:
```

Conan 用户安装依赖配置、缓存
- Windows：`C:\Users\<username>\.conan`
- Linux/macOS：`~/.conan`


#### profile/default
```yaml
profile/default:
    settings:
        arch:
        build_type:
        compiler:
            version:
        os:
```

默认环境配置



### conan
```yaml
conan:
    --version:
    config:
        home: # 环境配置路径
    install: # 安装第三方依赖
        --build:
        --profile:
        --install-folder: # 
        --output-folder: # 指定输出文件目录
    profile:
        detect: # 配置环境检测、创建
            --name: # 指定配置环境名称
        list: # 配置环境列表
    remote:
        add: # 添加镜像源
        remove:
        update: # 更新镜像源
    search:
    upload:
```


#### conanfile.txt
```yaml
conanfile.txt:
    generators: # 工具生成
        CMakeDeps:
        CMakeToolchain:
    requires: # 项目依赖
```

C++项目配置文件


#### conanbuildinfo.cmake
```c
# 引入 Conan 生成的 CMake 配置文件
include_directories(${CMAKE_BINARY_DIR})

# 引入 Conan 包的 CMake 配置
include(${CMAKE_BINARY_DIR}/conanbuildinfo.cmake)
conan_basic_setup()

# 将 Conan 依赖库链接到可执行文件
target_link_libraries(MyProject ${CONAN_LIBS})
```

cmake集成conan构建


## 核心内容
```yaml
```


### Profile

conan不同编译器环境的配置文件
