# *DISTRIBUTION







### *DISTRIBUTIONDefine spatial distributions.

This option is used to define a spatial distribution.

**Products: **Abaqus/Standard  Abaqus/Explicit  Abaqus/CFD  Abaqus/CAE  

**Type: **Model data  

**Level: **Part,  Part instance,  Assembly,  Model  

**Abaqus/CAE: **Property module

##### **References:**

- ["Distribution definition," Section 2.8.1 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-int-adefiningdistributions)
- [*CONTACT CLEARANCE](ch03abk55.md)
- [*DENSITY](ch04abk13.md)
- [*DISTRIBUTION TABLE](ch04abk30.md)
- [*ELASTIC](ch05abk03.md)
- [*EXPANSION](ch05abk34.md)
- [*FLUID BOUNDARY](ch06abk17.md)
- [*MEMBRANE SECTION](ch13abk16.md)
- [*ORIENTATION](ch15abk01.md)
- [*SHELL GENERAL SECTION](ch18abk14.md)
- [*SHELL SECTION](ch18abk15.md)

### **Required parameters: **

LOCATION

Set LOCATION=ELEMENT to define a distribution on elements.

Set LOCATION=NODE to define a distribution on nodes.

Set LOCATION=NONE to define a distribution used with a fluid boundary condition.

NAME

Set this parameter equal to a label that will be used to refer to the distribution.

TABLE

Set this parameter equal to the distribution table that defines the format of the data given on the data lines.

### **Optional parameter: **

INPUT

Set this parameter equal to the name of the alternate input file containing the data lines for this option. See ["Input syntax rules," Section 1.2.1 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-int-iinputsyntax), for the syntax of such file names. If this parameter is omitted, it is assumed that the data follow the keyword line.

### **Data lines to define a distribution of the coordinates of points *a* and *b* used to define a local coordinate system: **

**First line:**

Repeat this data line as often as necessary to define the data for element numbers or element sets.

### **Data lines to define a distribution of additional rotation angles used to define a local coordinate system: **

**First line:**

Repeat this data line as often as necessary to define the data for element numbers or element sets.

### **Data lines to define a distribution of shell or membrane thickness: **

**First line:**

Repeat this data line as often as necessary to define the data for element numbers or element sets.

### **Data lines to define a distribution of shell offset: **

**First line:**

Repeat this data line as often as necessary to define the data for element numbers or element sets.

### **Data lines to define a distribution of general section stiffnesses: **

**First line:**

**Second line:**

**Third line:**

Repeat this set of data lines as often as necessary to define the data for element numbers or element sets.

### **Data lines to define a distribution of initial contact clearances: **

**First line:**

Repeat this data line as often as necessary.

### **Data lines to define a distribution of isotropic elastic moduli: **

**First line:**

Repeat this data line as often as necessary to define the data for element numbers or element sets.

### **Data lines to define a distribution of orthotropic elastic moduli: **

**First line:**

**Second line:**

Repeat this set of data lines as often as necessary to define data for element numbers or element sets.

### **Data lines to define a distribution of orthotropic elastic moduli using engineering constants: **

**First line:**

**Second line:**

Repeat this set of data lines as often as necessary to define the data for element numbers or element sets.

### **Data lines to define a distribution of orthotropic elastic moduli in plane stress: **

**First line:**

Repeat this data line as often as necessary to define the data for element numbers or element sets.

### **Data lines to define a distribution of anisotropic elastic moduli: **

**First line:**

**Second line:**

**Third line:**

Repeat this set of data lines as often as necessary to define the data for element numbers or element sets.

### **Data lines to define a distribution of mass density: **

**First line:**

Repeat this data line as often as necessary to define the data for element numbers or element sets.

### **Data lines to define a distribution of isotropic thermal expansion: **

**First line:**

Repeat this data line as often as necessary to define the data for element numbers or element sets.

### **Data lines to define a distribution of orthotropic thermal expansion: **

**First line:**

Repeat this data line as often as necessary to define the data for element numbers or element sets.

### **Data lines to define a distribution of anisotropic thermal expansion: **

**First line:**

Repeat this data line as often as necessary to define the data for element numbers or element sets.

### **Data lines to define a distribution of pressure that varies with the total volume of fluid crossing a surface in Abaqus/CFD: **

**First line when specifying pressure first:**

**First line when specifying volume first:**

Repeat this data line as often as necessary to define the data for pressure and volume.




