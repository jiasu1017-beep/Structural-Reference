# *FABRIC







### *FABRICSpecify the in-plane response of a fabric material.

This option is used to define the in-plane behavior of a fabric material under plane stress conditions. 

**Product: **Abaqus/Explicit  

**Type: **Model data  

**Level: **Model  

##### **References:**

- ["Fabric material behavior," Section 23.4.1 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-mat-cfabric)
- ["VFABRIC," Section 1.2.4 of the Abaqus User Subroutines Reference Guide](../sub/sub-link.md#sub-rtn-uexpfabric)
- [*DAMPING](ch04abk06.md)
- [*DENSITY](ch04abk13.md)
- [*DEPVAR](ch04abk14.md)
- [*INITIAL CONDITIONS](ch09abk18.md)
- [*ORIENTATION](ch15abk01.md)
- [*SECTION CONTROLS](ch18abk01.md)
- [*UNIAXIAL](ch20abk03.md)

### **Optional parameters: **

PROPERTIES

This parameter can be used only if the USER parameter is specified. 

Set this parameter equal to the number of property values needed as data in user subroutine [`VFABRIC`](../sub/sub-link.md#sub-xsl-vfabric). The default value is 0.

You can introduce state variables using the [*DEPVAR](ch04abk14.md) option and update these variables within user subroutine [`VFABRIC`](../sub/sub-link.md#sub-xsl-vfabric). You can delete the element, if needed, using one of these state variables. 

STRESS FREE INITIAL SLACK

Set STRESS FREE INITIAL SLACK=YES (default) to generate zero stresses in regions under initial compressive strains along the fill and the warp directions (these initial compressive strains may arise from modeling techniques such as the initial metric method—see [*INITIAL CONDITIONS](ch09abk18.md), TYPE=REF COORDINATE). The stress remains zero as the strain is continuously recovered from the initial compressive values toward the strain-free state. Once the initial slack is recovered, any subsequent compressive strains generate stresses as per the material definition.

Set STRESS FREE INITIAL SLACK=NO to generate stresses in the initial configuration as per the material definition even over fabric regions that are under compressive strains.

Abaqus also offers a technique to introduce any initial stresses, both tensile and compressive, in fabric materials gradually over a specified time period (see [*SECTION CONTROLS](ch18abk01.md)).

USER

Include this parameter if the fabric stresses in a local system are updated in user subroutine [`VFABRIC`](../sub/sub-link.md#sub-xsl-vfabric) given the total and the incremental fabric strains in the local system.

If this parameter is omitted, you must include the [*UNIAXIAL](ch20abk03.md) option to define the fabric response using test data in terms of the fabric stresses and the fabric strains in the local system.

The local system for the fabric material defined either through the test data or the user subroutine is initialized to the fill and the warp yarn directions in the reference configuration by using the [*ORIENTATION](ch15abk01.md) option. Abaqus updates this local system with deformation to track the fill and the warp directions in the current configuration.

### **Data lines to define the material properties for the USER fabric model: **

**No data lines are needed if the PROPERTIES parameter is omitted or set to 0. Otherwise, first line:**

Repeat this data line as often as necessary to define the material properties.




