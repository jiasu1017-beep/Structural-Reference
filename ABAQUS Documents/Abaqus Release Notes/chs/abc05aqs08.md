# 5.8 车辆行驶舒适性和耐久性协同仿真





**产品：** Abaqus/Standard  Abaqus/Explicit

**优势：** 现在可以使用 Abaqus 和 FTire（来自 Cosin Scientific Software）进行车辆行驶舒适性和耐久性仿真。

**说明：** Abaqus 协同仿真技术与 FTire 结合使用，用于解决车辆在不平路面上机动的复杂舒适性和耐久性仿真。可以对加速、制动、滚动和打滑等机动进行建模。车辆及其悬架和车轮轮辋在 Abaqus 中建模。轮胎、道路以及轮胎在道路上的运动在 FTire（柔性环 tire 模型）中建模。Abaqus 计算与车辆在道路上行驶时由 FTire 计算的力和扭矩相关的位移和旋转。大多数 Abaqus 功能都可以使用，包括非线性材料、非线性几何效应、接触和连接器。复杂的轮胎现象在 FTire 中基于严格的机械、摩擦学和热力学原理进行解释。

Abaqus 和 FTire 的协同仿真由 SIMULIA 提供支持并通过 qualification。
**参考文献：**

**Abaqus Analysis User's Guide**
- ["协同仿真：概述，" 第 17.1.1 节](../usb/usb-link.md#usb-anl-acosimulationover)
- ["准备用于协同仿真的 Abaqus 分析，" 第 17.2.1 节](../usb/usb-link.md#usb-anl-acosimulationprep)
