# 13.1 VEXTERNALDB: User subroutine that gives control to the user at key moments of the analysis







### 13.1 [`VEXTERNALDB`](../sub/sub-link.md#sub-xsl-vexternaldb): User subroutine that gives control to the user at key moments of the analysis

**Product: **Abaqus/Explicit  

**Benefits: **You can now use user subroutine [`VEXTERNALDB`](../sub/sub-link.md#sub-xsl-vexternaldb) to dynamically exchange data among Abaqus user subroutines and with external programs or files. 

**Description: **User subroutine [`VEXTERNALDB`](../sub/sub-link.md#sub-xsl-vexternaldb) is called automatically once at the beginning of the analysis, at the beginning of each step, before each increment, at the start of each increment, at the end of each increment, at the end of each step, and finally at the end of the analysis; thus ceding control to you at key moments. You can modify the suggested time increment and trigger output of restart data, if desired. You can also instruct Abaqus to skip the remainder of the current step or to terminate the whole analysis. You can use the new allocatable local array utilities to coordinate data between various other user subroutines on a given process. Further, you can deploy the allocatable global arrays and the MPI mechanism within [`VEXTERNALDB`](../sub/sub-link.md#sub-xsl-vexternaldb) to synchronize your data among the processes in domain parallel analyses.
**References: **

**Abaqus User Subroutines Reference Guide**
- ["VEXTERNALDB," Section 1.2.3](../sub/sub-link.md#sub-rtn-uexpexternaldb)
- ["Obtaining parallel processes information," Section 2.1.4](../sub/sub-link.md#sub-utl-ugetnumcpus)
- ["Allocatable arrays," Section 2.1.23](../sub/sub-link.md#sub-utl-localarrays)




