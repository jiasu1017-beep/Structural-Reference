# *BEAM SECTION







### *BEAM SECTIONSpecify a beam section when numerical integration over the section is required.

This option is used to define the cross-section for beam elements when numerical integration over the section is required (usually because of nonlinear material response in the section).

**Products: **Abaqus/Standard  Abaqus/Explicit  Abaqus/CAE  

**Type: **Model data  

**Level: **Part,  Part instance  

**Abaqus/CAE: **Property module

##### **References:**

- ["Using a beam section integrated during the analysis to define the section behavior," Section 29.3.6 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-elm-eusingbeamsection)
- ["Beam modeling: overview," Section 29.3.1 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-elm-ebeamoverview)
- ["Pipes and pipebends with deforming cross-sections: elbow elements," Section 29.5.1 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-elm-eelbows)

### **Required parameters: **

ELSET

Set this parameter equal to the name of the element set for which this section is defined.

MATERIAL

Set this parameter equal to the name of the material to be used with this beam section definition.

SECTION

Set this parameter equal to the name of the section type (see ["Beam cross-section library," Section 29.3.9 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-elm-ebeamcrosssectlib)). The following cross-sections are available for beam elements:
- ARBITRARY, for an arbitrary section.
- BOX, for a rectangular, hollow box section.
- CIRC, for a solid circular section.
- HEX, for a hollow hexagonal section.
- I, for an I-beam section.
- L, for an L-beam section.
- PIPE, for a thin-walled circular section.
- RECT, for a solid, rectangular section.
- THICK PIPE, for a thick-walled circular section (Abaqus/Standard only).
- TRAPEZOID, for a trapezoidal section.

Set SECTION=ELBOW for elbow elements, which are available only in Abaqus/Standard.

### **Optional parameters: **

LUMPED

This parameter is relevant only for linear Timoshenko beam elements in Abaqus/Standard.

Set LUMPED=YES (default) to use a lumped mass matrix in frequency extraction and modal analysis procedures.

Set LUMPED=NO to use a mass matrix based on a cubic interpolation of deflection and quadratic interpolation of the rotation fields in frequency extraction and modal analysis procedures.

POISSON

Set this parameter equal to the effective Poisson's ratio for the section to provide uniform strain in the section because of strain of the beam axis (so that the beam changes cross-sectional area when it is stretched). The value of the effective Poisson's ratio must be between 1.0 and 0.5. The default is POISSON=0. A value of 0.5 will enforce incompressible behavior of the element.

This parameter is used only in large-displacement analyses. It is not used with elbow elements or with element types B23, B33, PIPE21, PIPE22, and the equivalent “hybrid” elements (which are available only in Abaqus/Standard).

ROTARY INERTIA

This parameter is relevant only for three-dimensional Timoshenko beam elements.

Set ROTARY INERTIA=EXACT (default) to use the exact rotary inertia corresponding to the beam cross-section geometry in dynamic and eigenfrequency extraction procedures.

Set ROTARY INERTIA=ISOTROPIC to use an approximate rotary inertia for the cross-section. In Abaqus/Standard the rotary inertia associated with the torsional mode of deformation is used for all rotational degrees of freedom. In Abaqus/Explicit the rotary inertia for all rotational degrees of freedom is equal to a scaled flexural inertia with a scaling factor chosen to maximize the stable time increment.

TEMPERATURE

Use this parameter to select the mode of temperature and field variable input used on the [*FIELD](ch06abk07.md), the [*INITIAL CONDITIONS](ch09abk18.md), or the [*TEMPERATURE](ch19abk01.md) options.

 For beam elements set TEMPERATURE=GRADIENTS (default) to specify temperatures and field variables as values at the origin of the cross-section, together with gradients with respect to the 2-direction and, for beams in space, the 1-direction of the section. Set TEMPERATURE=VALUES to give temperatures and field variables as values at the points shown in the beam section descriptions (see ["Beam cross-section library," Section 29.3.9 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-elm-ebeamcrosssectlib)).

 For elbow elements set TEMPERATURE=GRADIENTS (default) to specify temperatures and field variables at the middle of the pipe wall and the gradient through the pipe thickness. Set TEMPERATURE=VALUES to give temperatures and field variables as values at points through the section, as shown in ["Pipes and pipebends with deforming cross-sections: elbow elements," Section 29.5.1 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-elm-eelbows). 

### **Data lines for BOX, CIRC, HEX, I, L, PIPE, RECT, THICK PIPE, and TRAPEZOID sections: **

**First line:**

**Second line (optional; enter a blank line if the default values are to be used):**

The entries on this line must be (0, 0, 1) for planar beams. The default for beams in space is (0, 0, 1) if the first beam section axis is not defined by an additional node in the element's connectivity. See ["Beam element cross-section orientation," Section 29.3.4 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-elm-ebeamcrosssection), for details.

**Third line (optional):**

### **Data lines for ARBITRARY sections: **

**First line:**

**Second line:**

Repeat the second data line as often as necessary to define the ARBITRARY section.

**Third line (optional):**

The entries on this line must be (0, 0, 1) for planar beams. The default for beams in space is (0, 0, 1) if the first beam section axis is not defined by an additional node in the element's connectivity. See ["Beam element cross-section orientation," Section 29.3.4 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-elm-ebeamcrosssection), for details.

### **Data lines for ELBOW sections: **

**First line:**

**Second line:**

Enter the coordinates of the point of intersection of the tangents to the straight pipe segments adjoining the elbow, or, if this section is associated with straight pipes, the coordinates of a point off the pipe axis. The second cross-sectional axis will lie in the plane thus defined, with its positive direction pointing toward this off-axis point.

**Third line:**




