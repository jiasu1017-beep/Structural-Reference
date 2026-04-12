# 5.11 协同仿真增强





**产品：** Abaqus/Standard  Abaqus/Explicit  Abaqus/CFD

**优势：** 多项增强功能，包括体积耦合支持、在壳单元两个面上交换热场以及为第三方客户端生成配置文件，提高了协同仿真技术的可用性。

**说明：** 以下协同仿真增强功能可用：
- Abaqus/Explicit 现在支持接口区域为体积的协同仿真。体积耦合允许耦合占据相同空间的物理场，如电磁-结构耦合的情况。
- 在 Abaqus/Standard 和 Abaqus/Explicit 中，现在可以在壳单元的 SPOS 和 SNEG 两个面上交换热场。在以前的版本中，热耦合仅支持 SPOS 或 SNEG 面。如果两面都加载，必须定义两个区域，一个包含 SPOS 面，另一个包含 SNEG 面。
- 在 SIMULIA Co-Simulation Engine 配置文件中，您可以指定在空间映射期间未找到交点的节点和元素的处理方式。您可以指定默认值或指定使用最近邻节点或元素的值。
- Abaqus/Standard 和 Abaqus/Explicit 的输入文件预处理器现在编写一个模型描述文件，其中包含协同仿真定义（如区域名称、场及其因果关系等）。此信息可供第三方客户端使用，以生成协同仿真配置文件，而无需解析 Abaqus 输入文件。
- SIMULIA Co-Simulation Engine 的运行时环境（Runtime Environment，RRE）现在支持版本控制。如果在 CSE director 或任何客户端中检测到不兼容的 RRE 库，协同仿真将终止并显示适当的消息。

**参考文献：**

**Abaqus Analysis User's Guide**
- ["准备用于协同仿真的 Abaqus 分析，" 第 17.2.1 节](../usb/usb-link.md#usb-anl-acosimulationprep)
