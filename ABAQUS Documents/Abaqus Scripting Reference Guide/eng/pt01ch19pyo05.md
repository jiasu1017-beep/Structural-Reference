# 19.5 DebondVCCT object







The DebondVCCT object defines the parameters needed to activate crack propagation using VCCT.

The DebondVCCT object is derived from the [Crack](pt01ch19pyo04.md) object.

**Access**

```
import part
mdb.models[*name*].parts[*name*].engineeringFeatures.cracks[*name*]
import assembly
mdb.models[*name*].rootAssembly.engineeringFeatures.cracks[*name*]
```

### 19.5.1 DebondVCCT(...)

This method creates a DebondVCCT object. Although the constructor is available both for parts and for the assembly, DebondVCCT objects are currently supported only under the assembly.

**Path**

```
mdb.models[*name*].parts[*name*].engineeringFeatures.DebondVCCT
mdb.models[*name*].rootAssembly.engineeringFeatures.DebondVCCT
```

**Required arguments**

*name*

A String specifying the repository key.

*initiationStep*

A String specifying the name of the step in which the DebondVCCT object is created.

*surfToSurfInteraction*

A String specifying the name of the [SurfaceToSurfaceContactStd](pt01ch25pyo75.md) object that defines the surface to surface interaction for the crack surfaces.

**Optional arguments**

*debondingForceAmplitude*

A SymbolicConstant specifying whether the debond force between the two surfaces at the crack tip is to be released immediately or gradually during the following increment after debonding. Possible values are STEP and RAMP. The default value is STEP.

*printToDATFrequency*

An Int specifying the frequency at which output will be printed to DAT file. The default value is 1.

**Return value**

A DebondVCCT object.

**Exceptions**

None.

### 19.5.2 setValues(...)

This method modifies the DebondVCCT object.

**Required arguments**

None.

**Optional arguments**

The optional arguments to `setValues` are the same as the arguments to the [DebondVCCT](pt01ch19pyo05.md#ker-debondvcct-debondvcct-pyc) method, except for the *name* argument.

**Return value**

None

**Exceptions**

None.

### 19.5.3 Members

The DebondVCCT object has members with the same names and descriptions as the arguments to the [DebondVCCT](pt01ch19pyo05.md#ker-debondvcct-debondvcct-pyc) method.

In addition, the DebondVCCT object has the following member:

*suppressed*

A Boolean specifying whether the crack is suppressed or not. The default value is OFF.

### 19.5.4 Corresponding analysis keywords

| [*DEBOND](../key/key-link.md#usb-kws-hdebond) |
| --- |




