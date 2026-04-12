# F







### facet

An individual element face or edge.

### fastener

A point-to-point connection between two or more surfaces such as a spot weld or rivet connection. When you model fasteners, the attachment to each of the surfaces being connected is distributed to several nodes to be connected in the neighborhood of the [fastening point](gl01gls07.md#gls-fasteningpoint).
For more information:- ["Mesh-independent fasteners," Section 35.3.4 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-cni-afastener)

- ["About fasteners," Section 29.1 of the Abaqus/CAE User's Guide](../usi/usi-link.md#usi-eng-fastener-overview)

### fastening point

The actual point where a fastener layer attaches to the surfaces that are being connected with fasteners. The location is determined by considering the [positioning point](gl01gls17.md#gls-positioningpoint) location, projection method, and surfaces to be fastened.
For more information:- ["Mesh-independent fasteners," Section 35.3.4 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-cni-afastener)

### features

The basic definitions that combine to make up an Abaqus/CAE native part and assembly, such as geometry operations and positioning constraints. Each feature contains parameters, such as size, location, and depth. Abaqus/CAE retains the parameters that define each feature and uses this information to regenerate a part or assembly if a feature is modified.
For more information:- ["What is feature-based modeling?," Section 11.3 of the Abaqus/CAE User's Guide](../usi/usi-link.md#usi-prt-concepts)

### feature angle

An angle formed between the normals of the two facets connected to an edge.
For more information:- ["Assigning surface properties for general contact in Abaqus/Explicit," Section 36.4.2 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-cni-asurfacepropassign)

- ["Surface properties for general contact in Abaqus/Standard," Section 36.2.2 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-cni-asurfacepropassignstd)

- ["Defining model feature edges," Section 55.3.2 of the Abaqus/CAE User's Guide](../usi/usi-link.md#usv-gen-featureframe)

- ["Defining mesh feature edges," Section 76.5 of the Abaqus/CAE User's Guide](../usi/usi-link.md#uss-dsp-dynamic-featangle)

### Feature Manipulation toolset

An Abaqus/CAE toolset that contains tools that you use to create and manage features.
For more information:- [Chapter 65, "The Feature Manipulation toolset," of the Abaqus/CAE User's Guide](../usi/usi-link.md#usi-fts)

### field

A definition of input or output data representing the value of a variable such as displacement, temperature, or pressure over a domain.

### field output

The output of variables that are written relatively infrequently to the output database. Typically, you request field output from your entire model or a large region of your model; Abaqus/Standard and Abaqus/Explicit write every component of the variable to the output database at the selected frequency. In the Abaqus/CAE Visualization module you can view field output in the form of a deformed, contour, or symbol plot and you can produce a report of field output.
For more information:- ["Output to the output database," Section 4.1.3 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-out-odboutput)

### fillet

A circular arc that joins two lines in a continuous manner. When you are using the Sketch module, you can create a fillet between two lines meeting at an angle. When you are creating or modifying a three-dimensional solid part, you can fillet, or round, selected edges.
For more information:- ["Sketching fillets between two lines," Section 20.10.9 of the Abaqus/CAE User's Guide](../usi/usi-link.md#usi-ske-filletbtn)

- ["Blending edges," Section 11.27 of the Abaqus/CAE User's Guide](../usi/usi-link.md#usi-prt-help-blendedges)

### fixed-interface substructure dynamic modes

[Substructure dynamic modes](gl01gls20.md#gls-substructuredynamic) in which all retained degrees of freedom have been constrained.
For more information:- ["Defining substructures," Section 10.1.2 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-anl-asuperelementdef)

### fixed part instance

The [part instance](gl01gls17.md#gls-partinstance) whose position remains fixed during the application of an assembly constraint in Abaqus/CAE.
For more information:- ["How the position constraint methods differ," Section 13.5.2 of the Abaqus/CAE User's Guide](../usi/usi-link.md#usi-asm-concept-alignmate)

### frame

In a structure, a mechanical skeleton structure.

In a finite element model, a frame element provides efficient modeling for design calculations of frame-like structures composed of initially straight, slender members.
For more information:- ["Frame elements," Section 29.4.1 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-elm-eframe)

In history output data, a container in the output database structure that corresponds to a snapshot in the history of the simulation. In addition, the term applies to a single plot in an animating series.
For more information:- ["Generating output database reports," Section 3.2.20 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-int-dodbreportproc)

- ["Selecting the results step and frame," Section 42.3 of the Abaqus/CAE User's Guide](../usi/usi-link.md#usv-res-stepframe)

- [Chapter 49, "Animating plots," of the Abaqus/CAE User's Guide](../usi/usi-link.md#usv-animation)

### free body cross-section

The set of nodes and elements that make up the surface across which you want Abaqus/CAE to display the resultant forces and moments. 
For more information:- ["Resultant forces and moments on free body cuts in Abaqus/CAE," Section 67.1 of the Abaqus/CAE User's Guide](../usi/usi-link.md#usi-fbd-intro)

- ["Creating or editing a free body cut," Section 67.2 of the Abaqus/CAE User's Guide](../usi/usi-link.md#usi-fbd-hlp-create)

### free body cut

In the Visualization module of Abaqus/CAE, a tool that displays the resultant forces and moments transmitted across a selected surface of your model.
For more information:- ["Resultant forces and moments on free body cuts in Abaqus/CAE," Section 67.1 of the Abaqus/CAE User's Guide](../usi/usi-link.md#usi-fbd-intro)

- ["Creating or editing a free body cut," Section 67.2 of the Abaqus/CAE User's Guide](../usi/usi-link.md#usi-fbd-hlp-create)

### free meshing

 A meshing technique that uses no preestablished mesh patterns and allows more flexibility than structured meshing. When you mesh a region using the structured meshing technique, you can predict the pattern of the mesh based on the region topology. In contrast, it is impossible to predict a free mesh pattern before creating the mesh. 
For more information:- ["Free meshing," Section 17.10 of the Abaqus/CAE User's Guide](../usi/usi-link.md#usi-mgn-conc-free)

### free-interface substructure dynamic modes

[Substructure dynamic modes](gl01gls20.md#gls-substructuredynamic) in which none of the retained degrees of freedom have been constrained.
For more information:- ["Defining substructures," Section 10.1.2 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-anl-asuperelementdef)

### free rotation handle

The point at the top of the [3D compass](gl01gls01.md#gls-3dcompass) that allows you to rotate the view of a model in any direction.
For more information:- ["Rotating the view using the 3D compass," Section 5.3.1 of the Abaqus/CAE User's Guide](../usi/usi-link.md#uss-viw-3dcompass-rotate)

### frustum

The three-dimensional space visible in a viewport in movie camera mode; it is a truncated pyramid with its apex at the camera position. The frustum begins at the near plane (a plane parallel to the pyramid base but closer to the camera) and extends to the far plane (the pyramid base). The near plane and far plane positions are determined by the view options in Abaqus/CAE.
For more information:- ["Understanding camera modes and view options," Section 5.1 of the Abaqus/CAE User's Guide](../usi/usi-link.md#uss-viw-under-camera)




