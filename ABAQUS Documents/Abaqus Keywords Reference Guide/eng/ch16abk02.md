# *PARAMETER DEPENDENCE







### *PARAMETER DEPENDENCEDefine dependence table for tabularly dependent parameters.

This option is used to define the dependence table that specifies the relationship between tabularly dependent and independent parameters.

**Products: **Abaqus/Standard  Abaqus/Explicit  

**Type: **Model data  

**Level: **Part,  Part instance,  Assembly,  Model,  Step

##### **References:**

- ["Parametric input," Section 1.4.1 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-int-iparinput)
- ["Parametric shape variation," Section 2.1.2 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-int-iparshapevar)

### **Required parameters: **

NUMBER VALUES

Set this keyword parameter equal to the number of values in each line of the parameter dependence table. This number must be equal to the sum of the number of dependent and the number of independent parameters for which this table is used.

TABLE

Set this keyword parameter equal to the name of the table being defined in this option.

### **Data lines to define the parameter dependence table: **

**First line:**

Repeat this data line as often as necessary to define additional rows of the parameter dependence table. The data given on this data line cannot be parameterized.




