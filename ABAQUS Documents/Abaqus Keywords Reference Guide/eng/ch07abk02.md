# *GAP CONDUCTANCE







### *GAP CONDUCTANCEIntroduce heat conductance between interface surfaces.

This option is used to provide conductive heat transfer between closely adjacent (or contacting) surfaces. It must be used in conjunction with the [*SURFACE INTERACTION](ch18abk50.md) option or in an Abaqus/Standard analysis with the [*GAP](ch07abk01.md) option.

**Products: **Abaqus/Standard  Abaqus/Explicit  Abaqus/CAE  

**Type: **Model data in Abaqus/Standard; History data in Abaqus/Explicit  

**Level: **Part,  Part instance,  Assembly,  Model in Abaqus/Standard; Step in Abaqus/Explicit  

**Abaqus/CAE: **Interaction module

##### **References:**

- ["Thermal contact properties," Section 37.2.1 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-cni-athermalinteraction)
- [*GAP](ch07abk01.md)
- [*INTERFACE](ch09abk22.md)
- [*SURFACE INTERACTION](ch18abk50.md)
- ["GAPCON," Section 1.1.10 of the Abaqus User Subroutines Reference Guide](../sub/sub-link.md#sub-rtn-ugapcon)

### **Optional parameters: **

DEPENDENCIES

Set this parameter equal to the number of field variables on which the gap conductance, *k*, depends.

PRESSURE

Include this parameter to indicate that *k* is a function of the contact pressure between the surfaces, *p*. Omit this parameter to define *k* as a function of the clearance, *d*, between the surfaces.

USER

This parameter applies only to Abaqus/Standard analyses.

Include this parameter to define *k* in user subroutine [`GAPCON`](../sub/sub-link.md#sub-xsl-gapcon). Using this parameter will cause the DEPENDENCIES and PRESSURE parameters and any data lines to be ignored.

### **Data lines to define the gap conductance (*k*) directly: **

**First line:**

Repeat this data line as often as necessary to define the dependence of gap conductance on gap clearance, gap pressure, average surface temperature, average mass flow rate, and any predefined field variables. At least two data lines must be specified. When gap conductance is defined as a function of clearance, the value of the conductance drops to zero immediately after the last data point; therefore, there is no heat conductance when the clearance is greater than the value corresponding to the last data point.

### **Data lines to define the gap conductance (*k*) by a user subroutine: **

There are no data lines when the USER parameter is used. Instead, define the gap conductance in user subroutine [`GAPCON`](../sub/sub-link.md#sub-xsl-gapcon).




