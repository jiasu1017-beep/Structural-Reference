# *CORRELATION







### *CORRELATIONDefine cross-correlation properties for random response loading.

This option is used to define the cross-correlation as part of the definition of random loading for use in the [*RANDOM RESPONSE](ch17abk07.md) analysis procedure. The [*PSD-DEFINITION](ch16abk32.md) option is also needed to give the frequency function to be used with the correlation definition.

**Product: **Abaqus/Standard  

**Type: **History data 

**Level: **Step

##### **References:**

- ["Random response analysis," Section 6.3.11 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-anl-arandomresponse)
- [*PSD-DEFINITION](ch16abk32.md)
- ["UCORR," Section 1.1.22 of the Abaqus User Subroutines Reference Guide](../sub/sub-link.md#sub-rtn-uucorr)

### **Required parameter for TYPE=CORRELATED and TYPE=UNCORRELATED: **

PSD

Set this parameter equal to the name of the frequency function defined on the [*PSD-DEFINITION](ch16abk32.md) option to be associated with this correlation option.

### **Optional parameters: **

COMPLEX

Set COMPLEX=YES to include both real and imaginary terms in the cross-correlation definition. The alternative is to include real terms only using COMPLEX=NO (default). 

INPUT

Set this parameter equal to the name of the alternate input file containing the data lines for this option. See ["Input syntax rules," Section 1.2.1 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-int-iinputsyntax), for the syntax of such file names. If this parameter is omitted, it is assumed that the data follow the keyword line.

TYPE

Set TYPE=CORRELATED (default) if all terms in the correlation matrix should be included.

Set TYPE=UNCORRELATED if only diagonal terms should be used.

Set TYPE=MOVING NOISE for moving noise loading. In this case only one [*CORRELATION](ch03abk77.md) option can be used in the step. The COMPLEX parameter cannot be used with TYPE=MOVING NOISE.

USER

Include this parameter to indicate that user subroutine [`UCORR`](../sub/sub-link.md#sub-xsl-ucorr) will be called to obtain the scaling factors for the correlation matrix. If this parameter is included, the TYPE parameter can be set only to CORRELATED or UNCORRELATED.

### **Data lines for TYPE=CORRELATED or TYPE=UNCORRELATED: **

**First line:**

Repeat this data line as often as necessary to define the load cases and their associated scaling factors.

### **Data lines if the USER parameter is included: **

**First line:**

Repeat this data line as often as necessary to define the load cases to be correlated.

### **Data lines for TYPE=MOVING NOISE: **

**First line:**

Repeat this data line as often as necessary to define the random loading.




