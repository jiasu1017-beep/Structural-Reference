# *GASKET THICKNESS BEHAVIOR







### *GASKET THICKNESS BEHAVIORSpecify a gasket thickness-direction behavior.

This option is used to define the behavior in the thickness direction for a gasket.

**Products: **Abaqus/Standard  Abaqus/CAE  

**Type: **Model data  

**Level: **Model  

**Abaqus/CAE: **Property module

##### **Reference:**

- ["Defining the gasket behavior directly using a gasket behavior model," Section 32.6.6 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-elm-egasketbehavior)

### **Optional parameters: **

DEPENDENCIES

Set this parameter equal to the number of field variable dependencies included in the definition of the data, in addition to temperature. If this parameter is omitted, it is assumed that the data depend only on temperature. See ["Specifying field variable dependence" in "Material data definition," Section 21.1.2 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-mat-cmaterialdata-fvdepen), for more information.

DIRECTION

Set DIRECTION=LOADING (default) to prescribe the loading curve of the model used to define the gasket thickness-direction behavior.

Set DIRECTION=UNLOADING to prescribe the unloading curves of the model used to define the gasket thickness-direction behavior.

TENSILE STIFFNESS FACTOR

Set this parameter equal to the fraction of the initial compressive stiffness that defines the stiffness in tension. The default value is 103. This parameter can be used only with DIRECTION=LOADING.

TYPE

Set TYPE=DAMAGE to define a damage elasticity model for the gasket thickness-direction behavior.

Set TYPE=ELASTIC-PLASTIC (default) to define an elastic-plastic model for the gasket thickness-direction behavior.

VARIABLE

Set VARIABLE=FORCE to define the behavior in terms of force versus closure or force per unit length versus closure, depending on the element type with which this behavior is being used.

Set VARIABLE=STRESS (default) to define the behavior in terms of pressure versus closure.

### **The following parameters are optional, mutually exclusive, and can be used only with DIRECTION=LOADING: **

SLOPE DROP

Set this parameter equal to the relative drop in slope on the loading curve that defines the onset of plastic deformation. The default value is 0.1. 

YIELD ONSET

Set this parameter equal to the closure value at which the onset of yield occurs. The specified value must correspond to a point on the loading curve at which the slope decreases.

### **Data lines to define the loading in terms of pressure versus closure (DIRECTION=LOADING and VARIABLE=STRESS): **

**First line:**

**Subsequent lines (only needed if the DEPENDENCIES parameter has a value greater than five):**

Repeat this set of data lines as often as necessary to define the dependence of the loading curve on temperature and field variables.

### **Data lines to define the loading in terms of force or force per unit length per closure (DIRECTION=LOADING and VARIABLE=FORCE): **

**First line:**

**Subsequent lines (only needed if the DEPENDENCIES parameter has a value greater than five):**

Repeat this set of data lines as often as necessary to define the dependence of the loading curve on temperature and field variables.

### **Data lines to define the unloading in terms of pressure versus closure for an elastic-plastic model (TYPE=ELASTIC-PLASTIC, DIRECTION=UNLOADING, and VARIABLE=STRESS): **

**First line:**

**Subsequent lines (only needed if the DEPENDENCIES parameter has a value greater than four):**

Repeat this set of data lines as often as necessary to define the dependence of the unloading curve of the elastic-plastic model on temperature and field variables.

### **Data lines to define the unloading in terms of force or force per unit length versus closure for an elastic-plastic model (TYPE=ELASTIC-PLASTIC, DIRECTION=UNLOADING, and VARIABLE=FORCE): **

**First line:**

**Subsequent lines (only needed if the DEPENDENCIES parameter has a value greater than four):**

Repeat this set of data lines as often as necessary to define the dependence of the unloading curve of the elastic-plastic model on temperature and field variables.

### **Data lines to define the unloading in terms of pressure versus closure for a damage model (TYPE=DAMAGE, DIRECTION=UNLOADING, and VARIABLE=STRESS): **

**First line:**

**Subsequent lines (only needed if the DEPENDENCIES parameter has a value greater than four):**

Repeat this set of data lines as often as necessary to define the dependence of the unloading curve of the damage model on temperature and field variables.

### **Data lines to define the unloading in terms of force or force per unit length versus closure for a damage model (TYPE=DAMAGE, DIRECTION=UNLOADING, and VARIABLE=FORCE): **

**First line:**

**Subsequent lines (only needed if the DEPENDENCIES parameter has a value greater than four):**

Repeat this set of data lines as often as necessary to define the dependence of the unloading curve of the damage model on temperature and field variables.




