# *CONTACT INITIALIZATION DATA







### *CONTACT INITIALIZATION DATADefine contact initialization methods for general contact.

This option is used to define contact initialization methods for Abaqus/Standard. The contact initialization method is applied to a contact interaction using the [*CONTACT INITIALIZATION ASSIGNMENT](ch03abk64.md) option.

**Products: **Abaqus/Standard  Abaqus/CAE  

**Type: **Model data  

**Level: **Model  

**Abaqus/CAE: **Interaction module

##### **References:**

- ["Controlling initial contact status in Abaqus/Standard," Section 36.2.4 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-cni-agenlcontinitializationstd)
- ["Common difficulties associated with contact modeling in Abaqus/Standard," Section 39.1.2 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-cni-acontacttrouble)
- [*CONTACT](ch03abk54.md)
- [*CONTACT INITIALIZATION ASSIGNMENT](ch03abk64.md)

### **Required parameter: **

NAME

Set this parameter equal to a label that will be used to refer to this contact initialization method.

### **Optional, mutually exclusive parameters: **

INITIAL CLEARANCE

Set this parameter equal to a positive value to specify an initial clearance distance.

INTERFERENCE FIT

Include this parameter without setting it to a value to treat initial overclosures as interference fits.

Set this parameter equal to a positive value to specify an interference distance.

If this parameter is omitted, initial overclosures are resolved with strain-free adjustments.

### **Optional parameters: **

MINIMUM DISTANCE

Set MINIMUM DISTANCE=YES (default) to automatically activate localized contact damping when nearby surfaces are touching at only a single point. 

Set MINIMUM DISTANCE=NO to forgo this automatic localized damping.

SEARCH ABOVE

Set this parameter equal to a positive value to ensure that the search zone for contact initialization includes gaps at least as large as the specified value.

SEARCH BELOW

Set this parameter equal to a positive value to ensure that the search zone for contact initialization includes overclosures at least as large as the specified value.

**There are no data lines associated with this option.**



