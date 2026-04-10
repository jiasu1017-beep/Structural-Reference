# *VIEW FACTOR OUTPUT







### *VIEW FACTOR OUTPUTWrite radiation view factors to the results file in cavity radiation heat transfer analysis.

This option is used to write cavity radiation element view factor matrices to the results file. This option is available only for heat transfer analysis including cavity radiation.

**Product: **Abaqus/Standard  

**Type: **History data 

**Level: **Step

##### **References:**

- ["Cavity radiation," Section 41.1.1 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-cni-acavityradiation)
- ["Output," Section 4.1.1 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-out-ooutput)

### **Required parameter: **

CAVITY

Set this parameter equal to the name of the cavity for which this output request is being made.

### **Optional parameter: **

FREQUENCY

Set this parameter equal to the output frequency, in increments. The output will always be written at the last increment of each step unless FREQUENCY=0. The default is FREQUENCY=1. Set FREQUENCY=0 to suppress the output.

**There are no data lines associated with this option.**



