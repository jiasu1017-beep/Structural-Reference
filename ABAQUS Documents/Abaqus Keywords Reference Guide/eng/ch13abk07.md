# *MASS FLOW RATE







### *MASS FLOW RATESpecify fluid mass flow rate in a heat transfer analysis.

This option is used to specify the mass flow rate per unit area (or through the entire section for one-dimensional elements) for forced convection/diffusion elements in a heat transfer analysis. This option cannot be used with hydrostatic fluid elements.

**Product: **Abaqus/Standard  

**Type: **History data 

**Level: **Step

##### **References:**

- ["Uncoupled heat transfer analysis," Section 6.5.2 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-anl-aheattransfer)
- ["UMASFL," Section 1.1.40 of the Abaqus User Subroutines Reference Guide](../sub/sub-link.md#sub-rtn-uumasfl)

### **Optional parameters: **

AMPLITUDE

Set this parameter equal to the name of the amplitude versus time curve that defines the magnitude of the flow rate during the step (["Amplitude curves," Section 34.1.2 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-prc-pamplitude)). If this parameter is omitted, the reference magnitude is applied immediately at the beginning of the step or linearly over the step, depending on the value assigned to the AMPLITUDE parameter on the [*STEP](ch18abk36.md) option (["Defining an analysis," Section 6.1.2 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-anl-aover)).

INPUT

Set this parameter equal to the name of the alternate input file containing the data lines for this option. See ["Input syntax rules," Section 1.2.1 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-int-iinputsyntax), for the syntax of such file names. If this parameter is omitted, it is assumed that the data follow the keyword line. 

OP

Set OP=MOD (default) for existing [*MASS FLOW RATE](ch13abk07.md) values to remain, with this option modifying existing flow rates or defining additional flow rates.

Set OP=NEW if all existing [*MASS FLOW RATE](ch13abk07.md) values applied to the model should be removed.

USER

Include this parameter to indicate that user subroutine [`UMASFL`](../sub/sub-link.md#sub-xsl-umasfl) will be used to define mass flow rate values. [`UMASFL`](../sub/sub-link.md#sub-xsl-umasfl) will be called for each node given on the data lines. If values are also given on the data lines, these values will be ignored.

### **Data lines to define mass flow rates: **

**First line:**

Repeat this data line as often as necessary to define mass flow rates at different nodes.

### **Data lines to define mass flow rates using user subroutine [`UMASFL`](../sub/sub-link.md#sub-xsl-umasfl): **

**First line:**

Repeat this data line as often as necessary. [`UMASFL`](../sub/sub-link.md#sub-xsl-umasfl) will be called for each node listed.




