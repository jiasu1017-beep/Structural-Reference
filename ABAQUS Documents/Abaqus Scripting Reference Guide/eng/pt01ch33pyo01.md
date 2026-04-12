# 33.1 Model object







          Abaqus creates a Model               object named `Model-1`               when a session is started.

**Access**

```
mdb.models[*name*]
```

### 33.1.1 Model(...)

This method creates a Model object.

**Path**

```
mdb.Model
```

**Required argument**

*name*

A String specifying the repository key.

**Optional arguments**

*description*

A String specifying the purpose and contents of the Model object. The default value is an empty string.

*stefanBoltzmann*

 `None` or a Float specifying the Stefan-Boltzmann constant. The default value is `None`.

*absoluteZero*

 `None` or a Float specifying the absolute zero constant. The default value is `None`.

*waveFormulation*

A SymbolicConstant specifying the type of incident wave formulation to be used in acoustic problems. Possible values are NOT_SET, SCATTERED, and TOTAL. The default value is NOT_SET.

*modelType*

A SymbolicConstant specifying the analysis model type. Possible values are STANDARD_EXPLICIT CFD                              and ELECTROMAGNETIC. The default is STANDARD_EXPLICIT.

*universalGas*

 `None` or a Float specifying the universal gas constant. The default value is `None`.

**Return value**

A Model object.

**Exceptions**

None.

### 33.1.2 ModelFromInputFile(...)

This method creates a Model object by reading the keywords in an input file and creating the corresponding Abaqus/CAE objects.

**Path**

```
mdb.ModelFromInputFile
```

**Required arguments**

*name*

A String specifying the repository key.

*inputFileName*

A String specifying the name of the input file (including the `.inp`                              extension) to be parsed into the new model. This String can also be the full path to the input file if it is located in another directory.

**Optional arguments**

None.

**Return value**

A Model object.

**Exceptions**

None.

### 33.1.3 ModelFromOdbFile(...)

This method creates a Model object by reading an output database and creating any corresponding Abaqus/CAE objects.

**Path**

```
mdb.ModelFromOdbFile
```

**Required arguments**

*name*

A String specifying the repository key.

*odbFileName*

A String specifying the name of the output database file (including the `.odb`                              extension) to be read into the new model. This String can also be the full path to the output database file if it is located in another directory.

**Optional arguments**

None.

**Return value**

A Model object.

**Exceptions**

None.

### 33.1.4 ModelFromNastranFile(...)

This method creates a Model object by reading the keywords in a Nastran bulk data file or Nastran input file and creating any corresponding Abaqus/CAE objects. The default values is discussed in following and can be defined alternatively in the Abaqus environment file as the one used for the translator from Nastran to Abaqus. For more information, see ["Translating Nastran bulk data files to Abaqus input files," Section 3.2.28 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-int-dnasabaproc).

**Path**

```
mdb.ModelFromNastranFile
```

**Required arguments**

*modelName*

A String specifying the repository key.

*inputFileName*

A String specifying the name of the Nastran input file (including the `.bdf, .dat, .nas, .nastran, .blk, .bulk`                              extension) to be read into the new model. This String can also be the full path to the Nastran input file if it is located in another directory.

**Optional arguments**

*sectionConsolidation*

A SymbolicConstant specifying the method used to create shell section. Possible values are PRESERVE_SECTION, GROUP_BY_MATERIAL, and NONE. If PRESERVE_SECTION                              is used, an Abaqus section is created corresponding to each shell property ID. If GROUP_BY_MATERIAL                              is used, a single Abaqus section is created for all homogeneous elements referencing the same material. In both cases, material orientations and offsets are created using discrete fields. If NONE                              is used, a separate shell section is created for each combination of orientation, material offset, and/or thickness. The default is PRESERVE_SECTION.

*preIntegratedShell*

A Boolean specifying whether the pre-integrated shell section is created in default for shell element. The default value is OFF.

*weightMassScaling*

A Boolean specifying whether the value on the Nastran data line PARAM, WTMASS is used as a multiplier for all density, mass, and rotary inertia values created in the Abaqus input file. The default value is ON.

