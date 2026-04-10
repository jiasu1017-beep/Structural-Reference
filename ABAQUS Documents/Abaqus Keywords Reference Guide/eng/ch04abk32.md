# *DOMAIN DECOMPOSITION







### *DOMAIN DECOMPOSITIONDefine a region for domain decomposition and/or define constraints on the domain decomposition.

This option is used to define a domain decomposition region and/or to define constraints on the domain decomposition.

**Product: **Abaqus/Explicit  

**Type: **Model data  

**Level: **Assembly  

##### **Reference:**

- ["Parallel execution in Abaqus/Explicit," Section 3.5.3 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-int-aparallelexecution)

### **Optional parameter: **

ELSET

Set this parameter equal to the name of the element set to define a domain decomposition region. This element set will be split into the user-specified number of parallel domains. If this parameter is omitted, this domain decomposition region will include all elements not included in other domain decomposition regions.

### **Data lines to define constraints on domain decomposition: **

**First line:**

Repeat this data line as often as necessary to define constraints on the domain decomposition.




