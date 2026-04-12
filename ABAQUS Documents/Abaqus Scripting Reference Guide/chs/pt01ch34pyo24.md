# 34.24 OdbStep 对象

输出数据库包含与其来源的模型数据库相同的步骤。

**访问**

```
import odbAccess
session.odbs[*name*].steps[*name*]
```

### 34.24.1 Step(...)

此方法创建 OdbStep 对象。

**路径**

```
session.odbs[*name*].Step
```

**必要参数**

*name*

一个字符串，指定仓库键。

*description*

一个字符串，指定步骤描述。

*domain*

一个 SymbolicConstant，指定步骤的域。可能的值为 TIME、FREQUENCY、ARC_LENGTH 和 MODAL。

可以为该步骤创建的 [OdbFrame](pt01ch34pyo14.md) 对象的类型基于 *domain* 参数的值。

**可选参数**

*timePeriod*

一个 Float，指定步骤的时间周期。如果 *domain*=TIME，则需要 *timePeriod*；否则，此参数不适用。默认值为 0.0。

*previousStepName*

一个字符串，指定前一个步骤。如果 *previousStepName* 为空字符串，则使用仓库中的最后一步。如果 *previousStepName* 不是最后一步，这将更改为该位置的步骤的 *previousStepName* 成员。一个特殊值 'Initial' 指的是内部初始模型步骤，可用于在任何其他现有步骤之前的第一位置插入新步骤。默认值为空字符串。

*procedure*

一个字符串，指定步骤过程。默认值为空字符串。

*totalTime*

一个 Float，指定在此步骤之前所有步骤中花费的分析时间。默认值为 1.0。

**返回值**

OdbStep 对象。

**异常**

如果 *previousStepName* 无效：

```
ValueError: previousStepName is invalid
```

### 34.24.2 getFrame(...)

此方法检索与给定帧值关联的 [OdbFrame](pt01ch34pyo14.md) 对象。

**必要参数**

*frameValue*

一个 Double，指定需要帧的值。*frameValue* 可以是步时间或频率。

**可选参数**

*match*

一个 SymbolicConstant，指定当精确帧值不存在时返回哪个帧。可能的值为 CLOSEST、BEFORE、AFTER 和 EXACT。默认值为 CLOSEST。

当 *match*=CLOSEST 时，Abaqus 返回最接近的帧。如果请求的帧值恰好在两帧之间，Abaqus 返回该值之后的帧。

当 *match*=EXACT 时，如果精确帧值不存在，Abaqus 会引发异常。

**返回值**

[OdbFrame](pt01ch34pyo14.md) 对象。

**异常**

如果未找到 [OdbFrame](pt01ch34pyo14.md) 对象：

```
OdbError: Frame not found.
```

### 34.24.3 getFrame(...)

此方法检索与给定负载情况关联的 [OdbFrame](pt01ch34pyo14.md) 对象。

**必要参数**

*loadCase*

一个 [OdbLoadCase](pt01ch34pyo16.md) 对象，指定步骤中的负载情况。

**可选参数**

无。

**返回值**

[OdbFrame](pt01ch34pyo14.md) 对象。

**异常**

如果未找到 [OdbFrame](pt01ch34pyo14.md) 对象：

```
OdbError: Frame not found.
```

### 34.24.4 getFrame(...)

此方法检索与给定负载情况和帧值关联的 [OdbFrame](pt01ch34pyo14.md) 对象。

**必要参数**

*loadCase*

一个 [OdbLoadCase](pt01ch34pyo16.md) 对象，指定步骤中的负载情况。

*frameValue*

一个 Double，指定需要帧的值。*frameValue* 可以是步时间或频率。

**可选参数**

*match*

一个 SymbolicConstant，指定当精确帧值不存在时返回哪个帧。可能的值为 CLOSEST、BEFORE、AFTER 和 EXACT。默认值为 CLOSEST。

当 *match*=CLOSEST 时，Abaqus 返回最接近的帧。如果请求的帧值恰好在两帧之间，Abaqus 返回该值之后的帧。

当 *match*=EXACT 时，如果精确帧值不存在，Abaqus 会引发异常。

**返回值**

[OdbFrame](pt01ch34pyo14.md) 对象。

**异常**

如果未找到 [OdbFrame](pt01ch34pyo14.md) 对象：

```
OdbError: Frame not found.
```

### 34.24.5 getHistoryRegion(...)

此方法检索与模型中 HistoryPoint 关联的 [HistoryRegion](pt01ch34pyo10.md) 对象。

**必要参数**

*point*

一个 [HistoryPoint](pt01ch34pyo09.md) 对象，指定模型中的点。

**可选参数**

*loadCase*

一个 [OdbLoadCase](pt01ch34pyo16.md) 对象，指定步骤中的负载情况。

**返回值**

[HistoryRegion](pt01ch34pyo10.md) 对象。

**异常**

如果未找到 [HistoryRegion](pt01ch34pyo10.md) 对象：

```
OdbError: HistoryRegion not found.
```

### 34.24.6 setDefaultDeformedField(...)

此方法设置步骤中的默认变形场变量。

**必要参数**

*field*

一个 [FieldOutput](pt01ch34pyo06.md) 对象，指定用于可视化的默认变形场变量。

**可选参数**

无。

**返回值**

无

**异常**

无。

### 34.24.7 setDefaultField(...)

此方法设置步骤中的默认场变量。

**必要参数**

*field*

一个 [FieldOutput](pt01ch34pyo06.md) 对象，指定用于可视化的默认场变量。

**可选参数**

无。

**返回值**

无

**异常**

无。

### 34.24.8 成员

OdbStep 对象具有与 [Step](pt01ch34pyo24.md#ker-odbstep-step-pyc) 方法的参数名称和描述相同的成员。

此外，OdbStep 对象可以具有以下成员：

*number*

一个整数，指定步骤编号。

*nlgeom*

一个布尔值，指定此步骤是否可能发生几何非线性。

*mass*

一个 Float，指定模型的当前质量值。如果存在声学介质，则不包括声学介质的质量。

*acousticMass*

一个 Float，指定模型声学介质的当前质量值。

*frames*

一个 [OdbFrameArray](pt01ch34pyo14.md) 对象。

*historyRegions*

[HistoryRegion](pt01ch34pyo10.md) 对象的仓库。

*loadCases*

[OdbLoadCase](pt01ch34pyo16.md) 对象的仓库。

*massCenter*

浮点数元组，指定质心坐标。

*inertiaAboutCenter*

浮点数元组，指定关于质心的惯性和惯性积。对于 3-D 模型，惯性量按以下顺序写入：I(XX)、I(YY)、I(ZZ)、I(XY)、I(XZ) 和 I(YZ)。对于 2-D 模型，仅输出 I(ZZ) 和 I(XY)。

*inertiaAboutOrigin*

浮点数元组，指定关于全局坐标系原点的惯性和惯性积。对于 3-D 模型，惯性量按以下顺序写入：I(XX)、I(YY)、I(ZZ)、I(XY)、I(XZ) 和 I(YZ)。对于 2-D 模型，仅输出 I(ZZ) 和 I(XY)。

*acousticMassCenter*

浮点数元组，指定声学介质的质心坐标。
