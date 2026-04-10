# *ADAPTIVE MESH







### *ADAPTIVE MESHDefine an adaptive mesh domain.

This option is used to define an adaptive mesh domain and to specify the frequency and intensity of adaptive meshing for that domain. 

**Products: **Abaqus/Standard  Abaqus/Explicit  Abaqus/CAE  

**Type: **History data 

**Level: **Step

**Abaqus/CAE: **Supported in the Step module; only one adaptive mesh domain can be defined per step.

##### **References:**

- ["Defining ALE adaptive mesh domains in Abaqus/Explicit," Section 12.2.2 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-anl-aaledomains)
- ["ALE adaptive meshing and remapping in Abaqus/Explicit," Section 12.2.3 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-anl-aaleremesh)
- ["Defining ALE adaptive mesh domains in Abaqus/Standard," Section 12.2.6 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-anl-aalestd)
- ["ALE adaptive meshing and remapping in Abaqus/Standard," Section 12.2.7 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-anl-aalestdremesh)
- [*ADAPTIVE MESH CONTROLS](ch01abk06.md)
- [*ADAPTIVE MESH CONSTRAINT](ch01abk05.md)

### **At least one of the following parameters is required: **

ELSET

Set this parameter equal to the name of the element set that contains all the solid elements in the adaptive mesh domain.

OP

Set OP=MOD (default) to modify the frequency and intensity of adaptive meshing for an existing adaptive mesh domain (with the same element set name) or to define a new adaptive mesh domain.

Set OP=NEW if all adaptive mesh domains that are currently in effect should be removed. To remove only selected adaptive mesh domains, use OP=NEW and respecify all adaptive mesh domains that are to be retained.

The OP parameter must be the same for all uses of the [*ADAPTIVE MESH](ch01abk04.md) option within a single step.

### **Optional parameters: **

CONTROLS

Set this parameter equal to the name of the [*ADAPTIVE MESH CONTROLS](ch01abk06.md) option associated with this adaptive mesh domain. Adaptive mesh controls can be used to control the adaptive meshing in explicit dynamic analysis and in implicit acoustic analysis and to control the advection algorithms applied to the adaptive mesh domain in explicit dynamic analysis.

FREQUENCY

Set this parameter equal to the frequency in increments at which adaptive meshing is to be performed. When the option is used in acoustic analysis or when a spatial mesh constraint or an Eulerian boundary region is defined on the adaptive mesh domain in explicit dynamic analysis, the default frequency is 1. In all other cases the default frequency is 10.

INITIAL MESH SWEEPS

This parameter applies only to Abaqus/Explicit analyses.

Set this parameter equal to the number of mesh sweeps to be performed at the beginning of the first step in which this adaptive mesh definition is active. The default number of initial mesh sweeps is 5 if [*ADAPTIVE MESH CONTROLS](ch01abk06.md), SMOOTHING OBJECTIVE=UNIFORM is used. The default number of initial mesh sweeps is 2 if [*ADAPTIVE MESH CONTROLS](ch01abk06.md),SMOOTHING OBJECTIVE=GRADED is used.

MESH SWEEPS

Set this parameter equal to the number of mesh sweeps to be performed in each adaptive mesh increment. The default number of mesh sweeps is 1.

**There are no data lines associated with this option.**



