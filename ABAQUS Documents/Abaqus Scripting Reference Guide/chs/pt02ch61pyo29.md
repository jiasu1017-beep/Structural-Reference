# 61.29 SectorDefinition 对象

SectorDefinition 对象描述循环对称模型的对称扇区数量和对称轴。

**访问**

```
odb.sectorDefinition()
```

### 61.29.1 成员

SectorDefinition 对象具有以下成员：

**原型**

```
int numSectors();
const odb_SequenceSequenceFloat symmetryAxis();
```

*numSectors*

一个 Int，指定循环对称模型中的扇区数量。

*symmetryAxis*

一个 odb_SequenceSequenceFloat，指定对称轴上两点的坐标。
