# *INITIAL CONDITIONS







### *INITIAL CONDITIONSSpecify initial conditions for the model.

This option is used to prescribe initial conditions for an analysis.

**Products: **Abaqus/Standard  Abaqus/Explicit  Abaqus/CFD  Abaqus/CAE  Abaqus/Aqua  

**Type: **Model data  

**Level: **Model  

**Abaqus/CAE: **Load module

##### **References:**

- ["Initial conditions in Abaqus/Standard and Abaqus/Explicit," Section 34.2.1 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-prc-pinitialcond)
- ["Initial conditions in Abaqus/CFD," Section 34.2.2 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-prc-pinitialcondcfd)

### Defining initial conditions in Abaqus/Standard and Abaqus/Explicit

### **Required parameter: **

TYPE

Set TYPE=ACOUSTIC STATIC PRESSURE to define initial static pressure values at acoustic nodes for use in evaluating the cavitation status of the acoustic element nodes in Abaqus/Explicit.

Set TYPE=CONCENTRATION to give initial normalized concentrations for a mass diffusion analysis in Abaqus/Standard.

Set TYPE=CONTACT to specify initial bonded contact conditions on part of the slave surface identified by a node set in an Abaqus/Standard analysis.

Set TYPE=DAMAGE INITIATION to specify initial values of the damage initiation measure. The CRITERION parameter must also be used to specify the damage initiation criterion for which initial conditions are being specified. The REBAR and SECTION POINTS parameters can be used with this parameter when CRITERION=DUCTILE or CRITERION=SHEAR.

Set TYPE=ENRICHMENT to specify initial location of an enriched feature, such as a crack, in an Abaqus/Standard analysis. Two signed distance functions per node are generally required to describe the crack location, including the location of crack tips, in a cracked geometry. The first describes the crack surface while the second is used to construct an orthogonal surface so that the intersection of the two surfaces gives the crack front. The first signed distance function is assigned only to nodes of elements intersected by the crack while the second signed distance function is assigned only to nodes of elements containing the crack tips. No explicit representation of the crack is needed as the crack is entirely described by the nodal data. 

Set TYPE=FIELD to specify initial values of field variables. The VARIABLE parameter can be used with this parameter to define the field variable number. The STEP and INC parameters can be used in conjunction with the FILE parameter to define initial values of field variables from a results (`.fil`) or output database (`.odb`) file. The STEP and INC parameters can also be used in conjunction with the FILE and OUTPUT VARIABLE parameters to define initial values of field variables based on scalar nodal output variables read from an output database file. 

Set TYPE=FLUID PRESSURE to give initial pressures for hydrostatic fluid filled cavities.

