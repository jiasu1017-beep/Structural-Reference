# 47.1 Session object







The Session object has no constructor. Abaqus creates the*session*               member when a session is started.

**Access**

```
session
```

### 47.1.1 setValues(...)

This method modifies the Session                       object.

**Required arguments**

None.

**Optional argument**

*kernelMemoryLimit*

A Float specifying the memory limit value for the Abaqus/CAE kernel process in megabytes. If the limit is exceeded, Abaqus/CAE displays an error message.

The default memory limit value for Windows 32-bit systems if not set is 1800 MB. Increasing the memory limit is not recommended unless you are using a Windows 32-bit system with the boot option `/3GB /userva=SizeInMBytes`                                to extend the amount of memory available for Abaqus/CAE. In this case the limit can be changed to 2800 MB.

If the kernel memory size reaches the **abq_ker_memory**                                value or the virtual memory limit of the machine, the following message will be displayed:

```
Operation did not complete due to a memory allocation failure.
```

For optimal performance, the memory limit should be set to a value less than the physical amount of memory on the machine.

The minimum setting allowed is 256 MB.

**Return value**

None

**Exceptions**

None.

### 47.1.2 enableCADConnection(...)

This method enables an associative import CAD connection for the specified *CADName*.

**Required argument**

*CADName*

A String specifying the CAD system. Available options are Pro/ENGINEER, CATIA V5, CATIA V6, NX and SolidWorks.

**Optional argument**

*portNum*

An Integer specifying the port number to be used by the CAD system to communicate with Abaqus/CAE. If unspecified, attempts will be made to identify an open port.

**Return value**

The connection port number used for the CAD connection.

**Exceptions**

None.

### 47.1.3 isCADConnectionEnabled()

This method checks the status of CAD Connection.

**Arguments**

None.

**Return value**

A Boolean value of True if the CAD connection enabled and False if the CAD connection disabled.

**Exceptions**

None.

### 47.1.4 disableCADConnection(...)

This method disables an associative import CAD connection that was enabled.

**Required argument**

*CADName*

A String specifying the CAD system for which associative import will be disabled. Available options are Pro/ENGINEER, CATIA V5, CATIA V6, NX and SolidWorks.

**Optional arguments**

None.

**Return value**

None

**Exceptions**

None.

### 47.1.5 enableParameterUpdate(...)

This method enables an associative import CAD connection with parameters for the specified *CADName*.

**Required arguments**

*CADName*

A String specifying the CAD system for which parameter update will be enabled. Available option is Pro/ENGINEER.

*CADVersion*

A String specifying the CAD Version. Allowable options are Wildfire2 and Wildfire3.

**Optional argument**

*CADPort*

An Integer specifying the port number to be used by Abaqus/CAE to communicate with the CAD system. If unspecified, attempts will be made to identify an open port. This port number is not the same as the *portNum*                                used by the associative import interface.

**Return value**

None

**Exceptions**

None.

### 47.1.6 setCADPortNumber(...)

For the given CAD system, this method saves the port number in Abaqus/CAE. This port number is used to send the parameter information to the CAD system.

**Required arguments**

*CADName*

A String specifying the CAD system for which the port number will be saved. The available options are 'CATIA V5' and 'CATIA V6'.

*Port*

An integer specifying the port number to be used by Abaqus/CAE to send the modified parameters to the CAD system.

**Optional arguments**

None.

**Return value**

None

**Exceptions**

None.

### 47.1.7 updateCADParameters(...)

This method updates the parameters for the specified model using the specified parameter file.

**Required arguments**

*modelName*

A String specifying the model name to update.

*CADName*

A String specifying the CAD system for which Abaqus updates the parameters. The available options are 'Pro/ENGINEER', 'CATIA V5' and 'CATIA V6'.

*parameterFile*

A parameter file containing the parameters that were exposed in the CAD system using the 'ABQ_' prefix.

*CADPartFile*

A file name specifying the CAD part file for which parameter update is triggered.

For *CADName*='CATIA V5' or 'CATIA V6', you can specify either products or parts using this argument. If you specify a product, Abaqus updates all of the parts associated with that product.

