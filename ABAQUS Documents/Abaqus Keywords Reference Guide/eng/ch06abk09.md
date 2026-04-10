# *FILE OUTPUT







### *FILE OUTPUTDefine output written to the results file.

**Warning:**This option can create a very large file.

The [*FILE OUTPUT](ch06abk09.md) option provides output of nodal, element, or global data to the selected results file. The [*EL FILE](ch05abk01.md), the [*ENERGY FILE](ch05abk22.md), and/or the [*NODE FILE](ch14abk10.md) options must be used in conjunction with the [*FILE OUTPUT](ch06abk09.md) option.

**Products: **Abaqus/Explicit  Abaqus/CAE  

**Type: **History data 

**Level: **Step

**Abaqus/CAE: **Unsupported; Pub _nolinebreak?Abaqus/CAEPub /_nolinebreak? reads output from the output database file only.

##### **References:**

- ["Output to the data and results files," Section 4.1.2 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-out-oprintfile)
- [*EL FILE](ch05abk01.md)
- [*ENERGY FILE](ch05abk22.md)
- [*NODE FILE](ch14abk10.md)

### **Required parameter: **

NUMBER INTERVAL

Set this parameter equal to the number of intervals during the step at which the file output states are to be written. Abaqus/Explicit will always write the results at the beginning of the step. For example, if NUMBER INTERVAL=10, Abaqus/Explicit will write 11 results states consisting of the values at the beginning of the step and the values at the end of 10 intervals throughout the step. The value of this parameter must be a positive integer.

### **Optional parameter: **

TIME MARKS

Set TIME MARKS=NO (default) to write the results at the increment ending immediately after the time dictated by the NUMBER INTERVAL parameter.

Set TIME MARKS=YES to write results at the exact times dictated by the NUMBER INTERVAL parameter. TIME MARKS=YES cannot be used when either the FIXED TIME INCREMENTATION or the DIRECT USER CONTROL parameter is included on the [*DYNAMIC](ch04abk43.md) option. 

**There are no data lines associated with this option.**



