# vcpkg


## 基础介绍


C++包管理工具
- 经典模式
- 清单模式


vcpkg环境变量：
- CMAKE_TOOLCHAIN_FILE: cmake集成vcpkg.cmake
- VCPKG_DEFAULT_TRIPLET：设置默认的 triplet（构建平台x64-windows）
- VCPKG_ROOT：设置 vcpkg 安装目录的根路径
- VCPKG_INSTALLATION_ROOT：设置 vcpkg 安装依赖库的根路径
- VCPKG_FEATURE_FLAGS：控制 vcpkg 的功能选项，允许启用或禁用某些特性
- VCPKG_VISUAL_STUDIO_PATH：设置 vcpkg 使用的 Visual Studio 的路径
- VCPKG_INSTALLED_DIR：
- VCPKG_PORTS：


cmake使用`CMAKE_TOOLCHAIN_FILE`变量关联`vcpkg.cmake`文件，从而使得vcpkg安装的第三方模块可被cmake使用

### 安装目录
```yaml
vcpkg:
    /docs:
    /installed: # 安装的第三方库
        /vcpkg:
        /x64-windows: # 分平台安装
            /bin:
            /debug:
            /include:
            /lib:
            /share:
    /packages:
    /ports: # 存放所有库源代码的地方(定义了如何从源代码编译和安装该库。这个文件会包含下载源代码、解压、配置、构建和安装等步骤)
    /scripts:
        /buildsystems:
            vcpkg.cmake: # 集成CMake
    /toolsrc:
    /triplets:
    /versions:
    vcpkg.exe:
```


#### cmake集成
```c

```


### vcpkg
```yaml
vcpkg:
    --version:
    add: # 添加第三方库，添加ports引用（项目级安装，修改vspkg.json），后续还需要手动install（安装到本地vcpkg_installed目录，同全局安装的installed目录）
        port:
    export:
        --lockfile:
    help:
    install: # 安装第三方库（用户级全局安装）
    integrate:  # 用户级、项目级 集成（默认用户级）
        install:
    list: # 查看已安装库
    new: # 新建vcpkg.json
        --application: # 
    remove: # 删除第三方库
    search:
    update:
```

包管理命令



#### vcpkg.json
```yaml
vcpkg.json:
    dependencies: # 依赖的第三方库 port
    description:
    name:
    version:
```


项目包配置文件



## 核心内容


### Ports

