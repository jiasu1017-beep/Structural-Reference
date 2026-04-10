# *COHESIVE BEHAVIOR







### *COHESIVE BEHAVIORSpecify surface-based cohesive behavior properties.

This option is used to define surface-based cohesive behavior in a mechanical contact analysis. It must be used in conjunction with the [*SURFACE INTERACTION](ch18abk50.md) option.

**Products: **Abaqus/Standard  Abaqus/Explicit  Abaqus/CAE  

**Type: **Model data  

**Level: **Model  

**Abaqus/CAE: **Interaction module

##### **References:**

- ["Surface-based cohesive behavior," Section 37.1.10 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-cni-acohesivebehavior)
- [*SURFACE INTERACTION](ch18abk50.md)

### **Optional parameters: **

DEPENDENCIES

Set this parameter equal to the number of field variable dependencies included in the definition of the moduli. If this parameter is omitted, it is assumed that the moduli are constant or depend only on temperature. See ["Specifying field variable dependence" in "Material data definition," Section 21.1.2 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-mat-cmaterialdata-fvdepen), for more information.

ELIGIBILITY

Set ELIGIBILITY=CURRENT CONTACTS (default) to define cohesive behavior not only for all nodes of the slave surface that are in contact with the master surface at the start of a step, but also for slave nodes that are not initially in contact but may come in contact during the course of a step.

Set ELIGIBILITY=ORIGINAL CONTACTS to restrict cohesive behavior to only those nodes of the slave surface that are in contact with the master surface at the start of a step.

Set ELIGIBILITY=SPECIFIED CONTACTS to restrict cohesive behavior to a subset of slave nodes defined using [*INITIAL CONDITIONS](ch09abk18.md), TYPE=CONTACT. This parameter value is available only for Abaqus/Standard analyses.

REPEATED CONTACTS

Include this parameter to modify the default post-failure behavior when progressive damage has been defined. By default, cohesive behavior is not enforced for nodes on the slave surface once ultimate failure has occurred at those nodes. Use the REPEATED CONTACTS parameter to enforce cohesive behavior for recurrent contacts at nodes on the slave surface subsequent to ultimate failure. 

TYPE

Set TYPE=UNCOUPLED (default) to define uncoupled traction behavior.

Set TYPE=COUPLED to define coupled traction behavior.

### **Data lines to define uncoupled traction separation behavior (TYPE=UNCOUPLED): **

**First line:**

**Subsequent lines (only needed if the DEPENDENCIES parameter has a value greater than four; relevant only for defining uncoupled traction behavior):**

Repeat this set of data lines as often as necessary to define the elastic behavior as a function of temperature and other predefined field variables.

### **Data lines to define coupled traction separation behavior (TYPE=COUPLED): **

**First line:**

**Subsequent lines (only needed if the DEPENDENCIES parameter has a value greater than one):**

Repeat this set of data lines as often as necessary to define the elastic behavior as a function of temperature and other predefined field variables.




