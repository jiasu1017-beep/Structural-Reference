# *INCIDENT WAVE







### *INCIDENT WAVEDefine incident wave loading for a blast or scattering load on a boundary.

The preferred interface for applying incident wave loading is the [*INCIDENT WAVE INTERACTION](ch09abk10.md) option used in conjunction with the [*INCIDENT WAVE INTERACTION PROPERTY](ch09abk11.md) option. The alternative interface uses the [*INCIDENT WAVE](ch09abk08.md) option to apply incident wave loading.

The [*INCIDENT WAVE PROPERTY](ch09abk12.md) option must be used in conjunction with the [*INCIDENT WAVE](ch09abk08.md) option. If the incident wave field includes a reflection off a plane outside the boundaries of the mesh, this effect can be modeled with the [*INCIDENT WAVE REFLECTION](ch09abk13.md) option.

**Products: **Abaqus/Standard  Abaqus/Explicit  Abaqus/CAE  

**Type: **History data 

**Level: **Step

**Abaqus/CAE: **Unsupported; this option has been superseded by incident wave interactions.

##### **References:**

- ["Acoustic, shock, and coupled acoustic-structural analysis," Section 6.10.1 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-anl-aacoustic)
- ["Acoustic and shock loads," Section 34.4.6 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-prc-pacoustic)
- [*INCIDENT WAVE PROPERTY](ch09abk12.md)
- [*INCIDENT WAVE REFLECTION](ch09abk13.md)

### **Required parameter: **

PROPERTY

Set this parameter equal to the name of the [*INCIDENT WAVE PROPERTY](ch09abk12.md) option defining the incident wave field.

### **Required, mutually exclusive parameters: **

ACCELERATION AMPLITUDE

Set this parameter equal to the name of the amplitude curve defining the fluid particle acceleration time history at the standoff point (["Amplitude curves," Section 34.1.2 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-prc-pamplitude)). This amplitude curve will be used to compute the fluid traction *only*: a solid surface requiring a pressure load cannot be specified on the data line of an [*INCIDENT WAVE](ch09abk08.md) option if the ACCELERATION AMPLITUDE parameter is used.

This parameter is valid only for planar incident waves using the [*INCIDENT WAVE PROPERTY](ch09abk12.md), TYPE=PLANE option. Reflected loads, using the [*INCIDENT WAVE REFLECTION](ch09abk13.md) option, are not permitted in this case.

PRESSURE AMPLITUDE

Set this parameter equal to the name of the amplitude curve defining the fluid pressure time history at the standoff point (["Amplitude curves," Section 34.1.2 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-prc-pamplitude)). The corresponding fluid traction, if required, will be computed from the pressure amplitude reference.

### **Data lines to define an incident wave: **

**First line:**

Repeat this data line as often as necessary to describe the loading on the surfaces due to the incident wave. In problems involving fluid-solid boundaries, both the fluid surface and the solid surface comprising the boundary must have an incident wave load specified, using the appropriate load type.




