# *SUBSTRUCTURE MATRIX OUTPUT







### *SUBSTRUCTURE MATRIX OUTPUTWrite a substructure's recovery matrix, reduced stiffness matrix, mass matrix, load case vectors, and gravity load vectors to a file.

This option is used to write a substructure's recovery matrix, reduced stiffness matrix, mass matrix, load case vectors, and gravity load vectors to a file. It can be used only in a [*SUBSTRUCTURE GENERATE](ch18abk42.md) analysis.

**Product: **Abaqus/Standard  

**Type: **History data 

**Level: **This option is not supported in a model defined in terms of an assembly of part instances.

##### **Reference:**

- ["Defining substructures," Section 10.1.2 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-anl-asuperelementdef)

### **Optional parameters: **

FILE NAME

This parameter is intended for use with OUTPUT FILE=USER DEFINED.

Set this parameter equal to the name of the file (without an extension) to which the data will be written. The extension `.mtx` will be added to the file name provided by the user; see ["Input syntax rules," Section 1.2.1 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-int-iinputsyntax), for the syntax of such file names.

If the OUTPUT FILE parameter is omitted or set equal to RESULTS FILE, use of the FILE NAME parameter overrides the OUTPUT FILE setting; the data will be written to the named file, not to the results (`.fil`) file.

GRAVITY LOAD

Set GRAVITY LOAD=YES to write the substructure gravity load vectors (only available if the gravity load vectors are requested with the [*SUBSTRUCTURE GENERATE](ch18abk42.md) option). The default is GRAVITY LOAD=NO.

MASS

Set MASS=YES to write the substructure mass matrix (only available if the mass matrix is requested with the [*SUBSTRUCTURE GENERATE](ch18abk42.md) option). The default is MASS=NO.

OUTPUT FILE

Set OUTPUT FILE=RESULTS FILE (default) to write the data to the results (`.fil`) file in the format specified in ["Results file output format," Section 5.1.2 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-out-fformat).

Set OUTPUT FILE=USER DEFINED to write the results to a user-specified file in the format of the [*USER ELEMENT](ch20abk07.md), LINEAR option (["User-defined elements," Section 32.15.1 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-elm-euserelem)). The name of the file is specified using the FILE NAME parameter.

RECOVERY MATRIX

Set RECOVERY MATRIX=YES to write the substructure recovery matrix (only available if the recovery matrix is requested with the [*SUBSTRUCTURE GENERATE](ch18abk42.md) option). The default is RECOVERY MATRIX=NO.

SLOAD

Set SLOAD=YES to write the substructure load case vectors. The default is SLOAD=NO.

STIFFNESS

Set STIFFNESS=YES to write the substructure stiffness matrix. The default is STIFFNESS=NO.

**There are no data lines associated with this option.**



