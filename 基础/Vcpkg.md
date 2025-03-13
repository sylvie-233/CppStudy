# vcpkg


## 基础介绍


C++包管理工具

cmake使用`CMAKE_TOOLCHAIN_FILE`变量关联`vcpkg.cmake`文件，从而使得vcpkg安装的第三方模块可被cmake使用

### 安装目录
```yaml
vcpkg:
    /docs:
    /ports:
    /scripts:
    /toolsrc:
    /triplets:
    /versions:
```


### vcpkg
```yaml
vcpkg:
    help:
    install:
    integrate: 
        install:
    list:
    remove:
    search:
    update:
```

#### vcpkg.json
```yaml
vcpkg.json:
    
```


项目包配置文件



## 核心内容