# ASM

`小迪x64dbg教程：P18`

## 基础介绍

汇编


MASM工具

32位程序地址偏移从`0040_0000`开始
- 镜像基址
- 代码基址
- 数据基址


### ml
```yaml
ml:

```

编译器



#### link
```yaml
link:

```

链接器


### DLL


windows默认加载DLL：
- 核心功能（如 ntdll.dll, kernel32.dll）
- GUI相关（如 user32.dll, gdi32.dll）
- 网络和安全（如 ws2_32.dll, secur32.dll）
- 多媒体（如 winmm.dll, dwmapi.dll）
- C运行库（如 msvcrt.dll, ucrtbase.dll）
- 系统Shell和Explorer相关（如 shell32.dll, shlwapi.dll）


字符串以`0`结尾

## 核心内容
```yaml
寄存器:
    EAX:
    EBX:
    ECX:
    EDX:
    EBP:
    ESP: # 栈顶指针寄存器 push：ESP减少（栈向低地址增长）pop：ESP增加（栈向高地址增长）。
    ESI:
    EDI:
    EIP: # 指令指针寄存器，当前运行地址
    EFLAGS: # 标志寄存器

指令:
    call: # 函数调用
    jmp: # 直接跳转
    jne: # 不等于0跳转
    mov: # 数据移动指令
    nop: # 空指令
    or:
    push:
    ret: # 函数返回，无条件跳转
```


### EFLAGS

标志寄存器
- ZF：零标志位，结果为0，则该位置1
- OF：溢出标志位
- CF：进位标志位
- PF：
- SF：符号标志位
- TF：
- AF：
- DF：方向标志位
- IF：


### call

函数调用

push传参：低字节先传
函数调用传参：从后往前传参（最后的参数最先传入）
ESP+4：函数的第一个参数