For *CADName*='Pro/ENGINEER', this argument is optional, and you can specify update for parts only. However, a single file can be associated with multiple parts in the case of family tables. In this case, Abaqus updates all listed parts.

**Optional arguments**

*CADPartName*

An String specifying the part name to update. This part name should match the part name in the originating CAD system.

If you specify neither *CADPartFile* nor *CADPartName* during an update in which you specified *CADName*='Pro/ENGINEER', Abaqus updates all of the parts in the specified file. 

**Return value**

None

**Exceptions**

None.

### 47.1.8 disableParameterUpdate(...)

This method disables an associative CAD connection using parameters.

**Required argument**

*CADName*

A String specifying the CAD system for which the parameter update will be disabled. Available option is Pro/ENGINEER.

**Optional arguments**

None.

**Return value**

None

**Exceptions**

None.

### 47.1.9 printToFile(...)

This method prints canvas objects to a file using the attributes stored in the [PrintOptions](pt01ch43pyo01.md)                       object and the appropriate format options object.

**Required argument**

*fileName*

A String specifying the file to which the image is to be written. If no file extension is supplied, an extension is added based on the selected image format (.`ps`, .`eps`, .`png`, .`tif`, .`svg`, or .`svgz`                              ).

**Optional arguments**

*format*

A SymbolicConstant specifying the image format. Possible values arePS, EPS, PNG, TIFF, and SVG. The default value is PS.

*canvasObjects*

A sequence of canvas objects (viewports, text strings, or arrows) to print. The default is to print all canvas objects.

*compression*

A Boolean specifying the format for an SVG file.  It is only valid to use this argument when *format*                                is SVG. Possible values are False (Uncompressed)                                and True (Compressed).

**Return value**

None

**Exceptions**

None.

### 47.1.10 printToPrinter(...)

This method prints canvas objects to a Windows printer or to a PostScript printer. The attributes used for printing to a Windows printer are stored in the [PrintOptions](pt01ch43pyo01.md)                       object and the [PageSetupOptions](pt01ch43pyo03.md)                       object; the attributes used for printing to a PostScript printer are stored in the [PrintOptions](pt01ch43pyo01.md)                       object and the [PsOptions](pt01ch43pyo05.md)                       object.

**Required arguments**

None.

**Optional arguments**

*printCommand*

A String specifying the operating system command or printer name to issue for printing to the printer. The default value is “lpr” or the value specified by the `printOptions`                                method. If you create a script to print directly to a Windows printer, the *printCommand*                                must take the following form:

```
session.printToPrinter.setValues(printCommand='PRINTER[
                                 *number of characters in name*
                                 ]:
                                 *printername*
                                 PROPERTIES[
                                 *number of characters in properties*
                                 ]:
                                 *document properties*
                                 ')

```
                                The `PROPERTIES`                                is a list of characters that represents the printing preferences for the selected Windows printer. The properties are not required in a script; the printed output will use the current settings for the selected printer. You can use `'PRINTER[7]: DEFAULT'`                                to specify the default Windows printer.

*numCopies*

An Int specifying the number of copies to print. Possible values are 1 ![](../graphics/ker_eqn00013.gif)                               *numCopies*                               ![](../graphics/ker_eqn00013.gif)                              100. The default value is 1.

*canvasObjects*

A sequence of canvas objects (viewports, text strings, or arrows) to print. The default is to print all canvas objects.

**Return value**

None

**Exceptions**

If *printCommand*                             is invalid:

```
SystemError: invalid print command
```

If the print command fails:

```
SystemError: print command failed
```

If *numCopies*                             is out of range:

```
RangeError: numCopies must be in the range 1 <= value <= 100
```

If *compression*                             is specified when *format*                             is not SVG                           :

```
TypeError: keyword error on compression
```

### 47.1.11 saveOptions(...)

This method saves your customized display settings.

**Required argument**

*directory*

A SymbolicConstant specifying the directory in which Abaqus saves the file that will be used to restore your customized settings (`abaqus_v6.11.gpr`                              ). Possible values are HOME                                and CURRENT.

**Optional arguments**

None.

