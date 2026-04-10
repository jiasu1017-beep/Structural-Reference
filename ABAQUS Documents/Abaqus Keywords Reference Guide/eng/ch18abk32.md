# *STEADY STATE CRITERIA







### *STEADY STATE CRITERIASpecify steady-state criteria for terminating a quasi-static uni-directional simulation.

This option is used to specify the norms that must be satisfied to halt a quasi-static uni-directional simulation based on achieving a steady-state condition. It must be used in conjunction with the [*STEADY STATE DETECTION](ch18abk33.md) option.

**Product: **Abaqus/Explicit  

**Type: **History data 

**Level: **Step

##### **References:**

- ["Output to the output database," Section 4.1.3 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-out-odboutput)
- ["Steady-state detection," Section 11.8.1 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-anl-asteadystatedetection)
- [*STEADY STATE DETECTION](ch18abk33.md)

**There are no parameters associated with this option.**

### **Data lines to define steady-state detection norms SSPEEQ and SSSPRD: **

**First line:**

Repeat this data line as often as necessary. Each line defines a criterion that must be satisfied to achieve steady state.

### **Data lines to define steady-state detection norms SSFORC and SSTORQ: **

**First line:**

Repeat this data line as often as necessary. Each line defines a criterion that must be satisfied to achieve steady state.




