# *VARIABLE MASS SCALING







### *VARIABLE MASS SCALINGSpecify mass scaling during the step.

This option is used to specify mass scaling during the step for part or all of the model.

**Products: **Abaqus/Explicit  

**Type: **History data 

**Level: **Step

**Abaqus/CAE: **Step module

##### **References:**

- ["Mass scaling," Section 11.6.1 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-anl-amassscaling)
- ["Output," Section 4.1.1 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-out-ooutput)

### **Optional parameters: **

DT

Set this parameter equal to the desired element stable time increment for the element set provided. The mass scaling is applied according to the method specified with the TYPE parameter. If the DT parameter is omitted, all variable mass scaling definitions from previous steps are removed, and the scaled mass matrix from the end of the previous step is carried over to the current step.

ELSET

Set this parameter equal to the name of the element set for which this mass scaling definition is being applied. If this parameter is omitted, the mass scaling definition will apply to all elements in the model.

The [*VARIABLE MASS SCALING](ch21abk01.md) option can be repeated with different ELSET definitions to define different mass scaling for the specified element sets.

TYPE

Set TYPE=UNIFORM to scale the masses of the elements equally so that the smallest element stable time increment of the scaled elements equals the value assigned to DT.

Set TYPE=BELOW MIN (default) to scale the masses of only the elements whose element stable time increments are less than the value assigned to DT. The masses of these elements will be scaled so that the element stable time increments equal the value assigned to DT.

Set TYPE=SET EQUAL DT to scale the masses of all elements so that they have the same element stable time increment equal to the value assigned to DT.

Set TYPE=ROLLING to scale the element masses automatically for the simulation of a rolling process. The appropriate value for the target stable time increment is determined by Abaqus from several parameters of the rolling process. The DT parameter will be ignored in this case.

### **Required, mutually exclusive parameters if the DT parameter or the TYPE=ROLLING parameter is used: **

FREQUENCY

Set this parameter equal to the frequency, in increments, at which mass scaling calculations are to be performed during the step. For example, FREQUENCY=5 will scale the mass at the beginning of the step and at increments 5, 10, 15, etc. The value of this parameter must be a positive integer.

NUMBER INTERVAL

Set this parameter equal to the number of intervals during the step at which mass scaling calculations will be performed. For example, if NUMBER INTERVAL=2, mass scaling calculations will be performed at the beginning of the step, the increment immediately following the half-way point in the step, and the final increment in the step.

### **Required parameters for TYPE=ROLLING: **

CROSS SECTION NODES

Set this parameter equal to the number of nodes in the cross-section of the workpiece. Increasing this value will decrease the amount of mass scaling used. 

EXTRUDED LENGTH

Set this parameter equal to the average element length in the rolling direction.

FEED RATE

Set this parameter equal to the estimated average velocity of the workpiece in the rolling direction at steady-state conditions.

**There are no data lines associated with this option.**



