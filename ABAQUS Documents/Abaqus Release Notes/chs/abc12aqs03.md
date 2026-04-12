# 12.3 最后收敛增量的输出







**产品：**Abaqus/Standard  

**优点：**如果 Abaqus/Standard 分析中的通用步骤未能收敛，则将最后收敛增量的结果写入输出数据库。这有助于诊断收敛失败的原因。

**说明：**默认输出行为已修改为在未实现收敛时输出最后收敛增量。只有在第一个增量之后存在收敛困难时才会写入输出。此默认行为适用于 Abaqus/Standard 中的所有通用步骤。
**参考：**

**Abaqus Analysis User's Guide**
- ["Output to the output database," Section 4.1.3](../usb/usb-link.md#usb-out-odboutput)

