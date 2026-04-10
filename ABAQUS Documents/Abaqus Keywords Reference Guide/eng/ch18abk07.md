# *SELECT EIGENMODES







### *SELECT EIGENMODESSelect the modes to be used in a modal dynamic, complex eigenvalue extraction, or substructure generation analysis.

This option selects the modes to be used in a dynamic analysis based on modes, in a complex eigenvalue extraction analysis, or in a substructure generation analysis. Only one option per step can be used. If this option is omitted  in a dynamic analysis based on modes or in a complex eigenvalue extraction analysis, all modes extracted in the prior [*FREQUENCY](ch06abk35.md) step will be used, including residual modes if they were activated.

If this option is omitted  in a substructure generation analysis, none of the modes extracted in the prior [*FREQUENCY](ch06abk35.md) step will be used, including residual modes if they were activated. 

**Products: **Abaqus/Standard  Abaqus/CAE  

**Type: **History data 

**Level: **Step

**Abaqus/CAE: **Supported in the Step module only for substructure generation.

##### **References:**

- ["Implicit dynamic analysis using direct integration," Section 6.3.2 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-anl-adynamic)
- ["Complex eigenvalue extraction," Section 6.3.6 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-anl-acomplexfreqextract)
- ["Transient modal dynamic analysis," Section 6.3.7 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-anl-amodaldynamic)
- ["Mode-based steady-state dynamic analysis," Section 6.3.8 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-anl-asteadystdyn)
- ["Subspace-based steady-state dynamic analysis," Section 6.3.9 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-anl-asteadystdynsubspace)
- ["Defining substructures," Section 10.1.2 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-anl-asuperelementdef)
- ["Response spectrum analysis," Section 6.3.10 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-anl-aresponsespectrum)
- ["Random response analysis," Section 6.3.11 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-anl-arandomresponse)
- [*MODAL DAMPING](ch13abk17.md)

### **Optional parameters: **

DEFINITION

Set DEFINITION=MODE NUMBERS (default) to indicate that the selected modes are given as a collection of mode numbers.

Set DEFINITION= FREQUENCY RANGE to indicate that the modes are selected from the specified frequency ranges including frequency boundaries. Frequency ranges can be discontinuous.

 If both the [*MODAL DAMPING](ch13abk17.md) and [*SELECT EIGENMODES](ch18abk07.md) options are used in the same step, the DEFINITION parameter must be set equal to the same value in both options.

GENERATE

If this parameter is included, each data line should give a first mode, ![](../graphics/key_eqn00707.gif); a last mode, ![](../graphics/key_eqn00708.gif); and the increment in mode numbers between these modes, *i*. Then all modes going from ![](../graphics/key_eqn00707.gif) to ![](../graphics/key_eqn00708.gif) in steps of *i* will be added to the set. *i* must be an integer such that ![](../graphics/key_eqn00926.gif) is a whole number (not a fraction).

This parameter can be used only with DEFINITION=MODE NUMBERS.

### **Data lines if DEFINITION=MODE NUMBERS and the GENERATE parameter is omitted: **

**First line:**

Repeat this data line as often as necessary. Up to 16 entries are allowed per line.

### **Data lines if DEFINITION=MODE NUMBERS and the GENERATE parameter is included: **

**First line:**

Repeat this data line as often as necessary.

### **Data lines if DEFINITION=FREQUENCY RANGE: **

**First line:**

Repeat this data line as often as necessary.




