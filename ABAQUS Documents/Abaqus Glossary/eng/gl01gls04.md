# C







### CAD Connection toolset

An Abaqus/CAE toolset that allows you to create a connection from Abaqus/CAE to a third-party CAD system; you can use the CAD system to modify the model or to change its position, and you can use the established connection to update the model quickly in Abaqus/CAE. 
For more information:- [Chapter 60, "The CAD Connection toolset," of the Abaqus/CAE User's Guide](../usi/usi-link.md#usi-cad)

### canvas

The region of the Abaqus/CAE main window where work takes place. 
For more information:- [Chapter 4, "Managing viewports on the canvas," of the Abaqus/CAE User's Guide](../usi/usi-link.md#uss-cnv)

### CATIA

A CAD/CAM/CAE software package from Dassault Systmes. CATIA-format parts and assemblies can be imported into Abaqus/CAE.
For more information:- ["What kinds of files can be imported and exported from Abaqus/CAE?," Section 10.1.1 of the Abaqus/CAE User's Guide](../usi/usi-link.md#usi-imp-concepts-whatkind)

### chamfer

A straight blend that creates a beveled edge connecting two surfaces.
For more information:- ["Blend features," Section 11.9.5 of the Abaqus/CAE User's Guide](../usi/usi-link.md#usi-prt-conc-round)

### check box

An element of Abaqus/CAE dialog boxes that can be used to turn a particular option alternately off or on.
For more information:- ["Using basic dialog box components," Section 3.2.1 of the Abaqus/CAE User's Guide](../usi/usi-link.md#uss-int-dialog-basic)

### child feature

A feature in Abaqus/CAE that, when created, depends on an existing feature called the parent feature for geometric and dimensioning information. When you modify a parent feature, the modification may change its child features. Likewise, when you delete a parent feature, Abaqus/CAE automatically deletes all of its child features.
For more information:- ["The relationship between parts and features," Section 11.3.1 of the Abaqus/CAE User's Guide](../usi/usi-link.md#usi-prt-conc-parts-features)

### coarsening rate limit

A limit that you specified in a remeshing rule that modulates the rate at which larger elements are introduced into the mesh when Abaqus/CAE is adaptively remeshing.
For more information:- ["Refinement and coarsening rate factors" in "Solution-based mesh sizing," Section 12.3.3 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-anl-aadpsizing-ratefactors)

- ["Choosing remeshing rule constraints," Section 17.21.4 of the Abaqus/CAE User's Guide](../usi/usi-link.md#usi-mgn-adaptivity-ruleconstraints)

### co-execution

The co-simulation execution of two Abaqus analysis jobs that are executed in Abaqus/CAE in synchronization with one another.
For more information:- ["Structural-to-structural co-simulation," Section 17.3.1 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-anl-acosimabqtoabq)

- ["Fluid-to-structural and conjugate heat transfer co-simulation," Section 17.3.2 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-anl-acosimcfdtoabq)

- ["Understanding analysis jobs," Section 19.2 of the Abaqus/CAE User's Guide](../usi/usi-link.md#usi-ana-concepts)

- [Chapter 26, "Co-simulation," of the Abaqus/CAE User's Guide](../usi/usi-link.md#usi-adv-cosimulations)

### compass

See [3D compass](gl01gls01.md#gls-3dcompass).

### compatible mesh

An interface between two meshes where the mesh topology is consistent across the interface.
For more information:- ["Compatible meshes between part instances," Section 17.14.3 of the Abaqus/CAE User's Guide](../usi/usi-link.md#usi-mgn-advanced-compatibility)

### connector

In an Abaqus analysis, an element that models the behavior of mechanical joints or fasteners between components of a model and may include (nonlinear) force versus displacement (or velocity) behavior, friction, damage, and other phenomena.
For more information:- [Chapter 31, "Connector Elements," of the Abaqus Analysis User's Guide](../usb/usb-link.md#usbconnector)

In an Abaqus/CAE model, a connection that allows you to model mechanical relationships between two points in an assembly. 
For more information:- ["What is a connector?," Section 24.2 of the Abaqus/CAE User's Guide](../usi/usi-link.md#usi-adv-conn-whatis)

### constraint

In a modeling interaction, a relationship between particular degrees of freedom that is enforced during the simulation; for example, linear constraints, general constraints, and kinematic coupling.
For more information:- [Chapter 35, "Constraints," of the Abaqus Analysis User's Guide](../usb/usb-link.md#usbconstraints)

In a prescribed condition, a prespecified value of a degree of freedom. See also [boundary condition](gl01gls03.md#gls-boundarycondition).
For more information:- ["Managing prescribed conditions," Section 16.3 of the Abaqus/CAE User's Guide](../usi/usi-link.md#usi-lbi-edit-manager)

In an Abaqus/CAE assembly, a feature that specifies the geometric relationships between parts to establish their relative position.
For more information:- ["How the position constraint methods differ," Section 13.5.2 of the Abaqus/CAE User's Guide](../usi/usi-link.md#usi-asm-concept-alignmate)

In an Abaqus/CAE sketch, a feature used to specify geometric relationships between entities in a sketch.
For more information:- ["Customizing the use of constraints in the Sketcher," Section 20.9.10 of the Abaqus/CAE User's Guide](../usi/usi-link.md#usi-ske-constraintsframe)

### constraint control point

The point in a coupling constraint definition to which the motion of the coupled surface is constrained.
For more information:- ["Coupling constraints," Section 35.3.2 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-cni-pcoupling)

- ["Defining coupling constraints," Section 15.15.4 of the Abaqus/CAE User's Guide](../usi/usi-link.md#usi-itn-helptopic-coupling)

### constraint region

An element-based or node-based surface involved in a coupling constraint.
For more information:- ["Coupling constraints," Section 35.3.2 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-cni-pcoupling)

- ["Defining coupling constraints," Section 15.15.4 of the Abaqus/CAE User's Guide](../usi/usi-link.md#usi-itn-helptopic-coupling)

### construction geometry

Points, lines, or circles in the Abaqus/CAE Sketch module that help you position and align objects in your sketch. Construction geometry is visible only when you are sketching and is not visible on the part or assembly you are creating or modifying after you exit the Sketch module.
For more information:- ["Construction geometry," Section 20.5.2 of the Abaqus/CAE User's Guide](../usi/usi-link.md#usi-ske-congeo)

- ["Connectors: overview," Section 31.1.1 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-elm-econnectoroverview)

### contact initialization

In general contact definitions in Abaqus, a set of rules governing the adjustment of surface positions at the beginning of the analysis. Contact initialization is intended to provide minor corrections to slight overclosures or gaps caused by mesh discretization.
For more information:- ["Controlling initial contact status in Abaqus/Standard," Section 36.2.4 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-cni-agenlcontinitializationstd)

- ["Controlling initial contact status for general contact in Abaqus/Explicit," Section 36.4.4 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-cni-aadjustgeneral)

- ["Contact initialization editor," Section 15.9.5 of the Abaqus/CAE User's Guide](../usi/usi-link.md#usi-itn-manage-continiteditor)

### contact pair

Two model surfaces that can interact with each other according to mechanical, thermal, electrical, or pore fluid contact properties.
For more information:- ["Defining contact pairs in Abaqus/Standard," Section 36.3 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usbcontactpairstd)

- ["Defining contact pairs in Abaqus/Explicit," Section 36.5 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usbcontactpairexp)

### context bar

A region of the Abaqus/CAE GUI located directly above the canvas and drawing area that contains a **Module** list from which you can select a module; other items in the context bar are a function of the module in which you are working. (Abaqus/Viewer contains only the Visualization module.)
For more information:- ["Components of the main window," Section 2.2.1 of the Abaqus/CAE User's Guide](../usi/usi-link.md#uss-top-mainabqwindow)

### context-sensitive help

A detailed set of instructions that allows you to gain immediate access to specific information in the Abaqus/CAE online guide. Invoke context-sensitive help by selecting ****Help**![](../graphics/images/arrow.gif)**On Context**** from the main menu bar and then clicking almost any feature of an Abaqus/CAE window or dialog box.
For more information:- ["Displaying context-sensitive help," Section 2.6.1 of the Abaqus/CAE User's Guide](../usi/usi-link.md#uss-gst-cshelp)

### contour plot

Graphical output from the Visualization module of Abaqus/CAE that displays the values of a particular analysis variable at a specified step and frame. These values are shown as colored lines, colored bands, or colored faces on the model, depending on the customization options you select.
For more information:- [Chapter 44, "Contouring analysis results," of the Abaqus/CAE User's Guide](../usi/usi-link.md#usv-contour)

### CORM (components of relative motion)

Relative displacements and rotations that are local to a connector.
For more information:- ["Connection-type library," Section 31.1.5 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-elm-econnectortypelibrary)

- ["Creating connector sections," Section 15.12.11 of the Abaqus/CAE User's Guide](../usi/usi-link.md#usi-itn-help-createconnprop)

### co-simulation

A multiphysics capability that provides several functions, available within Abaqus or as separate add-on analysis capabilities, for runtime coupling of Abaqus and another analysis program. An Abaqus analysis can be coupled to another Abaqus analysis or to a third-party analysis program to perform multidisciplinary simulations and multidomain (multimodel) coupling. 
For more information:- ["Co-simulation: overview," Section 17.1.1 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-anl-acosimulationover)

- [Chapter 26, "Co-simulation," of the Abaqus/CAE User's Guide](../usi/usi-link.md#usi-adv-cosimulations)

### CSYS (coordinate system)

An Abaqus/CAE datum coordinate system, either rectangular, cylindrical, or spherical.
For more information:- ["Creating datum coordinate systems," Section 62.9 of the Abaqus/CAE User's Guide](../usi/usi-link.md#usi-dtm-csys)

### current viewport

A window on the canvas, identified by a different color title bar than other viewports, in which work in Abaqus/CAE takes place. There is only one current viewport at any time.
For more information:- ["What is a viewport?," Section 4.1.1 of the Abaqus/CAE User's Guide](../usi/usi-link.md#uss-cnv-whatis-viewport)

### custom view

A predefined view (particular combinations of position, orientation, and scale factor)  that Abaqus/CAE allows you to apply to an object in a selected viewport. The custom views are front, back, left, right, top, bottom, and isometric, as well as four user-defined views.
For more information:- ["Custom views," Section 5.2.8 of the Abaqus/CAE User's Guide](../usi/usi-link.md#uss-viw-under-predefviews)




