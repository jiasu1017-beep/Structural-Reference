# *USER DEFINED FIELD







### *USER DEFINED FIELDRedefine field variables at a material point.

This material option is used to allow the values of field variables at a material point to be redefined within an increment via user subroutine [`USDFLD`](../sub/sub-link.md#sub-xsl-usdfld) in Abaqus/Standard analyses or user subroutine [`VUSDFLD`](../sub/sub-link.md#sub-xsl-vusdfld) in Abaqus/Explicit analyses. If the [*USER DEFINED FIELD](ch20abk06.md) option is used, it must appear within a [*MATERIAL](ch13abk08.md) definition (["Material data definition," Section 21.1.2 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-mat-cmaterialdata)).

**Products: **Abaqus/Standard  Abaqus/Explicit  Abaqus/CAE  

**Type: **Model data  

**Level: **Model  

**Abaqus/CAE: **Property module

##### **References:**

- ["USDFLD," Section 1.1.50 of the Abaqus User Subroutines Reference Guide](../sub/sub-link.md#sub-rtn-uusdfld)
- ["VUSDFLD," Section 1.2.22 of the Abaqus User Subroutines Reference Guide](../sub/sub-link.md#sub-rtn-uexpusdfld)

### **Optional parameter: **

PROPERTIES

This parameter applies only to Abaqus/Explicit analyses.

Set this parameter equal to the number of properties being entered. The properties are available for use in user subroutine [`VUSDFLD`](../sub/sub-link.md#sub-xsl-vusdfld).

### **Data lines to define material properties when PROPERTIES is specified: **

**First line:**

Repeat this data line as often as necessary to define all material properties.




