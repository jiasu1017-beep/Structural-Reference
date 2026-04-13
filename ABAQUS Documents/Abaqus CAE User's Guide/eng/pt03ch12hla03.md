# 12.19 Using the Query toolset to obtain assignment information







You can use the Query toolset to display the following:
- A list of all of the regions to which you have assigned sections.
- The name of a section assigned to a selected region.
- Information regarding the regions that require section assignments.
- The beam orientations assigned to selected wire regions.
- The material orientations assigned to selected shell and solid regions.
- A graphic representation of the plies in a composite layup or a composite section.
- The rebar reference orientations assigned to selected shell regions.
- The direction of shell/membrane normals assigned to all shell and axisymmetric wire regions.
- The direction of beam/truss tangents assigned to all wire regions.
- The composite layups and plies that contain disjoint regions.

**To display information about a region:**

1. From the main menu bar, select ****Tools**![](../graphics/images/arrow.gif)**Query****. **Tip:**You can also query the model by clicking the ![](../graphics/ico_info.png) tool in the **Query** toolbar. Abaqus/CAE displays the **Query** dialog box. You can request either a general query or a module-specific query. The **Shell element normals** and **Beam element tangents** queries are general queries. For a discussion of the information displayed by general queries, see ["Obtaining general information about the model," Section 71.2.2](pt06ch71s02hlb02.md). The **Section assignments**, **Regions missing sections**, **Beam orientations**, **Material orientations**, **Rebar orientations**, **Ply stack plot**, and **Disjoint ply regions** queries are specific to the Property module.
2. From the **Property Module Queries** list, select the property of interest.
3. Select the region that you want to query in the viewport. **Tip:**You can limit the types of objects that you can select in the viewport by clicking the selection filter tool ![](../graphics/ico_sketchOptions-nls.png) in the prompt area and then clicking the selection filter of your choice in the dialog box that appears. See ["Using the selection options," Section 6.3](pt01ch06s03.md), for more information.
4. Once you have selected the region that you want to query, the following information appears: **Section assignment queries** Abaqus/CAE displays the name of the section or sections assigned to the selected region in the message area. If you query a region with a section assignment that has been suppressed, Abaqus/CAE reports no section assignments for that region. **Regions missing sections** If any regions of your part require a section assignment and do not have one, Abaqus/CAE highlights these regions in the viewport and prompts you to save the regions as a set. If you want to save these regions as a named set, toggle on **Save regions in a set** from the dialog box that appears; and, if desired, customize the default set name. **Beam section orientation queries** Abaqus/CAE displays the name of the beam orientation assigned to the selected beam region in the message area. In addition, the ![](../graphics/usi_eqn00394.gif)-direction for each beam region in the part appears in the message area. **Material orientation queries** Abaqus/CAE displays the type of the material orientation assigned to the selected region in the message area. For the `GLOBAL`, `SYSTEM`, and `DISCRETE` types, Abaqus/CAE displays the material orientation triads in the viewport. In addition, information concerning the material orientation of each region in the part appears in the message area. **Rebar orientation queries** Abaqus/CAE displays the name of the rebar orientation assigned to the selected region in the message area. In addition, information concerning the rebar reference orientation of each region in the part appears in the message area. **Ply stack plot** Abaqus/CAE creates a new viewport and displays a graphical representation of a core sample through a composite layup or a composite section. The image shows the plies in the layup along with details of each ply, such as its fiber orientation, thickness, reference plane, and integration points. For more information, see [Chapter 53, "Viewing a ply stack plot](pt05ch53.md)." **Disjoint ply regions** Abaqus/CAE displays in the message area the names of the composite layups and the plies within them that contain disjoint regions.
5. To exit the querying procedure, click the cancel button ![](../graphics/afxI_cancel.png) in the prompt area.

![](../graphics/images/black4rule.gif)For information on related topics, click any of the following items:- ["Creating and editing sections," Section 12.13](pt03ch12s13.md)
- ["Understanding the role of the Query toolset," Section 71.1](pt06ch71s01.md)




