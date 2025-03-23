# OS_introduction

## Operating-System Structure
A common approach is to partition the task into small components, or modules, rather than have one single system. Each of these modules should be a well-defined portion of the system, with carefully defined interfaces and functions. 

## monolithic kernel

### define

![image-20250318103343581](https://naasi.oss-cn-shanghai.aliyuncs.com/image-20250318103343581.png)

Most of what is thought of as OS functionality is provided in these large kernels, including scheduling, file system, networking, device drivers, memory management, and more. 

Typically, a monolithic kernel is implemented as **a single process**, with all elements sharing the same address space. 

most of the operating system functionality runs inside the operating system kernel.

### monolithic kernel and monolithic system

This organization suggests a basic structure for the operating system:

1. A main program that invokes the requested service procedure.
2. A set of service procedures that carry out the system calls.
3. A set of utility procedures that help the service procedures.

![image-20250318101906915](https://naasi.oss-cn-shanghai.aliyuncs.com/image-20250318101906915.png)

this picture describes a simple model for a monolithic system.

The monolithic approach is often known as **a tightly coupled system** because changes to one part of the system can have wide-ranging effects on other parts.

### Layed OS

![image-20250318102321012](https://naasi.oss-cn-shanghai.aliyuncs.com/image-20250318102321012.png)

The first layer can be debugged without any concern for the rest of the system.

## micro-kernel

The main function of the microkernel is to provide communication between the client program and the various services that are also running in user space. Communication is provided through message passing, which was One benefit of the microkernel approach is that it makes extending the operating system easier, All new services are added to user space and conse-quently do not require modification of the kernel. 

![image-20250318103006126](https://naasi.oss-cn-shanghai.aliyuncs.com/image-20250318103006126.png)

## module

The idea of the design is for the kernel to provide core services, while
other services are implemented dynamically, as the kernel is running. Linking services dynamically is preferable to adding new features directly to the kernel which would require recompiling the kernel every time a change was made.

## virtual machine
The primary way the OS does this is through a general technique thatwe call virtualization. That is, the OS takes a physical resource (such asthe processor, or memory, or a disk) and transforms it into a more gen-eral, powerful, and easy-to-use virtual form of itself. Thus, we sometimes
refer to the operating system as a virtual machine.

![image-20250318104300639](https://naasi.oss-cn-shanghai.aliyuncs.com/image-20250318104300639.png)

Pushing this one step further, some operating systems virtualize the entire computer. running the operating system as an application on top of another operating system. This is called creating a virtual machine. The operating system running in the virtual machine, called the guest operating_system, thinks it is running on a real, physical machine, but this is an illusion presented by the true operating system running underneath.

## Exokernels

Its job is to allocate resources to virtual machines and then check attempts to use them to make sure no machine is trying to use somebody else's resources.

## System Boot

After an operating system is generated, it must be made available for use by the hardware. But how does the hardware know where the kernel is or how to load that kernel? The process of starting a computer by loading the kernel is known as booting the system. On most systems, the boot process proceeds as follows:

1. A small piece of code known as the bootstrap program or boot loader locates the kernel.
2. The kernel is loaded into memory and started.
3. The kernel initializes hardware.
4. The root file system is mounted.

