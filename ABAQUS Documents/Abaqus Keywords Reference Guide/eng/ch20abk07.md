# *USER ELEMENT







### *USER ELEMENTIntroduce a user-defined element type.

This option is used to introduce a linear or a general user-defined element. It must precede any reference to this user element on an [*ELEMENT](ch05abk07.md) option.

**Products: **Abaqus/Standard  Abaqus/Explicit  Abaqus/CAE  

**Type: **Model data  

**Level: **Part,  Part instance,  Model  

**Abaqus/CAE: **Actuator/sensor interactions can be defined in the Interaction module.

##### **References:**

- ["User-defined elements," Section 32.15.1 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-elm-euserelem)
- ["UEL," Section 1.1.28 of the Abaqus User Subroutines Reference Guide](../sub/sub-link.md#sub-rtn-uuel)
- ["VUEL," Section 1.2.12 of the Abaqus User Subroutines Reference Guide](../sub/sub-link.md#sub-rtn-uexpuel)
- [*ELEMENT](ch05abk07.md)
- [*MATRIX](ch13abk09.md)
- [*UEL PROPERTY](ch20abk01.md)

### Introducing a linear user-defined element (Abaqus/Standard only)

### **Required parameter: **

TYPE

Set this parameter equal to the element type key used to identify this element on the [*ELEMENT](ch05abk07.md) option. The format of this type key must be U*n* in Abaqus/Standard, where *n* is a positive integer less than 10000. To use this element type, set TYPE=U*n* on the [*ELEMENT](ch05abk07.md) option.

### **Optional parameters: **

FILE

Set this parameter equal to the name of the results file (with no extension) from which the data are to be read. See ["Input syntax rules," Section 1.2.1 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-int-iinputsyntax), for the syntax of such file names.

This parameter can be used only if the user-defined element type is linear and its stiffness and/or mass matrices are to be read from the Abaqus/Standard results file of a previous analysis (in which they were written by using the [*ELEMENT MATRIX OUTPUT](ch05abk08.md) or [*SUBSTRUCTURE MATRIX OUTPUT](ch18abk44.md) options). When this parameter is used, all values are taken from the results file. For example, if the stiffness or mass being read from the results file is not symmetric, the UNSYMM parameter will be invoked automatically.

If this parameter is omitted, the data will be read from a standard input file.

INTEGRATION

This parameter applies only to Abaqus/Standard analyses.

 Set this parameter equal to the number of integration points to be used in Gauss integration. This parameter must be used in conjunction with the TENSOR parameter.

TENSOR

This parameter applies only to Abaqus/Standard analyses.

 Include this parameter to specify the element type. This parameter must be used in conjunction with the INTEGRATION parameter.

Set TENSOR=THREED to specify that it is a three-dimensional element in a stress/displacement or heat transfer analysis.

Set TENSOR=TWOD to specify that it is a two-dimensional element in a heat transfer analysis.

Set TENSOR=PSTRAIN to specify that it is a plane strain element in a stress/displacement analysis.

Set TENSOR=PSTRESS to specify that it is a plane stress element in a stress/displacement analysis.

### **Required parameters if the FILE parameter is included: **

OLD ELEMENT

Set this parameter equal to the element number that was assigned to the element whose matrices are being read. This parameter can also be set to a substructure identifier to read a substructure matrix from an Abaqus/Standard results file.

STEP

Set this parameter equal to the step number in which the element matrix was written. This parameter is not required if using a substructure whose matrix was output during its generation.

INCREMENT

Set this parameter equal to the increment number in which the element matrix was written. This parameter is not required if using a substructure whose matrix was output during its generation.

### **Required parameters if the FILE parameter is omitted: **

LINEAR

Include this parameter to indicate that the behavior of the element type is linear and is defined by a stiffness matrix and/or a mass matrix. The [*MATRIX](ch13abk09.md) option is required to define the element's behavior.

NODES

Set this parameter equal to the number of nodes associated with an element of this type.

### **Optional parameters if the FILE parameter is omitted: **

COORDINATES

Abaqus/Standard assigns space to store the coordinate values at each node in user subroutine [`UEL`](../sub/sub-link.md#sub-xsl-uel). The default number of coordinate values is equal to the largest active degree of freedom of the user element with a maximum of 3. Use the COORDINATES parameter to increase the number of coordinate values.

UNSYMM

Include this parameter if the element matrices are not symmetric. This parameter will cause Abaqus/Standard to use its unsymmetric equation solution capability.

The presence or absence of this parameter determines the form in which the matrices must be provided for reading.

### **Data lines if the FILE parameter is omitted: **

**First line:**

**Second line if the active degrees of freedom are different at subsequent nodes:**

Repeat the second data line as often as necessary.

### Introducing a general user-defined element

### **Required parameters: **

TYPE

Set this parameter equal to the element type key used to identify this element on the [*ELEMENT](ch05abk07.md) option. The format of this type key must be U*n* in Abaqus/Standard and VU*n* in Abaqus/Explicit, where *n* is a positive integer less than 10000. To use this element type, set TYPE=U*n* (or VU*n*) on the [*ELEMENT](ch05abk07.md) option.

NODES

Set this parameter equal to the number of nodes associated with an element of this type.

### **Optional parameters: **

COORDINATES

Set this parameter equal to the maximum number of coordinates needed in user subroutine [`UEL`](../sub/sub-link.md#sub-xsl-uel) in Abaqus/Standard and user subroutine [`VUEL`](../sub/sub-link.md#sub-xsl-vuel) in Abaqus/Explicit at any node point of the element. Abaqus assigns space to store the coordinate values at all the nodes associated with elements of this type. The default is COORDINATES=1.

Abaqus will change the value of COORDINATES to be the maximum of the user-specified value of the COORDINATES parameter or the value of the largest active degree of freedom of the user element that is less than or equal to 3. For example, if COORDINATES=1 and the active degrees of freedom of the user element are 2, 3, and 6, the value of COORDINATES will be changed to 3. If COORDINATES=2 and the active degrees of freedom of the user element are 11 and 12, the value of COORDINATES will remain as 2.

I PROPERTIES

Set this parameter equal to the number of integer property values needed as data in user subroutine [`UEL`](../sub/sub-link.md#sub-xsl-uel) (or [`VUEL`](../sub/sub-link.md#sub-xsl-vuel)) to define such an element. The default is I PROPERTIES=0.

PROPERTIES

Set this parameter equal to the number of real (floating point) property values needed as data in user subroutine [`UEL`](../sub/sub-link.md#sub-xsl-uel)  (or [`VUEL`](../sub/sub-link.md#sub-xsl-vuel)) to define such an element. The default is PROPERTIES=0.

UNSYMM

This parameter applies only to Abaqus/Standard analyses. 

Include this parameter if the element matrices are not symmetric. This parameter will cause Abaqus/Standard to use its unsymmetric equation solution capability.

VARIABLES

Set this parameter equal to the number of solution-dependent state variables that must be stored within the element. Its value must be greater than 0. The default is VARIABLES=1.

### **Data lines to define a general user-defined element: **

**First line:**

**Second line if the active degrees of freedom are different at subsequent nodes:**

Repeat the second data line as often as necessary.




