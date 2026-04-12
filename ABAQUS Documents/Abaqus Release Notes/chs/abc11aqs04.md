# 11.4 作业执行控制增强







**产品：**Abaqus/Standard  Abaqus/Explicit  Abaqus/CFD  

**优点：**您现在可以远程控制作业执行；以前，您需要在运行分析的机器上执行作业控制命令。此外，两个新的命令行选项可用于网络连接。

**说明：**作业执行控制的执行程序包括 **abaqus suspend**、**abaqus resume** 和 **abaqus terminate**。这些实用程序用于暂停、恢复和终止 Abaqus 分析作业。您现在可以远程执行这些命令；您不需要在运行分析的机器上执行这些命令。

**host** 和 **port** 选项分别用于指定运行分析作业的连接的主机名和端口号。您可以指定 **job** 选项或 **host** 和 **port** 选项来暂停、恢复或终止 Abaqus 分析作业。
**参考：**

**Abaqus Analysis User's Guide**
- ["Job execution control," Section 3.2.39](../usb/usb-link.md#usb-int-dsuspend)

