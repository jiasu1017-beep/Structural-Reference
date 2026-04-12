# 61.32 顶层命令





Odb 命令执行以下操作：
- 确定输出数据库（`.odb`）文件是否需要升级到当前版本。
- 确定输出变量在一系列场中的极值；例如，在一系列载荷情况下的极值。
- 打开现有的输出数据库文件并创建一个新的 Odb 对象。
- 将输出数据库文件升级到当前版本，并将升级后的输出数据库写入新文件。
- 在分析运行期间从 C++ 用户子程序内部获取活动的输出数据库。
- 确定基础 Section、Profile 或 Amplitude 对象的实际子类型。
- 将基础 Section、Profile 或 Amplitude 对象转换为适当的子类型。

### 61.32.1 isUpgradeRequiredForOdb(...)

此方法确定输出数据库文件是否需要升级到当前版本。

**原型**

```
bool isUpgradeRequiredForOdb(const odb_String& upgradeRequiredOdbPath);
```

**必需参数**

*upgradeRequiredOdbPath*

一个 odb_String，指定要测试的输出数据库文件的路径。该测试确定输出数据库是否需要升级到当前版本。

**可选参数**

无。

**返回值**

一个布尔值，指示测试结果。值为 True 表示输出数据库需要升级到当前版本。

**异常**

无。

### 61.32.2 maxEnvelope(...)

检索输出变量在一系列场中的最大值。

**原型**

```
odb_SequenceFieldOutput maxEnvelope(
    const odb_SequenceFieldOutput & inputFields);
odb_SequenceFieldOutput maxEnvelope(
    const odb_SequenceFieldOutput & inputFields,
    odb_Enum::odb_InvariantEnum invariant);
odb_SequenceFieldOutput maxEnvelope(
    const odb_SequenceFieldOutput & inputFields,
    const odb_String& componentLabel);
```

**必需参数**

| 参数 |
| --- |
| 一个 odb_SequenceFieldoutput 对象，包含将计算其最大值的 所有 fieldOutput 对象。 |
| 一个 SymbolicConstant，指定比较向量或张量时使用的不变量或分量标签。可能的值为：- odb_Enum::MAGNITUDE - odb_Enum::MISES - odb_Enum::TRESCA - odb_Enum::PRESS - odb_Enum::INV3 - odb_Enum::MAX_PRINCIPAL - odb_Enum::MID_PRINCIPAL - odb_Enum::MIN_PRINCIPAL 如果场是向量或张量，您必须提供此参数或下一参数。 |
| 一个 odb_String，指定用于选择最大值的张量或向量的分量。 |

**可选参数**

无。

**返回值**

一个 odb_SequenceFieldOutput 对象。第一个 fieldOutput 对象包含最大值。第二个 fieldOutput 对象包含具有最大值的场的索引。索引遵循在场输出对象列表中场的排列顺序，这些对象作为函数的参数提供。

**异常**

OdbError

TypeError

```
此函数不接受关键字参数。
```

### 61.32.3 minEnvelope(...)

检索输出变量在一系列场中的最小值。

**原型**

```
odb_SequenceFieldOutput minEnvelope(
    const odb_SequenceFieldOutput & inputFields);
odb_SequenceFieldOutput minEnvelope(
    const odb_SequenceFieldOutput & inputFields,
    odb_Enum::odb_InvariantEnum invariant);
odb_SequenceFieldOutput minEnvelope(
    const odb_SequenceFieldOutput & inputFields,
    const odb_String& componentLabel);
```

**必需参数**

| 参数 |
| --- |
| 一个 odb_SequenceFieldoutput 对象，包含将计算其最大值的 所有 fieldOutput 对象。 |
| 一个 SymbolicConstant，指定比较向量或张量时使用的，不变量或分量标签。可能的值为：- odb_Enum::MAGNITUDE - odb_Enum::MISES - odb_Enum::TRESCA - odb_Enum::PRESS - odb_Enum::INV3 - odb_Enum::MAX_PRINCIPAL - odb_Enum::MID_PRINCIPAL - odb_Enum::MIN_PRINCIPAL 如果场是向量或张量，您必须提供此参数或下一参数。 |
| 一个 odb_String，指定用于选择最小值的张量或向量的分量。 |

**可选参数**

无。

**返回值**

一个 odb_SequenceFieldOutput 对象。第一个 fieldOutput 对象包含最小值。第二个 fieldOutput 对象包含具有最小值的场的索引。索引遵循在场输出对象列表中场的排列顺序，这些对象作为函数的参数提供。

**异常**

OdbError

TypeError

```
此函数不接受关键字参数。
```

### 61.32.4 openOdb(...)

此方法打开一个现有的输出数据库（`.odb`）文件并创建一个新的 Odb 对象。

**原型**

```
odb_Odb& openOdb(const odb_String& path);
```

**必需参数**

*path*

一个 odb_String，指定现有输出数据库（`.odb`）文件的路径。

