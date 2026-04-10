# *CO-SIMULATION







### *CO-SIMULATIONIdentify the analysis program for co-simulation with Abaqus.

This option is used to identify the analysis program for co-simulation with Abaqus and the co-simulation controls used to define the coupling and rendezvousing scheme.

**Products: **Abaqus/Standard  Abaqus/Explicit  Abaqus/CFD  Abaqus/CAE  

**Type: **History data 

**Level: **Step

**Abaqus/CAE: **Interaction module

##### **References:**

- ["Co-simulation: overview," Section 17.1.1 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-anl-acosimulationover)
- ["Preparing an Abaqus analysis for co-simulation," Section 17.2.1 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-anl-acosimulationprep)
- ["Structural-to-structural co-simulation," Section 17.3.1 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-anl-acosimabqtoabq)
- ["Fluid-to-structural and conjugate heat transfer co-simulation," Section 17.3.2 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-anl-acosimcfdtoabq)
- [*CO-SIMULATION CONTROLS](ch03abk79.md)
- [*CO-SIMULATION REGION](ch03abk80.md)

### **Required parameters: **

NAME

Set this parameter equal to a label that will be used to refer to the co-simulation event. The co-simulation name adheres to the naming convention for labels (see ["Input syntax rules," Section 1.2.1 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-int-iinputsyntax)), except that it cannot begin with a number.

PROGRAM

Set PROGRAM=MULTIPHYSICS for exchange of data between Abaqus and the SIMULIA Co-Simulation Engine, which in turn can exchange data with third-party analysis programs that support the SIMULIA Co-Simulation Engine. This parameter should also be used in an Abaqus/CFD to Abaqus/Standard or Abaqus/CFD to Abaqus/Explicit co-simulation.

Set PROGRAM=ABAQUS for exchange of data with another Abaqus analysis in an Abaqus/Standard to Abaqus/Explicit co-simulation.

Set PROGRAM=DIRECT for exchange of data between Abaqus and certain third-party analysis programs. For more information, refer to the appropriate third-party program documentation.

Set PROGRAM=MPCCI for exchange of data between Abaqus and the Mesh-based parallel Code Coupling Interface (MpCCI), which in turn can exchange data with third-party analysis programs supporting MpCCI. 

### **Optional parameter: **

CONTROLS

This parameter is required when PROGRAM=ABAQUS or PROGRAM=MPCCI.

Set this parameter equal to the name of the co-simulation controls to be used to define the coupling and rendezvousing scheme.

For PROGRAM=DIRECT or PROGRAM=MULTIPHYSICS, the co-simulation controls are defined in the co-simulation configuration file.

**There are no data lines associated with this option.**



