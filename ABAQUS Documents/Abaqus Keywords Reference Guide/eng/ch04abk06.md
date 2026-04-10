# *DAMPING







### *DAMPINGSpecify material damping.

**Warning:**The use of stiffness proportional material damping in Abaqus/Explicit may reduce the stable time increment dramatically and can lead to longer analysis times. See ["Material damping," Section 26.1.1 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-mat-cdampingopt).

This option is used to provide material damping for mode-based analyses and for direct-integration dynamic analysis in Abaqus/Standard and for explicit dynamic analysis in Abaqus/Explicit.

Damping is defined in a material data block except in the case of elements defined with the [*BEAM GENERAL SECTION](ch02abk05.md) option,  the [*SHELL GENERAL SECTION](ch18abk14.md) option, the [*ROTARY INERTIA](ch17abk20.md) option, the [*MASS](ch13abk04.md) option, or the [*SUBSTRUCTURE PROPERTY](ch18abk46.md) option. For the [*BEAM GENERAL SECTION](ch02abk05.md), the [*SHELL GENERAL SECTION](ch18abk14.md), and the [*SUBSTRUCTURE PROPERTY](ch18abk46.md) options the [*DAMPING](ch04abk06.md) option must be used in conjunction with the property references. For the [*MASS](ch13abk04.md) and the [*ROTARY INERTIA](ch17abk20.md) options damping must be specified using either the ALPHA or the COMPOSITE parameter associated with these options. Damping may also be defined as step data using the [*GLOBAL DAMPING](ch07abk15.md) option and may come from damper elements like connectors and dashpots.

**Products: **Abaqus/Standard  Abaqus/Explicit  Abaqus/CAE  

**Type: **Model data  

**Level: **Part,  Part instance  

**Abaqus/CAE: **Property module

##### **References:**

- ["Material damping," Section 26.1.1 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-mat-cdampingopt)
- ["Dynamic analysis procedures: overview," Section 6.3.1 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-anl-adynamicproc)
- ["Explicit dynamic analysis," Section 6.3.3 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-anl-aexpdynamic)

### **Optional parameters: **

ALPHA

Set this parameter equal to the ![](../graphics/key_eqn00077.gif) factor to create Rayleigh mass proportional damping in the following procedures: 
- [*DYNAMIC](ch04abk43.md) (Abaqus/Standard or Abaqus/Explicit)
- [*COMPLEX FREQUENCY](ch03abk26.md)
- [*STEADY STATE DYNAMICS](ch18abk34.md), DIRECT
- [*STEADY STATE DYNAMICS](ch18abk34.md), SUBSPACE PROJECTION
- [*STEADY STATE DYNAMICS](ch18abk34.md) that allows nondiagonal damping
- [*MODAL DYNAMIC](ch13abk18.md) that allows nondiagonal damping

This parameter is ignored in mode-based procedures that use Lanczos or subspace iteration eigenvalue extraction that is not based on the SIM architecture. The default is ALPHA=0. (Units of [T1](../popups/usb-int-iconventions-unitsym.md).) 

In Abaqus/Explicit set ALPHA=TABULAR to specify that the mass proportional damping is dependent on temperature and/or field variables.

BETA

Set this parameter equal to the ![](../graphics/key_eqn00577.gif) factor to create Rayleigh stiffness proportional damping in the following procedures: 
- [*DYNAMIC](ch04abk43.md) (Abaqus/Standard or Abaqus/Explicit)
- [*COMPLEX FREQUENCY](ch03abk26.md)
- [*STEADY STATE DYNAMICS](ch18abk34.md), DIRECT
- [*STEADY STATE DYNAMICS](ch18abk34.md), SUBSPACE PROJECTION
- [*STEADY STATE DYNAMICS](ch18abk34.md) that allows nondiagonal damping
- [*MODAL DYNAMIC](ch13abk18.md) that allows nondiagonal damping

This parameter is ignored in mode-based procedures that use Lanczos or subspace iteration eigenvalue extraction that is not based on the SIM architecture. The default is BETA=0. (Units of T.)

In Abaqus/Explicit set BETA=TABULAR to specify that the stiffness proportional damping is dependent on temperature and/or field dependent variables. 

COMPOSITE

This parameter applies only to Abaqus/Standard analyses.

Set this parameter equal to the fraction of critical damping to be used with this material in calculating composite damping factors for the modes. Composite damping is used in modal-based procedures that follow subspace iteration eigenvalue extraction or eigenvalue extraction using the Lanczos eigensolver that does not use the SIM architecture, except for [*STEADY STATE DYNAMICS](ch18abk34.md), SUBSPACE PROJECTION. Use the [*MODAL DAMPING](ch13abk17.md), VISCOUS=COMPOSITE (or MODAL=COMPOSITE) option to activate composite modal damping.

The default is COMPOSITE=0.

DEPENDENCIES

This parameter applies only to Abaqus/Explicit analyses when ALPHA=TABULAR and/or BETA=TABULAR.

Set this parameter equal to the number of field variables included in the definition of the ![](../graphics/key_eqn00077.gif) and/or ![](../graphics/key_eqn00577.gif) factors, in addition to temperature. If this parameter is omitted, it is assumed that Rayleigh damping is constant or depends only on temperature. See ["Specifying field variable dependence" in "Material data definition," Section 21.1.2 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-mat-cmaterialdata-fvdepen), for more information.

STRUCTURAL

Set this parameter equal to the ![](../graphics/key_eqn00578.gif) factor to create  imaginary stiffness proportional damping in the following procedures:
- [*FREQUENCY](ch06abk35.md), DAMPING PROJECTION=ON
- [*STEADY STATE DYNAMICS](ch18abk34.md), DIRECT
- [*STEADY STATE DYNAMICS](ch18abk34.md), SUBSPACE PROJECTION
- [*STEADY STATE DYNAMICS](ch18abk34.md) that allows nondiagonal damping
- [*MODAL DYNAMIC](ch13abk18.md) that allows nondiagonal damping
- [*COMPLEX FREQUENCY](ch03abk26.md) that uses the SIM architecture

This parameter is ignored in mode-based procedures that use Lanczos or subspace iteration eigenvalue extraction that is not based on the SIM architecture.

The default is STRUCTURAL=0.

### **Data lines to define temperature and/or field variable-dependent mass proportional damping (ALPHA=TABULAR) in Abaqus/Explicit: **

**First line:**

**Subsequent lines (only needed if the DEPENDENCIES parameter has a value greater than six):**

Repeat this set of data lines as often as necessary to define the alpha damping as a function of temperature and other predefined field variables.

### **Data lines to define temperature and/or field variable-dependent stiffness proportional damping (BETA=TABULAR) in Abaqus/Explicit: **

**First line:**

**Subsequent lines (only needed if the DEPENDENCIES parameter has a value greater than six):**

Repeat this set of data lines as often as necessary to define the beta damping as a function of temperature and other predefined field variables.

### **Data lines to define both temperature and/or field variable-dependent mass and stiffness proportional damping (both ALPHA=TABULAR and BETA=TABULAR) in Abaqus/Explicit: **

**First line:**

**Subsequent lines (only needed if the DEPENDENCIES parameter has a value greater than five):**

Repeat this set of data lines as often as necessary to define the alpha and beta damping as a function of temperature and other predefined field variables.




