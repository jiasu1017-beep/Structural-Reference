# Summary of C++ ODB API changes between Abaqus 6.12 and Abaqus 6.13







This section summarizes the changes and the additions that have been made to the C++ ODB API between Abaqus 6.12 and Abaqus 6.13. SIMULIA makes every attempt to have the Abaqus Scripting Interface be backward compatible, and Abaqus can execute most Abaqus Scripting Interface scripts from previous versions of Abaqus. However, backward compatibility is not guaranteed beyond two versions of Abaqus, and it is recommended that you upgrade your commands to the most recent version.

The full path to the method is listed along with the required and optional arguments. Arguments enclosed within angle brackets, “<>”, are optional arguments. The syntax of the commands is as follows:

| (**Blue bold text**) | New method or argument. |
| --- | --- |
| (*Red italic text*) | Removed method or argument. |
| (*Green italic text*) | Changed argument; for example, the argument type has changed or the possible values of the SymbolicConstant have changed. |

You can click on a method to view its description in the command reference. Refer to the [Abaqus Scripting Reference Guide](book01.md) for Abaqus 6.12 for a description of methods that have been removed.**Amplitude commands**

No changes.
**Beam section profile commands**

No changes.
**Connector commands**

No changes.
**Filter commands**

No changes.
**Material commands**

[Material.MagneticPermeability(table, **table2**, **table3**<, type, frequencyDependency, temperatureDependency, dependencies, **nonlinearBH**>)](../ker/ker-link.md#ker-magneticpermeability-magneticpermeability-cpp)

**Odb commands**

No changes.
**Property commands**

No changes.
**Section commands**

[BeamSection.TransverseShearBeam(**scfDefinition**<, k23, k13, slendernessCompensation>)](../ker/ker-link.md#ker-transverseshearbeam-transverseshearbeam-cpp)

**Infrastructure commands**

No changes.



