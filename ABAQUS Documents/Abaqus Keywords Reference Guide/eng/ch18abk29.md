# *SPRING







### *SPRINGDefine spring behavior.

This option is used to define the spring behavior for spring elements. It is also used to assign a structural damping factor to form the imaginary part of the spring stiffness matrix. The imaginary stiffness represents an element-level damping contribution to the frequency domain dynamic equations and to the time domain mode-based dynamic analyses that support nondiagonal damping (see ["Modal dynamic analysis," Section 2.5.5 of the Abaqus Theory Guide](../stm/stm-link.md#stm-anl-modaldynamic)).

In Abaqus/Standard analyses it is also used to define the spring behavior for ITS and JOINTC elements. If the [*SPRING](ch18abk29.md) option is being used to define part of the behavior of ITS or JOINTC elements, it must be used in conjunction with the [*ITS](ch09abk23.md) or [*JOINT](ch10abk01.md) options and the ELSET and ORIENTATION parameters should not be used.

**Products: **Abaqus/Standard  Abaqus/Explicit  Abaqus/CAE  

**Type: **Model data  

**Level: **Part,  Part instance,  Assembly  

**Abaqus/CAE: **Property module and Interaction module; supported only for linear behavior independent of field variables. For nonlinear behavior or to include field variables, model connectors in the Interaction module.

##### **References:**

- ["Springs," Section 32.1.1 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-elm-espring)
- ["Flexible joint element," Section 32.3.1 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-elm-ejoint)
- ["Tube support elements," Section 32.8.1 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-elm-eitselem)

### **Required parameter if the behavior of spring elements is being defined: **

ELSET

Set this parameter equal to the name of the element set containing the spring elements for which this behavior is being defined.

### **Optional parameters: **

COMPLEX STIFFNESS

This parameter is relevant in direct-solution and subspace-based steady-state analyses and in mode-based analyses with [*FREQUENCY](ch06abk35.md), DAMPING PROJECTION=ON in Abaqus/Standard that support nondiagonal damping.

Include this parameter to define both the real and imaginary parts of the stiffness. The imaginary part represents structural damping.

If this parameter is omitted, the default is real stiffness only.

DEPENDENCIES

Set this parameter equal to the number of field variable dependencies included in the definition of the real spring stiffness data, in addition to temperature. If this parameter is omitted, it is assumed that the spring stiffness is independent of field variables. See “Using the DEPENDENCIES parameters to define field variable dependence” in ["Material data definition," Section 21.1.2 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-mat-cmaterialdata), for more information.

NONLINEAR

Include this parameter to define nonlinear spring behavior. Omit this parameter to define linear spring behavior.

ORIENTATION

This parameter applies only to Abaqus/Standard analyses.

If the option is being used to define the behavior of SPRING1 or SPRING2 elements, this parameter can be used to refer to an orientation definition so that the spring is acting in a local system. Set this parameter equal to the name of the [*ORIENTATION](ch15abk01.md) definition (["Orientations," Section 2.2.5 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-int-corientation)).

RTOL

This parameter applies only to Abaqus/Explicit analyses.

Set this parameter equal to the tolerance to be used for regularizing the material data. The default is RTOL=0.03. See ["Material data definition," Section 21.1.2 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-mat-cmaterialdata), for a discussion of data regularization.

### **Data lines to define linear spring behavior for SPRINGA or ITS elements: **

**First line:**

**Second line:**

**Subsequent lines (only needed if the DEPENDENCIES parameter has a value greater than five):**

Repeat this set of data lines as often as necessary to define the spring stiffness as a function of frequency, temperature, and other predefined field variables.

### **Data lines to define nonlinear spring behavior for SPRINGA or ITS elements: **

**First line:**

**Second line:**

**Subsequent lines (only needed if the DEPENDENCIES parameter has a value greater than five):**

Repeat this set of data lines as often as necessary to define the spring stiffness as a function of temperature and other predefined field variables.

### **Data lines to define linear spring behavior for SPRING1, SPRING2, or JOINTC elements: **

**First line:**

If the ORIENTATION parameter is included on the [*SPRING](ch18abk29.md) option when defining spring elements or on the [*JOINT](ch10abk01.md) option when defining joint elements, the degrees of freedom specified here are in the local system defined by the [*ORIENTATION](ch15abk01.md) option referenced.

**Second line:**

**Subsequent lines (only needed if the DEPENDENCIES parameter has a value greater than five):**

Repeat this set of data lines as often as necessary to define the spring stiffness as a function of frequency, temperature, and other predefined field variables.

### **Data lines to define nonlinear spring behavior for SPRING1, SPRING2, or JOINTC elements: **

**First line:**

If the ORIENTATION parameter is included on the [*SPRING](ch18abk29.md) option when defining spring elements or on the [*JOINT](ch10abk01.md) option when defining joint elements, the degrees of freedom specified here are in the local system defined by the [*ORIENTATION](ch15abk01.md) option referenced.

**Second line:**

**Subsequent lines (only needed if the DEPENDENCIES parameter has a value greater than five):**

Repeat this set of data lines as often as necessary to define the spring stiffness as a function of temperature and other predefined field variables.

### **Data lines to define linear spring behavior for SPRINGA elements with COMPLEX STIFFNESS: **

**First line:**

**Second line:**

Repeat this set of data lines as often as necessary to define the spring stiffness and structural damping factor as a function of frequency.

### **Data lines to define linear spring behavior for SPRING1 and SPRING2 elements with COMPLEX STIFFNESS: **

**First line:**

If the ORIENTATION parameter is included on the [*SPRING](ch18abk29.md) option when defining spring elements, the degrees of freedom specified here are in the local system defined by the [*ORIENTATION](ch15abk01.md) option referenced.

**Second line:**

Repeat this set of data lines as often as necessary to define the spring stiffness and the structural damping factor as a function of frequency.




