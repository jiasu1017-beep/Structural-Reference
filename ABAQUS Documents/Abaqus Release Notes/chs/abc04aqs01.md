# 4.1 AMS 特征值求解器可以提取耦合结构-声学特征模式





**产品：** Abaqus/Standard

**优势：** 耦合结构-声学特征模式可以由 AMS 特征值求解器计算并使用 SIM 架构存储。此外，模态方法可以利用这些模式进行模态叠加。

**描述：** 如果模型包含结构-声学耦合，AMS 特征值求解器可以提取耦合模式。以前，此功能仅适用于 Lanczos 特征值求解器。此增强功能允许您利用 AMS 特征值求解器提供的卓越性能。例如，提取 250 万自由度车身模型的约 1,000 个耦合模式，Lanczos 特征值求解器需要 3 小时 3 分钟；AMS 特征值求解器仅需 32 分钟，快了近 6 倍。此基准测试在使用 16 核 Sandy Bridge 机器（128 GB 内存）上执行。

AMS 特征值求解器计算的耦合结构-声学模式在以下使用 SIM 架构的模态过程中受支持：
- 复特征值提取，
- 基于模态的稳态动态分析，
- 子空间稳态动态分析，以及
- 子结构生成。

**参考：**

**Abaqus Analysis User's Guide**
- [“Natural frequency extraction，” Section 6.3.5](../usb/usb-link.md#usb-anl-afreqextraction)

**Abaqus Keywords Reference Guide**
- [*COMPLEX FREQUENCY](../key/key-link.md#usb-kws-hcomplexfrequency)
- [*FREQUENCY](../key/key-link.md#usb-kws-hfrequency)
- [*STEADY STATE DYNAMICS](../key/key-link.md#usb-kws-hsteadystdyn)
- [*SUBSTRUCTURE GENERATE](../key/key-link.md#usb-kws-ssubgenerate)

**Abaqus Theory Guide**
- [“Coupled acoustic-structural medium analysis，” Section 2.9.1](../stm/stm-link.md#stm-anl-acouststruct)




