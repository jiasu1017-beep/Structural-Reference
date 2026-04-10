# *PARAMETER







### *PARAMETERDefine parameters for input parametrization.

This option is used to define parameters that can be used in place of Abaqus input quantities.

**Products: **Abaqus/Standard  Abaqus/Explicit  

**Type: **Model data  

**Level: **Part,  Part instance,  Assembly,  Model,  Step

##### **References:**

- ["Parametric input," Section 1.4.1 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-int-iparinput)
- ["Parametric shape variation," Section 2.1.2 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-int-iparshapevar)

### **Optional keyword parameters to define tabularly dependent parameters (if any is specified, they must all be specified): **

DEPENDENT

Set this keyword parameter equal to the list of dependent parameters being defined in this option. The list must be given inside parentheses as parameter names separated by commas; for example, `(depPar1, depPar2, depPar3)`.

INDEPENDENT

Set this keyword parameter equal to the list of independent parameters used in this option. The list must be given inside parentheses as parameter names separated by commas; for example, `(indPar1, indPar2, indPar3)`.

TABLE

Set this keyword parameter equal to the name of the parameter dependence table, defined by the [*PARAMETER DEPENDENCE](ch16abk02.md) option, that defines the relationship between the dependent and independent parameters in this option.

### **Data lines to define independent or expressionally dependent parameters if the DEPENDENT, INDEPENDENT, and TABLE keyword parameters are omitted: **

**First line:**

Repeat this data line as often as necessary to define independent and expressionally dependent parameters. The data given on this data line cannot be parameterized.




