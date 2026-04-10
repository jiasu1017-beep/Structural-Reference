# *SUBSTRUCTURE LOAD CASE







### *SUBSTRUCTURE LOAD CASEBegin the definition of a substructure load case.

This option is used to begin the definition of a substructure load case for the substructure currently being generated. It can be used only in a [*SUBSTRUCTURE GENERATE](ch18abk42.md) analysis.

**Products: **Abaqus/Standard  Abaqus/CAE  

**Type: **History data 

**Level: **This option is not supported in a model defined in terms of an assembly of part instances.

##### **References:**

- ["Defining substructures," Section 10.1.2 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-anl-asuperelementdef)
- [*SLOAD](ch18abk20.md)

### **Required parameter: **

NAME

Set this parameter equal to a label that will be used to refer to the load case in [*SLOAD](ch18abk20.md) option specifications when applying loads to the substructure during an analysis.

### **To define the loads: **

Enter any mechanical loading options (["Concentrated loads," Section 34.4.2 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-prc-ploadgeneral), and ["Distributed loads," Section 34.4.3 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-prc-ploaddistributed)) or thermal loading options (["Thermal loads," Section 34.4.4 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-prc-pthermal)) to define the loads forming the load case. Specify a magnitude for each load. This magnitude will be scaled by a magnitude and amplitude reference specified in the [*SLOAD](ch18abk20.md) option. The load case definition continues until an option is encountered that is not one of the loading options. If boundary conditions are included in a [*SUBSTRUCTURE LOAD CASE](ch18abk43.md), they are always active, even if the [*SLOAD](ch18abk20.md) option is not used.




