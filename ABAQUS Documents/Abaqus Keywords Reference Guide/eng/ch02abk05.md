# *BEAM GENERAL SECTION







### *BEAM GENERAL SECTIONSpecify a beam section when numerical integration over the section is not required.

This option is used to define linear or nonlinear beam section response when numerical integration over the section is not required. In this case the beam section geometry and material descriptions are combined; no [*MATERIAL](ch13abk08.md) reference is associated with this option.

**Products: **Abaqus/Standard  Abaqus/Explicit  Abaqus/CAE  

**Type: **Model data  

**Level: **Part,  Part instance  

**Abaqus/CAE: **General beam sections with linear response are supported in the Property module.

##### **References:**

- ["Using a general beam section to define the section behavior," Section 29.3.7 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-elm-eusingbeamgensect)
- ["Beam modeling: overview," Section 29.3.1 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-elm-ebeamoverview)

### **Required parameter: **

ELSET

Set this parameter equal to the name of the element set for which the section is defined.

### **Required parameter in Abaqus/Explicit, optional parameter in Abaqus/Standard: **

DENSITY

Set this parameter equal to the mass density (mass per unit volume) of the beam material. In an Abaqus/Standard analysis this parameter is needed only when the mass of the elements is required, such as in dynamic analysis or gravity loading. This parameter cannot be used when SECTION=MESHED.

### **Optional parameters: **

DEPENDENCIES

This parameter cannot be used when SECTION=NONLINEAR GENERAL or SECTION=MESHED.

Set this parameter equal to the number of field variable dependencies included in the definition of material moduli, in addition to temperature. If this parameter is omitted, it is assumed that the moduli are constant or depend only on temperature. 

LUMPED

This parameter is relevant only for linear Timoshenko beam elements in Abaqus/Standard.

Set LUMPED=YES (default) to use a lumped mass matrix in frequency extraction and modal analysis procedures.

Set LUMPED=NO to use a mass matrix based on a cubic interpolation of deflection and quadratic interpolation of the rotation fields in frequency extraction and modal analysis procedures.

POISSON

Set this parameter equal to the effective Poisson's ratio for the section to provide uniform strain in the section due to strain of the beam axis (so that the cross-sectional area changes when the beam is stretched). The value of the effective Poisson's ratio must be between 1.0 and 0.5. The default is POISSON=0. A value of 0.5 will enforce incompressible behavior of the element.

For PIPE elements with SECTION=PIPE, this parameter will also be used along with the Young's modulus given on the third data line to compute the axial strain due to hoop strain.

This parameter is used only in large-displacement analysis. It is not used with element types B23, B33, or the equivalent “hybrid” elements (which are available only in Abaqus/Standard).

ROTARY INERTIA

This parameter is relevant only for three-dimensional Timoshenko beam elements.

Set ROTARY INERTIA=EXACT (default) to use the exact rotary inertia corresponding to the beam cross-section geometry in dynamic and eigenfrequency extraction procedures.

Set ROTARY INERTIA=ISOTROPIC to use an approximate rotary inertia for the cross-section. In Abaqus/Standard the rotary inertia associated with the torsional mode of deformation is used for all rotational degrees of freedom. In Abaqus/Explicit the rotary inertia for all rotational degrees of freedom is equal to a scaled flexural inertia with a scaling factor chosen to maximize the stable time increment. ROTARY INERTIA=ISOTROPIC is not relevant and cannot be used when SECTION=MESHED; the default value of EXACT always applies for meshed sections.

SECTION

Set SECTION=GENERAL (default) to define a general beam section with linear response.

Set SECTION=NONLINEAR GENERAL to define general nonlinear behavior of the cross-section.

Set SECTION=MESHED to define an arbitrarily shaped solid cross-section meshed with warping elements.

Set this parameter equal to the name of a library section to choose a standard library section (see ["Beam cross-section library," Section 29.3.9 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-elm-ebeamcrosssectlib)). The following cross-sections are available:
- ARBITRARY, for an arbitrary section.
- BOX, for a rectangular, hollow box section.
- CIRC, for a solid circular section.
- HEX, for a hollow hexagonal section.
- I, for an I-beam section.
- L, for an L-beam section.
- PIPE, for a hollow, circular section.
- RECT, for a solid, rectangular section.
- TRAPEZOID, for a trapezoidal section.

TAPER

This parameter is relevant only for Abaqus/Standard analyses.

Include this parameter to define a general beam section with a tapered cross-section.

ZERO

This parameter cannot be used when SECTION=MESHED.

Set this parameter equal to the reference temperature for thermal expansion (![](../graphics/key_eqn00086.gif)), if required. The default is ZERO=0.

### **Data lines for SECTION=GENERAL: **

**First line:**

**Second line (optional; enter a blank line if the default values are to be used):**

The entries on this line must be (0, 0, ![](../graphics/key_eqn00089.gif)) for planar beams. The default for beams in space is (0, 0, ![](../graphics/key_eqn00089.gif)) if the first beam section axis is not defined by an additional node in the element's connectivity. See ["Beam element cross-section orientation," Section 29.3.4 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-elm-ebeamcrosssection), for details.

