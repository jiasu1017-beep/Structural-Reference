# *CONNECTOR BEHAVIOR







### *CONNECTOR BEHAVIORBegin the specification of a connector behavior.

This option is used to indicate the start of a connector behavior definition.

**Products: **Abaqus/Standard  Abaqus/Explicit  Abaqus/CAE  

**Type: **Model data  

**Level: **Model  

**Abaqus/CAE: **Interaction module

##### **References:**

- ["Connector behavior," Section 31.2.1 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-elm-econnectorbehavior)
- [*CONNECTOR SECTION](ch03abk50.md)

### **Required parameter: **

NAME

Set this parameter equal to the behavior name referred to on the [*CONNECTOR SECTION](ch03abk50.md) option. Connector behavior names in the same input file must be unique.

### **Optional parameters: **

EXTRAPOLATION

The choice of extrapolation defined here applies to all suboptions of the connector behavior unless it is redefined on the suboption.

Set EXTRAPOLATION=CONSTANT (default) to use constant extrapolation of the dependent variables outside the specified range of the independent variables.

Set EXTRAPOLATION=LINEAR to use linear extrapolation of the dependent variables outside the specified range of the independent variables.

INTEGRATION

This parameter applies only to Abaqus/Explicit analyses.

Set INTEGRATION=IMPLICIT (default) to integrate the connector behavior with implicit time integration.

Set INTEGRATION=EXPLICIT to integrate the connector behavior with explicit time integration.

REGULARIZE

This parameter applies only to Abaqus/Explicit analyses. The choice of regularization defined here applies to all suboptions of the connector behavior unless it is redefined on the suboption.

Set REGULARIZE=ON (default) to regularize the user-defined tabular connector behavior data. 

Set REGULARIZE=OFF to use the user-defined tabular connector behavior data directly without regularization. 

RTOL

This parameter applies only to Abaqus/Explicit analyses. The regularization tolerance defined here applies to all suboptions of the connector behavior unless it is redefined on the suboption.

Set this parameter equal to the tolerance to be used to regularize the connector behavior data. The default is RTOL=0.03.

**There are no data lines associated with this option.**



