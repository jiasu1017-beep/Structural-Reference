# *NONSTRUCTURAL MASS







### *NONSTRUCTURAL MASSSpecify mass contribution to the model from nonstructural features.

This option is used to include the mass contribution from nonstructural features in the model. The nonstructural mass can be applied over an element set that contains solid, shell, membrane, surface, beam, or truss elements.

**Products: **Abaqus/Standard  Abaqus/Explicit  Abaqus/CAE  

**Type: **Model data  

**Level: **Part,  Part instance,  Assembly  

**Abaqus/CAE: **Property module and Interaction module.

##### **Reference:**

- ["Nonstructural mass definition," Section 2.7.1 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-int-anonstructuralmass)

### **Required parameters: **

ELSET

Set this parameter equal to the name of the element set containing the elements over which a given nonstructural mass is to be distributed.

UNITS

Set UNITS=TOTAL MASS to specify the nonstructural mass in the units of “mass.”

Set UNITS=MASS PER VOLUME to specify the nonstructural mass in the units of  “mass per unit volume.”

Set UNITS=MASS PER AREA to specify the nonstructural mass in the units of  “mass per unit area.” This value is valid only for an element set that contains conventional shells, membranes, and/or surface elements.

Set UNITS=MASS PER LENGTH to specify the nonstructural mass in the units of  “mass per unit length.” This value is valid only for an element set that contains beam and/or truss elements. 

### **Optional parameter: **

DISTRIBUTION

This parameter is relevant only when UNITS=TOTAL MASS.

Set DISTRIBUTION=MASS PROPORTIONAL (default) to distribute the total nonstructural mass among the members of the element set region in proportion to the element structural mass. The underlying structural density over the element set region is scaled uniformly; therefore, the center of mass for the element set region is not altered. 

Set DISTRIBUTION=VOLUME PROPORTIONAL to distribute the total nonstructural mass among the members of the element set region in proportion to the element volume in the initial configuration. A uniform value is added to the underlying structural density over the element set region; therefore, if the region has nonuniform structural density, the center of mass for the element set region may be altered.

### **Data line for UNITS=TOTAL MASS: **

**First (and only) line:**

Abaqus does not use any specific physical units, so the user's choice must be consistent.

### **Data line for UNITS=MASS PER VOLUME: **

**First (and only) line:**

Abaqus does not use any specific physical units, so the user's choice must be consistent.

### **Data line for UNITS=MASS PER AREA: **

**First (and only) line:**

Abaqus does not use any specific physical units, so the user's choice must be consistent.

### **Data line for UNITS=MASS PER LENGTH: **

**First (and only) line:**

Abaqus does not use any specific physical units, so the user's choice must be consistent.




