# *HYPERFOAM







### *HYPERFOAMSpecify elastic properties for a hyperelastic foam.

This option is used to define material constants for a general elastomeric foam. This material is distinct from the regular hyperelastic materials in that it is highly compressible.

**Products: **Abaqus/Standard  Abaqus/Explicit  Abaqus/CAE  

**Type: **Model data  

**Level: **Model  

**Abaqus/CAE: **Property module

##### **References:**

- ["Hyperelastic behavior in elastomeric foams," Section 22.5.2 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-mat-chyperfoam)
- [*BIAXIAL TEST DATA](ch02abk09.md)
- [*PLANAR TEST DATA](ch16abk13.md)
- [*SIMPLE SHEAR TEST DATA](ch18abk18.md)
- [*UNIAXIAL TEST DATA](ch20abk04.md)
- [*VOLUMETRIC TEST DATA](ch21abk08.md)

### **Optional parameters: **

MODULI

This parameter is applicable only when the [*HYPERFOAM](ch08abk07.md) option is used in conjunction with the [*VISCOELASTIC](ch21abk04.md) option.

Set MODULI=INSTANTANEOUS to indicate that the hyperfoam material constants define the instantaneous behavior. This parameter value is not available for frequency domain viscoelasticity in an Abaqus/Standard analysis.

Set MODULI=LONG TERM (default) to indicate that the hyperfoam material constants define the long-term behavior.

N

Set this parameter equal to the order of the strain energy potential. The maximum value is N=6. The default is N=1.

POISSON

Set this parameter equal to the effective Poisson's ratio, ![](../graphics/key_eqn00579.gif), of the material. This parameter is valid only when the TEST DATA INPUT parameter is specified.

If this parameter is included, it is assumed that ![](../graphics/key_eqn00805.gif) for all *i* and that lateral strain test data and volumetric test data are not required. If this parameter is omitted, the ![](../graphics/key_eqn00806.gif) are calculated from lateral strain data and/or volumetric test data.

TEST DATA INPUT

Include this parameter if the ![](../graphics/key_eqn00792.gif), the ![](../graphics/key_eqn00793.gif), and the ![](../graphics/key_eqn00806.gif) material constants are to be computed by Abaqus from data taken from simple tests on a material specimen. If this parameter is omitted, ![](../graphics/key_eqn00792.gif), ![](../graphics/key_eqn00793.gif), and ![](../graphics/key_eqn00806.gif) must be given directly on the data lines.

### **To define elastomeric foam behavior by giving test data: **

No data lines are used with this option when the TEST DATA INPUT parameter is specified. The data are given instead under the [*BIAXIAL TEST DATA](ch02abk09.md), the [*PLANAR TEST DATA](ch16abk13.md), the [*SIMPLE SHEAR TEST DATA](ch18abk18.md), the [*UNIAXIAL TEST DATA](ch20abk04.md), and the [*VOLUMETRIC TEST DATA](ch21abk08.md) options.

### **Data lines to define the elastic properties directly: **

**First line if N=1:**

Repeat this data line as often as necessary to define the material constants as a function of temperature.

**First line if N=2:**

Repeat this data line as often as necessary to define the material constants as a function of temperature.

**First line if N=3:**

**Second line if N=3:**

Repeat this pair of data lines as often as necessary to define the material constants as a function of temperature.

**Data lines for higher values of N (up to 6):**




