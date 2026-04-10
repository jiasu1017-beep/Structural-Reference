# *FLUID EXCHANGE PROPERTY







### *FLUID EXCHANGE PROPERTYDefine the fluid exchange property for flow in or out of a fluid cavity.

This option is used to define the fluid exchange property for flow between two fluid cavities or between a fluid cavity and its environment.

**Products: **Abaqus/Standard  Abaqus/Explicit  Abaqus/CAE  

**Type: **Model data  

**Level: **Model  

**Abaqus/CAE: **Interaction module

##### **References:**

- ["Fluid exchange definition," Section 11.5.3 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-anl-afluidcavityexchange)
- [*FLUID EXCHANGE](ch06abk21.md)

### **Required parameters: **

NAME

Set this parameter equal to a label that will be used to refer to the fluid exchange property.

TYPE

Set TYPE=BULK VISCOSITY to define fluid exchange where the mass flow rate is related to the pressure difference by both viscous and hydrodynamic resistance coefficients.

 Set TYPE=ENERGY FLUX to define fluid exchange by specifying the heat energy flow rate leakage explicitly. This parameter value applies only to Abaqus/Explicit analyses.

Set TYPE=ENERGY RATE LEAKAGE to define fluid exchange  by specifying the heat energy flow rate as a function of temperature difference and pressure. This parameter value applies only to Abaqus/Explicit analyses.

Set TYPE=FABRIC LEAKAGE to define fluid exchange due to fabric leakage. 

 Set TYPE=MASS FLUX to define fluid exchange by specifying the mass flow rate leakage explicitly. 

Set TYPE=MASS RATE LEAKAGE to define fluid exchange by specifying the mass flow rate as a function of pressure difference and temperature. 

Set TYPE=ORIFICE to define fluid exchange through a vent orifice. This parameter value applies only to Abaqus/Explicit analyses.

Set TYPE=VOLUME FLUX to define fluid exchange  by specifying the volume rate leakage explicitly.

Set TYPE=VOLUME RATE LEAKAGE to define fluid exchange  by specifying the volume rate leakage as a function of pressure difference and temperature.

Set TYPE=USER to indicate that user subroutine [`VUFLUIDEXCH`](../sub/sub-link.md#sub-xsl-vufluidexch) is used in Abaqus/Explicit to define fluid exchange by specifying the mass flow rate and/or heat energy flow rate. 

### **Optional parameters: **

CONSTANTS

This parameter applies only to Abaqus/Explicit analyses.

Set this parameter equal to the number of constant values needed as data to define the fluid exchange in user subroutine [`VUFLUIDEXCH`](../sub/sub-link.md#sub-xsl-vufluidexch). The default is CONSTANTS=0.

DEPENDENCIES

Set this parameter equal to the number of field variables included in the specification of the coefficients defined by the TYPE parameter. If this parameter is omitted, the coefficients are assumed not to depend on any field variables. 

DEPVAR

This parameter applies only to Abaqus/Explicit analyses.

Set this parameter equal to the number of solution-dependent state variables required for user subroutine [`VUFLUIDEXCH`](../sub/sub-link.md#sub-xsl-vufluidexch). The default is DEPVAR=0. 

### **Data lines for TYPE=BULK VISCOSITY: **

**First line:**

**Subsequent lines (only needed if the DEPENDENCIES parameter has a value greater than four):**

Repeat this set of data lines as often as necessary to specify the viscous and hydrodynamic resistance coefficients as functions of average absolute pressure, average temperature, and other predefined field variables.

### **Data line for TYPE=ENERGY FLUX: **

**First (and only) line:**

### **Data lines for TYPE=ENERGY RATE LEAKAGE: **

**First line:**

**Subsequent lines (only needed if the DEPENDENCIES parameter has a value greater than four):**

Repeat this set of data lines as often as necessary to define the heat energy flow rate as a function of temperature difference, average absolute pressure, average temperature, and other predefined field variables. 

### **Data lines for TYPE=FABRIC LEAKAGE or TYPE=ORIFICE: **

**First line:**

**Subsequent lines (only needed if the DEPENDENCIES parameter has a value greater than five):**

Repeat this set of data lines as often as necessary to define the discharge coefficient as a function of pressure, temperature, and other predefined field variables. 

### **Data line for TYPE=MASS FLUX: **

**First (and only) line:**

### **Data lines for TYPE=MASS RATE LEAKAGE: **

**First line:**

**Subsequent lines (only needed if the DEPENDENCIES parameter has a value greater than four):**

Repeat this set of data lines as often as necessary to specify the mass flow rate as a function of pressure difference, average absolute pressure, average temperature, and other predefined field variables.

### **Data line for TYPE=VOLUME FLUX: **

**First (and only) line:**

### **Data lines for TYPE=VOLUME RATE LEAKAGE: **

**First line:**

**Subsequent lines (only needed if the DEPENDENCIES parameter has a value greater than four):**

Repeat this set of data lines as often as necessary to define the volume rate leakage as a function of pressure difference, average absolute pressure, average temperature, and other predefined field variables. 

### **Data lines for TYPE=USER: **

**First line:**

Repeat this data line as often as necessary to define all fluid exchange constants. 




