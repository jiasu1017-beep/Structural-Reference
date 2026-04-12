# 12.4 接触相关能量的输出







**产品：**Abaqus/Standard  

**优点：**引入了新的接触相关整体模型能量，并且能量计算（ETOTAL）已得到改进。

**说明：**新的能量输出变量可用于避免总能量平衡 ETOTAL 的漂移并提供对模拟行为的深入了解。这些新输出变量说明如[表 12--1](abc12aqs04.md#rnb-contact-energy) 中所述的内聚接触能量、与接触稳定和接触阻尼相关的耗散能量以及与接触约束"不连续功"相关的能量。

**表 12-1** 接触相关能量的新输出变量。
| 描述 | 输出变量 |
| --- | --- |
| 内聚接触能量 | 存储在与法向接触约束相关的所有惩罚弹簧和"软化"接触约束中的能量 | ALLCCEN |
| 存储在与切向接触约束相关的所有惩罚弹簧中的能量 | ALLCCET |
| 存储在与法向和切向接触约束相关的所有惩罚弹簧和"软化"接触约束中的能量（等于 ALLCCEN 和 ALLCCET 的和） | ALLCCE |
| 与接触稳定和接触阻尼相关的能量耗散 | 整个模型的法向接触方向 | ALLCCSDN |
| 整个模型的切向接触方向 | ALLCCSDT |
| 整个模型（等于 ALLCCSDN 和 ALLCCSDT 的和） | ALLCCSD |
| 与接触约束"不连续功"相关的能量 | 说明当接触条件变化时由接触力所做的功中未被其他接触能量变量说明的部分 | ALLCCDW |

现有的输出变量 ALLSD 和 ALLVD 继续像以前版本的 Abaqus 那样说明与接触稳定和接触阻尼相关的耗散能量。

与接触稳定和接触阻尼相关的内聚接触能量和耗散能量与数值效应相关，在理想情况下（如无限惩罚刚度或零稳定刚度）这些效应为零。与模型中其他基于物理的能量（如内能 ALLIE）相比，这些输出变量的显著值有时表明解不准确。接触约束不连续功将随着时间增量大小变得非常小而趋于零。然而，正如《Abaqus Example Problems Guide》中["Energy computations in a contact analysis," Section 1.1.25](../exa/exa-link.md#exa-sta-contactenergy) 中所讨论的，ALLCCDW 具有显著值而不会导致解不准确是很常见的。
**参考：**

**Abaqus Analysis User's Guide**
- ["Output to the output database," Section 4.1.3](../usb/usb-link.md#usb-out-odboutput)
- ["Abaqus/Standard output variable identifiers," Section 4.2.1](../usb/usb-link.md#usb-out-houtputvar)
- ["Whole model contact-related energy variables" in "Defining general contact interactions in Abaqus/Standard," Section 36.2.1](../usb/usb-link.md#usb-cni-acontactgeneralstd-contener)

**Abaqus Keywords Reference Guide**
- [*ENERGY OUTPUT](../key/key-link.md#usb-kws-henergyoutput)
- [*ENERGY PRINT](../key/key-link.md#usb-kws-henergyprint)

**Abaqus Example Problems Guide**
- ["Energy computations in a contact analysis," Section 1.1.25](../exa/exa-link.md#exa-sta-contactenergy)

