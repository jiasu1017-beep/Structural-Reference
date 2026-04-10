# *ENERGY PRINT







### *ENERGY PRINTPrint a summary of the total energies.

This option is used to print a summary of the total energy content of a whole model or part of a model to the data (`.dat`) file.

**Product: **Abaqus/Standard  

**Type: **History data 

**Level: **Step

##### **Reference:**

- ["Output to the data and results files," Section 4.1.2 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-out-oprintfile)

### **Optional parameters: **

ELSET

Set this parameter equal to the name of the element set for which this output request is being made. If this parameter is omitted, the energy for the whole model will be output. 

FREQUENCY

Set this parameter equal to the output frequency, in increments. The output will always be printed at the last increment of each step unless FREQUENCY=0. The default is FREQUENCY=1. Set FREQUENCY=0 to suppress the output.

**There are no data lines associated with this option.**



