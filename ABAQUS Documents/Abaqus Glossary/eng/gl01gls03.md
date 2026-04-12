# B







### base feature

The first feature you create when building an Abaqus/CAE part; you construct the remainder of the part by adding more features that either modify or add detail to the base feature. All other features of the part are children of the base feature; therefore, the base feature cannot be suppressed or deleted.
For more information:- ["The base feature," Section 11.3.2 of the Abaqus/CAE User's Guide](../usi/usi-link.md#usi-prt-conc-base)

### base solution

In general, the initial run or solution of a process; the meaning varies according to the context in which the term is used. 
For more information:- ["Characteristics of error indicators" in "Solution-based mesh sizing," Section 12.3.3 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-anl-aadpsizing-chracteristics)

### base solution variable

The variable selected to use in the calculation of the base solution of a process. Base solution variables are expressed as element averages of the base solution and identified by an “AVG” suffix; for example, MISESAVG.
For more information:- ["Solution accuracy" in "Error indicator output," Section 4.1.4 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-anl-aadperrorindicators-variables)

### basic manager

An Abaqus/CAE dialog box that contains lists of all the objects of a certain type that you have created in the current model. The basic manager also contains **Create**, **Edit**, **Copy**, **Rename**, and **Delete** buttons that you can use to manipulate existing objects and to create new ones. See also [step-dependent manager](gl01gls20.md#gls-stepmanager). 
For more information:- ["What are basic managers?," Section 3.4.1 of the Abaqus/CAE User's Guide](../usi/usi-link.md#uss-int-mgr-whatis)

### BC

See [boundary condition](gl01gls03.md#gls-boundarycondition).

### beam sections

The area properties for the cross-section of beam elements.
For more information:- ["Meshed beam cross-sections," Section 10.6 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usbabeamgen)

- ["Choosing a beam cross-section," Section 29.3.2 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-elm-ebeamsections)

### bias factor

A factor defined in an [adaptive remeshing](gl01gls02.md#gls-adaptiveremeshing) rule that determines the distribution of element sizing between the locations of minimum and maximum solution intensity.
For more information:- ["Bias factor" in "Solution-based mesh sizing," Section 12.3.3 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-anl-aadpsizing-biasfactor)

### bias function

See [bias parameter](gl01gls03.md#gls-biasparam).
For more information:- ["The bias parameter" in "Mode-based steady-state dynamic analysis," Section 6.3.8 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-anl-asteadystdyn-biasparam)

### bias parameter

In a steady-state dynamic analysis, a variable used to bias the frequency points for which results are required toward the ends of the user-defined frequency range. The bias parameter provides closer spacing of the results points either toward the middle or toward the ends of each frequency interval.
For more information:- ["The bias parameter" in "Mode-based steady-state dynamic analysis," Section 6.3.8 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-anl-asteadystdyn-biasparam)

### blend

A geometric fillet or chamfer that can be created in Abaqus/CAE to smooth an edge of a three-dimensional solid part.
For more information:- ["Blend features," Section 11.9.5 of the Abaqus/CAE User's Guide](../usi/usi-link.md#usi-prt-conc-round)

### blind cut

A cut that penetrates a three-dimensional object only to a specified depth, rather than passing all the way through it. In Abaqus/CAE this depth is stored as a parameter of the cut feature and can be modified.
For more information:- ["Adding a cut feature," Section 11.24 of the Abaqus/CAE User's Guide](../usi/usi-link.md#usi-prt-help-addcut)

### bottom-up meshing

A manual process used to create a hexahedral or hex-dominated mesh on a solid region that is unmeshable or difficult to mesh using the automated top-down meshing techniques. Bottom-up meshing allows you to select sweep, extrude, or revolve methods and parameters such as the source and connecting faces that Abaqus/CAE uses to build up a solid mesh of hexahedral elements. See also [top-down meshing](gl01gls21.md#gls-topdown).
For more information:- [Chapter 17, "The Mesh module," of the Abaqus/CAE User's Guide](../usi/usi-link.md#usi-mgn)

### boundary condition

A prescribed value for a basic solution variable, such as displacement, rotation, or temperature.
For more information:- ["Boundary conditions in Abaqus/Standard and Abaqus/Explicit," Section 34.3.1 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-prc-pboundary)

- ["Boundary conditions in Abaqus/CFD," Section 34.3.2 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-prc-pboundarycfd)

- [Chapter 16, "The Load module," of the Abaqus/CAE User's Guide](../usi/usi-link.md#usi-lbi)

### boundary face

In an Abaqus/Standard analysis, an exterior face or a face of a free surface.
For more information:- ["Eulerian analysis," Section 14.1.1 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-anl-aeuleriananalysis)

In an Abaqus/CAE model, a face of a three-dimensional element that is shared by only a single element.
For more information:- ["Merging and cutting part instances," Section 13.7.1 of the Abaqus/CAE User's Guide](../usi/usi-link.md#usi-asm-conc-merge-hybrid)

### boundary mesh

The mesh generated on the boundary faces of a three-dimensional geometric region.
For more information:- ["What is a tetrahedral boundary mesh?," Section 17.10.4 of the Abaqus/CAE User's Guide](../usi/usi-link.md#usi-mgn-conc-meshing-freepreview)




