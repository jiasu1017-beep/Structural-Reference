# 47.8 NetworkDatabaseConnector 对象





NetworkDatabaseConnector 对象允许您访问远程系统上的输出数据库。

**访问**

```
session.networkDatabaseConnectors[*name*]
```

### 47.8.1 NetworkDatabaseConnector(...)

此方法创建 NetworkDatabaseConnector 对象，可用于访问远程输出数据库。您可以从任何平台创建网络数据库连接器：Windows、UNIX 或 Linux。但是，网络数据库连接器服务器必须位于 UNIX 或 Linux 平台上；您无法访问位于远程 Windows 系统上的输出数据库。您只能访问远程输出数据库；无法访问远程模型数据库。

**路径**

```
session.NetworkDatabaseConnector
```

**必要参数**

*name*

String，指定存储库键。

*hostName*

String，指定远程计算机的名称。

*directory*

String，指定远程计算机上的目录。

**可选参数**

*remoteAbaqusDriverName*

String，指定在远程计算机上执行 Abaqus/CAE 的命令名称。

*remoteLoginMechanism*

SymbolicConstant，指定本地系统上的远程 shell 命令。可能的值为 RSH 和 SSH。默认值为 RSH。

*sshPath*

String，指定本地系统上 `ssh` 命令的路径。默认值为空字符串。

*serverPort*

Int，指定远程计算机上的服务器端口。如果 *serverPort* =0，则允许主机和远程系统建立自己的端口号。默认值为 0。

*connectionPort*

Int，指定远程计算机上的连接端口。默认值为 0。

*serverTimeout*

Int，指定远程服务器的超时时间（以秒为单位）。例如：86400 对应一天。如果服务器在指定时间内未收到来自客户端的任何通信，则服务器退出。默认值为 86400。

*allowAutomaticStartup*

Boolean，指定是否启动远程网络数据库连接器服务器。默认值为 ON。

**返回值**

NetworkDatabaseConnector 对象。

**异常**

无。

### 47.8.2 start(...)

此方法在远程主机上启动远程网络数据库连接器服务器。

**必要参数**

无。

**可选参数**

*serverPort*

Int，指定远程计算机上的服务器端口。如果 *serverPort* =0，则允许主机和远程系统建立自己的端口号。默认值为 0。

*serverTimeout*

Int，指定远程服务器的超时时间（以秒为单位）。例如：86400 对应一天。如果服务器在指定时间内未收到来自客户端的任何通信，则服务器退出。默认值为 86400。

**返回值**

无

**异常**

无。

### 47.8.3 stop()

此方法在远程主机上停止远程网络数据库连接器服务器。

**参数**

无。

**返回值**

无

**异常**

无。

### 47.8.4 setValues(...)

此方法修改 NetworkDatabaseConnector 对象。

**必要参数**

无。

**可选参数**

`setValues` 的可选参数与 [NetworkDatabaseConnector](pt01ch47pyo08.md#ker-networkdatabaseconnector-networkdatabaseconnector-pyc) 方法的参数相同，但 *name* 参数除外。

**返回值**

无

**异常**

无。

### 47.8.5 成员

NetworkDatabaseConnector 对象的成员与 [NetworkDatabaseConnector](pt01ch47pyo08.md#ker-networkdatabaseconnector-networkdatabaseconnector-pyc) 方法的参数具有相同的名称和描述。

此外，NetworkDatabaseConnector 对象具有以下成员：

*connected*

Boolean，指定客户端与服务器之间的连接是否已建立。


