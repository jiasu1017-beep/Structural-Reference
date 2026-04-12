# 47.1 Session 对象





Session 对象没有构造函数。Abaqus 在会话启动时创建 *session* 成员。

**访问**

```
session
```

### 47.1.1 setValues(...)

此方法修改 Session 对象。

**必要参数**

无。

**可选参数**

*kernelMemoryLimit*

Float，指定 Abaqus/CAE 内核进程的内存限制值（以 MB 为单位）。如果超过限制，Abaqus/CAE 会显示错误消息。

对于 Windows 32 位系统，如果未设置，默认内存限制值为 1800 MB。除非您使用具有 `/3GB /userva=SizeInMBytes` 引导选项的 Windows 32 位系统来扩展 Abaqus/CAE 可用的内存量，否则不建议增加内存限制。在这种情况下，可以将限制更改为 2800 MB。

如果内核内存大小达到 **abq_ker_memory** 值或机器的虚拟内存限制，将显示以下消息：

```
Operation did not complete due to a memory allocation failure.
```

为了获得最佳性能，内存限制应设置为小于机器上的物理内存量。

允许的最小设置为 256 MB。

**返回值**

无

**异常**

无。

### 47.1.2 enableCADConnection(...)

此方法为指定的 *CADName* 启用关联导入 CAD 连接。

**必要参数**

*CADName*

String，指定 CAD 系统。可用选项有 Pro/ENGINEER、CATIA V5、CATIA V6、NX 和 SolidWorks。

**可选参数**

*portNum*

Integer，指定 CAD 系统用于与 Abaqus/CAE 通信的端口号。如果未指定，将尝试识别开放端口。

**返回值**

用于 CAD 连接的连接端口号。

**异常**

无。

### 47.1.3 isCADConnectionEnabled()

此方法检查 CAD 连接的状态。

**参数**

无。

**返回值**

如果 CAD 连接已启用，则为 True 的布尔值；如果 CAD 连接已禁用，则为 False。

**异常**

无。

### 47.1.4 disableCADConnection(...)

此方法禁用已启用的关联导入 CAD 连接。

**必要参数**

*CADName*

String，指定要禁用关联导入的 CAD 系统。可用选项有 Pro/ENGINEER、CATIA V5、CATIA V6、NX 和 SolidWorks。

**可选参数**

无。

**返回值**

无

**异常**

无。

### 47.1.5 enableParameterUpdate(...)

此方法为指定的 *CADName* 启用带参数的关联导入 CAD 连接。

**必要参数**

*CADName*

String，指定要启用参数更新的 CAD 系统。可用选项有 Pro/ENGINEER。

*CADVersion*

String，指定 CAD 版本。允许的选项有 Wildfire2 和 Wildfire3。

**可选参数**

*CADPort*

Integer，指定 Abaqus/CAE 用于与 CAD 系统通信的端口号。如果未指定，将尝试识别开放端口。此端口号与关联导入接口使用的 *portNum* 不同。

**返回值**

无

**异常**

无。

### 47.1.6 setCADPortNumber(...)

对于给定的 CAD 系统，此方法在 Abaqus/CAE 中保存端口号。此端口号用于将参数信息发送到 CAD 系统。

**必要参数**

*CADName*

String，指定要保存端口号的 CAD 系统。可用选项有 'CATIA V5' 和 'CATIA V6'。

*Port*

Integer，指定 Abaqus/CAE 用于将修改后的参数发送到 CAD 系统的端口号。

**可选参数**

无。

**返回值**

无

**异常**

无。

### 47.1.7 updateCADParameters(...)

此方法使用指定的参数文件更新指定模型的参数。

**必要参数**

*modelName*

String，指定要更新的模型名称。

*CADName*

String，指定 Abaqus 更新参数的 CAD 系统。可用选项有 'Pro/ENGINEER'、'CATIA V5' 和 'CATIA V6'。

*parameterFile*

参数文件，包含在 CAD 系统中使用 'ABQ_' 前缀暴露的参数。

*CADPartFile*

指定触发参数更新的 CAD 零件文件的文件名。

对于 *CADName*='CATIA V5' 或 'CATIA V6'，您可以使用此参数指定产品或零件。如果指定产品，Abaqus 会更新与该产品关联的所有零件。

