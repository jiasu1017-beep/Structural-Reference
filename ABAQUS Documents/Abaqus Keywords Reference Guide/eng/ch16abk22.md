# *POROUS METAL PLASTICITY







### *POROUS METAL PLASTICITYSpecify a porous metal plasticity model.

This option is used to specify the porous part of the porous metal plasticity model.

The [*POROUS METAL PLASTICITY](ch16abk22.md) option can be used in conjunction with the [*VOID NUCLEATION](ch21abk07.md) option to define the nucleation of voids. In an Abaqus/Explicit analysis it can also be used in conjunction with the [*POROUS FAILURE CRITERIA](ch16abk21.md) option to specify the material failure criteria.

**Products: **Abaqus/Standard  Abaqus/Explicit  Abaqus/CAE  

**Type: **Model data  

**Level: **Model  

**Abaqus/CAE: **Property module

##### **References:**

- ["Porous metal plasticity," Section 23.2.9 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-mat-cpormetalplas)
- [*VOID NUCLEATION](ch21abk07.md)
- [*POROUS FAILURE CRITERIA](ch16abk21.md)

### **Optional parameters: **

DEPENDENCIES

Set this parameter equal to the number of field variable dependencies, in addition to temperature, included in the definition of the ![](../graphics/key_eqn01005.gif), ![](../graphics/key_eqn01006.gif), and ![](../graphics/key_eqn01007.gif) parameters. If this parameter is omitted, ![](../graphics/key_eqn01005.gif), ![](../graphics/key_eqn01006.gif), and ![](../graphics/key_eqn01007.gif) may depend only on temperature. See ["Specifying field variable dependence" in "Material data definition," Section 21.1.2 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-mat-cmaterialdata-fvdepen), for more information.

RELATIVE DENSITY

Set this parameter equal to ![](../graphics/key_eqn01008.gif), the initial relative density of the material. If this parameter is omitted, the initial relative density is interpolated from the values given in the [*INITIAL CONDITIONS](ch09abk18.md), TYPE=RELATIVE DENSITY option.

### **Data lines to define porous metal plasticity: **

**First line:**

**Subsequent lines (only needed if the DEPENDENCIES parameter has a value greater than four):**

Repeat this set of data lines as often as necessary to define the dependence of ![](../graphics/key_eqn01005.gif), ![](../graphics/key_eqn01006.gif), and ![](../graphics/key_eqn01007.gif) on temperature and other predefined field variables.




