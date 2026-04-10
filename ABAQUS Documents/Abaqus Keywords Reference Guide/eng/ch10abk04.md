# *JOINTED MATERIAL







### *JOINTED MATERIALSpecify the jointed material model.

This option is used to define a failure surface and the flow parameters for a single joint system or for bulk material failure in the elastic-plastic model of a jointed material, or it can be used to define shear retention in open joints. Up to three joint systems can be defined for each material point.

**Product: **Abaqus/Standard  

**Type: **Model data  

**Level: **Model  

##### **Reference:**

- ["Jointed material model," Section 23.5.1 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-mat-cjointedmat)

### **Optional parameters: **

DEPENDENCIES

Set this parameter equal to the number of field variable dependencies included in the definition of the parameters of the model, in addition to temperature. If this parameter is omitted, it is assumed that the parameters depend only on temperature. See ["Specifying field variable dependence" in "Material data definition," Section 21.1.2 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-mat-cmaterialdata-fvdepen), for more information.

JOINT DIRECTION

Set this parameter equal to the name of the [*ORIENTATION](ch15abk01.md) used to define the direction of a joint system. This use of the [*ORIENTATION](ch15abk01.md) option does not affect the output of components of stress and strain—it only defines the joint orientation in the original configuration. Omit this parameter to give the bulk material failure parameters. The JOINT DIRECTION parameter cannot be used with the SHEAR RETENTION parameter.

NO SEPARATION

Include this parameter to prevent the joint from opening. This parameter must be used in conjunction with the JOINT DIRECTION parameter.

SHEAR RETENTION

Include this parameter to define shear retention in open joints. If this parameter is omitted, zero shear retention is assumed. The SHEAR RETENTION parameter cannot be used with the JOINT DIRECTION parameter.

### **Data lines defining failure surface and flow parameters (SHEAR RETENTION omitted): **

**First line:**

**Subsequent lines (only needed if the DEPENDENCIES parameter has a value greater than four):**

Repeat this set of data lines as often as necessary to define the dependence of the failure and surface flow parameters on temperature and other predefined field variables.

### **Data lines defining the shear retention in open joints (SHEAR RETENTION included): **

**First line:**

**Subsequent lines (only needed if the DEPENDENCIES parameter has a value greater than six):**

Repeat this set of data lines as often as necessary to define the dependence of the shear retention on temperature and other predefined field variables.




