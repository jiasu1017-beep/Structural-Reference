# *CO-SIMULATION CONTROLS







### *CO-SIMULATION CONTROLSSpecify the coupling and rendezvousing scheme for co-simulation.

This option is used to specify the coupling and rendezvousing scheme for co-simulation. It must be used in conjunction with the [*CO-SIMULATION](ch03abk78.md) option to identify the analysis program for which the co-simulation controls are specified. This option is required for co-simulation when PROGRAM=ABAQUS or PROGRAM=MPCCI is used on the [*CO-SIMULATION](ch03abk78.md) option.

**Products: **Abaqus/Standard  Abaqus/Explicit  Abaqus/CFD  Abaqus/CAE  

**Type: **History data 

**Level: **Step

**Abaqus/CAE: **Interaction module

##### **References:**

- ["Co-simulation: overview," Section 17.1.1 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-anl-acosimulationover)
- ["Preparing an Abaqus analysis for co-simulation," Section 17.2.1 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-anl-acosimulationprep)
- ["Structural-to-structural co-simulation," Section 17.3.1 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-anl-acosimabqtoabq)
- ["Fluid-to-structural and conjugate heat transfer co-simulation," Section 17.3.2 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-anl-acosimcfdtoabq)
- [*CO-SIMULATION](ch03abk78.md)
- [*CO-SIMULATION REGION](ch03abk80.md)

### Specifying the coupling and rendezvousing scheme for CO-SIMULATION, PROGRAM=ABAQUS

### **Required parameter: **

NAME

Set this parameter equal to the label that will be used to identify the co-simulation controls. All co-simulation control names in the same input file must be unique.

### **Optional parameters: **

FACTORIZATION FREQUENCY

This parameter is valid when used with the TIME INCREMENTATION=SUBCYCLE parameter.

Set FACTORIZATION FREQUENCY=EXPLICIT INCREMENT (default) to specify factoring of the interface matrix every Abaqus/Explicit increment.

Set FACTORIZATION FREQUENCY=STANDARD INCREMENT to specify factoring of the interface matrix once per Abaqus/Standard increment.

TIME INCREMENTATION

Set TIME INCREMENTATION=SUBCYCLE (default) to allow Abaqus to take one or more increments to reach the next target time to exchange data with the external program. This setting is valid only in an Abaqus/Standard or Abaqus/Explicit analysis.

Set TIME INCREMENTATION=LOCKSTEP to force Abaqus to use only one increment to reach the next target time.

**There are no data lines associated with this option.**

### Specifying the coupling and rendezvousing scheme for CO-SIMULATION, PROGRAM=MPCCI

### **Required parameters: **

NAME

Set this parameter equal to the label that will be used to identify the co-simulation controls. All co-simulation control names in the same input file must be unique.

STEP SIZE

Set this parameter equal to a value that defines the constant coupling step size to be used throughout the coupled simulation.

Set STEP SIZE=IMPORT for Abaqus to import a coupling step size from the external program for the next coupling step. 

Set STEP SIZE=EXPORT for Abaqus to export a coupling step size to the external program for the next coupling step. 

Set STEP SIZE=MAX for Abaqus to select the maximum coupling step size based on the suggested coupling step size of Abaqus and the external program. 

Set STEP SIZE=MIN for Abaqus  to select the minimum coupling step size based on the suggested coupling step size of Abaqus and the external program. 

**There are no data lines associated with this option.**




