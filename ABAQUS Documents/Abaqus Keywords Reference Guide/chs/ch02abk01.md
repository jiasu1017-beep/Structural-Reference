# *BASELINE CORRECTION





### *BASELINE CORRECTION包含基准线修正。

此选项用于修改加速度历史，以最小化通过对给定加速度进行时间积分所获得的位移的整体漂移。它必须紧跟在[*AMPLITUDE](ch01abk09.md)选项的数据行之后。

**产品：**Abaqus/Standard  Abaqus/CAE

**类型：**模型数据或历史数据

**级别：**模型、步骤

**Abaqus/CAE：**振幅工具集

##### **参考：**

- [*AMPLITUDE](ch01abk09.md)
- ["振幅曲线，" Abaqus Analysis User's Guide第34.1.2节](../usb/usb-link.md#usb-prc-pamplitude)

**此选项没有参数。**

### **定义修正间隔的数据行（可选；如果没有给出数据行，则基准线修正将振幅定义的整个时间视为单个修正间隔）：**

**第一行：**

根据需要重复此数据行。每行（最后一行除外）必须正好有八个时间点。




