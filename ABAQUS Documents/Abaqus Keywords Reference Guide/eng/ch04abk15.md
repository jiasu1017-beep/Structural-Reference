# *DESIGN GRADIENT







### *DESIGN GRADIENTDirectly specify design gradients for design sensitivity analysis.

This option is used to specify directly design gradients with respect to design parameters, excluding design parameters related to shape. (By default, Abaqus/Design will automatically determine the design gradients with respect to non-shape design parameters numerically based on the parameterization of the input file. Design gradients with respect to shape design parameters must be specified via the [*PARAMETER SHAPE VARIATION](ch16abk03.md) option.)

**Product: **Abaqus/Design  

**Type: **Model data  

**Level: **Part,  Part instance,  Assembly,  Model,  Step

##### **References:**

- ["Design sensitivity analysis," Section 19.1.1 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-anl-adsa)
- [*PARAMETER](ch16abk01.md)
- [*DESIGN PARAMETER](ch04abk16.md)

### **Required parameters: **

DEPENDENT

Set this parameter equal to the list of parameter names whose gradients with respect to the design parameter are to be specified. The list must be given inside parentheses as parameter names separated by commas; for example, `(depPar1, depPar2, depPar3)`.

INDEPENDENT

Set this parameter equal to the name of the design parameter with respect to which gradients are specified.

### **Data lines to define the design gradients: **

**First line:**

Repeat this data line as often as necessary to define the gradients of the dependent parameters consecutively with respect to the design parameter. Up to 16 entries are allowed per line.




