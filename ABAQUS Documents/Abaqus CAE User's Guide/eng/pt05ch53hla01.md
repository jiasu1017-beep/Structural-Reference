# 53.1 Overview of ply stack plots







A ply stack plot is a graphical representation of the plies from a selected region of a composite model. In effect, a ply stack plot is a core sample of the plies in the selected region. The region can be from a composite layup or from a composite section.

You can customize the appearance of a ply stack plot. For example, the image can show the sequence of plies, the orientation of the fibers in each ply, the material in each ply, the relative thickness of the ply, and the location of the reference surface. [Figure 53--1](pt05ch53hla01.md#usv-stack-overview) illustrates a ply stack plot.

**Figure 53–1** A ply stack plot.

![](../graphics/usv-stack-overview-nls.png)

The staircase appearance has no corresponding physical meaning; it is just a mechanism that allows you to view all of the plies in a region. For example, the plies are not ending at each stair.

The triad in a ply stack plot represents the element orientation system, and it shows the shell normal or stacking direction (the 3-direction) and the 1- and 2-directions for the plies.  The fibers are always drawn in the 1–2 plane at an angle with respect to the 1-direction. In solid composite layups the fibers in a ply do not always run parallel to the 1–2 plane (e.g., if the 3-direction of the ply orientation and the element stacking direction are not aligned). In this situation the fibers in the ply stack plot are not a true depiction of the fibers in the composite, but rather a graphical representation of the rotation angles in the composite section or layup definition: the angle drawn in the ply stack plot is the rotation angle specified in the ply table measured about the element stacking direction axis. For more information, see ["Understanding composite layups and orientations," Section 23.3](pt04ch23s03.md).

Ply stack plots do not draw fibers for ply orientations that are based on a user-defined coordinate system or a rotation angle distribution. Abaqus/CAE displays an asterisk (for coordinate systems) or a caret (for rotation angle distributions) on such plies to signify that it cannot draw lines in the 1–2 plane that accurately represent the fiber direction for the ply. Similarly, if you use a discrete field distribution to define a ply's thickness, Abaqus/CAE draws the ply in the ply stack plot based on the average thickness of the other uniform plies in the layup and displays the discrete field name next to the plot (if thickness labels are turned on).

It is important to know the position of the reference surface when you are modeling a composite with conventional shell elements. The mesh will be positioned on the reference surface, and contact is defined relative to the reference surface. The ply stack plot allows you to view the reference surface relative to other plies in the composite, as shown in [Figure 53--2](pt05ch53hla01.md#usv-stack-offset).

**Figure 53–2** The reference surface in a ply stack plot.

![](../graphics/usv-stack-offset-nls.png)

You can display a ply stack plot in the Property module after you have created a composite layup or assigned a composite section to a region. You can also display a ply stack plot in the Visualization module after you have analyzed a model with a composite layup or a composite section. For more information, see ["Defining composite layups," Section 12.2.4](pt03ch12s02s04.md), and ["Creating composite shell sections," Section 12.13.7](pt03ch12s13s02.md), in the HTML version of this guide.

To produce a ply stack plot, select ****Tools**![](../graphics/images/arrow.gif)**Query**** from the main menu bar and select **Ply stack plot** from the dialog box that appears. After you have displayed a ply stack plot, you can customize its appearance by clicking the **Ply Stack Plot Options** button from the prompt area or by clicking the ![](../graphics/ico_plotPlyStackOptions.png) tool in the toolbox (in the Visualization module). For detailed instructions on customizing a ply stack plot, see ["Customizing ply stack plots," Section 53.2](pt05ch53s01.md).



