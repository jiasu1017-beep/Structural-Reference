# *CONTACT RESPONSE







### *CONTACT RESPONSEDefine contact responses for design sensitivity analysis.

This option is used to write contact response sensitivities to the output database. It must be used in conjunction with the [*DESIGN RESPONSE](ch04abk17.md) option.

**Product: **Abaqus/Design  

**Type: **History data 

**Level: **Step

##### **References:**

- ["Design sensitivity analysis," Section 19.1.1 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-anl-adsa)
- [*DESIGN RESPONSE](ch04abk17.md)

### **Optional parameters: **

MASTER

Set this parameter equal to the name of the master surface for which this output request is being made.

NSET

Set this parameter equal to the name of the node set for which this output request is being made. 

SLAVE

Set this parameter equal to the name of the slave surface for which this output request is being made.

### **Data lines to request contact sensitivity output: **

**First line:**

Repeat this data line as often as necessary to define the contact responses whose sensitivities are to be written to the output database.




