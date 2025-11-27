# vcpkg


## 基础介绍


C++包管理工具
- 经典模式：全局安装
- 清单模式：项目级别安装

安装步骤：clone github仓库，执行`bootstrap-vcpkg.bat`脚本


vcpkg环境变量：
- VCPKG_ROOT：设置 vcpkg 安装目录的根路径
- CMAKE_TOOLCHAIN_FILE: cmake集成vcpkg.cmake
- VCPKG_DEFAULT_TRIPLET：设置默认的 triplet（构建平台x64-windows）
- VCPKG_INSTALLATION_ROOT：设置 vcpkg 安装依赖库的根路径
- VCPKG_FEATURE_FLAGS：控制 vcpkg 的功能选项，允许启用或禁用某些特性
- VCPKG_VISUAL_STUDIO_PATH：设置 vcpkg 使用的 Visual Studio 的路径
- VCPKG_INSTALLED_DIR：
- VCPKG_PORTS：

- 默认第三方包安装到VCPKG_ROOT中
- cmake使用`CMAKE_TOOLCHAIN_FILE`变量关联`vcpkg.cmake`文件，从而使得vcpkg安装的第三方模块可被cmake使用
- install安装指定的triplet目标平台：vcpkg 不能自动识别你当前系统，而是你必须明确告诉它使用哪个 triple
- vcpkg的两种运行模式：manifest项目级安装、classic全局安装
- port定义了第三方包的本地管理配置
- vcpkg 的 installed 目录中，一个库在同一个 triplet 下只能存在一个版本（可通过自定义port、给库起别名解决）

### 安装目录
```yaml
vcpkg:
    /buildtrees:
    /docs:
    /downloads:
    /installed: # 安装的第三方库
        /vcpkg:
        /x64-windows: # 分平台安装
            /bin:
                <package>.dll:
                <package>.pdb:
            /debug:
                /bin:
                /lib:
            /include:
                /<package>: # 第三方包的头文件
            /lib:
                <package>.lib:
            /share:
                /<package>: # 安装的第三方包
    /packages:
    /ports: # 存放所有库源代码的地方(定义了如何从源代码编译和安装该库。这个文件会包含下载源代码、解压、配置、构建和安装等步骤)
    /scripts:
        /buildsystems:
            vcpkg.cmake: # 集成CMake
    /toolsrc:
    /triplets: # 平台相关
    /versions:
    vcpkg.exe:
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
        install: # 用户级安装
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

### Triplet

目标平台

### Port

port = 第三方库的“安装配方”，用于定义：
1. 库的来源（GitHub、源码压缩包等）
2. 编译方式（CMake、MSBuild、make）
3. 依赖关系（其他 port）
4. 安装路径（include、lib、bin、share）








