# 15.3 Changes in Abaqus user subroutines







This section summarizes the changes and the additions that have been made to user subroutines that can be used in an Abaqus model.

| **mod** | **(S)** | [`UCREEPNETWORK`](../sub/sub-link.md#sub-xsl-ucreepnetwork) |
| --- | --- | --- |
|  |  | Four new variables can be defined: Four variables can now be passed in for information: |
| **mod** | **(S)** | [`UEXTERNALDB`](../sub/sub-link.md#sub-xsl-uexternaldb) |
|  |  | The `LOP` variable to be passed in for information can take new values. `LOP`=5 indicates that the user subroutine is being called at the start of a step. `LOP`=6 indicates that the user subroutine is being called at the end of a step. |
| **mod** | **(S)** | [`UMAT`](../sub/sub-link.md#sub-xsl-umat) |
|  |  | Variable `JSTEP(1)` can now be passed in to identify the step number. |
| **new** | **(S)** | [`UXFEMNONLOCALWEIGHT`](../sub/sub-link.md#sub-xsl-uxfemnonlocalweight) |
|  |  | User subroutine to define the weight function used to compute the average stress/strain to determine the crack propagation direction. |
| **new** | **(E)** | [`VEXTERNALDB`](../sub/sub-link.md#sub-xsl-vexternaldb) |
|  |  | User subroutine that gives control to the user at key moments of the analysis so that data can be exchanged dynamically among Abaqus user subroutines and with external programs or files. |
| **new** | **(E)** | [`VUCHARLENGTH`](../sub/sub-link.md#sub-xsl-vucharlength) |
|  |  | User subroutine to define characteristic element length at a material point. |




