# *CONSTRAINT CONTROLS







### *CONSTRAINT CONTROLSReset overconstraint checking controls.

**Warning:**Use this option to specify the technique to be used to enforce constraints associated with connector elements. Otherwise, this option should not be used unless the user is certain that the model is free of overconstraints. An overconstraint means applying multiple consistent or inconsistent kinematic constraints. Many models have nodal degrees of freedom that are overconstrained, and such overconstraints may lead to inaccurate solutions or nonconvergence. By default, the model will be checked for overconstraints. The consistent overconstraints will be removed whenever possible, while an error message is issued if an inconsistent overconstraint is detected.

**Product: **Abaqus/Standard  

**Type: **Model or history data  

**Level: **Model,  Step

##### **References:**

- ["Overconstraint checks," Section 35.6.1 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-cni-aoverconstraintchecks)
- ["Connectors: overview," Section 31.1.1 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-elm-econnectoroverview)
- ["Mesh tie constraints," Section 35.3.1 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-cni-ptiedconstraint)
- ["Common difficulties associated with contact modeling in Abaqus/Standard," Section 39.1.2 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-cni-acontacttrouble)

### **Optional and mutually exclusive parameters (model data only): **

DELETE SLAVE

Include this parameter to delete contact elements associated with tied slave nodes.

NO CHANGES

Include this parameter to perform overconstraint checks but to prevent Abaqus from changing the model to remove redundant constraints. Detailed messages regarding overconstraints are generated. If this parameter is omitted, Abaqus will attempt to change the model automatically.

NO CHECKS

Include this parameter to suppress overconstraint checks for this model. If this parameter is omitted, overconstraint checks are performed.

PRINT

Set PRINT=YES to print the constraint chains to the message file. If you set PRINT=NO (default), the constraint chains will not be printed.

### **Optional parameters (history data only): **

CHECK FREQUENCY

Set this parameter equal to the desired overconstraint check frequency, in increments. Overconstraint checks are always performed at the beginning of the first increment of the step unless overconstraint checks are suppressed. The default value is CHECK FREQUENCY=1 such that overconstraint checks are performed every increment. Set CHECK FREQUENCY=0 to suppress overconstraint checks in this step.

TERMINATE ANALYSIS

Set TERMINATE ANALYSIS=NO (default) to allow an analysis to continue when an overconstraint is encountered. Detailed messages regarding the overconstraints are issued.

Set TERMINATE ANALYSIS=FIRST OCCURRENCE if the analysis is to be terminated the first time an overconstraint is encountered in a nonlinear general step.

Set TERMINATE ANALYSIS=CONVERGED if the analysis is to be terminated when convergence is achieved in an increment in a nonlinear general step and an overconstraint exists.

If either FIRST OCCURRENCE or CONVERGED is used in a linear perturbation step (where iterations are not necessary), the analysis will be stopped in the first increment when an overconstraint is encountered.

**There are no data lines associated with this option.**



