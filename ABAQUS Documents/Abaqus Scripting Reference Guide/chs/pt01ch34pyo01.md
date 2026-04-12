# 34.31 Odb 命令

Odb 命令执行以下操作：
- 确定输出数据库（`.odb`）文件是否需要升级到当前版本。
- 确定多个字段上输出变量的极值；例如，在多个负载情况上。
- 打开现有的输出数据库文件并创建新的 Odb 对象。
- 将输出数据库文件升级到当前版本并将升级后的输出数据库写入新文件。

### 34.31.1 isUpgradeRequiredForOdb(...)

此方法确定输出数据库文件是否需要升级到当前版本。

您可以使用以下任一技术访问此方法：
- 从在 Abaqus/CAE 外部运行的脚本。例如，``` import odbAccess needsUpgrade = odbAccess.isUpgradeRequiredForOdb( upgradeRequiredOdbPath='myOdb.odb') ```
- 从 Abaqus/CAE 中的 Visualization 模块。例如，``` import visualization needsUpgrade = session.isUpgradeRequiredForOdb( upgradeRequiredOdbPath='myOdb.odb') ```

**必要参数**

*upgradeRequiredOdbPath*

一个字符串，指定要测试的输出数据库文件的路径。该测试确定输出数据库是否需要升级到当前版本。

**可选参数**

无。

**返回值**

一个布尔值，指示测试结果。值为 True 表示输出数据库需要升级到当前版本。

**异常**

无。

### 34.31.2 maxEnvelope(...)

检索多个字段上输出变量的最大值。

**必要参数**

`maxEnvelope` 方法不使用关键字参数。

| 参数 |
| --- |
| 将从中计算最大值的类似 fieldOutput 对象列表。 |
| 一个 SymbolicConstant，指定比较向量或张量时使用的不变量或分量标签。可能的值为：- MAGNITUDE - MISES - TRESCA - PRESS - INV3 - MAX_PRINCIPAL - MID_PRINCIPAL - MIN_PRINCIPAL 如果字段是向量或张量，您必须提供此参数或以下参数。 |
| 一个字符串，指定用于选择最大值的张量或向量的分量。 |

**可选参数**

无。

**返回值**

两个 fieldOutput 对象的序列。第一个 fieldOutput 对象包含最大值。第二个 fieldOutput 对象包含包含最大值的字段的索引。索引遵循作为函数参数提供的 fieldOutput 对象列表中字段的顺序。

**异常**

OdbError

TypeError

```
This function takes no keyword arguments.
```

### 34.31.3 minEnvelope(...)

检索多个字段上输出变量的最小值。

**必要参数**

`minEnvelope` 方法不使用关键字参数。

| 参数 |
| --- |
| 将从中计算最大值的类似 fieldOutput 对象列表。 |
| 一个 SymbolicConstant，指定比较向量或张量时使用的不变量或分量标签。可能的值为：- MAGNITUDE - MISES - TRESCA - PRESS - INV3 - MAX_PRINCIPAL - MID_PRINCIPAL - MIN_PRINCIPAL 如果字段是向量或张量，您必须提供此参数或以下参数。 |
| 一个字符串，指定用于选择最小值的张量或向量的分量。 |

**可选参数**

无。

**返回值**

两个 fieldOutput 对象的序列。第一个 fieldOutput 对象包含最小值。第二个 fieldOutput 对象包含包含最小值的字段的索引。索引遵循作为函数参数提供的 fieldOutput 对象列表中字段的顺序。

**异常**

OdbError

TypeError

```
This function takes no keyword arguments.
```

### 34.31.4 openOdb(...)

此方法打开现有的输出数据库（`.odb`）文件并创建新的 Odb 对象。当在 Abaqus/CAE 外部执行脚本时，通常只能一次打开一个输出数据库。例如，

```
import odbAccess
shockLoadOdb = odbAccess.openOdb(path='myOdb.odb')
```

**必要参数**

*path*

一个字符串，指定现有输出数据库（`.odb`）文件的路径。

**可选参数**

*readOnly*

一个布尔值，指定文件是否仅允许只读访问或同时允许读写访问。初始值为 False，表示将允许读写访问。

*readInternalSets*

一个布尔值，指定文件是否允许访问在数据库上指定为 Internal 的集合。初始值为 False，表示内部集合将不会被读取。

**返回值**

Odb 对象。

**异常**

如果输出数据库是由先前版本的 Abaqus 生成的，需要升级：

```
OdbError: The database is from a previous release of Abaqus. Run `abaqus upgrade -job <*newFilename*> -odb <*oldFileName*>` to upgrade it.
```

如果输出数据库是由更新版本的 Abaqus 生成的，并且需要升级 Abaqus 安装：

```
OdbError: Abaqus installation must be upgraded before this output database can be opened.
```

### 34.31.5 openOdb(...)

此方法打开现有的输出数据库（`.odb`）文件并创建新的 Odb 对象。此方法仅通过 Abaqus/CAE 内的 session 对象访问，并将新的 Odb 对象添加到 `session.odbs` 仓库。此方法允许您同时打开多个输出数据库，并使用仓库键指定特定的输出数据库。例如，

```
import visualization
session.openOdb(name='myOdb', path='stress.odb', readOnly=True)
```

**必要参数**

*name*

一个字符串，指定仓库键。如果 *name* 与输出数据库（`.odb`）文件的 *path* 不同，则必须同时指定 *path*。此外，为了支持接口的向后兼容性，如果省略 *name* 参数，则 *path* 和 *name* 将被视为相同。

**可选参数**

*path*

一个字符串，指定现有输出数据库（`.odb`）文件的路径。

*readOnly*

一个布尔值，指定文件是否仅允许只读访问或同时允许读写访问。当从 Abaqus/CAE 打开输出数据库文件时，初始值为 TRUE，表示仅允许只读访问。

**返回值**

Odb 对象。

**异常**

如果输出数据库是由先前版本的 Abaqus 生成的，需要升级：

```
OdbError: The database is from a previous release of Abaqus.
```

```
Run `abaqus upgrade -job <*newFilename*> -odb <*oldFileName*>` to upgrade it.
```

如果输出数据库是由更新版本的 Abaqus 生成的，并且需要升级 Abaqus 安装：

```
OdbError: Abaqus installation must be upgraded before this
```

```
output database can be opened.
```

如果文件不是有效的数据库：

```
AbaqusError: Cannot open file <*filename*>.
```

### 34.31.6 upgradeOdb(...)

此方法将现有 Odb 对象升级到当前版本，并将 Odb 对象的升级版本写入文件。此外，Abaqus/CAE 将有关升级状态的信息写入日志（`*.log`）文件。

您可以使用以下任一技术访问此方法：
- 从在 Abaqus/CAE 外部运行的脚本。例如，``` import odbAccess odbAccess.upgradeOdb(existingOdbPath='oldOdb', upgradedOdbPath='upgradedOdb') ```
- 从 Abaqus/CAE 中的 session 对象。例如，``` import visualization session.upgradeOdb(existingOdbPath='oldOdb', upgradedOdbPath='upgradedOdb') ```

**必要参数**

*existingOdbPath*

一个字符串，指定包含要升级的输出数据库的文件的路径。

*upgradedOdbPath*

一个字符串，指定将包含升级后的输出数据库的文件的路径。

**可选参数**

无。

**返回值**

无

**异常**

如果输出数据库升级失败：

```
OdbError: cannot convert database
```
