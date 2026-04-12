# Summary of Abaqus Scripting Interface changes between Abaqus 6.13 and Abaqus 6.14







This section summarizes the changes and the additions that have been made to the Abaqus Scripting Interface between Abaqus 6.13 and Abaqus 6.14. SIMULIA makes every attempt to have the Abaqus Scripting Interface be backward compatible, and Abaqus can execute most Abaqus Scripting Interface scripts from previous versions of Abaqus. However, backward compatibility is not guaranteed beyond two versions of Abaqus, and it is recommended that you upgrade your commands to the most recent version.

To help you determine the status of your scripts, Abaqus displays a dialog box listing the deprecated commands when you execute the script from the main menu using ****File**![](../graphics/images/arrow.gif)**Run Script****. You are advised to upgrade scripts that contain deprecated commands as soon as possible. To run the upgrade utility, type the following command at the system prompt:

```
abaqus python -m upgradeScript [options] *scriptName* [*scriptName* ...]
```
*scriptName* can be either a file or a directory. You can also enter a wildcard (`*`) rather than a directory to upgrade all scripts within the current working directory. The options for the upgrade utility are:

| `-fileNames` *fileName* | Read a list of file names from the file specified. |
| --- | --- |
| `-logfileName` *logFileName* | Specify the name of the log file. |
| `-backup` | Whether to make backup versions of the upgraded files. By default, no backup versions are created. |
| `-preview` | Preview the changes to the file instead of changing the file. |
| `-diffExecutable` *application* | The application used to display the differences between the script and the upgraded script. By default, the differences are displayed by a web browser. |

The upgrade utility upgrades your scripts to the most recent version of Abaqus, regardless of when they were created. The upgrade utility upgrades both kernel commands and GUI commands. If *scriptName* is a directory, the upgrade utility upgrades each script in the directory. For example,
```
abaqus python -m upgradeScript -preview tireSlip.py tireWear
```
would preview all of the upgrades to the `tireSlip.py` script and to all of the scripts in the `tireWear` directory. 

