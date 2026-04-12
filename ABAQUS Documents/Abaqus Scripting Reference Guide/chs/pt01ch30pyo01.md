# 30.1 Mdb 对象

Mdb 对象是高级 Abaqus 模型数据库。模型数据库存储模型和分析控制。

**访问**

```
mdb
```

### 30.1.1 Mdb(...)

此构造函数创建一个空的 Mdb 对象。

**路径**

```
Mdb
```

**必需参数**

无。

**可选参数**

*pathName*

String，指定保存模型数据库到文件时使用的路径。如果不提供文件扩展名，`.cae` 会自动附加到路径。默认值为空字符串。

**返回值**

Mdb 对象。

**异常**

无。

### 30.1.2 importDxf(...)

此方法从包含 dxf 格式（AutoCAD）几何体的文件创建 [ConstrainedSketch](pt01ch48pyo01.md) 对象。仅支持有限数量的实体。此格式仅在没有其他格式可用时使用。

**路径**

```
importDxf
```

**必需参数**

*fileName*

String，指定要打开的 dxf 文件的路径。

**可选参数**

无。

**返回值**

Mdb 对象。

**异常**

无。

### 30.1.3 openMdb(...)

此方法打开现有的模型数据库文件。

**路径**

```
openMdb
```

**必需参数**

*pathName*

String，指定要打开的模型数据库文件的路径。如果不提供文件扩展名，Abaqus/CAE 会尝试打开附加了 `.cae` 的文件。

**可选参数**

无。

**返回值**

Mdb 对象。

**异常**

如果文件是无效的模型数据库：

```
MdbError: invalid model database.
```

如果文件包含的模型数据库来自当前运行的 Abaqus 版本以外的 Abaqus 版本：

```
MdbError: incompatible release number, expected                             *<Abaqus release>*, got                            *<earlier or later Abaqus release>*                
```

如果模型数据库文件已以写入模式打开：

```
MdbError: cannot open file: May be in use by another CAE session
```

如果命令因上述原因以外的原因未能打开模型数据库文件：

```
MdbError: cannot open file...
```

### 30.1.4 openAcis(...)

此方法从包含 ACIS 格式几何体的文件创建 [AcisFile](pt01ch37pyo03.md) 对象。此对象随后由 `PartFromGeometryFile` 方法使用。

**路径**

```
openAcis
```

**必需参数**

*fileName*

String，指定要打开的 ACIS 文件的路径。

**可选参数**

*scaleFromFile*

Boolean，指定是否使用从 ACIS 文件读取的变换来缩放、旋转和平移部件。默认值为 OFF。

**返回值**

AcisFile 对象。

**异常**

文件来自比 CAE 内核更新的 ACIS 版本。

```
Texterror: ACIS File version exceeds Kernel.
```

ACIS 文件中的数据已损坏。

```
Texterror: Failed to read ACIS file.
```

### 30.1.5 openCatia(...)

此方法从包含 CATIA V4 格式或 V5 格式几何体的文件创建 [AcisFile](pt01ch37pyo03.md) 对象。此对象随后由 `PartFromGeometryFile` 方法使用。

**路径**

```
openCatia
```

**必需参数**

*fileName*

String，指定要打开的 CATIA 文件的路径。

**可选参数**

*topology*

SymbolicConstant，指定要从文件读取的数据以及要创建的部件的拓扑。可能的值为 SOLID、SHELL 和 WIRE。如果 *topology*=SOLID，Abaqus/CAE 会尝试附加单元以创建实体。如果 *topology*=SHELL，Abaqus/CAE 将体构建为壳实体而不是实体实体。如果 CATIA V4 格式文件包含不同拓扑，则仅从文件导入所选拓扑。默认值为 SOLID。

*convertUnits*

SymbolicConstant，指定是否保留原始单位。可能的值为 ON 和 OFF。默认值为 OFF。

*combineBodies*

Boolean，指定是否合并 CATPart 文件中的体。如果要合并的体接触或重叠，将导致无效实体。对于 V4 格式和 CATProduct 文件，此选项将被忽略。

**返回值**

AcisFile 对象。

**异常**

无。

### 30.1.6 openEnf(...)

此方法从包含由 CATIA V5、I-DEAS 或 Pro/ENGINEER 创建的 Elysium Neutral File 格式几何体的文件创建 [AcisFile](pt01ch37pyo03.md) 对象。此对象随后由 `PartFromGeometryFile` 方法使用。

**路径**

```
openEnf
```

**必需参数**

*fileName*

String，指定由 I-DEAS、Pro/ENGINEER 或 CATIA V5 创建的 Elysium Neutral File 的路径。

*fileType*

String，指定创建文件的 CAD 系统类型。可能的值为 "ideas"、"proe" 或 "catiav5"。

