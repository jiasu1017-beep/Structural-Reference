# *FRACTURE CRITERION







### *FRACTURE CRITERIONSpecify crack propagation criteria.

This option is used to specify the criterion for crack propagation along initially partially bonded surfaces. It must appear immediately following the [*DEBOND](ch04abk09.md) option in Abaqus/Standard and after the [*COHESIVE BEHAVIOR](ch03abk23.md) option in Abaqus/Explicit. This option can also be used in Abaqus/Standard to specify a linear elastic fracture mechanics-based criterion for crack propagation in enriched elements. It must appear immediately following the [*SURFACE BEHAVIOR](ch18abk48.md) option in Abaqus/Standard in this case.

**Products: **Abaqus/Standard  Abaqus/Explicit  Abaqus/CAE  

**Type: **Model or history data in Abaqus/Standard; Model data in Abaqus/Explicit  

**Level: **Model or Step in Abaqus/Standard; Model in Abaqus/Explicit  

**Abaqus/CAE: **Interaction module

##### **References:**

- ["Crack propagation analysis," Section 11.4.3 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-anl-acrackpropagation)
- ["Modeling discontinuities as an enriched feature using the extended finite element method," Section 10.7.1 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-anl-aenrichment)
- [*DEBOND](ch04abk09.md)
- [*COHESIVE BEHAVIOR](ch03abk23.md)
- [*SURFACE BEHAVIOR](ch18abk48.md)

### **Required parameters: **

DISTANCE

This parameter is required only if TYPE=COD or TYPE=CRITICAL STRESS is used.

If TYPE=CRITICAL STRESS, set this parameter equal to the distance along the potential crack surface ahead of the crack tip at which the critical stress criterion is evaluated.

If TYPE=COD, set this parameter equal to the distance behind the crack tip along the slave surface at which the crack opening displacement is measured.

NSET

This parameter is required only if TYPE=CRACK LENGTH. Set this parameter equal to the name of the node set containing the nodes that are used to define the reference point.

TYPE

Set TYPE=CRITICAL STRESS to use the critical stress criterion at a distance ahead of the crack tip as the crack propagation criterion. This setting is available only in Abaqus/Standard.

Set TYPE=COD to use the critical value of the crack opening displacement at a distance behind the crack tip as the crack propagation criterion. This setting is available only in Abaqus/Standard.

Set TYPE=CRACK LENGTH to specify the crack length as a function of time. This setting is available only in Abaqus/Standard.

Set TYPE=ENHANCED VCCT to use the enhanced VCCT (Virtual Crack Closure Technique) criterion in which the onset and growth of a crack can be controlled by two different critical fracture energy release rates. This setting is available only in Abaqus/Standard.

Set TYPE=FATIGUE to indicate that the onset and fatigue crack growth are characterized by the relative fracture energy release rate at the crack tip based on the Paris law. This setting is available only in Abaqus/Standard.

Set TYPE=VCCT to use the VCCT (Virtual Crack Closure Technique) criterion as the crack propagation criterion. The VCCT criterion uses the principles of linear elastic fracture mechanics.

### **Optional parameters: **

DEPENDENCIES

This parameter is not relevant for TYPE=CRACK LENGTH. 

Set this parameter equal to the number of field variable dependencies included in the data lines. If this parameter is omitted, it is assumed that the data are constant or depend only on temperature. See ["Specifying field variable dependence" in "Material data definition," Section 21.1.2 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-mat-cmaterialdata-fvdepen), for more information.

MIXED MODE BEHAVIOR

This parameter  is relevant only for TYPE=ENHANCED VCCT, TYPE=FATIGUE, or TYPE=VCCT.

Set MIXED MODE BEHAVIOR=BK to specify the fracture energy as a function of the mode mix by means of the Benzeggagh-Kenane mixed mode fracture criterion.

Set MIXED MODE BEHAVIOR=POWER to specify the fracture energy as a function of the mode mix by means of a power law mixed mode fracture criterion.

Set MIXED MODE BEHAVIOR=REEDER to specify the fracture energy as a function of the mode mix by means of the REEDER mixed mode fracture criterion.

The default is MIXED MODE BEHAVIOR=BK.

NODAL ENERGY RATE

This parameter  is relevant only for TYPE=FATIGUE or TYPE=VCCT.

Include this parameter to indicate that the critical energy release rates should not be read from the data lines but should be interpolated from the critical energy release rates specified at the nodes with the [*NODAL ENERGY RATE](ch14abk07.md) option. The exponents are still read from the data lines.

NORMAL DIRECTION

This parameter can be used only in conjunction with TYPE=ENHANCED VCCT, TYPE=FATIGUE, or TYPE=VCCT for enriched elements in Abaqus/Standard.

Set NORMAL DIRECTION=MTS (default) to specify that the crack will propagate orthogonal to the direction of the maximum tangential stress when the fracture criterion is satisfied.

