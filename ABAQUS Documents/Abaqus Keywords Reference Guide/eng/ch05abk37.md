# *EXTREME VALUE







### *EXTREME VALUEDefine element and nodal variables to be monitored.

This option is used in conjunction with the [*EXTREME ELEMENT VALUE](ch05abk35.md) and/or the [*EXTREME NODE VALUE](ch05abk36.md) options to indicate that nodal and element variables are to be monitored in the current step and compared with user-specified values. For each variable specified with these options, the maximum, minimum, or absolute maximum value attained during the course of the analysis and the associated element or node number will be written to the status (`.sta`) file at the end of the step. Use the [*EXTREME VALUE](ch05abk37.md) option without the [*EXTREME ELEMENT VALUE](ch05abk35.md) or [*EXTREME NODE VALUE](ch05abk36.md) options and without any parameters to stop monitoring variables in a new step.

**Product: **Abaqus/Explicit  

**Type: **History data 

**Level: **Step

##### **References:**

- ["Explicit dynamic analysis," Section 6.3.3 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-anl-aexpdynamic)
- [*EXTREME ELEMENT VALUE](ch05abk35.md)
- [*EXTREME NODE VALUE](ch05abk36.md)

### **Optional parameter: **

HALT

Set HALT=NO (default) if the analysis should continue even if the variables have exceeded the user-specified bounds.

Set HALT=YES to stop the analysis at the first occurrence of a variable exceeding its user-specifed bound. The analysis will be stopped after the increment following the one in which such an occurrence took place.

**There are no data lines associated with this option.**



