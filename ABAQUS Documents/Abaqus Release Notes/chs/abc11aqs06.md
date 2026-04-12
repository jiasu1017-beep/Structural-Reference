# 11.6 将 Abaqus 数据转换到模态中性文件的增强







**产品：**Abaqus/Standard  

**优点：**将 Abaqus 结果转换到模态中性文件的速度显著加快，模态中性文件的大小可能比以前版本小得多。

**说明：**两个增强功能可用于 **abaqus adams** 转换器。转换器现在读取在子结构生成期间计算的惯性不变量而非重新计算，这使得将 Abaqus 子结构 SIM 数据库文件中的结果转换到 MSC.ADAMS 模态中性（`.mnf`）文件的速度显著加快。现在，转换器只需要处理"有趣"的位移模式子集，这可以导致显著更小的模态中性文件。
**参考：**

**Abaqus Analysis User's Guide**
- ["Translating Abaqus data to MSC.ADAMS modal neutral files," Section 3.2.36](../usb/usb-link.md#usb-int-dabaadmproc)

