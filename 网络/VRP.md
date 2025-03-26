# VRP

`华为数通路由交换HCNA/HCIA：P30`

## 基础介绍


华为网络搭建模拟器


段 -> 包 -> 帧 -> 比特


## 核心内容
```yaml
eNSP:
    AR: # 路由器
        aaa: # aaa 认证模式
            local-aaa-user:
            local-user:
                password: # 登录密码
                    ciper: # 加密
                privilege: # 权限
                    level: # 权限级别
                service-type: # 可用服务 
                    telnet:
        acl:
        dhcp:
        dir:
        display:
            arp:
            http:
                server:
            interface: # 显示网络接口
                brief:
            ip:
                interface: # 查看 接口 ip
                routing-table: # 查看路由表
            mac-address:
            saved-configuration: # 保存的配置
            startup: # 查看系统启动配置参数
            telnet:
                server:
                    status:
            this: # 当前视图的运行配置
            users: # 登录用户
            version:
        ftp:
        interface: # 网络接口
            GigabitEthernet: # x/x/x  进入接口配置模式
            loopback: # 回环接口
                ip:
                    address: # 配置接口 IP 地址
                    route-static: # 配置静态路由
        ip:
            route-static: # 配置 静态路由
        nat:
        ntp-service:
        quit: # 退出
        ospf:
        save: # 保存 系统配置，vrpcfg.zip
        startup:
            saved-configuration:
            system-software:
        sysname: # 修改设备名称
        system-view:
        telnet:
            server:
                enable:
        tftp:
            get:
        user-interface: # 用户连接接口
            console:
            vty:
                authentication-mode: # 修改认证模式
                    aaa:
                    password:
                set:
                    authentication:
                        password: # 设置登录密码
                user:
                    privilege: # 设置用户权限
                        level:
        vlan:
```
![VRP命令行视图](../assets/VRP命令行视图.png)
- 用户视图
- 系统视图
- 接口视图
- 协议视图



![VRP命令级别](../assets/VRP命令级别.png)
- 访问级别
- 监控级别
- 配置级别
- 管理级别

认证级别
- password密码认证
- aaa用户名密码认证



### 交换机




### 路由器

任意两个接口不能配置相同网段的ip





路由表
- 最长匹配原则

路由表来源：
- 直连路由：路由器接口上的网络
- 静态路由：管理员手动添加的网络
- 动态路由：路由器之间动态学习到的网络

等价路由、负载均衡
缺省路由





#### RIP



#### OSTF








## 网络协议

### DNS

域名解析
应用层协议



### HTTP




### FTP


文件传输协议


### TFTP

简单文件传输协议


### SMTP


### POP3


### IMAP

类似POP3


### TELNET

远程连接


### TCP

传输层协议
基于port

![TCP协议](../assets/TCP协议.png)

三次握手
syn发给你的序列号、ack确认你给我的
两组syn、ack

累计确认机制、并不是每次对方的syn都必须回复ack
窗口大小机制：告知对方自己剩余窗口容量，用于流量控制

四次挥手ack、fin



### UDP

传输层协议
基于port


![UDP协议](../assets/UDP协议.png)


### ICMP
```yaml
icmp:
    0:
        0: # Echo Reply
    8:
        0: # Echo Request
```

网络层协议
消息控制协议、type、code



### IP

网络层协议
![IP包头](../assets/IP包头.png)

数据分片
TTL：生存事件

![IP地址分类](../assets/IP地址分类.png)
 
![私网IP地址](../assets/私网IP地址.png)

网络地址、主机地址、广播地址
单播、广播、组播
冲突域、广播域


### ARP

网络层协议
根据ip获取mac地址


### Ethernet

以太网协议、局域网组网技术

![以太网帧](../assets/以太网帧.png)
数据帧大小：64~1518
MTU: 46~1500
目标地址、源地址、类型、帧校验序列：18

数据链路层
- LLC子层
- MAC子层

MAC地址：48位、6字节