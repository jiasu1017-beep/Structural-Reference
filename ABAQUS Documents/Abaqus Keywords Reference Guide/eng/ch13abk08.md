# *MATERIAL







### *MATERIALBegin the definition of a material.

This option is used to indicate the start of a material definition.

**Products: **Abaqus/Standard  Abaqus/Explicit  Abaqus/CFD  Abaqus/CAE  

**Type: **Model data  

**Level: **Model  

**Abaqus/CAE: **Property module

##### **Reference:**

- ["Material data definition," Section 21.1.2 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-mat-cmaterialdata)

### **Required parameter: **

NAME

Set this parameter equal to a label that will be used to refer to the material in the element property options. Material names in the same input file must be unique. Furthermore, material names should be unique from the names associated with property definitions such as [*CONNECTOR BEHAVIOR](ch03abk35.md) and [*FLUID BEHAVIOR](ch06abk16.md). Material names adhere to the naming convention for labels (see ["Input syntax rules," Section 1.2.1 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-int-iinputsyntax)), except that they cannot begin with a number.

### **Optional parameters: **

RTOL

This parameter applies only to Abaqus/Explicit analyses.

Set this parameter equal to the tolerance to be used for regularizing the material data. The default is RTOL=0.03.

SRATE FACTOR

This parameter applies only to Abaqus/Explicit analyses.

Set this parameter equal to the factor used for filtering the equivalent plastic strain rate for the evaluation of strain rate-dependent material data. The default value is 0.9.

STRAIN RATE REGULARIZATION

This parameter applies only to Abaqus/Explicit analyses and is used only to regularize strain rate-dependent material data.

Set STRAIN RATE REGULARIZATION=LOGARITHMIC (default) to use a logarithmic regularization for strain rate-dependent material data. 

Set STRAIN RATE REGULARIZATION=LINEAR to use a linear regularization for strain rate-dependent material data.

**There are no data lines associated with this option.**



