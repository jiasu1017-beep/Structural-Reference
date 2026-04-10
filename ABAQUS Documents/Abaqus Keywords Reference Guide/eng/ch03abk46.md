# *CONNECTOR LOCK







### *CONNECTOR LOCKDefine a locking criterion for connector elements.

This option is used to define a locking criterion for connector elements that have available components of relative motion.

**Products: **Abaqus/Standard  Abaqus/Explicit  Abaqus/CAE  

**Type: **Model data  

**Level: **Model  

**Abaqus/CAE: **Interaction module

##### **References:**

- ["Connector behavior," Section 31.2.1 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-elm-econnectorbehavior)
- ["Connection-type library," Section 31.1.5 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-elm-econnectortypelibrary)
- [*CONNECTOR BEHAVIOR](ch03abk35.md)

### **Required parameter: **

COMPONENT

Set this parameter equal to the component number on which a locking criterion is based. See ["Connection-type library," Section 31.1.5 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-elm-econnectortypelibrary), for components of relative motion definitions.

### **Optional parameters: **

DEPENDENCIES

This parameter applies only to Abaqus/Explicit analyses.

Set this parameter equal to the number of field variable dependencies included in the definition of the connector lock data, in addition to temperature. If this parameter is omitted, it is assumed that the connector lock is independent of field variables. See ["Specifying field variable dependence" in "Material data definition," Section 21.1.2 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-mat-cmaterialdata-fvdepen), for more information.

EXTRAPOLATION

Set EXTRAPOLATION=CONSTANT (default unless [*CONNECTOR BEHAVIOR](ch03abk35.md), EXTRAPOLATION=LINEAR is used) to use constant extrapolation of the dependent variables outside the specified range of the independent variables.

Set EXTRAPOLATION=LINEAR to use linear extrapolation of the dependent variables outside the specified range of the independent variables.

LOCK

Set this parameter equal to ALL (default) to lock all components of relative motion when the locking criterion is satisfied.

Set this parameter equal to an available component number to lock only that component of relative motion when the locking criterion is satisfied.

REGULARIZE

This parameter applies only to Abaqus/Explicit analyses.

Set REGULARIZE=ON (default unless [*CONNECTOR BEHAVIOR](ch03abk35.md), REGULARIZE=OFF is used) to regularize the user-defined tabular connector lock data. 

Set REGULARIZE=OFF to use the user-defined tabular connector lock data directly without regularization. 

RTOL

This parameter applies only to Abaqus/Explicit analyses.

Set this parameter equal to the tolerance to be used to regularize the connector lock data.

If this parameter is omitted, the default is RTOL=0.03 unless the tolerance is specified on the [*CONNECTOR BEHAVIOR](ch03abk35.md) option.

### **Data line to define the locking criterion: **

**First (and only) line for Abaqus/Standard:**

**Data lines for Abaqus/Explicit:**

**Subsequent lines (only needed if the DEPENDENCIES parameter has a value greater than one):**

Repeat this set of data lines as often as necessary to define the lock criterion as a function of temperature, and other predefined field variables.




