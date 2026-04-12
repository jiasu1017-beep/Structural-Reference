# 10.3 DataSet 对象

DataSet 对象指定材料测试数据。

**访问**

```
import calibration
mdb.models[*name*].calibrations[*name*].dataSets
```

### 10.3.1 DataSet(...)

此方法创建 DataSet 对象。

**路径**

```
mdb.models[*name*].calibrations[*name*].DataSet
```

**必需参数**

*name*

String，指定新数据集的名称。

*data*

Float 对的序列，指定数据集类型对。可能的值为应力/应变、力/位移或横向应变/轴应变对。

**可选参数**

*type*

String，指定新数据集的类型。值可以为"STRESS/STRAIN"、"FORCE/DISPLACEMENT"或"AXIALSTRAIN/TRANSVERSESTRAIN"。默认值为"STRESS/STRAIN"。

*form*

String，指定新数据集的形式。值可以为"NOMINAL"或"TRUE"。默认值为"NOMINAL"。

**返回值**

DataSet 对象。

**异常**

InvalidNameError。

### 10.3.2