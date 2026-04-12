# 25.40 FractureCriterion object







 The FractureCriterion object specifies fractureCriterion options for a contact interaction property.

**Access**

```
import interaction
mdb.models[*name*].interactionProperties[*name*].fractureCriterion
```

### 25.40.1 FractureCriterion(...)

This method creates a FractureCriterion object.

**Path**

```
mdb.models[*name*].interactionProperties[*name*].FractureCriterion
```

**Required argument**

*initTable*

A sequence of sequences of Floats specifying the value defining the fracture criterion. The items in the table data are described below.

**Optional arguments**

*type*

A SymbolicConstant specifying the type of data used to define the fracture criterion. Possible values are VCCT and ENHANCED VCCT. The default value is VCCT.

*mixedModeBehavior*

A SymbolicConstant specifying the mixed mode behavior type used to define fracture criterion. Possible values are BK, POWER, and REEDER. The default value is BK.

*temperatureDependency*

A Boolean specifying whether the fracture criterion data depend on temperature. The default value is OFF.

*dependencies*

An Int specifying the number of fracture criterion data field variables. The default value is 0.

*tolerance*

A Float specifying the tolerance for VCCT\Enhanced VCCT type. The default value is 0.2.

*specifyUnstableCrackProp*

A SymbolicConstant specifying whether to include unstable crack growth tolerance in fracture criterion. Possible values are ON and OFF. The default value is OFF.

*unstableTolerance*

The SymbolicConstant DEFAULT or a Float specifying the tolerance for unstable crack propagation. This parameter specified only if *specifyUnstableCrackProp*=ON. The default value is DEFAULT.

**Table data**

Table data for *initTable*:

If *type*=VCCT for *mixedModeBehavior*=BK or REEDER, the table data specify the following:
- Mode I critical energy release rate, ![](../graphics/ker_eqn00072.gif).
- Mode II critical energy release rate, ![](../graphics/ker_eqn00073.gif).
- Mode III critical energy release rate, ![](../graphics/ker_eqn00074.gif).
- Exponent, ![](../graphics/ker_eqn00075.gif).
- Temperature, if the data depend on temperature.
- Value of the first field variable, if the data depend on field variables.
- Value of the second field variable.
- Etc.

If *type*=VCCT for *mixedModeBehavior*=POWER, the table data specify the following:
- Mode I critical energy release rate, ![](../graphics/ker_eqn00072.gif).
- Mode II critical energy release rate, ![](../graphics/ker_eqn00073.gif).
- Mode III critical energy release rate, ![](../graphics/ker_eqn00074.gif).
- Exponent, ![](../graphics/ker_eqn00076.gif).
- Exponent, ![](../graphics/ker_eqn00077.gif).
- Exponent, ![](../graphics/ker_eqn00078.gif).
- Value of the first field variable, if the data depend on field variables.
- Value of the second field variable.
- Etc.

If *type*=ENHANCED VCCT for *mixedModeBehavior*=BK or REEDER, the table data specify the following:
- Mode I critical energy release rate for onset crack, ![](../graphics/ker_eqn00072.gif).
- Mode II critical energy release rate for onset crack, ![](../graphics/ker_eqn00073.gif).
- Mode III critical energy release rate for onset crack, ![](../graphics/ker_eqn00074.gif).
- Mode I critical energy release rate for crack propagation, ![](../graphics/ker_eqn00072.gif).
- Mode II critical energy release rate for crack propagation, ![](../graphics/ker_eqn00073.gif).
- Mode III critical energy release rate for crack propagation, ![](../graphics/ker_eqn00074.gif).
- Exponent, ![](../graphics/ker_eqn00075.gif).
- Temperature, if the data depend on temperature.
- Value of the first field variable, if the data depend on field variables.
- Value of the second field variable.
- Etc.

If *type*=ENHANCED VCCT for *mixedModeBehavior*=POWER, the table data specify the following:
- Mode I critical energy release rate for onset crack, ![](../graphics/ker_eqn00072.gif).
- Mode II critical energy release rate for onset crack, ![](../graphics/ker_eqn00073.gif).
- Mode III critical energy release rate for onset crack, ![](../graphics/ker_eqn00074.gif).
- Mode I critical energy release rate for crack propagation, ![](../graphics/ker_eqn00072.gif).
- Mode II critical energy release rate for crack propagation, ![](../graphics/ker_eqn00073.gif).
- Mode III critical energy release rate for crack propagation, ![](../graphics/ker_eqn00074.gif).
- Exponent, ![](../graphics/ker_eqn00076.gif).
- Exponent, ![](../graphics/ker_eqn00077.gif).
- Exponent, ![](../graphics/ker_eqn00078.gif).
- Value of the first field variable, if the data depend on field variables.
- Value of the second field variable.
- Etc.

**Return value**

A FractureCriterion object.

**Exceptions**

None.

### 25.40.2 setValues(...)

This method modifies the FractureCriterion object.

**Required arguments**

None.

**Optional arguments**

The optional arguments to `setValues` are the same as the arguments to the [FractureCriterion](pt01ch25pyo40.md#ker-fracturecriterion-fracturecriterion-pyc) method.

**Return value**

None

**Exceptions**

None.

### 25.40.3 Members

The FractureCriterion object has members with the same names and descriptions as the arguments to the [FractureCriterion](pt01ch25pyo40.md#ker-fracturecriterion-fracturecriterion-pyc) method.

### 25.40.4 Corresponding analysis keywords

| [*FRACTURE CRITERION](../key/key-link.md#usb-kws-hfracturecriterion) |
| --- |




