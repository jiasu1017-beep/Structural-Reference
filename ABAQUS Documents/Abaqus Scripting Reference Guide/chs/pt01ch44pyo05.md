# 44.5 PlyStackPlot 对象

PlyStackPlot 对象用于绘制复合铺层或复合壳截面中的铺层堆叠。

**访问**

```
import section
import visualization
```

### 44.5.1 MdbPlyStackPlot(...)

此方法从包含复合壳铺层的零件区域创建 PlyStackPlot 对象。

**Path**

```
section.MdbPlyStackPlot
```

**必需参数**

*part*

 [Part](pt01ch37pyo01.md) 对象。

*region*

 [Region](pt01ch45pyo03.md) 对象，包含复合壳铺层。

**可选参数**

无。

**返回值**

PlyStackPlot 对象。

**异常**

无。

### 44.5.2 OdbPlyStackPlot(...)

此方法从 Odb 对象的复合壳截面创建 PlyStackPlot 对象。

**Path**

```
visualization.OdbPlyStackPlot
```

**必需参数**

*odb*

 [Odb](pt01ch34pyo01.md) 对象。

*sectionName*

 String，指定包含复合壳截面的截面名称。

**可选参数**

*offset*

 Float，指定壳偏移。默认值为 0.0。

**返回值**

PlyStackPlot 对象。

**异常**

无。

### 44.5.3 成员

PlyStackPlot 对象没有成员。

