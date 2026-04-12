# D







### damage evolution

A law that defines how material degrades after one or more damage initiation criteria are met. Multiple forms of damage evolution may act on a material at the same time—one for each damage initiation criterion that was defined.
For more information:- ["Damage evolution and element removal for ductile metals," Section 24.2.3 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-mat-cdamageevolductile)

- ["Damage evolution and element removal for fiber-reinforced composites," Section 24.3.3 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-mat-cdamageevolfibercomposite)

- ["Damage evolution for ductile materials in low-cycle fatigue," Section 24.4.3 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-mat-cdamageevolfatigue)

- ["Damage evolution" in "Defining damage," Section 12.9.3 of the Abaqus/CAE User's Guide](../usi/usi-link.md#usi-prp-mechanical-damage-evolution)

### damage initiation criteria

The conditions that will initiate a crack. They can be based on either maximum principal stress or maximum principal strain to represent the behavior of a material.
For more information:- [Chapter 24, "Progressive Damage and Failure," of the Abaqus Analysis User's Guide](../usb/usb-link.md#usbdamage)

- ["Defining damage," Section 12.9.3 of the Abaqus/CAE User's Guide](../usi/usi-link.md#usi-prp-mechanical-damage)

### data check

An abbreviated Abaqus/Standard, Abaqus/Explicit, or Abaqus/CFD execution that checks only that the model is consistent and that all required model options have been set.
For more information:- ["Abaqus/Standard, Abaqus/Explicit, and Abaqus/CFD execution," Section 3.2.2 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-int-danalysisproc)

- ["Performing a data check on a model," Section 19.7.3 of the Abaqus/CAE User's Guide](../usi/usi-link.md#usi-ana-jobman-datacheckbtn)

- ["Performing a data check on an adaptivity process," Section 19.9.2 of the Abaqus/CAE User's Guide](../usi/usi-link.md#usi-ana-adpman-datacheckbtn)

### data line

A line in an Abaqus/Standard, Abaqus/Explicit, or Abaqus/CFD input file used to provide data that are more easily given in lists than as parameters on an option. If a data line is required, it must immediately follow the keyword line introducing the option.
For more information:- ["Input syntax rules," Section 1.2.1 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-int-iinputsyntax)

### datum

A feature of an Abaqus/CAE model that represents auxiliary geometry that can be used for reference when modeling a part or assembly. The following types of datum are available: points, axes, planes, and coordinate systems.
For more information:- ["Understanding the role of datum geometry," Section 62.1 of the Abaqus/CAE User's Guide](../usi/usi-link.md#usi-dtm-intro)

### Datum toolset

An Abaqus/CAE toolset used to create datum points, axes, planes, and coordinate systems with respect to a combination of existing geometry—such as vertices, planes, and edges—and existing datum geometry.
For more information:- [Chapter 62, "The Datum toolset," of the Abaqus/CAE User's Guide](../usi/usi-link.md#usi-dtm)"

### decoration

The Abaqus/CAE viewport title and the viewport border.
For more information:- ["Working with viewports," Section 4.3 of the Abaqus/CAE User's Guide](../usi/usi-link.md#uss-cnv-workwith-viewports)

### deformable part

A part that can deform under load. See also [discrete rigid part](gl01gls05.md#gls-discreterigid).
For more information:- ["Part types," Section 11.4.2 of the Abaqus/CAE User's Guide](../usi/usi-link.md#usi-prt-conc-type)

### deformation scale factor

The factor that is applied to the deformation field when you display a plot of a deformed model in Abaqus/CAE. You can scale the deformations to magnify, reduce, or otherwise distort the deformed model shape.
For more information:- ["Scaling deformations," Section 55.4.1 of the Abaqus/CAE User's Guide](../usi/usi-link.md#usv-custom-deffactorframe)

### deformed field output variable

The variable whose values control the shape of the model in a deformed shape plot in Abaqus/CAE. Deformed field output variables can only be vector quantities such as displacement or velocity.
For more information:- ["Selecting the deformed field output variable," Section 42.5.4 of the Abaqus/CAE User's Guide](../usi/usi-link.md#usv-res-deformedtabbtn)

### deformed shape plot

An Abaqus/CAE plot that displays the shape of a model at a specified step and frame of the analysis results according to the values of the deformed field output variable that you specify.
For more information:- [Chapter 43, "Plotting the undeformed and deformed shapes," of the Abaqus/CAE User's Guide](../usi/usi-link.md#usv-deformed)

### degrees of freedom (dof)

The fundamental variables calculated during an analysis: the set of independent displacements and/or rotations that specify completely the displaced or deformed position and orientation of the body or system. For example, in a stress/displacement analysis the degrees of freedom are the translations. For shell and beam elements the degrees of freedom are the rotations at each node.
For more information:- ["Conventions," Section 1.2.2 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-int-iconventions)

### Discrete Field toolset

An Abaqus/CAE toolset that allows you to create and manage discrete fields in the Property module, the Interaction module, or the Load module. Discrete fields associate unique values with individual nodes or elements in a meshed model. You can use discrete fields to define spatially varying parameters for selected model attributes, such as a temperature that varies by node over a region in an initial temperature predefined field.
For more information:- [Chapter 63, "The Discrete Field toolset," of the Abaqus/CAE User's Guide](../usi/usi-link.md#usi-dfl)

### discrete orientation

A definition of a spatially varying orientation for each native or orphan mesh element. A discrete orientation can be based on the topology of the part. You define the [normal axis](gl01gls15.md#gls-normalaxis) and the [primary axis](gl01gls17.md#gls-primaryaxis), and Abaqus/CAE uses these axes to construct a right-handed Cartesian coordinate system. A variety of selection methods are available to define the desired axes. Discrete orientations can be used for material orientations and composite layup orientations.
For more information:- ["Using discrete orientations for material orientations and composite layup orientations," Section 12.16 of the Abaqus/CAE User's Guide](../usi/usi-link.md#usi-prp-discrete-orient)

### discrete rigid part

A part that is assumed to be rigid and is used in contact analyses to model bodies that cannot deform. See also [deformable part](gl01gls05.md#gls-deformbody).
For more information:- ["Rigid parts," Section 11.7.1 of the Abaqus/CAE User's Guide](../usi/usi-link.md#usi-prt-conc-rigid)

### discrete set

An Abaqus/CAE set that is made up of either nodes or elements that you have selected from an orphan mesh.
For more information:- [Chapter 73, "The Set and Surface toolsets," of the Abaqus/CAE User's Guide](../usi/usi-link.md#usi-set)

### display group

A collection of selected model components in Abaqus/CAE that can contain any combination of part instances, geometry (cells, faces, or edges), nodes, elements, and surfaces or the default (entire) model. A display group allows you to reduce clutter on your screen and to focus on an area of interest within your model.
For more information:- [Chapter 78, "Using display groups to display subsets of your model," of the Abaqus/CAE User's Guide](../usi/usi-link.md#uss-dgp)

### display list

A feature in Abaqus/CAE that helps you display repeated images faster. When an object is displayed repeatedly (for example, in an animation), the system must perform many computations to render each animation frame. If you enable the display list option, the results of these computations are stored in a display list the first time you display the animation. The next time you display the animation, Abaqus/CAE refers to the display list instead of performing the calculations again; as a result, the animation is faster.
For more information:- ["Using display lists," Section 7.2 of the Abaqus/CAE User's Guide](../usi/usi-link.md#uss-pfm-lists)

### DMP (distributed memory parallel)

A mode of parallel execution where each processor has its own memory. Abaqus supports DMP using specific MPI libraries and interconnects. See also [MPI](gl01gls14.md#gls-mpi).

### double buffering

A graphics rendering technique used in Abaqus/CAE to prevent screen flicker when the viewport is refreshed.
For more information:- ["GraphicsOptions object," Section 17.9 of the Abaqus Scripting Reference Guide](../ker/ker-link.md#ker-graphicsoptions-pyc)

### double precision

The storage and manipulation of floating point numbers in 8 B, as opposed to single precision which uses a standard 4 B. Abaqus/Explicit performs calculations using double precision by default.
For more information:- ["Abaqus/Standard, Abaqus/Explicit, and Abaqus/CFD execution," Section 3.2.2 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-int-danalysisproc)

- ["Using the Abaqus environment settings," Section 3.3.1 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-int-denvfile)

### drag mode

A setting in Abaqus/CAE that allows you to display an image as a simple wireframe during mouse manipulations such as panning, zooming, and rotating; this mode allows faster manipulation of very large models in the shaded render style instead of the current render style (wireframe, filled, hidden line, or shaded). 
For more information:- ["Controlling drag mode," Section 7.6 of the Abaqus/CAE User's Guide](../usi/usi-link.md#uss-pfm-dm)

### drawing area

The visible portion of the Abaqus/CAE [canvas](gl01gls04.md#gls-canvas).
For more information:- ["Components of the main window," Section 2.2.1 of the Abaqus/CAE User's Guide](../usi/usi-link.md#uss-top-mainabqwindow)




