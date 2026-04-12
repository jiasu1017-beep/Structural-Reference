# 34.1 Odb 对象

Odb 对象是输出数据库（ODB）文件的内存中表示形式。

**访问**

```
import odbAccess
session.odbs[*name*]
```

### 34.1.1 Odb(...)

此方法创建一个新的 Odb 对象。

**路径**

```
session.Odb
```

**必要参数**

*name*

一个字符串，指定仓库键。

**可选参数**

*analysisTitle*

一个字符串，指定输出数据库的标题。默认值为空字符串。

*description*

一个字符串，指定输出数据库的描述。默认值为空字符串。

*path*

一个字符串，指定将写入新输出数据库（`.odb`）文件的文件路径。默认值为空字符串。

**返回值**

Odb 对象。

**异常**

无。

### 34.1.2 close()

此方法关闭输出数据库。

**参数**

无。

**返回值**

无

**异常**

无。

### 34.1.3 getFrame(...)

此方法返回指定时间、频率或模式的帧。它不会在帧之间插值。该方法不适用于包含不同域的步骤的 Odb 对象或包含负载情况特定数据的步骤的 Odb 对象。

**必要参数**

*frameValue*

一个 Double，指定需要帧的值。*frameValue* 可以是总时间或频率。

**可选参数**

*match*

一个 SymbolicConstant，指定当精确帧值不存在时返回哪个帧。可能的值为 CLOSEST、BEFORE、AFTER 和 EXACT。默认值为 CLOSEST。

当 *match*=CLOSEST 时，Abaqus 返回最接近的帧。如果请求的帧值恰好在两帧之间，Abaqus 返回该值之后的帧。

当 *match*=EXACT 时，如果精确帧值不存在，Abaqus 会引发异常。

**返回值**

一个 [OdbFrame](pt01ch34pyo14.md) 对象。

**异常**

如果找不到精确帧：

```
OdbError: Frame not found.
```

### 34.1.4 save()

此方法将输出保存到输出数据库（`.odb`）文件。

**参数**

无。

**返回值**

无

**异常**

OdbError

```
Database save failed. The database was opened as read-only. Modification of data is not permitted.
```

### 34.1.5 update()

此方法用于在 Abaqus 分析写入关联输出数据库时更新内存中的 Odb 对象。`update` 检查自打开或上次更新以来是否有其他步骤被写入输出数据库。如果有其他步骤被写入输出数据库，`update` 将它们添加到 Odb 对象中。

**参数**

无。

**返回值**

一个布尔值，指定是否有其他步骤或帧被添加到 Odb 对象。

**异常**

无。

### 34.1.6 成员

Odb 对象的成员与 [Odb](pt01ch34pyo01.md#ker-odb-odb-pyc) 方法的参数具有相同的名称和描述。

此外，Odb 对象可以具有以下成员：

*isReadOnly*

一个布尔值，指定输出数据库是否以只读访问方式打开。

*amplitudes*

[Amplitude](pt01ch03pyo01.md) 对象的仓库。

*filters*

[Filter](pt01ch22pyo01.md) 对象的仓库。

*rootAssembly*

一个 [OdbAssembly](pt01ch34pyo12.md) 对象。

*jobData*

一个 [JobData](pt01ch34pyo11.md) 对象。

*parts*

[OdbPart](pt01ch34pyo19.md) 对象的仓库。

*materials*

[Material](pt01ch29pyo01.md) 对象的仓库。

*steps*

[OdbStep](pt01ch34pyo24.md) 对象的仓库。

*sections*

[Section](pt01ch46pyo01.md) 对象的仓库。

*sectionCategories*

[SectionCategory](pt01ch34pyo27.md) 对象的仓库。

*sectorDefinition*

一个 [SectorDefinition](pt01ch34pyo29.md) 对象。

*userData*

一个 [UserData](pt01ch34pyo30.md) 对象。

*customData*

一个 [RepositorySupport](pt01ch14pyo02.md) 对象。

*profiles*

[Profile](pt01ch08pyo01.md) 对象的仓库。
