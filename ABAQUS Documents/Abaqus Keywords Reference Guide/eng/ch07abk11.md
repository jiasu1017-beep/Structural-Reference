# *GASKET SECTION







### *GASKET SECTIONSpecify element properties for gasket elements.

This option is used to define the properties of gasket elements.

**Products: **Abaqus/Standard  Abaqus/CAE  

**Type: **Model data  

**Level: **Part,  Part instance  

**Abaqus/CAE: **Property module

##### **References:**

- ["Gasket elements: overview," Section 32.6.1 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-elm-egasketoverview)
- ["Defining the gasket behavior using a material model," Section 32.6.5 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-elm-egasketmatbehavior)
- ["Defining the gasket behavior directly using a gasket behavior model," Section 32.6.6 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-elm-egasketbehavior)

### **Required parameter: **

ELSET

Set this parameter equal to the name of the element set containing the elements for which the gasket behavior is being defined.

### **Required, mutually exclusive parameters: **

BEHAVIOR

Set this parameter equal to the name of the gasket behavior to which the specified element set refers.

MATERIAL

Set this parameter equal to the name of the material of which the gasket is made.

### **Optional parameters: **

ORIENTATION

Set this parameter equal to the name given for the [*ORIENTATION](ch15abk01.md) option (["Orientations," Section 2.2.5 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-int-corientation)) to be used to define a local coordinate system for integration point calculations in the gasket elements in the specified element set.

STABILIZATION STIFFNESS

This parameter is usually not needed. It is used to change the default stabilization stiffness used in all but link elements to stabilize gasket elements that are not supported at all nodes, such as those that extend outside neighboring components. The default value is set equal to 109 times the initial compressive stiffness in the thickness direction. To change the default, set this parameter equal to the desired stabilization stiffness. The units are stress ([FL2](../popups/usb-int-iconventions-unitsym.md)). In case the thickness behavior is defined in terms of force versus closure, the initial compressive stiffness needs to be divided by the cross-sectional area to convert the units to stress before it can be used to set the desired stabilization stiffness.

### **Data line to define the attributes of gasket elements: **

**First (and only) line:**




