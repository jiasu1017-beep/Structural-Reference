# 33.1 Model 对象

启动会话时，Abaqus 会创建一个名为 `Model-1` 的 Model 对象。

**访问**

```
mdb.models[*name*]
```

### 33.1.1 Model(...)

此方法创建一个 Model 对象。

**路径**

```
mdb.Model
```

**必要参数**

*name*

一个字符串，指定仓库键。

**可选参数**

*description*

一个字符串，指定 Model 对象的目的和内容。默认值为空字符串。

*stefanBoltzmann*

`None` 或一个 Float，指定 Stefan-Boltzmann 常数。默认值为 `None`。

*absoluteZero*

`None` 或一个 Float，指定绝对零常数。默认值为 `None`。

*waveFormulation*

一个 SymbolicConstant，指定声学问题中使用的入射波公式类型。可能的值为 NOT_SET、SCATTERED 和 TOTAL。默认值为 NOT_SET。

*modelType*

一个 SymbolicConstant，指定分析模型类型。可能的值为 STANDARD_EXPLICIT、CFD 和 ELECTROMAGNETIC。默认为 STANDARD_EXPLICIT。

*universalGas*

`None` 或一个 Float，指定通用气体常数。默认值为 `None`。

**返回值**

Model 对象。

**异常**

无。

### 33.1.2 ModelFromInputFile(...)

此方法通过读取输入文件中的关键字并创建相应的 Abaqus/CAE 对象来创建 Model 对象。

**路径**

```
mdb.ModelFromInputFile
```

**必要参数**

*name*

一个字符串，指定仓库键。

*inputFileName*

一个字符串，指定要解析到新模型中的输入文件的名称（包括 `.inp` 扩展名）。如果该字符串位于另一个目录中，也可以是输入文件的完整路径。

**可选参数**

无。

**返回值**

Model 对象。

**异常**

无。

### 33.1.3 ModelFromOdbFile(...)

此方法通过读取输出数据库并创建任何相应的 Abaqus/CAE 对象来创建 Model 对象。

**路径**

```
mdb.ModelFromOdbFile
```

**必要参数**

*name*

一个字符串，指定仓库键。

*odbFileName*

一个字符串，指定要读入新模型的输出数据库文件的名称（包括 `.odb` 扩展名）。如果该字符串位于另一个目录中，也可以是输出数据库文件的完整路径。

**可选参数**

无。

**返回值**

Model 对象。

**异常**

无。

### 33.1.4 ModelFromNastranFile(...)

此方法通过读取 Nastran 批量数据文件或 Nastran 输入文件中的关键字并创建任何相应的 Abaqus/CAE 对象来创建 Model 对象。默认值在下面讨论，也可以在用于从 Nastran 到 Abaqus 的翻译器的 Abaqus 环境文件中定义。有关更多信息，请参阅《Abaqus Analysis User's Guide》第 3.2.28 节"将 Nastran 批量数据文件翻译为 Abaqus 输入文件"。

**路径**

```
mdb.ModelFromNastranFile
```

**必要参数**

*modelName*

一个字符串，指定仓库键。

*inputFileName*

一个字符串，指定要读入新模型的 Nastran 输入文件的名称（包括 `.bdf、.dat、.nas、.nastran、.blk、.bulk` 扩展名）。如果该字符串位于另一个目录中，也可以是 Nastran 输入文件的完整路径。

**可选参数**

*sectionConsolidation*

一个 SymbolicConstant，指定用于创建壳截面的是方法。可能的值为 PRESERVE_SECTION、GROUP_BY_MATERIAL 和 NONE。如果使用 PRESERVE_SECTION，则为每个壳属性 ID 创建一个对应的 Abaqus 截面。如果使用 GROUP_BY_MATERIAL，则为所有引用相同材料的均质元素创建一个 Abaqus 截面。在这两种情况下，材料方向和偏移都使用离散场创建。如果使用 NONE，则为每个方向、材料偏移和/或厚度的组合创建一个单独的壳截面。默认为 PRESERVE_SECTION。

*preIntegratedShell*

一个布尔值，指定是否为壳单元默认创建预集成壳截面。默认值为 OFF。

*weightMassScaling*

一个布尔值，指定是否使用 Nastran 数据行 PARAM、WTMASS 的值作为在 Abaqus 输入文件中创建的所有密度、质量和转动惯量值的乘数。默认值为 ON。

