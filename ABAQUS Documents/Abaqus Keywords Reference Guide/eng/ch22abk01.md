# *WAVE







### *WAVEDefine gravity waves for use in immersed structure calculations.

This option is used to define gravity waves for use in applying loads.

**Product: **Abaqus/Aqua  

**Type: **Model data  

**Level: **Model  

##### **References:**

- ["Abaqus/Aqua analysis," Section 6.11.1 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-anl-aaqua)
- ["VWAVE," Section 1.2.25 of the Abaqus User Subroutines Reference Guide](../sub/sub-link.md#sub-rtn-uexpwave)
- ["UWAVE," Section 1.1.56 of the Abaqus User Subroutines Reference Guide](../sub/sub-link.md#sub-rtn-uuwave)

### **Optional parameters: **

INPUT

Set this parameter equal to the name of the alternate input file containing the data lines for this option. See ["Input syntax rules," Section 1.2.1 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-int-iinputsyntax), for the syntax of such file names. If this parameter is omitted, it is assumed that the data follow the keyword line. 

TYPE

Set TYPE=STOKES (default) to use Stokes fifth-order wave theory.

Set TYPE=AIRY to use Airy (linearized) wave theory.

Set TYPE=GRIDDED (Abaqus/Standard only) to use gridded data to define the fluid particle velocities, accelerations, free surface elevation, and dynamic pressure.

Set TYPE=USER to allow user-defined waves and update fluid variables like velocity, acceleration, free surface elevation, pressure, and pressure gradients.

### **Optional parameter for TYPE=AIRY: **

WAVE PERIOD

Include this parameter to indicate that the second field in the data line specifies the wave period, ![](../graphics/key_eqn01186.gif). If this parameter is omitted, the second field in the data line specifies the wavelength, ![](../graphics/key_eqn01187.gif).

### **Required parameter for TYPE=GRIDDED: **

DATA FILE

Set this parameter equal to the name of the file containing the gridded data. The file must be a sequential, binary-format file containing records in the format described in ["Abaqus/Aqua analysis," Section 6.11.1 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-anl-aaqua).

### **Optional parameters for TYPE=GRIDDED: **

MINIMUM

Set this parameter equal to the elevation below which point the structure is fully immersed for all time *t*. If this parameter is omitted, the elevation of the structure is compared against the instantaneous free surface to check for fluid surface penetration.

QUADRATIC

Include this parameter to indicate that quadratic interpolation of the wave data is used to determine information between grid points. If this parameter is omitted, linear interpolation is used.

### **Optional parameter for TYPE=USER: **

STOCHASTIC

This parameter applies only to Abaqus/Standard analyses.

Include this parameter to make the intermediate configuration available to user subroutine [`UWAVE`](../sub/sub-link.md#sub-xsl-uwave). Set this parameter equal to a random number seed for use in stochastic analysis. If this parameter is omitted or is included without a value, a default value of 0.0 is used for the random number seed. This value is passed into user subroutine [`UWAVE`](../sub/sub-link.md#sub-xsl-uwave). It is not used otherwise by Abaqus/Aqua.

PROPERTIES

This parameter applies only to Abaqus/Explicit analyses.

Set this parameter equal to the number of constant properties required for the user-defined wave. The default value is zero. This value is passed into user subroutine [`VWAVE`](../sub/sub-link.md#sub-xsl-vwave) as the integer argument `NPROPS`, whereas the property values are passed in as the real array `PROPS`.

DEPVAR

This parameter applies only to Abaqus/Explicit analyses.

Set this parameter equal to the number of state variables required for user-defined waves. The default value is zero. This value is passed into user subroutine [`VWAVE`](../sub/sub-link.md#sub-xsl-vwave) as the integer argument `NSTATEVAR`. The state variables are stored at the nodes of the elements on which the Abaqus/Aqua loads are applied and passed into user subroutine [`VWAVE`](../sub/sub-link.md#sub-xsl-vwave) as the real array argument `STATEVAR`. You must update the state variables in the user subroutine. They are initialized to zero at the beginning of each step.

### **Data line to define Stokes fifth-order waves (TYPE=STOKES): **

**First (and only) line:**

### **Data lines to define Airy waves (TYPE=AIRY): **

**First line:**

Repeat this data line as often as necessary to define multiple wave trains; one line per wave component.

### **Data line to define gridded wave data (TYPE=GRIDDED): **

**First (and only) line:**

### **Data lines to define frequency versus wave amplitude data for stochastic user wave theory (TYPE=USER) in an Abaqus/Standard analysis: **

**First line:**

Repeat this data line as often as necessary to define the wave spectrum. These data pairs are passed into user subroutine [`UWAVE`](../sub/sub-link.md#sub-xsl-uwave). They are not used otherwise by Abaqus/Aqua.

### **Data lines to define wave theory (TYPE=USER) in an Abaqus/Explicit analysis: **

**First line:**

Repeat this data line as often as necessary to include all properties, with a maximum of eight values per line.




