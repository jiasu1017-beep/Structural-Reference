# *FIXED MASS SCALING







### *FIXED MASS SCALING Specify mass scaling at the beginning of the step.

This option is used to specify mass scaling at the beginning of the step for part or all of the model.

**Products: **Abaqus/Explicit  

**Type: **History data 

**Level: **Step

**Abaqus/CAE: **Step module

##### **References:**

- ["Mass scaling," Section 11.6.1 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-anl-amassscaling)
- ["Output," Section 4.1.1 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-out-ooutput)

### **Optional parameters: **

DT

Set this parameter equal to the desired element stable time increment for the element set provided. This parameter must be used in conjunction with the TYPE parameter to define how the mass scaling is to be applied.

If both the FACTOR and DT parameters are omitted, a default mass scaling value of 1.0 is used. If both parameters are included, the mass is first scaled by the value assigned to the FACTOR parameter and then possibly scaled again, depending on the values assigned to the DT and TYPE parameters.

ELSET

Set this parameter equal to the name of the element set for which this mass scaling definition is being applied. If this parameter is omitted, the mass scaling definition will apply to all elements in the model.

The [*FIXED MASS SCALING](ch06abk13.md) option can be repeated with different ELSET definitions to define different mass scaling for the specified element sets.

FACTOR

Set this parameter equal to the mass scaling factor. The masses of the elements will be scaled once at the beginning of the step by the value assigned to the FACTOR parameter.

If both the FACTOR and DT parameters are omitted, a default mass scaling value of 1.0 is used. If both parameters are included, the mass is first scaled by the value assigned to the FACTOR parameter and then possibly scaled again, depending on the values assigned to the DT and TYPE parameters.

TYPE

Set TYPE=UNIFORM to scale the masses of the elements equally so that the smallest element stable time increment of the scaled elements equals the value assigned to DT.

Set TYPE=BELOW MIN (default) to scale the masses of only the elements whose element stable time increments are less than the value assigned to DT. The masses of these elements will be scaled so that the element stable time increments equal the value assigned to DT.

Set TYPE=SET EQUAL DT to scale the masses of all elements so that they all have the same element stable time increment equal to the value assigned to DT.

**There are no data lines associated with this option.**



