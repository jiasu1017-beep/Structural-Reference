# *BASE MOTION







### *BASE MOTIONDefine the base motion for linear, eigenmode-based, dynamic procedures.

This option is relevant only during linear dynamics procedures that use the natural modes of the system ([*STEADY STATE DYNAMICS](ch18abk34.md) without the DIRECT parameter, [*MODAL DYNAMIC](ch13abk18.md), and [*RANDOM RESPONSE](ch17abk07.md)).

**Products: **Abaqus/Standard  

**Type: **History data 

**Level: **Step

##### **References:**

- ["Natural frequency extraction," Section 6.3.5 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-anl-afreqextraction)
- ["Transient modal dynamic analysis," Section 6.3.7 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-anl-amodaldynamic)
- ["Mode-based steady-state dynamic analysis," Section 6.3.8 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-anl-asteadystdyn)
- ["Random response analysis," Section 6.3.11 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-anl-arandomresponse)

### **Required parameter: **

DOF

Set this parameter equal to the direction (1–6, including rotations) for which the base motion is being defined. This direction is always a global direction.

Set this parameter equal to 8 for the acoustic degree of freedom, which is for use for secondary base motions only in the SIM-based architecture.

### **Required parameter for [*MODAL DYNAMIC](ch13abk18.md) and [*STEADY STATE DYNAMICS](ch18abk34.md) analyses: **

AMPLITUDE

Set this parameter equal to the name of the [*AMPLITUDE](ch01abk09.md) option that defines the time history ([*MODAL DYNAMIC](ch13abk18.md)) or frequency spectrum ([*STEADY STATE DYNAMICS](ch18abk34.md)) of the motion. This parameter is irrelevant for the [*RANDOM RESPONSE](ch17abk07.md) procedure. The parameter DEFINITION=SOLUTION DEPENDENT cannot be used in an [*AMPLITUDE](ch01abk09.md) referenced by this option.

### **Optional parameters: **

BASE NAME

Set this parameter equal to the name of the base if this base motion is to be applied to a secondary base. The base name is defined with the BASE NAME parameter on the [*BOUNDARY](ch02abk12.md) option in the [*FREQUENCY](ch06abk35.md) step.

LOAD CASE

Set this parameter equal to the load case number. This parameter is used in [*RANDOM RESPONSE](ch17abk07.md) analysis, where it is the cross-reference for the load case on the [*CORRELATION](ch03abk77.md) option.

SCALE

Set this parameter equal to the scale factor for the amplitude curve. The default is SCALE=1.0. This parameter applies during [*MODAL DYNAMIC](ch13abk18.md) and [*STEADY STATE DYNAMICS](ch18abk34.md) procedures. 

TYPE

Set TYPE=ACCELERATION (default), VELOCITY, or DISPLACEMENT.

### **Optional, mutually exclusive parameters for steady-state dynamics analysis: **

IMAGINARY

Include this parameter to define the imaginary (out-of-phase) part of the base motion record given by the amplitude definition.

REAL

Include this parameter (default) to define the real (in-phase) part of the base motion record given by the amplitude definition.

### **There are no data lines associated with this option unless a primary base motion defines rotation about a point that is not the origin of the coordinate system. **

### **Data line to define the center of rotation for a prescribed rotation: **

**First (and only) line:**

This data line is relevant only for a primary base motion defined in the [*MODAL DYNAMIC](ch13abk18.md) and [*STEADY STATE DYNAMICS](ch18abk34.md) procedures.




