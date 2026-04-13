# 20.14 Adding reference geometry







When you sketch the profile of a feature, Abaqus/CAE projects onto the sketch sheet the part edges and vertices that are in the same plane as the sketch plane. In addition, Abaqus/CAE projects all datum axes and datum points onto the sketch sheet. These projected lines and points are called reference geometry, and you can use them for reference while sketching. If you want to use other edges and vertices, including orphan element edges and orphan nodes, you must project them onto the sketch plane as reference geometry by selecting ****Add**![](../graphics/images/arrow.gif)**References**** from the main menu bar. Alternatively, if you want to create new sketch edges from existing model edges, you can select ****Add**![](../graphics/images/arrow.gif)**Edges**** from the main menu bar (for more information, see ["Projecting edges onto a sketch," Section 20.15](pt03ch20hla03.md)).

**To add reference geometry:**

1. From the Sketcher toolbox, select the **Project References** tool ![](../graphics/ico_sketchProjectReferences.png). For a diagram of the tools in the Sketcher toolbox, see ["The Sketcher tools," Section 20.4.1](pt03ch20s04s01.md). Abaqus/CAE displays prompts in the prompt area to guide you through the procedure.
2. Select the edges, vertices, orphan element edges, and orphan nodes you want to project onto the sketch plane as reference geometry.
3. Click mouse button 2 when you have finished making selections. Abaqus/CAE creates isolated points for the projected reference vertices and nodes and creates reference edges for the geometric and orphan element edges.

![](../graphics/images/black4rule.gif)For information on related topics, click any of the following items:- ["Reference geometry," Section 20.5.1](pt03ch20s05s01.md)
- ["Projecting edges onto a sketch," Section 20.15](pt03ch20hla03.md)




