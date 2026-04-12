# Summary of Abaqus Scripting Interface changes between Abaqus 6.12 and Abaqus 6.13







This section summarizes the changes and the additions that have been made to the Abaqus Scripting Interface between Abaqus 6.12 and Abaqus 6.13. SIMULIA makes every attempt to have the Abaqus Scripting Interface be backward compatible, and Abaqus can execute most Abaqus Scripting Interface scripts from previous versions of Abaqus. However, backward compatibility is not guaranteed beyond two versions of Abaqus, and it is recommended that you upgrade your commands to the most recent version.

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
- The `upgradeScript6*M*_6*N*` utility allow you to upgrade a kernel script from one version to another (where *M* and *N* are two-digit minor release numbers); for example, ``` abaqus python --m upgradeScript612_613 *filenames* ```
- The `upgradeGuiScript6*M*_6*N*` utility allows you to upgrade a GUI script from one version to another; for example, ``` abaqus python --m upgradeGuiScript612_613 *filenames* ```

In the following list of modified commands, the full path to the method is listed along with the required and optional arguments. Arguments enclosed within angle brackets, “< >”, are optional arguments. The syntax of the commands is as follows:

| (**Blue bold text**) | New method or argument. |
| --- | --- |
| (*Red italic text*) | Removed method or argument. |
| (*Green italic text*) | Changed argument; for example, the argument type has changed or the possible values of the SymbolicConstant have changed. |

You can click on a method to view its description in the command reference. Refer to the [Abaqus Scripting Reference Guide](book01.md) for Abaqus 6.12 for a description of methods that have been removed.**Abaqus/CAE Display Preferences commands**

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

