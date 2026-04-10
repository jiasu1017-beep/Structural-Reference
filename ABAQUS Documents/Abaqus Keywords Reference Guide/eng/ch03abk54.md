# *CONTACT







### *CONTACTBegin the definition of general contact.

This option is used to indicate the start of a general contact definition. The various aspects of a general contact definition are specified by using other options in conjunction with the [*CONTACT](ch03abk54.md) option.

**Products: **Abaqus/Standard  Abaqus/Explicit  Abaqus/CAE  

**Type: **Model or history data  

**Level: **Model,  Step

**Abaqus/CAE: **Interaction module

##### **References:**

- ["Defining general contact interactions in Abaqus/Standard," Section 36.2.1 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-cni-acontactgeneralstd)
- ["Defining general contact interactions in Abaqus/Explicit," Section 36.4.1 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-cni-acontactgeneral)

### **Optional parameter: **

OP

This parameter applies only to Abaqus/Explicit.

Set OP=MOD (default) to modify an existing general contact definition relative to the previous step.

Set OP=NEW to delete any previously specified general contact definition and specify a new one. OP=NEW is ignored when the general contact definition is specified as model data.

**There are no data lines associated with this option.**



