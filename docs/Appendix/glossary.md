# 词汇表

!!! Failure "本文目前尚未完稿，存在诸多未尽章节且未经审阅，不是正式版本。"

**在本次 Linux101 介绍活动中，你会遇到许多可能从来没有概念的名词，为了便于大致理解概念与作为讲义辅助查阅，将涉及到的基本概念编写于此，正文可在适当位置加以引用。**

*部分词条并非使用专业而严格的方式解释，仅为快速理解而编写，更加严格的定义可参阅各大百科。*

## Whatis ...

### 操作系统 {#operating-system}

我们的计算机无时无刻不在同时管理着多个任务，运行着多个程序。然而对于只有单个单核 CPU 的计算机来说，正常情况下只能顺序执行一串代码，意味着多个程序总要以某种方式连接起来。
 
 CPU 的算力是程序的竞争资源之一，必须有一个管理者出现来保证资源分配的相对公平，这位管理者便是操作系统。
 
 操作系统本身也是程序，任务便是将应用程序接成一条线，自己负责切换程序，决定谁来使用 CPU，用多长时间。这样既能适配硬件的 CPU，满足其某一时刻只能执行一条指令的要求，也能促进应用程序合理运行，满足用户的功能需求。可见，操作系统的核心功能在于伺候程序。

那么，操作系统如何安排程序呢？这个问题在[第四章](../Ch04/index.md)有详细介绍。

### GNU：GNU is Not UNIX!<span style="font-size: smaller">（回音：...is not unix...is not unix...is not unix...）</span> {#gnu}

!!! tip 

    时间回到上世纪 70-80 年代，一代操作系统巨星 UNIX 在 AT&T 的商业化策略下选择了自闭，不再提供源代码给使用者。这不仅意味着金钱上的制约，更是一种对修改研究软件权力的制约。想想看，如果想对一个文本编辑器添加一个小功能，却由于版权原因被逼写一份自己的编辑器，可以说相当令人绝望。于是，Richard Stallman 带着他的 GNU Emacs 站了出来，号召 hacker 们搭建起自由的软件平台——GNU。

正如标题所见，GNU 的全称使用了一种递归，表达了与 Unix 这种对“自由”的限制决裂的态度。（虽然我一直在疑惑开头的 G 从哪来）

