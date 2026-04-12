# 5.10 SIMULIA Co-Simulation Engine 增强





**产品：** Abaqus/Standard  Abaqus/Explicit

**优势：** SIMULIA Co-Simulation Engine 已增强，允许定义多个协同仿真区域并提供配置文件升级功能。

**说明：** SIMULIA Co-Simulation Engine 现在支持多个区域和多个场，用于 Abaqus/Standard 和 Abaqus/Explicit 与某些合作伙伴产品的耦合。客户端可以指定一个或多个区域作为其协同仿真接口。协同仿真接口区域可以是离散点集、曲面区域、体积区域或这些类型的混合。客户端之间的对应区域必须具有相同的区域类型、共定位并具有相同的区域边界。

多个区域可用于：
- 在不同的协同仿真接口上传输不同的场类型
- 点、曲面区域和体积区域之间的耦合
- 在预期存在映射困难的复杂几何区域中分配不同的搜索和映射容差

CSE director 进程可以自动从以前的版本升级配置文件的 schema。
**参考文献：**

**Abaqus Analysis User's Guide**
- ["SIMULIA Co-Simulation Engine director 执行，" 第 3.2.3 节](../usb/usb-link.md#usb-int-dcosimcontrolproc)
- ["协同仿真：概述，" 第 17.1.1 节](../usb/usb-link.md#usb-anl-acosimulationover)
