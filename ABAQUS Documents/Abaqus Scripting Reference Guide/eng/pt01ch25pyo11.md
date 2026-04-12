# 25.11 CohesiveBehavior object







The CohesiveBehavior object specifies cohesive behavior for a contact interaction property.

**Access**

```
import interaction
mdb.models[*name*].interactionProperties[*name*].cohesiveBehavior
```

### 25.11.1 CohesiveBehavior(...)

This method creates a CohesiveBehavior object.

**Path**

```
mdb.models[*name*].interactionProperties[*name*].CohesiveBehavior
```

**Required arguments**

None.

**Optional arguments**

*repeatedContacts*

A Boolean specifying whether to enforce cohesive behavior for recurrent contacts at nodes on the slave surface subsequent to ultimate failure. The default value is OFF.

*eligibility*

A SymbolicConstant specifying the eligible slave nodes. Possible values are ALL_NODES, INITIAL_NODES, and SPECIFIED. The default value is ALL_NODES.

*defaultPenalties*

A Boolean specifying whether to use the default contact penalties. The default value is ON.

*coupling*

A SymbolicConstant specifying whether the traction-separation coefficients are coupled or uncoupled.  This argument is valid only for *defaultPenalties*=OFF. Possible values are UNCOUPLED and COUPLED. The default value is UNCOUPLED.

*temperatureDependency*

A Boolean specifying whether the coefficient data depend on temperature.  This argument is valid only for *defaultPenalties*=OFF. The default value is OFF.

*dependencies*

An Int specifying the number of field variables.  This argument is valid only for *defaultPenalties*=OFF. The default value is 0.

*table*

A sequence of sequences of Floats specifying the traction-separation coefficients. The items in the table data are described below.  This argument is valid only for *defaultPenalties*=OFF.

**Table data**

If *coupling*=UNCOUPLED, the table data specify the following:
- Stiffness coefficient in the normal direction, ![](../graphics/ker_eqn00063.gif).
- Stiffness coefficient in the first shear direction, ![](../graphics/ker_eqn00064.gif).
- Stiffness coefficient in the second shear direction, ![](../graphics/ker_eqn00065.gif).
- Temperature, if the data depend on temperature.
- Value of the first field variable, if the data depend on field variables.
- Value of the second field variable.
- Etc.

If *coupling*=COUPLED, the table data specify the following:- Stiffness coefficient in the normal direction, ![](../graphics/ker_eqn00063.gif).
- Stiffness coefficient in the first shear direction, ![](../graphics/ker_eqn00064.gif).
- Stiffness coefficient in the second shear direction, ![](../graphics/ker_eqn00065.gif).
- Coupled stiffness coefficient, ![](../graphics/ker_eqn00066.gif).
- Coupled stiffness coefficient, ![](../graphics/ker_eqn00067.gif).
- Coupled stiffness coefficient, ![](../graphics/ker_eqn00068.gif).
- Temperature, if the data depend on temperature.
- Value of the first field variable, if the data depend on field variables.
- Value of the second field variable.
- Etc.

**Return value**

A CohesiveBehavior object.

**Exceptions**

None.

### 25.11.2 setValues(...)

This method modifies the CohesiveBehavior object.

**Required arguments**

None.

**Optional arguments**

The optional arguments to `setValues` are the same as the arguments to the [CohesiveBehavior](pt01ch25pyo11.md#ker-cohesivebehavior-cohesivebehavior-pyc) method.

**Return value**

None

**Exceptions**

None.

### 25.11.3 Members

The CohesiveBehavior object has members with the same names and descriptions as the arguments to the [CohesiveBehavior](pt01ch25pyo11.md#ker-cohesivebehavior-cohesivebehavior-pyc) method.

### 25.11.4 Corresponding analysis keywords

| [*COHESIVE BEHAVIOR](../key/key-link.md#usb-kws-mcohesivebehavior) |
| --- |




