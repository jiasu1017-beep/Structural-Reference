# 5.10 Enhancements to the SIMULIA Co-Simulation Engine







**Products: **Abaqus/Standard  Abaqus/Explicit  

**Benefits: **The SIMULIA Co-Simulation Engine is enhanced to allow the definition of multiple co-simulation regions and to provide a configuration file upgrade capability.

**Description: **The SIMULIA Co-Simulation Engine  now supports multiple regions and multiple fields for Abaqus/Standard and Abaqus/Explicit coupled with certain partner products. A client can specify one or more regions as its co-simulation interface. The co-simulation interface region can be a set of discrete points, a surface region, a volume region, or a mixture of these types.  Corresponding regions between clients need to be of the same region type, co-located, and have the same region boundaries.

Multiple regions can be used for:
- Transferring different field types across different co-simulation interfaces
- Coupling between points, surface regions, and volume regions
- Assigning different search and mapping tolerances in areas of complex geometry where mapping difficulties are expected

The CSE director process can automatically upgrade the schema for the configuration file from previous releases.
**References: **

**Abaqus Analysis User's Guide**
- ["SIMULIA Co-Simulation Engine director execution," Section 3.2.3](../usb/usb-link.md#usb-int-dcosimcontrolproc)
- ["Co-simulation: overview," Section 17.1.1](../usb/usb-link.md#usb-anl-acosimulationover)