*loadCases*

一个布尔值，指定是否为线性静态分析的每个 SUBCASE 翻译为 [*LOAD CASE](../key/key-link.md#usb-kws-hloadcase) 选项，并将所有此类 [*LOAD CASE](../key/key-link.md#usb-kws-hloadcase) 选项分组在单个 [*STEP](../key/key-link.md#usb-kws-hstep) 选项中。默认值为 ON。

*coupleBeamOffsets*

一个布尔值，指定是否将梁单元连接性翻译为偏移位置处的新节点，并刚性耦合新节点和原始节点。如果不翻译，梁单元偏移将翻译为 [*CENTROID](../key/key-link.md#usb-kws-mcentroid) 和 [*SHEAR CENTER](../key/key-link.md#usb-kws-mshearcenter) 选项，它们是 [*BEAM GENERAL SECTION](../key/key-link.md#usb-kws-mbeamgensect) 选项的子选项。默认值为 ON。当梁单元引用 PBARL 或 PBEAML 属性时，或者当梁偏移在梁轴方向有显著分量时，此参数的设置始终为 ON。

*cbar*

一个字符串，指定从 CBAR 和 CBEAM 单元创建的 2 节点梁。可能的值为 B31 和 B33。默认为 B31。

*cquad4*

一个字符串，指定从 CQUAD4 单元创建的 4 节点壳。可能的值为 S4 和 S4R。默认为 S4。如果选择减缩积分单元，则自动应用增强沙漏公式。

*chexa*

一个字符串，指定从 CHEXA 单元创建的 8 节点砖块。可能的值为 C3D8I、C3D8 和 C3D8R。默认为 C3D8I。如果选择减缩积分单元，则自动应用增强沙漏公式。

*ctetra*

一个字符串，指定从 CTETRA 单元创建的 10 节点四面体。可能的值为 C3D10 和 C3D10M。默认为 C3D10。

*keepTranslatedFiles*

一个布尔值，指定在从 Nastran 输入文件创建模型后是否保留生成的 Abaqus 输入文件。默认值为 ON。

**返回值**

Model 对象。

**异常**

无。

### 33.1.5 setValues(...)

此方法修改 Model 对象。

**必要参数**

无。

**可选参数**

*description*

一个字符串，指定 Model 对象的目的和内容。默认值为空字符串。

*noPartsInputFile*

一个布尔值，指定是否在写入输入文件时不包含部件和装配体。默认值为 OFF。

*absoluteZero*

`None` 或一个 Float，指定绝对零常数。默认值为 `None`。

*stefanBoltzmann*

`None` 或一个 Float，指定 Stefan-Boltzmann 常数。默认值为 `None`。

*waveFormulation*

一个 SymbolicConstant，指定声学问题中使用的入射波公式类型。可能的值为 NOT_SET、SCATTERED 和 TOTAL。默认值为 NOT_SET。

*universalGas*

`None` 或一个 Float，指定通用气体常数。默认值为 `None`。

*restartJob*

一个字符串，指定生成重启数据的作业名称。

*restartStep*

一个字符串，指定重启分析将开始的步骤名称。

*restartIncrement*

一个整数，指定重启分析将开始的增量、间隔、迭代或循环。要选择步骤的末尾，请使用 SymbolicConstant STEP_END。

*endRestartStep*

一个布尔值，指定由 *restartStep* 指定的步骤应在由 *restartIncrement* 指定的增量处终止。

*globalJob*

一个字符串，指定为全局模型生成结果的作业名称。

*shellToSolid*

一个布尔值，指定壳全局模型驱动实体子模型。

**返回值**

无

**异常**

无。

### 33.1.6 成员

Model 对象可以具有以下成员：

*name*

一个字符串，指定仓库键。

*stefanBoltzmann*

`None` 或一个 Float，指定 Stefan-Boltzmann 常数。默认值为 `None`。

*absoluteZero*

`None` 或一个 Float，指定绝对零常数。默认值为 `None`。

*waveFormulation*

一个 SymbolicConstant，指定声学问题中使用的入射波公式类型。可能的值为 NOT_SET、SCATTERED 和 TOTAL。默认值为 NOT_SET。

*universalGas*

`None` 或一个 Float，指定通用气体常数。默认值为 `None`。

*noPartsInputFile*

一个布尔值，指定是否在写入输入文件时不包含部件和装配体。默认值为 OFF。

*restartIncrement*

一个整数，指定重启分析将开始的增量、间隔、迭代或循环。要选择步骤的末尾，请使用 SymbolicConstant STEP_END。

*endRestartStep*

一个布尔值，指定由 *restartStep* 指定的步骤应在由 *restartIncrement* 指定的增量处终止。

*shellToSolid*

一个布尔值，指定壳全局模型驱动实体子模型。

*lastChangedCount*

一个 Float，指定指示模型上次更改时的时间戳。

*description*

一个字符串，指定 Model 对象的目的和内容。默认值为空字符串。

*restartJob*

一个字符串，指定生成重启数据的作业名称。

*restartStep*

一个字符串，指定重启分析将开始的步骤名称。

*globalJob*

一个字符串，指定为全局模型生成结果的作业名称。

*keywordBlock*

一个 [KeywordBlock](pt01ch33pyo02.md) 对象。

*rootAssembly*

一个 [Assembly](pt01ch06pyo01.md) 对象。

*amplitudes*

[Amplitude](pt01ch03pyo01.md) 对象的仓库。

*profiles*

[Profile](pt01ch08pyo01.md) 对象的仓库。

*boundaryConditions*

[BoundaryCondition](pt01ch09pyo01.md) 对象的仓库。

*constraints*

[Constraint](pt01ch13pyo01.md) 对象的仓库。

*analyticalFields*

[AnalyticalField](pt01ch21pyo02.md) 对象的仓库。

*discreteFields*

[DiscreteField](pt01ch21pyo04.md) 对象的仓库。

*predefinedFields*

[PredefinedField](pt01ch42pyo01.md) 对象的仓库。

*interactions*

[Interaction](pt01ch25pyo01.md) 对象的仓库。

*interactionProperties*

[InteractionProperty](pt01ch25pyo48.md) 对象的仓库。

*contactControls*

[ContactControl](pt01ch25pyo16.md) 对象的仓库。

*contactInitializations*

[ContactInitialization](pt01ch25pyo20.md) 对象的仓库。

*contactStabilizations*

[ContactStabilization](pt01ch25pyo23.md) 对象的仓库。

*linkedInstances*

字符串元组的元组，指定当前模型中的链接子 PartInstance 名称到不同模型中对应父 PartInstance 名称的映射。

*linkedParts*

字符串元组的元组，指定当前模型中的链接子 Part 名称到不同模型中对应父 Part 名称的映射。

*loads*

[Load](pt01ch27pyo01.md) 对象的仓库。

*materials*

[Material](pt01ch29pyo01.md) 对象的仓库。

*calibrations*

[Calibration](pt01ch10pyo01.md) 对象的仓库。

*sections*

[Section](pt01ch46pyo01.md) 对象的仓库。

*remeshingRules*

[RemeshingRule](pt01ch02pyo11.md) 对象的仓库。

*sketches*

[ConstrainedSketch](pt01ch48pyo01.md) 对象的仓库。

*parts*

[Part](pt01ch37pyo01.md) 对象的仓库。

*steps*

[Step](pt01ch49pyo01.md) 对象的仓库。

*featureOptions*

[FeatureOptions](pt01ch20pyo02.md) 对象。

*adaptiveMeshConstraints*

[AdaptiveMeshConstraint](pt01ch02pyo01.md) 对象的仓库。

*adaptiveMeshControls*

[AdaptiveMeshControl](pt01ch02pyo03.md) 对象的仓库。

*timePoints*

[TimePoint](pt01ch51pyo09.md) 对象的仓库。

*filters*

[Filter](pt01ch22pyo01.md) 对象的仓库。

*integratedOutputSections*

[IntegratedOutputSection](pt01ch51pyo06.md) 对象的仓库。

*fieldOutputRequests*

[FieldOutputRequest](pt01ch51pyo02.md) 对象的仓库。

*historyOutputRequests*

[HistoryOutputRequest](pt01ch51pyo04.md) 对象的仓库。

*optimizationTasks*

[OptimizationTask](pt01ch36pyo01.md) 对象的仓库。

### 33.1.7 对应的分析关键字

| [*PHYSICAL CONSTANTS](../key/key-link.md#usb-kws-mphysicalconsts) |
| --- |