[**Assembly.copyMeshPattern(<elements, faces, elemFaces, targetFace, nodes, coordinates>)**](../ker/ker-link.md#ker-assembly-copymeshpattern-pyc)

[Assembly.getAngle(plane1, plane2, line1, line2<, **commonVertex**>)](../ker/ker-link.md#ker-assembly-getangle-pyc)

[**Assembly.smoothNodes(<name, coordinates>)**](../ker/ker-link.md#ker-assembly-smoothnodes-pyc)

[**ModelInstance.Instance(name, model)**](../ker/ker-link.md#ker-modelinstance-instance-pyc)

[**ModelInstance.ConvertConstraints()**](../ker/ker-link.md#ker-modelinstance-convertconstraints-pyc)

[**ModelInstance.translate(vector)**](../ker/ker-link.md#ker-modelinstance-translate-pyc)

**Basic geometry commands**

[**CellArray.getMask()**](../ker/ker-link.md#ker-cellarray-getmask-pyc)

[**Edge.getEdgesByEdgeAngle(angle)**](../ker/ker-link.md#ker-edge-getedgesbyedgeangle-pyc)

[**EdgeArray.getMask()**](../ker/ker-link.md#ker-edgearray-getmask-pyc)

[**Face.getFacesByCurvature()**](../ker/ker-link.md#ker-face-getfacesbycurvature-pyc)

[**FaceArray.getMask()**](../ker/ker-link.md#ker-facearray-getmask-pyc)

[**IgnoredEdgeArray.getMask()**](../ker/ker-link.md#ker-ignorededgearray-getmask-pyc)

[**IgnoredVertexArray.getMask()**](../ker/ker-link.md#ker-ignoredvertexarray-getmask-pyc)

[**VertexArray.getMask()**](../ker/ker-link.md#ker-vertexarray-getmask-pyc)

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

[Assembly.generateMesh(*regions*<, **regions**, seedConstraintOverride, meshTechniqueOverride, boundaryPreview, boundaryMeshOverride>)](../ker/ker-link.md#ker-assembly-generatemesh-pyc)

[**Part.copyMeshPattern(<elements, faces, elemFaces, **targetFace**, nodes, coordinates>)**](../ker/ker-link.md#ker-part-copymeshpattern-pyc)

[Part.generateMesh(*regions*<, **regions**, seedConstraintOverride, meshTechniqueOverride, boundaryPreview, boundaryMeshOverride>)](../ker/ker-link.md#ker-part-generatemesh-pyc)

**Engineering feature commands**

[**EngineeringFeature.DebondVCCT(name, initiationStep, surfToSurfInteraction <, debondingForceAmplitude, printToDATFrequency>)**](../ker/ker-link.md#ker-debondvcct-debondvcct-pyc)

**Feature commands**

No changes.
**Field commands**

No changes.
**Filter commands**

No changes.
**History and Field Report commands**

No changes.
**Input File Reader commands**

No changes.
**Interaction commands**

[ContactProperty.FractureCriterion(initTable<, type, mixedModeBehavior, temperatureDependency, dependencies, tolerance, **specifyUnstableCrackProp**, **unstableTolerance**>)](../ker/ker-link.md#ker-fracturecriterion-fracturecriterion-pyc)

**Job commands**

No changes.
**Load commands**

No changes.
**Load Case commands**

No changes.
**Material commands**

[Material.MagneticPermeability(table, **table2**, **table3**<, type, frequencyDependency, temperatureDependency, dependencies, **nonlinearBH**>)](../ker/ker-link.md#ker-magneticpermeability-magneticpermeability-pyc)

**Mdb commands**

No changes.
**Mesh commands**

[**MeshEdge.getElementsViaTopology()**](../ker/ker-link.md#ker-meshedge-getelementsviatopology-pyc)

[**MeshEdgeArray.getMask()**](../ker/ker-link.md#ker-meshedgearray-getmask-pyc)

[**MeshElement.getElementsByFeatureEdge(<angle>)**](../ker/ker-link.md#ker-meshelement-getelementsbyfeatureedge-pyc)

[**MeshElementArray.getMask()**](../ker/ker-link.md#ker-meshelementarray-getmask-pyc)

[**MeshFace.getElemEdgesByFaceAngle(<angle>)**](../ker/ker-link.md#ker-meshface-getelemedgesbyfaceangle-pyc)

[**MeshFace.getElemFacesByLayer()**](../ker/ker-link.md#ker-meshface-getelemfacesbylayer-pyc)

[**MeshFace.getElemFacesByLimitingAngle(<angle>)**](../ker/ker-link.md#ker-meshface-getelemfacesbylimitingangle-pyc)

[**MeshFace.getElementsViaTopology()**](../ker/ker-link.md#ker-meshface-getelementsviatopology-pyc)

[**MeshFaceArray.getMask()**](../ker/ker-link.md#ker-meshfacearray-getmask-pyc)

[**MeshNode.getNodesByFeatureEdge(<angle>)**](../ker/ker-link.md#ker-meshnode-getnodesbyfeatureedge-pyc)

[**MeshNodeArray.getMask()**](../ker/ker-link.md#ker-meshnodearray-getmask-pyc)

**Messaging commands**

No changes.
**Miscellaneous commands**

No changes.
**Model commands**

No changes.
**Odb commands**

No changes.
**Odb Display commands**

[OrientationOptions.setValues(<options, axis1Color, showAxis1, axis2Color, showAxis2, axis3Color, showAxis3, symbolSize, lineThickness, **orientation**, arrowheadStyle, scaleMode>)](../ker/ker-link.md#ker-odbdisplay-setvalues-pyc)

**Optimization commands**

No changes.
**Part commands**

[Model.PartFromGeometryFile(name, geometryFile, dimensionality, type <, bodyNum, combine, retainBoundary, **usePartNameFromFile**, stitchTolerance, twist, scale, convertToAnalytical, convertToPrecise>)](../ker/ker-link.md#ker-part-partfromgeometryfile-pyc)

[Part.getAngle(plane1, plane2, line1, line2<, **commonVertex**>)](../ker/ker-link.md#ker-part-getangle-pyc)

[Part.FaceFromElementFaces(elementFaces<, **stitch**, **stitchTolerance**, **analyticFitTolerance**>)](../ker/ker-link.md#ker-part-facefromelementfaces-pyc)

[**Part.getFeatureCells(name)**](../ker/ker-link.md#ker-part-getfeaturecells-pyc)

[**Part.getFeatureEdges(name)**](../ker/ker-link.md#ker-part-getfeatureedges-pyc)

[**Part.getFeatureFaces(name)**](../ker/ker-link.md#ker-part-getfeaturefaces-pyc)

[**Part.getFeatureVertices(name)**](../ker/ker-link.md#ker-part-getfeaturevertices-pyc)

[Part.seedPart(*regions*, size<, deviationFactor, minSizeFactor, constraint>)](../ker/ker-link.md#ker-part-seedpart-pyc)

[**Part.smoothNodes(<nodes, coordinates>)**](../ker/ker-link.md#ker-part-smoothnodes-pyc)

**Partition commands**

No changes.
**Path and Probe commands**

No changes.
**Plot Options commands**

[BasicOptions.setValues(<options, cameraCsysName, cameraMovesWithCsys, cameraFollowsRotation, averagingThreshold, quantityToPlot, curveRefinementLevel, noResultsColor, featureAngle, otherSymbolSize, renderBeamProfiles, beamScaleFactor, renderShellThickness, shellScaleFactor, accountForDeactivatedElems, bcDisplay, connectorDisplay, highlightConnectorPts, showConnectorAxes, showConnectorType, pointElements, referencePoints, massElements, springElements, spotWelds, tracerParticles, **pc3dElements**, **pd3dElements**, sweepArs, sweepElem, sweepStartAngleArs, sweepStartAngleElem, sweepEndAngleArs, sweepEndAngleElem, numSweepSegmentsArs, numSweepSegmentsElem, numericForm, complexAngle, sectionResults, envelopeCriteria, envelopeDataPosition, plyResultLocation, sectionPointScheme, sweepSectors, sectorSelectionType, selectedSectorNumbers, sweepSectorStartAngle, sweepSectorEndAngle, extrudeArs, extrudeArsDepthAutoCompute, extrudeElem, extrudeArsDepth, extrudeElemDepth, mirrorPatternOrder, mirrorCsysName, mirrorAboutXyPlane, mirrorAboutXzPlane, mirrorAboutYzPlane, mirrorDisplayBodies, patternCsysName, patternNumX, patternNumY, patternNumZ, patternOffsetX, patternOffsetY, patternOffsetZ, patternRotationAxis, patternTotalAngle, patternNumCircular, couplingDisplay, coordSystemDisplay, scratchCoordSystemDisplay, transformationType, datumCsys, rigidTransformPrimary, rigidTransformDeformed, transformOnDeformed, averageElementOutput, averageOnlyDisplayed, computeOutput, regionBoundaries, useRegionBoundaries, userRegions, includeFeatureBoundaries>)](../ker/ker-link.md#ker-basicoptions-setvalues-pyc)

**Plug-in commands**

No changes.
**Predefined Field commands**

No changes.
**Print commands**

No changes.
**Property commands**

No changes.
**Region commands**

No changes.
**Section commands**

[BeamSection.TransverseShearBeam(**scfDefinition**<, k23, k13, slendernessCompensation>)](../ker/ker-link.md#ker-transverseshearbeam-transverseshearbeam-pyc)

**Session commands**

No changes.
**Sketcher commands**

No changes.
**Step  commands (step)**

No changes.
**Step commands (miscellaneous) **

[Control.setValues(<allowPropagation, resetDefaultValues, discontinuous, constraints, lineSearch, timeIncrementation, directCyclic, concentrationField, displacementField, electricalPotentialField, globalField, hydrostaticFluidPressureField, poreFluidPressureField, rotationField, temperatureField, **vcctLinearScaling**>)](../ker/ker-link.md#ker-control-setvalues-pyc)

**Step (output) commands**

No changes.
**Text Representation commands**

No changes.
**Utility commands**

No changes.
**View commands**

No changes.
**XY commands**

[Session.XYDataFromPath(path, **name**, includeIntersections, shape, pathStyle, numIntervals, labelType <, *name*, viewport, step, frame, variable, deformedMag, numericForm, complexAngle>)](../ker/ker-link.md#ker-xydata-xydatafrompath-pyc)