**可选参数**

*readOnly*

一个布尔值，指定文件是否仅允许只读访问或同时允许读写访问。初始值为 False，表示将允许读写访问。

*readInternalSets*

一个布尔值，指定文件是否允许访问数据库上指定为 Internal 的集。初始值为 False，表示不会读取内部集。

**返回值**

一个 Odb 对象。

**异常**

如果输出数据库是由以前版本的 Abaqus 生成的，需要升级：

```
OdbError: The database is from a previous release of Abaqus. Run `abaqus upgrade `
```

```
`-job <*newFilename*> -odb <*oldFileName*>` 来升级它。
```

如果输出数据库是由较新版本的 Abaqus 生成的，且 Abaqus 安装需要升级：

```
OdbError: Abaqus installation must be upgraded before this output database can be opened.
```

### 61.32.5 openOdb(...)

此方法打开一个现有的输出数据库（`.odb`）文件并创建一个新的 Odb 对象。

**原型**

```
odb_Odb& openOdb(const odb_String& name,
const odb_String& path, bool readOnly);
```

**必需参数**

*name*

一个 odb_String，指定仓库键。

**可选参数**

*path*

一个 odb_String，指定现有输出数据库（`.odb`）文件的路径。

*readOnly*

一个布尔值，指定文件是否仅允许只读访问或同时允许读写访问。初始值为 False，表示将允许读写访问。

**返回值**

一个 Odb 对象。

**异常**

如果输出数据库是由以前版本的 Abaqus 生成的，需要升级：

```
OdbError: The database is from a previous release of Abaqus. Run `abaqus upgrade `
```

```
`-job <*newFilename*> -odb <*oldFileName*>` 来升级它。
```

如果输出数据库是由较新版本的 Abaqus 生成的，且 Abaqus 安装需要升级：

```
OdbError: Abaqus installation must be upgraded before this output database can be opened.
```

如果文件不是有效的数据库：

```
AbaqusException: Cannot open file <*filename*>.
```

### 61.32.6 upgradeOdb(...)

此方法将现有的 Odb 对象升级到当前版本，并将升级后的 Odb 对象写入文件。此外，Abaqus/CAE 将升级状态的信息写入日志（`*.log`）文件。

**原型**

```
void upgradeOdb(const odb_String& existingOdbPath,
const odb_String& upgradedOdbPath);
```

**必需参数**

*existingOdbPath*

一个 odb_String，指定包含要升级的输出数据库的文件路径。

*upgradedOdbPath*

一个 odb_String，指定将包含升级后的输出数据库的文件路径。

**可选参数**

无。

**返回值**

无

**异常**

如果输出数据库升级失败：

```
OdbError: cannot convert database
```

### 61.32.7 getActiveOdb(...)

此方法旨在用于在 C++ 编写的 Abaqus/Standard 或 Abaqus/Explicit 用户子程序内部使用。它获取分析产品正在使用的对象，并使用户能够在用户子程序内部修改它。如果当前打开了多个输出数据库，此方法将抛出异常。

**原型**

```
odb_Odb& getActiveOdb();
```

**参数**

无。

**返回值**

一个 Odb 对象。

**异常**

如果打开了多个输出数据库文件：

```
OdbError: The getActiveOdb method can only be called if a single odb file is open.
```

如果没有打开输出数据库文件：

```
OdbError: No odb files are open.
```

无。

### 61.32.8 odb_IsA(...)

此方法接受一个类型和一个基础对象，并返回一个布尔值，指示所提供的基础对象的子类型是否与类型参数匹配。此方法在从其容器中获取基础 Section、Profile 或 Amplitude 对象时非常有用。例如，如果用户想确定由 odb_SectionContainer 返回的基础 odb_Section 对象实际上是 odb_BeamSection 类型，他可以使用 odb_BeamSection 作为类型，odb_Section 对象作为基础对象来调用此方法。

**原型**

```
bool odb_IsA(TYPE, const BASETYPE& obj);
```

**必需参数**

*TYPE*

基础类对象的潜在类型。

*obj*

被测试是否为 TYPE 的基础对象。

**可选参数**

无。

**返回值**

一个布尔值。

**异常**

无。

### 61.32.9 odb_dynamicCast(...)

此方法将提供的 Section、Profile 或 Amplitude 转换为指定的子类型。此方法在从适当的容器中获取基础对象并将其转换为子类型以访问该特定子类型的数据成员时非常有用。如果转换不可能，此方法将抛出 odb_BaseException。

**原型**

```
const TYPE& returnObj = odb_dynamicCast(TYPE, const BASETYPE& obj);
```

**必需参数**

*TYPE*

基础类对象的潜在类型。

*obj*

要转换为 TYPE 的基础对象。

**可选参数**

无。

**返回值**

一个 TYPE 类型的对象。

**异常**

如果转换不可能：

```
Bad cast: From BASETYPE To TYPE.
```





