# 61.25 OdbStep 对象

输出数据库包含与其源模型数据库相同的步。

**访问**

```
odb.steps()[*name*]
```

### 61.25.1 Step(...)

此方法创建一个 OdbStep 对象。

**路径**

```
odb.Step
```

**原型**

```
odb_Step&
Step(const odb_String& name,
     const odb_String& description,
     odb_Enum::odb_DomainEnum domain,
     double timePeriod,
     const odb_String& previousStepName,
     const odb_String& procedure,
     double totalTime);
```

**必需参数**

*name*

一个 odb_String，指定存储库键。

*description*

一个 odb_String，指定步描述。

*domain*

一个 odb_Enum::odb_DomainEnum，指定步的域。可能的值为 odb_Enum::TIME、odb_Enum::FREQUENCY、odb_Enum::ARC_LENGTH 和 odb_Enum::MODAL。

可以为该步创建的 [OdbFrame](pt02ch61pyo15.md) 对象的类型基于 *domain* 参数的值。

**可选参数**

*timePeriod*

一个 Double，指定步的时间周期。如果 *domain*=odb_Enum::TIME，则需要 *timePeriod*；否则，此参数不适用。默认值为 0.0。

*previousStepName*

一个 odb_String，指定前一步。如果 *previousStepName* 是空字符串，则使用存储库中的最后一步。如果 *previousStepName* 不是最后一步，这将更改位于该位置的步的 *previousStepName* 成员。特殊值 'Initial' 指的是内部初始模型步，仅用于在任何其他现有步之前的第一位置插入新步。默认值为空字符串。

*procedure*

一个 odb_String，指定步的过程。默认值为空字符串。

*totalTime*

一个 Double，指定在此步之前所有步中消耗的分析时间。默认值为 1.0。

**返回值**

一个 OdbStep 对象。

**异常**

如果 *previousStepName* 无效：

```
ValueError: previousStepName is invalid
```

### 61.25.2 getFrame(...)

此方法检索与给定帧值关联的 [OdbFrame](pt02ch61pyo15.md) 对象。

**原型**

```
odb_Frame
getFrame(double frameValue,
         odb_Enum::odb_MatchEnum match);
```

**必需参数**

*frameValue*

一个 Double，指定需要帧的值。*frameValue* 可以是步时间或频率。

**可选参数**

*match*

一个 odb_Enum::odb_MatchEnum，指定如果没有精确帧值时返回哪个帧。可能的值为 odb_Enum::CLOSEST、odb_Enum::BEFORE、odb_Enum::AFTER 和 odb_Enum::EXACT。默认值为 odb_Enum::CLOSEST。

当 *match*=odb_Enum::CLOSEST 时，Abaqus 返回最接近的帧。如果请求的帧值恰好在两帧之间，Abaqus 返回该值之后的帧。

当 *match*=odb_Enum::EXACT 时，如果精确帧值不存在，Abaqus 引发异常。

**返回值**

一个 [OdbFrame](pt02ch61pyo15.md) 对象。

**异常**

如果未找到 [OdbFrame](pt02ch61pyo15.md) 对象：

```
OdbError: Frame not found.
```

### 61.25.3 getFrame(...)

此方法检索与给定载荷工况关联的 [OdbFrame](pt02ch61pyo15.md) 对象。

**原型**

```
odb_Frame
getFrame(const odb_LoadCase& loadCase);
```

**必需参数**

*loadCase*

一个 [OdbLoadCase](pt02ch61pyo17.md) 对象，指定步中的载荷工况。

**可选参数**

无。

**返回值**

一个 [OdbFrame](pt02ch61pyo15.md) 对象。

**异常**

如果未找到 [OdbFrame](pt02ch61pyo15.md) 对象：

```
OdbError: Frame not found.
```

### 61.25.4 getFrame(...)

此方法检索与给定载荷工况和帧值关联的 [OdbFrame](pt02ch61pyo15.md) 对象。

**原型**

```
odb_Frame
getFrame(const odb_LoadCase& loadCase,
         double frameValue,
         odb_Enum::odb_MatchEnum match);
```

**必需参数**

*loadCase*

一个 [OdbLoadCase](pt02ch61pyo17.md) 对象，指定步中的载荷工况。

*frameValue*

一个 Double，指定需要帧的值。*frameValue* 可以是步时间或频率。

**可选参数**

*match*

一个 odb_Enum::odb_MatchEnum，指定如果没有精确帧值时返回哪个帧。可能的值为 odb_Enum::CLOSEST、odb_Enum::BEFORE、odb_Enum::AFTER 和 odb_Enum::EXACT。默认值为 odb_Enum::CLOSEST。

