# *REFLECTION







### *REFLECTIONDefine reflection symmetries for a cavity radiation heat transfer analysis.

This option is used to define a cavity symmetry by reflection through a line or a plane. It can be used only following the [*RADIATION SYMMETRY](ch17abk05.md) option.

**Products: **Abaqus/Standard  Abaqus/CAE  

**Type: **History data 

**Level: **Step

**Abaqus/CAE: **Interaction module

##### **References:**

- ["Cavity radiation," Section 41.1.1 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-cni-acavityradiation)
- [*RADIATION SYMMETRY](ch17abk05.md)

### **Required parameter: **

TYPE

Set TYPE=LINE to create a cavity composed of the cavity surface defined in the model and its reflection through a line. See [Figure 17.13--1](ch17abk13.md#kreflection-line). This option can be used only for two-dimensional cases.

Set TYPE=PLANE to create a cavity composed of the cavity surface defined in the model and its reflection through a plane. See [Figure 17.13--2](ch17abk13.md#kreflection-plane). This option can be used only for three-dimensional cases.

Set TYPE=ZCONST to create a cavity composed by the cavity surface defined in the model and its reflection through a line of constant *z*-coordinate. See [Figure 17.13--3](ch17abk13.md#kreflection-zconst). This option can be used only for axisymmetric cases.

### **Data line to define reflection of a two-dimensional cavity (TYPE=LINE): **

**First (and only) line:**

### **Data lines to define reflection of a three-dimensional cavity (TYPE=PLANE): **

**First line:**

**Second line:**

### **Data line to define reflection of an axisymmetric cavity (TYPE=ZCONST): **

**First (and only) line:**

**Figure 17.13–1** [*REFLECTION](ch17abk13.md), TYPE=LINE option.

![](../graphics/kreflection-line.png)

**Figure 17.13–2** [*REFLECTION](ch17abk13.md), TYPE=PLANE option.

![](../graphics/kreflection-plane.png)

**Figure 17.13–3** [*REFLECTION](ch17abk13.md), TYPE=ZCONST option.

![](../graphics/kreflection-zconst-nls.png)




