# *BEAM FLUID INERTIA







### *BEAM FLUID INERTIADefine additional beam inertia due to immersion in a fluid.

This option is used in conjunction with the [*BEAM SECTION](ch02abk06.md) or [*BEAM GENERAL SECTION](ch02abk05.md) option to include added inertia effects in Timoshenko beam elements due to immersion in an inviscid fluid.

**Products: **Abaqus/Standard  Abaqus/Explicit  Abaqus/CAE  

**Type: **Model data  

**Level: **Part,  Part instance,  Assembly  

**Abaqus/CAE: **Property module

##### **References:**

- ["Beam section behavior," Section 29.3.5 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-elm-ebeamsectionbehavior)
- ["Acoustic, shock, and coupled acoustic-structural analysis," Section 6.10.1 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-anl-aacoustic)
- ["Loading due to an incident dilatational wave field," Section 6.3.1 of the Abaqus Theory Guide](../stm/stm-link.md#stm-ldc-undexloads)

### **Optional, mutually exclusive parameters: **

FULL

Use this parameter to specify a fully submerged beam (default).

HALF

Use this parameter to specify a half-submerged beam.

### **Data line to define beam fluid inertia: **

**First (and only) line:**




