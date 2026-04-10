# *PERIODIC MEDIA







### *PERIODIC MEDIASpecify a periodic media.

This option is used to specify a periodic media.

**Product: **Abaqus/Explicit  

**Type: **Model data  

**Level: **Model  

##### **Reference:**

- ["Periodic media analysis," Section 10.5.1 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-anl-aperiodicmedia)

### **Required parameters: **

INLET CONTROL NODE

Set this parameter equal to either the node number of the inlet control node or the name of a node set containing the inlet control node. If a node set name is chosen, the node set must contain exactly one node.

NAME

Set this parameter equal to the name of the periodic media.

ORIENTATION

Set this parameter equal to the name of an orientation definition (["Orientations," Section 2.2.5 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-int-corientation)) used to define the trigger plane for periodic media block shuffling. The local *z*-axis is perpendicular to the trigger plane and points in the same direction as the media transport.

OUTLET CONTROL NODE

Set this parameter equal to either the node number of the outlet control node or the name of a node set containing the outlet control node. If a node set name is chosen, the node set must contain exactly one node.

TRIGGER NODE

Set this parameter equal to either the node number of the trigger node or the name of a node set containing the trigger node. If a node set name is chosen, the node set must contain exactly one node. The trigger plane is defined via a combination of trigger node location and the specified orientation.

### **Data lines to define a periodic media: **

**First line:**

Repeat this data line as often as necessary. Use one data line for each section of periodic media. The order of the periodic section is from inlet to outlet.




