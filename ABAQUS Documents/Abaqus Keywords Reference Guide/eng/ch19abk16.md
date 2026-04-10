# *TRS







### *TRSUsed to define temperature-time shift for time history viscoelastic analysis.

This option can be used only in conjunction with the [*VISCOELASTIC](ch21abk04.md) option and, in Abaqus/Explicit, with the [*VISCOSITY](ch21abk05.md) option.

In an Abaqus/Standard analysis, either the nonlinear viscoelasticity must be defined by using the [*VISCOELASTIC](ch21abk04.md), NONLINEAR option or viscoelasticity must be defined in the time domain by using the [*VISCOELASTIC](ch21abk04.md), TIME option.

**Products: **Abaqus/Standard  Abaqus/Explicit  Abaqus/CAE  

**Type: **Model data  

**Level: **Model  

**Abaqus/CAE: **Property module

##### **References:**

- ["Time domain viscoelasticity," Section 22.7.1 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-mat-ctimevisco)
- ["Parallel rheological framework," Section 22.8.2 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-mat-cnonlinvisco)
- ["UTRS," Section 1.1.53 of the Abaqus User Subroutines Reference Guide](../sub/sub-link.md#sub-rtn-uutrs)
- ["UTRSNETWORK," Section 1.1.54 of the Abaqus User Subroutines Reference Guide](../sub/sub-link.md#sub-rtn-uutrsnetwork)
- ["VUTRS," Section 1.2.23 of the Abaqus User Subroutines Reference Guide](../sub/sub-link.md#sub-rtn-uexputrs)
- [*VISCOELASTIC](ch21abk04.md)
- [*VISCOSITY](ch21abk05.md)

### **Optional parameters: **

DEFINITION

Set DEFINITION=WLF (default) to define the shift function by the Williams-Landel-Ferry approximation. 

Set DEFINITION=ARRHENIUS to define the shift function by the Arrhenius approximation. 

Set DEFINITION=USER to define the shift function in user subroutines. In Abaqus/Standard analyses define the shift function in user subroutine [`UTRS`](../sub/sub-link.md#sub-xsl-utrs) for the linear viscoelastic model (see ["Time domain viscoelasticity," Section 22.7.1 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-mat-ctimevisco)) or in user subroutine [`UTRSNETWORK`](../sub/sub-link.md#sub-xsl-utrsnetwork) for the nonlinear viscoelastic model defined using the parallel rheological framework (see ["Parallel rheological framework," Section 22.8.2 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-mat-cnonlinvisco)). In Abaqus/Explicit analyses define the shift function in user subroutine [`VUTRS`](../sub/sub-link.md#sub-xsl-vutrs) for the linear viscoelastic model.

PROPERTIES

This parameter applies only to Abaqus/Explicit analyses and to Abaqus/Standard analyses if user subroutine [`UTRSNETWORK`](../sub/sub-link.md#sub-xsl-utrsnetwork) is used to define the shift function.

Set this parameter equal to the number of properties being entered. The properties are available for use in user subroutines [`VUTRS`](../sub/sub-link.md#sub-xsl-vutrs) or [`UTRSNETWORK`](../sub/sub-link.md#sub-xsl-utrsnetwork).

### **Data line to define the shift function by the Williams-Landel-Ferry approximation: **

**First (and only) line:**

### **Data line to define the shift function by the Arrhenius approximation: **

**First (and only) line:**

In addition, you need to specify the universal gas constant and absolute zero using the [*PHYSICAL CONSTANTS](ch16abk09.md) option.

### **Data lines to define material properties for a user-defined shift function (DEFINITION=USER): **

**No data lines are needed if the PROPERTIES parameter is omitted or set to 0. Otherwise, first line:**

Repeat this data line as often as necessary to define all material properties.