**可选参数**

*topology*

SymbolicConstant，指定要从文件读取的数据以及要创建的部件的拓扑。可能的值为 SOLID、SHELL 和 WIRE。如果 *topology*=SOLID，Abaqus/CAE 会尝试附加单元以创建实体。如果 *topology*=SHELL，Abaqus/CAE 将体构建为壳实体而不是实体实体。默认值为 SOLID。

*convertUnits*

Boolean，指定部件尺寸是否应转换为毫米。默认值为 OFF。

**返回值**

AcisFile 对象。

**异常**

无。

### 30.1.7 openIges(...)

此方法从包含 IGES 格式几何体的文件创建 [AcisFile](pt01ch37pyo03.md) 对象。此对象随后由 `PartFromGeometryFile` 方法使用。

**路径**

```
openIges
```

**必需参数**

*fileName*

String，指定要打开的 IGES 文件的路径。

**可选参数**

*trimCurve*

SymbolicConstant，指定用于定义绑定参数曲面的修剪曲线的方法。可能的值为：
- DEFAULT，根据 IGES 文件的内容指定其中之一。
- PARAMETRIC_DATA，使用被修剪曲面的参数空间。
- THREED_DATA，使用实空间——部件的坐标系以及修剪曲线位于参数曲面上的指示。

默认值为 DEFAULT。

*scaleFromFile*

SymbolicConstant，指定导入的几何体是否需要使用 IGES 文件中可用的单位信息进行缩放。可能的值为 ON 和 OFF。默认值为 OFF。当此参数设置为 ON 时，几何体将根据 IGES 文件中指定的单位系统缩放到毫米。

*msbo*

Boolean，指定 IGES 文件是否包含 MSBO（流形实体 B-Rep 对象）实体。默认值为 False。

*includedLayers*

Int 序列，指定将从 IGES 文件翻译以构建部件的实体所在的层级或图层。默认是包含所有图层。

*topology*

SymbolicConstant，指定要从文件读取的数据以及要创建的部件的拓扑。可能的值为 SOLID、SHELL 和 WIRE。如果 *topology*=SOLID，Abaqus/CAE 会尝试附加单元以创建实体。如果 *topology*=SHELL，Abaqus/CAE 将体构建为壳实体而不是实体实体。默认值为 SOLID。

*uniteWires*

SymbolicConstant，指定导入的线是否需要合并。可能的值为 ON 和 OFF。默认值为 ON。导入草图时，此值设置为 OFF。

**返回值**

AcisFile 对象。

**异常**

IGES 文件中的数据已损坏。

```
Texterror: Failed to read IGES file.
```

### 30.1.8 openParasolid(...)

此方法从包含 Parasolid 格式几何体的文件创建 [AcisFile](pt01ch37pyo03.md) 对象。此对象随后由 `PartFromGeometryFile` 方法使用。

**路径**

```
openParasolid
```

**必需参数**

*fileName*

String，指定要打开的 Parasolid 文件的路径。

**可选参数**

*topology*

SymbolicConstant，指定要从文件读取的数据以及要创建的部件的拓扑。可能的值为 SOLID、SHELL 和 WIRE。如果 *topology*=SOLID，Abaqus/CAE 会尝试附加单元以创建实体。如果 *topology*=SHELL，Abaqus/CAE 将体构建为壳实体而不是实体实体。默认值为 SOLID。

**返回值**

AcisFile 对象。

**异常**

无。

### 30.1.9 openStep(...)

此方法从包含 STEP 格式几何体的文件创建 [AcisFile](pt01ch37pyo03.md) 对象。此对象随后由 `PartFromGeometryFile` 方法使用。

**路径**

```
openStep
```

**必需参数**

*fileName*

String，指定要打开的 STEP 文件的路径。

**可选参数**

*scale*

Float，指定要应用于导入几何实体的缩放因子。默认值为 1.0。

**返回值**

AcisFile 对象。

**异常**

STEP 文件中的数据已损坏。

```
Texterror: Failed to read STEP file.
```

### 30.1.10 openVda(...)

此方法从包含 VDA-FS 格式几何体的文件创建 [AcisFile](pt01ch37pyo03.md) 对象。此对象随后由 `PartFromGeometryFile` 方法使用。

**路径**

```
openVda
```

**必需参数**

*fileName*

String，指定要打开的 VDA-FS 文件的路径。

**可选参数**

无。

**返回值**

AcisFile 对象。

**异常**

VDA-FS 文件中的数据已损坏。

```
Texterror: Failed to read VDA file.
```

### 30.1.11 close()

此方法关闭打开的 Mdb 对象，但不将 Mdb 对象保存到磁盘。关闭 Mdb 对象后，此方法会创建一个新的未命名空 Mdb 对象。

