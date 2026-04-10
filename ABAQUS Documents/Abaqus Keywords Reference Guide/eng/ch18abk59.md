# *SYSTEM







### *SYSTEMSpecify a local coordinate system in which to define nodes.

This option is used to define nodes by accepting coordinates relative to a specified local rectangular coordinate system and generating the nodal coordinates in the global coordinate system.

**Products: **Abaqus/Standard  Abaqus/Explicit  Abaqus/CFD  Abaqus/CAE  

**Type: **Model data  

**Level: **Part,  Part instance  

**Abaqus/CAE: **Not applicable; instancing a part in the Assembly module creates a local coordinate system. 

##### **Reference:**

- ["Node definition," Section 2.1.1 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-int-inode)

**There are no parameters associated with this option.**

### **Data lines to define a local coordinate system: **

**First line:**

**Second line (optional; if not provided, the *Z*-axis direction remains unchanged, and the ![](../graphics/key_eqn01097.gif)-axis is projected onto the ![](../graphics/key_eqn01033.gif) plane):**

**Figure 18.59–1** Local coordinate system.

![](../graphics/ksystem-nls.png)




