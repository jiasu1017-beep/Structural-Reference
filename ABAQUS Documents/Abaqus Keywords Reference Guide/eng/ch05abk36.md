# *EXTREME NODE VALUE







### *EXTREME NODE VALUEDefine nodal variables to be monitored.

This option is used to define nodal variables that are to be monitored and compared with user-specified values. It must be used in conjunction with the [*EXTREME VALUE](ch05abk37.md) option.

**Product: **Abaqus/Explicit  

**Type: **History data 

**Level: **Step

##### **References:**

- ["Explicit dynamic analysis," Section 6.3.3 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-anl-aexpdynamic)
- [*EXTREME VALUE](ch05abk37.md)

### **Required parameter: **

NSET

Set this parameter equal to the name of the node set in which the variables are to be monitored.

### **Required, mutually exclusive parameters: **

ABS

Include this parameter if the user-specified value is to be the upper bound for the absolute value of the variable. At every increment Abaqus/Explicit will check whether the absolute value of the variable has exceeded the specified value.

MAX

Include this parameter if the user-specified value is to be the upper bound for the variable. At every increment Abaqus/Explicit will check whether the variable has exceeded the specified value.

MIN

Include this parameter if the user-specified value is to be the lower bound for the variable. At every increment Abaqus/Explicit will check whether the variable has fallen below the specified value.

### **Optional parameter: **

OUTPUT

Set OUTPUT=YES (default) if the requested field-type output to the output database and an additional restart state are to be written when any variable value exceeds the user-specified bounds for the first time. The output will be written in the increment following the one in which such an occurrence took place.

Set OUTPUT=NO to prevent any output from being written.

### **Data lines to define nodal variables and the maxima or minima: **

**First line:**

Repeat the data line as often as necessary to define additional variables to be monitored and their maxima or minima.




