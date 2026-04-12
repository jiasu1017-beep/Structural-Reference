# 61.1 Odb 对象





Odb 对象是输出数据库（ODB）文件的内存表示。

**访问**

```
odb
```

### 61.1.1 Odb(...)

此方法创建一个新的 Odb 对象。

**路径**

```
Odb
```

**原型**

```
odb_Odb&
Odb(const odb_String& name,
    const odb_String& analysisTitle,
    const odb_String& description,
    const odb_String& path);
```

**必需参数**

*name*

一个 odb_String，指定仓库键。

**可选参数**

*analysisTitle*

一个 odb_String，指定输出数据库的标题。默认值为空字符串。

*description*

一个 odb_String，指定输出数据库的描述。默认值为空字符串。

*path*

一个 odb_String，指定将写入新输出数据库（`.odb`）文件的路径。默认值为空字符串。

**返回值**

一个 Odb 对象。

**异常**

无。

### 61.1.2 close()

此方法关闭一个输出数据库。

**原型**

```
void
close();
```

**参数**

无。

**返回值**

无

**异常**

无。

### 61.1.3 getFrame(...)

此方法返回指定时间、频率或模式的帧。它不会在帧之间插值。该方法不适用于包含具有不同域的步骤的 Odb 对象，也不适用于包含具有载荷情况特定数据的步骤的 Odb 对象。

**原型**

```
odb_Frame
getFrame(double frameValue,
         odb_Enum::odb_MatchEnum match);
```

**必需参数**

*frameValue*

一个 Double，指定需要帧的值。*frameValue* 可以是总时间或频率。

**可选参数**

*match*

一个 odb_Enum::odb_MatchEnum，指定如果没有在确切帧值处存在帧，则返回哪个帧。可能的值为 odb_Enum::CLOSEST、odb_Enum::BEFORE、odb_Enum::AFTER 和 odb_Enum::EXACT。默认值为 odb_Enum::CLOSEST。

当 *match*=odb_Enum::CLOSEST 时，Abaqus 返回最接近的帧。如果请求的帧值恰好在两个帧之间，Abaqus 返回该值之后的帧。

当 *match*=odb_Enum::EXACT 时，如果确切帧值不存在，Abaqus 会抛出异常。

**返回值**

一个 [OdbFrame](pt02ch61pyo15.md) 对象。

**异常**

如果找不到确切帧：

```
OdbError: Frame not found.
```

### 61.1.4 save()

此方法将输出保存到输出数据库（`.odb`）文件中。

**原型**

```
void
save();
```

**参数**

无。

**返回值**

无

**异常**

OdbError

```
Database save failed. The database was opened as read-only. Modification of data is not permitted.
```

### 61.1.5 update()

此方法在 Abaqus 分析将数据写入关联的输出数据库时，用于更新内存中的 Odb 对象。`update` 检查自打开或上次更新以来是否有其他步骤写入输出数据库。如果有其他步骤写入输出数据库，`update` 会将它们添加到 Odb 对象中。

**原型**

```
bool
update();
```

**参数**

无。

**返回值**

一个布尔值，指定是否向 Odb 对象添加了其他步骤或帧。

**异常**

无。

### 61.1.6 hasSectorDefinition()

此方法检查是否存在有效的 [SectorDefinition](pt02ch61pyo29.md) 对象，指示循环对称模型。

**原型**

```
bool
hasSectorDefinition();
```

**参数**

无。

**返回值**

一个布尔值，指定是否可以获得有效的扇区定义。

**异常**

无。

### 61.1.7 成员

Odb 对象的成员与 [Odb](pt02ch61pyo01.md#ker-odb-odb-cpp) 方法的参数具有相同的名称和描述。

此外，Odb 对象可以具有以下成员：

**原型**

```
odb_String name() const;
               odb_String analysisTitle() const;
               odb_String description() const;
               odb_String path() const;
               bool isReadOnly() const;
               odb_Assembly& rootAssembly();
               odb_JobData jobData() const;
               odb_PartRepository& parts();
               odb_StepRepository& steps();
               odb_SectionCategoryRepository& sectionCategories();
               odb_SectorDefinition& sectorDefinition();
               odb_InteractionRepository& interactions();
               odb_InteractionPropertyRepository& interactionProperties();
               odb_ConstraintRepository& constraints();
```

*isReadOnly*

一个布尔值，指定输出数据库是否以只读方式打开。

*rootAssembly*

一个 [OdbAssembly](pt02ch61pyo13.md) 对象。

*jobData*

一个 [JobData](pt02ch61pyo12.md) 对象。

*parts*

[OdbPart](pt02ch61pyo20.md) 对象的仓库。

*steps*

[OdbStep](pt02ch61pyo25.md) 对象的仓库。

*sectionCategories*

[SectionCategory](pt02ch61pyo27.md) 对象的仓库。

*sectorDefinition*

一个 [SectorDefinition](pt02ch61pyo29.md) 对象。

*userData*

一个 [UserData](pt02ch61pyo30.md) 对象。





