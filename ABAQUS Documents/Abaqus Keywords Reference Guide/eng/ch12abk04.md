# *LOW DENSITY FOAM







### *LOW DENSITY FOAMSpecify properties for a low-density foam.

This option is used to define material coefficients for low-density foam materials. The [*LOW DENSITY FOAM](ch12abk04.md) option must be used in conjunction with the [*UNIAXIAL TEST DATA](ch20abk04.md), DIRECTION=TENSION and the [*UNIAXIAL TEST DATA](ch20abk04.md), DIRECTION=COMPRESSION options to specify the stress-strain response of the foam material in uniaxial tension and compression, respectively.

**Products: **Abaqus/Explicit  Abaqus/CAE  

**Type: **Model data  

**Level: **Model  

**Abaqus/CAE: **Property module

##### **References:**

- ["Low-density foams," Section 22.9.1 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-mat-clowdensfoam)
- [*UNIAXIAL TEST DATA](ch20abk04.md)

### **Optional parameters: **

LATERAL STRAIN DATA

Use this parameter to specify if lateral strain data are provided as part of the definition of the uniaxial  response of the material in tension and compression.

Set LATERAL STRAIN DATA=NO (default) if no lateral strain data are specified in the definition of the uniaxial response. The lateral strains are assumed to be zero in this case (zero Poisson's ratio).

Set LATERAL STRAIN DATA=YES if lateral strain data are specified in the definition of the uniaxial response.

STRAIN RATE

Use this parameter to define the strain rate measure  used for constitutive calculations.

Set STRAIN RATE=VOLUMETRIC to use the volumetric strain rate. This value is the default if LATERAL STRAIN DATA=NO.

Set STRAIN RATE=PRINCIPAL to use the nominal strain rate along each principal direction of deformation.

Set STRAIN RATE=MAX PRINCIPAL to use the maximum nominal strain rate along the principal direction of deformation. This is the default and only option available when LATERAL STRAIN DATA=YES.

RATE EXTRAPOLATION

Use this parameter to specify extrapolation of rate-dependent uniaxial stress-strain curves beyond the maximum specified strain rate.

Set RATE EXTRAPOLATION=NO (default) to prevent extrapolation. The curve corresponding to the maximum specified strain rate will be used for strain rates greater than the maximum.

Set RATE EXTRAPOLATION=YES to trigger extrapolation beyond the maximum specified strain rate by using the slope with respect to strain rate.

TENSION CUTOFF

Include this parameter to specify a tension cutoff value for the maximum principal stress that the low-density material can sustain with tension. The tension cutoff value must be greater than zero.

FAIL

This parameter is relevant only when the TENSION CUTOFF parameter is used.

Set FAIL=NO (default) to force the maximum principal stress to remain below the tension cutoff without deleting the element.

Set FAIL=YES to allow element deletion when the tension cutoff value is reached.

### **Data line to specify the relaxation coefficients for low-density foams: **

**First (and only) line:**




