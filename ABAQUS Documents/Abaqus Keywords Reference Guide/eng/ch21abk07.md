# *VOID NUCLEATION







### *VOID NUCLEATIONDefine the nucleation of voids in a porous material.

This option is used to model the nucleation of voids in a porous material. It can be used only with the [*POROUS METAL PLASTICITY](ch16abk22.md) option.

**Products: **Abaqus/Standard  Abaqus/Explicit  Abaqus/CAE  

**Type: **Model data  

**Level: **Model  

**Abaqus/CAE: **Property module

##### **References:**

- ["Porous metal plasticity," Section 23.2.9 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-mat-cpormetalplas)
- [*POROUS METAL PLASTICITY](ch16abk22.md)

### **Optional parameter: **

DEPENDENCIES

Set this parameter equal to the number of field variable dependencies, in addition to temperature, that define the normal distribution of the nucleation strain. If this parameter is omitted, the constants defining the normal distribution may depend only on temperature. See ["Specifying field variable dependence" in "Material data definition," Section 21.1.2 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-mat-cmaterialdata-fvdepen), for more information.

### **Data lines to define void nucleation: **

**First line:**

**Subsequent lines (only needed if the DEPENDENCIES parameter has a value greater than four):**

Repeat this set of data lines as often as necessary to define the dependence of ![](../graphics/key_eqn01182.gif), ![](../graphics/key_eqn01183.gif), and ![](../graphics/key_eqn01184.gif) on temperature and other predefined field variables.




