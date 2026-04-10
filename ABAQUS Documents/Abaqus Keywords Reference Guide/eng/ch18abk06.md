# *SELECT CYCLIC SYMMETRY MODES







### *SELECT CYCLIC SYMMETRY MODESSpecify the cyclic symmetry modes in an eigenvalue analysis of a cyclic symmetric structure.

This option is used to specify which cyclic symmetry modes should be used in an eigenvalue analysis.

**Products: **Abaqus/Standard  Abaqus/CAE  

**Type: **History data 

**Level: **Step

**Abaqus/CAE: **Interaction module

##### **References:**

- ["Analysis of models that exhibit cyclic symmetry," Section 10.4.3 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-anl-acyclicsymmetry)
- [*CYCLIC SYMMETRY MODEL](ch03abk92.md)
- [*TIE](ch19abk06.md)

### **Optional parameters: **

EVEN

Include this parameter to request the even cyclic symmetry modes only. If this parameter is omitted, all cyclic symmetry modes will be used within the NMIN, NMAX range.

NMIN

Set this parameter equal to the lowest cyclic symmetry mode number. The default value is 0.

NMAX

Set this parameter equal to the highest cyclic symmetry mode number. The default value is the highest number that is feasible for the number of sectors given in the [*CYCLIC SYMMETRY MODEL](ch03abk92.md) option.

**There are no data lines associated with this option.**