**Third line:**

**Subsequent lines (only needed if the DEPENDENCIES parameter has a value greater than four):**

Repeat this set of data lines as often as necessary to define the properties as a function of temperature and other predefined field variables.

### **Data lines for SECTION=GENERAL if the TAPER parameter is included: **

**First line (properties of node A):**

**Second line (properties of node B):**

**Third line (optional; enter a blank line if the default values are to be used):**

The entries on this line must be (0, 0, ![](../graphics/key_eqn00089.gif)) for planar beams. The default for beams in space is (0, 0, ![](../graphics/key_eqn00089.gif)) if the first beam section axis is not defined by an additional node in the element's connectivity. See ["Beam element cross-section orientation," Section 29.3.4 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-elm-ebeamcrosssection), for details.

**Fourth line:**

**Subsequent lines (only needed if the DEPENDENCIES parameter has a value greater than four):**

Repeat this set of data lines as often as necessary to define the properties as a function of temperature and other predefined field variables.

### **Data lines for SECTION=NONLINEAR GENERAL: **

**First line:**

The axial and bending behaviors of the section are defined by using the [*AXIAL](ch01abk16.md), [*M1](ch13abk32.md), [*M2](ch13abk33.md), [*TORQUE](ch19abk08.md), and [*THERMAL EXPANSION](ch19abk05.md) options.

**Second line (optional):**

The entries on this line must be (0, 0, ![](../graphics/key_eqn00089.gif)) for planar beams. The default for beams in space is (0, 0, ![](../graphics/key_eqn00089.gif)) if the first beam section axis is not defined by an additional node in the element's connectivity. See ["Beam element cross-section orientation," Section 29.3.4 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-elm-ebeamcrosssection), for details.

### **Data lines for SECTION=MESHED: **

**First line:**

The entries on this line must be (0, 0, 1) for planar beams. The default for beams in space is (0, 0, 1) if the first beam section axis is not defined by an additional node in the element's connectivity. See ["Beam element cross-section orientation," Section 29.3.4 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-elm-ebeamcrosssection), for details.

**Second line:**

The entries on this line and the following line consist of the beam section properties that result from the two-dimensional meshed cross-section generation procedure. The properties are written to the file `*jobname*.bsp` during the cross-section generation and are typically read into a subsequent beam analysis using the [*INCLUDE](ch09abk14.md) option. See ["Meshed beam cross-sections," Section 10.6.1 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-anl-ameshedsection), for details.

**Third line:**

### **Data lines for BOX, CIRC, HEX, I, L, PIPE, RECT, and TRAPEZOID sections: **

**First line:**

**Second line (optional; enter a blank line if the default values are to be used):**

The entries on this line must be (0, 0, ![](../graphics/key_eqn00089.gif)) for planar beams. The default for beams in space is (0, 0, ![](../graphics/key_eqn00089.gif)) if the first beam section axis is not defined by an additional node in the element's connectivity. See ["Beam element cross-section orientation," Section 29.3.4 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-elm-ebeamcrosssection), for details.

**Third line:**

**Subsequent lines (only needed if the DEPENDENCIES parameter has a value greater than four):**

Repeat this set of data lines as often as necessary to define the properties as a function of temperature and other predefined field variables.

### **Data lines for BOX, CIRC, HEX, I, L, PIPE, RECT, and TRAPEZOID sections if the TAPER parameter is included: **

**First line (properties of node A):**

**Second line (properties of node B):**

**Third line (optional; enter a blank line if the default values are to be used):**

The entries on this line must be (0, 0, ![](../graphics/key_eqn00089.gif)) for planar beams. The default for beams in space is (0, 0, ![](../graphics/key_eqn00089.gif)) if the first beam section axis is not defined by an additional node in the element's connectivity. See ["Beam element cross-section orientation," Section 29.3.4 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-elm-ebeamcrosssection), for details.

**Fourth line:**

**Subsequent lines (only needed if the DEPENDENCIES parameter has a value greater than four):**

Repeat this set of data lines as often as necessary to define the properties as a function of temperature and other predefined field variables.

### **Data lines for SECTION=ARBITRARY: **

**First line:**

**Second line:**

Repeat the second data line as often as necessary to define the ARBITRARY section.

**Third line (optional; enter a blank line if the default values are to be used):**

The entries on this line must be (0, 0, ![](../graphics/key_eqn00089.gif)) for planar beams. The default for beams in space is (0, 0, ![](../graphics/key_eqn00089.gif)) if the first beam section axis is not defined by an additional node in the element's connectivity. See ["Beam element cross-section orientation," Section 29.3.4 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-elm-ebeamcrosssection), for details.

**Fourth line:**

**Subsequent lines (only needed if the DEPENDENCIES parameter has a value greater than four):**

Repeat this set of data lines as often as necessary to define the properties as a function of temperature and other predefined field variables.