当 *match*=odb_Enum::CLOSEST 时，Abaqus 返回最接近的帧。如果请求的帧值恰好在两帧之间，Abaqus 返回该值之后的帧。

当 *match*=odb_Enum::EXACT 时，如果精确帧值不存在，Abaqus 引发异常。

**返回值**

一个 [OdbFrame](pt02ch61pyo15.md) 对象。

**异常**

如果未找到 [OdbFrame](pt02ch61pyo15.md) 对象：

```
OdbError: Frame not found.
```

### 61.25.5 getHistoryRegion(...)

此方法检索与模型中 HistoryPoint 关联的 [HistoryRegion](pt02ch61pyo11.md) 对象。

**原型**

```
odb_HistoryRegion
getHistoryRegion(const odb_HistoryPoint& point,
                 const odb_LoadCase& loadCase);
```

**必需参数**

*point*

一个 [HistoryPoint](pt02ch61pyo10.md) 对象，指定模型中的点。

**可选参数**

*loadCase*

一个 [OdbLoadCase](pt02ch61pyo17.md) 对象，指定步中的载荷工况。

**返回值**

一个 [HistoryRegion](pt02ch61pyo11.md) 对象。

**异常**

如果未找到 [HistoryRegion](pt02ch61pyo11.md) 对象：

```
OdbError: HistoryRegion not found.
```

### 61.25.6 setDefaultDeformedField(...)

此方法设置步中的默认变形场变量。

**原型**

```
void
setDefaultDeformedField(const odb_FieldOutput& field);
```

**必需参数**

*field*

一个 [FieldOutput](pt02ch61pyo07.md) 对象，指定用于可视化的默认变形场变量。

**可选参数**

无。

**返回值**

无

**异常**

无。

### 61.25.7 setDefaultField(...)

此方法设置步中的默认场变量。

**原型**

```
void
setDefaultField(const odb_FieldOutput& field);
```

**必需参数**

*field*

一个 [FieldOutput](pt02ch61pyo07.md) 对象，指定用于可视化的默认场变量。

**可选参数**

无。

**返回值**

无

**异常**

无。

### 61.25.8 成员

OdbStep 对象具有与 [Step](pt02ch61pyo25.md#ker-odbstep-step-cpp) 方法参数相同名称和描述的成员。

此外，OdbStep 对象可以具有以下成员：

**原型**

```
odb_String name() const;
odb_String description() const;
odb_Enum::odb_DomainEnum domain() const;
const odb_LoadCaseRepository& loadCases();
float timePeriod() const;
float totalTime() const;
odb_String previousStepName() const;
odb_String procedure() const;
int number() const;
bool nlgeom() const;
odb_Frame frames(int frameNo);
odb_SequenceFrame& frames();
odb_HistoryRegionRepository& historyRegions();
double mass() const;
odb_SequenceDouble massCenter() const;
odb_SequenceDouble inertiaAboutCenter() const;
odb_SequenceDouble inertiaAboutOrigin() const;
double acousticMass() const;
odb_SequenceDouble acousticMassCenter() const;
odb_SequenceNodalDofs eliminatedNodalDofs() const;
```

*number*

一个 Int，指定步编号。

*nlgeom*

一个 Boolean，指定此步是否可能发生几何非线性。

*mass*

一个 Double，指定模型的当前质量值。如果存在声学介质，则不包括声学介质的质量。

*acousticMass*

一个 Double，指定模型声学介质的当前质量值。

*frames*

[OdbFrame](pt02ch61pyo15.md) 对象的序列。

*historyRegions*

[HistoryRegion](pt02ch61pyo11.md) 对象的存储库。

*loadCases*

[OdbLoadCase](pt02ch61pyo17.md) 对象的存储库。

*massCenter*

一个 odb_SequenceDouble，指定质心坐标。

*inertiaAboutCenter*

一个 odb_SequenceDouble，指定关于质心的惯矩和惯积。对于 3-D 模型，惯量按以下顺序写出：I(XX)、I(YY)、I(ZZ)、I(XY)、I(XZ) 和 I(YZ)。对于 2-D 模型，仅输出 I(ZZ) 和 I(XY)。

*inertiaAboutOrigin*

一个 odb_SequenceDouble，指定关于全局坐标系原点的惯矩和惯积。对于 3-D 模型，惯量按以下顺序写出：I(XX)、I(YY)、I(ZZ)、I(XY)、I(XZ) 和 I(YZ)。对于 2-D 模型，仅输出 I(ZZ) 和 I(XY)。

*acousticMassCenter*

一个 odb_SequenceDouble，指定声学介质的质心坐标。
