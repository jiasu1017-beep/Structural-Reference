# *ACOUSTIC MEDIUM







### *ACOUSTIC MEDIUMSpecify an acoustic medium.

This option is used to define the properties of an acoustic medium used with acoustic elements. The [*ACOUSTIC MEDIUM](ch01abk02.md) option must be used in conjunction with the [*MATERIAL](ch13abk08.md) option. The [*ACOUSTIC MEDIUM](ch01abk02.md) option can be used multiple times to specify all the properties of an acoustic medium.

**Products: **Abaqus/Standard  Abaqus/Explicit  Abaqus/CAE  

**Type: **Model data  

**Level: **Model  

**Abaqus/CAE: **Property module

##### **Reference:**

- ["Acoustic medium," Section 26.3.1 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-mat-cacousticmed)

### **Optional, mutually exclusive parameters: **

BULK MODULUS

Include this parameter to define the bulk modulus for the acoustic medium (default). 

CAVITATION LIMIT

This parameter applies only to Abaqus/Explicit analyses.

Include this parameter to define the cavitation pressure limit for the acoustic medium. When the fluid absolute pressure drops to this limit, the acoustic medium undergoes free volume expansion or cavitation without a further decrease in the pressure. A negative cavitation limit value represents an acoustic medium that is capable of sustaining a negative absolute pressure up to the specified limit value. Any nonzero initial acoustic static pressure values such as those due to the atmospheric pressure and/or the hydrostatic loading can be specified using the [*INITIAL CONDITIONS](ch09abk18.md), TYPE=ACOUSTIC STATIC PRESSURE option.

If this parameter is omitted, the fluid is assumed not to cavitate even under arbitrarily large negative pressure conditions.

COMPLEX BULK MODULUS

Include this parameter to define the complex bulk modulus for the acoustic medium.

COMPLEX DENSITY

Include this parameter to define the complex density for the acoustic medium.

POROUS MODEL

This parameter applies only to Abaqus/Standard analyses.

Set POROUS MODEL=DELANY BAZLEY (default) to use the Delany-Bazley model to compute the frequency-dependent complex density and the complex bulk modulus.

Set POROUS MODEL=MIKI to use the Delany-Bazley-Miki model to compute the frequency-dependent complex density and the complex bulk modulus.

VOLUMETRIC DRAG

Include this parameter to define the volumetric drag coefficient for the acoustic medium. 

### **Optional parameter: **

DEPENDENCIES

Set this parameter equal to the number of field variable dependencies included in the definition of the acoustic medium, in addition to temperature. If this parameter is omitted, it is assumed that the acoustic medium property is constant or depends only on temperature. See ["Specifying field variable dependence" in "Material data definition," Section 21.1.2 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-mat-cmaterialdata-fvdepen), for more information.

### **Data lines to define the bulk modulus of an acoustic material: **

**First line:**

**Subsequent lines (only needed if the DEPENDENCIES parameter has a value greater than six):**

Repeat this set of data lines as often as necessary to define the bulk modulus as a function of temperature and other predefined field variables.

### **Data lines to define the cavitation pressure limit of an acoustic material: **

**First line:**

**Subsequent lines (only needed if the DEPENDENCIES parameter has a value greater than six):**

Repeat this set of data lines as often as necessary to define the cavitation pressure limit as a function of temperature and other predefined field variables.

### **Data line to define the complex bulk modulus of an acoustic material: **

**First line:**

Repeat this data line as often as necessary to define the complex bulk modulus as a function of frequency. 

### **Data line to define the complex density of an acoustic material: **

**First line:**

Repeat this data line as often as necessary to define the complex density as a function of frequency.

### **Data lines to define the volumetric drag of an acoustic material: **

**First line:**

**Subsequent lines (only needed if the DEPENDENCIES parameter has a value greater than five):**

Repeat this set of data lines as often as necessary to define the volumetric drag as a function of frequency, temperature, and other predefined field variables.

### **Data line when POROUS MODEL=DELANY BAZLEY or POROUS MODEL=MIKI: **

**First (and only) line:**




