# 5.12 MpCCI 与 SIMULIA Co-Simulation Engine 的连接器





**产品：** Abaqus/Standard  Abaqus/Explicit

**优势：** SIMULIA Co-Simulation Engine 现在支持与 MpCCI 的接口，扩展了可与 Abaqus 耦合的第三方求解器数量。

**说明：** 在 Abaqus 6.14 发布之前，MpCCI 客户端软件嵌入在 Abaqus/Standard 和 Abaqus/Explicit 中。从 Abaqus 6.14 版本开始，Fraunhofer SCAI 开发了 MpCCI 服务器与 SIMULIA Co-Simulation Engine 之间的连接。此连接将协同仿真功能扩展到可与 Abaqus 耦合的非合作伙伴、MpCCI 兼容求解器。此连接器支持 SIMULIA Co-Simulation Engine 的最新功能，包括隐式迭代耦合。

连接器进程由 Fraunhofer SCAI 分发。有关 MpCCI 的更多信息，请参阅 [www.mpcci.de](http://www.mpcci.de)。有关与第三方软件耦合的更多信息，请参阅 [www.3ds.com/simulia](http://www.3ds.com/simulia) 上的[协同仿真](http://www.3ds.com/support/certified-hardware/simulia-system-information/compatibility/co-simulation/)页面。

通过 MpCCI 与 Abaqus 的第三方代码耦合由 Fraunhofer SCAI 提供支持并通过 qualification。
**参考文献：**

**Abaqus Analysis User's Guide**
- ["协同仿真：概述，" 第 17.1.1 节](../usb/usb-link.md#usb-anl-acosimulationover)