*loadCases*

A Boolean specifying whether each SUBCASE for linear static analyses is translated to a [*LOAD CASE](../key/key-link.md#usb-kws-hloadcase)                              option, and all such [*LOAD CASE](../key/key-link.md#usb-kws-hloadcase)                              options are grouped in a single [*STEP](../key/key-link.md#usb-kws-hstep)                              option. The default value is ON.

*coupleBeamOffsets*

A Boolean specifying whether to translate the beam element connectivity to newly created nodes at the offset location and rigidly coupling the new and original nodes. If not, beam element offsets are translated to the [*CENTROID](../key/key-link.md#usb-kws-mcentroid)                              and [*SHEAR CENTER](../key/key-link.md#usb-kws-mshearcenter)                              options, which are suboptions of the [*BEAM GENERAL SECTION](../key/key-link.md#usb-kws-mbeamgensect)                              option. The default value is ON. When the beam element references a PBARL or PBEAML property or if the beam offset has a significant component in the direction of the beam axis, the setting for this argument is always ON.

*cbar*

A String specifying the 2-node beam that is created from CBAR and CBEAM elements. Possible values are B31 and B33. The default is B31.

*cquad4*

A String specifying the 4-node shell that is created from CQUAD4 elements. Possible values are S4 and S4R. The default is S4. If a reduced-integration element is chosen, the enhanced hourglass formulation is applied automatically.

*chexa*

A String specifying the 8-node brick that is created from CHEXA elements. Possible values are C3D8I, C3D8 and C3D8R. The default is C3D8I. If a reduced-integration element is chosen, the enhanced hourglass formulation is applied automatically.

*ctetra*

A String specifying the 10-node tetrahedron that is created from CTETRA elements. Possible values are C3D10 and C3D10M. The default is C3D10.

*keepTranslatedFiles*

A Boolean specifying whether to keep the generated Abaqus input file after the model is created from the Nastran input file. The default value is ON.

**Return value**

A Model object.

**Exceptions**

None.

### 33.1.5 setValues(...)

This method modifies the Model                     object.

**Required arguments**

None.

**Optional arguments**

*description*

A String specifying the purpose and contents of the Model object. The default value is an empty string.

*noPartsInputFile*

A Boolean specifying whether an input file should be written without parts and assemblies. The default value is OFF.

*absoluteZero*

 `None` or a Float specifying the absolute zero constant. The default value is `None`.

*stefanBoltzmann*

 `None` or a Float specifying the Stefan-Boltzmann constant. The default value is `None`.

*waveFormulation*

A SymbolicConstant specifying the type of incident wave formulation to be used in acoustic problems. Possible values are NOT_SET, SCATTERED, and TOTAL. The default value is NOT_SET.

*universalGas*

 `None` or a Float specifying the universal gas constant. The default value is `None`.

*restartJob*

A String specifying the name of the job that generated the restart data.

*restartStep*

A String specifying the name of the step where the restart analysis will start.

*restartIncrement*

An Int specifying the increment, interval, iteration or cycle where the restart analysis will start. To select the end of the step use the SymbolicConstant STEP_END.

*endRestartStep*

A Boolean specifying that the step specified by *restartStep*                  should be terminated at the increment specified by *restartIncrement*.

*globalJob*

A String specifying the name of the job that generated the results for the global model.

*shellToSolid*

A Boolean specifying that a shell global model drives a solid submodel.

**Return value**

None

**Exceptions**

None.

### 33.1.6 Members

The Model object can have the following members:

*name*

A String specifying the repository key.

*stefanBoltzmann*

 `None` or a Float specifying the Stefan-Boltzmann constant. The default value is `None`.

*absoluteZero*

 `None` or a Float specifying the absolute zero constant. The default value is `None`.

*waveFormulation*

A SymbolicConstant specifying the type of incident wave formulation to be used in acoustic problems. Possible values are NOT_SET, SCATTERED, and TOTAL. The default value is NOT_SET.

*universalGas*

 `None` or a Float specifying the universal gas constant. The default value is `None`.

*noPartsInputFile*

A Boolean specifying whether an input file should be written without parts and assemblies. The default value is OFF.

*restartIncrement*

An Int specifying the increment, interval, iteration or cycle where the restart analysis will start. To select the end of the step use the SymbolicConstant STEP_END.

*endRestartStep*

A Boolean specifying that the step specified by *restartStep*                  should be terminated at the increment specified by *restartIncrement*.

*shellToSolid*

A Boolean specifying that a shell global model drives a solid submodel.

*lastChangedCount*

A Float specifying the time stamp that indicates when the model was last changed.

*description*

A String specifying the purpose and contents of the Model object. The default value is an empty string.

*restartJob*

A String specifying the name of the job that generated the restart data.

*restartStep*

A String specifying the name of the step where the restart analysis will start.

*globalJob*

A String specifying the name of the job that generated the results for the global model.

*keywordBlock*

A [KeywordBlock](pt01ch33pyo02.md) object.

*rootAssembly*

An [Assembly](pt01ch06pyo01.md) object.

*amplitudes*

A repository of [Amplitude](pt01ch03pyo01.md) objects.

*profiles*

A repository of [Profile](pt01ch08pyo01.md) objects.

*boundaryConditions*

A repository of [BoundaryCondition](pt01ch09pyo01.md) objects.

*constraints*

A repository of [Constraint](pt01ch13pyo01.md) objects.

*analyticalFields*

A repository of [AnalyticalField](pt01ch21pyo02.md) objects.

*discreteFields*

A repository of [DiscreteField](pt01ch21pyo04.md) objects.

*predefinedFields*

A repository of [PredefinedField](pt01ch42pyo01.md) objects.

*interactions*

A repository of [Interaction](pt01ch25pyo01.md) objects.

*interactionProperties*

A repository of [InteractionProperty](pt01ch25pyo48.md) objects.

*contactControls*

A repository of [ContactControl](pt01ch25pyo16.md) objects.

*contactInitializations*

A repository of [ContactInitialization](pt01ch25pyo20.md) objects.

*contactStabilizations*

A repository of [ContactStabilization](pt01ch25pyo23.md) objects.

*linkedInstances*

A tuple of tuples of Strings specifying the linked child PartInstance name in the current model to the corresponding parent PartInstance name in a different model.

*linkedParts*

A tuple of tuples of Strings specifying the linked child Part name in the current model to the corresponding parent Part name in a different model.

*loads*

A repository of [Load](pt01ch27pyo01.md) objects.

*materials*

A repository of [Material](pt01ch29pyo01.md) objects.

*calibrations*

A repository of [Calibration](pt01ch10pyo01.md) objects.

*sections*

A repository of [Section](pt01ch46pyo01.md) objects.

*remeshingRules*

A repository of [RemeshingRule](pt01ch02pyo11.md) objects.

*sketches*

A repository of [ConstrainedSketch](pt01ch48pyo01.md) objects.

*parts*

A repository of [Part](pt01ch37pyo01.md) objects.

*steps*

A repository of [Step](pt01ch49pyo01.md) objects.

*featureOptions*

A [FeatureOptions](pt01ch20pyo02.md) object.

*adaptiveMeshConstraints*

A repository of [AdaptiveMeshConstraint](pt01ch02pyo01.md) objects.

*adaptiveMeshControls*

A repository of [AdaptiveMeshControl](pt01ch02pyo03.md) objects.

*timePoints*

A repository of [TimePoint](pt01ch51pyo09.md) objects.

*filters*

A repository of [Filter](pt01ch22pyo01.md) objects.

*integratedOutputSections*

A repository of [IntegratedOutputSection](pt01ch51pyo06.md) objects.

*fieldOutputRequests*

A repository of [FieldOutputRequest](pt01ch51pyo02.md) objects.

*historyOutputRequests*

A repository of [HistoryOutputRequest](pt01ch51pyo04.md) objects.

*optimizationTasks*

A repository of [OptimizationTask](pt01ch36pyo01.md) objects.

### 33.1.7 Corresponding analysis keywords

| [*PHYSICAL CONSTANTS](../key/key-link.md#usb-kws-mphysicalconsts) |
| --- |




