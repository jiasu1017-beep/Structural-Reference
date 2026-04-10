# *SPECTRUM







### *SPECTRUMDefine or create a response spectrum.

This option is used to convert a dynamic event into a spectrum to be used in a [*RESPONSE SPECTRUM](ch17abk15.md) analysis. You can define a spectrum using values of *S* as a function of frequency and damping or create a spectrum from a user-specified amplitude that describes a dynamic event.

**Products: **Abaqus/Standard  Abaqus/CAE  

**Type: **Model data  

**Level: **Model  

**Abaqus/CAE: **Amplitude toolset; supported only for defining a spectrum.

##### **References:**

- ["Response spectrum analysis," Section 6.3.10 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-anl-aresponsespectrum)
- [*RESPONSE SPECTRUM](ch17abk15.md)

### Defining a spectrum using values of S as a function of frequency and damping

### **Required parameter: **

NAME

Set this parameter equal to a label that will be used to refer to the spectrum. This label is used to cross-reference a spectrum on the [*RESPONSE SPECTRUM](ch17abk15.md) option.

### **Optional parameters: **

G

Set this parameter equal to the value of the acceleration of gravity. This parameter is used only when TYPE=G is specified.

INPUT

Set this parameter equal to the name of the alternate input file containing the data lines for this option. See ["Input syntax rules," Section 1.2.1 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-int-iinputsyntax), for the syntax of such file names. If this parameter is omitted, it is assumed that the data follow the keyword line.

TYPE

Set TYPE=DISPLACEMENT, TYPE=VELOCITY, or TYPE=ACCELERATION (default) to define the units in which the spectrum is defined.

Set TYPE=G to enter an acceleration spectrum in *g*-units. The parameter G then defines the gravitational acceleration.

### **Date lines to define a spectrum using values of *S* as a function of frequency and damping: **

**First line:**

Repeat this data line as often as necessary to define the spectrum at all frequencies at each damping value.

### Creating a spectrum from a user-specified amplitude

### **Required parameters: **

CREATE

Use this parameter to invoke spectrum building from a dynamic event provided by the user specified amplitude. 

AMPLITUDE

Set this parameter equal to an amplitude name that describes the dynamic event used to create the spectrum.

NAME

Set this parameter equal to a label that will be used to refer to this created spectrum. This label is used to cross-reference a spectrum on the [*RESPONSE SPECTRUM](ch17abk15.md) option.

 TIME INCREMENT

Set this parameter equal to the time increment for implicit time integration scheme used to build this spectrum. 

### **Optional parameters: **

G

Set this parameter equal to the value of the acceleration of gravity. This parameter is used when TYPE=G or EVENT TYPE=G is specified.

TYPE

Set TYPE=DISPLACEMENT, TYPE=VELOCITY, or TYPE=ACCELERATION (default) to define the units in which the spectrum is created.

Set TYPE=G to create an acceleration spectrum in *g*-units. The parameter G then defines the gravitational acceleration.

ABSOLUTE

This parameter is only relevant for acceleration spectrum. Use this parameter to request creation of absolute acceleration spectrum (default, if both ABSOLUTE and RELATIVE  parameters are omitted).

RELATIVE

This parameter is only relevant for acceleration spectrum. Use this parameter to request creation of relative acceleration spectrum.

DAMPING GENERATE

Use this parameter to request generation of the list containing the fraction of critical damping for which spectra will be created.

EVENT TYPE

Set EVENT TYPE=DISPLACEMENT, EVENT TYPE=VELOCITY, or EVENT TYPE=ACCELERATION (default) to define the units in which the amplitude is defined.

Set EVENT TYPE=G to enter an acceleration amplitude in *g*-units. The parameter G then defines the gravitational acceleration.

FILE

Set this parameter equal to the name of the alternate output file containing the created spectrum data. Each line of this data file will contain magnitude of the spectrum, frequency, in cycles per time, at which this magnitude is used, and associated damping, given as ratio of critical damping. See ["Input syntax rules," Section 1.2.1 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-int-iinputsyntax), for the syntax of such file names. If this parameter is omitted, it is assumed that the created spectrum can only be used in a subsequent response spectrum procedures of the same or restarted job.

### **Data lines to create a spectrum from a user-specified amplitude: **

**First line:**

**Second line if the DAMPING GENERATE parameter is omitted:**

**Second line if the DAMPING GENERATE parameter is included:**




