# *TIME POINTS







### *TIME POINTSSpecify time points at which data are written to the output database file, or specify time points in the loading history at which the response of a structure will be evaluated in a direct cyclic analysis.

This option is used to specify time points at which data are written to the output database file or, if it is used in conjunction with the [*DIRECT CYCLIC](ch04abk24.md) option, to specify time points in the loading history at which the response of a structure will be evaluated.

**Products: **Abaqus/Standard  Abaqus/Explicit  Abaqus/CAE  

**Type: **Model data  

**Level: **Model  

**Abaqus/CAE: **Step module

##### **References:**

- [*DIRECT CYCLIC](ch04abk24.md)
- [*OUTPUT](ch15abk03.md)

### **Required parameter: **

NAME

Set this parameter equal to a label that will be used to refer to the time points.

### **Optional parameters: **

GENERATE

If this parameter is included, each data line should give a starting time point, ![](../graphics/key_eqn00153.gif); an ending time point, ![](../graphics/key_eqn01104.gif); and the time increment between these two specified time points, ![](../graphics/key_eqn01105.gif). 

INPUT

Set this parameter equal to the name of the alternate input file containing the data lines for this option. See ["Input syntax rules," Section 1.2.1 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-int-iinputsyntax), for the syntax of such file names. If this parameter is omitted, it is assumed that the data follow the keyword line.

### **Data lines if the GENERATE parameter is omitted: **

**First line:**

Repeat this data line as often as necessary. Up to eight entries are allowed per line. If you use the [*TIME POINTS](ch19abk07.md) option in conjunction with the [*DIRECT CYCLIC](ch04abk24.md) option, the listed time points must include the starting time and ending time in a single loading cycle. The time points must be specified in the step time.

### **Data lines if the GENERATE parameter is included: **

**First line:**

Repeat this data line as often as necessary. If you use the [*TIME POINTS](ch19abk07.md) option in conjunction with the [*DIRECT CYCLIC](ch04abk24.md) option, the listed time points must include the starting time and ending time in a single loading cycle. The time points must be specified in the step time.




