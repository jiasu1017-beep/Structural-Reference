# *VOLUMETRIC TEST DATA







### *VOLUMETRIC TEST DATAProvide volumetric test data.

This option can be used only in conjunction with the [*HYPERELASTIC](ch08abk06.md) option, the [*HYPERFOAM](ch08abk07.md) option, or the [*VISCOELASTIC](ch21abk04.md) option.

**Products: **Abaqus/Standard  Abaqus/Explicit  Abaqus/CAE  

**Type: **Model data  

**Level: **Model  

**Abaqus/CAE: **Property module

##### **References:**

- ["Hyperelastic behavior of rubberlike materials," Section 22.5.1 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-mat-chyperelastic)
- ["Hyperelastic behavior in elastomeric foams," Section 22.5.2 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-mat-chyperfoam)
- ["Time domain viscoelasticity," Section 22.7.1 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-mat-ctimevisco)
- [*HYPERELASTIC](ch08abk06.md)
- [*HYPERFOAM](ch08abk07.md)
- [*VISCOELASTIC](ch21abk04.md)

### Hyperelastic material model

 Volumetric loading test data can be provided by this option to include user-defined material compressibility. Compressibility can alternatively be included by using the POISSON parameter on the [*HYPERELASTIC](ch08abk06.md) option or, in the case of the Marlow model, by specifying the nominal lateral strain under the [*UNIAXIAL TEST DATA](ch20abk04.md) option. If none of these options is used to specify volumetric behavior, Abaqus/Standard assumes that the material is incompressible, while Abaqus/Explicit will select a default value for the compressibility. See the discussion under “Compressibility” in ["Hyperelastic behavior of rubberlike materials," Section 22.5.1 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-mat-chyperelastic), before using this option in Abaqus/Explicit.

### **Optional parameter: **

SMOOTH

Include this parameter to apply a smoothing filter to the stress-strain data. If the parameter is omitted, no smoothing is performed.

Set this parameter equal to the number *n* such that ![](../graphics/key_eqn00106.gif) is equal to the total number of data points in the moving window through which a cubic polynomial is fit using the least-squares method. *n* should be larger than 1. The default is SMOOTH=3.

### **Optional parameter when the [*VOLUMETRIC TEST DATA](ch21abk08.md) option is used in conjunction with the [*HYPERELASTIC](ch08abk06.md), MARLOW option: **

DEPENDENCIES

Set this parameter equal to the number of field variable dependencies included in the definition of the test data. If this parameter is omitted, it is assumed that the test data depend only on temperature. See “Using the DEPENDENCIES parameter to define field variable dependence”  in ["Material data definition," Section 21.1.2 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-mat-cmaterialdata), for more information.

### **Data lines to specify volumetric test data for hyperelasticity other than the Marlow model (the volume ratios must be arranged in either ascending or descending order if the SMOOTH parameter is used): **

**First line:**

Repeat this data line as often as necessary.

### **Data lines to specify volumetric test data for the Marlow model (the volume ratios must be arranged in descending order if the SMOOTH parameter is used): **

**First line:**

**Subsequent lines (only needed if the DEPENDENCIES parameter has a value greater than five):**

Repeat this set of data lines as often as necessary to define the test data as a function of temperature and other predefined field variables. The volume ratios must be given in descending order.

### Hyperfoam material model

**There are no parameters associated with this option.**

### **Data lines to specify volumetric test data for a hyperfoam: **

**First line:**

Repeat this data line as often as necessary.

### Viscoelastic material model

### **Optional parameter: **

VOLINF

To specify creep test data, set this parameter equal to the value of the long-term, normalized volumetric compliance, ![](../graphics/key_eqn00200.gif). 

To specify relaxation test data, set this parameter equal to the value of the long-term, normalized volumetric modulus ![](../graphics/key_eqn00201.gif). 

The volumetric compliance is related to the volumetric modulus by ![](../graphics/key_eqn00202.gif). The fitting procedure will use this value in the constraint ![](../graphics/key_eqn00203.gif).

### **Data lines to specify volumetric creep test data for a viscoelastic material: **

**First line:**

Repeat this data line as often as necessary to give the compliance-time data.

### **Data lines to specify volumetric relaxation test data for a viscoelastic material: **

**First line:**

Repeat this data line as often as necessary to give the modulus-time data.




