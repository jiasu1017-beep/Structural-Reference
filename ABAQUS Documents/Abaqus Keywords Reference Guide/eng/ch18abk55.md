# *SURFACE SMOOTHING







### *SURFACE SMOOTHINGDefine surface smoothing methods.

This option is used to create a surface smoothing definition for contact interactions. It must be used in conjunction with the [*CONTACT PAIR](ch03abk68.md) option. The defined smoothing methods apply to the specified regions of the surfaces in the referenced contact pair.

**Products: **Abaqus/Standard  Abaqus/CAE  

**Type: **Model data  

**Level: **Model  

**Abaqus/CAE: **Interaction module

##### **Reference:**

- ["Smoothing contact surfaces in Abaqus/Standard," Section 38.1.3 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-cni-asmoothsurfaces)

### **Required parameter: **

NAME

Set this parameter equal to a label that will be used to refer to this surface smoothing definition.

This label is referred to by the GEOMETRIC CORRECTION parameter on the [*CONTACT PAIR](ch03abk68.md) option.

### **Data lines to define the surface regions on which smoothing is applied: **

**Data line to define smoothing on regions of two-dimensional surfaces that correspond (or nearly correspond) to a circular arc (see [Figure 18.55--1](ch18abk55.md#msmoothcir2d-surfacesmoothing)):**

**Data line to define smoothing on regions of surfaces that correspond (or nearly correspond) to a surface of revolution (see [Figure 18.55--2](ch18abk55.md#msmoothcir3d-surfacesmoothing)):**

**Figure 18.55–2** Three-dimensional circumferential smoothing.

![](../graphics/usb-kws-msmoothcir3d-nls.png)

**Data line to define smoothing on regions of surfaces that correspond (or nearly correspond) to a sphere section (see [Figure 18.55--3](ch18abk55.md#msmoothsph3d-surfacesmoothing)):**

**Figure 18.55–3** Spherical smoothing.

![](../graphics/usb-kws-msmoothsph3d-nls.png)

**Data line to define smoothing on regions of surfaces that correspond (or nearly correspond) to a toroidal surface (see [Figure 18.55--4](ch18abk55.md#msmoothtor3d-surfacesmoothing)):**

Repeat the above data lines as often as necessary to define all surface regions that require smoothing.

**Figure 18.55–4** Three-dimensional toroidal smoothing.

![](../graphics/usb-kws-msmoothtor3d-nls.png)




