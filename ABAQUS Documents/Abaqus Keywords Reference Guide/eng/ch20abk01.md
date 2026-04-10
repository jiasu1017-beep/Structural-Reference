# *UEL PROPERTY







### *UEL PROPERTYDefine property values to be used with a user element type.

This option is used to define the properties of a user element.

**Products: **Abaqus/Standard  Abaqus/Explicit  Abaqus/CAE  

**Type: **Model data  

**Level: **Part,  Part instance,  Model  

**Abaqus/CAE: **Actuator/sensor interaction properties can be defined in the Interaction module.

##### **References:**

- ["User-defined elements," Section 32.15.1 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-elm-euserelem)
- [*USER ELEMENT](ch20abk07.md)

### **Required parameter: **

ELSET

Set this parameter equal to the name of the element set containing the user elements for which these property values are being defined.

### **Optional parameters: **

MATERIAL

This parameter applies only to Abaqus/Standard analyses.

Set this parameter equal to the name of the material to be used with these elements.

ORIENTATION

This parameter applies only to Abaqus/Standard analyses.

Set this parameter equal to the name of an orientation definition (["Orientations," Section 2.2.5 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-int-corientation)) to be used to define a local coordinate system for material calculations in the elements in this set.

### **Optional parameters (relevant only for direct-integration dynamic analysis with linear user elements): **

ALPHA

Set this parameter equal to the Rayleigh mass damping factor, ![](../graphics/key_eqn00080.gif).

BETA

Set this parameter equal to the Rayleigh stiffness damping factor, ![](../graphics/key_eqn00135.gif).

### **To define the properties of linear user elements: **

There are no data lines required.

### **Data lines to define the properties of nonlinear user elements if the PROPERTIES and/or I PROPERTIES parameters are used on the [*USER ELEMENT](ch20abk07.md) option with a value of one or more: **

**First line:**

Repeat this data line as often as necessary. Eight values per line are used for both real and integer values.




