# *SYMMETRIC RESULTS TRANSFER







### *SYMMETRIC RESULTS TRANSFERImport results from an axisymmetric or partial three-dimensional analysis.

This option is used to transfer a solution from an axisymmetric analysis to a three-dimensional model or to transfer the solution of a partial three-dimensional model to a full three-dimensional model. It can be used only in conjunction with the [*SYMMETRIC MODEL GENERATION](ch18abk57.md) option.

**Product: **Abaqus/Standard  

**Type: **Model data  

**Level: **This option is not supported in a model defined in terms of an assembly of part instances.

##### **References:**

- ["Transferring results from a symmetric mesh or a partial three-dimensional mesh to a full three-dimensional mesh," Section 10.4.2 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-anl-aaxiresulttransfer)
- ["Symmetric model generation," Section 10.4.1 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-anl-aaximodelgen)
- [*SYMMETRIC MODEL GENERATION](ch18abk57.md)

### **Optional parameters: **

STEP

Set this parameter equal to the step number on the restart file at which the results must be obtained. If this parameter is omitted, the results will be obtained at the last available step found on the restart file.

INC

Set this parameter equal to the increment number on the restart file at which the results must be obtained. If this parameter is omitted, the results will be obtained at the end of the step specified by the STEP parameter.

ITERATION

This parameter is relevant only if the solution is transferred from a previous direct cyclic analysis.

Set this parameter equal to the iteration number on the restart file at which the results must be obtained. Since restart information can be written only at the end of an iteration in a direct cyclic analysis, the INC parameter is irrelevant and is ignored if the ITERATION parameter is specified. 

If this parameter is omitted, the results will be obtained at the end of the step specified by the STEP parameter.

UNBALANCED STRESS

Set UNBALANCED STRESS=STEP (default) if the stress unbalance is to be resolved in the first increment.

Set UNBALANCED STRESS=RAMP if the stress unbalance is to be resolved linearly over the step.

**There are no data lines associated with this option.**



