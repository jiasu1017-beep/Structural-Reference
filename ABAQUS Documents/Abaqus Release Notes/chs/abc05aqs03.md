# 5.3 SIMULIA Co-Simulation Engine API 可用性





**产品：** Abaqus/Standard  Abaqus/Explicit  Abaqus/CFD

**优势：** 允许您将内部代码与 Abaqus 求解器耦合的 SIMULIA Co-Simulation Engine API 现在随 Abaqus 介质一起正式发布。

**说明：** SIMULIA Co-Simulation Engine（CSE）API 允许您将内部代码与 Abaqus 求解器耦合。协同仿真和在客户端代码中嵌入 CSE API 面向熟悉 Abaqus、内部软件、协同仿真技术和编程的高级用户。我们鼓励您与当地的 SIMULIA 支持办公室讨论您的协同仿真需求。

CSE API 工具包随 Abaqus 介质一起分发。安装 Abaqus 时，CSE API 工具包安装在以下位置：

```
*install_dir*/api/cse/6.14-*x*_*platform*_CSE-api.zip
```
例如，如果您在 `C:\SIMULIA\Abaqus\6.14–1` 中安装 Abaqus 6.14，则 Windows 64 位平台的 CSE API 工具包位于以下位置：
```
C:\SIMULIA\Abaqus\6.14–1\api\cse\6.14-1_win86_64_CSE-api.zip
```
该 `.zip` 文件包含 CSE API 头文件、库、文档和示例问题。
**参考文献：**

**Abaqus Analysis User's Guide**
- [第 17 章，"协同仿真"](../usb/usb-link.md#usbcosim)

**Abaqus Installation and Licensing Guide**
- ["Abaqus 父目录，" 第 B.2 节](../sgb/sgb-link.md#sgb-chp-directories-abaqus)
