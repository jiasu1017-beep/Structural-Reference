# A







### Abaqus/AMS

An add-on analysis capability for Abaqus/Standard that allows you to select the automatic multi-level substructuring (AMS) eigensolver when performing a natural frequency extraction. 
For more information:- ["Automatic multi-level substructuring (AMS) eigensolver" in "Natural frequency extraction," Section 6.3.5 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-anl-afreqextraction-ams)

### Abaqus/Aqua

An add-on analysis capability for Abaqus/Standard and Abaqus/Explicit for calculating drag and buoyancy loads based on steady current, wave, and wind effects for modeling offshore piping and floating platform structures. Abaqus/Aqua is applicable for structures that can be idealized using line elements, including beam, pipe, and truss elements.
For more information:- ["Abaqus/Aqua analysis," Section 6.11.1 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-anl-aaqua)

### Abaqus/CAE

The Complete Abaqus Environment: a program that provides a simple, consistent interactive graphical interface for creating, submitting, monitoring, and evaluating results from Abaqus simulations. Abaqus/CAE is divided into modules, where each module defines a logical aspect of the modeling process; for example, defining the geometry, defining material properties, generating a mesh, submitting analysis jobs, and interpreting results.
For more information:- [Part I, "Interacting with Abaqus/CAE," of the Abaqus/CAE User's Guide](../usi/usi-link.md#uss-inter-abq)

### Abaqus/CFD

A computational fluid dynamics program with extensive support for preprocessing, simulation, and postprocessing in Abaqus/CAE. Abaqus/CFD provides scalable parallel CFD simulation capabilities to address a broad range of nonlinear coupled fluid-thermal and fluid-structural problems.
For more information:- ["Introduction: general," Section 1.1.1 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-int-igeneral)

- ["Fluid dynamic analysis procedures: overview," Section 6.6.1 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-anl-afluidproc)

### Abaqus/Design

An add-on capability for Abaqus/Standard and Abaqus/Explicit that allows an Abaqus model to be defined with parametric variables. Parameter studies with such models can be performed with scripts that generate models with various values for the parametric variables, run the analyses, and gather the results. These scripts are developed using Python, an interpreted language.
For more information:- ["Parametric input," Section 1.4.1 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-int-iparinput)

### Abaqus/Explicit

 An explicit dynamics finite element program that provides nonlinear, transient, dynamic analysis of solids and structures using explicit time integration. Its powerful contact capabilities, reliability, and computational efficiency on large models also make it highly effective for quasi-static applications involving discontinuous nonlinear behavior.
For more information:- ["Introduction: general," Section 1.1.1 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-int-igeneral)

### Abaqus/Foundation

An optional subset of Abaqus/Standard that provides more cost-efficient access to the linear static and dynamic analysis functionality in Abaqus/Standard.

### Abaqus PDE (Abaqus Python Development Environment)

An application that allows you to create, edit, test, and debug Python scripts. It can be used with scripts containing general Python commands, Abaqus Scripting Interface commands, or Abaqus/CAE graphical user interface (GUI) commands.
For more information:- [Part III, "The Abaqus Python development environment," of the Abaqus Scripting User's Guide](../cmd/cmd-link.md#cmd-pde)

### Abaqus/Standard

A general-purpose finite element program that can be used for analysis of static, dynamic, heat transfer, and a variety of coupled problems. Abaqus/Standard provides both automatic and direct user control of the time step and is effective for analyzing the static, dynamic, thermal, and electrical response of both linear and nonlinear models.
For more information:- ["Introduction: general," Section 1.1.1 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-int-igeneral)

### Abaqus/Viewer

A subset of Abaqus/CAE that contains just the Visualization module to provide graphical display of finite element models and results. It obtains model and result information from the output database (ODB). The major capabilities of Abaqus/Viewer include undeformed and deformed shape plotting; results, contour, and symbol plotting; *X–Y* plotting and reporting; field output reporting; plot customization; and animation.
For more information:- [Part V, "Viewing results," of the Abaqus/CAE User's Guide](../usi/usi-link.md#usi-vismod)

### ACIS

An industry-standard library of geometric modeling functions that reads and writes ACIS format files (`*file_name*.sat`). ACIS files give you a way to move geometry between Abaqus/CAE and third-party modeling products. You can import the base feature of a part from an ACIS file; in addition, you can export a part or the part instances in the assembly to an ACIS file. 
For more information:- ["Using the File menu," Section 9.6 of the Abaqus/CAE User's Guide](../usi/usi-link.md#usi-dbs-filepopmenu)

### active representation

Geometry that will be meshed and used in an analysis, including all geometry in a model except for reference representations and suppressed features.
For more information:- ["Understanding midsurface modeling," Section 35.1 of the Abaqus/CAE User's Guide](../usi/usi-link.md#usi-adv-midsurface-understand)

### adaptive remeshing

An automated process to refine mesh discretization based on selected error indicators in solution results.
For more information:- ["Adaptive remeshing: overview," Section 12.3.1 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-anl-aadpover)

### adaptivity process

A succession of analysis jobs that Abaqus/CAE creates during adaptive remeshing. Each job uses a mesh that was generated by Abaqus/CAE based on the values of the error indicator output variables in the output database and the settings in your remeshing rule.
For more information:- ["Understanding adaptivity processes," Section 19.3 of the Abaqus/CAE User's Guide](../usi/usi-link.md#usi-ana-adaptivityconcepts)

### ALE (Arbitrary Lagrangian-Eulerian) adaptive meshing

A technique that combines the features of pure Lagrangian analysis and pure Eulerian analysis to control element distortion in cases where large deformation or loss of material occurs. ALE allows the mesh to move independently of the material but does not alter the topology (elements and connectivity) of the mesh. 
For more information:- ["ALE adaptive meshing: overview," Section 12.2.1 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-anl-aaleover)

### analysis input file

See [input file](gl01gls10.md#gls-inputfile).

### analysis input file processor

A component of Abaqus that processes the input file and submits the resulting data to the appropriate analysis program, either Abaqus/Standard, Abaqus/Explicit, or Abaqus/CFD. The input file processor interprets the Abaqus options, performs the necessary consistency checking, and prepares the data for the analysis program.
For more information:- ["Defining a model in Abaqus," Section 1.3.1 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-int-imodel)

### analysis procedure

See [procedure](gl01gls17.md#gls-procedure).

### Analytical Field toolset

An Abaqus/CAE toolset that allows you to define spatially varying parameters for selected interactions and prescribed conditions in the Interaction module or in the Load module.
For more information:- [Chapter 58, "The Analytical Field toolset," of the Abaqus/CAE User's Guide](../usi/usi-link.md#usi-fld)

### analytical rigid part

See [analytical rigid surface](gl01gls02.md#gls-analyticalrigidsurface).

### analytical rigid surface

An undeformable geometric surface with profiles that can be described with straight and curved line segments. These profiles can be swept along a generator vector or rotated about an axis to form a three-dimensional surface. Analytical rigid surfaces are not element-based and, thus, can model many surface geometries exactly and may result in decreased computational cost in an analysis.
For more information:- ["Analytical rigid surface definition," Section 2.3.4 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-int-arigidsurf)

- ["Rigid parts," Section 11.7.1 of the Abaqus/CAE User's Guide](../usi/usi-link.md#usi-prt-conc-rigid)

### anchor points

In Abaqus/CAE, points in a viewport that control the motion of text and arrow annotations. 
For more information:- ["What are arrow and text annotations?," Section 4.1.2 of the Abaqus/CAE User's Guide](../usi/usi-link.md#uss-cnv-whatis-anno)

In Abaqus/Standard contact interactions, points created on a surface by the small-sliding tracking approach to define the location and orientation of planar contact constraints.
For more information:- ["Contact formulations in Abaqus/Standard," Section 38.1.1 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-cni-acontactpairform)

### angle method

A process in Abaqus/CAE that allows you to select multiple faces, edges, elements, element faces, or nodes based on the spatial angles between the items.
For more information:- ["Using the angle and feature edge method to select multiple objects," Section 6.2.3 of the Abaqus/CAE User's Guide](../usi/usi-link.md#uss-pic-byangle)

### annotation

An explanatory note or symbol that you create when working with Abaqus/CAE. Abaqus/CAE automatically generates several types of annotations. Viewport annotations generated by Abaqus/CAE include the triad as well as the legend, title block, and state block of Visualization module plots.
For more information:- ["What are arrow and text annotations?," Section 4.1.2 of the Abaqus/CAE User's Guide](../usi/usi-link.md#uss-cnv-whatis-anno)

- [Chapter 56, "Customizing viewport annotations," of the Abaqus/CAE User's Guide](../usi/usi-link.md#usv-general)

### assembly

A collection of positioned part instances. A model contains only one assembly.
For more information:- ["Defining an assembly," Section 2.10.1 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-int-ipartassy)

- [Chapter 13, "The Assembly module," of the Abaqus/CAE User's Guide](../usi/usi-link.md#usi-asm)

### Assembly module

An Abaqus/CAE module used to create instances of parts and to construct an assembly by positioning those instances relative to each other in a global coordinate system.
For more information:- [Chapter 13, "The Assembly module," of the Abaqus/CAE User's Guide](../usi/usi-link.md#usi-asm)

### assembly-related modules

Abaqus/CAE modules in which the assembly is displayed in the viewport. The Assembly, Step, Interaction, Load, and Mesh modules are considered to be assembly-related modules.
For more information:- ["What is a module?," Section 2.3 of the Abaqus/CAE User's Guide](../usi/usi-link.md#uss-top-whatis-module)

### assembly set

Named groupings of points, edges, surfaces, or volumes that identify regions of an Abaqus/CAE assembly.
For more information:- ["How do part sets and assembly sets differ?," Section 73.2.2 of the Abaqus/CAE User's Guide](../usi/usi-link.md#usi-set-conc-difference)

### attachment line

A feature in Abaqus/CAE that allows you to specify the location of discrete fasteners by projecting selected points through multiple faces.
For more information:- ["Understanding attachment points and lines," Section 59.1 of the Abaqus/CAE User's Guide](../usi/usi-link.md#usi-att-conc-attach-methods)

### attachment point

A feature in Abaqus/CAE that allows you to specify the location of a [positioning point](gl01gls17.md#gls-positioningpoint) for point-based fasteners.
For more information:- ["Understanding attachment points and lines," Section 59.1 of the Abaqus/CAE User's Guide](../usi/usi-link.md#usi-att-conc-attach-methods)

### Attachment toolset

An Abaqus/CAE toolset available in the Property, Assembly, and Interaction modules that allows you to create and manage attachment points and lines that you can use to create point-based and discrete fasteners, respectively.
For more information:- [Chapter 59, "The Attachment toolset," of the Abaqus/CAE User's Guide](../usi/usi-link.md#usi-att)

### AutoCAD files

Two-dimensional profiles stored in AutoCAD files (`*file_name*.dxf`) that can be imported into Abaqus/CAE as stand-alone sketches.
For more information:- ["Imported sketches," Section 20.3.2 of the Abaqus/CAE User's Guide](../usi/usi-link.md#usi-ske-import)




