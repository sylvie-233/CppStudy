# ASM

``

## 基础介绍

汇编


必备工具：
- x64dbg
- ollydbg
- ida
- ce


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



## 核心内容
```yaml
Register:
    EAX:
    EBX:
    ECX:
    EDX:
    EBP: # 栈基址指针寄存器
    ESP: # 栈顶指针寄存器 高到低 push：ESP减少（栈向低地址增长）pop：ESP增加（栈向高地址增长）。
    ESI:
    EDI:
    EIP: # 指令指针寄存器，当前运行地址
    EFLAGS: # 标志寄存器
    ST0: # 浮点栈（0-7）
    XMM0: # 浮点寄存器（0-7）

Command:
    add: # 加法
    call: # 函数调用
    cmp: # sub
    div: # EDX|EAX
    fadd: # 浮点加法运算
    fld: # 数据压入浮点栈中
    fstp: # 栈中数据存入内存
    idiv:
    imul:
    inc:
    jmp: # 直接跳转
    jne: # 不等于0跳转
    lea: # 取地址
    mul:
    mov: # 数据移动指令
    movss:
    nop: # 空指令
    or:
    pop: # 弹出栈
    popad:
    push: # 推入栈中
    pushad: # 寄存器全部压栈，保护寄存器、内存现场
    ret: # 函数返回，无条件跳转
    sub:
    test: # 0
```

SS栈段
CS代码段
DS数据段
ES附加段



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
将下一条执行指令地址压入栈中，并跳转到函数内部
ret自动弹栈，获取原执行地址

push传参：低字节先传
函数调用传参：从后往前传参（最后的参数最先传入）
ESP+4：函数的第一个参数

函数第一行`push ebp`、`mov ebp, esp`

栈上最上面的两个东西：函数返回地址、旧ebp
函数调用过程中：ebp指向旧ebp，ebp+4指向返回地址，ebp+8指向第一个参数




### DLL


windows默认加载DLL：
- 核心功能（如 ntdll.dll, kernel32.dll）
- GUI相关（如 user32.dll, gdi32.dll）
- 网络和安全（如 ws2_32.dll, secur32.dll）
- 多媒体（如 winmm.dll, dwmapi.dll）
- C运行库（如 msvcrt.dll, ucrtbase.dll）
- 系统Shell和Explorer相关（如 shell32.dll, shlwapi.dll）


字符串以`0`结尾