对于 *CADName*='Pro/ENGINEER'，此参数是可选的，您可以仅为零件指定更新。但是，在族表的情况下，单个文件可以与多个零件关联。在这种情况下，Abaqus 会更新所有列出的零件。

**可选参数**

*CADPartName*

String，指定要更新的零件名称。此零件名称应与原始 CAD 系统中的零件名称匹配。

如果在更新期间未指定 *CADPartFile* 和 *CADPartName*（其中您指定了 *CADName*='Pro/ENGINEER'），Abaqus 会更新指定文件中的所有零件。

**返回值**

无

**异常**

无。

### 47.1.8 disableParameterUpdate(...)

此方法禁用使用参数的关联 CAD 连接。

**必要参数**

*CADName*

String，指定要禁用参数更新的 CAD 系统。可用选项有 Pro/ENGINEER。

**可选参数**

无。

**返回值**

无

**异常**

无。

### 47.1.9 printToFile(...)

此方法使用存储在 [PrintOptions](pt01ch43pyo01.md) 对象和适当格式选项对象中的属性将画布对象打印到文件。

**必要参数**

*fileName*

String，指定要写入图像的文件。如果未提供文件扩展名，则根据所选图像格式添加扩展名（.`ps`、.`eps`、.`png`、.`tif`、.`svg` 或 .`svgz`）。

**可选参数**

*format*

SymbolicConstant，指定图像格式。可能的值为 PS、EPS、PNG、TIFF 和 SVG。默认值为 PS。

*canvasObjects*

画布对象序列（视口、文本字符串或箭头）进行打印。默认为打印所有画布对象。

*compression*

Boolean，指定 SVG 文件的格式。仅当 *format* 为 SVG 时使用此参数才有效。可能的值为 False（未压缩）和 True（压缩）。

**返回值**

无

**异常**

无。

### 47.1.10 printToPrinter(...)

此方法将画布对象打印到 Windows 打印机或 PostScript 打印机。用于打印到 Windows 打印机的属性存储在 [PrintOptions](pt01ch43pyo01.md) 对象和 [PageSetupOptions](pt01ch43pyo03.md) 对象中；用于打印到 PostScript 打印机的属性存储在 [PrintOptions](pt01ch43pyo01.md) 对象和 [PsOptions](pt01ch43pyo05.md) 对象中。

**必要参数**

无。

**可选参数**

*printCommand*

String，指定用于打印到打印机的操作系统命令或打印机名称。默认值为 "lpr" 或 `printOptions` 方法指定的值。如果创建脚本直接打印到 Windows 打印机，*printCommand* 必须采用以下形式：

```
session.printToPrinter.setValues(printCommand='PRINTER[
                                 *name 中的字符数*
                                 ]:
                                 *printername*
                                 PROPERTIES[
                                 *properties 中的字符数*
                                 ]:
                                 *document properties*
                                 ')
```

`PROPERTIES` 是一个字符列表，表示所选 Windows 打印机的打印首选项。脚本中不需要这些属性；打印输出将使用所选打印机的当前设置。您可以使用 `'PRINTER[7]: DEFAULT'` 来指定默认 Windows 打印机。

*numCopies*

Int，指定打印份数。可能的值为 1 ![](../graphics/ker_eqn00013.gif) *numCopies* ![](../graphics/ker_eqn00013.gif) 100。默认值为 1。

*canvasObjects*

画布对象序列（视口、文本字符串或箭头）进行打印。默认为打印所有画布对象。

**返回值**

无

**异常**

如果 *printCommand* 无效：

```
SystemError: invalid print command
```

如果打印命令失败：

```
SystemError: print command failed
```

如果 *numCopies* 超出范围：

```
RangeError: numCopies must be in the range 1 <= value <= 100
```

如果为非 SVG 格式指定了 *compression*：

```
TypeError: keyword error on compression
```

### 47.1.11 saveOptions(...)

此方法保存您自定义的显示设置。

**必要参数**

*directory*

SymbolicConstant，指定 Abaqus 保存文件的目录，该文件用于恢复您的自定义设置（`abaqus_v6.11.gpr`）。可能的值为 HOME 和 CURRENT。

