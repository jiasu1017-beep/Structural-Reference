# 10.1 Calibration 对象

Calibration 对象是用于指定材料校准的对象。Calibration 对象存储用于从测试数据指定材料的数据。

**访问**

```
import calibration
mdb.models[*name*].calibrations[*name*]
```

### 10.1.1 Calibration(...)

此方法创建 Calibration 对象。

**路径**

```
mdb.models[*name*].Calibration
```

**必需参数**

*name*

String，指定新校准的名称。

**可选参数**

无。

**返回值**

Calibration 对象。

**异常**

InvalidNameError。

### 10.1.2 成员

Calibration 对象的成员与 [Calibration](pt01ch10pyo01.md#ker-calibration-calibration-pyc) 方法的参数具有相同的名称和描述。

此外，Calibration 对象可以具有以下成员：

*dataSets*

[DataSet](pt01ch10pyo03.md) 对象。

*behaviors*

[Behavior](pt01ch10pyo02.md) 对象。
