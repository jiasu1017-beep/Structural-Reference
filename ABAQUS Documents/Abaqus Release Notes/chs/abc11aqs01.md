# 11.1 AMS 特征值求解器的 GPGPU 加速







**产品：**Abaqus/Standard  Abaqus/AMS  

**优点：**AMS 特征值求解器可以使用支持计算的 GPGPU 卡来减少频率提取分析的运行时间。

**说明：**AMS 特征值求解器的降阶特征值解阶段的 GPGPU 加速为需要超过 10,000 个特征模态的大规模模型提供了改进的性能。此外，与 Abaqus 6.13 相比，降阶特征值解阶段的并行扩展性得到了改进。[表 11--1](abc11aqs01.md#ams-solver-table1) 说明了两 个工业模型的 AMS 特征值求解器由于 GPGPU 加速而获得的性能改进：模型 1 是 250 万自由度车体模型，模型 2 是 940 万自由度车体模型。两个分析都在 Linux 机器上运行，配备双 2.6 GHz Intel Sandybridge 处理器（2 ![](../graphics/rnb_eqn00002.gif) 8 核）、128 GB 内存和 2 个 Nvidia Kepler 卡（K20X）。在所有情况下都使用了 16 个核心。

**表 11-1** AMS 特征值求解器 GPGPU 加速带来的性能改进。
| 模型 | 自由度 | 模态数 | Abaqus 6.13 | Abaqus 6.14 | Abaqus 6.14 含 2 个 GPU | Abaqus 6.14 GPU 加速加速因子 |
| --- | --- | --- | --- | --- | --- | --- |
| 模型 1 | 250 万 | 16,926 | 3816 秒 | 3433 秒 | 2662 秒 | 1.29 |
| 模型 2 | 940 万 | 10,743 | 1293 秒 | 1159 秒 | 837 秒 | 1.38 |

**参考：**

**Abaqus Analysis User's Guide**
- ["Natural frequency extraction," Section 6.3.5](../usb/usb-link.md#usb-anl-afreqextraction)

**Abaqus Keywords Reference Guide**
- [*FREQUENCY](../key/key-link.md#usb-kws-hfrequency)

