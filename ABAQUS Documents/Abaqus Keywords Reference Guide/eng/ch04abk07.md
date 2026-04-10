# *DAMPING CONTROLS







### *DAMPING CONTROLSSpecify damping controls.

This option is used to control the type (viscous, structural) and source of damping (material, global) within the step definition for the following types of analyses in Abaqus/Standard:
- [*STEADY STATE DYNAMICS](ch18abk34.md), DIRECT
- [*STEADY STATE DYNAMICS](ch18abk34.md), SUBSPACE PROJECTION
- [*STEADY STATE DYNAMICS](ch18abk34.md) that supports nondiagonal damping
- [*MODAL DYNAMIC](ch13abk18.md) that supports nondiagonal damping
- [*MATRIX GENERATE](ch13abk12.md)
- [*SUBSTRUCTURE GENERATE](ch18abk42.md)

Damping can be defined at the material level using [*DAMPING](ch04abk06.md); at the element level using [*SPRING](ch18abk29.md), COMPLEX STIFFNESS or [*CONNECTOR DAMPING](ch03abk39.md); for acoustic elements using [*ACOUSTIC MEDIUM](ch01abk02.md), VOLUMETRIC DRAG; or using the acoustic impedance definitions ([*IMPEDANCE](ch09abk01.md) and [*SIMPEDANCE](ch18abk17.md)). Damping is defined at the global level using [*GLOBAL DAMPING](ch07abk15.md). The [*DAMPING CONTROLS](ch04abk07.md) option controls which of the supplied damping options will participate in the current step or within a substructure.

The [*DAMPING CONTROLS](ch04abk07.md) option is also used to define the type and the source of substructure damping under the [*SUBSTRUCTURE PROPERTY](ch18abk46.md) option in all analysis procedures using substructures that take damping into account. The rules for using this option within a substructure property definition are the same as the rules for using it within a step definition (see ["Defining substructure damping" in "Using substructures," Section 10.1.1 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-anl-asuperelements-damping), for details).

**Products: **Abaqus/Standard  Abaqus/CAE  

**Type: **Model or history data  

**Level: **Part,  Part instance  

**Abaqus/CAE: **Supported in the Step module only for substructure generation.

##### **References:**

- ["Material damping," Section 26.1.1 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-mat-cdampingopt)
- ["Damping in dynamic analysis" in "Dynamic analysis procedures: overview," Section 6.3.1 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-anl-adynamicproc-damp)
- [*FREQUENCY](ch06abk35.md)

### **Optional parameters: **

STRUCTURAL

Set this parameter equal to ELEMENT to request the structural damping matrix that includes material and/or element damping properties only.

Set this parameter equal to FACTOR to request the structural damping matrix that includes the global damping factor only.

Set this parameter equal to COMBINED to request the structural damping matrix that includes the combination of both ELEMENT and FACTOR.

Set this parameter equal to NONE to exclude the structural damping matrix at this step.

If this parameter is omitted or the option is not used within the step definition, the default uses all structural damping specified at the model and step levels. If both material and global structural damping are specified, the COMBINED damping is used.

If this parameter is omitted or the option is not used as a suboption of [*SUBSTRUCTURE PROPERTY](ch18abk46.md), the substructure property uses COMBINED as the default with the structural factor specified under the [*DAMPING](ch04abk06.md), STRUCTURAL option. 

VISCOUS

Set this parameter equal to ELEMENT to request a viscous damping matrix that includes material and/or element damping properties only.

Set this parameter equal to FACTOR to request a viscous damping matrix that includes the global damping factor only.

Set this parameter equal to COMBINED to request a viscous damping matrix that includes a combination of ELEMENT and FACTOR.

Set this parameter equal to NONE to exclude the viscous damping matrix in this step.

If this parameter is omitted or the option is not used within the step definition, the default uses all viscous damping specified at the model and step levels. If both material and global damping are specified, the COMBINED damping is used.

 If this parameter is omitted or the option is not used as a suboption of [*SUBSTRUCTURE PROPERTY](ch18abk46.md), the substructure property uses COMBINED as the default with the mass and stiffness proportional Rayleigh damping factors specified under the [*DAMPING](ch04abk06.md), ALPHA or BETA option.

**There are no data lines associated with this option.**



