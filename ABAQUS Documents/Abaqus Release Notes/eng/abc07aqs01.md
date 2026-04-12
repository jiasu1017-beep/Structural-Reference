# 7.1 Support for coupled temperature–pore pressure elements in Abaqus/CAE







### 7.1 Support for coupled temperature--pore pressure elements in Abaqus/CAE

**Product: **Abaqus/CAE  

**Benefits: **You can now assign element types from the coupled temperature–pore pressure family of elements to your model in Abaqus/CAE.

**Description: **Coupled temperature–pore pressure elements are used in Abaqus/Standard for modeling fully or partially saturated fluid flow through a deforming porous medium in which the stress, fluid pore pressure, and temperature fields are fully coupled to one another. The **Element Type** dialog box in the Mesh module now enables you to assign element types from the coupled temperature–pore pressure family of elements, which includes element types C3D8PT, C3D8PHT, C3D8RPT, C3D8RPHT, and C3D10MPT.

**Abaqus/CAE Usage: **
```
Mesh module
    ****Mesh**![](../graphics/images/arrow.gif)**Element Type****: **Family**: **Coupled Temperature-Pore pressure**
```

**References: **

**Abaqus Analysis User's Guide**
- ["Three-dimensional solid element library," Section 28.1.4](../usb/usb-link.md#usb-elm-e3delem)

**Abaqus/CAE User's Guide**
- ["Element type assignment," Section 17.5.3](../usi/usi-link.md#usi-mgn-conc-elem-assign)




