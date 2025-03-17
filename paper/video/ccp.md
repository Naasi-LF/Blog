# 计算机组成

## 计算机系统概述

### 冯诺依曼

![image-20250206175120151](https://naasi.oss-cn-shanghai.aliyuncs.com/image-20250206175120151.png)

输入，输出，控制器，运算器，存储器

### 硬件

CPU、主存、磁盘

![image-20250206175514012](https://naasi.oss-cn-shanghai.aliyuncs.com/image-20250206175514012.png)

### 性能

响应时间（个人户） / 吞吐率（带宽，单位时间内所需要完成的任务数量，数据中心）

性能 = 1 / 执行时间



### 时钟频率

时钟间隔的时间

每秒多少个时间周期 单位Hz  1/时间周期

1G = 10^3 M = 10^6K = 10^9

1s = 10^3 ms = 10^6 us = 10^9ns = 10^12 ps

例如 时钟周期250ps  时钟频率4GHz

手机 cpu 3.2GHz 每秒钟多少个时钟周期 

![image-20250207024704006](https://naasi.oss-cn-shanghai.aliyuncs.com/image-20250207024704006.png)

上升沿+下降沿   

频率越快越好  CPU执行的次数



### CPI

一个指令需要的**时间周期数**

CPU时间 = 指令数 * CPI * 时间周期时间



### MIPS  

每秒执行多少百万条指令数

MIPS = 指令数 / （指令时间 * 10^6）

CPU时间就是指令时间



### 过程

```shell
linux> gcc -o hello hello.c

```

源程序通过编译系统生成可执行程序

预处理 编译 汇编 链接

![image-20250207041318421](https://naasi.oss-cn-shanghai.aliyuncs.com/image-20250207041318421.png)

预处理 把include放进去

编译 生成汇编程序  核心

汇编  生成不可读的而进程文件

链接  链接一些库 例如print.o

## 整数

### Byte

一个字节  八个比特bit

八个比特 00000000~11111111 0~255

### Hex

![image-20250207162750509](https://naasi.oss-cn-shanghai.aliyuncs.com/image-20250207162750509.png)

0x开头

0x173A4C  

![image-20250207163811019](https://naasi.oss-cn-shanghai.aliyuncs.com/image-20250207163811019.png)

### 无符号数

![image-20250207164017509](https://naasi.oss-cn-shanghai.aliyuncs.com/image-20250207164017509.png)

X取值0和1 w位

### 有符号数

![image-20250207164234698](https://naasi.oss-cn-shanghai.aliyuncs.com/image-20250207164234698.png)

### 范围

![image-20250207164701853](https://naasi.oss-cn-shanghai.aliyuncs.com/image-20250207164701853.png)

![image-20250207164750570](https://naasi.oss-cn-shanghai.aliyuncs.com/image-20250207164750570.png)

### 强制转换

#### 无符号数有符号数

![image-20250207164934204](https://naasi.oss-cn-shanghai.aliyuncs.com/image-20250207164934204.png)

![image-20250207165011682](https://naasi.oss-cn-shanghai.aliyuncs.com/image-20250207165011682.png)

#### 无符号扩展

![image-20250207165134185](https://naasi.oss-cn-shanghai.aliyuncs.com/image-20250207165134185.png)

#### 有符号数扩展

根据符号位的数值

![image-20250207165227770](https://naasi.oss-cn-shanghai.aliyuncs.com/image-20250207165227770.png)

### 溢出

![image-20250207165357049](https://naasi.oss-cn-shanghai.aliyuncs.com/image-20250207165357049.png)

 减法可以转换加法

![image-20250207165753358](https://naasi.oss-cn-shanghai.aliyuncs.com/image-20250207165753358.png)

### 大端小端

![image-20250207170042347](https://naasi.oss-cn-shanghai.aliyuncs.com/image-20250207170042347.png)

### 左移右移

![image-20250207170144413](https://naasi.oss-cn-shanghai.aliyuncs.com/image-20250207170144413.png)

### 左移代替乘法

![image-20250207170404700](https://naasi.oss-cn-shanghai.aliyuncs.com/image-20250207170404700.png)

## 浮点数

小数 / 大形式数存储

### 浮点表示

![image-20250210185441159](https://naasi.oss-cn-shanghai.aliyuncs.com/image-20250210185441159.png)

![image-20250210185510644](https://naasi.oss-cn-shanghai.aliyuncs.com/image-20250210185510644.png)

![image-20250210192112436](https://naasi.oss-cn-shanghai.aliyuncs.com/image-20250210192112436.png)

1. 规格化的值
2. 非规格化的值  非常接近于0的数
3. 特殊值

![image-20250210192454360](https://naasi.oss-cn-shanghai.aliyuncs.com/image-20250210192454360.png)

![image-20250210192728698](https://naasi.oss-cn-shanghai.aliyuncs.com/image-20250210192728698.png)

![image-20250210192900239](https://naasi.oss-cn-shanghai.aliyuncs.com/image-20250210192900239.png)

![image-20250210193013291](https://naasi.oss-cn-shanghai.aliyuncs.com/image-20250210193013291.png)

![image-20250210193131849](https://naasi.oss-cn-shanghai.aliyuncs.com/image-20250210193131849.png)

![image-20250210193245439](https://naasi.oss-cn-shanghai.aliyuncs.com/image-20250210193245439.png)

![image-20250211165230747](https://naasi.oss-cn-shanghai.aliyuncs.com/image-20250211165230747.png)

![image-20250211165442924](https://naasi.oss-cn-shanghai.aliyuncs.com/image-20250211165442924.png)

对接阶码大的数

![image-20250211165618574](https://naasi.oss-cn-shanghai.aliyuncs.com/image-20250211165618574.png)

![image-20250211165737241](https://naasi.oss-cn-shanghai.aliyuncs.com/image-20250211165737241.png)

![image-20250212020000901](https://naasi.oss-cn-shanghai.aliyuncs.com/image-20250212020000901.png)

![image-20250212021321990](https://naasi.oss-cn-shanghai.aliyuncs.com/image-20250212021321990.png)

## 运算部件

![image-20250215203402377](https://naasi.oss-cn-shanghai.aliyuncs.com/image-20250215203402377.png)

![image-20250215203424203](https://naasi.oss-cn-shanghai.aliyuncs.com/image-20250215203424203.png)

![image-20250215203538267](https://naasi.oss-cn-shanghai.aliyuncs.com/image-20250215203538267.png)

-b = ~b +1

证明

X(1010) + ~X (0101) = 1111

因此 X + ~X = -1

-X = ~X + 1

![image-20250216235403605](https://naasi.oss-cn-shanghai.aliyuncs.com/image-20250216235403605.png)

![image-20250216235638657](https://naasi.oss-cn-shanghai.aliyuncs.com/image-20250216235638657.png)

## 内存

![image-20250217000014232](https://naasi.oss-cn-shanghai.aliyuncs.com/image-20250217000014232.png)

![image-20250217001948730](https://naasi.oss-cn-shanghai.aliyuncs.com/image-20250217001948730.png)

DRAM 不断的对电容进行充电

![image-20250217002325414](https://naasi.oss-cn-shanghai.aliyuncs.com/image-20250217002325414.png)

![image-20250217002439284](https://naasi.oss-cn-shanghai.aliyuncs.com/image-20250217002439284.png)

![image-20250217002809593](https://naasi.oss-cn-shanghai.aliyuncs.com/image-20250217002809593.png)

![image-20250217003157579](https://naasi.oss-cn-shanghai.aliyuncs.com/image-20250217003157579.png)

要两次的地址发送才能取到

先发行地址再发列地址

为什么要存在行和列

节约稀缺的引脚资源，可以节省一半的地址

1*16 要4位

4*4 只要2位

![image-20250217004143882](https://naasi.oss-cn-shanghai.aliyuncs.com/image-20250217004143882.png)

![image-20250217004543733](https://naasi.oss-cn-shanghai.aliyuncs.com/image-20250217004543733.png)



## Cache

![image-20250217174643564](https://naasi.oss-cn-shanghai.aliyuncs.com/image-20250217174643564.png)

### 直接映射

![image-20250217181408905](https://naasi.oss-cn-shanghai.aliyuncs.com/image-20250217181408905.png)

每一组只有一个Cache块

行数 = 组数

组选择

![image-20250217181552475](https://naasi.oss-cn-shanghai.aliyuncs.com/image-20250217181552475.png)

行匹配

查看是否有效

如果Vavid=1 有效 =0无效

查看Tag是否相等

字抽取

![image-20250217181854225](https://naasi.oss-cn-shanghai.aliyuncs.com/image-20250217181854225.png)

设置起始位置

### 组相连

![image-20250217182024396](https://naasi.oss-cn-shanghai.aliyuncs.com/image-20250217182024396.png)

![image-20250217182308215](https://naasi.oss-cn-shanghai.aliyuncs.com/image-20250217182308215.png)

### 全相连

只有一个组

![image-20250217182436853](https://naasi.oss-cn-shanghai.aliyuncs.com/image-20250217182436853.png)

### 写

写穿透 写到cache立马写到内存

写回 直到cache被替换的时候再写道内存



写分配 没有命中 先把内存中的数据放到cache

写不分配 直接写道内存

![image-20250217183007074](https://naasi.oss-cn-shanghai.aliyuncs.com/image-20250217183007074.png)

![image-20250217231349242](https://naasi.oss-cn-shanghai.aliyuncs.com/image-20250217231349242.png)



## 虚拟内存

具体见操作系统

## 指令系统

这是处理器能够直接识别并执行的机器指令的集合，也就是硬件层面能够理解的二进制代码。

![image-20250219163753514](https://naasi.oss-cn-shanghai.aliyuncs.com/image-20250219163753514.png)

中间代码 方便看

![image-20250219165115890](https://naasi.oss-cn-shanghai.aliyuncs.com/image-20250219165115890.png)

MIPS 32个  Intel x86-64 16个

### 字的概念

字长和寄存器大小相同 为32bit

决定了虚拟地址空间的最大大小

32位系统 32bit = 1word

32位系统 64bit = 1word

32位 双字  64位 四字

MIPS R型

 • 操作码（opcode）：6 位
  • 源寄存器（rs）：5 位
  • 源寄存器（rt）：5 位
  • 目标寄存器（rd）：5 位
  • 移位数（shamt）：5 位
  • 功能码（funct）：6 位

![image-20250219170449082](https://naasi.oss-cn-shanghai.aliyuncs.com/image-20250219170449082.png)

I型

- 操作码 (opcode)：6 位
- 第一个寄存器字段（通常是源寄存器 rs）：5 位
- 第二个寄存器字段（目标寄存器或另外一个源寄存器 rt）：5 位
- 立即数（immediate）：16 位

### 寻址操作

先要把数据放到寄存器里面

算术指令 缺点操作数的地址

分支跳转 确定指令的有效地址

操作数是寄存器 

操作数是常数字段

### 数据传送指令

在内存和寄存器之间怎么移动数据

取数 lw

存数 sw

![image-20250219172228143](https://naasi.oss-cn-shanghai.aliyuncs.com/image-20250219172228143.png)

![image-20250219172819603](https://naasi.oss-cn-shanghai.aliyuncs.com/image-20250219172819603.png)

相对地址 PC

直接地址

![image-20250219173827542](https://naasi.oss-cn-shanghai.aliyuncs.com/image-20250219173827542.png)

### x86

64 r

32 e

```cpp
;-----------------------------------------------
; Caller (main) 代码示例
; main 中使用 EAX 存放重要数据，
; 且 EAX 被视为 Caller Saved，func 可能修改 EAX，
; 所以需要在调用前保存 EAX 的值。
;-----------------------------------------------
main:
    mov  eax, 0x12345678   ; 把重要数据 0x12345678 载入 EAX
    push eax               ; 保存 EAX 的值到栈中

    call func              ; 调用被调用者函数 func

    pop eax                ; 从栈中恢复 EAX 的值

    ; 此时 EAX 依然是 0x12345678
    ; 后续代码可以安全使用 EAX 的值
    ret
        
        
;-----------------------------------------------
; Callee (func) 代码示例
; func 使用 EBX（属于 Callee Saved），因此必须保存 EBX 的值，
; 并在函数结束前恢复。
;-----------------------------------------------
func:
    push ebx            ; 保存 EBX 的原值（callee saved）

    ; 进行一些操作，示例中修改 EBX 的值
    mov  ebx, 0xDEADBEEF ; 给 EBX 赋予新的值
    ; 同时可以对 EAX、ECX、EDX 任意操作，
    ; 因为这些是 Caller Saved，调用者会负责保存恢复
    mov  eax, 0          ; 例如，将返回值存放在 EAX 中

    pop ebx             ; 恢复 EBX 的原值，保证调用者看到的 EBX 没有变化

    ret
```

寄存器 内存地址 立即数

两者操作数相反

`mov eax, [ebx]` 表示将内存地址由 `ebx` 指向的数据加载到 `eax` 中

![image-20250219181212825](https://naasi.oss-cn-shanghai.aliyuncs.com/image-20250219181212825.png)

专门寄存器去栈低位置

存器可以存储任意数据，比如数字或者地址。当寄存器存储的是一个数据值，而你需要直接操作这个值时，不用加中括号；而当寄存器存储的是一个地址，你希望访问这个地址指向的内存区域中的数据时，就需要使用中括号 [] 来表示内存访问。

![image-20250219182732355](https://naasi.oss-cn-shanghai.aliyuncs.com/image-20250219182732355.png)

### 处理器基本系统

![image-20250309220814222](https://naasi.oss-cn-shanghai.aliyuncs.com/image-20250309220814222.png)

![image-20250309220835357](https://naasi.oss-cn-shanghai.aliyuncs.com/image-20250309220835357.png)

CPU和内存通过总线连接 

总线：数据、控制、地址总线

读/写 通过控制总线发送内存

数据通过数据总线读数据 

地址通过地址总线

寄存器和ALU通过内部总线连接，通过总线进行数据交换，在CPU内部

通过 MDR 写入内存

![image-20250309221302966](https://naasi.oss-cn-shanghai.aliyuncs.com/image-20250309221302966.png)

 指令周期：

取指 ： 从内存中拿到指令

执行：解释操作码 执行操作

中断 如果允许中断 且中断发生 则保存进程状态（PC）并服务中断

不是直接寻址

add (1) 2 3

2是寄存器里面，1是内存地址，需要从内存里读取，要进行一次额外的内存访问的操作

MBR == MDR

![image-20250309222154488](https://naasi.oss-cn-shanghai.aliyuncs.com/image-20250309222154488.png)

![image-20250309222304026](https://naasi.oss-cn-shanghai.aliyuncs.com/image-20250309222304026.png)

中断 PC写到栈上面（内存上面）

栈的原因：中断回复

PC寄存器用来存储指向下一条指令的地址

处理器：数据通路和控制器

控制器的功能是负责协调并控制计算机各部件执行程序的指令序列，包括取指令、分析指令和执行指令；运算器的功能是对数据进行加工。

![image-20250309223526341](https://naasi.oss-cn-shanghai.aliyuncs.com/image-20250309223526341.png)

### 流水线

![image-20250309224050040](https://naasi.oss-cn-shanghai.aliyuncs.com/image-20250309224050040.png)

![image-20250309224310438](https://naasi.oss-cn-shanghai.aliyuncs.com/image-20250309224310438.png)

![image-20250309224444390](https://naasi.oss-cn-shanghai.aliyuncs.com/image-20250309224444390.png)

![image-20250309224533726](https://naasi.oss-cn-shanghai.aliyuncs.com/image-20250309224533726.png)

吞吐量: 一秒执行多少个指令

![image-20250309224958236](https://naasi.oss-cn-shanghai.aliyuncs.com/image-20250309224958236.png)

![image-20250309225341750](https://naasi.oss-cn-shanghai.aliyuncs.com/image-20250309225341750.png)

![image-20250309225548327](https://naasi.oss-cn-shanghai.aliyuncs.com/image-20250309225548327.png)

## 总线

![image-20250310205135189](https://naasi.oss-cn-shanghai.aliyuncs.com/image-20250310205135189.png)

![image-20250310210012216](https://naasi.oss-cn-shanghai.aliyuncs.com/image-20250310210012216.png)

![image-20250310210057947](https://naasi.oss-cn-shanghai.aliyuncs.com/image-20250310210057947.png)

![image-20250310210312145](https://naasi.oss-cn-shanghai.aliyuncs.com/image-20250310210312145.png)

![image-20250310224625837](https://naasi.oss-cn-shanghai.aliyuncs.com/image-20250310224625837.png)

![image-20250310224802747](https://naasi.oss-cn-shanghai.aliyuncs.com/image-20250310224802747.png)

![image-20250310224812338](https://naasi.oss-cn-shanghai.aliyuncs.com/image-20250310224812338.png)

仲裁：总线忙碌状态 等到空闲了才能响应发起请求的设备

CPU访问外设是如何寻址的

都是通过地址访问 统一编址

![image-20250310230253069](https://naasi.oss-cn-shanghai.aliyuncs.com/image-20250310230253069.png)

![image-20250310233057781](https://naasi.oss-cn-shanghai.aliyuncs.com/image-20250310233057781.png)

![image-20250310233323542](https://naasi.oss-cn-shanghai.aliyuncs.com/image-20250310233323542.png)

![image-20250310233817693](https://naasi.oss-cn-shanghai.aliyuncs.com/image-20250310233817693.png)

半同步：结合同步异步

![image-20250310234050102](https://naasi.oss-cn-shanghai.aliyuncs.com/image-20250310234050102.png)

ISA 工业标准总线

PCI 外部互联

![image-20250310234304693](https://naasi.oss-cn-shanghai.aliyuncs.com/image-20250310234304693.png)

IDE 磁盘硬盘

## IO

![image-20250312184505887](https://naasi.oss-cn-shanghai.aliyuncs.com/image-20250312184505887.png)

![image-20250312185815013](https://naasi.oss-cn-shanghai.aliyuncs.com/image-20250312185815013.png)

CPU如何访问IO端口的寄存器

1. 统一编址，CPU访问内存单元和外部寄存器对于CPU来说是一样的
2. 独立编址，单独的CPU指令

 ![image-20250312190802297](https://naasi.oss-cn-shanghai.aliyuncs.com/image-20250312190802297.png)

![image-20250312191232180](https://naasi.oss-cn-shanghai.aliyuncs.com/image-20250312191232180.png)

![image-20250312191245480](https://naasi.oss-cn-shanghai.aliyuncs.com/image-20250312191245480.png)

IO发出的中断都是可屏蔽中断

![image-20250312191549483](https://naasi.oss-cn-shanghai.aliyuncs.com/image-20250312191549483.png)

![image-20250312191828992](https://naasi.oss-cn-shanghai.aliyuncs.com/image-20250312191828992.png)

![image-20250312192516980](https://naasi.oss-cn-shanghai.aliyuncs.com/image-20250312192516980.png)

![image-20250312192709749](https://naasi.oss-cn-shanghai.aliyuncs.com/image-20250312192709749.png)

![image-20250312192952001](https://naasi.oss-cn-shanghai.aliyuncs.com/image-20250312192952001.png)

![image-20250312193019421](https://naasi.oss-cn-shanghai.aliyuncs.com/image-20250312193019421.png)

![image-20250312195636447](https://naasi.oss-cn-shanghai.aliyuncs.com/image-20250312195636447.png)

![image-20250312200115487](https://naasi.oss-cn-shanghai.aliyuncs.com/image-20250312200115487.png)
