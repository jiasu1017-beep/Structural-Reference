# 7.2 阻尼

如果允许无阻尼结构自由振动，振动的幅度保持不变。然而在现实中，能量通过结构的运动被耗散，振动幅度会逐渐减小直至停止。这种能量耗散称为阻尼。阻尼通常假定为粘性阻尼或与速度成正比。动力平衡方程可以重写为包含阻尼的形式：

![d0](../graphics/gsk_eqn00090.gif)

![d0](../graphics/gsk_eqn00110.gif)

其中：

*C* 是结构的阻尼矩阵

![gsk_eqn00111.gif](../graphics/gsk_eqn00111.gif) 是结构的速度

能量的耗散是由多种效应引起的，包括结构关节处的摩擦和局部材料滞后。阻尼是一种便捷的方式，可以在不详细建模各效应的情况下包含重要的能量吸收。

在Abaqus/Standard中，无阻尼系统的特征模态被计算出来，然而大多数工程问题都涉及某种形式的阻尼，无论多么小。阻尼固有频率与每个模态的无阻尼固有频率之间的关系为：

![d0](../graphics/gsk_eqn00112.gif)

其中：

![gsk_eqn00113.gif](../graphics/gsk_eqn00113.gif) 是阻尼特征值

![gsk_eqn00114.gif](../graphics/gsk_eqn00114.gif) 是阻尼比，即临界阻尼的分数

*c* 是该模态形状的阻尼

![gsk_eqn00115.gif](../graphics/gsk_eqn00115.gif) 是临界阻尼

对于小的 ![gsk_eqn00116.gif](../graphics/gsk_eqn00116.gif) 值（![gsk_eqn00117.gif](../graphics/gsk_eqn00117.gif) < 0.1），阻尼系统的固有频率非常接近无阻尼系统的相应量。随着 ![gsk_eqn00116.gif](../graphics/gsk_eqn00116.gif) 的增加，无阻尼固有频率变得不那么准确；当 ![gsk_eqn00116.gif](../graphics/gsk_eqn00116.gif) 接近1时，使用无阻尼固有频率变得无效。

如果一个结构处于临界阻尼状态（![gsk_eqn00118.gif](../graphics/gsk_eqn00118.gif)），在任何扰动后，它将尽可能快地（不超调）返回到初始静态配置（参见图7-2）。

**图7-2** 不同 ![gsk_eqn00117.gif](../graphics/gsk_eqn00117.gif) 值下的阻尼运动模式。

![graphics/gss-damping-v-nls.png](../graphics/gss-damping-v-nls.png)

## 7.2.1 在Abaqus/Standard中阻尼的定义

在Abaqus/Standard中，可以为瞬态模态分析定义多种不同类型的阻尼：直接模态阻尼、瑞利阻尼和复合模态阻尼。

阻尼通过使用 `*MODAL DAMPING`（模态阻尼）选项为模态动力学过程定义。此选项是步骤定义的一部分，允许为每个模态定义不同数量的阻尼。直接阻尼、瑞利阻尼和复合阻尼都可以通过这种方式定义。

**直接模态阻尼**

与每个模态相关的临界阻尼分数 ![gsk_eqn00116.gif](../graphics/gsk_eqn00116.gif) 可以使用直接模态阻尼来定义。通常使用的值在临界阻尼的1%到10%范围内。直接模态阻尼允许您精确地定义系统每个模态的阻尼。

`*MODAL DAMPING` 选项上的 `VISCOUS`=`FRACTION OF CRITICAL DAMPING`（粘性=临界阻尼分数）参数表示指定了直接模态阻尼。例如，要为前10个模态定义4%的临界模态阻尼，为模态11-20定义5%，，请在步骤定义中包含以下内容：

```abaqus
*MODAL DAMPING, VISCOUS=FRACTION OF CRITICAL DAMPING
1, 10, 0.04
11, 20, 0.05
```

**瑞利阻尼**

在瑞利阻尼中，假定阻尼矩阵是质量矩阵和刚度矩阵的线性组合：

![d0](../graphics/gsk_eqn00119.gif)

其中 ![gsk_eqn00051.gif](../graphics/gsk_eqn00051.gif) 和 ![gsk_eqn00120.gif](../graphics/gsk_eqn00120.gif) 是用户定义的常数。虽然阻尼与质量和刚度矩阵成正比的假设没有严格的物理依据，但实际上阻尼分布很少被详细了解足以证明任何其他更复杂的模型是合理的。一般来说，对于重阻尼系统（即高于约10%临界阻尼），该模型变得不可靠。与其他形式的阻尼一样，您可以精确地定义系统每个模态的瑞利阻尼。

对于给定的模态 *i*，阻尼比 ![gsk_eqn00121.gif](../graphics/gsk_eqn00121.gif) 与瑞利阻尼值 ![gsk_eqn00051.gif](../graphics/gsk_eqn00051.gif) 和 ![gsk_eqn00120.gif](../graphics/gsk_eqn00120.gif) 通过以下公式关联：

![d0](../graphics/gsk_eqn00122.gif)

`*MODAL DAMPING` 选项上的 `VISCOUS`=`RAYLEIGH` 参数表示要使用瑞利阻尼。例如，要为模态1-10定义 ![gsk_eqn00051.gif](../graphics/gsk_eqn00051.gif) = 0.2525 和 ![gsk_eqn00120.gif](../graphics/gsk_eqn00120.gif) = 2.9 × 10⁻³，为模态11-20定义 ![gsk_eqn00051.gif](../graphics/gsk_eqn00051.gif) = 0.2727 和 ![gsk_eqn00120.gif](../graphics/gsk_eqn00120.gif) = 3.03 × 10⁻³，应在步骤定义中包含以下行：

```abaqus
*MODAL DAMPING, VISCOUS=RAYLEIGH
1, 10, 0.2525, 2.9E-3
11, 20, 0.2727, 3.03E-3
```

**复合阻尼**

在复合阻尼中，为每种材料定义临界阻尼的分数，然后为整个结构找到复合阻尼值。当结构中存在许多不同材料时，此选项很有用。复合阻尼在本指南中不再进一步讨论。

## 7.2.2 选择阻尼值

在大多数线性动力学问题中，正确指定阻尼对于获得准确结果很重要。然而，阻尼是近似的，因为它模拟结构的能量吸收特性，而不试图模拟引起这些特性的物理机制。因此，很难确定模拟所需的阻尼数据。有时您可能有动态测试的数据可用，但通常您将不得不使用从参考资料或经验中获得的数据。在这种情况下，您应该非常谨慎地解释结果，并且应该使用参数研究来评估模拟对阻尼值的敏感性。
