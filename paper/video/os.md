# OS

## 进程与线程

### 进程

> 进程：一个正在运行程序的抽象

widows: 图形界面

Linux: shell 输入命令

### 进程创建

Linux : fork() + execve()

Windows : CreateProcess()

父进程: shell  子进程 : hello

创建场景有:

1. 操作系统初始化
2. 程序创建进程 fork() ---父进程子进程
3. 用户请求 shell创建 ./hello
4. 批处理作业的初始化

### 进程地址空间

进程运行时，存在**独立**的虚拟地址空间。

【用户模式：代码段、数据段、堆（malloc）、用户栈（函数调用）、共享库】

【内核模式】

父进程产生子进程时候【shell: fork()】，子进程也需要虚拟地址空间，父进程子进程有**独立**的地址空间。

进程会是一种**树**的结构。

### 进程控制块/进程表

> 描述进程的状态的字段

结构体字段包括：寄存器 程序计数器 堆栈指针 进程状态 优先级调度 参数进程ID 父进程信号......

### 进程状态

CPU是一种资源，不是想用就能用

进程创建后，属于**就绪**队列，等待被（CPU）执行。

三种状态：

1. 运行：CPU当前执行当前代码进程
2. 阻塞：发生系统调用，例如read()读文件IO操作，对于CPU来说等很长时间。这时候进程便是阻塞状态。
3. 就绪：IO结束后，变为就绪

<img src="https://naasi.oss-cn-shanghai.aliyuncs.com/image-20250204195439132.png" alt="image-20250204195439132" style="zoom:67%;" />

### 进程终止

终止的几种情况：

* 正常退出 （自愿）
* 出错退出（自愿）--- 如果打开文件失败，则退出
* 严重错误 （非自愿）--- 除数为0 引用不存在
* 被其他进程杀死（非自愿）--- shell: kill 

### 跟踪状态

| 时间  | Process0 | Process1 | 注                             |
| ---   | ---      | ---      | ------------------------------ |
| 1     | 运行     | 就绪     |                                |
| 2     | 运行     | 就绪     |                                |
| 3     | 运行     | 就绪     |                                |
| 4     | 阻塞     | 运行     | Process0 发起 I/O              |
| 5     | 阻塞     | 运行     | Process0 被阻塞                |
| 6     | 阻塞     | 运行     | 所以 Process1 运行             |
| 7     | 就绪     | 运行     | I/O 完成                       |
| 8     | 就绪     | 运行     | Process1 现在完成              |
| 9     | 运行     | -        |                                |
| 10    | 运行     | -        | Process0 现在完成              |

### 调度指标

**周转时间**： 任务完成时间 - 任务到达系统的时间 （任务、工作、进程为同一种概念）

扩展： 周转时间其实是等待时间+执行时间，等待是在就绪队列的等待，执行时间是本任务执行的时间

周转时间是**性能**指标，另外一个指标是**公平**，与性能两者经常矛盾

### 调度算法

#### 先来先服务 

优点：简单易于理解

缺点：系统平均周期高

<img src="https://naasi.oss-cn-shanghai.aliyuncs.com/image-20250204205028068.png" alt="image-20250204205028068" style="zoom: 67%;" />

B、C虽然只有十秒，但是要等100秒

#### 最短任务优先

运行最短的任务，然后是次短的任务、

当**所有任务同时到达**时，最短任务优先是一个最优的调度算法

<img src="https://naasi.oss-cn-shanghai.aliyuncs.com/image-20250204221935771.png" alt="image-20250204221935771" style="zoom: 67%;" />

假设A在t=0到达 B、C 在t=10到达，平均时间多少秒。

<img src="https://naasi.oss-cn-shanghai.aliyuncs.com/image-20250204222526781.png" alt="image-20250204222526781" style="zoom: 80%;" />

#### 抢占式最短完成时间优先调度

比谁的**剩余时间**最少

<img src="https://naasi.oss-cn-shanghai.aliyuncs.com/image-20250204222807103.png" alt="image-20250204222807103" style="zoom:80%;" />

#### 高响应比优先调度算法

