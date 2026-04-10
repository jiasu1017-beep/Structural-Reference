# *FLUID INFLATOR PROPERTY







### *FLUID INFLATOR PROPERTYDefine a fluid inflator property.

This option is used to define a fluid inflator property to model the deployment of an airbag. 

**Product: **Abaqus/Explicit  

**Type: **Model data  

**Level: **Part,  Part instance  

##### **References:**

- ["Inflator definition," Section 11.5.4 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-anl-afluidinflator)
- [*FLUID INFLATOR](ch06abk26.md)

### **Required parameters: **

EFFECTIVE AREA

This parameter is relevant only for TYPE=DUAL PRESSURE and TYPE=PRESSURE AND MASS.

Set this parameter equal to the total inflator orifice area.

NAME

Set this parameter equal to a label that will be used to refer to the fluid inflator property.

TANK VOLUME

 This parameter is relevant only for TYPE=DUAL PRESSURE or TYPE=TANK TEST.

Set this parameter equal to the tank volume.

TYPE

Set TYPE=DUAL PRESSURE to use the dual pressure method to obtain the mass flow rate of the gas species.

Set TYPE=PRESSURE AND MASS to use the given mass flow rate and inflator pressure to obtain the gas temperature.

Set TYPE=TANK TEST to use tank test data to obtain the mass flow rate of the gas species.

Set TYPE=TEMPERATURE AND MASS to use the given mass flow rate and inflator gas temperature to obtain the gas pressure.

### **Optional parameter: **

DISCHARGE COEFFICIENT

This parameter is relevant only for TYPE=DUAL PRESSURE and TYPE=PRESSURE AND MASS.

Set this parameter equal to the discharge coefficient of the inflator orifice. The default value is 0.4. 

### **Data lines for TYPE=DUAL PRESSURE: **

**First line:**

Repeat this data line as often as necessary to define the inflator pressure and tank pressure as functions of inflation time.

### **Data lines for TYPE=PRESSURE AND MASS: **

**First line:**

Repeat this data line as often as necessary to define the inflator pressure and inflator mass flow rate as functions of inflation time.

### **Data lines for TYPE=TANK TEST: **

**First line:**

Repeat this data line as often as necessary to define the inflator gas temperature and tank pressure as functions of inflation time.

### **Data lines for TYPE=TEMPERATURE AND MASS: **

**First line:**

Repeat this data line as often as necessary to define the inflator gas temperature and inflator mass flow rate as functions of inflation time.