Set NORMAL DIRECTION=1 to specify that the crack will propagate orthogonal to the element local 1-direction when the fracture criterion is satisfied.

Set NORMAL DIRECTION=2 to specify that the crack will propagate orthogonal to the element local 2-direction when the fracture criterion is satisfied.

SYMMETRY

Include this parameter to compare the opening between the slave surface and the symmetry plane to half the COD value specified. The SYMMETRY parameter is relevant only for TYPE=COD when the user is using symmetry conditions to model the problem. In this case the NORMAL parameter must be specified on the [*INITIAL CONDITIONS](ch09abk18.md) option.

UNSTABLE GROWTH TOLERANCE

Set this parameter equal to the tolerance within which the unstable crack propagation criterion must be satisfied for multiple nodes at and ahead of the crack tip to be allowed to debond without the cut back of increment size in one increment when the VCCT criterion is satisfied for an unstable crack problem.

If this parameter is included without a specified value, the default value is infinity.

This parameter is meaningful only when used with the [*DEBOND](ch04abk09.md) option in Abaqus/Standard.

TOLERANCE

Set this parameter equal to the tolerance within which the crack propagation criterion must be satisfied. The default is TOLERANCE=0.1 for TYPE=CRITICAL STRESS, TYPE=COD, and TYPE=CRACK LENGTH; for TYPE=ENHANCED VCCT and TYPE=VCCT, the default is TOLERANCE=0.2.

VISCOSITY

This parameter applies only to Abaqus/Standard analyses and can be used only in combination with TYPE=ENHANCED VCCT or TYPE=VCCT.

Set this parameter equal to the value of the viscosity coefficient used in the viscous regularization.  The default value is 0.0.

### **Data lines to define the critical stress criterion (TYPE=CRITICAL STRESS): **

**First line:**

**Subsequent lines (only needed if the DEPENDENCIES parameter has a value greater than four):**

Repeat this set of data lines as often as necessary to define the critical stress criterion as a function of temperature and/or field variables.

### **Data lines to define the crack opening displacement criterion (TYPE=COD): **

**First line:**

**Subsequent lines (only needed if the DEPENDENCIES parameter has a value greater than five):**

Repeat this set of data lines as often as necessary to define the crack opening displacement criterion as a function of temperature and/or field variables.

### **Data lines to define the crack length versus time criterion (TYPE=CRACK LENGTH): **

**First line:**

Repeat this data line as often as necessary to define the crack length as a function of time.

### **Data lines to define the onset and growth of a crack for the enhanced VCCT criterion (TYPE=ENHANCED VCCT) for MIXED MODE BEHAVIOR=BK or REEDER: **

**First line:**

**Subsequent lines (only needed if the DEPENDENCIES parameter has a nonzero value):**

Repeat this set of data lines as often as necessary to define the critical energy rates and exponent as a function of temperature and field variables.

### **Data lines to define the onset and growth of a crack for the enhanced VCCT criterion (TYPE=ENHANCED VCCT) for MIXED MODE BEHAVIOR=POWER: **

**First line:**

**Second line:**

**Subsequent lines (only needed if the DEPENDENCIES parameter has a value greater than six):**

Repeat this set of data lines as often as necessary to define the critical energy rates and exponents as a function of temperature and field variables.

### **Data lines to define the low-cycle fatigue onset and crack growth criterion (TYPE=FATIGUE) for MIXED MODE BEHAVIOR=BK or REEDER: **

**First line:**

**Second line:**

**Subsequent lines (only needed if the DEPENDENCIES parameter has a value greater than five):**

Repeat this set of data lines as often as necessary to define the constants used in the Paris law, critical energy rates, and exponents as a function of temperature and field variables.

### **Data lines to define the low-cycle fatigue onset and crack growth criterion (TYPE=FATIGUE) for MIXED MODE BEHAVIOR=POWER: **

**First line:**

**Second line:**

**Subsequent lines (only needed if the DEPENDENCIES parameter has a value greater than three):**

Repeat this set of data lines as often as necessary to define the constants used in the Paris law, the critical energy rates, and exponents as a function of temperature and field variables.

### **Data lines to define the VCCT criterion (TYPE=VCCT) for MIXED MODE BEHAVIOR=BK or REEDER: **

**First line:**

**Subsequent lines (only needed if the DEPENDENCIES parameter has a value greater than three):**

Repeat this set of data lines as often as necessary to define the critical energy rates and exponent as a function of temperature and field variables.

### **Data lines to define the VCCT criterion (TYPE=VCCT) for MIXED MODE BEHAVIOR=POWER: **

**First line:**

**Subsequent lines (only needed if the DEPENDENCIES parameter has a value greater than one):**

Repeat this set of data lines as often as necessary to define the critical energy rates and exponents as a function of temperature and field variables.




