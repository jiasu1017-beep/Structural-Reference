# 30.2 Mdb 命令

以下命令将模型数据库（`.cae`）升级到当前版本，并将升级后的模型数据库写入新文件。

### 30.2.1 upgradeMdb(...)

此方法将现有 Mdb 对象升级到当前版本，并将升级后的 Mdb 对象写入文件。此外，Abaqus/CAE 将有关升级状态的信息写入日志文件（` *upgradedMdbPath*.log`）。

**路径**

```
upgradeMdb
```

**必需参数**

*existingMdbPath*

String，指定包含要升级的模型数据库的文件路径。

*upgradedMdbPath*

String，指定将包含升级模型数据库的文件路径。

**可选参数**

无。

**返回值**

无

**异常**

如果模型数据库升级失败：

```
MdbError: cannot convert file
```

### 30.2.2 CombineOptResults(...)

此方法组合现有 ODB 文件中每个优化周期的结果，并写入合并后的 ODB 文件。

**路径**

```
CombineOptResults
```

**必需参数**

*optResultLocation*

String，指定存在优化结果的文件夹路径。

**可选参数**

*optIter*

SymbolicConstant，指定应合并结果的优化周期。可能的值为 INITIAL_AND_LAST、NONE、ALL、LAST、EVERY_NCYCLES、SPECIFY。

默认值为 INITIAL_AND_LAST。

*nValues*

Int 或 Int 元组，指定应合并结果的优化周期。此参数仅在 *optIter* 选择 EVERY_NCYCLES 或 SPECIFY 时使用。

默认值为 ALL。

*models*

字符串元组，指定执行结果合并的 *models* 列表。

默认值为 ALL。

*steps*

字符串元组，指定从所选 *models* 中要包含在 odb 合并中的步骤列表。

默认值为 ALL。

*analysisFieldVariables*

字符串元组，指定要包含在 odb 合并中的 *analysisFieldVariables* 列表。

默认值为 ALL。

*includeResultsFrom*

SymbolicConstant，指定结果将合并到的目标 odb。可能的值为 ORIGINAL_MODEL、FIRST 或 LAST。

默认值为 FIRST。

*originalModel*

String，如果 *includeResultsFrom* 设置为 ORIGINAL_MODEL，则指定目标 odb 的路径。
