# 61.9 HistoryOutput 对象

HistoryOutput 对象包含指定变量在某一点的历史输出。

**访问**

```
odb.steps()[*name*].historyRegions()[*name*].historyOutputs()[*name*]
```

### 61.9.1 HistoryOutput(...)

此方法创建一个 HistoryOutput 对象。

**路径**

```
odb.steps()[*name*].historyRegions()[*name*].HistoryOutput
```

**原型**

```
odb_HistoryOutput&
HistoryOutput(const odb_String& name,
              const odb_String& description,
              odb_Enum::odb_DataTypeEnum type,
              const odb_SequenceInvariant& validInvariants);
```

**必需参数**

*name*

一个 odb_String，指定输出变量名称。

*description*

一个 odb_String，指定输出变量。

*type*

一个 odb_Enum::odb_DataTypeEnum，指定输出类型。当前仅支持 odb_Enum::SCALAR。

**可选参数**

*validInvariants*

一个 odb_SequenceInvariant，指定应该为此场计算的不变量。可能的值为 odb_Enum::MAGNITUDE、odb_Enum::MISES、odb_Enum::TRESCA、odb_Enum::PRESS、odb_Enum::INV3、odb_Enum::MAX_PRINCIPAL、odb_Enum::MID_PRINCIPAL 和 odb_Enum::MIN_PRINCIPAL。默认值为空序列。

**返回值**

一个 HistoryOutput 对象。

**异常**

无。

### 61.9.2 addData(...)

此方法向 HistoryOutput 对象的 *data* 成员添加数据。

**原型**

```
void
addData(double frame,
        double value);
```

**必需参数**

*frame*

一个 Double，指定帧值。*frame* 可以指定为步时间、频率或模态编号。

*value*

一个 Double，指定在 *frame* 指定的帧值处变量的值。

**可选参数**

无。

**返回值**

无

**异常**

无。

### 61.9.3 addData(...)

此方法向 HistoryOutput 对象的 *data* 成员添加数据。

**原型**

```
void
addData(const odb_SequenceFloat& frame,
        const odb_SequenceFloat& value);
```

**必需参数**

*frame*

一个 odb_SequenceFloat，指定帧值。*frame* 可以指定为步时间、频率或模态编号。

*value*

一个 odb_SequenceFloat，指定在 *frame* 指定的帧值处变量的值。

**可选参数**

无。

**返回值**

无

**异常**

如果 *frame* 的长度与 *value* 的长度不同，则引发 ValueError。

### 61.9.4 addData(...)

此方法向 HistoryOutput 对象的 *data* 成员添加数据。

**原型**

```
void
addData(const odb_SequenceSequenceFloat& data);
```

**必需参数**

*data*

一个 odb_SequenceSequenceFloat，指定对 (*frameValue*, *value*)，其中 *frameValue* 可以是时间、频率或模态，*value* 是指定变量在 *frameValue* 处的值。（此值取决于变量的类型。）

**可选参数**

无。

**返回值**

无

**异常**

无。

### 61.9.5 成员

HistoryOutput 对象具有与 [HistoryOutput](pt02ch61pyo09.md#ker-historyoutput-historyoutput-cpp) 方法参数相同名称和描述的成员。

此外，HistoryOutput 对象可以具有以下成员：

**原型**

```
odb_String name() const;
odb_String description() const;
odb_SequenceSequenceFloat data() const;
odb_SequenceSequenceFloat conjugateData() const;
```

*data*

一个 odb_SequenceSequenceFloat，指定对 (*frameValue*, *value*)，其中 *frameValue* 可以是时间、频率或模态，*value* 是指定变量在 *frameValue* 处的值。（此值取决于变量的类型。）

*conjugateData*

一个 odb_SequenceSequenceFloat，指定每个帧值（时间、频率或模态）处指定复数变量的虚部。对的形式为 (*frameValue*, *value*)。
