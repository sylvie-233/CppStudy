# Croncpp


## 基础介绍

轻量级的 C++ 库，提供类 Unix Cron 语法支持，可以解析和执行定时任务


cron表达式
```
* * * * * <command to execute>
│ │ │ │ │
│ │ │ │ └─── 星期几 (0 - 7) (0 和 7 都代表周日)
│ │ │ └───── 月份 (1 - 12)
│ │ └─────── 日 (1 - 31)
│ └───────── 小时 (0 - 23)
└─────────── 分钟 (0 - 59)
```



## 核心内容
```yaml
<croncpp.h>:
    croncpp:
        cron:
            expression: # cron表达式
            scheduler: # 调度器
                schedule(): # 执行
                start(): # 开始
                stop(): # 停止
```