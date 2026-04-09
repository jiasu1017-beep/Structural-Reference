# 12.12 Abaqus/Standard与Abaqus/Explicit的兼容性

---

Abaqus/Standard和Abaqus/Explicit的机械接触算法存在根本性差异。这些差异反映在接触条件的定义方式上。主要差异如下：

- 对于接触对，Abaqus/Standard默认情况下通常对接触约束使用纯主-从关系（请参阅《Abaqus分析用户指南》的"在Abaqus/Standard中定义接触对"第36.3.1节）；从表面的节点被约束不得穿透主表面。从表面的节点可以穿透主表面（理论上）。Abaqus/Explicit包含此公式，但通常默认使用平衡主-从权重（请参阅《Abaqus分析用户指南》的"在Abaqus/Explicit中接触对的接触公式"第38.2.2节）。
- Abaqus/Standard和Abaqus/Explicit的接触公式在许多方面有所不同。例如，Abaqus/Standard提供面-面公式，而Abaqus/Explicit提供边-边公式。
- Abaqus/Standard和Abaqus/Explicit的约束施加方法在某些方面有所不同。例如，Abaqus/Standard和Abaqus/Explicit都提供罚函数约束方法，但默认的罚刚度不同。
- Abaqus/Standard和Abaqus/Explicit都提供小滑动接触公式（请参阅《Abaqus分析用户指南》的"在Abaqus/Standard中的接触公式"第38.1.1节，以及《Abaqus分析用户指南》的"在Abaqus/Explicit中接触对的接触公式"第38.2.2节）。但是，Abaqus/Standard的小滑动接触公式根据从节点的当前位置将载荷传递到主节点。Abaqus/Explicit始终通过锚点传递载荷。

由于这些差异，在Abaqus/Standard分析中指定的接触定义不能导入到Abaqus/Explicit分析中，反之亦然（请参阅《Abaqus分析用户指南》的"在Abaqus/Explicit和Abaqus/Standard之间传输结果"第9.2.2节）。
