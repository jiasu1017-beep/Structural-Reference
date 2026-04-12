# 61.15 OdbFrame 对象

OdbFrame 对象的域取自父步。

**访问**

```
odb.steps()[*name*].frames(*i*)
```

### 61.15.1 Frame(...)

此方法创建一个 OdbFrame 对象并将其追加到帧序列。

**路径**

```
odb.steps()[*name*].Frame
```

**原型**

```
 odb_Frame
                  Frame(int incrementNumber,
                  float frameValue,
                  const odb_String& description);
```

**必需参数**

*incrementNumber*

一个 Int，指定步内的帧增量编号。基础帧通常具有增量编号 0，结果从 1 开始。在多个载荷工况的情况下，相同的增量编号会为每个载荷工况重复。

*frameValue*

一个 Float，指定由 [Step](#ker-step-cpp) 对象的 *domain* 成员决定的单位的值。在时间域中等效于 *stepTime*；在频率域中等效于 *frequency*；在模态域中等效于 *mode*。

**可选参数**

*description*

一个 odb_String，指定帧的内容。默认值为空字符串。

**返回值**

一个 OdbFrame 对象。

**异常**

无。

### 61.15.2 Frame(...)

此构造函数在频率域中创建一个 OdbFrame 对象，并将其追加到帧序列。构造函数的参数仅在 *domain*=FREQUENCY 或 *domain*=MODAL 时有效。

**路径**

```
odb.steps()[*name*].Frame
```

**原型**

```
 odb_Frame
                  Frame(int mode,
                  float frequency,
                  const odb_String& description);
```

**必需参数**

*mode*

一个 Int，指定特征模态。此成员仅在 *domain*=odb_Enum::MODAL 时有效。

*frequency*

一个 Float，指定频率。此成员仅在 *domain*=odb_Enum::FREQUENCY 或 [Step](#ker-step-cpp) 对象的 *procedureType* 成员="FREQUENCY" 时有效。默认值为 0.0。

**可选参数**

*description*

一个 odb_String，指定帧的内容。默认值为空字符串。

**返回值**

一个 OdbFrame 对象。

**异常**

无。

### 61.15.3 Frame(...)

此构造函数为特定载荷工况创建一个 OdbFrame 对象，并将其追加到帧序列。

**路径**

```
odb.steps()[*name*].Frame
```

**原型**

```
 odb_Frame
                  Frame(const odb_LoadCase& loadCase,
                  const odb_String& description,
                  float frequency);
```

**必需参数**

*loadCase*

一个 [OdbLoadCase](pt02ch61pyo17.md) 对象，指定帧的载荷工况。

**可选参数**

*description*

一个 odb_String，指定帧的内容。默认值为空字符串。

*frequency*

一个 Float，指定频率。此成员仅在 *domain*=odb_Enum::FREQUENCY 或 [Step](#ker-step-cpp) 对象的 *procedureType* 成员="FREQUENCY" 时有效。默认值为 0.0。

**返回值**

一个 OdbFrame 对象。

**异常**

无。

### 61.15.4 成员

OdbFrame 对象具有与 [Frame](pt02ch61pyo15.md#ker-odbframe-frame-cpp) 方法参数相同名称和描述的成员。

此外，OdbFrame 对象可以具有以下成员：

**原型**

```
odb_Frame associatedFrame();
int cyclicModeNumber();
odb_String description() const;
odb_Enum::odb_DomainEnum domain() const;
odb_FieldOutputRepository& fieldOutputs();
int incrementNumber() const;
float frameValue() const;
float frequency() const;
const odb_LoadCase& loadCase() const;
int mode() const;
```

*cyclicModeNumber*

一个 Int，指定与此帧上存储的数据关联的循环模态编号。只有循环对称模型的频率分析具有循环模态编号。

*domain*

一个 odb_Enum::odb_DomainEnum，指定帧所属步的域。可能的值为 odb_Enum::TIME、odb_Enum::FREQUENCY 和 odb_Enum::MODAL。

*frequency*

一个 Float，指定频率。此成员仅在 *domain*=odb_Enum::FREQUENCY 或 [Step](#ker-step-cpp) 对象的 *procedureType* 成员="FREQUENCY" 时有效。默认值为 0.0。

*mode*

一个 Int，指定特征模态。此成员仅在 *domain*=odb_Enum::MODAL 时有效。

*associatedFrame*

一个 OdbFrame 对象，指定与此循环对称模式对应的数据的实部或虚部。

*fieldOutputs*

[FieldOutput](pt02ch61pyo07.md) 对象的存储库，指定 *fieldOutputs* 存储库的键是表示输出变量的 String。

*loadCase*

一个 [OdbLoadCase](pt02ch61pyo17.md) 对象，指定帧的载荷工况。
