# *DEBOND







### *DEBONDActivate crack propagation capability and specify debonding amplitude curve.

This option is used to specify that crack propagation may occur between two surfaces that are initially partially bonded. The [*FRACTURE CRITERION](ch06abk33.md) option must appear immediately following this option.

**Products: **Abaqus/Standard  Abaqus/CAE  

**Type: **History data 

**Level: **Step

##### **References:**

- ["Crack propagation analysis," Section 11.4.3 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-anl-acrackpropagation)
- [*FRACTURE CRITERION](ch06abk33.md)

### **Required parameters: **

MASTER

Set this parameter equal to the name of the master surface of the contact pair used in the crack propagation analysis.

SLAVE

Set this parameter equal to the name of the slave surface of the contact pair used in the crack propagation analysis.

### **Optional parameters: **

DEBONDING FORCE

Set DEBONDING FORCE=STEP (default) if the traction between the two surfaces at the crack tip is to be released immediately during the following increment after debonding.

Set DEBONDING FORCE=RAMP if the traction between the two surfaces at the crack tip is to be released gradually during succeeding increments after debonding to avoid a sudden loss of stability.

This parameter is relevant only when TYPE=VCCT or TYPE= ENHANCED VCCT is used on the [*FRACTURE CRITERION](ch06abk33.md) option.

FREQUENCY

Set this parameter equal to the output frequency, in increments. The crack-tip location and associated quantities will always be printed at the last increment of each step unless FREQUENCY=0. The default is FREQUENCY=1. Set FREQUENCY=0 to suppress this output.

OUTPUT

If this parameter is omitted, crack propagation information will be printed in the data (`.dat`) file but not stored in the results (`.fil`) file.

Set OUTPUT=FILE to store the crack propagation information in the results file.

Set OUTPUT=BOTH to print the crack propagation information in the data file and to store it in the results file.

TIME INCREMENT

Set this parameter equal to the suggested time increment for automatic time incrementation to use for the first increment just after debonding starts. The default is the last relative time given on the data lines below.

For fixed time incrementation the value of this parameter will be used as the time increment after debonding starts if Abaqus/Standard finds it needs a smaller time increment than its current value. The time increment size will be modified as required until debonding is complete.

### **Data lines to define the debonding amplitude curve: **

**First line:**

Repeat this data line as often as necessary to define the debonding amplitude curve.




