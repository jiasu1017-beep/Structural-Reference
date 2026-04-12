# 5.11 Enhancements for co-simulation







**Products: **Abaqus/Standard  Abaqus/Explicit  Abaqus/CFD  

**Benefits: **Several enhancements, including support for volume coupling, exchanging thermal fields on both faces of shell elements, and configuration file generation for third-party clients, improve the usability of the co-simulation technique.

**Description: **The following enhancements for co-simulation are available:
- Abaqus/Explicit now supports co-simulation where the interface region is a volume. Volume coupling allows coupling physics where the interface occupies the same space, as in the case of electromagnetic-to-structural coupling.
- In Abaqus/Standard and Abaqus/Explicit thermal fields can now be exchanged on both the SPOS and SNEG faces of shell elements. In previous releases only the SPOS or SNEG face was supported for thermal coupling. If both sides are loaded, you must define two regions, one containing the SPOS faces and the other containing the SNEG faces.
- In the SIMULIA Co-Simulation Engine configuration file, you can now specify the treatment for nodes and elements for which no intersection is found during the spatial mapping. You can specify a default value or specify that the value of the nearest neighbor node or element is to be used.
- The input file preprocessor for Abaqus/Standard and Abaqus/Explicit now writes a model description file that contains the co-simulation definitions (e.g., region names, field and their causality, etc.) This information can be used by a third-party client to generate the co-simulation configuration file without having to parse the Abaqus input file.
- The Run Time Environment (SRE) of the SIMULIA Co-Simulation Engine now supports version control. If incompatible SRE libraries are detected in either the CSE director or any of the clients, the co-simulation is terminated with an appropriate message.

**Reference: **

**Abaqus Analysis User's Guide**
- ["Preparing an Abaqus analysis for co-simulation," Section 17.2.1](../usb/usb-link.md#usb-anl-acosimulationprep)




