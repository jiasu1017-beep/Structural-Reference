# *GASKET CONTACT AREA







### *GASKET CONTACT AREASpecify a gasket contact area or contact width for average pressure output.

This option is used to define contact area or contact width versus closure curves to output an average pressure through variable CS11. It can be used only with gasket link and three-dimensional line gasket elements that have their thickness-direction behavior defined in terms of force or force per unit length.

**Products: **Abaqus/Standard  Abaqus/CAE  

**Type: **Model data  

**Level: **Model  

**Abaqus/CAE: **Property module

##### **Reference:**

- ["Defining the gasket behavior directly using a gasket behavior model," Section 32.6.6 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-elm-egasketbehavior)

### **Optional parameter: **

DEPENDENCIES

Set this parameter equal to the number of field variable dependencies included in the definition of the data, in addition to temperature. If this parameter is omitted, it is assumed that the data depend only on temperature. See ["Specifying field variable dependence" in "Material data definition," Section 21.1.2 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-mat-cmaterialdata-fvdepen), for more information.

### **Data lines to define a contact area for average pressure output: **

**First line:**

**Subsequent lines (only needed if the DEPENDENCIES parameter has a value greater than five):**

Repeat this set of data lines as often as necessary to define the dependence of the contact area or width versus closure curves on temperature and field variables.