**Return value**

None

**Exceptions**

None.

### 47.1.12 writeVrmlFile(...)

This method exports the current viewport objects to a file.

**Required argument**

*fileName*

A String specifying the file to which the graphics data is to be written. If no file extension is supplied, an extension is added based on the selected format (.`wrl`, .`wrz`).

**Optional arguments**

*format*

A Boolean specifying the format. Possible values are False (Uncompressed)                                and True (Compressed).

*canvasObjects*

A sequence of canvas objects (viewports, text strings, or arrows) to export.

**Return value**

None

**Exceptions**

None.

### 47.1.13 write3DXMLFile(...)

This method exports the current viewport objects to a file.

**Required argument**

*fileName*

A String specifying the file to which the graphics data is to be written. If no file extension is supplied, (.`3dxml`) will be added.

**Optional arguments**

*format*

A Boolean specifying the format. Possible values are False (Uncompressed)                                and True (Compressed).

*canvasObjects*

A sequence of canvas objects to export.

**Return value**

None

**Exceptions**

None.

### 47.1.14 writeOBJFile(...)

This method exports the current viewport objects to a file.

**Required argument**

*fileName*

A String specifying the file to which the graphics data is to be written. If no file extension is supplied, (.`obj`) will be added.

**Optional argument**

*canvasObjects*

A sequence of canvas objects to export.

**Return value**

None

**Exceptions**

None.

### 47.1.15 Members

The Session object can have the following members:

*attachedToGui*

A Boolean specifying whether an Abaqus interactive session is running.

*replayInProgress*

A Boolean specifying whether Abaqus is executing a replay file.

*kernelMemoryFootprint*

A Float specifying the memory usage value for the Abaqus/CAE kernel process in megabytes.

*kernelMemoryMaxFootprint*

A Float specifying the maximum value for the memory usage for the Abaqus/CAE kernel process in megabytes.

*kernelMemoryLimit*

A Float specifying the limit for the memory use for the Abaqus/CAE kernel process in megabytes.

*colors*

A repository of [Color](pt01ch47pyo03.md) objects.

*journalOptions*

A [JournalOptions](pt01ch47pyo06.md) object specifying how to record selection of geometry in the journal and replay files.

*memoryReductionOptions*

A [MemoryReductionOptions](pt01ch47pyo07.md) object specifying options for running in reduced memory mode.

*nodeQuery*

A [NodeQuery](pt01ch39pyo04.md) object specifying nodes and their coordinates in a path.

*sketcherOptions*

A [ConstrainedSketcherOptions](pt01ch48pyo04.md) object specifying common options for all sketches.

*viewerOptions*

A [ViewerOptions](pt01ch35pyo10.md) object.

*animationController*

An [AnimationController](pt01ch04pyo01.md) object.

*aviOptions*

An [AVIOptions](pt01ch04pyo03.md) object.

*imageAnimationOptions*

An [ImageAnimationOptions](pt01ch04pyo04.md) object.

*imageAnimation*

An [ImageAnimation](pt01ch04pyo05.md) object.

*quickTimeOptions*

A [QuickTimeOptions](pt01ch04pyo06.md) object.

*viewports*

A repository of [Viewport](pt01ch11pyo04.md) objects.

*customData*

A [RepositorySupport](pt01ch14pyo02.md) object.

*defaultFieldReportOptions*

A [FieldReportOptions](pt01ch23pyo01.md) object.

*defaultFreeBodyReportOptions*

A [FreeBodyReportOptions](pt01ch23pyo02.md) object.

*fieldReportOptions*

A [FieldReportOptions](pt01ch23pyo01.md) object.

*freeBodyReportOptions*

A [FreeBodyReportOptions](pt01ch23pyo02.md) object.

*odbs*

A repository of [Odb](pt01ch34pyo01.md) objects.

*scratchOdbs*

A repository of [ScratchOdb](pt01ch34pyo26.md) objects.

*defaultOdbDisplay*

A [DefaultOdbDisplay](pt01ch35pyo04.md) object.

*defaultPlot*

A [DefaultPlot](pt01ch55pyo08.md) object.

*defaultChartOptions*

