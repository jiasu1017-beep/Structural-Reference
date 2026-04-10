# *NODE







### *NODESpecify nodal coordinates.

This option is used to define a node directly by specifying its coordinates. Nodal coordinates given in this option are in a local system if the [*SYSTEM](ch18abk59.md) option is in effect when this option is used.

**Products: **Abaqus/Standard  Abaqus/Explicit  Abaqus/CFD  Abaqus/CAE  

**Type: **Model data  

**Level: **Part,  Part instance,  Assembly  

**Abaqus/CAE: **Mesh module

##### **Reference:**

- ["Node definition," Section 2.1.1 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-int-inode)

### **Optional parameters: **

INPUT

Set this parameter equal to the name of the alternate input file containing the data lines for this option. See ["Input syntax rules," Section 1.2.1 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-int-iinputsyntax), for the syntax of such file names. If this parameter is omitted, it is assumed that the data follow the keyword line.

NSET

Set this parameter equal to the name of the node set to which these nodes will be assigned. Node sets created or modified with this option will always be sorted.

SYSTEM

Set SYSTEM=R (default) to give coordinates in a rectangular Cartesian coordinate system. Set SYSTEM=C to give coordinates in a cylindrical system. Set SYSTEM=S to give coordinates in a spherical system. See [Figure 14.9--1](ch14abk09.md#kngen).

The SYSTEM parameter is entirely local to this option. As the data lines are read, the coordinates given are transformed to rectangular Cartesian coordinates immediately. If the [*SYSTEM](ch18abk59.md) option is also in effect, these are local rectangular Cartesian coordinates, which are then immediately transformed to global Cartesian coordinates.

### **Data lines to define the node: **

**First line:**

The normal will be used only for element types with rotational degrees of freedom. See [Part VI, "Elements," of the Abaqus Analysis User's Guide](../usb/usb-link.md#usbechapter).

Repeat this data line as often as necessary.

**Figure 14.9–1** Coordinate systems.

![](../graphics/kngen-nls.png)




