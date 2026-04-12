# 8.3 基于SIM的分析过程的声学基础运动







**产品：**Abaqus/Standard  

**优点：**您现在可以将具有 prescribed 压力值的声学介质与模式分析中不同约束点的不同值一起使用（类似于直接解稳态动态分析中的功能）。此功能在汽车行业中有用；例如，用于分析消音器和燃油箱。

**说明：**声压基础运动在模态SIM基瞬态动态和稳态动态（包括子空间投影）分析中作为"secondary"基实现。

为了在模态分析中启用非零边界条件，Abaqus 使用"big mass"方法。从数学上讲，这是惩罚方法的一种变体。Abaqus 使用 secondary 基运动来支持模态过程中的非零边界条件。Named secondary 基通过在频率提取步骤中指定边界条件来定义。在连续的模态分析步骤中，这些边界条件可以与幅值曲线关联并作为基础运动应用。您现在可以将 secondary 基运动应用于声压自由度8；在以前的版本中，您只能将 secondary 基运动应用于机械自由度（1-6）。由于声学激励是一个标量值（与机械自由度相反），因此节点的方向无关紧要。

声压基础运动已为以下模型实现：
- 仅声学介质
- 组合声学和结构介质；非耦合模式
- 组合声学和结构介质；耦合模式（仅限模态稳态动态，包括子空间投影，分析）

**参考：**

**Abaqus Analysis User's Guide**
- ["Dynamic analysis procedures: overview," Section 6.3.1](../usb/usb-link.md#usb-anl-adynamicproc)
- ["Prescribed motions in modal superposition procedures" in "Transient modal dynamic analysis," Section 6.3.7](../usb/usb-link.md#usb-anl-amodaldynamic-motion)

**Abaqus Keywords Reference Guide**
- [*BASE MOTION](../key/key-link.md#usb-kws-hbasemotion)