More options are available if you use the `upgradeScript` method in an Abaqus Scripting Interface script to upgrade your scripts. For more information, see ["Upgrade script commands," Section 53.10](pt01ch53pyc06.md). In addition, an Abaqus plug-in is available that provides a graphical interface to the `upgradeScript` method. For more information, see ["Upgrading a script," Section 82.5 of the Abaqus/CAE User's Guide](../usi/usi-link.md#usi-plg-example-upgradescript).

Alternatively, you can run the following upgrade utilities from the command line interface. The same options are available as for the `upgradeScript` function.
- The `upgradeScript6*M*_6*N*` utility allow you to upgrade a kernel script from one version to another (where *M* and *N* are two-digit minor release numbers); for example, ``` abaqus python --m upgradeScript613_614 *filenames* ```
- The `upgradeGuiScript6*M*_6*N*` utility allows you to upgrade a GUI script from one version to another; for example, ``` abaqus python --m upgradeGuiScript613_614 *filenames* ```

In the following list of modified commands, the full path to the method is listed along with the required and optional arguments. Arguments enclosed within angle brackets, “< >”, are optional arguments. The syntax of the commands is as follows:

| (**Blue bold text**) | New method or argument. |
| --- | --- |
| (*Red italic text*) | Removed method or argument. |
| (*Green italic text*) | Changed argument; for example, the argument type has changed or the possible values of the SymbolicConstant have changed. |

You can click on a method to view its description in the command reference. Refer to the [Abaqus Scripting Reference Guide](book01.md) for Abaqus 6.13 for a description of methods that have been removed.**Abaqus/CAE Display Preferences commands**

No changes.
**Adaptivity commands**

No changes.
**Amplitude commands**

No changes.
**Animation commands**

No changes.
**Annotation commands**

No changes.
**Assembly commands**

No changes.
**Basic geometry commands**

No changes.
**Beam section profile commands**

No changes.
**Boundary condition commands**

No changes.
**Calibration commands**

No changes.
**Canvas commands**

No changes.
**Connector commands**

No changes.
**Constraint commands**

No changes.
**customKernel module**

No changes.
**Datum commands**

No changes.
**Display Group commands**

No changes.
**Display Options commands**

No changes.
**Edit Mesh commands**

No changes.
**Engineering feature commands**

No changes.
**Feature commands**

No changes.
**Field commands**

[**writeFreeBodyReport(fileName, append<, step, frame, stepFrame, odb>)**](../ker/ker-link.md#ker-fld-writereport-writefreebodyreport-pyc)

**Filter commands**

No changes.
**History and Field Report commands**

No changes.
**Input File Reader commands**

No changes.
**Interaction commands**

No changes.
**Job commands**

[OptimizationProcess(name, model, task, prototypeJob<, description, maxDesignCycle, **dataSaveFrequency**, **saveInitial**, **saveFirst**, **saveLast**, **saveEvery**>)](../ker/ker-link.md#ker-optimizationprocess-optimizationprocess-pyc)

[**Job.writeParAndInputFiles()**](../ker/ker-link.md#ker-optimizationprocess-writeparandinputfiles-pyc)

**Load commands**

No changes.
**Load Case commands**

No changes.
**Material commands**

*Shear(table<, temperatureDependency, dependencies>)*

[MaxeDamageInitiation(table<, definition, feq, fnn, fnt, frequency, ks, numberImperfections, temperatureDependency, dependencies, alpha, omega, tolerance, direction, **position**>)](../ker/ker-link.md#ker-damageinitiation-maxedamageinitiation-pyc)

[MaxpeDamageInitiation(table<, definition, feq, fnn, fnt, frequency, ks, numberImperfections, temperatureDependency, dependencies, alpha, omega, tolerance, direction, **position**>)](../ker/ker-link.md#ker-damageinitiation-maxpedamageinitiation-pyc)

[MaxpsDamageInitiation(table<, definition, feq, fnn, fnt, frequency, ks, numberImperfections, temperatureDependency, dependencies, alpha, omega, tolerance, direction, **position**>)](../ker/ker-link.md#ker-damageinitiation-maxpsdamageinitiation-pyc)

[MaxsDamageInitiation(table<, definition, feq, fnn, fnt, frequency, ks, numberImperfections, temperatureDependency, dependencies, alpha, omega, tolerance, direction, **position**>)](../ker/ker-link.md#ker-damageinitiation-maxsdamageinitiation-pyc)

[QuadeDamageInitiation(table<, definition, feq, fnn, fnt, frequency, ks, numberImperfections, temperatureDependency, dependencies, alpha, omega, tolerance, direction, **position**>)](../ker/ker-link.md#ker-damageinitiation-quadedamageinitiation-pyc)

[QuadsDamageInitiation(table<, definition, feq, fnn, fnt, frequency, ks, numberImperfections, temperatureDependency, dependencies, alpha, omega, tolerance, direction, **position**>)](../ker/ker-link.md#ker-damageinitiation-quadsdamageinitiation-pyc)

**Mdb commands**

[**Mdb.CombineOptResults(optResultLocation<, optIter, nValues, models, steps, analysisFieldVariables, includeResultsFrom, originalModel>)**](../ker/ker-link.md#ker-mdb-mdb-combineoptresults-pyc)

**Mesh commands**

[Mesh.getElementsByFeatureEdge(**angle**<, *angle*>)](../ker/ker-link.md#ker-meshelement-getelementsbyfeatureedge-pyc)

[Mesh.getNodesByFeatureEdge(**angle**<, *angle*>)](../ker/ker-link.md#ker-meshnode-getnodesbyfeatureedge-pyc)

[Mesh.getElemFacesByFaceAngle(**angle**<, *angle*>)](../ker/ker-link.md#ker-meshface-getelemfacesbyfaceangle-pyc)

[Mesh.getElemEdgesByFaceAngle(**angle**<, *angle*>)](../ker/ker-link.md#ker-meshface-getelemedgesbyfaceangle-pyc)

[Mesh.getElementsByFaceAngle(**angle**<, *angle*>)](../ker/ker-link.md#ker-meshface-getelementsbyfaceangle-pyc)

[Mesh.getElemFacesByLimitingAngle(**angle**<, *angle*>)](../ker/ker-link.md#ker-meshface-getelemfacesbylimitingangle-pyc)

[Mesh.getElemFacesByLayer(**numLayer**)](../ker/ker-link.md#ker-meshface-getelemfacesbylayer-pyc)

**Messaging commands**

No changes.
**Miscellaneous commands**

No changes.
**Model commands**

No changes.
**Odb commands**

No changes.
**Odb Display commands**

No changes.
**Optimization commands**

[**SizingClusterAreas(name, regions)**](../ker/ker-link.md#ker-sizingclusterareas-sizingclusterareas-pyc)

[**SizingCyclicSymmetry(name, region, translation<, axis, csys, ignoreFrozenArea>)**](../ker/ker-link.md#ker-sizingcyclicsymmetry-sizingcyclicsymmetry-pyc)

[**SizingFrozenArea(name, region)**](../ker/ker-link.md#ker-sizingfrozenarea-sizingfrozenarea-pyc)

[**SizingMemberSize(name, region, minWidth)**](../ker/ker-link.md#ker-sizingmembersize-sizingmembersize-pyc)

[**SizingPlanarSymmetry(name, region<, axis, csys, ignoreFrozenArea>)**](../ker/ker-link.md#ker-sizingplanarsymmetry-sizingplanarsymmetry-pyc)

[**SizingPointSymmetry(name, region<, csys, ignoreFrozenArea>)**](../ker/ker-link.md#ker-sizingpointsymmetry-sizingpointsymmetry-pyc)

[**SizingRotationalSymmetry(name, angle, region<, axis, csys, ignoreFrozenArea>)**](../ker/ker-link.md#ker-sizingrotationalsymmetry-sizingrotationalsymmetr-pyc)

[**SizingTask(name<, elementthicknessDeltaStopCriteria, freezeBoundaryConditionRegions, freezeLoadRegions, modeTrackingRegion, numFulfilledStopCriteria, numTrackedModes, objectiveFunctionDeltaStopCriteria, stopCriteriaDesignCycle, thicknessMoveLimit, thicknessUpdateStrategy>)**](../ker/ker-link.md#ker-sizingtask-sizingtask-pyc)

[**SizingThicknessControl(name, region, thicknessRestrictionBy<, maxThickness, minThickness>)**](../ker/ker-link.md#ker-sizingthicknesscontrol-sizingthicknesscontrol-pyc)

**Part commands**

[Feature.FaceFromElementFaces(elementFaces<, stitch, stitchTolerance, analyticFitTolerance, **associateFace**>)](../ker/ker-link.md#ker-feature-facefromelementfaces-pyc)

[**Feature.Mirror(mirrorPlane, keepOriginal<, keepInternalBoundaries>)**](../ker/ker-link.md#ker-feature-mirror-pyc)

[Feature.WireSpline(points<, **mergeType**, *mergeWire*, smoothClosedSpline>)](../ker/ker-link.md#ker-feature-wirespline-pyc)

[**Feature.WirePolyLine(points<, mergeType>)**](../ker/ker-link.md#ker-feature-wirepolyline-pyc)

**Partition commands**

No changes.
**Path and Probe commands**

No changes.
**Plot Options commands**

No changes.
**Plug-in commands**

No changes.
**Predefined Field commands**

No changes.
**Print commands**

No changes.
**Property commands**

[**SectionAssignment.getVertices()**](../ker/ker-link.md#ker-sectionassignment-getvertices-pyc)

**Region commands**

No changes.
**Section commands**

[*SectionAssignment.getVertices()*](../ker/ker-link.md#ker-sectionassignment-getvertices-pyc)

**Session commands**

[Session.updateCADParameters(modelName, CADName, parameterFile, **CADPartFile**<, CADPartName, *CADPartFile*>)](../ker/ker-link.md#ker-session-updatecadparameters-pyc)

**Sketcher commands**

No changes.
**Step  commands (step)**

No changes.
**Step commands (miscellaneous) **

No changes.
**Step (output) commands**

No changes.
**Text Representation commands**

No changes.
**Utility commands**

No changes.
**View commands**

No changes.
**XY commands**

No changes.



