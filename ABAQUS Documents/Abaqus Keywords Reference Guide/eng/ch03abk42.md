# *CONNECTOR FAILURE







### *CONNECTOR FAILUREDefine a failure criterion for connector elements.

This option is used to define a failure criterion for connector elements. 

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

Set this parameter equal to the connector's component number for which a failure criterion is defined in Abaqus/Standard; only an available component of relative motion can be chosen. In Abaqus/Explicit any connector component number can be specified. See ["Connection-type library," Section 31.1.5 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-elm-econnectortypelibrary), for connector components of relative motion definitions.

### **Optional parameter: **

RELEASE

In Abaqus/Standard set this parameter equal to ALL (default) to release all available components of relative motion when the failure criterion is satisfied. In Abaqus/Explicit set this parameter equal to ALL (default) to release all components (available or constrained) when the failure criterion is satisfied.

In Abaqus/Standard set this parameter equal to an available component of relative motion number to release only that component when the failure criterion is satisfied. In Abaqus/Explicit set this parameter equal to a component number to release only that component when the failure criterion is satisfied.

### **Data line to define the failure criterion: **

**First (and only) line:**