**可选参数**

无。

**返回值**

无

**异常**

无。

### 47.1.12 writeVrmlFile(...)

此方法将当前视口对象导出到文件。

**必要参数**

*fileName*

String，指定要写入图形数据的文件。如果未提供文件扩展名，则根据所选格式添加扩展名（.`wrl`、.`wrz`）。

**可选参数**

*format*

Boolean，指定格式。可能的值为 False（未压缩）和 True（压缩）。

*canvasObjects*

要导出的画布对象序列（视口、文本字符串或箭头）。

**返回值**

无

**异常**

无。

### 47.1.13 write3DXMLFile(...)

此方法将当前视口对象导出到文件。

**必要参数**

*fileName*

String，指定要写入图形数据的文件。如果未提供文件扩展名，则添加（.`3dxml`）。

**可选参数**

*format*

Boolean，指定格式。可能的值为 False（未压缩）和 True（压缩）。

*canvasObjects*

要导出的画布对象序列。

**返回值**

无

**异常**

无。

### 47.1.14 writeOBJFile(...)

此方法将当前视口对象导出到文件。

**必要参数**

*fileName*

String，指定要写入图形数据的文件。如果未提供文件扩展名，则添加（.`obj`）。

**可选参数**

*canvasObjects*

要导出的画布对象序列。

**返回值**

无

**异常**

无。

### 47.1.15 成员

Session 对象可以具有以下成员：

*attachedToGui*

Boolean，指定 Abaqus 交互会话是否正在运行。

*replayInProgress*

Boolean，指定 Abaqus 是否正在执行重放文件。

*kernelMemoryFootprint*

Float，指定 Abaqus/CAE 内核进程的内存使用值（以 MB 为单位）。

*kernelMemoryMaxFootprint*

Float，指定 Abaqus/CAE 内核进程内存使用量的最大值（以 MB 为单位）。

*kernelMemoryLimit*

Float，指定 Abaqus/CAE 内核进程的内存使用限制（以 MB 为单位）。

*colors*

[Color](pt01ch47pyo03.md) 对象存储库。

*journalOptions*

[JournalOptions](pt01ch47pyo06.md) 对象，指定如何在日志和重放文件中记录几何选择。

*memoryReductionOptions*

[MemoryReductionOptions](pt01ch47pyo07.md) 对象，指定以降低内存模式运行的选项。

*nodeQuery*

[NodeQuery](pt01ch39pyo04.md) 对象，指定路径中的节点及其坐标。

*sketcherOptions*

[ConstrainedSketcherOptions](pt01ch48pyo04.md) 对象，指定所有草图的通用选项。

*viewerOptions*

[ViewerOptions](pt01ch35pyo10.md) 对象。

*animationController*

[AnimationController](pt01ch04pyo01.md) 对象。

*aviOptions*

[AVIOptions](pt01ch04pyo03.md) 对象。

*imageAnimationOptions*

[ImageAnimationOptions](pt01ch04pyo04.md) 对象。

*imageAnimation*

[ImageAnimation](pt01ch04pyo05.md) 对象。

*quickTimeOptions*

[QuickTimeOptions](pt01ch04pyo06.md) 对象。

*viewports*

[Viewport](pt01ch11pyo04.md) 对象存储库。

*customData*

[RepositorySupport](pt01ch14pyo02.md) 对象。

*defaultFieldReportOptions*

[FieldReportOptions](pt01ch23pyo01.md) 对象。

*defaultFreeBodyReportOptions*

[FreeBodyReportOptions](pt01ch23pyo02.md) 对象。

*fieldReportOptions*

[FieldReportOptions](pt01ch23pyo01.md) 对象。

*freeBodyReportOptions*

[FreeBodyReportOptions](pt01ch23pyo02.md) 对象。

*odbs*

[Odb](pt01ch34pyo01.md) 对象存储库。

*scratchOdbs*

[ScratchOdb](pt01ch34pyo26.md) 对象存储库。

*defaultOdbDisplay*

[DefaultOdbDisplay](pt01ch35pyo04.md) 对象。

*defaultPlot*

[DefaultPlot](pt01ch55pyo08.md) 对象。

