# *DYNAMIC TEMPERATURE-DISPLACEMENT







### *DYNAMIC TEMPERATURE-DISPLACEMENTDynamic coupled thermal-stress analysis using explicit integration.

This option is used to indicate that a dynamic coupled thermal-stress analysis is to be performed using explicit integration.

**Products: **Abaqus/Explicit  Abaqus/CAE  

**Type: **History data 

**Level: **Step

**Abaqus/CAE: **Step module

##### **Reference:**

- ["Fully coupled thermal-stress analysis," Section 6.5.3 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-anl-acouptempdisp)

### **Required parameter: **

EXPLICIT

Include this parameter to specify explicit time integration.

### **Optional, mutually exclusive parameters: **

DIRECT USER CONTROL

Include this parameter to specify that this step should use a fixed time increment that is specified by the user.

ELEMENT BY ELEMENT

Include this parameter to indicate that variable, automatic time incrementation using the element-by-element stable time increment estimates should be used. This method will generally require more increments and more computational time than the global time estimator.

FIXED TIME INCREMENTATION

Include this parameter to specify that this step should use a fixed time increment that will be determined by Abaqus/Explicit at the beginning of the step using the element-by-element time estimator.

### **Optional parameters: **

IMPROVED DT METHOD

Set IMPROVED DT METHOD=YES (default) to use the “improved” method to estimate the element stable time increment due to the mechanical response for three-dimensional continuum elements and elements with plane stress formulations (shell, membrane, and two-dimensional plane stress elements). 

Set IMPROVED DT METHOD=NO to use the conservative method to estimate the element stable time increment due to the mechanical response for  three-dimensional continuum elements and elements with plane stress formulations. 

SCALE FACTOR

Set this parameter equal to the factor that is used to scale the time increment computed by Abaqus/Explicit. The default scaling factor is 1.0. This parameter can be used to scale the default global time estimate, and it can be used in conjunction with the ELEMENT BY ELEMENT and FIXED TIME INCREMENTATION parameters. It cannot be used in conjunction with the DIRECT USER CONTROL parameter.

### **Data line for automatic time incrementation (global or ELEMENT BY ELEMENT estimation): **

**First (and only) line:**

### **Data line for fixed time incrementation using DIRECT USER CONTROL: **

**First (and only) line:**

### **Data line for fixed time incrementation using FIXED TIME INCREMENTATION: **

**First (and only) line:**