![image-20250204223153141](https://naasi.oss-cn-shanghai.aliyuncs.com/image-20250204223153141.png)

思考：和 **等待时间/执行时间**比值 相关

对于长作业 等待时间越长，相应比越高，越能克服饥饿。

#### 响应时间

> 任务到达系统首次运行的时间

响应时间 = 首次运行 - 到达时间

响应时间 = 等待时间

#### 时间片调度 （轮转调度）

每个进程被分配一个时间段，称为时间片，允许进程在该时间内执行。

时间片结束，该进程没有执行完，接下来CPU分配给另外进程执行。

![image-20250205005145809](https://naasi.oss-cn-shanghai.aliyuncs.com/image-20250205005145809.png)

如何确定时间片的长度？

假设进程切换1ms

时间片是4ms  20%浪费在管理开销

时间片是100ms 1%浪费在管理开销

时间片在20ms~50ms比较合理，既不能太小也不能太大

#### 多级反馈队列

每个队列有不同优先级

1. A>B 选择A
2. A=B 轮转运行AB
3. 最初放在最高
4. 一旦用完某个时间配额，优先级降低 【Q4 :C ,C时间配额20ms,结束后到Q3】
5. 一段时间后，所有工作加到优先级队列

思考题：加入用户代码不适用系统调用，CPU是不是一直在用户模式，无法切换内核模式？

或者说，假设用户使用循环打印一直占用CPU,是否一直处于用户态？

操作系统做进程调度（进程切换），进入内核模式

**时钟中断**，每个一段时间响应中断，会进入内核态进行进程切换。

### 进程切换

又叫上下文切换

1. 保存当前上下文（保存A）
2. 恢复之前被抢占进程的上下文（恢复B）
3. 将控制转给新恢复的进程

### 线程

> 一个应用存在多种活动

Word : 写交互 、自动保存

* 轻量级，容易创建（进程状态太多，代价大）
* 计算密集 --- 不能获得性能提升
* IO和计算 --- 多线程允许这些操作重叠执行（并行操作）

<img src="https://naasi.oss-cn-shanghai.aliyuncs.com/image-20250205022348896.png" alt="image-20250205022348896" style="zoom:80%;" />

### 线程访问

| 进程内容（共享） | 每个线程的内容（不共享） |
| ---------- | ---------- |
| 地址空间   | 程序计数器 |
| 全局变量   | 寄存器     |
| 打开文件   | 堆栈       |
| 子进程     | 状态       |
| 即将发生的报警 |            |
| 信号与信号处理程序 |            |
| 账户信息   |            |

### 线程包的实现

1. 用户管理线程 内核对线程一无所知

   内核来说是**单线程管理**

   可以在不支持线程的系统实现

2. 内核管理  创建和撤销代价

   a线程表在用户空间管理,b内核管理进程表

![image-20250205022840141](https://naasi.oss-cn-shanghai.aliyuncs.com/image-20250205022840141.png)



3. 混合实现

   <img src="https://naasi.oss-cn-shanghai.aliyuncs.com/image-20250205023125472.png" alt="image-20250205023125472" style="zoom:80%;" />

## 信号量

### 竞争条件

两个进程想同时访问共享内存

out 指向下一个打印机要打印的槽位 ， in 指向进程需要打印的文件的放入位置

当进程A B几乎在同一时刻发送文件

![image-20250205233809595](https://naasi.oss-cn-shanghai.aliyuncs.com/image-20250205233809595.png)



### 临界区

对**共享内存**进行访问的**程序片段**

![image-20250205234847705](https://naasi.oss-cn-shanghai.aliyuncs.com/image-20250205234847705.png)

1. 两个进程不处于一个临界区
2. 不能无限制等待临界区
3. 不应对CPU的速度和数量
4. 临界区外的进程不得阻塞其他进程

### 屏蔽中断

单处理器，进入临界区后，**屏蔽所有中断**。

CPU发生时钟中断和其他中断才能进行**进程切换**（没有办法切换内核态）

看似简单，但是用户态的进程是不能屏蔽中断的，权限不够

多核处理器，屏蔽中断只对屏蔽指令的CPU有效

对于内核态来说，是很方便的

### Peterson

```cpp
#define FALSE 0            // 定义 FALSE 为 0
#define TRUE 1             // 定义 TRUE 为 1
#define N 2                // 定义进程总数为 2

int turn;                  // 全局变量，表示当前轮到的进程
int interested[N];         // 表示进程是否有兴趣进入临界区，数组大小为进程数

// 进入临界区的函数
void enter_region(int process)
{
  int other;             
  other = 1 - process;     // 获取另一个进程的编号（当进程为 0 时，other 为 1；反之亦然）
  
  interested[process] = TRUE;  // 标记该进程有进入临界区的意愿
  turn = process;             // 设置当前进程为优先考虑
  // 当当前进程还是优先且另一个进程也有进入临界区的意愿时，保持等待
  while (turn == process && interested[other] == TRUE)
    ;
}

// 离开临界区的函数
void leave_region(int process)
{
  interested[process] = FALSE;  // 标记进程已经退出临界区
}
```

缺点，需要一直忙等



### TSL指令

将lock读到寄存器，再将lock写一个非零值，读和写不可分割

![image-20250206001924837](https://naasi.oss-cn-shanghai.aliyuncs.com/image-20250206001924837.png)

CPU锁住内存总线（归为独有），禁止其他CPU在本条指令结束前进行操作

本条指令是无法中断的

![image-20250206002400310](https://naasi.oss-cn-shanghai.aliyuncs.com/image-20250206002400310.png)

```bash
enter_region:
TSL REGISTER, LOCK
CMP REGISTER,#0
JNE enter_region
RET

leave_region:
MOVE LOCK,#0
RET
```



### Swap指令 / XCHG

```bash
enter_region:
MOVE REGISTER,#1
XCHG REGISTER, LOCK
CMP REGISTER,#0
JNE enter_region
RET
leave_region:
MOVE LOCK,#0
RET
```



三种算法的缺点，都需要进行等待。直到允许为止。



### 生产者消费者问题

两个进程共享缓冲区

生产者放数据，生产者产生数据

问题：生产者缓冲区放满了（生产者sleep）、消费者消耗的快缓冲区为空（消费者等待）

```cpp
#define N 100
int count = 0;
void producer(void)
{
    int item;
    while (TRUE) {
        item = produce_item();
        if (count == N) sleep();
        insert_item(item);
        count = count + 1;
        if (count == 1) wakeup (consumer);
    }
}
void consumer(void)
{
    int item;
    while (TRUE) {
        if (count == 0) sleep();
        item = remove_item();
        count = count - 1;
        if (count == N - 1) wakeup(producer);
        consume_item(item);
    }
}
```

极端情况：

当前缓冲区空了，消费者执行的时候count是否等于0，消费者暂停（执行变成就绪，并不是睡眠），生产者启动，唤醒消费者（生产者认为消费者睡眠），唤醒信号丢失。



### 信号量介绍

用整形变量记录唤醒次数

P 尝试 检查值是否大于0 减去1并继续 为0则睡眠

P操作检查数值，修改数值是**原子的**，是不可分割的

V 增加 对信号量加1 也是原子的

如何实现原子？ 

系统调用实现，单个CPU进行屏蔽中断，多个CPU通过TSL或Swap（PV操作时间非常短）

1. full 占用缓冲区的数量
2. empty  空缓冲区的数量
3. mutex 保证生产者和消费者互斥 确保不会同时访问缓冲区

```cpp
void producer(void)
{
    int item;
    while (TRUE) {
        item = produce_item();
        down(&empty);// P
        down(&mutex);// P
        // 上面两个操作是否能交换次序？
        // 如果缓冲区满了，会出现死锁，生产者先锁起来占有，然后睡眠。
        insert_item(item);
        up(&mutex);
        up(&full);
    }
}

void consumer(void)
{
    int item;
    while (TRUE) {
        down(&full);
        down(&mutex);
        item = remove_item();
        up(&mutex);
        up(&empty);
        consume_item(item);
    }
}
```

缺点：容易死锁，可读性差

## 同步问题

### 管程

把信号量和操作原语进行封装

把共享变量和共享变量的操作集合到一个模块

每次只有一个进程在管程内部

#### 方法

条件变量 x
wait signal操作

x.wait()  进程被挂起

x.signal() 进程被唤醒,没有挂起就没有意义



### 读者写者问题

一个飞机订票，允许多个用户查看分配，但是正在预定的客户必须拥有对数据库的独占访问。

读数据库多个进程可以，写数据库不行

```cpp
// 定义全局信号量和计数器，用于实现读写者问题的同步
semaphore mutex = 1; // 用于保护读者数量（rc）的互斥信号量
semaphore db = 1;    // 用于对数据库进行访问控制的信号量

int rc = 0; // 当前处于读者状态的线程计数

// 写者函数
void writer(void)
{
    while (TRUE) {
        think_up_data();   // 产生新的数据
        down(&db);         // 获取数据库使用权（进入临界区）
        write_data_base(); // 将数据写入数据库
        up(&db);           // 释放数据库使用权（退出临界区）
    }
}

// 读者函数
void reader(void)
{
    while (TRUE) {
        down(&mutex);      // 进入临界区，开始修改读者计数
        rc = rc + 1;       // 增加读者计数
        if (rc == 1) {     // 如果是第一个进入的读者，则锁定数据库，阻止写操作
            down(&db);
        }
        up(&mutex);        // 退出临界区
        
        read_data_base();  // 从数据库中读取数据
        
        down(&mutex);      // 进入临界区，开始修改读者计数
        rc = rc - 1;       // 读者计数减一
        if (rc == 0) {     // 如果最后一个读者离开，则释放数据库锁
            up(&db);
        }
        up(&mutex);        // 退出临界区
        
        use_data_read();   // 使用刚刚读取的数据
    }
}
```



### 哲学家就餐问题

两个动作，思考和吃饭

当一个哲学家饿了时，他试图分两次去取左边和右边的又子，每次拿一把，但不分次序。如果成功得到两把叉子，就开始吃饭，吃完饭后放下叉子继续思考。

<img src="https://naasi.oss-cn-shanghai.aliyuncs.com/image-20250206150142255.png" alt="image-20250206150142255" style="zoom:50%;" />

如果五位哲学家同时拿起了左边的叉子,那么就没有人能够拿到他们右边的叉子,于是发生死锁
修改上述解决方法: 拿到左叉子后, 检查右叉子是否可用, 如果不可用, 放下左叉子, 等待一段时间后, 重复这个过程。
可能在某个瞬间, 所有哲学家同时拿起了左叉子, 然后检查右叉子不可用, 又放下左叉子。如此永远重复下去。
所有程序都在不停的运行, 但是都无法取得进展, 称为饥饿。
可能想到的解决方法: 随机等待一段时间, 再拿右边的叉子。

解决方法：随机等待，但是还是会有极端情况

```CPP
// 哲学家编号，从 0 到 N-1
// 函数 take_forks 用于请求叉子，开始进餐
void take_forks(int i) {
  // 进入临界区，防止多个哲学家同时修改状态
  down(&mutex);
  
  // 将哲学家 i 的状态设置为 HUNGRY（饥饿）
  state[i] = HUNGRY;
  
  // 尝试检测是否可以开始进餐（检查左右邻居是否正在进餐）
  test(i);
  
  // 离开临界区
  up(&mutex);
  
  // 如果哲学家 i 无法获得叉子，将在此处阻塞，直到可以进餐
  down(&s[i]);
}

// 函数 test 检查哲学家 i 是否满足进餐条件
void test(int i) {
  // 如果哲学家 i 正处于饥饿状态，并且其左右邻居均不在进餐状态
  if (state[i] == HUNGRY && state[LEFT] != EATING && state[RIGHT] != EATING) {
    // 设置哲学家 i 的状态为 EATING（进餐）
    state[i] = EATING;
    
    // 释放哲学家 i，使其可以从阻塞状态中恢复，开始进餐
    up(&s[i]);
  }
}


void put_forks(i)
{
  down(&mutex);
  state[i] = THINKING;
  test(LEFT);
  test(RIGHT);
  up(&mutex);
}

void test(i)
{
  if (state[i] == HUNGRY && state[LEFT] != EATING && state[RIGHT] != EATING) {
    state[i] = EATING;
    up(&s[i]);
  }
}
```

## 死锁

多个进程争夺资源导致的僵局

A,B 分别将文档扫描后刻录到光盘上面

A在扫描仪 B在刻录机 谁也不让谁

### 资源

可抢占资源   抢占不会有副作用

如果缺页，从磁盘加载内存



不可抢占资源  无法抢夺的资源 

光盘刻录机刻录中抢占，会导致刻录失败



### 条件

互斥 

每个资源  分配中/空闲

请求和保持 （占有和等待）

保持一种资源，又提出新的资源，请求阻塞时，以获得的资源也保持不放

不可抢占

进程以获得的资源不能被强制性的抢占，只能使用完释放

环路等待

进程形成一条环路



### 死锁的恢复和检测

允许死锁发生，检测到发生时进行恢复

![image-20250207172810639](https://naasi.oss-cn-shanghai.aliyuncs.com/image-20250207172810639.png)

![image-20250207173038173](https://naasi.oss-cn-shanghai.aliyuncs.com/image-20250207173038173.png)

出现环路，发生死锁

 恢复

1. 允许抢占恢复 取决去资源类型
2. 回滚恢复 记录状态 镜像的保存
3. 杀死进程



### 资源轨迹图

![image-20250207174331884](https://naasi.oss-cn-shanghai.aliyuncs.com/image-20250207174331884.png)

走到红色里面后出现死锁

### 安全状态

![image-20250207174638272](https://naasi.oss-cn-shanghai.aliyuncs.com/image-20250207174638272.png)

BCA的调度去做 ， 是一个安全状态

### 不安全状态

![image-20250207175032627](https://naasi.oss-cn-shanghai.aliyuncs.com/image-20250207175032627.png)

不安全状态不一定是死锁

### 银行家算法

判断请求是否会导致不安全状态

如果是，则拒绝该请求

死锁避免从本质上是不可能的

进程数不固定，最大资源数不固定

### 死锁预防

**破坏互斥条件**

加入允许使用打印机 造成混乱

使用假脱机，允许多个进程同时产生输出

![image-20250208160449629](https://naasi.oss-cn-shanghai.aliyuncs.com/image-20250208160449629.png)

进程进入磁盘缓冲区，实现多进程共享功能，只申请打印机功能

**破坏请求和保持条件**

如果所需资源全部可用，那么进程运行结束

如果一个或多个正在被使用，那么不分配配，进程等待

当进程请求资源时候，先释放占有的所有资源，再尝试获取所有资源



**破坏不可抢占条件**

打印机：不可抢占-->可共享

将设备虚拟化，避免发生混乱

假设一个进程分配到了一台打印机，正在打印输出。如果他需要的绘图仪无法获得，强制性的把它占有的打印机占掉，会引起混乱

不过 并不是所有资源都可以进行类似的虚拟化



**破坏环路**

如果是一个很耗时的IO操作再释放资源，这是不可接收的

 ## 虚拟内存

物理寻址

![image-20250208162619818](https://naasi.oss-cn-shanghai.aliyuncs.com/image-20250208162619818.png)

虚拟寻址

![image-20250208162649881](https://naasi.oss-cn-shanghai.aliyuncs.com/image-20250208162649881.png)

 

MMU  地址转换器

### 地址空间

![image-20250208163003884](https://naasi.oss-cn-shanghai.aliyuncs.com/image-20250208163003884.png)

虚拟地址：8位，32位

物理地址：内存条，4GB 8GB

![image-20250208163504072](https://naasi.oss-cn-shanghai.aliyuncs.com/image-20250208163504072.png)

![image-20250208163632572](https://naasi.oss-cn-shanghai.aliyuncs.com/image-20250208163632572.png)

可执行程序被赋予了虚拟地址

虚拟地址   每个进程认为独占

![image-20250208164000715](https://naasi.oss-cn-shanghai.aliyuncs.com/image-20250208164000715.png)

![image-20250208164119492](https://naasi.oss-cn-shanghai.aliyuncs.com/image-20250208164119492.png)

### 虚拟页

虚拟地址和物理地址存在对应关系   

4KB 虚拟页大小和物理页一致

 

![image-20250208164506749](https://naasi.oss-cn-shanghai.aliyuncs.com/image-20250208164506749.png)

Cached 在虚拟内存中并映射

Uncached 没有在物理页但在磁盘中

Unallocated 未分配的 磁盘中也没有

如何记录虚拟页和物理页的对应？

![image-20250208165128837](https://naasi.oss-cn-shanghai.aliyuncs.com/image-20250208165128837.png)

1 虚拟页i在物理页中

0 表示不在 缺页

例如PTE7 缓存VP7在内存中 页表的地址为物理的地址



###  转换

虚拟地址分为两部分：

虚拟页号 (20bit)

虚拟页偏移量 （12 bit  4KB）

  ![image-20250209203358171](https://naasi.oss-cn-shanghai.aliyuncs.com/image-20250209203358171.png)

  ![image-20250209204102238](https://naasi.oss-cn-shanghai.aliyuncs.com/image-20250209204102238.png)

 ### 多级页表

如果每个进程都有一个页表消耗太大，因此用多级页表

![image-20250209204342381](https://naasi.oss-cn-shanghai.aliyuncs.com/image-20250209204342381.png)

![image-20250209204932365](https://naasi.oss-cn-shanghai.aliyuncs.com/image-20250209204932365.png)



一种选择,在程序执行时将整个程序加载到物理内存   问题是,最初可能不需要整个程序都处于内存  

仅在需要时才加载页面,这种技术被称为请求调页   对于请求调页的虚拟内存,页面只有在程序执行期间被请求  时才被加载。因此,从未访问的页从不加载到物理内存中。

### 缺页

![image-20250209205501176](https://naasi.oss-cn-shanghai.aliyuncs.com/image-20250209205501176.png)

如何去选择牺牲页？

## 页面调度算法

### FIFO

最先进入物理内存的页面放在表头  最晚的在链表尾部

缺页中断时，把新的页面插在尾部

Belady异常

![image-20250210171247040](https://naasi.oss-cn-shanghai.aliyuncs.com/image-20250210171247040.png)

![image-20250210171323506](https://naasi.oss-cn-shanghai.aliyuncs.com/image-20250210171323506.png)

### 最优页面置换 OPT

![image-20250210171510454](https://naasi.oss-cn-shanghai.aliyuncs.com/image-20250210171510454.png)

### 最近最少使用 LRU

置换未使用时间最长的页面

最近最多的在表头

最近最少的表尾

缺点 每次访问内存都要更新整个链表

### 时钟页面置换（最实用）

![image-20250210173447400](https://naasi.oss-cn-shanghai.aliyuncs.com/image-20250210173447400.png)

改进时钟页面算法

（访问位，修改位）

![image-20250210173755181](https://naasi.oss-cn-shanghai.aliyuncs.com/image-20250210173755181.png)

给进程分配的页数？

### 页面分配

固定/可变分配 局部/全局置换

![image-20250210175054536](https://naasi.oss-cn-shanghai.aliyuncs.com/image-20250210175054536.png)

固定分配和全局分配同时不存在

### 分段

分段不是分页

页面是定长的  12/4KB  10/1KB

段不是固定的

和分页类似

段号 + 段内地址

## 文件

### 存储结构

三种结构：字节序列（txt word）、记录序列（组织文件的一种结构）、树（检索快）

### 类型

Linux -- 一切皆文件

普通文件 ASCII、二进制（乱码）

目录文件 文件夹

特殊文件 字符特殊文件（键鼠）、块特殊文件（Disk）

### 文件访问

顺序访问

从文件开始按顺序全部访问

随机访问

通过任何次序读---数据库

### 文件属性（元数据）

 ![image-20250210182322948](https://naasi.oss-cn-shanghai.aliyuncs.com/image-20250210182322948.png)

### 磁盘分配空间

有效利用磁盘空间 提高文件的访问速度

连续分配

![image-20250210182716548](https://naasi.oss-cn-shanghai.aliyuncs.com/image-20250210182716548.png)

链接分配

![image-20250210183439517](https://naasi.oss-cn-shanghai.aliyuncs.com/image-20250210183439517.png)

索引分配

![image-20250210183832177](https://naasi.oss-cn-shanghai.aliyuncs.com/image-20250210183832177.png)

![image-20250210184646117](https://naasi.oss-cn-shanghai.aliyuncs.com/image-20250210184646117.png)

### 文件操作

![image-20250212180506455](https://naasi.oss-cn-shanghai.aliyuncs.com/image-20250212180506455.png)

![image-20250213173024114](https://naasi.oss-cn-shanghai.aliyuncs.com/image-20250213173024114.png)

文件控制块和文件一一对应

![image-20250213173227738](https://naasi.oss-cn-shanghai.aliyuncs.com/image-20250213173227738.png)

存储文件的元信息

1. 创建文件
2. 读文件
3. 写文件
4. 删除文件
5. 截断文件

C语言的库函数封装了系统调用

![image-20250213173607028](https://naasi.oss-cn-shanghai.aliyuncs.com/image-20250213173607028.png)

通过文件描述符进行读写

### 目录文件

文件夹

记录文件的位置

```cpp
struct dirent{
    ino_t d_ino;
    char d_name[256];
}
```

![image-20250213173946698](https://naasi.oss-cn-shanghai.aliyuncs.com/image-20250213173946698.png)

### 链接

目录中每个名字到索引节点的链接

硬链接

![image-20250213174930370](https://naasi.oss-cn-shanghai.aliyuncs.com/image-20250213174930370.png)

在磁盘上面只存储了一份

软链接

![image-20250213175414182](https://naasi.oss-cn-shanghai.aliyuncs.com/image-20250213175414182.png)

### 当前目录

解析相对路径时，会把当前工作目录作为起点

### 空闲空间管理

维护一个空闲所有空闲的空间

文件 目录文件都存储在磁盘上面

## 磁盘

### 基本结构

![image-20250213180123725](https://naasi.oss-cn-shanghai.aliyuncs.com/image-20250213180123725.png)

![image-20250213180505930](https://naasi.oss-cn-shanghai.aliyuncs.com/image-20250213180505930.png)

柱面 磁道 扇区 提供一个三元组 物理位置

扇区与扇区之间有间隙

### 磁盘格式化

低级格式化/物理格式化

![image-20250213181026248](https://naasi.oss-cn-shanghai.aliyuncs.com/image-20250213181026248.png)

逻辑格式化

![image-20250213181218426](https://naasi.oss-cn-shanghai.aliyuncs.com/image-20250213181218426.png)

### 访问时间

寻道时间 （寻找正确的磁道）比较长

旋转时间 盘片的旋转

磁盘带宽  传输时间

### 磁盘调度算法

#### FCFS调度

![image-20250213181731201](https://naasi.oss-cn-shanghai.aliyuncs.com/image-20250213181731201.png)

#### SSTF

![image-20250213181910325](https://naasi.oss-cn-shanghai.aliyuncs.com/image-20250213181910325.png)

#### SCAN

电梯算法

![image-20250213182112938](https://naasi.oss-cn-shanghai.aliyuncs.com/image-20250213182112938.png)

#### C-SCAN

变种

不处理回程的请求 立即返回到磁盘的开头

![image-20250213182319550](https://naasi.oss-cn-shanghai.aliyuncs.com/image-20250213182319550.png)

## 设备管理

### 控制方式

* 程序IO方式
* 中断驱动IO
* 直接内存访问
* 通道控制

### 软件原理

设备独立性

访问IO设备不指定设备类型 ==> 用read读文件 不需要指定文件在磁盘还是U盘等

![image-20250214173130212](https://naasi.oss-cn-shanghai.aliyuncs.com/image-20250214173130212.png)

### 驱动程序

IO设备需要特定代码来控制 设备驱动程序

![image-20250214173359420](https://naasi.oss-cn-shanghai.aliyuncs.com/image-20250214173359420.png)

### 与设备无关的

公共的IO功能

统一的接口

![image-20250214173844686](https://naasi.oss-cn-shanghai.aliyuncs.com/image-20250214173844686.png)

### 缓冲

减少CPU的中断频率

![image-20250214174440048](https://naasi.oss-cn-shanghai.aliyuncs.com/image-20250214174440048.png)

### 执行流程

![image-20250214174611007](https://naasi.oss-cn-shanghai.aliyuncs.com/image-20250214174611007.png)