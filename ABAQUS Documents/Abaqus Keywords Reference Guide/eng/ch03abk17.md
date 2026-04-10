# *CHANGE FRICTION







### *CHANGE FRICTIONChange friction properties.

Use this option in conjunction with the [*FRICTION](ch06abk36.md) option to change the values of friction properties from step to step.

**Products: **Abaqus/Standard  Abaqus/CAE  

**Type: **History data 

**Level: **Step

**Abaqus/CAE: **Interaction module

##### **References:**

- ["Mechanical contact properties: overview," Section 37.1.1 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-cni-acontactmechanical)
- ["Frictional behavior," Section 37.1.5 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-cni-afriction)
- ["Connector behavior," Section 31.2.1 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-elm-econnectorbehavior)
- [*FRICTION](ch06abk36.md)

### **Required, mutually exclusive parameters: **

ELSET

Use this parameter if the contact conditions have been modeled with contact elements or if friction is defined in connector elements. Set this parameter equal to the name of the element set containing the contact or connector elements for which the friction properties are being redefined.

INTERACTION

Use this parameter if the contact conditions have been modeled with surface-based contact pairs or general contact. Set this parameter equal to the name of the [*SURFACE INTERACTION](ch18abk50.md) property definition for which the friction properties are being redefined.

### **Optional parameters: **

AMPLITUDE

Set this parameter equal to the name of the amplitude curve (defined in the [*AMPLITUDE](ch01abk09.md) option) that gives the time variation of any changes in friction coefficients and allowable elastic slip throughout the step (["Amplitude curves," Section 34.1.2 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-prc-pamplitude)).

If this parameter is omitted, transitions in these friction properties occur according to the value assigned to the AMPLITUDE parameter on the [*STEP](ch18abk36.md) option (see ["Defining an analysis," Section 6.1.2 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-anl-aover)). Changes in friction properties other than the friction coefficient and the allowable elastic slip are always made immediately. Sudden changes in friction properties when the frictional stress is nonzero can cause convergence difficulties.

RESET

Include this parameter to reset the friction properties to their original values. When this parameter is used, no [*FRICTION](ch06abk36.md) option is needed to redefine the friction properties.

**There are no data lines associated with this option.**



