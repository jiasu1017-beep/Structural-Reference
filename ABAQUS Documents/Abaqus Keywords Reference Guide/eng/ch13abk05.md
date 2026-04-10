# *MASS ADJUST







### *MASS ADJUSTAdjust and/or redistribute the mass of an element set.

This option is used to either increase or decrease uniformly the mass of the elements in an element set so that the total mass for that set matches a specified value. It can also be used to redistribute the mass among the elements in the element set to raise the minimum stable time increment for that set to a specified target value. Mass can be adjusted for multiple element sets; the mass is adjusted in the order in which the element sets are specified. This behavior influences the final outcome for element sets that share elements. This option can appear only once in an analysis.

**Product: **Abaqus/Explicit  

**Type: **Model data  

**Level: **Assembly  

##### **Reference:**

- ["Adjust and/or redistribute mass of an element set," Section 2.6.1 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-int-amassadjust)

### **Optional parameter: **

TARGET DT

Set this parameter equal to a default minimum element stable time increment for all of the mass-adjusted element sets. Individualized target time increments can be specified for selected sets, if needed. A nonzero target value causes redistribution of mass within the element sets. If this parameter is omitted, mass redistribution occurs only for element sets for which a minimum element stable time increment value is specified on the data lines.

### **Data lines to adjust and/or redistribute the mass of element sets: **

**First line:**

Repeat this data line as often as necessary to adjust the mass for different element sets. The same element set label cannot be entered more than once. The mass is adjusted in the order the element sets are specified on the data lines. 




