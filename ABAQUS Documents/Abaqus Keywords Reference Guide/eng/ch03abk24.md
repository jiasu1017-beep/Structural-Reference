# *COHESIVE SECTION







### *COHESIVE SECTIONSpecify element properties for cohesive elements.

This option is used to define the properties of cohesive elements.

**Products: **Abaqus/Standard  Abaqus/Explicit  Abaqus/CAE  

**Type: **Model data  

**Level: **Part,  Part instance  

**Abaqus/CAE: **Property module

##### **References:**

- ["Cohesive elements: overview," Section 32.5.1 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-elm-ecohesiveoverview)
- ["Defining the constitutive response of cohesive elements using a continuum approach," Section 32.5.5 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-elm-ecohesivematbehavior)

### **Required parameters: **

ELSET

Set this parameter equal to the name of the element set containing the elements for which the cohesive properties are being defined.

MATERIAL

Set this parameter equal to the name of the material to be used with these elements.

RESPONSE

This parameter specifies the geometric assumption that defines the constitutive behavior of the cohesive elements.

Set RESPONSE=TRACTION SEPARATION if the response is defined directly in terms of traction and separation.

Set RESPONSE=CONTINUUM to specify that the cohesive elements model a strain state involving one direct (opening strain) and two transverse shear components.

Set RESPONSE=GASKET to specify that the stress state in the cohesive elements is uniaxial.

When RESPONSE=CONTINUUM or GASKET, the constitutive behavior of the element must be defined in terms of continuum material properties using any available material model in Abaqus (subject to the limitation that certain models are not available for a one-dimensional stress state).

### **Optional parameters: **

CONTROLS

Set this parameter equal to the name of a [*SECTION CONTROLS](ch18abk01.md) definition (see ["Section controls," Section 27.1.4 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-elm-esectioncontrol)). The [*SECTION CONTROLS](ch18abk01.md) option can be used to specify whether the cohesive elements should be deleted once they completely fail. This option may also be used to specify a maximum value of the scalar degradation (damage) parameter, *D*, and/or the viscosity coefficient, ![](../graphics/key_eqn00195.gif), for viscous regularization.

ORIENTATION

Set this parameter equal to the name given for the [*ORIENTATION](ch15abk01.md) option (["Orientations," Section 2.2.5 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-int-corientation)) to be used to define a local coordinate system for integration point calculations in the cohesive elements in the specified element set.

STACK DIRECTION

Set this parameter equal to 1, 2, 3, or ORIENTATION to define the cohesive element stack or thickness direction. Specify one of the numerical values to select the corresponding isoparametric direction of the element as the stack or thickness direction. The default is STACK DIRECTION=3 for three-dimensional cohesive elements and STACK DIRECTION=2 for two-dimensional and axisymmetric elements. 

If STACK DIRECTION=ORIENTATION, the ORIENTATION parameter is also required.

To obtain a desired thickness direction, the appropriate numerical value for the STACK DIRECTION parameter depends on the element connectivity. For a mesh-independent specification, use STACK DIRECTION=ORIENTATION.

This parameter cannot be used with pore pressure cohesive elements.

THICKNESS

Set THICKNESS=GEOMETRY if the initial constitutive thickness of the cohesive layer is determined from the nodal coordinates of the elements.

Set THICKNESS=SPECIFIED to specify the initial constitutive thickness of the layer on the data line below. If the data field representing the initial constitutive thickness is left blank or set equal to zero, a unit thickness is assumed.

The default value of this parameter depends on the choice of the RESPONSE parameter. If RESPONSE=TRACTION SEPARATION, the default is THICKNESS=SPECIFIED. If RESPONSE=CONTINUUM, the default is THICKNESS=GEOMETRY. If RESPONSE=GASKET, there is no default; the THICKNESS parameter must be stated explicitly.

### **Data line to define the attributes of cohesive elements: **

**First (and only) line:**




