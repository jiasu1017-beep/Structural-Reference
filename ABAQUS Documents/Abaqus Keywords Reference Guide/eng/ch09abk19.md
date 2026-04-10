# *INSTANCE







### *INSTANCEBegin an instance definition.

This option is used to instance a part within an assembly. It must be used in conjunction with the [*ASSEMBLY](ch01abk14.md) and [*END INSTANCE](ch05abk17.md) options. If the instance is not imported from a previous analysis, the [*INSTANCE](ch09abk19.md) option must be used in conjunction with the [*PART](ch16abk04.md) option. When importing a part instance from a previous analysis, the [*INSTANCE](ch09abk19.md) option must be used in conjunction with the [*IMPORT](ch09abk04.md) option.

**Products: **Abaqus/Standard  Abaqus/Explicit  Abaqus/CFD  Abaqus/CAE  

**Type: **Model data  

**Level: **Assembly  

**Abaqus/CAE: **Assembly module for part instances not imported from a previous analysis; Load module for part instances imported from a previous analysis

##### **References:**

- ["Defining an assembly," Section 2.10.1 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-int-ipartassy)
- ["Transferring results between Abaqus analyses: overview," Section 9.2.1 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-anl-atransferoverview)
- [*END INSTANCE](ch05abk17.md)
- [*IMPORT](ch09abk04.md)

### **Required parameters if the instance is not imported from a previous analysis: **

NAME

 Set this parameter equal to a label that will be used to refer to the instance.

PART

Set this parameter equal to the name of the part being instanced.

### **Required parameter if the instance is to be imported from a previous analysis: **

INSTANCE

 Set this parameter equal to the name of the instance to be imported from the previous analysis.

### **Optional import parameter: **

LIBRARY

Set this parameter equal to the name of the previous analysis from which the instance should be imported. The previous analysis output database (`.odb`) file should reside in the current (working) directory. If the LIBRARY parameter is omitted, the job name of the previous analysis must be specified on the command line using the **oldjob** parameter (see ["Abaqus/Standard, Abaqus/Explicit, and Abaqus/CFD execution," Section 3.2.2 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-int-danalysisproc)). If both methods are used, the command line specification will take precedence over the LIBRARY parameter.

### **Data line to translate an instance that is not imported from a previous analysis: **

**First (and only) line:**

### **Data lines to translate and/or rotate an instance that is not imported from a previous analysis: **

**First line:**

Enter values of zero to apply a pure rotation.

**Second line:**

If both translation and rotation are specified, translation is applied before rotation.

### **There are no data lines for an instance that is imported from a previous analysis. **

**Figure 9.19–1** Rotation of an instance.

![](../graphics/ksuperprop-rot.png)




