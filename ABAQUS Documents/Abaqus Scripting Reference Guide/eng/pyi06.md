# Summary of C++ ODB API changes between Abaqus 6.11 and Abaqus 6.12







This section summarizes the changes and the additions that have been made to the C++ ODB API between Abaqus 6.11 and Abaqus 6.12. SIMULIA makes every attempt to have the Abaqus Scripting Interface be backward compatible, and Abaqus can execute most Abaqus Scripting Interface scripts from previous versions of Abaqus. However, backward compatibility is not guaranteed beyond two versions of Abaqus, and it is recommended that you upgrade your commands to the most recent version.

The full path to the method is listed along with the required and optional arguments. Arguments enclosed within angle brackets, “<>”, are optional arguments. The syntax of the commands is as follows:

| (**Blue bold text**) | New method or argument. |
| --- | --- |
| (*Red italic text*) | Removed method or argument. |
| (*Green italic text*) | Changed argument; for example, the argument type has changed or the possible values of the SymbolicConstant have changed. |

You can click on a method to view its description in the command reference. Refer to the [Abaqus Scripting Reference Guide](book01.md) for Abaqus 6.11 for a description of methods that have been removed.**Amplitude commands**

[**PsdDefinition(name, data<, unitType, referenceGravityAcceleration, referenecePower, user, timeSpan, amplitude>)**](../ker/ker-link.md#ker-psddefinition-psddefinition-cpp)

**Beam section profile commands**

[PipeProfile(name, r, t<, **formulation**>)](../ker/ker-link.md#ker-pipeprofile-pipeprofile-cpp)

**Connector commands**

No changes.
**Filter commands**

No changes.
**Material commands**

[**MagneticPermeability(table<, **type**, frequencyDependency, temperatureDependency, dependencies>)**](../ker/ker-link.md#ker-magneticpermeability-magneticpermeability-cpp)

[Dielectric(table<, type, **frequencyDependency**, temperatureDependency, dependencies>)](../ker/ker-link.md#ker-dielectric-dielectric-cpp)

[ElectricalConductivity(table<, type, **frequencyDependency**, temperatureDependency, dependencies>)](../ker/ker-link.md#ker-electricalconductivity-electricalconductivity-cpp)

[Permeability(specificWeight, **inertialDragCoefficient**, table<, type, temperatureDependency, dependencies>)](../ker/ker-link.md#ker-permeability-permeability-cpp)

**Odb commands**

[FieldOutput(name, description, type<, componentLabels, validInvariants, **isEngineeringTensor**>)](../ker/ker-link.md#ker-fieldoutput-fieldoutput-cpp)

[**FieldOutput.addData(field)**](../ker/ker-link.md#ker-fieldoutput-adddata2-cpp)

**Property commands**

No changes.
**Section commands**

No changes.
**Infrastructure commands**

No changes.



