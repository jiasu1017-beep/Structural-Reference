# *MATRIX INPUT







### *MATRIX INPUTRead in a matrix for a part of the model.

This option can be used to input a matrix in sparse format. 

**Product: **Abaqus/Standard  

**Type: **Model data  

**Level: **Model  

##### **References:**

- ["Defining matrices," Section 2.11.1 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-int-idefiningmatrices)
- [*MATRIX ASSEMBLE](ch13abk10.md)

### **Required parameter: **

NAME

Set this parameter equal to a label that will be used to refer to this matrix.

### **Optional parameters: **

INPUT

Set this parameter equal to the name of the alternate input file from which the data lines are to be read in text format. See ["Input syntax rules," Section 1.2.1 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-int-iinputsyntax), for the syntax of such file names.

Set this parameter equal to the name of the `.sim` file to read a matrix from the SIM database. The MATRIX parameter is also required in this case.

 If this parameter is omitted, it is assumed that the data follow the keyword line.

MATRIX

This parameter defines the matrix to be read from the SIM database. It must be used together with the INPUT parameter defining the `.sim` file.

Set MATRIX=STIFFNESS to read the stiffness matrix.

Set MATRIX=MASS to read the mass matrix.

Set MATRIX=VISCOUS DAMPING to read the viscous damping matrix.

Set MATRIX=STRUCTURAL DAMPING to read the structural damping matrix.

SCALE FACTOR

Set this parameter equal to a nonzero real number ![](../graphics/key_eqn00896.gif) by which all matrix entries will be multiplied. The default value is ![](../graphics/key_eqn00897.gif).

TYPE

This parameter defines the shape of the matrix.

Set TYPE=SYMMETRIC (default) to read the upper or lower triangular portion of a square symmetric matrix. If a full matrix is specified, corresponding terms above and below the diagonal must be equal.

Set TYPE=UNSYMMETRIC to read a square unsymmetric matrix.

### **Data lines to define the matrix in sparse format (only nonzero terms): **

**First line:**

Give data to define a symmetric matrix in lower triangular, upper triangular, or square format. For a square matrix to be symmetric, corresponding entries above and below the diagonal must have exactly the same values.

Repeat this data line as often as necessary.