Set TYPE=HARDENING to prescribe initial equivalent plastic strain and, if relevant, the initial backstress tensor or to prescribe initial volumetric compacting plastic strain for the crushable foam model. The REBAR and, in Abaqus/Standard, SECTION POINTS and USER parameters can be used with this parameter. If the USER parameter is used, the initial conditions on equivalent plastic strain and, if relevant, the backstress tensor must be specified via user subroutine [`HARDINI`](../sub/sub-link.md#sub-xsl-hardini) for each section point and for each rebar. Consequently, in this case the REBAR and SECTION POINTS parameters do not have any effect and are ignored. If the USER parameter is omitted, Abaqus/Standard assumes that the initial conditions are defined on the data lines.

Set TYPE=INITIAL GAP to identify the elements within which tangential fluid flow exists initially .

Set TYPE=MASS FLOW RATE to specify initial values of mass flow rates in Abaqus/Standard heat transfer analyses involving forced convection modeled with the forced convection/diffusion heat transfer elements.

Set TYPE=PLASTIC STRAIN to specify initial plastic strains. The SECTION POINTS and REBAR parameters can be used with this parameter. It is assumed that the plastic strain components are defined on each data line in the order given for the element type, as defined in [Part VI, "Elements," of the Abaqus Analysis User's Guide](../usb/usb-link.md#usbechapter).

Set TYPE=PORE PRESSURE to give initial pore fluid pressures for a coupled pore fluid diffusion/stress analysis in Abaqus/Standard. The STEP and INC parameters can also be used with the FILE parameter to define initial values of pore fluid pressures based on scalar nodal output variables read from an output database (`.odb`) file.

Set TYPE=POROSITY to give initial porosity values for materials defined with the [*EOS COMPACTION](ch05abk28.md) option in Abaqus/Explicit.

Set TYPE=PRESSURE STRESS to give initial pressure stresses for a mass diffusion analysis in Abaqus/Standard. The STEP and INC parameters can be used in conjunction with the FILE parameter to define initial values of pressure stress from the results (`.fil`) file of a previous Abaqus/Standard stress/displacement analysis.

Set TYPE=RATIO to give initial void ratio values for a coupled pore fluid diffusion/stress analysis in Abaqus/Standard. The STEP and INC parameters can be used in conjunction with the FILE parameter to define initial values of void ratio from the output database (`.odb`) file of a previous Abaqus/Standard soil analysis. The USER parameter can be used with this parameter to define initial void ratio values in user subroutine [`VOIDRI`](../sub/sub-link.md#sub-xsl-voidri).

Set TYPE=REF COORDINATE to define the reference mesh (initial metric) for membrane elements in Abaqus/Explicit using the element number and the coordinates of all of the nodes associated with the element. If a reference mesh is specified for an element, no initial stress or strain can be specified for the same element. The initial stress and strain are computed automatically to account for deformation from the reference to the initial configuration.

Set TYPE=NODE REF COORDINATE to define the reference mesh (initial metric) for membrane elements in Abaqus/Explicit using node numbers and the coordinates of each node. If a reference mesh is specified for an element, no initial stress or strain can be specified for the same element. The initial stress and strain are computed automatically to account for deformation from the reference to the initial configuration.

Set TYPE=RELATIVE DENSITY to give initial relative density values for materials defined with the [*POROUS METAL PLASTICITY](ch16abk22.md) option.

Set TYPE=ROTATING VELOCITY to prescribe initial velocities in terms of an angular velocity and a global translational velocity.

Set TYPE=SATURATION to give initial saturation values for the analysis of flow through a porous medium in Abaqus/Standard. If no initial saturation values are given on this option, the default is fully saturated conditions (saturation of 1.0). For partial saturation the initial saturation and the pore fluid pressure must be consistent in the sense that the pore fluid pressure must lie within the range of absorption and exsorption values for the initial saturation value. If this is not the case, Abaqus/Standard will adjust the saturation value as needed to satisfy this requirement.

Set TYPE=SOLUTION to give initial values of solution-dependent state variables. The REBAR and, in Abaqus/Standard, USER parameters can be used with this parameter. If TYPE=SOLUTION is used without the USER parameter, element average quantities of the solution-dependent state variables must be defined on each data line.

Set TYPE=SPECIFIC ENERGY to give initial specific energy values for materials defined with the [*EOS](ch05abk27.md) option in Abaqus/Explicit.

Set TYPE=SPUD EMBEDMENT to give the initial embedment for a spud can in an Abaqus/Aqua analysis.

Set TYPE=SPUD PRELOAD to give the initial preload value for a spud can in an Abaqus/Aqua analysis.

Set TYPE=STRESS to give initial stresses. (These stresses are effective stresses when the analysis includes pore fluid flow.) The GEOSTATIC; the REBAR; the SECTION POINTS; and, in Abaqus/Standard, the USER parameters can be used with this parameter. If TYPE=STRESS is used without the USER parameter, it is assumed that the stress components are defined on each data line in the order given for the element type, as defined in [Part VI, "Elements," of the Abaqus Analysis User's Guide](../usb/usb-link.md#usbechapter). The STEP and INC parameters can also be used with the FILE parameter to define initial stress values based on stress output variables read from an output database (`.odb`) file.

Set TYPE=TEMPERATURE to give initial temperatures. The STEP and INC parameters can be used in conjunction with the FILE parameter to define initial temperatures from the results (`.fil`) or output database (`.odb`) file of a previous Abaqus/Standard heat transfer analysis.

Set TYPE=VELOCITY to prescribe initial velocities. Initial velocities should be defined in the global directions, regardless of the use of the [*TRANSFORM](ch19abk11.md) option.

Set TYPE=VOLUME FRACTION to define the initial material content of Eulerian elements in an Abaqus/Explicit analysis.

### **Optional parameters: **

ABSOLUTE EXTERIOR TOLERANCE

This parameter is relevant only for use with the INTERPOLATE parameter. Set this parameter equal to the absolute value (given in the units used in the model) by which nodes of the current model may lie outside the region of the model in the output database specified by the FILE parameter. If this parameter is not used or has a value of 0.0, the EXTERIOR TOLERANCE parameter will apply.

CRITERION

Set CRITERION=DUCTILE to provide the damage initiation measure for the ductile damage initiation criterion.

Set CRITERION=MSFLD to provide the damage initiation measure for the Mschenborn and Sonne forming limit diagram based damage initiation criterion.

Set CRITERION=SHEAR to provide the damage initiation measure for the shear damage initiation criterion.

DEFINITION

Set DEFINITION=COORDINATES (default) to define the axis of rotation for TYPE=ROTATING VELOCITY by giving the coordinates of the two points, *a* and *b*.

Set DEFINITION=NODES  to define the axis of rotation for TYPE=ROTATING VELOCITY by giving global node numbers for points *a* and *b*.

DRIVING ELSETS

This parameter is relevant only for use with the INTERPOLATE parameter. Include this parameter to indicate that the field (temperature, void ratio, and pore pressure only) is interpolated from a user-specified element set from the previous analysis to a user-specified node set in the current job. This parameter is used to eliminate mapping ambiguity in cases where element regions in the previous analysis are close or touching. To accomplish part instance to part instance mapping, define your element and node sets to correspond to the respective instances in the previous and current analysis.

EXTERIOR TOLERANCE

This parameter is relevant only for use with the INTERPOLATE parameter. Set this parameter equal to the fraction of the average element size by which nodes of the current model may lie outside the region of the elements of the model in the output database specified by the FILE parameter. The default value is 0.05.

If both tolerance parameters are specified, Abaqus uses the tighter tolerance.

FILE

Set this parameter equal to the name of the results (`.fil`) file or output database (`.odb`) file from which initial field variable, stress, void ratio, pore pressure, or pressure stress data are to be read. This parameter must be used in conjunction with the STEP and INC parameters. For more information, see ["File extensions used by Abaqus," Section 3.6.1 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-int-dfileextensions).

FULL TENSOR

Include this parameter if the kinematic shift tensor (backstress) components are specified using the full tensor format, regardless of the element type to which the initial conditions are applied.

This parameter can be used only in conjunction with the parameter TYPE=HARDENING. It cannot be used if any of the parameters REBAR, SECTION POINTS, or USER has been used.

GEOSTATIC

This parameter is used only with TYPE=STRESS to specify that a geostatic stress state, in which stresses vary with elevation only, is being defined.

INC

This parameter is used only with the FILE parameter. If this parameter is omitted, the initial conditions will be read from the last increment of the step specified on the STEP parameter or from the last step if the STEP parameter is omitted.

 The parameter specifies the increment in the results (`.fil`) file of a previous Abaqus analysis from which prescribed fields of TYPE=FIELD, TYPE=PRESSURE STRESS, or TYPE=TEMPERATURE are to be read.  It can also specify the increment in the output database (`.odb`) file of a previous Abaqus analysis from which prescribed fields of TYPE=FIELD, TYPE=PORE PRESSURE, TYPE=STRESS, TYPE=RATIO, or TYPE=TEMPERATURE are to be read.

INPUT

Set this parameter equal to the name of the alternate input file containing the data lines for this option. See ["Input syntax rules," Section 1.2.1 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-int-iinputsyntax), for the syntax of such file names. If this parameter is omitted, it is assumed that the data follow the keyword line.

INTERPOLATE

Include this parameter in conjunction with the FILE, STEP, and INC parameters to indicate that the nodal temperatures being read into the temperature field or the scalar nodal output variable being read into a predefined field needs to be interpolated between dissimilar meshes. This feature is used to read nodal values from an output database (`.odb`) file generated during a previous Abaqus analysis.

For void ratio initialization from a previous output database file, this parameter is automatically activated and the old void ratios from either the element integration points or the element nodes are read and mapped onto the current nodes.

For temperature fields this parameter and the MIDSIDE parameter are mutually exclusive. For temperature fields if the initial analysis uses first-order elements and the current mesh is the same but uses second-order elements, use the MIDSIDE parameter instead. The MIDSIDE parameter is not supported for predefined fields; therefore, the INTERPOLATE parameter is the only option for initializing predefined fields using scalar nodal output values from a dissimilar mesh.

MIDSIDE

This parameter applies only to Abaqus/Standard analyses.

Include this parameter in conjunction with the FILE, STEP, and INC parameters to indicate that midside node temperatures in second-order elements are to be interpolated from corner node temperatures. This feature is used to read temperatures from a results (`.fil`) or output database (`.odb`) file generated during a heat transfer analysis using first-order elements. This parameter and the INTERPOLATE parameter are mutually exclusive. 

NORMAL

This parameter applies only to Abaqus/Standard analyses.

This parameter can be used only with TYPE=CONTACT to specify that the nodes in the node set (or the contact pair, if a node set is not defined) are bonded only in the normal (contact) direction and are allowed to move freely in the tangential direction. If the nodes in the node set (or the contact pair) are to be bonded in all directions, this parameter should be omitted.

NUMBER BACKSTRESSES

Set this parameter equal to the number of backstresses. This parameter can be used only in conjunction with TYPE=HARDENING. The default number of backstresses is 1, and the maximum allowed is 10.

OUTPUT VARIABLE

This parameter is required when TYPE=FIELD and the FILE parameter references an output database.

Set this parameter equal to the scalar nodal output variable that will be read from an output database and used to initialize a specified predefined field. For a list of scalar nodal output variables that can be used to initialize a predefined field, see ["Predefined fields," Section 34.6.1 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-prc-pfields).

REBAR

This parameter can be used with TYPE=DAMAGE INITIATION, TYPE=HARDENING, TYPE=PLASTIC STRAIN, TYPE=SOLUTION, or TYPE=STRESS.

When used with TYPE=DAMAGE INITIATION, it specifies the initial value of the damage initiation measure in the rebar.

When used with TYPE=HARDENING, it specifies that rebars are in a work hardened state, with initial equivalent plastic strain and, possibly, initial backstress.

When used with TYPE=PLASTIC STRAIN, it specifies the initial plastic strain in the rebar.

When used with TYPE=SOLUTION, it specifies that rebars are being assigned initial solution-dependent state variable values.

When used with TYPE=STRESS, it specifies that prestress in rebars is being defined. When performing an Abaqus/Standard analysis, some iteration will usually be needed in this case to establish a self-equilibrating stress state in the rebar and concrete. The [*PRESTRESS HOLD](ch16abk29.md) option can be useful for post-tensioning simulations (see ["Defining rebar as an element property," Section 2.2.4 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-int-erebar)).

SECTION POINTS

This parameter is used only with TYPE=DAMAGE INITIATION, TYPE=HARDENING, TYPE=PLASTIC STRAIN, and TYPE=STRESS to specify damage initiation measures, hardening variables, plastic strains, and stresses at individual section points through the thickness of a shell element. This parameter can be used only when shell properties are defined using the [*SHELL SECTION](ch18abk15.md) option. It cannot be used when properties are defined using the [*SHELL GENERAL SECTION](ch18abk14.md) option.

STEP

This parameter is used only with the FILE parameter. If this parameter is omitted, the initial conditions will be read from the last step.

The parameter specifies the step in the results (`.fil`) file of a previous Abaqus analysis from which prescribed fields of TYPE=FIELD, TYPE=PRESSURE STRESS, or TYPE=TEMPERATURE are to be read. It can also specify the step in the output database (`.odb`) file of a previous Abaqus analysis from which prescribed fields of TYPE=FIELD, TYPE=PORE PRESSURE, TYPE=STRESS, TYPE=RATIO, or TYPE=TEMPERATURE are to be read. 

UNBALANCED STRESS

This parameter applies only to Abaqus/Standard analyses.

This parameter is used only with TYPE=STRESS. 

Set UNBALANCED STRESS=RAMP (default) if the unbalanced stress is to be resolved linearly over the step.

Set UNBALANCED STRESS=STEP if the unbalanced stress is to be resolved in the first increment.

USER

This parameter applies only to Abaqus/Standard analyses.

This parameter can be used with TYPE=HARDENING, TYPE=PORE PRESSURE, TYPE=RATIO, TYPE=SOLUTION, or TYPE=STRESS.

When used with TYPE=HARDENING, it specifies that the initial conditions on equivalent plastic strain and, if relevant, backstress tensor are to be given via user subroutine [`HARDINI`](../sub/sub-link.md#sub-xsl-hardini).

When used with TYPE=PORE PRESSURE, it specifies that initial pore pressures are to be given via user subroutine [`UPOREP`](../sub/sub-link.md#sub-xsl-uporep).

When used with TYPE=RATIO, it specifies that initial void ratios are to be given via user subroutine [`VOIDRI`](../sub/sub-link.md#sub-xsl-voidri).

When used with TYPE=SOLUTION, it specifies that initial solution-dependent state variable fields are to be given via user subroutine [`SDVINI`](../sub/sub-link.md#sub-xsl-sdvini).

When used with TYPE=STRESS, it specifies that stresses are to be given via user subroutine [`SIGINI`](../sub/sub-link.md#sub-xsl-sigini).

VARIABLE

This parameter is used only with TYPE=FIELD when it is used to define the field variable number. The default is VARIABLE=1. Any number of separate field variables can be used: each must be numbered consecutively (1, 2, 3, etc.)

### **Data line for TYPE=ACOUSTIC STATIC PRESSURE: **

**First (and only) line:**

### **Data lines for TYPE=CONCENTRATION: **

**First line:**

Repeat this data line as often as necessary to define the initial normalized concentration at various nodes or node sets.

### **Data lines for TYPE=CONTACT: **

**First line:**

Repeat this data line as often as necessary to define partially bonded surfaces.

### **Data lines for TYPE=DAMAGE INITIATION, CRITERION=DUCTILE or CRITERION=SHEAR if the REBAR and SECTION POINTS parameters are omitted: **

**First line:**

Repeat this data line as often as necessary to define initial damage initiation measures in various elements or element sets.

### **Data lines for TYPE=DAMAGE INITIATION, CRITERION=DUCTILE or CRITERION=SHEAR with the REBAR parameter included: **

**First line:**

Repeat this data line as often as necessary to define initial damage initiation measures for rebars in various elements or element sets.

### **Data lines for TYPE=DAMAGE INITIATION, CRITERION=DUCTILE or CRITERION=SHEAR with the SECTION POINTS parameter included: **

**First line:**

Repeat this data line as often as necessary to define initial damage initiation measures in various elements or element sets. The initial damage initiation measures must be defined at all section points within an element.

### **Data lines for TYPE=DAMAGE INITIATION, CRITERION=MSFLD: **

**First line:**

Repeat this data line as often as necessary to define initial damage initiation measures in various elements or element sets.

### **Data lines for TYPE=ENRICHMENT: **

**First line:**

Repeat this data line as often as necessary to define initial signed distance functions in various elements or element sets. The signed distance functions must be defined at all nodes within an element.

### **Data lines for TYPE=FIELD, VARIABLE=*n*: **

**First line:**

**Subsequent lines (only needed if initial values must be specified at more than seven temperature points at any node):**

It may be necessary to leave blank data lines for some nodes if any other node in the model has more than seven field variable points because the total number of field variables that Abaqus expects to read for any node is based on the maximum number of field variable values for all the nodes in the model. These trailing initial values will be zero and will not be used in the analysis.

Repeat this set of data lines as often as necessary to define initial temperatures at various nodes or node sets.

### **No data lines are required for TYPE=FIELD, VARIABLE=*n*, FILE=*file*, STEP=*step*, INC=*inc*. **

### **Data lines for TYPE=FLUID PRESSURE: **

**First line:**

Repeat this data line as often as necessary to define initial fluid pressure for various fluid-filled cavities.

### **Data lines to prescribe initial equivalent plastic strain or backstresses using TYPE=HARDENING if the REBAR, SECTION POINTS, and USER parameters are omitted: **

**First line:**

**Subsequent lines (only needed if the NUMBER BACKSTRESSES parameter has a value greater than one):**

The backstress components are relevant only for the kinematic hardening models. Give the backstress components as defined for this element type in [Part VI, "Elements," of the Abaqus Analysis User's Guide](../usb/usb-link.md#usbechapter). Values given on the data lines are applied uniformly over the element. In any element for which an [*ORIENTATION](ch15abk01.md) option applies, backstresses must be given in the local system (["Orientations," Section 2.2.5 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-int-corientation)).

Repeat this set of data lines as often as necessary to define the hardening parameters for various elements or element sets.

### **Data lines to prescribe initial volumetric compacting plastic strain for the crushable foam model using TYPE=HARDENING: **

**First line:**

Repeat this data line as often as necessary to define the initial volumetric compacting plastic strain for various elements or element sets.

### **Data lines for TYPE=HARDENING, REBAR: **

**First line:**

**Subsequent lines (only needed if the NUMBER BACKSTRESSES parameter has a value greater than one):**

Repeat this set of data lines as often as necessary to define the hardening parameters for rebars in various elements or element sets.

### **No data lines are required for TYPE=HARDENING, USER. **

### **Data lines for TYPE=HARDENING, SECTION POINTS: **

**First line:**

**Subsequent lines (only needed if the NUMBER BACKSTRESSES parameter has a value greater than one):**

The backstress components are relevant only for the kinematic hardening model. Give the backstress components as defined for this element type in [Part VI, "Elements," of the Abaqus Analysis User's Guide](../usb/usb-link.md#usbechapter). In any element for which an [*ORIENTATION](ch15abk01.md) option applies, the backstress components must be given in the local system (["Orientations," Section 2.2.5 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-int-corientation)).

Repeat this set of data lines as often as necessary to define the hardening parameters in various elements or element sets. The hardening parameters must be defined at all section points within an element.

### **Data lines for TYPE=INITIAL GAP: **

**First line:**

Repeat this data line as often as necessary to identify various elements or element sets.

### **Data lines for TYPE=MASS FLOW RATE: **

**First line:**

Repeat this data line as often as necessary to define mass flow rates at various nodes or node sets.

### **Data lines for TYPE=NODE REF COORDINATE: **

**First line:**

Repeat this data line as often as necessary to define the initial coordinates of the mesh using nodal coordinates.

### **Data lines to prescribe initial plastic strains using TYPE=PLASTIC STRAIN if the REBAR and SECTION POINTS parameters are omitted: **

**First line:**

Give the plastic strain components as defined for this element type in [Part VI, "Elements," of the Abaqus Analysis User's Guide](../usb/usb-link.md#usbechapter). Values given on the data lines are applied uniformly over the element. In any element for which an [*ORIENTATION](ch15abk01.md) option applies, the plastic strains must be given in the local system (["Orientations," Section 2.2.5 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-int-corientation)).

Repeat this data line as often as necessary to define initial plastic strains in various elements or element sets.

### **Data lines for TYPE=PLASTIC STRAIN, REBAR: **

**First line:**

Repeat this data line as often as necessary to define the initial plastic strain in the rebars of various elements or element sets.

### **Data lines for TYPE=PLASTIC STRAIN, SECTION POINTS: **

**First line:**

Give the initial plastic strain components as defined for this element type in [Part VI, "Elements," of the Abaqus Analysis User's Guide](../usb/usb-link.md#usbechapter). In any element for which an [*ORIENTATION](ch15abk01.md) option applies, the plastic strain components must be given in the local system (["Orientations," Section 2.2.5 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-int-corientation)).

Repeat this data line as often as necessary to define initial plastic strains in various elements or element sets. Plastic strains must be defined at all section points within an element.

### **Data lines for TYPE=PORE PRESSURE if the USER parameter is omitted: **

**First line:**

Omit the elevation values and the second pore pressure value to define a constant pore pressure distribution.

Repeat this data line as often as necessary to define the fluid pore pressure at various nodes or node sets.

### **No data lines are required for TYPE=PORE PRESSURE, USER. **

### **No data lines are required for TYPE=PORE PRESSURE, FILE=*file*, STEP=*step*, INC=*inc*. **

### **No data lines are required for TYPE=PORE PRESSURE, FILE=*file*, STEP=*step*, INC=*inc*, INTERPOLATE. **

### **Data lines for TYPE=PORE PRESSURE, FILE=*file*, STEP=*step*, INC=*inc*, DRIVING ELSETS: **

**First line:**

 Repeat this data line as often as necessary. The node set identified on the data lines will be assigned values from the element set in the output database (`.odb`) file. If a duplicate node is defined on a subsequent data line, it will be removed from the subsequent void ratio mapping and printed out to the data (`.dat`) file.

### **Data lines for TYPE=POROSITY: **

**First line:**

Repeat this data line as often as necessary to define initial porosity in various elements or element sets.

### **Data lines for TYPE=PRESSURE STRESS: **

**First line:**

Repeat this data line as often as necessary to define the pressure stress at various nodes or node sets.

### **No data lines are required for TYPE=PRESSURE STRESS, FILE=*file*, STEP=*step*, INC=*inc*. **

### **Data lines for TYPE=RATIO if the USER parameter is omitted: **

**First line:**

Omit the elevation values and the second void ratio value to define a constant void ratio distribution.

Repeat this data line as often as necessary to define void ratios at various nodes or node sets.

### **No data lines are required for TYPE=RATIO, USER. **

### **No data lines are required for TYPE=RATIO, FILE=*file*, STEP=*step*, INC=*inc*. **

### **Data lines for TYPE=RATIO, FILE=*file*, STEP=*step*, INC=*inc*, DRIVING ELSETS: **

**First line:**

 Repeat this data line as often as necessary. The node set identified on the data lines will be assigned values from the element set in the output database (`.odb`) file. If a duplicate node is defined on a subsequent data line, it will be removed from the subsequent void ratio mapping and printed out to the data (`.dat`) file.

### **Data lines for TYPE=REF COORDINATE: **

**First line:**

**Second line:**

Repeat this pair of data lines as often as necessary to define the reference mesh in various elements. The order of the nodal coordinates must be consistent with the element connectivity.

### **Data lines for TYPE=RELATIVE DENSITY: **

**First line:**

Repeat this data line as often as necessary to define initial relative density at various nodes or node sets.

### **Data lines for TYPE=ROTATING VELOCITY, DEFINITION=COORDINATES: **

**First line:**

**Second line:**

Repeat this pair of data lines as often as necessary to define the angular and translational velocities at various nodes or node sets.

### **Data lines for TYPE=ROTATING VELOCITY, DEFINITION=NODES: **

**First line:**

**Second line:**

Repeat this pair of data lines as often as necessary to define the angular and translational velocities at various nodes or node sets.

### **Data lines for TYPE=SATURATION: **

**First line:**

Repeat this data line as often as necessary to define saturation at various nodes or node sets.

### **Data lines for TYPE=SOLUTION if the USER and REBAR parameters are omitted: **

**First line:**

**Subsequent lines (only needed if more than seven solution-dependent state variables exist in the model):**

It may be necessary to leave blank data lines for some elements if any other element in the model has more solution-dependent state variables because the total number of variables that Abaqus expects to read for any element is based on the maximum number of solution-dependent state variables for all the elements in the model. These trailing initial values will be zero and will not be used in the analysis. Values given on the data lines will be applied uniformly over the element.

Repeat this set of data lines as often as necessary to define initial values of solution-dependent state variables for various elements or element sets.

### **Data lines for TYPE=SOLUTION, REBAR: **

**First line:**

**Subsequent lines (only needed if more than six solution-dependent state variables exist in the model):**

It may be necessary to leave blank data lines for some elements if any other element in the model has more solution-dependent state variables because the total number of variables that Abaqus expects to read for any element is based on the maximum number of solution-dependent state variables for all the elements in the model. These trailing initial values will be zero and will not be used in the analysis. Values given on the data lines will be applied uniformly over the element.

Repeat this set of data lines as often as necessary to define initial values of solution-dependent state variables for various elements or element sets.

### **No data lines are required for TYPE=SOLUTION, USER. **

### **Data lines for TYPE=SPECIFIC ENERGY: **

**First line:**

Repeat this data line as often as necessary to define initial specific energy in various elements or element sets.

### **Data lines for TYPE=SPUD EMBEDMENT: **

**First line:**

Repeat this data line as often as necessary to define initial embedment for various elements or element sets.

### **Data lines for TYPE=SPUD PRELOAD: **

**First line:**

Repeat this data line as often as necessary to define initial preload for various elements or element sets.

### **Data lines for TYPE=STRESS if the GEOSTATIC, REBAR, SECTION POINTS, and USER parameters are omitted: **

**First line:**

Give the stress components as defined for this element type in [Part VI, "Elements," of the Abaqus Analysis User's Guide](../usb/usb-link.md#usbechapter). Stress values given on data lines are applied uniformly and equally over all integration points of the element. In any element for which an [*ORIENTATION](ch15abk01.md) option applies, the stresses must be given in the local system (["Orientations," Section 2.2.5 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-int-corientation)).

Repeat this data line as often as necessary to define initial stresses in various elements or element sets.

### **Data lines for TYPE=STRESS, GEOSTATIC: **

**First line:**

Repeat this data line as often as necessary to define an initial geostatic stress state in various elements or element sets.

### **Data lines for TYPE=STRESS, REBAR: **

**First line:**

Repeat this data line as often as necessary to define initial stress in the rebars of various elements or element sets.

### **Data lines for TYPE=STRESS, SECTION POINTS: **

**First line:**

Give the stress components as defined for this element type in [Part VI, "Elements," of the Abaqus Analysis User's Guide](../usb/usb-link.md#usbechapter). Stress values given on data lines are applied uniformly over the element. In any element for which an [*ORIENTATION](ch15abk01.md) option applies, the stresses must be given in the local system (["Orientations," Section 2.2.5 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-int-corientation)).

Repeat this data line as often as necessary to define initial stresses in various elements or element sets. Stresses must be defined at all section points within an element.

### **No data lines are required for TYPE=STRESS, USER. **

### **No data lines are required for TYPE=STRESS, FILE=*file*, STEP=*step*, INC=*inc*. **

### **Data lines for TYPE=TEMPERATURE: **

**First line:**

**Subsequent lines (only needed if there are more than seven temperature values at any node):**

If more than seven temperature values are needed at any node, continue on the next line. It may be necessary to leave blank data lines for some nodes if any other node in the model has more than seven temperature points because the total number of temperatures that Abaqus expects to read for any node is based on the maximum number of temperature values of all the nodes in the model. These trailing initial values will be zero and will not be used in the analysis.

Repeat this data line (or set of lines) as often as necessary to define initial temperatures at various nodes or node sets.

### **No data lines are required for TYPE=TEMPERATURE, FILE=*file*, STEP=*step*, INC=*inc*. **

### **Data lines for TYPE=TEMPERATURE, FILE=*file*, STEP=*step*, INC=*inc*, INTERPOLATE, DRIVING ELSETS: **

**First line:**

 Repeat this data line as often as necessary. The node set identified on the data lines will be assigned values from the element set in the output database (`.odb`) file. If a duplicate node is defined on a subsequent data line, it will be removed from the subsequent temperature mapping and printed out to the data (`.dat`) file.

### **Data lines for TYPE=VELOCITY: **

**First line:**

Repeat this data line as often as necessary to define the initial velocity at various nodes or node sets.

### **Data lines for TYPE=VOLUME FRACTION: **

**First line:**

Repeat this data line as often as necessary to define the initial geometry of all Eulerian material instances. An element may appear in more than one data line if it initially contains more than one material. Elements are filled incrementally by reading the data lines in the input file from bottom to top; once the volume fraction for an element reaches one, additional volume fractions assigned to that element are ignored. If the final volume fraction for an element is less than one, the remainder of that element is filled with void; similarly, uninitialized elements are filled with void.

### Defining initial conditions in Abaqus/CFD

### **Required parameters: **

ELEMENT AVERAGE

Include this parameter to define initial conditions for an Abaqus/CFD analysis.

TYPE

Set TYPE=DENSITY to define the initial density for a fluid analysis. For the incompressible flow procedure, if the initial density is not specified, the material density is used by default.

Set TYPE=VELOCITY to define the initial velocity field. For the incompressible flow procedure, the initial velocities can be modified to satisfy the divergence-free startup conditions.

Set TYPE=TEMPERATURE to define the initial temperature field. This setting is valid only when the energy equation has been activated for the incompressible flow procedure.

Set TYPE=TURBKE to define the initial turbulent kinetic energy field. This setting is valid only when the *k*-![](../graphics/key_eqn00849.gif) or *k*-![](../graphics/key_eqn00018.gif) model has been activated for the incompressible flow procedure.

Set TYPE=TURBEPS to define the initial turbulent energy dissipation rate. This setting is valid only when the ![](../graphics/key_eqn00372.gif)-![](../graphics/key_eqn00849.gif) model has been activated for the incompressible flow procedure.

Set TYPE=TURBOMEGA to define the initial specific energy dissipation rate. This setting is valid only when the *k*-![](../graphics/key_eqn00018.gif) model has been activated for the incompressible flow procedure.

Set TYPE=TURBNU to define the initial turbulent viscosity for the Spalart-Allmaras model. This setting is valid only when the Spalart-Allmaras model has been activated for the incompressible flow procedure.

Set TYPE=TURBINTENSITY to define the initial turbulence intensity. This setting is valid when the *k*-![](../graphics/key_eqn00849.gif), *k*-![](../graphics/key_eqn00018.gif), or the Spalart-Allmaras model has been activated for the incompressible flow procedure.

Set TYPE=TURBVELOCITYSCALE to define the initial velocity scale. This setting is valid when the *k*-![](../graphics/key_eqn00849.gif), *k*-![](../graphics/key_eqn00018.gif), or the Spalart-Allmaras model has been activated for the incompressible flow procedure.

Set TYPE=TURBVISCOSITYRATIO to define the initial eddy to molecular viscosity ratio. This setting is valid when the *k*-![](../graphics/key_eqn00849.gif), *k*-![](../graphics/key_eqn00018.gif), or the Spalart-Allmaras model has been activated for the incompressible flow procedure.

Set TYPE=TURBLENGTHSCALE to define the initial turbulent length scale. This setting is valid when the *k*-![](../graphics/key_eqn00849.gif), *k*-![](../graphics/key_eqn00018.gif), or the Spalart-Allmaras model has been activated for the incompressible flow procedure.

### **Data line for TYPE=DENSITY: **

**First (and only) line:**

### **Data lines for TYPE=VELOCITY: **

**First line:**

Repeat this data line as often as necessary to define the components of the initial velocity for various element sets.

### **Data line for TYPE=TEMPERATURE: **

**First (and only) line:**

### **Data line for TYPE=TURBKE: **

**First (and only) line:**

### **Data line for TYPE=TURBEPS: **

**First (and only) line:**

### **Data line for TYPE=TURBOMEGA: **

**First (and only) line:**

### **Data line for TYPE=TURBNU: **

**First (and only) line:**

### **Data line for TYPE=TURBINTENSITY: **

**First (and only) line:**

### **Data line for TYPE=TURBVELOCITYSCALE: **

**First (and only) line:**

### **Data line for TYPE=TURBVISCOSITYRATIO: **

**First (and only) line:**

### **Data line for TYPE=TURBLENGTHSCALE: **

**First (and only) line:**




