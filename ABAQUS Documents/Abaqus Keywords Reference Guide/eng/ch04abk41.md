# *DSFLUX







### *DSFLUXSpecify distributed surface fluxes for heat transfer analysis.

This option is used to apply distributed surface fluxes for a fully coupled thermal-stress analysis in Abaqus/Standard and Abaqus/Explicit. In Abaqus/Standard it is also used for heat transfer, coupled thermal-electrical, and coupled thermal-electrical-structural analyses. In Abaqus/CFD it is used for thermal energy (heat) transport and conjugate heat transfer analyses.

**Products: **Abaqus/Standard  Abaqus/Explicit  Abaqus/CFD  Abaqus/CAE  

**Type: **History data 

**Level: **Step

**Abaqus/CAE: **Load module

##### **References:**

- ["Thermal loads," Section 34.4.4 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-prc-pthermal)
- ["DFLUX," Section 1.1.3 of the Abaqus User Subroutines Reference Guide](../sub/sub-link.md#sub-rtn-udflux)

### **Optional parameters: **

AMPLITUDE

Set this parameter equal to the name of the amplitude curve that defines the magnitude of the distributed fluxes during the step (["Amplitude curves," Section 34.1.2 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-prc-pamplitude)).

If this parameter is omitted for uniform flux types in an Abaqus/Standard analysis, the reference magnitude is applied immediately at the beginning of the step or linearly over the step, depending on the value assigned to the AMPLITUDE parameter on the [*STEP](ch18abk36.md) option (["Defining an analysis," Section 6.1.2 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-anl-aover)). If this parameter is omitted in an Abaqus/Explicit or Abaqus/CFD analysis, the reference magnitude is applied immediately at the beginning of the step.

For nonuniform flux type SNU (which is available only in Abaqus/Standard), the flux magnitude is defined in user subroutine [`DFLUX`](../sub/sub-link.md#sub-xsl-dflux), and AMPLITUDE references are ignored.

OP

Set OP=MOD (default) for existing [*DSFLUX](ch04abk41.md)s to remain, with this option modifying existing fluxes or defining additional fluxes.

Set OP=NEW if all existing [*DSFLUX](ch04abk41.md)s applied to the model should be removed.

### **Data lines to define a distributed surface flux: **

**First line:**

Repeat this data line as often as necessary to define distributed fluxes for different surfaces.




