# *SHELL SECTION







### *SHELL SECTIONSpecify a shell cross-section.

This option is used to specify a shell cross-section.

**Products: **Abaqus/Standard  Abaqus/Explicit  Abaqus/CAE  

**Type: **Model data  

**Level: **Part,  Part instance  

**Abaqus/CAE: **Property module

##### **References:**

- ["Shell elements: overview," Section 29.6.1 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-elm-eshelloverview)
- ["Using a shell section integrated during the analysis to define the section behavior," Section 29.6.5 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-elm-eusingshellsection)

### **Required parameter: **

ELSET

Set this parameter equal to the name of the element set containing the shell elements for which the section behavior is being defined.

### **Required, mutually exclusive parameters: **

COMPOSITE

Include this parameter if the shell is made up of several layers of material.

MATERIAL

Set this parameter equal to the name of the material of which the shell is made.

### **Optional parameters: **

CONTROLS

In an Abaqus/Explicit analysis, set this parameter equal to the name of a section controls definition (see ["Section controls," Section 27.1.4 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-elm-esectioncontrol)) to be used to specify the second-order accurate element formulation option, a nondefault hourglass control formulation option, or scale factors.

In an Abaqus/Standard analysis, set this parameter equal to the name of a section controls definition to be used to specify the enhanced hourglass control formulation (see ["Section controls," Section 27.1.4 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-elm-esectioncontrol)) or to be used in a subsequent Abaqus/Explicit import analysis.

DENSITY

Set this parameter equal to a mass per unit surface area of the shell.

If this parameter is used, the mass of the shell includes a contribution from this parameter in addition to any contribution from the material definition.

LAYUP

This parameter is relevant only when the COMPOSITE parameter is used.

