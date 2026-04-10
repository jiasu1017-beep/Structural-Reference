# *ELEMENT







### *ELEMENTDefine elements by giving their nodes.

This option is used to define an element directly by specifying its nodes.

**Products: **Abaqus/Standard  Abaqus/Explicit  Abaqus/CFD  Abaqus/CAE  

**Type: **Model data  

**Level: **Part,  Part instance,  Assembly  

**Abaqus/CAE: **Mesh module

##### **Reference:**

- ["Element definition," Section 2.2.1 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-int-ielement)

### **Required parameter: **

TYPE

Set this parameter equal to the element type, as defined in [Part VI, "Elements," of the Abaqus Analysis User's Guide](../usb/usb-link.md#usbechapter).

For user elements specify the U*n* type identification (see ["User-defined elements," Section 32.15.1 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-elm-euserelem)). The [*USER ELEMENT](ch20abk07.md) option must also appear in the same input file.

For substructures specify the Z*n* type identification (see ["Using substructures," Section 10.1.1 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-anl-asuperelements)).

### **Optional parameters: **

ELSET

Set this parameter equal to the name of the element set to which these elements will be assigned.

FILE

This parameter applies only to Abaqus/Standard analyses.

This parameter is meaningful only for substructures. Set this parameter equal to the name (with no extension) of the substructure library on which the substructure resides. See ["Input syntax rules," Section 1.2.1 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-int-iinputsyntax), for the syntax of such library names. If no name is specified, the default name is used (see ["Using substructures," Section 10.1.1 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-anl-asuperelements)).

INPUT

Set this parameter equal to the name of the alternate input file containing the data lines for this option. See ["Input syntax rules," Section 1.2.1 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-int-iinputsyntax), for the syntax of such file names. If this parameter is omitted, it is assumed that the data follow the keyword line.

OFFSET

When the [*ELEMENT](ch05abk07.md) option is used to define the connectivity of axisymmetric elements with asymmetric deformation in Abaqus/Standard, set this parameter equal to a positive offset number for use in specifying the additional nodes needed in the connectivity (see ["Element definition," Section 2.2.1 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-int-ielement), for more information). The default is OFFSET=100000.

When the [*ELEMENT](ch05abk07.md) option is used to define the connectivity of gasket elements in Abaqus/Standard or cohesive elements, set the OFFSET parameter equal to a positive offset number for use in defining the remaining nodes of the element when only part of the element nodes are defined explicitly. If this parameter is omitted, the connectivity of the entire gasket or cohesive element must be specified on the data lines (see ["Defining the gasket element's initial geometry," Section 32.6.4 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-elm-egasketinit), and ["Defining the cohesive element's initial geometry," Section 32.5.4 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-elm-ecohesiveinit)).

SOLID ELEMENT NUMBERING

This parameter applies only to Abaqus/Standard analyses.

This parameter can be used only when the [*ELEMENT](ch05abk07.md) option is used to define gasket elements. Use this parameter to specify the connectivity of gasket elements using the node ordering of an equivalent solid element. Set it equal to the face number of the equivalent solid element that corresponds to the first face (SNEG) of the gasket element. If no value is assigned to this parameter, it is assumed that the first face (S1) of the solid element corresponds to the first face of the gasket element.

### **Data lines to define the elements: **

**First line:**

The order of nodes for each element type (the element's connectivity) is given in [Part VI, "Elements," of the Abaqus Analysis User's Guide](../usb/usb-link.md#usbechapter).

**Continuation lines (only needed if the previous line ends with a comma):**

Repeat this set of data lines as often as necessary, with up to 16 integer values per line (maximum 80 characters).




