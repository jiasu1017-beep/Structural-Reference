# Summary of Abaqus Scripting Interface changes between Abaqus 6.11 and Abaqus 6.12







This section summarizes the changes and the additions that have been made to the Abaqus Scripting Interface between Abaqus 6.11 and Abaqus 6.12. SIMULIA makes every attempt to have the Abaqus Scripting Interface be backward compatible, and Abaqus can execute most Abaqus Scripting Interface scripts from previous versions of Abaqus. However, backward compatibility is not guaranteed beyond two versions of Abaqus, and it is recommended that you upgrade your commands to the most recent version.

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
- The `upgradeScript6*M*_6*N*` utility allow you to upgrade a kernel script from one version to another (where *M* and *N* are two-digit minor release numbers); for example, ``` abaqus python --m upgradeScript611_612 *filenames* ```
- The `upgradeGuiScript6*M*_6*N*` utility allows you to upgrade a GUI script from one version to another; for example, ``` abaqus python --m upgradeGuiScript611_612 *filenames* ```

In the following list of modified commands, the full path to the method is listed along with the required and optional arguments. Arguments enclosed within angle brackets, “< >”, are optional arguments. The syntax of the commands is as follows:

| (**Blue bold text**) | New method or argument. |
| --- | --- |
| (*Red italic text*) | Removed method or argument. |
| (*Green italic text*) | Changed argument; for example, the argument type has changed or the possible values of the SymbolicConstant have changed. |

You can click on a method to view its description in the command reference. Refer to the [Abaqus Scripting Reference Guide](book01.md) for Abaqus 6.11 for a description of methods that have been removed.**Abaqus/CAE Display Preferences commands**

No changes.
**Adaptivity commands**

No changes.
**Amplitude commands**

