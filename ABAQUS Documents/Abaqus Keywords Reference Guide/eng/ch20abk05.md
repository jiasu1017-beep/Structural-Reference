# *UNLOADING DATA







### *UNLOADING DATAProvide unloading data for uniaxial behavior models in connectors or unloading data from uniaxial and shear tests for fabrics.

This option is used to define unloading response for the uniaxial behavior of connector elements when used in conjunction with the [*CONNECTOR BEHAVIOR](ch03abk35.md), [*CONNECTOR UNIAXIAL BEHAVIOR](ch03abk52.md), and [*LOADING DATA](ch12abk03.md) options.

This option is used to define the unloading response from a uniaxial or a shear test for fabric materials when used in conjunction with the [*FABRIC](ch06abk01.md), [*UNIAXIAL](ch20abk03.md), and [*LOADING DATA](ch12abk03.md) options. A fabric uniaxial test is specified with increasing strains along the specified yarn direction. A fabric shear test is specified with increasing shear strains as the fill and the warp yarns rotate with respect to each other.

**Product: **Abaqus/Explicit  

**Type: **Model data  

**Level: **Model  

##### **References:**

- ["Connector uniaxial behavior," Section 31.2.10 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-elm-econnuniaxialbehav)
- ["Fabric material behavior," Section 23.4.1 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-mat-cfabric)
- [*CONNECTOR BEHAVIOR](ch03abk35.md)
- [*CONNECTOR UNIAXIAL BEHAVIOR](ch03abk52.md)
- [*FABRIC](ch06abk01.md)
- [*LOADING DATA](ch12abk03.md)
- [*UNIAXIAL](ch20abk03.md)

### Defining the unloading response for uniaxial behavior in connectors

### **Required parameter: **

DEFINITION

Set DEFINITION=COMBINED to define an unloading path based on the specified unloading curve and a transition slope to transition from the loading to the unloading curve.

Set DEFINITION=EXPONENTIAL to define an exponential unloading path.

Set DEFINITION=INTERPOLATED CURVE to define an unloading path based on an interpolation between the specified unloading curves.

Set DEFINITION=QUADRATIC to define a quadratic unloading path.

Set DEFINITION=SHIFTED CURVE to define an unloading path based on shifting the specified unloading curve to the point of unloading.

### **Optional parameter: **

RATE DEPENDENT

Include this parameter to define rate-dependent unloading data. If this parameter is omitted, the data are assumed to be rate independent. This parameter can be used only if the loading data are elastic and rate dependent.

### ** Data lines for DEFINITION=COMBINED to define rate-independent unloading behavior that does not depend on independent components: **

**First line:**

**Second line:**

**Subsequent lines (only needed if the DEPENDENCIES parameter has a value greater than five):**

Do not repeat the first data line. Repeat the subsequent data lines as often as necessary to define the unloading curve data.

### ** Data lines for DEFINITION=COMBINED to define rate-independent unloading behavior that depends on independent components: **

**First line:**

**Second line:**

Do not repeat the first data line. Repeat the subsequent data lines as often as necessary to define the unloading curve data.

### **Data line for DEFINITION=EXPONENTIAL and DEFINITION=QUADRATIC: **

**First (and only) line:**

### ** Data lines for DEFINITION=INTERPOLATED CURVE and DEFINITION=SHIFTED CURVE to define rate-independent unloading behavior (the RATE DEPENDENT parameter is omitted) that does not depend on independent components: **

**First line:**

**Subsequent lines (only needed if the DEPENDENCIES parameter has a value greater than five):**

Repeat this set of data lines as often as necessary to define the unloading curve data.

### ** Data lines for DEFINITION=INTERPOLATED CURVE and DEFINITION=SHIFTED CURVE to define rate-independent unloading behavior (the RATE DEPENDENT parameter is omitted) that depends on independent components: **

**First line:**

 Repeat this set of data lines as often as necessary to define the unloading curve data.

### ** Data lines for DEFINITION=INTERPOLATED CURVE to define rate-dependent unloading behavior (the RATE DEPENDENT parameter is included) that does not depend on independent components: **

**First line:**

**Subsequent lines (only needed if the DEPENDENCIES parameter has a value greater than four):**

Repeat this set of data lines as often as necessary to define the unloading curve data.

### ** Data lines for DEFINITION=INTERPOLATED CURVE to define rate-dependent unloading behavior (the RATE DEPENDENT parameter is included) that depends on independent components: **

**First line:**

 Repeat this set of data lines as often as necessary to define the unloading curve data.

### Defining the unloading response data from uniaxial tests of fabric materials

### **Required parameter: **

DEFINITION

Set DEFINITION=COMBINED to define an unloading path based on the specified unloading curve and a transition slope to transition from the loading to the unloading curve.

Set DEFINITION=EXPONENTIAL to define an exponential unloading path.

Set DEFINITION=INTERPOLATED CURVE to define an unloading path based on an interpolation between the specified unloading curves.

Set DEFINITION=QUADRATIC to define a quadratic unloading path.

Set DEFINITION=SHIFTED CURVE to define an unloading path based on shifting the specified unloading curve to the point of unloading.

The available unloading path types depend on the behavior type assigned to the test data (as defined on the [*LOADING DATA](ch12abk03.md) option).

### **Optional parameter: **

RATE DEPENDENT

Include this parameter equal to define rate-dependent unloading data. If this parameter is omitted, the data are assumed to be rate independent. This parameter can be used only if the loading data are elastic and rate dependent.

### ** Data lines for DEFINITION=COMBINED: **

**First line:**

**Second line:**

**Subsequent lines (only needed if the DEPENDENCIES parameter has a value greater than five):**

Do not repeat the first data line. Repeat the subsequent data lines as often as necessary to define the unloading curve data.

### **Data line for DEFINITION=EXPONENTIAL and DEFINITION=QUADRATIC: **

**First (and only) line:**

### ** Data lines for DEFINITION=INTERPOLATED CURVE and DEFINITION=SHIFTED CURVE to define uniaxial rate-independent unloading behavior (the RATE DEPENDENT parameter is omitted): **

**First line:**

**Subsequent lines (only needed if the DEPENDENCIES parameter has a value greater than five):**

Repeat this set of data lines as often as necessary to define the unloading curve data.

### ** Data lines for DEFINITION=INTERPOLATED CURVE to define uniaxial rate-dependent unloading behavior (the RATE DEPENDENT parameter is included): **

**First line:**

**Subsequent lines (only needed if the DEPENDENCIES parameter has a value greater than four):**

Repeat this set of data lines as often as necessary to define the unloading curve data.




