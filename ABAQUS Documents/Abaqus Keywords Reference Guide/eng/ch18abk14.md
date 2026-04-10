# *SHELL GENERAL SECTION







### *SHELL GENERAL SECTIONDefine a general, arbitrary, elastic shell section.

This option is used to define a general, arbitrary, elastic shell section.

**Products: **Abaqus/Standard  Abaqus/Explicit  Abaqus/CAE  

**Type: **Model data  

**Level: **Part,  Part instance  

**Abaqus/CAE: **Property module

##### **References:**

- ["Shell elements: overview," Section 29.6.1 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-elm-eshelloverview)
- ["Using a general shell section to define the section behavior," Section 29.6.6 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-elm-eusingshellgensect)
- ["UGENS," Section 1.1.35 of the Abaqus User Subroutines Reference Guide](../sub/sub-link.md#sub-rtn-uugens)

### **Required parameter: **

ELSET

Set this parameter equal to the name of the element set containing the shell elements for which the section behavior is being defined.

### **Required parameter in Abaqus/Explicit, optional parameter in Abaqus/Standard: **

DENSITY

Set this parameter equal to the mass per unit surface area of the shell.

If the MATERIAL and COMPOSITE parameters are omitted, this density accounts for the mass of the shell, since no material definition is given.

If the MATERIAL or COMPOSITE parameter is used, the mass of the shell includes a contribution from this parameter in addition to any contribution from the material definition.

### **Optional parameters: **

BENDING ONLY

Include this parameter to ignore membrane stiffness effects in the shell. Bending stiffness and transverse shear stiffness coefficients are computed normally. Membrane-bending coupling coefficients are set to zero. Diagonal membrane stiffness coefficients are set to 1  106 times the largest diagonal bending stiffness term. Off-diagonal membrane stiffness coefficients are set to zero.

CONTROLS

In an Abaqus/Explicit analysis, set this parameter equal to the name of a section controls definition (see ["Section controls," Section 27.1.4 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-elm-esectioncontrol)) to be used to specify the second-order accurate element formulation option, a nondefault hourglass control formulation option, or scale factors.

In an Abaqus/Standard analysis, set this parameter equal to the name of a section controls definition to be used to specify the enhanced hourglass control formulation (see ["Section controls," Section 27.1.4 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-elm-esectioncontrol)) or to be used in a subsequent Abaqus/Explicit import analysis.

LAYUP

This parameter is relevant only when the COMPOSITE parameter is used.

Set this parameter equal to the name of a composite layup (see [Chapter 23, "Composite layups," of the Abaqus/CAE User's Guide](../usi/usi-link.md#usi-adv-layups)). Abaqus/CAE uses this name to identify the composite layup that contains the shell section. 

MEMBRANE ONLY

Include this parameter to ignore bending stiffness effects in the shell. Membrane stiffness and transverse shear stiffness coefficients are computed normally. Membrane-bending coupling coefficients are set to zero. Diagonal bending stiffness coefficients are set to 1  106 times the largest diagonal membrane stiffness term. Off-diagonal bending stiffness coefficients are set to zero.

OFFSET

Include this parameter to define the distance (as a fraction of the shell thickness) from the shell midsurface to the reference surface (containing the nodes of the element). This parameter accepts positive or negative values, the labels SPOS or SNEG, or in  an Abaqus/Standard analysis the name of a distribution (see ["Distribution definition," Section 2.8.1 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-int-adefiningdistributions)).

Positive values of the offset are in the positive normal direction (see ["Shell elements: overview," Section 29.6.1 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-elm-eshelloverview)). When OFFSET=0.5 (or SPOS), the top surface of the shell is the reference surface. When OFFSET=0.5 (or SNEG), the bottom surface of the shell is the reference surface.  The default is OFFSET=0, which indicates that the middle surface of the shell is the reference surface.  This parameter is ignored for continuum shells.

In an Abaqus/Standard analysis a spatially varying offset can be specified by setting OFFSET equal to the name of a distribution. The distribution used to define the shell offset must have a default value. The default offset is used by any shell element assigned to the shell section that is not specifically assigned a value in the distribution.

ORIENTATION

Set this parameter equal to the name of an orientation definition (see ["Orientations," Section 2.2.5 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-int-corientation)) to be used with the section forces and section strains.

POISSON

Include this parameter to define the shell thickness direction behavior. 

Set this parameter equal to a nonzero value to cause the thickness direction strain under plane stress conditions to be a linear function of the membrane strains. The value of the POISSON parameter must be between 1.0 and 0.5. 

Set POISSON=ELASTIC to automatically select this parameter value based on the initial isotropic elastic part of the material definition.

The default is POISSON=0.5.

SMEAR ALL LAYERS

This parameter is relevant only when the COMPOSITE parameter is used.

Include this parameter to ignore the material layer stacking sequence. Transverse shear stiffness coefficients are computed normally. Membrane-bending coupling terms are set to zero, and bending stiffness terms are computed as *T* 2/12 times the corresponding membrane stiffness terms, where *T* is the total thickness of the shell.

STACK DIRECTION

This parameter is relevant only for continuum shells.

Set this parameter equal to 1, 2, 3, or ORIENTATION to define the continuum shell stack or thickness direction. Specify one of the numerical values to select the corresponding isoparametric direction of the element as the stack or thickness direction. The default is STACK DIRECTION=3.

If STACK DIRECTION=ORIENTATION, the ORIENTATION parameter is also required.

To obtain a desired thickness direction, the appropriate numerical value for the STACK DIRECTION parameter depends on the element connectivity. For a mesh-independent specification, use STACK DIRECTION=ORIENTATION.  If the orientation assigned to the ORIENTATION parameter is defined with a distribution (["Distribution definition," Section 2.8.1 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-int-adefiningdistributions)), STACK DIRECTION=ORIENTATION is not supported.

SYMMETRIC

This parameter is relevant only when the COMPOSITE parameter is used.

Include this parameter if the layers in the composite shell are symmetric about a central core. This parameter cannot be used if a spatially varying thickness or orientation angle is defined on any composite layer using a distribution (["Distribution definition," Section 2.8.1 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-int-adefiningdistributions)).

THICKNESS MODULUS

This parameter is relevant only for continuum shells.

Set this parameter equal to an effective thickness modulus. The default effective thickness modulus is twice the initial in-plane shear modulus based on the material definition.

ZERO

If the section is defined by its general stiffness, set this parameter equal to ![](../graphics/key_eqn00086.gif), the reference temperature for thermal expansion (for example, ZERO=50 means ![](../graphics/key_eqn01068.gif)).

This parameter is ignored if the COMPOSITE, the MATERIAL, or the USER parameter is specified.

### **The following parameters are optional, mutually exclusive, and used only if the section is not defined by its general stiffness on the data lines: **

COMPOSITE

Include this parameter to indicate that the shell is composed of layers with different linear elastic material behavior.

MATERIAL

Set this parameter equal to the name of the single linear elastic material of which the shell is made.

USER

This parameter applies only to Abaqus/Standard analyses and cannot be used with continuum shell elements. See ["Using a general shell section to define the section behavior," Section 29.6.6 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-elm-eusingshellgensect), for use of this option in linear perturbation analyses.

Include this parameter to indicate that the shell section stiffness is defined in user subroutine [`UGENS`](../sub/sub-link.md#sub-xsl-ugens).

### **The following parameters are optional, mutually exclusive, and can be used only in combination with the MATERIAL, the COMPOSITE, or the USER parameter: **

NODAL THICKNESS

Include this parameter to indicate that the shell thickness should not be read from the data lines but should be interpolated from the thickness specified at the nodes with the [*NODAL THICKNESS](ch14abk08.md) option. For composite sections the total thickness is interpolated from the nodes, and the thicknesses of the layers specified on the data lines are scaled proportionally. This parameter is ignored for continuum shells.

SHELL THICKNESS

Set this parameter equal to the name of a distribution (["Distribution definition," Section 2.8.1 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-int-adefiningdistributions)) to define spatially varying thickness. If this parameter is used for a non-composite section, the thickness on the data line is ignored. For composite sections the total thickness is defined by the distribution, and the thicknesses of the layers specified on the data lines are scaled proportionally. This parameter is ignored for continuum shells. 

The distribution used to define shell thickness must have a default value. The default thickness is used by any shell element assigned to the shell section that is not specifically assigned a value in the distribution.

### **The following optional parameters can be used only in combination with the USER parameter: **

I PROPERTIES

Set this parameter equal to the number of integer property values needed as data in user subroutine [`UGENS`](../sub/sub-link.md#sub-xsl-ugens). The default is I PROPERTIES=0.

PROPERTIES

Set this parameter equal to the number of real (floating point) property values needed as data in user subroutine [`UGENS`](../sub/sub-link.md#sub-xsl-ugens). The default is PROPERTIES=0.

UNSYMM

Include this parameter if the section stiffness matrices are not symmetric. This parameter will invoke the unsymmetric equation solution capability.

VARIABLES

Set this parameter equal to the number of solution-dependent variables that must be stored for the section. The default is VARIABLES=1.

### **Optional parameter for use when the MATERIAL, the COMPOSITE, and the USER parameters are omitted: **

DEPENDENCIES

Set this parameter equal to the number of field variable dependencies included in the definition of the scaling moduli, in addition to temperature. If this parameter is omitted, it is assumed that the moduli are constant or depend only on temperature. 

### **Data line if the MATERIAL parameter is included: **

**First (and only) line:**

### **Data lines if the COMPOSITE parameter is included: **

**First line:**

Repeat this data line as often as necessary to define the layers of the shell. The order of the laminated shell layers with respect to the positive direction of the shell normal is defined by the order of the data lines. If the SYMMETRIC parameter is included, specify only half the layers, from the bottom layer to the midplane.

### **Data lines to define the shell section directly if the MATERIAL, the COMPOSITE, and the USER parameters are omitted: **

**First line:**

Repeat this data line three times. Enter 21 entries total, 8 per line on the first two lines and 5 on the third line.

**Second line (optional):**

**Third line (optional):**

**Subsequent lines (only needed if the DEPENDENCIES parameter has a value greater than five):**

Repeat this set of data lines as often as necessary to define *Y* and ![](../graphics/key_eqn00080.gif) as functions of temperature and other predefined field variables.

### **Data lines to define spatially varying shell section stiffness with a distribution if the MATERIAL, the COMPOSITE, and the USER parameters are omitted: **

**First line:**

**Second line (optional):**

**Third line (optional):**

**Subsequent lines (only needed if the DEPENDENCIES parameter has a value greater than five):**

Repeat this set of data lines as often as necessary to define *Y* and ![](../graphics/key_eqn00080.gif) as functions of temperature and other predefined field variables.

### **Data lines if the USER parameter is included: **

**First line:**

**Second line:**

Repeat this data line as often as necessary to define the properties required in [`UGENS`](../sub/sub-link.md#sub-xsl-ugens). Enter eight values per line for both real and integer values.