而进入 Linux 世界，便意味着将一直与 GNU 软件打交道。先看看一堆字母 g 开头的：gcc-C 编译器，gdb-程序调试器，gzip-压缩，gnome-桌面环境，gimp-图像编辑（对标 Photoshop），首字母 g 都是 gnu 的缩写；（当然 grep-查找，grab-启动引导程序不属此类。）我们 Linux 上的系统管理命令虽然未必以 g 开头，但都属于自由软件，默默地为 Linux 奉献着；还有[更多性能优异的软件 ↗](https://www.gnu.org/software/)，被自由软件爱好者维护、分享······加入 Linux，便是认同了这种极客精神与开源文化。

这里有一份[Redhat 公司制作的录音节目 command-line-heroes ↗](https://www.redhat.com/en/command-line-heroes)，纪念开源世界的历史与文化，对自己英语听力有自信的同学可以选择收听一下。

### Terminal / Console {#terminal}

还记得在 Unix 诞生之前由通用电器公司主持的 Multix 计划吗？对了，就是可以让用户把一套键盘显示器往墙上一插，直接连接到远端主机的计划。当时键盘和显示器连为一体，称为终端（terminal）。而主机自带的一套键盘与屏幕只能给系统管理员使用，称为控制台（<abbr title="con- 表强调，-sol 整体，词源同 solid —— 即构成一个整体，整体控制的工具。">console</abbr>），用来输出启动 debug 信息（现在的 Linux 系统如果因故障而不得不<abbr title="telinit 1">进入单用户修复模式</abbr>，则只有一个终端 `/dev/console` 开启）。

然而随着时代的发展，这种模式逐渐被家庭电脑的分布式主机取代，我们不需要，也没有多套终端了，只有显示器、键盘、鼠标。但是为了向前兼容性，我们需要假装这是一个（甚至多个）终端，所以一般发行版 `/dev` 目录下有 7 个终端 `tty1 ~ tty7`，通过 `ctrl + alt + F1 ~ F7` 切换键盘与显示器与哪个终端相对应。

再后来，随着时代发展，终端需要出现在图形界面上了，然而承载图形界面的也是终端，所以终端里的终端就需要终端模拟器来实现了。由此，出现在图形界面上的终端才叫终端模拟器。

[更多对于终端的理解↗](https://www.linuxdashen.com/%E4%BD%A0%E7%9C%9F%E7%9A%84%E7%9F%A5%E9%81%93%E4%BB%80%E4%B9%88%E6%98%AF%E7%BB%88%E7%AB%AF%E5%90%97%EF%BC%9F)

这里的终端与下面的 shell 经常被弄混，这里便澄清一下两者关系。

### Shell {#shell}

但凡使用 Linux，必然要与之交互。广义上讲，能与用户交互的程序都符合 shell 的定义（比如图形界面可以识别鼠标位置信息，点击操作和键盘快捷键）。然而 Linux 本身以命令行工具为主，而 shell 狭义上就是命令行解释工具，即允许用户在一定程度上 “说人话” 来调用程序。

如果发行版中根本没有 shell，计算机没有办法理解从键盘控制器发来的字符说的都是啥，系统也就不能为我所用了。所以，用好 shell，才能真正用懂 Linux。

没有图形界面时，shell 一般为控制台（tty）的子进程，在图形界面上 shell 建立在虚拟终端（pty —— pseudo tty）之上。顺带一提，ssh的父进程也是一个 pty。

### Kernel {#kernel}

有壳（shell）必有核（kernel），只有这里的核才是操作系统本体，真正负责调度程序，管理硬件的部分。而 Linux 发行版本身则是一个套装，意味着一个核用不同的软件包装出来，其中体现着发行版之间不同的理念。

### 中断（IRQ: Interrupt Request）[外链指南↗](https://www.ibm.com/developerworks/cn/linux/l-cn-linuxkernelint/index.html) {#irq}

你正在看书，被电话铃声打断，接完电话，继续读书。这里就很好地阐释了中断的基本原理：电话铃是中断的核心，电话号决定了是谁打来的，你要使用什么语言回应。

从程序的角度来看，中断对应着程序正常执行逻辑被打断，跳转到特定的中断处理程序。上面的电话铃代表是哪个硬件上产生的中断信号，告诉 CPU 应当如何处理。处理完之后自然回到正在运行的程序中（或者如果电话中老妈让你把饭热上，便对应 CPU 进行调度切换更高“优先级”任务的过程）。

在中断机制中，中断号与其处理程序的映射尤为重要，这些映射储存在中断向量<abbr title="一种数据结构，在 case 语句中用到">表</abbr>中。

没有中断，计算机仍将停留在批处理年代的早期，只能管理 IO，无法进行调度。

#### 时钟中断 {#clock-irq}

操作系统之所以可以单核多任务（并发），很大程度上是由于时钟中断的存在，时钟电路

中断向量的详细介绍，在此↗

### 系统调用（System Call） {#system-call}

如果说进程调度体现了系统进程与资源的管理作用，那么系统调用体现的是系统为进程提供服务的功能。操作系统既然提供了对硬件的抽象，那么必然要让程序去使用这些抽象。于是系统调用可以按照其提供的抽象分为针对进程的，针对文件的，针对内存的，针对用户的调用。除此之外还有网络管理以及调节操作系统自身的调用。我们所熟悉的 read，write 读写文件，更改文件各种权限；进程设置自身的gid，sid；甚至最简单的读取目录都经过系统调用。

显然这样做的目的之一是便于管理：要想让各个程序和平运行不抢设备的 IO，权力一定要上交到仲裁者手中。如果 A 的 IO 受到 B 的干扰，那么 A 的运行无法得到保证。只有操作系统为它们俩的 IO 排好先后顺序，才能保证它们顺利拿到数据。其次，各种权限信息与进程管理信息的修改显然不可以绕过操作系统。再者，类似于网络的这种相对较强的实时需求，必然需要操作系统的支持，没有哪个用户程序可以单独胜任。所以，系统调用是各用户进程“使用”操作系统的统一接口。

### POSIX 标准 {#posix}

### 内建命令 {#builtin-command}

```bash
$ whereis ls
$ whereis bg
```

### 文件描述符 {#file-descriptor}

## 另一些常用小命令

### alias

### .



### 四大查找

接触任何新事物时，都需要接触两类信息。一类是成体系的，循序渐进的指导信息（如本次101讲义），被筛选之后主动呈现；一类是碎片信息，需要自己主动搜集，搜集能力与手段便十分重要。

**不知你在遇到不清楚的概念时，有没有使用页面上方的搜索功能呢？**

#### locate

#### whereis

#### which

#### find（从略）

## 外部链接

本条目致力于提供成体系介绍 Linux 的其他网站的路径。

- [https://cyc2018.github.io/CS-Notes/#/notes/Linux](https://cyc2018.github.io/CS-Notes/#/notes/Linux)
虽然这是针对面试的速成，不过简洁性与通俗性符合初学者的认知。
