# 15.2 Changes in Abaqus options







This section summarizes the changes and the additions that have been made to the options that define an Abaqus model.

| **mod** | **(E)** | [*ADAPTIVE MESH REFINEMENT](../key/key-link.md#usb-kws-hadaptivemeshrefinement) |
| --- | --- | --- |
|  |  | Use the new COARSENING parameter to specify if refinement can be removed once the refinement criteria are no longer met. |
| **mod** | **(S)(E)(C)** | [*AMPLITUDE](../key/key-link.md#usb-kws-mamplitude) |
|  |  | The DEFINITION parameter can now be used to define the amplitude via co-simulation with a logical modeling program. |
| **new** | **(S)** | [*BEAM SECTION OFFSET](../key/key-link.md#usb-kws-mbeamsectionoffset) |
|  |  | Define an offset for the beam cross-section origin. |
| **mod** | **(S)** | [*BOUNDARY](../key/key-link.md#usb-kws-hboundary) |
|  |  | The PHANTOM parameter can now be set equal to EDGE to apply boundary conditions to a phantom node located at an element edge in enriched elements. |
| **mod** | **(S)** | [*CFLOW](../key/key-link.md#usb-kws-hcflow) |
|  |  | The PHANTOM parameter is now available to apply concentrated flows to a phantom node located at an element edge or located coincident with a specified real node in enriched elements. |
| **new** | **(E)** | [*CHARACTERISTIC LENGTH](../key/key-link.md#usb-kws-mcharacteristiclength) |
|  |  | Define characteristic element length at a material point. |
| **mod** | **(S)** | [*CONTACT OUTPUT](../key/key-link.md#usb-kws-hcontactoutput) |
|  |  | The SURFACE parameter is now available in Abaqus/Standard for small-sliding contact between cracked surfaces in enriched elements. |
| **mod** | **(S)(E)** | [*CO-SIMULATION](../key/key-link.md#usb-kws-hcosimulation) |
|  |  | The PROGRAM parameter is no longer set to a value of LOGICAL for co-simulation with Dymola. The parameter setting PROGRAM=MULTIPHYSICS is now used for Dymola co-simulation. |
| **mod** | **(S)** | [*CREEP](../key/key-link.md#usb-kws-mcreep) |
|  |  | The LAW parameter can now be set to choose an Anand law, a Darveaux law, or a double power law. |
| **mod** | **(S)(E)** | [*DAMAGE INITIATION](../key/key-link.md#usb-kws-mdamageinitiation) |
|  |  | The R CRACK DIRECTION parameter is available for calculating the averaged stress/strain used to obtain the crack propagation direction. |
| **new** | **(E)** | [*DOMAIN DECOMPOSITION](../key/key-link.md#usb-kws-mdomaindecomp) |
|  |  | Define a region for domain decomposition and/or define constraints on the domain decomposition. |
| **mod** | **(S)(E)** | [*ELASTIC](../key/key-link.md#usb-kws-melastic) |
|  |  | The COMPRESSION FACTOR parameter is now available for defining different elastic moduli in tension and compression for uncoupled traction-separation elastic behavior. |
| **mod** | **(S)(E)** | [*FASTENER](../key/key-link.md#usb-kws-mfastener) |
|  |  | The ATTACHMENT METHOD can now take the value CONNECTORDIRECTION to establish fastening points on the respective surfaces based on the axial direction of the connector element associated with the fastener. |
| **mod** | **(E)** | [*FILTER](../key/key-link.md#usb-kws-mfilter) |
|  |  | The INVARIANT parameter can now take the values MAXP, INTERMP, and MINP to apply the filtering to the maximum principal stress, the intermediate principal stress, or the minimum principal stress, respectively. |
| **new** | **(S)** | [*FLEXIBLE BODY](../key/key-link.md#usb-kws-hflexiblebody) |
|  |  | Generate a flexible body from a substructure. |
| **mod** | **(S)** | [*FLUID CAVITY](../key/key-link.md#usb-kws-mfluidcavity) |
|  |  | The ADDED VOLUME parameter is now available in Abaqus/Standard. |
| **mod** | **(S)(E)** | [*INITIAL CONDITIONS](../key/key-link.md#usb-kws-minitialcond) |
|  |  | The TYPE parameter now supports a new value, DAMAGE INITIATION. A new parameter, CRITERION may be set to DUCTILE, SHEAR, or MSFLD to specify the damage initiation criterion for which the initial measure is being provided. |
| **new** | **(S)** | [*MATRIX CHECK](../key/key-link.md#usb-kws-hmatrixcheck) |
|  |  | Check the quality of the generated stiffness and mass matrices. |
| **mod** | **(S)** | [*MATRIX GENERATE](../key/key-link.md#usb-kws-hmatrixgenerate) |
|  |  | Use the new optional FIELD, MPC, and SOURCE parameters to indicate that matrices are generated for the structural or acoustic parts of the model, to apply the multipoint constraints during the matrix generation, and to generate matrices including contributions from the finite elements or from the matrix input, respectively. |
| **mod** | **(C)** | [*TURBULENCE MODEL](../key/key-link.md#usb-kws-hturbulence) |
|  |  | The TYPE parameter can now be set to specify the realizable ![](../graphics/rnb_eqn00007.gif)-![](../graphics/rnb_eqn00001.gif) turbulence model. |
| **mod** | **(S)** | [*USER MATERIAL](../key/key-link.md#usb-kws-musermaterial) |
|  |  | The new HYBRID FORMULATION parameter is now available in Abaqus/Standard. It can be set to TOTAL or to INCOMPRESSIBLE to define almost-incompressible or incompressible nonlinear elastic user material response. |
| **mod** | **(S)(E)** | [*VISCOELASTIC](../key/key-link.md#usb-kws-mviscoelast) |
|  |  | The LAW parameter can now be set to choose a power law model. |
| **mod** | **(S)** | [*VISCOUS](../key/key-link.md#usb-kws-mviscous) |
|  |  | The LAW parameter can be set to choose an Anand law, a Darveaux law, or a double power law. |




