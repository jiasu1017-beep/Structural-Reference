# 59.3 Creating attachment points by picking or reading from a file







You can position attachment points by picking each point from the viewport or by reading the coordinates of the points from a file. If desired, you can create the attachment points by projecting the specified points onto a selected face. You can use attachment points to define the location of point-based fasteners. For more information, see ["About fasteners," Section 29.1](pt04ch29s01.md).

**To create attachment points by picking or reading from a file:**

1. From the main menu bar, select ****Tools**![](../graphics/images/arrow.gif)**Attachment**![](../graphics/images/arrow.gif)**Points From File/By Picking****. Abaqus/CAE displays the **Create Attachment Points** dialog box. **Tip:**You can also create attachment points by picking or reading from a file using the ![](../graphics/ico_attPtByPick.png) tool, located with the attachment tools in the Interaction module toolbox or the Property module toolbox. For a diagram of the attachment tools in the toolbox, see ["Understanding attachment points and lines," Section 59.1](pt06ch59s01.md).
2. From the dialog box, use one of the following methods to enter the coordinates of each attachment point in the table: - Select ![](../graphics/ico_selectBlue.png) to pick a point from the part or assembly in the viewport. You can select any existing point from the part, including vertices, datum points, interesting points, reference points, and orphan mesh nodes. You can also enter the *X*-, *Y*-, and *Z*-coordinates of the point in the text field that appears in the prompt area. - Click ![](../graphics/ico_fileOpen.png) to read an ASCII file containing the *X*-, *Y*-, and *Z*-coordinates of each point. - Click ![](../graphics/ico_delete.png) to delete the selected row from the table. For more information, see ["Entering tabular data," Section 3.2.7](pt01ch03s02s07.md). If the attachment points are created on a part, the coordinates you provide are relative to the part's coordinate system. If the attachment points are created on the assembly, the coordinates are relative to the assembly's global coordinate system.
3. To project the specified points onto a selected face, display the **Projection** tabbed page, and do the following: 1. Toggle on **Project onto faces**. 2. Click ![](../graphics/ico_selectBlue.png), and select the faces onto which the points will be projected. The faces can be planar or nonplanar. 3. Select the method for projecting the points. - Choose **Proximity** to allow Abaqus/CAE to draw a vector from each point to the closest point on the selected faces. - Choose **Direction** to define the vector along which to project the points. Click ![](../graphics/ico_selectBlue.png) to choose the **Start point** and **End point** of the vector. For more information, see ["Understanding the projection methods," Section 59.2](pt06ch59s02.md).
4. By default, Abaqus/CAE creates a set that will contain the attachment points. If desired, you can modify the set name. Toggle off **Create set with name** if you do not want to create a set containing the attachment points.
5. Click **OK** to create the attachment points. Abaqus/CAE displays the attachment points. You cannot modify attachment points; you must delete the points and create new points.

![](../graphics/images/black4rule.gif)For information on related topics, click any of the following items:- ["Understanding attachment points and lines," Section 59.1](pt06ch59s01.md)
- ["About fasteners," Section 29.1](pt04ch29s01.md)