A [DefaultChartOptions](pt01ch55pyo07.md) object.

*odbData*

A repository of [OdbData](pt01ch40pyo08.md) objects.

*mdbData*

A repository of [MdbData](pt01ch40pyo27.md) objects.

*paths*

A repository of [Path](pt01ch39pyo01.md) objects.

*freeBodies*

A repository of [FreeBody](pt01ch39pyo03.md) objects.

*streams*

A repository of [Stream](pt01ch39pyo09.md) objects.

*spectrums*

A repository of [Spectrum](pt01ch39pyo08.md) objects.

*currentProbeValues*

A [CurrentProbeValues](pt01ch39pyo02.md) object.

*defaultProbeOptions*

A [ProbeOptions](pt01ch39pyo05.md) object.

*probeOptions*

A [ProbeOptions](pt01ch39pyo05.md) object.

*probeReport*

A [ProbeReport](pt01ch39pyo06.md) object.

*defaultProbeReport*

A [ProbeReport](pt01ch39pyo06.md) object.

*selectedProbeValues*

A [SelectedProbeValues](pt01ch39pyo07.md) object.

*printOptions*

A [PrintOptions](pt01ch43pyo01.md) object.

*epsOptions*

An [EpsOptions](pt01ch43pyo02.md) object.

*pageSetupOptions*

A [PageSetupOptions](pt01ch43pyo03.md) object.

*pngOptions*

A [PngOptions](pt01ch43pyo04.md) object.

*psOptions*

A [PsOptions](pt01ch43pyo05.md) object.

*svgOptions*

A [SvgOptions](pt01ch43pyo06.md) object.

*tiffOptions*

A [TiffOptions](pt01ch43pyo07.md) object.

*autoColors*

An [AutoColors](pt01ch47pyo02.md) object specifying the color palette to be used for color coding.

*xyColors*

An [AutoColors](pt01ch47pyo02.md) object specifying the color palette to be used for[XYCurve](pt01ch55pyo15.md)                     objects.

*xyDataObjects*

A repository of [XYData](pt01ch55pyo01.md) objects.

*curves*

A repository of [XYCurve](pt01ch55pyo15.md) objects.

*xyPlots*

A repository of [XYPlot](pt01ch55pyo16.md) objects.

*charts*

A repository of [Chart](pt01ch55pyo06.md) objects.

*defaultXYReportOptions*

An [XYReportOptions](pt01ch55pyo17.md) object.

*xyReportOptions*

An [XYReportOptions](pt01ch55pyo17.md) object.

*views*

A repository of [View](pt01ch54pyo01.md) objects.

*networkDatabaseConnectors*

A repository of [NetworkDatabaseConnector](pt01ch47pyo08.md) objects.

*displayGroups*

A repository of [DisplayGroup](pt01ch16pyo01.md) objects.

*graphicsInfo*

A [GraphicsInfo](pt01ch17pyo08.md) object.

*defaultGraphicsOptions*

A [GraphicsOptions](pt01ch17pyo09.md) object.

*graphicsOptions*

A [GraphicsOptions](pt01ch17pyo09.md) object.

*defaultViewportAnnotationOptions*

A [ViewportAnnotationOptions](pt01ch17pyo19.md) object.

*queues*

A repository of [Queue](pt01ch26pyo05.md) objects.

*currentViewportName*

A String specifying the name of the current viewport.

*sessionState*

A [Dictionary](#ker-dictionary-pyc) object specifying the viewports and their associated models. The Dictionary key specifies the viewport name. The Dictionary value is a Dictionary specifying the model name.

*images*

A repository of [Image](pt01ch47pyo05.md) objects.

*movies*

A repository of [Movie](pt01ch04pyo07.md) objects.

*defaultLightOptions*

A [LightOptions](pt01ch17pyo12.md) object.

*drawingArea*

A [DrawingArea](pt01ch11pyo02.md) object.

*defaultMesherOptions*

A [MesherOptions](pt01ch31pyo07.md) object specifying how to control default settings in the Mesh module.

*drawings*

A repository of [Drawing](pt01ch47pyo04.md) objects.




