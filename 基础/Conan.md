# Conan


## 基础介绍

一个流行的 C/C++ 包管理工具，提供了简单高效的方式来管理和集成第三方库

Conan 是用 Python 编写的，所以你可以使用 pip 安装 Conan
`pip install conan`



### CONAN_USER_HOME
Conan安装依赖缓存
- Windows：`C:\Users\<username>\.conan`
- Linux/macOS：`~/.conan`
```
~/.conan
├── data/          # 包含所有安装的库的数据文件
│   └── <package_name>/
│       └── <version>/
│           └── <package_revision>/
├── packages/      # 包含所有包的二进制文件（安装时下载的）
│   └── <package_hash>/
│       ├── bin/
│       ├── include/
│       ├── lib/
│       └── share/
└── conan.conf     # Conan 配置文件
```



### conan
```yaml
conan:
    install:
        --build:
        --profile:
        --install-folder:
    profile:
        detect:
    search:
    upload:
```


#### conanfile.txt
```yaml
conanfile.txt:
    requires:
```

项目配置文件


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