[**PsdDefinition(name, data<, unitType, referenceGravityAcceleration, referenecePower, user, timeSpan, amplitude>)**](../ker/ker-link.md#ker-psddefinition-psddefinition-pyc)

**Animation commands**

No changes.
**Annotation commands**

No changes.
**Assembly commands**

[Assembly.InstanceFromBooleanMerge(name, instances<, keepIntersections, originalInstances, **domain**, **mergeNodes**, **nodeMergingTolerance**, **removeDuplicateElements**>)](../ker/ker-link.md#ker-partinstance-instancefrombooleanmerge-pyc)

**Basic geometry commands**

[Face.getFacesByFaceAngle(**angle**<, *angle*>)](../ker/ker-link.md#ker-face-getfacesbyfaceangle-pyc)

**Beam section profile commands**

[PipeProfile(name, r, t<, **formulation**>)](../ker/ker-link.md#ker-pipeprofile-pipeprofile-pyc)

**Boundary condition commands**

[**FluidCavityPressureBC(name, createStepName, fluidCavity <, magnitude, amplitude, fixed>)**](../ker/ker-link.md#ker-fluidcavitypressurebc-pyc)

[**FluidCavityPressureBC.setValuesInStep(stepName<, magnitude, amplitude>)**](../ker/ker-link.md#ker-fluidcavitypressurebc-setvaluesinstep-pyc)

[**AccelerationBaseMotionBC(name, createStepName, dof<, amplitudeScaleFactor, centerOfRotation, correlation, secondaryBase, useComplex, amplitude>)**](../ker/ker-link.md#ker-accelerationbasemotionbc-accelerationbasemotionbc-pyc)

[**DisplacementBaseMotionBC(name, createStepName, dof<, amplitudeScaleFactor, centerOfRotation, correlation, secondaryBase, useComplex, amplitude>)**](../ker/ker-link.md#ker-displacementbasemotionbc-displacementbasemotionbc-pyc)

[**FluidCavityPressureBC(name, createStepName, fluidCavity<, magnitude, amplitude, fixed>)**](../ker/ker-link.md#ker-fluidcavitypressurebc-fluidcavitypressurebc-pyc)

[FluidInletOutletBC(name, createStepName, region<, **fieldName**, **distributionType**, **localCsys**, momentumType, pressure, v1, v2, v3, momentumAmplitude, temperature, temperatureAmplitude, kineticEnergy, kineticEnergyAmplitude, dissipationRate, dissipationRateAmplitude, eddyViscosity, eddyViscosityAmplitude>)](../ker/ker-link.md#ker-fluidinletoutletbc-fluidinletoutletbc-pyc)

[FluidWallConditionBC(name, createStepName, region<, **fieldName**, **distributionType**, **localCsys**, type, v1, v2, v3, velocityAmplitude, thermalEnergyType, temperature, heatFlux, thermalEnergyAmplitude, kineticEnergy, kineticEnergyAmplitude, dissipationRate, dissipationRateAmplitude, eddyViscosity, eddyViscosityAmplitude>)](../ker/ker-link.md#ker-fluidwallconditionbc-fluidwallconditionbc-pyc)

[**MagneticVectorPotentialBC(name, createStepName, region<, component1, component2, component3, amplitude, distributionType, localCsys>)**](../ker/ker-link.md#ker-magneticvectorpotentialbc-magneticvectorpotentialbc-pyc)

[**SecondaryBaseBC(name, createStepName, regions, dofs)**](../ker/ker-link.md#ker-secondarybasebc-secondarybasebc-pyc)

[**VelocityBaseMotionBC(name, createStepName, dofs<, amplitudeScaleFactor, centerOfRotation, correlation, secondaryBase, useComplex, amplitude>)**](../ker/ker-link.md#ker-velocitybasemotionbc-velocitybasemotionbc-pyc)

[ConnAccelerationBC(name, createStepName, *connectors*<, **region**, **fastenerName**, **fastenerSetName**, a1, a2, a3, ar1, ar2, ar3, amplitude, distributionType>)](../ker/ker-link.md#ker-connaccelerationbc-connaccelerationbc-pyc)

[ConnDisplacementBC(name, createStepName, *connectors*<, **region**, **fastenerName**, **fastenerSetName**, u1, u2, u3, ur1, ur2, ur3, fixed, amplitude, distributionType, buckleCase>)](../ker/ker-link.md#ker-conndisplacementbc-conndisplacementbc-pyc)

[ConnVelocityBC(name, createStepName, *connectors*<, **region**, **fastenerName**, **fastenerSetName**, v1, v2, v3, vr1, vr2, vr3, amplitude, distributionType>)](../ker/ker-link.md#ker-connvelocitybc-connvelocitybc-pyc)

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

[EngineeringFeature.PointMassInertia(name, region <, mass, **mass1**, **mass2**, **mass3**, i11, i22, i33, i12, i13, i23, localCsys, alpha, composite>)](../ker/ker-link.md#ker-pointmassinertia-pointmassinertia-pyc)

**Feature commands**

No changes.
**Field commands**

[MappedField(name<, regionType, partLevelData, pointDataFormat, gridPointPlane, defaultUnmappedValue, mappingAlgorithm, searchTolType, boundarySearchTol, neighborhoodSearchTol, negativeNormalSearchTol, positiveNormalSearchTol, **scaleCoordinates**, gridPointData, xyzPointData, **coordinateScalingFactors**, localCsys, description>)](../ker/ker-link.md#ker-mappedfield-mappedfield-pyc)

**Filter commands**

No changes.
**History and Field Report commands**

No changes.
**Input File Reader commands**

Input File Reader commands are new in Abaqus 6.12.

[**InputFile(file<, directory>)**](../ker/ker-link.md#ker-inputfile-inputfile-pyc)

[**Parse(organize, verbose, bulk, usePyArray)**](../ker/ker-link.md#ker-inputfile-parse-pyc)

**Interaction commands**

[ContactExp(name, createStepName<, **globalSmoothing**, useAllstar, includedPairs, excludedPairs, contactPropertyAssignments, surfaceThicknessAssignments, surfaceOffsetAssignments, surfaceFeatureAssignments, **smoothingAssignments**, masterSlaveAssignments>)](../ker/ker-link.md#ker-contactexp-contactexp-pyc)

[ContactStd(name, createStepName<, **globalSmoothing**, useAllstar, includedPairs, excludedPairs, contactPropertyAssignments, **surfaceFeatureAssignments**, surfaceThicknessAssignments, surfaceOffsetAssignments, masterSlaveAssignments, initializationAssignments, **stabilizationAssignments**, smoothingAssignments>)](../ker/ker-link.md#ker-contactstd-contactstd-pyc)

[**FluidCavity(name, createStepName, cavityPoint, cavitySurface, interactionProperty <, ambientPressure, thickness, useAdiabatic, checkNormals>)**](../ker/ker-link.md#ker-fluidcavity-fluidcavity-pyc)

[**FluidCavityProperty(name <, definition, fluidDensity, molecularWeight, useExpansion, expansionTempDep, expansionDependencies, referenceTemperature, expansionTable, useBulkModulus, bulkModulusTempDep, bulkModulusDependencies, bulkModulusTable, useCapacity, capacityType, capacityTempDep, capacityDependencies, capacityTable>)**](../ker/ker-link.md#ker-fluidcavityproperty-fluidcavityproperty-pyc)

[**FluidCavityState(name , createStepName, cavityPoint, cavitySurface, interactionProperty<, ambientPressure, thickness, useAdiabatic, checkNormals>)**](../ker/ker-link.md#ker-fluidcavitystate-fluidcavitystate-pyc)

[**FluidExchange(name , createStepName, cavityPoint, interactionProperty<, definition, secondCavity, exchangeArea>)**](../ker/ker-link.md#ker-fluidexchange-fluidexchange-pyc)

[**FluidExchangeProperty(name , dataTable<, definition, pressureDependency, temperatureDependency, fieldDependencies>)**](../ker/ker-link.md#ker-fluidexchangeproperty-fluidexchangeproperty-pyc)

[**GapElectricalConductance(<definition, clearanceDependency, pressureDependency, temperatureDependencyC, dependenciesC, clearanceDepTable, temperatureDependencyP, dependenciesP, pressureDepTable>)**](../ker/ker-link.md#ker-gapelectricalconductance-gapelectricalconductance-pyc)

[**StabilizationAssignment.appendInStep(stepName, assignments)**](../ker/ker-link.md#ker-stabilizationassignment-appendinstep-pyc)

[**StabilizationAssignment.changeValuesInStep(stepName, index, value)**](../ker/ker-link.md#ker-stabilizationassignment-changevaluesinstep-pyc)

[**StabilizationAssignment.delete(indices)**](../ker/ker-link.md#ker-stabilizationassignment-delete-pyc)

[StdInitialization(name<, *useInterferenceFit*, **overclosureType**, **interferenceDistance**, **clearanceDistance**, openingTolerance, overclosureTolerance>)](../ker/ker-link.md#ker-stdinitialization-stdinitialization-pyc)

[**StdStabilization(name<, zeroDistance, reductionFactor, scaleFactor, tangentialFactor, amplitude, reset>)**](../ker/ker-link.md#ker-stdstabilization-stdstabilization-pyc)

**Job commands**

No changes.
**Load commands**

[**BodyCurrentDensity(name, createStepName, region, comp1, comp2, comp3<, amplitude, distributionType>)**](../ker/ker-link.md#ker-bodycurrentdensity-bodycurrentdensity-pyc)

[ConnectorForce(name, createStepName, *connectors*<, **region**, **fastenerName**, **fastenerSetName**, f1, f2, f3, amplitude>)](../ker/ker-link.md#ker-connectorforce-connectorforce-pyc)

[ConnectorMoment(name, createStepName, *connectors*<, **region**, **fastenerName**, **fastenerSetName**, m1, m2, m3, amplitude>)](../ker/ker-link.md#ker-connectormoment-connectormoment-pyc)

[**PorDragBodyForce(name, createStepName, region, fieldName, distributionType, magnitude)**](../ker/ker-link.md#ker-pordragbodyforce-pordragbodyforce-pyc)

[**SurfaceCurrentDensity(name, createStepName, region, comp1, comp2, comp3<, distributionType, amplitude>)**](../ker/ker-link.md#ker-surfacecurrentdensity-surfacecurrentdensity-pyc)

**Load Case commands**

No changes.
**Material commands**

[**MagneticPermeability(table<, **type**, frequencyDependency, temperatureDependency, dependencies>)**](../ker/ker-link.md#ker-magneticpermeability-magneticpermeability-pyc)

[Dielectric(table<, type, **frequencyDependency**, temperatureDependency, dependencies>)](../ker/ker-link.md#ker-dielectric-dielectric-pyc)

[ElectricalConductivity(table<, type, **frequencyDependency**, temperatureDependency, dependencies>)](../ker/ker-link.md#ker-electricalconductivity-electricalconductivity-cpp)

[Permeability(specificWeight, **inertialDragCoefficient**, table<, type, temperatureDependency, dependencies>)](../ker/ker-link.md#ker-permeability-permeability-pyc)

**Mdb commands**

No changes.
**Mesh commands**

[associateMeshWithGeometry(geometricEntity<, **elements**, elemFaces, elemEdges, node>)](../ker/ker-link.md#ker-assembly-associatemeshwithgeometry-pyc)

[**deleteBoundaryLayerControls(regions)**](../ker/ker-link.md#ker-assembly-deleteboundarylayercontrols-pyc)

[**deleteMeshAssociationWithGeometry(geometricEntities <, addBoundingEntities>)**](../ker/ker-link.md#ker-assembly-deletemeshassociationwithgeometry-pyc)

[**setBoundaryLayerControls(regions , firstElemSize, growthFactor, numLayers <, inactiveFaces, setName>)**](../ker/ker-link.md#ker-assembly-setboundarylayercontrols-pyc)

**Messaging commands**

No changes.
**Miscellaneous commands**

No changes.
**Model commands**

No changes.
**Odb commands**

No changes.
**Odb Display commands**

[FieldOutput(name, description, type<, componentLabels, validInvariants, **isEngineeringTensor**>)](../ker/ker-link.md#ker-fieldoutput-fieldoutput-pyc)

[**FieldOutput.addData(field)**](../ker/ker-link.md#ker-fieldoutput-adddata2-pyc)

**Optimization commands**

[TopologyTask(name<, algorithm, densityMoveLimit, densityUpdateStrategy, elementDensityDeltaStopCriteria, filterRadius, firstCycleDeletedVolume, firstCycleDeletedVolumeTechnique, freezeBoundaryConditionRegions, freezeLoadRegions, frequencySpectrumWeight, initialDensity, materialInterpolationPenalty, materialInterpolationTechnique, maxDensity, minDensity, modeTrackingRegion, numDesignCycles, numFulfilledStopCriteria, numTrackedModes, objectiveFunctionDeltaStopCriteria, region, **softDeletionMethod**, softDeletionRadius, softDeletionRegion, **softDeletionThreshold**, stepSize, stiffnessMassDamping, stopCriteriaDesignCycle, structuralMassDamping, viscousMassDamping, viscousStiffnessDamping>)](../ker/ker-link.md#ker-topologytask-topologytask-pyc)

**Part commands**

[Assembly.PartFromInstanceMesh(name<, partInstances, **copyPartSets**, **copyAssemblySets**>)](../ker/ker-link.md#ker-part-partfrominstancemesh-pyc)

[PartFromGeometryFile(name, geometryFile, dimensionality, type<, bodyNum, combine, *stitchAfterCombine*, **retainBoundary**, stitchTolerance, twist, *topology*, scale, convertToAnalytical, *stitchEdges*, convertToPrecise>)](../ker/ker-link.md#ker-part-partfromgeometryfile-pyc)

[FaceFromElementFaces(elementFaces)](../ker/ker-link.md#ker-feature-facefromelementfaces-pyc)

[**getAssociatedCADPaths()**](../ker/ker-link.md#ker-part-getassociatedcadpaths-pyc)

[**getCADParameters()**](../ker/ker-link.md#ker-part-getcadparameters-pyc)

[**setAssociatedCADPaths(<partFile, rootFile>)**](../ker/ker-link.md#ker-part-setassociatedcadpaths-pyc)

[**Lock()**](../ker/ker-link.md#ker-part-lock-pyc)

[**LockForUpgrade()**](../ker/ker-link.md#ker-part-lockforupgrade-pyc)

[PartFromMesh(name<, **copySets**>)](../ker/ker-link.md#ker-part-partfrommesh-pyc)

[**Unlock()**](../ker/ker-link.md#ker-part-unlock-pyc)

**Partition commands**

No changes.
**Path and Probe commands**

No changes.
**Plot Options commands**

[ViewCutOptions.setValues(<options, belowOptions, useBelowOptions, onOptions, useOnOptions, aboveOptions, useAboveOptions, freeBodyCutThru, **freeBodyStepThru**, numCutFreeBody, **displaySlicing**, **slicingAtPathNodes**, **freeBodySumOnPath**, cutFreeBodyMin, cutFreeBodyMax, showHeatFlowRate, summationLoc, componentResolution, csysName, **pathName**, summationPoint, **yAxis**>)](../ker/ker-link.md#ker-viewcutoptions-setvalues-pyc)

**Plug-in commands**

No changes.
**Predefined Field commands**

[**FluidCavityPressure(name, fluidCavity, fluidPressure)**](../ker/ker-link.md#ker-fluidcavitypressure-fluidcavitypressure-pyc)

**Print commands**

No changes.
**Property commands**

No changes.
**Region commands**

No changes.
**Section commands**

No changes.
**Session commands**

No changes.
**Sketcher commands**

No changes.
**Step  commands (step)**

[**CoupledThermalElectricalStructuralStep(name, previous<, description, response, timePeriod, nlgeom, stabilizationMethod, stabilizationMagnitude, timeIncrementationMethod, maxNumInc, initialInc, minInc, maxInc, deltmx, cetol, creepIntegration, matrixStorage, amplitude, extrapolation, maintainAttributes, convertSDI, adaptiveDampingRatio, continueDampingFactors>)**](../ker/ker-link.md#ker-coupledthermalelectricalstructuralstep-coupledtherma-pyc)

[**EmagTimeHarmonicStep(name, previous, frequencyRange<, description, factorization>)**](../ker/ker-link.md#ker-emagtimeharmonicstep-emagtimeharmonicstep-pyc)

[FlowStep(name, previous<, description, timePeriod, energyEquation, incrementation, initialInc, divergenceTol, maximumCFL, incAdjustmentFreq, stepGrowthFactor, viscousFactor, boundaryFactor, **advectionFactor**, momOutputDiagnostics, momOutputConvergence, momIterationLimit, momCheckingFreq, momConvergenceLimit, pressureType, pressSolverType, pressSmootherType, pressPreSweeps, pressPostSweeps, pressOutputDiagnostics, pressOutputConvergence, pressIterationLimit, pressCheckingFreq, pressConvergenceLimit, transOutputDiagnostics, transOutputConvergence, transIterationLimit, transCheckingFreq, transConvergenceLimit, turbulenceModel, turbPrandtlNumber, turbCb1, turbCb2, turbCv1, turbCv2, turbCw1, turbCw2, turbCw3, turbSigma, turbKappa, turbCmu, turbCeps1, turbCeps2t, turbSigma_k, turbSigma_eps, turbBeta, turbLambda0>)](../ker/ker-link.md#ker-flowstep-flowstep-pyc)

**Step commands (miscellaneous) **

No changes.
**Step (output) commands**

[Model.FieldOutputRequest(name, createStepName <, region, variables, frequency, modes, timeInterval, numIntervals, timeMarks, boltLoad, sectionPoints, interactions, rebar, filter, directions, fasteners, assembledFastener, assembledFastenerSet, **exteriorOnly**, layupNames, layupLocationMethod, outputAtPlyTop, outputAtPlyMid, outputAtPlyBottom>)](../ker/ker-link.md#ker-fieldoutputrequest-setvalues-pyc)

**Text Representation commands**

[**redentABQ.indentFile(path<, indent, backup, runTest, verbose>)**](../ker/ker-link.md#ker-txt-redentabq-indentfile-pyc)

**Utility commands**

The Boolean object and Boolean constructor have both been renamed to AbaqusBoolean.

[**Customization.journalMethodCall(objectPath, methodName, args, kargs)**](../ker/ker-link.md#ker-utl-customization-journalmethodcall-pyc)

**View commands**

No changes.
**XY commands**

[AreaStyle(<color, *show*, **fill**, style>)](../ker/ker-link.md#ker-areastyle-areastyle-pyc)

[XYDataFromPath(path, includeIntersections, shape, **pathStyle**, **numIntervals**, labelType <, name, viewport, step, frame, variable, deformedMag, numericForm, complexAngle>)](../ker/ker-link.md#ker-xydata-xydatafrompath-pyc)




