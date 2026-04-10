# *CONNECTOR PLASTICITY







### *CONNECTOR PLASTICITYDefine plasticity behavior in connector elements.

This option is used to define plasticity behavior in connector elements. It must be used in conjunction with the [*CONNECTOR HARDENING](ch03abk44.md) option.

**Products: **Abaqus/Standard  Abaqus/Explicit  Abaqus/CAE  

**Type: **Model data  

**Level: **Model  

**Abaqus/CAE: **Interaction module

##### **References:**

- ["Connector behavior," Section 31.2.1 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-elm-econnectorbehavior)
- ["Connector plastic behavior," Section 31.2.6 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-elm-econnplastbehav)
- [*CONNECTOR BEHAVIOR](ch03abk35.md)
- [*CONNECTOR HARDENING](ch03abk44.md)
- [*CONNECTOR POTENTIAL](ch03abk49.md)

### **Optional parameter: **

COMPONENT

Set this parameter equal to the connector's component of relative motion for which plasticity behavior is specified.

If this parameter is omitted, the [*CONNECTOR POTENTIAL](ch03abk49.md) option must be used in conjunction with the [*CONNECTOR PLASTICITY](ch03abk48.md) option to specify coupled plasticity behavior.

### **There are no data lines associated with this option. **




