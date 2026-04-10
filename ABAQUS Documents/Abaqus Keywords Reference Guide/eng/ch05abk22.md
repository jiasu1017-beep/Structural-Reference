# *ENERGY FILE







### *ENERGY FILEWrite energy output to the results file.

This option is used to write a summary of the total energy content of a model to the results (`.fil`) file in an Abaqus/Standard analysis or to the selected results (`.sel`) file in an Abaqus/Explicit analysis. In an Abaqus/Explicit analysis it must be used in conjunction with the [*FILE OUTPUT](ch06abk09.md) option.

**Products: **Abaqus/Standard  Abaqus/Explicit  Abaqus/CAE  

**Type: **History data 

**Level: **Step

**Abaqus/CAE: **Unsupported; Pub _nolinebreak?Abaqus/CAEPub /_nolinebreak? reads output from the output database file only.

##### **References:**

- ["Output to the data and results files," Section 4.1.2 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-out-oprintfile)
- [*FILE OUTPUT](ch06abk09.md)

### **Optional parameters: **

ELSET

This parameter applies only to Abaqus/Standard analyses.

Set this parameter equal to the name of the element set for which this output request is being made. If this parameter is omitted, the energy for the whole model will be output.

FREQUENCY

This parameter applies only to Abaqus/Standard analyses.

Set this parameter equal to the output frequency, in increments. The output will always be written to the results file at the last increment of each step unless FREQUENCY=0. The default is FREQUENCY=1. Set FREQUENCY=0 to suppress the output.

**There are no data lines associated with this option.**