**参数**

无。

**返回值**

无

**异常**

无。

### 30.1.12 save()

此方法将 Mdb 对象保存到磁盘，位置由 *pathName* 指定（*pathName* 是 Mdb 对象的成员）。

**参数**

无。

**返回值**

无

**异常**

如果 *pathName* 为空：

```
MdbError: cannot save file: pathname member is empty
```

如果 *pathName* 为 `abaqus.cae`：

```
MdbError: "abaqus.cae" is an invalid CAE filename.
```

如果命令因上述原因以外的原因未能将 Mdb 对象保存到磁盘：

```
MdbError: cannot save file...
```

### 30.1.13 saveAs(...)

此方法将 Mdb 对象保存到磁盘的指定位置。

**必需参数**

*pathName*

String，指定保存模型数据库到文件时使用的路径。如果不提供文件扩展名，`.cae` 会自动附加到路径。

**可选参数**

无。

**返回值**

无

**异常**

如果 *pathName* 为 `abaqus.cae`：

```
MdbError: "abaqus.cae" is an invalid CAE filename.
```

如果命令因上述原因以外的原因未能将 Mdb 对象保存到磁盘：

```
MdbError: cannot save file...
```

### 30.1.14 openAuxMdb(...)

此方法打开磁盘上指定位置的辅助 Mdb 对象。这使得辅助 Mdb 中的模型可以复制到当前 Mdb 中。

**必需参数**

*pathName*

String，指定要打开的辅助 Mdb 的路径。如果不提供文件扩展名，`.cae` 会自动附加到路径。

**可选参数**

无。

**返回值**

无

**异常**

如果文件是无效的模型数据库：

```
MdbError: invalid model database.
```

如果文件包含的模型数据库来自当前运行的 Abaqus 版本以外的 Abaqus 版本：

```
MdbError: incompatible release number, expected                             *<Abaxis release>*, got                             *<earlier or later Abaqus release>*.                         
```

如果命令因上述原因以外的原因未能打开模型数据库文件：

```
MdbError: cannot open file...
```

### 30.1.15 closeAuxMdb()

此方法关闭先前使用 `openAuxMdb` 命令打开的辅助 Mdb。

**参数**

无。

**返回值**

无

**异常**

如果辅助 Mdb 之前未打开。

```
MdbError: The auxiliary Mdb was not opened..
```

### 30.1.16 getAuxMdbModelNames()

此方法返回先前使用 `openAuxMdb` 命令打开的辅助 Mdb 中存在的模型名称列表。

**参数**

无。

**返回值**

辅助 Mdb 中存在的模型名称列表。

**异常**

如果辅助 Mdb 之前未打开。

```
MdbError: The auxiliary Mdb was not opened..
```

### 30.1.17 copyAuxMdbModel(...)

此方法从先前使用 `openAuxMdb` 命令打开的辅助 Mdb 复制指定模型。

**必需参数**

*fromName*

String，指定要复制的辅助 Mdb 中的模型名称。

**可选参数**

*toName*

String，指定复制到 Mdb 后要赋予模型的名称。如果未指定此参数，则 *toName* 被假定为与 *fromName* 相同。如果 Mdb 中已存在名为 *toName* 的模型，它将被覆盖。

**返回值**

无

**异常**

如果辅助 Mdb 之前未打开。

```
MdbError: The auxiliary Mdb was not opened.
```

如果模型 fromName 不存在于辅助 Mdb 中。

```
KeyError: fromName does not exist.
```

### 30.1.18 成员

Mdb 对象的成员与 [Mdb](pt01ch30pyo01.md#ker-mdb-mdb-pyc) 方法的参数具有相同的名称和描述。

此外，Mdb 对象可以具有以下成员：

*version*

Int，指定内存中 Mdb 对象的版本号。

*lastChangedCount*

Float，指定与 Mdb 对象关联的计数器的值。计数器指示 Mdb 对象上次更改的时间。

*jobs*

[Job](pt01ch26pyo01.md) 对象仓库。

*adaptivityProcesses*

[AdaptivityProcess](pt01ch02pyo06.md) 对象仓库。

*coexecutions*

[Coexecution](pt01ch26pyo06.md) 对象仓库。

*optimizationProcesses*

[OptimizationProcess](pt01ch26pyo07.md) 对象仓库。

*meshEditOptions*

[MeshEditOptions](pt01ch18pyo03.md) 对象，指定编辑部件或部件实例上的网格时的撤销/重做行为。

*models*

[Model](pt01ch33pyo01.md) 对象仓库。

*customData*

[RepositorySupport](pt01ch14pyo02.md) 对象。

*annotations*

[Annotation](pt01ch05pyo01.md) 对象仓库。
