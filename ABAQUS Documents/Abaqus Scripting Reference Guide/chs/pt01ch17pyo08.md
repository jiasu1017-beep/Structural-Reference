# 17.8 GraphicsInfo 对象









GraphicsInfo 对象存储有关系统安装的图形适配器的信息。GraphicsInfo 对象没有构造函数或方法；Abaqus 在启动会话时创建 *GraphicsInfo* 成员。

如果您在远程系统上执行 Abaqus/CAE 并在本地显示主窗口，则 *glx 服务器* 是本地计算机，*glx 客户端* 是远程计算机。这种客户端和服务器的定义遵循 X11 命名约定。如果您在同一台机器上执行并显示 Abaqus/CAE，通常会看到服务器名称和客户端名称的相同值。

所有成员都是只读的。

**访问**

```
session.graphicsInfo
```

### 17.8.1 成员

GraphicsInfo 对象具有以下成员：

*glVersion*

类型为 (Int, Int, String) 的序列，指定 OpenGL 版本的三个组件。该序列由一个 Int（OpenGL 主版本号）、一个 Int（OpenGL 次版本号）和一个 String（任何附加信息）组成。

*glxServerVersion*

类型为 (Int, Int, String) 的序列，指定服务器 glx 版本的三个组件。该序列由一个 Int（glx 主版本号）、一个 Int（glx 次版本号）和一个 String（任何附加信息）组成。

*glxClientVersion*

类型为 (Int, Int, String) 的序列，指定客户端 glx 版本的三个组件。该序列由一个 Int（glx 主版本号）、一个 Int（glx 次版本号）和一个 String（任何附加信息）组成。

*glVendor*

一个 String，指定图形适配器供应商。在硬件加速系统上，*glVendor* 指定制造适配器的供应商。在没有硬件加速的系统上，*glVendor* 指定软件图形库的开发者。

*glRenderer*

一个 String，指定渲染设备的名称或软件图形库的名称。

*glxServerVendor*

一个 String，指定服务器端的 glx 开发者。

*glxClientVendor*

一个 String，指定客户端的 glx 开发者。





