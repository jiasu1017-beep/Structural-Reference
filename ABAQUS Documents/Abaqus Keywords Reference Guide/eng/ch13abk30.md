# *MPC







### *MPCDefine multi-point constraints.

This option is used to impose constraints between different degrees of freedom of the model.

**Products: **Abaqus/Standard  Abaqus/Explicit  Abaqus/CAE  

**Type: **Model data  

**Level: **Part,  Part instance,  Assembly  

**Abaqus/CAE: **Interaction module

##### **References:**

- ["General multi-point constraints," Section 35.2.2 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-cni-pmpc)
- ["MPC," Section 1.1.14 of the Abaqus User Subroutines Reference Guide](../sub/sub-link.md#sub-rtn-umpc)

### **Optional parameters: **

INPUT

Set this parameter equal to the name of the alternate input file containing the data lines for this option. See ["Input syntax rules," Section 1.2.1 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-int-iinputsyntax), for the syntax of such file names. If this parameter is omitted, it is assumed that the data follow the keyword line.

MODE

This parameter applies only to Abaqus/Standard analyses.

This parameter is used only if the USER parameter is included.

Set MODE=DOF (default) for user subroutine [`MPC`](../sub/sub-link.md#sub-xsl-mpc) to operate in a degree of freedom mode. 

Set MODE=NODE for user subroutine [`MPC`](../sub/sub-link.md#sub-xsl-mpc) to operate in a nodal mode.

USER

This parameter applies only to Abaqus/Standard analyses.

Include this parameter to indicate that the constraint is defined in user subroutine [`MPC`](../sub/sub-link.md#sub-xsl-mpc). 

### **Data lines to define multi-point constraints: **

**First line:**

The first 15 nodes or node sets of an MPC must be entered on the first line. If the MPC contains more than 15 nodes, enter 0 on the next line to indicate that it is a continuation line and then continue to enter the following nodes on this line. Any number of continuation lines are allowed. Exactly 15 nodes or node sets must be given on each line except the last line.




