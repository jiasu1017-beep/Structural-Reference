# *CONTACT PRINT







### *CONTACT PRINTDefine print requests for contact variables.

This option is used to provide tabular printed output of contact variables for contact surface pairs.

**Product: **Abaqus/Standard  

**Type: **History data 

**Level: **Step

##### **Reference:**

- ["Output to the data and results files," Section 4.1.2 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-out-oprintfile)

### **Optional parameters: **

FREQUENCY

Set this parameter equal to the output frequency, in increments. The output will always be printed at the last increment of each step unless FREQUENCY=0. The default is FREQUENCY=1. Set FREQUENCY=0 to suppress the output.

MASTER

Set this parameter equal to the name of the master surface for which this output request is being made. 

NSET

Set this parameter equal to the name of the node set for which this output request is being made.

SLAVE

Set this parameter equal to the name of the slave surface for which this output request is being made.

SUMMARY

Set SUMMARY=YES (default) to obtain a summary of the maximum and minimum values in each column of the table and their locations. Set SUMMARY=NO to suppress this summary.

TOTALS

Set TOTALS=YES to print the total of each column in the table. The default is TOTALS=NO.

### **Data lines to request contact variable output in the data file: **

**First line:**

Repeat this data line as often as necessary: each line defines a table. If this line is omitted, the default variables will be output.




