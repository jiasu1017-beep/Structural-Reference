# 4.2 AMS 特征值求解器性能改进





**产品：** Abaqus/Standard  Abaqus/AMS

**优势：** 对于包含许多分布耦合约束或具有拉格朗日乘子的其他特征（如紧固件、接触相互作用、连接器或超弹性材料）的大型模型，AMS 特征值求解器的性能已得到改进。

**描述：** AMS 特征值求解器中约束方程的增强处理为大尺度模型提供了改进的性能。 [表 4–1](abc04aqs02.md#ams-constraint-solver-table) 说明了一个拥有 1860 万自由度和 130 万约束方程的工业车模型的 AMS 特征值求解器性能改进。车身模型的频率提取分析在配备双 2.6 GHz Intel Sandy Bridge 处理器（2 ![](../graphics/rnb_eqn00002.gif) 8 核）和 128 GB 内存的 Linux 机器上运行。在表中，“Total Standard” 包括约束求解器、AMS 特征值求解器和 AMS 特征值求解过程非求解器部分的时间。

**表 4–1** AMS 特征值求解器中的性能改进。
|  | Abaqus 6.13 墙上时钟时间（秒） | Abaqus 6.14 墙上时钟时间（秒） | 加速因子 |
| --- | --- | --- | --- |
| 约束求解器 | 3027 | 52 | 58.2 |
| AMS 特征值求解器 | 3264 | 3242 | 不适用 |
| Total Standard | 8362 | 5311 | 1.6 |

**参考：**

**Abaqus Analysis User's Guide**
- [“Natural frequency extraction，” Section 6.3.5](../usb/usb-link.md#usb-anl-afreqextraction)

**Abaqus Keywords Reference Guide**
- [*FREQUENCY](../key/key-link.md#usb-kws-hfrequency)




