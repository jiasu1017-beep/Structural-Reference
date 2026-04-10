# *DISPLAY BODY







### *DISPLAY BODY Define a part instance that will be used for display only.

This option is used to specify that a part instance should be used for display purposes only and should not take part in the analysis. This option must be used in conjunction with the [*ASSEMBLY](ch01abk14.md) and [*INSTANCE](ch09abk19.md) options.

**Products: **Abaqus/Standard  Abaqus/Explicit  Abaqus/CAE  

**Type: **Model data  

**Level: **Assembly  

**Abaqus/CAE: **Interaction module

##### **Reference:**

- ["Display body definition," Section 2.9.1 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-int-adisplaybody)

### **Required parameter: **

INSTANCE

Set this parameter to the name of the part instance that is to be considered a display body.

### **Data line to specify the reference nodes (optional; if no data line is given, the display body will remain stationary during the analysis): **

**First (and only) line:**




