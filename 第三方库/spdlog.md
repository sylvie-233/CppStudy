# spdlog


## 基础介绍

一个高效、易用的 C++ 日志库
支持多线程、异步日志、日志级别、格式化等功能
`vcpkg install spdlog`


## 核心内容
```yaml
<spdlog/spdlog.h>:
    spdlog:
        sinks:
            basic_file_sink_st():
        basic_logger_mt(): # 创建日志记录器
        debug():
        info():
        set_default_logger():
        set_level():
        set_pattern(): # 设置输出格式
```