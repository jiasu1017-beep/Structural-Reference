# *SUBSTRUCTURE COPY







### *SUBSTRUCTURE COPYCopy a substructure definition.

This option is used to copy a substructure definition from one library to another or from one substructure identifier to another within one library.

**Product: **Abaqus/Standard  

**Type: **Model data  

**Level: **This option is not supported in a model defined in terms of an assembly of part instances.

##### **Reference:**

- ["Using substructures," Section 10.1.1 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-anl-asuperelements)

### **Required parameters: **

NEW TYPE

Set this parameter equal to the TYPE identifier of the substructure being created.

OLD TYPE

Set this parameter equal to the TYPE identifier of the substructure being copied.

### **Optional parameters: **

NEW LIBRARY

Set this parameter equal to the name of the substructure library in which the substructure is stored. The default library name is *jobname*.

OLD LIBRARY

Set this parameter equal to the name of the substructure library from which the substructure is being copied. The default library name is *jobname*.

**There are no data lines associated with this option.**



