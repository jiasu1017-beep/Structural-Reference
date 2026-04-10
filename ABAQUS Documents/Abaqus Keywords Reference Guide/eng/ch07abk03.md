# *GAP ELECTRICAL CONDUCTANCE







### *GAP ELECTRICAL CONDUCTANCESpecify electrical conductance between surfaces.

This option is used to introduce gap electrical conductance in a surface interaction model in a coupled thermal-electrical or a coupled thermal-electrical-structural simulation. It must be used in conjunction with the [*SURFACE INTERACTION](ch18abk50.md) option.

**Product: **Abaqus/Standard  

**Type: **Model data  

**Level: **Model  

##### **References:**

- ["Fully coupled thermal-stress analysis," Section 6.5.3 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-anl-acouptempdisp)
- ["Fully coupled thermal-electrical-structural analysis," Section 6.7.4 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-anl-acoupthermalelecstruct)
- ["Electrical contact properties," Section 37.3.1 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-cni-ajouleheatinteraction)
- [*SURFACE INTERACTION](ch18abk50.md)
- ["GAPELECTR," Section 1.1.11 of the Abaqus User Subroutines Reference Guide](../sub/sub-link.md#sub-rtn-ugapelectr)

### **Optional parameters: **

DEPENDENCIES

Set this parameter equal to the number of field variables on which ![](../graphics/key_eqn00759.gif) depends.

PRESSURE

Include this parameter to indicate that ![](../graphics/key_eqn00759.gif) is a function of the contact pressure between the surfaces, *p*. Omit this parameter to define ![](../graphics/key_eqn00759.gif) as a function of the clearance, *d*, between the surfaces.

USER

Include this parameter to define ![](../graphics/key_eqn00759.gif) in user subroutine [`GAPELECTR`](../sub/sub-link.md#sub-xsl-gapelectr). In this case the DEPENDENCIES parameter and any data lines are ignored.

### **Data lines to define the gap electrical conductance directly: **

**First line:**

Repeat this data line as often as necessary to define the dependence of gap electrical conductance on the surface separation, average surface temperature, and the average of any predefined field variables on the surfaces.




