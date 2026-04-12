# 34.29 SectorDefinition 对象

SectorDefinition 对象描述循环对称模型的symmetry sectors数量和symmetry axis。

**访问**

```
import odbAccess
session.odbs[*name*].sectorDefinition
```

### 34.29.1 成员

SectorDefinition 对象具有以下成员：

*numSectors*

一个整数，指定循环对称模型中的扇区数量。

*symmetryAxis*

浮点数元组的元组，指定symmetry axis上两点的坐标。
