# *SFILM







### *SFILMDefine film coefficients and associated sink temperatures over a surface for heat transfer analysis.

This option is used to provide film coefficients and sink temperatures over a surface for fully coupled thermal-stress analysis. In Abaqus/Standard it is also used in heat transfer, coupled thermal-electrical, and coupled thermal-electrical-structural analyses.

**Products: **Abaqus/Standard  Abaqus/Explicit  Abaqus/CFD  Abaqus/CAE  

**Type: **History data 

**Level: **Step

**Abaqus/CAE: **Interaction module

##### **References:**

- ["Thermal loads," Section 34.4.4 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-prc-pthermal)
- ["FILM," Section 1.1.6 of the Abaqus User Subroutines Reference Guide](../sub/sub-link.md#sub-rtn-ufilm)

### **Optional parameters: **

AMPLITUDE

Set this parameter equal to the name of the [*AMPLITUDE](ch01abk09.md) option that gives the variation of the sink temperature, ![](../graphics/key_eqn00086.gif), with time.

If this parameter is omitted in an Abaqus/Standard analysis, the reference sink temperature is applied immediately at the beginning of the step or linearly over the step, depending on the value assigned to the AMPLITUDE parameter on the [*STEP](ch18abk36.md) option (["Defining an analysis," Section 6.1.2 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-anl-aover)). If this parameter is omitted in an Abaqus/Explicit analysis, the reference sink temperature is applied immediately at the beginning of the step.

For nonuniform films of type FNU (which are available only in Abaqus/Standard), the sink temperature amplitude is defined in user subroutine [`FILM`](../sub/sub-link.md#sub-xsl-film), and AMPLITUDE references are used only to modify the sink temperature passed into the user subroutine.

FILM AMPLITUDE

This parameter applies only to Abaqus/Standard and Abaqus/Explicit analyses.

Set this parameter equal to the name of the [*AMPLITUDE](ch01abk09.md) option that gives the variation of the film coefficient, *h*, with time.

If this parameter is omitted in an Abaqus/Standard analysis, the reference film coefficient is applied immediately at the beginning of the step and kept constant over the step, independent of the value assigned to the AMPLITUDE parameter on the [*STEP](ch18abk36.md) option. If this parameter is omitted in an Abaqus/Explicit analysis, the reference sink temperature given on the data lines is applied throughout the step.

The FILM AMPLITUDE parameter is ignored if a film coefficient is defined to be a function of temperature and field variables using the [*FILM PROPERTY](ch06abk11.md) option.

For nonuniform films of type FNU (which are available only in Abaqus/Standard), the film coefficient amplitude is defined in user subroutine [`FILM`](../sub/sub-link.md#sub-xsl-film), and FILM AMPLITUDE references are used only to modify the film coefficient passed into the user subroutine.

OP

Set OP=MOD (default) to modify existing films or to define additional films.

Set OP=NEW if all existing [*SFILM](ch18abk08.md)s applied to the model should be removed.

### **Data lines to define sink temperatures and film coefficients: **

**First line:**

Repeat this data line as often as necessary to define film conditions for different surfaces.




