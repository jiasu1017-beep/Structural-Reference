# *BEAM SECTION GENERATE





### *BEAM SECTION GENERATE为网格化横截面生成梁截面属性。

此选项用于计算横截面翘曲函数，定义质心和剪切中心，并为网格化横截面生成刚度和惯性属性。这些属性被写入文件`*jobname*.bsp`，用于后续使用[*BEAM GENERAL SECTION](ch02abk05.md)，SECTION=MESHED选项的梁分析。

**产品：**Abaqus/Standard

**类型：**历史数据

**级别：**步骤

##### **参考：**

- ["网格化梁横截面，" Abaqus Analysis User's Guide第10.6.1节](../usb/usb-link.md#usb-anl-ameshedsection)
- ["梁截面行为，" Abaqus Analysis User's Guide第29.3.5节](../usb/usb-link.md#usb-elm-ebeamsectionbehavior)
- ["使用通用梁截面定义截面行为，" Abaqus Analysis User's Guide第29.3.7节](../usb/usb-link.md#usb-elm-eusingbeamgensect)

**此选项没有参数或数据行。**


