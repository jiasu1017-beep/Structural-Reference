# 6.7 Element deletion controlled by state variables







**Products: **Abaqus/Standard  

**Benefits: **In Abaqus/Standard deletion of solid, shell, membrane, and beam elements can now be controlled using state variables. Deleted elements have no ability to carry stresses and do not contribute to the stiffness of the model. They also do not undergo element quality checks, so an analysis cannot be terminated due to excessive distortion of such elements.

**Description: **Deletion of elements can now be controlled by state variables in Abaqus/Standard, similar to the functionality previously available in Abaqus/Explicit. The number of the state variable that controls deletion must be specified, and it can be different for each material. The state variable stores the element deletion flag, which can have a value of zero or one. A value of one indicates that the material point is active, while a value of zero indicates that the material point is inactive and the stresses at this point are set to zero. Once a material point is deleted, it cannot be reactivated. The deletion flag can be modified by any of the Abaqus/Standard user subroutines that use state variables and that are called at the material point. If all the material points of an element become inactive, the element is deleted. The status of an element can be monitored by requesting the output variable STATUS.
**References: **

**Abaqus Analysis User's Guide**
- ["User subroutines: overview," Section 18.1.1](../usb/usb-link.md#usb-anl-asubroutineover)
- ["User-defined mechanical material behavior," Section 26.7.1](../usb/usb-link.md#usb-mat-cusermat)

**Abaqus Keywords Reference Guide**
- [*DEPVAR](../key/key-link.md#usb-kws-mdepvar)




