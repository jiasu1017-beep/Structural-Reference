# *SURFACE INTERACTION







### *SURFACE INTERACTIONDefine surface interaction properties.

This option is used to create a surface interaction property definition. The surface interaction properties will govern any contact interactions that reference this surface interaction.

**Products: **Abaqus/Standard  Abaqus/Explicit  Abaqus/CAE  

**Type: **Model data in Abaqus/Standard; Model or history data in Abaqus/Explicit  

**Level: **Model in Abaqus/Standard; Model or Step in Abaqus/Explicit  

**Abaqus/CAE: **Interaction module

##### **References:**

- ["Assigning surface properties for contact pairs in Abaqus/Explicit," Section 36.5.2 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-cni-acontactpairsurfaces)
- ["Mechanical contact properties: overview," Section 37.1.1 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-cni-acontactmechanical)
- ["Contact pressure-overclosure relationships," Section 37.1.2 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-cni-anormalinteraction)
- ["Contact damping," Section 37.1.3 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-cni-acontactdamping)
- ["Frictional behavior," Section 37.1.5 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-cni-afriction)
- ["User-defined interfacial constitutive behavior," Section 37.1.6 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-cni-auserinteraction)
- ["Breakable bonds," Section 37.1.9 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-cni-aspotweld)
- ["Thermal contact properties," Section 37.2.1 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-cni-athermalinteraction)
- ["Electrical contact properties," Section 37.3.1 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-cni-ajouleheatinteraction)
- ["Pore fluid contact properties," Section 37.4.1 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-cni-aporefluidinteraction)
- ["UINTER," Section 1.1.39 of the Abaqus User Subroutines Reference Guide](../sub/sub-link.md#sub-rtn-uuinter)
- ["VUINTER," Section 1.2.18 of the Abaqus User Subroutines Reference Guide](../sub/sub-link.md#sub-rtn-uexpinter)
- ["VUINTERACTION," Section 1.2.19 of the Abaqus User Subroutines Reference Guide](../sub/sub-link.md#sub-rtn-uexpuinteraction)

### **Required parameter: **

NAME

Set this parameter equal to a label that will be used to refer to this surface interaction property.

Use this label on the INTERACTION parameter of the [*CONTACT PAIR](ch03abk68.md) option (for an Abaqus/Standard contact analysis or an Abaqus/Explicit analysis using the contact pair algorithm) or on the data line of the [*CONTACT PROPERTY ASSIGNMENT](ch03abk71.md) option (for an Abaqus/Explicit analysis using the general contact algorithm) to assign this surface interaction property to a contact interaction.

### **Optional parameters: **

DEPVAR

This parameter is relevant only when the USER parameter is included.

Set DEPVAR equal to the number of state-dependent variables required for user subroutine [`UINTER`](../sub/sub-link.md#sub-xsl-uinter) in an Abaqus/Standard analysis or for user subroutine [`VUINTER`](../sub/sub-link.md#sub-xsl-vuinter) or [`VUINTERACTION`](../sub/sub-link.md#sub-xsl-vuinteraction) in an Abaqus/Explicit analysis. The default is DEPVAR=0.

PAD THICKNESS

This parameter applies only to Abaqus/Explicit analyses using the contact pair algorithm.

Set this parameter equal to the thickness of an interfacial layer between the contacting surfaces. The value can be positive or negative.

PROPERTIES

This parameter is relevant only when the USER parameter is included.

Set this parameter equal to the number of property values needed as data to define the surface interaction model in user subroutine [`UINTER`](../sub/sub-link.md#sub-xsl-uinter) in an Abaqus/Standard analysis or in user subroutine [`VUINTER`](../sub/sub-link.md#sub-xsl-vuinter) or [`VUINTERACTION`](../sub/sub-link.md#sub-xsl-vuinteraction) in an Abaqus/Explicit analysis. The default is PROPERTIES=0.

 This parameter is ignored when the option is used in association with a connector element.

TRACKING THICKNESS

Set this parameter equal to the thickness that determines the contacting surfaces to be tracked.

In Abaqus/Standard the tracking range will be at least as large as the setting of this parameter; an internally computed default will remain in effect if this parameter setting is less than the default. In Abaqus/Standard this parameter extends the range over which contact opening distance (COPEN) output is provided for separated surfaces.

In Abaqus/Explicit this parameter applies only if user subroutine [`VUINTER`](../sub/sub-link.md#sub-xsl-vuinter) or [`VUINTERACTION`](../sub/sub-link.md#sub-xsl-vuinteraction) is also in effect. Only contacting surfaces whose proximity is within this thickness are available for user-defined interactions. This parameter affects only node-to-surface contact, and the input value for this parameter cannot be negative. An internal default value is used if a zero value is input or if the parameter is omitted.

UNSYMM

This parameter applies only to Abaqus/Standard analyses in which the USER parameter is included.

Include this parameter when the interface stiffness matrix is not symmetric. This parameter causes Abaqus/Standard to use its unsymmetric equation solution procedures.

USER

In an Abaqus/Standard analysis, include this parameter if the surface interaction model is to be defined in user subroutine [`UINTER`](../sub/sub-link.md#sub-xsl-uinter)

In an Abaqus/Explicit analysis, include this parameter without any assignment if the surface interaction model is to be defined in user subroutine [`VUINTER`](../sub/sub-link.md#sub-xsl-vuinter). Set USER=INTERACTION if the surface interaction model is to be defined in user subroutine [`VUINTERACTION`](../sub/sub-link.md#sub-xsl-vuinteraction). [`VUINTER`](../sub/sub-link.md#sub-xsl-vuinter) is applicable to contact pairs, whereas [`VUINTERACTION`](../sub/sub-link.md#sub-xsl-vuinteraction) is applicable to general contact. 

When this parameter is included, the [*SURFACE BEHAVIOR](ch18abk48.md) option and its various suboptions cannot be used under the same interaction definition.

### **Optional data line for two-dimensional models in Abaqus/Standard or for contact pairs involving node-based surfaces in Abaqus/Standard, if the USER parameter is omitted: **

**First (and only) line:**

### **Data lines to define the surface interaction in an Abaqus/Standard analysis if the USER parameter is used: **

**First line:**

**Second line (needed only if the PROPERTIES parameter is used):**

Repeat this data line as often as necessary to define all material constants.

### **Data lines to define the surface interaction in an Abaqus/Explicit analysis if the PROPERTIES parameter is used: **

**First line:**

**Second line:**

Repeat this data line as often as necessary to define all material constants.