*defaultChartOptions*

[DefaultChartOptions](pt01ch55pyo07.md) 对象。

*odbData*

[OdbData](pt01ch40pyo08.md) 对象存储库。

*mdbData*

[MdbData](pt01ch40pyo27.md) 对象存储库。

*paths*

[Path](pt01ch39pyo01.md) 对象存储库。

*freeBodies*

[FreeBody](pt01ch39pyo03.md) 对象存储库。

*streams*

[Stream](pt01ch39pyo09.md) 对象存储库。

*spectrums*

[Spectrum](pt01ch39pyo08.md) 对象存储库。

*currentProbeValues*

[CurrentProbeValues](pt01ch39pyo02.md) 对象。

*defaultProbeOptions*

[ProbeOptions](pt01ch39pyo05.md) 对象。

*probeOptions*

[ProbeOptions](pt01ch39pyo05.md) 对象。

*probeReport*

[ProbeReport](pt01ch39pyo06.md) 对象。

*defaultProbeReport*

[ProbeReport](pt01ch39pyo06.md) 对象。

*selectedProbeValues*

[SelectedProbeValues](pt01ch39pyo07.md) 对象。

*printOptions*

[PrintOptions](pt01ch43pyo01.md) 对象。

*epsOptions*

[EpsOptions](pt01ch43pyo02.md) 对象。

*pageSetupOptions*

[PageSetupOptions](pt01ch43pyo03.md) 对象。

*pngOptions*

[PngOptions](pt01ch43pyo04.md) 对象。

*psOptions*

[PsOptions](pt01ch43pyo05.md) 对象。

*svgOptions*

[SvgOptions](pt01ch43pyo06.md) 对象。

*tiffOptions*

[TiffOptions](pt01ch43pyo07.md) 对象。

*autoColors*

[AutoColors](pt01ch47pyo02.md) 对象，指定用于颜色编码的调色板。

*xyColors*

[AutoColors](pt01ch47pyo02.md) 对象，指定用于 [XYCurve](pt01ch55pyo15.md) 对象的调色板。

*xyDataObjects*

[XYData](pt01ch55pyo01.md) 对象存储库。

*curves*

[XYCurve](pt01ch55pyo15.md) 对象存储库。

*xyPlots*

[XYPlot](pt01ch55pyo16.md) 对象存储库。

*charts*

[Chart](pt01ch55pyo06.md) 对象存储库。

*defaultXYReportOptions*

[XYReportOptions](pt01ch55pyo17.md) 对象。

*xyReportOptions*

[XYReportOptions](pt01ch55pyo17.md) 对象。

*views*

[View](pt01ch54pyo01.md) 对象存储库。

*networkDatabaseConnectors*

[NetworkDatabaseConnector](pt01ch47pyo08.md) 对象存储库。

*displayGroups*

[DisplayGroup](pt01ch16pyo01.md) 对象存储库。

*graphicsInfo*

[GraphicsInfo](pt01ch17pyo08.md) 对象。

*defaultGraphicsOptions*

[GraphicsOptions](pt01ch17pyo09.md) 对象。

*graphicsOptions*

[GraphicsOptions](pt01ch17pyo09.md) 对象。

*defaultViewportAnnotationOptions*

[ViewportAnnotationOptions](pt01ch17pyo19.md) 对象。

*queues*

[Queue](pt01ch26pyo05.md) 对象存储库。

*currentViewportName*

String，指定当前视口的名称。

*sessionState*

[Dictionary](#ker-dictionary-pyc) 对象，指定视口及其关联的模型。Dictionary 键指定视口名称。Dictionary 值是指定模型名称的 Dictionary。

*images*

[Image](pt01ch47pyo05.md) 对象存储库。

*movies*

[Movie](pt01ch04pyo07.md) 对象存储库。

*defaultLightOptions*

[LightOptions](pt01ch17pyo12.md) 对象。

*drawingArea*

[DrawingArea](pt01ch11pyo02.md) 对象。

*defaultMesherOptions*

[MesherOptions](pt01ch31pyo07.md) 对象，指定如何控制 Mesh 模块中的默认设置。

*drawings*

[Drawing](pt01ch47pyo04.md) 对象存储库。


