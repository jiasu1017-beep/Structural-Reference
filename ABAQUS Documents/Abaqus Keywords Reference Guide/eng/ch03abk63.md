# *CONTACT INCLUSIONS







### *CONTACT INCLUSIONSSpecify self-contact surfaces or surface pairings to include in the general contact domain.

This option is used to specify the self-contact surfaces and surface pairings that should be considered by the general contact algorithm. It should be used in conjunction with the [*CONTACT](ch03abk54.md) option.

**Products: **Abaqus/Standard  Abaqus/Explicit  Abaqus/CAE  

**Type: **Model data in Abaqus/Standard; Model or history data in Abaqus/Explicit  

**Level: **Model in Abaqus/Standard; Model or Step in Abaqus/Explicit  

**Abaqus/CAE: **Interaction module

##### **References:**

- ["Defining general contact interactions in Abaqus/Standard," Section 36.2.1 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-cni-acontactgeneralstd)
- ["Defining general contact interactions in Abaqus/Explicit," Section 36.4.1 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-cni-acontactgeneral)
- [*CONTACT](ch03abk54.md)

### **Optional parameter: **

ALL EXTERIOR

Include this parameter to specify self-contact for a default unnamed, all-inclusive surface that includes all element-based surface facets and, in Abaqus/Explicit only, all analytical rigid surfaces. This is the simplest way to define the contact domain. The option should have no data lines when this parameter is used.

If this parameter is omitted, the contact surfaces must be specified on the data lines.

### **Data lines to specify contact inclusions if the ALL EXTERIOR parameter is omitted: **

**First line:**

Repeat this data line as often as necessary.




