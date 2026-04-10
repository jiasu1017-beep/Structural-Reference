# *FILE FORMAT







### *FILE FORMATSpecify format for results file output and invoke zero-increment results file output.

This option is used to specify the format in which the Abaqus/Standard results file output is written and to invoke zero-increment file output for all valid procedures in the analysis. This option can appear only once in an analysis, and the format cannot be changed upon restart.

**Products: **Abaqus/Standard  Abaqus/CAE  

**Type: **Model or history data  

**Level: **Model,  Step

**Abaqus/CAE: **Unsupported; Pub _nolinebreak?Abaqus/CAEPub /_nolinebreak? does not use the results file.

##### **Reference:**

- ["Output," Section 4.1.1 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-out-ooutput)

### **Optional parameters: **

ASCII

Include this parameter to specify that the results file output is to be written in ASCII format. If the [*FILE FORMAT](ch06abk08.md) option is omitted or this parameter is not used, the default is to write a binary file. 

ZERO INCREMENT

Include this parameter to specify that results file output should be written at the beginning of a step (the zero increment) for all valid procedures in the analysis. If the [*FILE FORMAT](ch06abk08.md) option is omitted or this parameter is not used, by default output will not be written at the zero increment.

**There are no data lines associated with this option.**



