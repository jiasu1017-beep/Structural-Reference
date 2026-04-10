# *PRINT







### *PRINTRequest or suppress output to the message file in an Abaqus/Standard analysis or to the status file in an Abaqus/Explicit analysis.

This option is used to obtain or suppress detailed printout in the message (`.msg`) file in an Abaqus/Standard analysis or in the status (`.sta`) file in an Abaqus/Explicit analysis.

**Products: **Abaqus/Standard  Abaqus/Explicit  Abaqus/CAE  

**Type: **History data 

**Level: **Step

**Abaqus/CAE: **Step module

##### **References:**

- ["Output," Section 4.1.1 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-out-ooutput)
- ["Output to the output database," Section 4.1.3 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-out-odboutput)

### **Optional parameters in Abaqus/Standard analyses: **

ADAPTIVE MESH

Set ADAPTIVE MESH=YES to request detailed output during adaptive mesh smoothing. The default is ADAPTIVE MESH=NO.

CONTACT

Set CONTACT=YES to request detailed output of points that are contacting or separating in interface and gap problems. This output is useful in difficult contact problems to track the development of the solution during iteration within an increment. The output will be printed for every increment unless FREQUENCY=0. The default is CONTACT=NO.

FREQUENCY

Set this parameter equal to the output frequency, in increments. The output will always be printed at the last increment of each step unless FREQUENCY=0. The default is FREQUENCY=1. Set FREQUENCY=0 to suppress the output.

MODEL CHANGE

Set MODEL CHANGE=YES to request detailed output of which elements are being removed or reactivated in the step. This output includes the new original coordinates and normals of elements being reactivated strain free in a large-displacement analysis. The default is MODEL CHANGE=NO.

PLASTICITY

Set PLASTICITY=YES to request detailed output of element and integration point numbers for which the plasticity algorithms have failed to converge in the material routines. This output is useful to determine the location in the mesh and the plasticity model for which Abaqus/Standard is encountering material model difficulties. This information may help in identifying modeling problems as well as material parameter specification problems. The default is PLASTICITY=NO.

RESIDUAL

Set RESIDUAL=YES (default) if the output of equilibrium residuals is to be given during the equilibrium iterations. Set RESIDUAL=NO to suppress the output.

SOLVE

Set SOLVE=YES (default) to request information regarding the actual number of equations and the memory requirement in each iteration. Set SOLVE=NO to suppress the output.

### **Optional parameters in Abaqus/Explicit analyses: **

ALLKE

Set ALLKE=YES to request that a column containing the total kinetic energy be printed in the status file. Set ALLKE=NO to suppress this printout. The default is ALLKE=YES.

CRITICAL ELEMENT

Set CRITICAL ELEMENT=YES to request that a column listing the element that has the smallest stable time increment and a column listing the value be printed in the status file. Set CRITICAL ELEMENT=NO to suppress this printout. The default is CRITICAL ELEMENT=YES.

DMASS

Set DMASS=YES to request that a column containing the percent change in total mass of the model due to mass scaling be printed in the status file. Set DMASS=NO to suppress this printout. The default is DMASS=NO unless active mass scaling is present in the step. [*FIXED MASS SCALING](ch06abk13.md) propagated from a previous step is not considered to be active mass scaling.

ETOTAL

Set ETOTAL=YES to request that a column containing the energy balance of the model be printed in the status file. Set ETOTAL=NO to suppress this printout. The default is ETOTAL=YES.

Other energy variables can also be printed. Please refer to["Total energy output" in "Output to the output database," Section 4.1.3 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-out-odboutput-energy), for energy variables available in Abaqus/Explicit.

MASS

Set MASS=YES to request that a column containing the total mass of the model be printed in the status file. Set MASS=NO to suppress this printout. The default is MASS=NO. 

**There are no data lines associated with this option.**