Set this parameter equal to the name of a composite layup (see [Chapter 23, "Composite layups," of the Abaqus/CAE User's Guide](../usi/usi-link.md#usi-adv-layups)). Abaqus/CAE uses this name to identify the composite layup that contains the shell section. 

NODAL THICKNESS

Include this parameter to indicate that the shell thickness should not be read from the data lines but should be interpolated from the thickness specified at the nodes with the [*NODAL THICKNESS](ch14abk08.md) option. For composite sections the total thickness is interpolated from the nodes and the thicknesses of the layers specified on the data lines are scaled proportionally.  This parameter is ignored for continuum shells.

The NODAL THICKNESS and SHELL THICKNESS parameters are mutually exclusive.

OFFSET

Include this parameter to define the distance (as a fraction of the shell thickness) from the shell midsurface to the reference surface (containing the nodes of the element). This parameter accepts positive or negative values, the labels SPOS or SNEG, or in  an Abaqus/Standard analysis the name of a distribution. See ["Distribution definition," Section 2.8.1 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-int-adefiningdistributions).

Positive values of the offset are in the positive normal direction (see ["Shell elements: overview," Section 29.6.1 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-elm-eshelloverview)). When OFFSET=0.5 (or SPOS), the top surface of the shell is the reference surface. When OFFSET=0.5 (or SNEG), the bottom surface of the shell is the reference surface.  The default is OFFSET=0, which indicates that the middle surface of the shell is the reference surface.  This parameter is ignored for continuum shells.

In an Abaqus/Standard analysis a spatially varying offset can be specified by setting OFFSET equal to the name of a distribution. The distribution used to define the shell offset must have a default value. The default offset is used by any shell element assigned to the shell section that is not specifically assigned a value in the distribution.

ORIENTATION

Set this parameter equal to the name of an orientation definition (["Orientations," Section 2.2.5 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-int-corientation)) to be used with material calculations in this definition of shell section behavior. This orientation will be used for material calculations and stress output in the individual layers, for the section forces output, and for the transverse shear stiffness. 

It is possible to use a different orientation definition for material calculations in the individual layers of a composite shell by referencing an orientation definition or giving an orientation angle (in degrees, positive counterclockwise relative to the shell local directions) on each layer definition data line. Any layer definition line that does not have an orientation reference or an angle specified will use the orientation defined here. While an orientation defined with a distribution can be used to specify the overall orientation for the shell section, an orientation defined with a distribution cannot be specified on the layers of a composite shell. 

POISSON

Include this parameter to define the shell thickness direction behavior. 

Set this parameter equal to a nonzero value to cause the thickness direction strain under plane stress conditions to be a linear function of the membrane strains. The value of the POISSON parameter must be between 1.0 and 0.5. 

Set POISSON=ELASTIC to automatically select this parameter value based on the initial elastic part of the material definition.

Set POISSON=MATERIAL in an Abaqus/Explicit analysis to cause the thickness direction strain under plane stress conditions to be a function of the membrane strains and the in-plane material properties.

In Abaqus/Standard the default is POISSON=0.5; in Abaqus/Explicit the default is POISSON=MATERIAL.

SECTION INTEGRATION

Set SECTION INTEGRATION=SIMPSON (default) to use Simpson's rule for the shell section integration.

Set SECTION INTEGRATION=GAUSS to use Gauss quadrature for the shell section integration. Gauss quadrature cannot be used for heat transfer or thermally coupled shell elements.

SHELL THICKNESS

Set this parameter equal to the name of a distribution (["Distribution definition," Section 2.8.1 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-int-adefiningdistributions)) to define spatially varying thickness. If this parameter is used for a non-composite section the thickness on the data line is ignored. For composite sections the total thickness is defined by the distribution and the thicknesses of the layers specified on the data lines are scaled proportionally. This parameter is ignored for continuum shells. 

The distribution used to define shell thickness must have a default value. The default thickness is used by any shell element assigned to the shell section that is not specifically assigned a value in the distribution.

The NODAL THICKNESS and SHELL THICKNESS parameters are mutually exclusive.

STACK DIRECTION

This parameter is relevant only for continuum shells.

Set this parameter equal to 1, 2, 3, or ORIENTATION to define the continuum shell stack or thickness direction. Specify one of the numerical values to select the corresponding isoparametric direction of the element as the stack or thickness direction. The default is STACK DIRECTION=3.

If STACK DIRECTION=ORIENTATION, the ORIENTATION parameter is also required.

To obtain a desired thickness direction, the appropriate numerical value for the STACK DIRECTION parameter depends on the element connectivity. For a mesh-independent specification, use STACK DIRECTION=ORIENTATION. If the orientation assigned to the ORIENTATION parameter is defined with a distribution (["Distribution definition," Section 2.8.1 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-int-adefiningdistributions)), STACK DIRECTION=ORIENTATION is not supported.

SYMMETRIC

This parameter is relevant only when the COMPOSITE parameter is used.

Include this parameter if the layers in the composite shell are symmetric about a central core.  This parameter cannot be used if a spatially varying thickness or orientation angle is defined on any composite layer using a distribution (["Distribution definition," Section 2.8.1 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-int-adefiningdistributions)).

TEMPERATURE

Use this parameter to select the mode of temperature and field variable input used on the [*FIELD](ch06abk07.md), the [*INITIAL CONDITIONS](ch09abk18.md), or the [*TEMPERATURE](ch19abk01.md) options.

Omit the TEMPERATURE parameter to define the predefined field by its magnitude on the reference surface of the shell and its gradient through the thickness.

Set TEMPERATURE=*n*, where *n* is the number of predefined field variable points in the shell or in each layer if the COMPOSITE parameter is used, to define the predefined field at *n* equally spaced points through each layer of the shell section.

 In a heat transfer analysis step or a coupled temperature-displacement analysis step when the [*FIELD](ch06abk07.md) option is used to specify values of predefined field variables, the TEMPERATURE parameter is required to specify the number of field variable points in the shell. The number of temperature points in the shell with temperature degrees of freedom is defined by the number of integration points specified on the data lines.

THICKNESS MODULUS

This parameter is relevant only for continuum shells. 

Set this parameter equal to an effective thickness modulus. The default effective thickness modulus is twice the initial in-plane shear modulus based on the material definition.

### **Data line to define a homogeneous shell (the MATERIAL parameter is included): **

**First (and only) line:**

### **Data lines to define a composite shell (the COMPOSITE parameter is included): **

**First line:**

Repeat this data line as often as necessary. Use one data line for each layer of the shell. The order of the laminated shell layers with respect to the positive direction of the shell normal is defined by the order of the data lines. If the SYMMETRIC parameter is included, specify only half the layers, from the bottom layer to the midplane.




