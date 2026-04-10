# *STEADY STATE DETECTION







### *STEADY STATE DETECTIONSpecify steady-state requirements for terminating a quasi-static uni-directional simulation.

This option is used to define the conditions that must be satisfied to determine that steady state has been reached. It must be used in conjunction with the [*STEADY STATE CRITERIA](ch18abk32.md) option.

**Product: **Abaqus/Explicit  

**Type: **History data 

**Level: **Step

##### **References:**

- ["Steady-state detection," Section 11.8.1 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-anl-asteadystatedetection)
- ["Output to the output database," Section 4.1.3 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-out-odboutput)
- [*STEADY STATE CRITERIA](ch18abk32.md)

### **Required parameters: **

ELSET

Set this parameter equal to the name of the element set for which this steady-state detection definition is being applied.

SAMPLING

This parameter is used to specify the method used to sample all steady-state norms associated with this option. See ["Steady-state detection," Section 11.8.1 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-anl-asteadystatedetection), for more information regarding steady-state norm definitions.

Set SAMPLING=PLANE BY PLANE to calculate the steady-state norms as each plane of elements crosses the exit plane. This method should be used only for non-Eulerian analyses with uniform planes of elements sequentially passing the exit plane. 

Set SAMPLING=UNIFORM to calculate the steady-state norms at an interval defined by the time required for material to flow through an element of average length. This interval is determined at the beginning of the step and remains constant throughout the step. This method should be used only for analyses with material flowing in and out of Eulerian boundary regions in the primary direction.

### **Data line to define primary direction and cutting plane position: **

**First (and only) line:**




