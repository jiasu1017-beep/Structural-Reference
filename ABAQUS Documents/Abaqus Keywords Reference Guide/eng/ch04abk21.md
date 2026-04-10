# *DIAGNOSTICS







### *DIAGNOSTICSControl diagnostic messages.

This option is used to request detailed diagnostic output or to cancel specific diagnostic checks. By default, short summaries of diagnostic checks are output if problems are detected during an analysis. In Abaqus/Explicit the diagnostics messages are written to the status (`.sta`) file or to the message (`.msg`) file.  In Abaqus/Standard the diagnostic messages are written to the data (`.dat`) file.

For a multistep analysis all parameter values remain the same during the analysis until they are redefined explicitly in the beginning of the next step.

**Products: **Abaqus/Standard  Abaqus/Explicit  

**Type: **Model data in Abaqus/Standard; History data in Abaqus/Explicit  

**Level: **Model in Abaqus/Standard; Step in Abaqus/Explicit  

##### **References:**

- ["Explicit dynamic analysis," Section 6.3.3 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-anl-aexpdynamic)
- ["Output and diagnostics for ALE adaptive meshing in Abaqus/Explicit," Section 12.2.5 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-anl-aaleoutput)
- ["Contact diagnostics in an Abaqus/Explicit analysis," Section 39.2.1 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-cni-aexpcontactdiagnostics)
- ["Linear elastic behavior," Section 22.2.1 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-mat-clinearelastic)
- ["Hyperelastic behavior of rubberlike materials," Section 22.5.1 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-mat-chyperelastic)
- [*CONTACT CONTROLS](ch03abk57.md)

### Defining diagnostics in an Abaqus/Explicit analysis

### **Optional parameters: **

ADAPTIVE MESH

Adaptive mesh information is written to the message (`.msg`) file for each adaptive mesh domain in the problem.

Set ADAPTIVE MESH=STEP SUMMARY (default) to obtain a summary at the end of the step. The summary gives the average number of advection sweeps per adaptive mesh increment and the average, maximum, and minimum percentages of nodes moved during the step.

Set ADAPTIVE MESH=SUMMARY to obtain a summary for each adaptive mesh increment. The summary gives the number of mesh sweeps, the average percentage of nodes moved during those mesh sweeps, and the number of advection sweeps performed during the adaptive mesh increment. In addition to this information, the STEP SUMMARY information will be written at the end of each step.

Set ADAPTIVE MESH=DETAIL to obtain detailed information about each adaptive mesh increment. The detailed report gives the number of mesh sweeps performed; the minimum, average, and maximum percentage of nodes moved during those mesh sweeps; the number of advection sweeps performed; the mass and momentum before and after advection; and the percentage volume change during the adaptive mesh increment. In addition to this information, the STEP SUMMARY information will be written at the end of each step.

Set ADAPTIVE MESH=OFF to suppress all diagnostic messages about adaptive meshing.

CONTACT INITIAL OVERCLOSURE

Set CONTACT INITIAL OVERCLOSURE=DETAIL (default) to write all of the initial displacements required to resolve initial overclosures to the message (`.msg`) file and a summary of the maximum initial overclosure for each contact pair to the status (`.sta`) file.

Set CONTACT INITIAL OVERCLOSURE=SUMMARY to obtain only a summary of the maximum initial overclosure for each contact pair in the status (`.sta`) file.

CRITICAL ELEMENTS

Set this parameter equal to the number of critical elements (elements having the smallest stable time increment) written to the output database diagnostic information. The default is 10.

CUTOFF RATIO

Set this parameter equal to the cutoff ratio of deformation speed versus wave speed (the default is 1.0). If the maximum ratio calculated is greater than this value, the analysis ends with an error message. The cutoff check is not applied to a model that has an equation of state material or a user-defined material.

DEEP PENETRATION FACTOR

Set this parameter equal to the fraction of the typical element face dimension in the general contact domain used to detect excessively deep penetrations (the default is 0.5). If during node-to-face contact the penetration of a node into its tracked face exceeds the deep penetration factor times the typical element face dimension in the general contact domain, a diagnostic message is issued. The deep penetration check does not apply to contact penetrations detected by the contact pair algorithm.

DEFORMATION SPEED CHECK

Set DEFORMATION SPEED CHECK=SUMMARY (default) to print messages for only the element with the greatest deformation speed to wave speed ratio in the model. This information is output to the status (`.sta`) file.

Set DEFORMATION SPEED CHECK=DETAIL to print messages for all elements with relatively large deformation speed. This information is output to the message (`.msg`) file.

Set DEFORMATION SPEED CHECK=OFF to suppress the deformation speed check.

DETECT CROSSED SURFACES

This parameter applies only to general contact.

Set DETECT CROSSED SURFACES=ON (default) to issue warning messages for instances of adjacent slaves being on opposite sides of master surfaces in the initial configuration.

Set DETECT CROSSED SURFACES=OFF to suppress this diagnostic.

PLASTICITY

Set PLASTICITY=SUMMARY (default) to obtain a summary of the total number of material points at which the plasticity algorithms have not converged. This information will be printed only at the first occurrence in the status (`.sta`) file.

Set PLASTICITY=DETAIL to obtain detailed information about the elements at which the plasticity algorithms have not converged. This information will be printed in the message (`.msg`) file. This request may cause the analysis to run for a longer time. It is currently available only for Mises plasticity.

Set PLASTICITY=OFF to suppress all of the diagnostic messages about the plasticity algorithms.

WARNING RATIO

Set this parameter equal to the warning ratio of deformation speed versus wave speed (the default ratio is 0.3). If the ratio calculated in an element is greater than this value, a warning message will be printed to the status (`.sta`) file or the message (`.msg`) file.

WARPED SURFACE

Set WARPED SURFACE=SUMMARY (default) to obtain a warning message in the status (`.sta`) file when a surface is first considered to contain at least one highly warped facet. 

Set WARPED SURFACE=DETAIL to have detailed warning messages also output to the message (`.msg`) file. 

Set WARPED SURFACE=OFF to suppress all warnings about warped surfaces.

**There are no data lines associated with this option.**

### Defining diagnostics in an Abaqus/Standard analysis

### **Optional parameter: **

NONHYBRID INCOMPRESSIBLE

If a model has nearly incompressible elastic or hyperelastic materials with an effective initial Poisson's ratio greater than 0.495 (i.e., the ratio of the initial bulk modulus to the initial shear modulus is greater than 100) used in nonbybrid continuum elements (except plane stress elements), error messages are written to the data (`.dat`) file during preprocessing. 

Set NONHYBRID INCOMPRESSIBLE=WARNING to replace the error messages with corresponding warning messages.

**There are no data lines associated with this option.**




