# 5.9 使用 Abaqus 和 Dymola 进行逻辑-物理协同仿真





**产品：** Abaqus/Standard  Abaqus/Explicit

**优势：** 现在可以使用协同仿真来建模逻辑组件和物理组件之间的交互。您可以在 Dymola 中建模逻辑控制（电子设备）、电动机、气动设备或液压设备，并在 Abaqus 中建模机械、热和声学物理。

**说明：** 现在可以在逻辑建模软件 Dymola 和 Abaqus 之间使用协同仿真，以将控制电子设备或电气设备的建模与机械、热或声学建模结合在一起。在任何给定时间，Abaqus 中计算的传感器信息可以导出到 Dymola，Dymola 处理此信息以产生驱动。然后将驱动导入 Abaqus 以将模型驱动到所需状态。示例包括：
- 由电子控制的电动机（Dymola 中建模）驱动的机械臂（Abaqus 中建模），以实现有效载荷所需的路径
- 汽车 ABS 系统，其中轮胎（Abaqus 中建模）需要保持滚动运动（通过传感器检测），同时最大化制动扭矩（Dymola 中计算的驱动）
- 挖掘机械，如挖掘机（Abaqus 中建模），需要受控液压压力（Dymola 中计算）才能将其组件移动到所需效果

**参考文献：**

**Abaqus Analysis User's Guide**
- ["协同仿真：概述，" 第 17.1.1 节](../usb/usb-link.md#usb-anl-acosimulationover)
- ["准备用于协同仿真的 Abaqus 分析，" 第 17.2.1 节](../usb/usb-link.md#usb-anl-acosimulationprep)
- ["结构到逻辑协同仿真，" 第 17.4.1 节](../usb/usb-link.md#usb-anl-acosimabqtodym)

**Abaqus Keywords Reference Guide**
- [*CO-SIMULATION REGION](../key/key-link.md#usb-kws-hcosimulationregion)

**Abaqus Example Problems Guide**
- ["使用 Abaqus-Dymola 协同仿真分析扬声器，" 第 9.1.3 节](../exa/exa-link.md#exa-aco-cosimspeaker)
