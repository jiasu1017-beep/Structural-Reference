# Summary of C++ ODB API changes between Abaqus 6.13 and Abaqus 6.14







This section summarizes the changes and the additions that have been made to the C++ ODB API between Abaqus 6.13 and Abaqus 6.14. SIMULIA makes every attempt to have the Abaqus Scripting Interface be backward compatible, and Abaqus can execute most Abaqus Scripting Interface scripts from previous versions of Abaqus. However, backward compatibility is not guaranteed beyond two versions of Abaqus, and it is recommended that you upgrade your commands to the most recent version.

The full path to the method is listed along with the required and optional arguments. Arguments enclosed within angle brackets, “<>”, are optional arguments. The syntax of the commands is as follows:

| (**Blue bold text**) | New method or argument. |
| --- | --- |
| (*Red italic text*) | Removed method or argument. |
| (*Green italic text*) | Changed argument; for example, the argument type has changed or the possible values of the SymbolicConstant have changed. |

You can click on a method to view its description in the command reference. Refer to the [Abaqus Scripting Reference Guide](book01.md) for Abaqus 6.13 for a description of methods that have been removed.**Amplitude commands**

No changes.
**Beam section profile commands**

No changes.
**Connector commands**

No changes.
**Filter commands**

No changes.
**Material commands**

No changes.
**Odb commands**

[FieldOutput.addData(position, instance, labels, data<, sectionPoint, localCoordSystem, **conjugateData**>)](../ker/ker-link.md#ker-fieldoutput-adddata-cpp)

[**FieldOutput.addData(position, instance, labels, data<, sectionPoint, localCoordSystem, conjugateData>)**](../ker/ker-link.md#ker-fieldoutput-adddata3-cpp)

[OdbAssembly.ConnectorOrientation(region, **csys1**, **axis1**, **angle1**, **csys2**, **axis2**, **angle2**<, *csys1*, *axis1*, *angle1*, *csys2*, *axis2*, *angle2*>)](../ker/ker-link.md#ker-odbassembly-connectororientation-cpp)

[**OdbAssembly.ConnectorOrientation(region, csys1, axis1, angle1<, orient2sameAs1>)**](../ker/ker-link.md#ker-odbassembly-connectororientation1-cpp)

**Property commands**

No changes.
**Section commands**

[CompositeShellSection(name, layup<, symmetric, **layupName**, thicknessType, preIntegrate, poissonDefinition, poisson, integrationRule, temperature, idealization, nTemp, thicknessModulus, useDensity, density, *layupName*, thicknessField, nodalThicknessField>)](../ker/ker-link.md#ker-compositeshellsection-compositeshellsection-cpp)

[HomogeneousShellSection(name, **thickness**, material<, *thickness*, numIntPts, thicknessType, preIntegrate, poissonDefinition, poisson, integrationRule, temperature, idealization, nTemp, thicknessModulus, useDensity, density, thicknessField, nodalThicknessField, >)](../ker/ker-link.md#ker-homogeneousshellsection-homogeneousshellsection-cpp)

**Infrastructure commands**

[Sequence.odb_SequenceType(<initialSize, *growSize*>)](../ker/ker-link.md#ker-inf-seq-seq-cpp)




