# *DASHPOT







### *DASHPOTDefine dashpot behavior.

This option is used to define the dashpot behavior for dashpot elements.

In Abaqus/Standard analyses it is also used to define the dashpot behavior for ITS and JOINTC elements. If the [*DASHPOT](ch04abk08.md) option is being used to define part of the behavior of ITS or JOINTC elements, it must be used in conjunction with the [*ITS](ch09abk23.md) or [*JOINT](ch10abk01.md) options and the ELSET and ORIENTATION parameters should not be used. 

**Products: **Abaqus/Standard  Abaqus/Explicit  Abaqus/CAE  

**Type: **Model data  

**Level: **Part,  Part instance,  Assembly  

**Abaqus/CAE: **Property module and Interaction module; supported only for linear behavior independent of field variables. For nonlinear behavior or to include field variables, model connectors in the Interaction module.

##### **References:**

- ["Dashpots," Section 32.2.1 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-elm-edashpot)
- ["Flexible joint element," Section 32.3.1 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-elm-ejoint)
- ["Tube support elements," Section 32.8.1 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-elm-eitselem)

### **Required parameter if the behavior of dashpot elements is being defined: **

ELSET

Set this parameter equal to the name of the element set containing the dashpot elements for which this behavior is being defined.

### **Optional parameters: **

DEPENDENCIES

Set this parameter equal to the number of field variable dependencies included in the definition of the dashpot coefficient, in addition to temperature. If this parameter is omitted, it is assumed that the dashpot coefficient is independent of field variables. See ["Specifying field variable dependence" in "Material data definition," Section 21.1.2 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-mat-cmaterialdata-fvdepen), for more information.

NONLINEAR

Include this parameter to define nonlinear dashpot behavior. Omit this parameter to define linear dashpot behavior.

ORIENTATION

This parameter applies only to Abaqus/Standard analyses.

If the option is being used to define the behavior of DASHPOT1 or DASHPOT2 elements, this parameter can be used to refer to an orientation definition so that the dashpot is acting in a local system. Set this parameter equal to the name of the [*ORIENTATION](ch15abk01.md) definition (["Orientations," Section 2.2.5 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-int-corientation)).

RTOL

This parameter applies only to Abaqus/Explicit analyses.

Set this parameter equal to the tolerance to be used for regularizing the material data. The default is RTOL=0.03. See ["Material data definition," Section 21.1.2 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-mat-cmaterialdata), for a discussion of data regularization.

### **Data lines to define linear dashpot behavior for DASHPOTA or ITS elements: **

**First line:**

**Second line:**

**Subsequent lines (only needed if the DEPENDENCIES parameter has a value greater than five):**

Repeat this set of data lines as often as necessary to define the dashpot coefficient as a function of frequency, temperature, and other predefined field variables.

### **Data lines to define nonlinear dashpot behavior for DASHPOTA or ITS elements: **

**First line:**

**Second line:**

**Subsequent lines (only needed if the DEPENDENCIES parameter has a value greater than five):**

Repeat this set of data lines as often as necessary to define the dashpot coefficient as a function of temperature and other predefined field variables.

### **Data lines to define linear dashpot behavior for DASHPOT1, DASHPOT2, or JOINTC elements: **

**First line:**

If the ORIENTATION parameter is included on the [*DASHPOT](ch04abk08.md) option when defining dashpot elements or on the [*JOINT](ch10abk01.md) option when defining joint elements, the degrees of freedom specified here are in the local system defined by the [*ORIENTATION](ch15abk01.md) option referenced.

**Second line:**

**Subsequent lines (only needed if the DEPENDENCIES parameter has a value greater than five):**

Repeat this set of data lines as often as necessary to define the dashpot coefficient as a function of frequency, temperature, and other predefined field variables.

### **Data lines to define nonlinear dashpot behavior for DASHPOT1, DASHPOT2, or JOINTC elements: **

**First line:**

If the ORIENTATION parameter is included on the [*DASHPOT](ch04abk08.md) option when defining dashpot elements or on the [*JOINT](ch10abk01.md) option when defining joint elements, the degrees of freedom specified here are in the local system defined by the [*ORIENTATION](ch15abk01.md) option referenced.

**Second line:**

**Subsequent lines (only needed if the DEPENDENCIES parameter has a value greater than five):**

Repeat this set of data lines as often as necessary to define the dashpot coefficient as a function of temperature and other predefined field variables.




