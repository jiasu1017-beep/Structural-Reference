# *MAP SOLUTION







### *MAP SOLUTIONMap a solution from an old mesh to a new mesh.

This option is used to transfer solution variables from an earlier analysis to a new mesh that occupies the same space.

**Product: **Abaqus/Standard  

**Type: **Model data  

**Level: **Model  

##### **Reference:**

- ["Mesh-to-mesh solution mapping," Section 12.4.1 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-anl-amapsolution)

### **Optional parameters: **

INC

Set this parameter equal to the increment number from which the old solution will be read. If this parameter is omitted, the last increment for which a solution is available will be read.

The STEP parameter must be specified if the INC parameter is used.

STEP

Set this parameter equal to the step number from which the old solution will be read. If this parameter is omitted, the last step and increment for which a solution is available will be read.

UNBALANCED STRESS

Set UNBALANCED STRESS=RAMP (default) if the stress unbalance is to be resolved linearly over the step.

Set UNBALANCED STRESS=STEP if the stress unbalance is to be resolved in the first increment.

### **Data line to translate an old-model mesh: **

**First (and only) line:**

### **Data lines to translate and/or rotate an old-model mesh: **

**First line:**

Enter values of zero to apply a pure rotation.

**Second line:**

If both translation and rotation are specified, translation is applied before rotation.

**Figure 13.3–1** Rotation of an old-model mesh.

![](../graphics/ksuperprop-rot.png)




