# R







### radio button

An option button that allows you to choose between mutually exclusive options in some Abaqus/CAE dialog boxes. When a particular option is controlled by radio buttons, you can choose only one of the buttons at a time.
For more information:- ["Using basic dialog box components," Section 3.2.1 of the Abaqus/CAE User's Guide](../usi/usi-link.md#uss-int-dialog-basic)

### rake

A line segment with a series of points specified along its length that controls the locations where Abaqus/CAE displays streamlines for a fluid flow analysis. 
For more information:- ["Creating a stream," Section 74.2 of the Abaqus/CAE User's Guide](../usi/usi-link.md#usi-str-hlp-create)

### recovery (`.rec`) file

A file (`*model_database_name*.rec`) containing commands that Abaqus/CAE can use to replicate the model database currently in memory if it becomes lost due to a catastrophic interruption of your Abaqus/CAE session, such as a power outage. The recovery file contains only those commands that were executed since the last time the model database was saved; all remaining commands are saved in the [journal file](gl01gls11.md#gls-journalfile).
For more information:- ["Recreating an unsaved model database," Section 9.5.3 of the Abaqus/CAE User's Guide](../usi/usi-link.md#usi-dbs-files-recover)

### reference dimension

A type of constraint in Abaqus/CAE that annotates quantities that are already controlled elsewhere in the sketch or quantities such as projected reference geometry that cannot be controlled within the current sketch. A reference dimension indicates the size of geometry in a sketch while allowing the size to change, as opposed to regular dimensions that fix the geometry at the dimensioned size. You can use reference dimensions to indicate the size of reference geometry or to provide alternate dimensions without overconstraining a sketch.
For more information:- ["Constraining, dimensioning, and parameterizing a sketch," Section 20.12 of the Abaqus/CAE User's Guide](../usi/usi-link.md#usi-ske-controlling)

### reference geometry

In Abaqus/CAE, the edges and vertices of the existing part or assembly that are in the same plane as the sketch plane. Abaqus/CAE projects the reference geometry onto the sketch sheet when you enter the Sketch module; you can select reference geometry to help position objects and to constrain the sketch to the underlying geometry.
For more information:- ["Reference geometry," Section 20.5.1 of the Abaqus/CAE User's Guide](../usi/usi-link.md#usi-ske-refgeo)

### reference representation

An alternative representation of a part or a subset (one or more cells) of a part that is not used in an Abaqus/CAE analysis. The reference representation replaces a selected part or portion of a part. The replaced geometry is removed from the active representation of the part—the geometry that will be meshed and used in an analysis—leaving the reference representation to display a translucent view of the same geometry. The reference representation is typically used as a tool to create a new active representation, such as a midsurface model. 
For more information:- ["Understanding the reference representation," Section 35.2 of the Abaqus/CAE User's Guide](../usi/usi-link.md#usi-adv-midsurface-underrefrep)

### reference surface

The spatial geometry defined by the nodes and normal directions of conventional shell elements. The reference surface is typically positioned at the center of the shell's thickness, but it is also possible to offset the reference surface from the midsurface.
For more information:- ["Shell elements: overview," Section 29.6.1 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-elm-eshelloverview)

- ["Defining the initial geometry of conventional shell elements," Section 29.6.3 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-elm-eshellgeometry)

- ["Defining a temperature field," Section 16.11.9 of the Abaqus/CAE User's Guide](../usi/usi-link.md#usi-lbi-helptopics-temp)

### refinement rate limit

An upper bound on the total number of elements calculated by the remesh algorithm in Abaqus/CAE that modulates the aggressivity of the sizing method and controls the introduction of smaller elements. When Abaqus/CAE is remeshing your model adaptively, the coarsening rate limit that you specified in the remeshing rule modulates the rate at which smaller elements are introduced into the mesh. The refinement factor has a significant effect on the convergence of the adaptive meshing procedure and may help you achieve faster and more efficient mesh convergence.
For more information:- ["Refinement and coarsening rate factors" in "Solution-based mesh sizing," Section 12.3.3 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-anl-aadpsizing-ratefactors)

### regenerate

A process that recalculates model geometry after a feature of an Abaqus/CAE model has been modified; by default, Abaqus/CAE automatically regenerates all dependent features if you modify a feature. For example, if you modify a feature of a part, Abaqus/CAE regenerates the part, any instances of the part in the assembly, and the final mesh.
For more information:- ["Using the Feature Manipulation toolset," Section 65.1 of the Abaqus/CAE User's Guide](../usi/usi-link.md#usi-fts-concepts)

### region

Any particular portion of an Abaqus/CAE model. A region can be a vertex, edge, face, cell, node, element, or a collection of these entities. You can specify and name specific regions of a part or assembly by creating sets and surfaces that contain those regions. You can divide a part or an assembly into more regions by partitioning it.
For more information:- [Chapter 73, "The Set and Surface toolsets," of the Abaqus/CAE User's Guide](../usi/usi-link.md#usi-set)

### remeshing rule

A rule used by Abaqus/CAE to adapt your mesh iteratively to meet specified error targets. A remeshing rule describes all aspects of your adaptive meshing specification:      
- The region to which the rule will be applied
- The step during which the rule will be applied
- The error indicator output variables
- The sizing method
- Sizing constraints

For more information:- ["What are remeshing rules?," Section 17.13.1 of the Abaqus/CAE User's Guide](../usi/usi-link.md#usi-mgn-conc-adaptivity-rulerole)

### render style

The style in which you display an object in a viewport in Abaqus/CAE. Examples of render style are **Wireframe**, **Hidden**, and **Shaded**.
For more information:- ["Choosing a render style," Section 76.2 of the Abaqus/CAE User's Guide](../usi/usi-link.md#uss-dsp-dynamic-render)

### replay

An option that specifies the name of the file from which Abaqus/CAE commands are to be replayed. Almost every operation that you perform in Abaqus/CAE is recorded automatically in the replay file (`abaqus.rpy`) in the form of Abaqus commands. Executing the replay file is equivalent to replaying the original sequence of operations.
For more information:- ["Recreating an unsaved model database," Section 9.5.3 of the Abaqus/CAE User's Guide](../usi/usi-link.md#usi-dbs-files-recover)

### restart (`.res`) file

A file (`*job_name*.res`) used to continue an analysis job.

In addition, a capability that allows you to run complex multistep simulations in stages rather than in a single job so that you can examine the results and confirm that the analysis is performing as expected before continuing with the next stage. The Abaqus restart analysis capability uses restart data from a prior solution to determine the model's response to additional load history.
For more information:- ["Restarting an analysis," Section 9.1.1 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-anl-arestart)

- ["Restart output requests," Section 14.5.2 of the Abaqus/CAE User's Guide](../usi/usi-link.md#usi-sim-conc-restart)

### Results Tree

A component of the Abaqus/CAE GUI that provides a visual description of the output data available in your session, including all open output databases and session-specific data such as *X–Y* data and *X–Y* plots.  This tool shares the left side of the Abaqus/CAE interface with the Model Tree.
For more information:- ["An overview of the Results Tree," Section 3.5.2 of the Abaqus/CAE User's Guide](../usi/usi-link.md#uss-top-resultstree-overview)

### resume

The process of restoring a feature that was temporarily deleted from an Abaqus/CAE model to simplify the appearance of a part or assembly. See also [suppress](gl01gls20.md#gls-suppress).
For more information:- ["Using the Feature Manipulation toolset," Section 65.1 of the Abaqus/CAE User's Guide](../usi/usi-link.md#usi-fts-concepts)

### rigid body

A collection of nodes, elements, and/or surfaces that is so much stiffer than the rest of the model that its deformation can be considered negligible. In Abaqus/Standard and Abaqus/Explicit a rigid body is a collection of rigid elements. See also [analytical rigid surface](gl01gls02.md#gls-analyticalrigidsurface) or [discrete rigid part](gl01gls05.md#gls-discreterigid) for information about rigid bodies in Abaqus/CAE.
For more information:- ["Analytical rigid surface definition," Section 2.3.4 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-int-arigidsurf)

- ["Modeling rigid bodies and display bodies," Section 11.7 of the Abaqus/CAE User's Guide](../usi/usi-link.md#usi-prt-rigid)

### rigid body reference node

The node located at the rigid body reference point. When constraining the rigid body, you apply constraints to the degrees of freedom of the rigid body reference node.
For more information:- ["Analytical rigid surface definition," Section 2.3.4 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-int-arigidsurf)

- ["The reference point," Section 11.8.1 of the Abaqus/CAE User's Guide](../usi/usi-link.md#usi-prt-conc-refpoint)

### rigid body reference point

A selected point that is used to define the motion of a rigid body (a rigid part in Abaqus/CAE) or to apply constraints to a rigid body. 
For more information:- ["Analytical rigid surface definition," Section 2.3.4 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-int-arigidsurf)

- ["The reference point," Section 11.8.1 of the Abaqus/CAE User's Guide](../usi/usi-link.md#usi-prt-conc-refpoint)

### round

A concave easing of an interior corner of a part used to reduce stress concentration; also known as a fillet. You can use the blend tools in the Part module to round selected edges of the part in the current viewport to the desired radius.
For more information:- ["Blend features," Section 11.9.5 of the Abaqus/CAE User's Guide](../usi/usi-link.md#usi-prt-conc-round)




