# *ELEMENT RESPONSE







### *ELEMENT RESPONSEDefine element responses for design sensitivity analysis.

This option is used to write element response sensitivities calculated at the integration points to the output database. It must be used in conjunction with the [*DESIGN RESPONSE](ch04abk17.md) option.

**Product: **Abaqus/Design  

**Type: **History data 

**Level: **Step

##### **References:**

- ["Design sensitivity analysis," Section 19.1.1 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-anl-adsa)
- [*DESIGN RESPONSE](ch04abk17.md)

### **Optional parameter: **

ELSET

Set this parameter equal to the name of the element set for which this sensitivity output is being made.

### **Data lines to request element sensitivity output: **

**First line:**

Repeat this data line as often as necessary to define the element responses whose sensitivities are to be written to the output database.




