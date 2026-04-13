# 20.20 Undoing and redoing sketching actions







Use the **Undo** tool ![](../graphics/ico_undo.png) or the **Redo** tool ![](../graphics/ico_redo.png) from the Sketcher toolbox to undo your previous operation or redo your most recently undone operation. For a diagram of the tools in the Sketcher toolbox, see ["The Sketcher tools," Section 20.4.1](pt03ch20s04s01.md).

Depending on your previous action, clicking the undo tool can have the following effect:
- Remove the object just created. Objects include sketch geometry (lines, arcs, circles, ellipses, fillets, splines, or points), construction geometry, or dimensions.
- Restore the sketch to its state prior to the editing operation just performed. Editing operations include copying entities, deleting entities, moving vertices, trimming edges, extending edges, breaking edges, and changing dimensions.
- Remove a retrieved stand-alone sketch, provided you have not positioned the sketch. Once you have positioned the retrieved sketch, clicking the undo tool moves the origin of the retrieved sketch back to the origin of the current sketch.

You can undo and redo several actions in a row. For example, if you sketch a circle and dimension its radius, your first undo operation removes the dimension and your second undo operation removes the circle. You can restore the circle by clicking the redo tool and restore its dimension by clicking the redo tool a second time. Abaqus/CAE stores a history of actions for the current sketch, and you can specify the maximum number of sketching operations to store (see ["Setting the maximum number of recorded sketching operations," Section 20.9.8](pt03ch20s09hlb08.md), for more information).

The **Undo** and **Redo** tools do not perform view manipulation operations. For example, if you sketch a circle, magnify the view, and click the undo tool, Abaqus/CAE deletes the circle (it does not resize the view).
![](../graphics/images/black4rule.gif)For information on related topics, click the following item: - ["Deleting Sketcher objects," Section 20.19.4](pt03ch20s16hlb04.md)




