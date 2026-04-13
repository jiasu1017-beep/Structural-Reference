# 37.5 Creating springs and dashpots connecting points to ground







In an Abaqus/Standard analysis you can define springs and dashpots that connect points to ground and exhibit the same linear behavior independent of field variables. For more information, see ["Springs," Section 32.1.1 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-elm-espring), and ["Dashpots," Section 32.2.1 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-elm-edashpot).

You can obtain history data of stress and strain from a spring/dashpot by using the history output request editor in the Step module. In the **Domain** section of the editor, select **Springs/Dashpots** and choose the desired spring/dashpot from the menu that appears. For more information, see ["Creating an output request," Section 14.12.1](pt03ch14s12hlb01.md).

**To create springs and dashpots that connect points to ground:**

1. From the main menu bar in the Property module or the Interaction module, select ****Special**![](../graphics/images/arrow.gif)**Springs/Dashpots**![](../graphics/images/arrow.gif)**Create****.
2. In the **Create Springs/Dashpots** dialog box that appears, name the springs/dashpots, select **Connect points to ground**, and click **Continue**.
3. Select the points to connect to ground using one of the following methods: - Select the points in the viewport. (For more information, see [Chapter 6, "Selecting objects within the viewport](pt01ch06.md).") **Tip:**The ![](../graphics/ico_filterVisible.png) **Select the Entity Closest to the Screen** tool in the **Selection** toolbar is toggled off by default. If you make an ambiguous selection, Abaqus/CAE highlights the point and displays a description of the point in the lower left corner of the viewport. Use the **Next** and **Previous** buttons to cycle through the possible selections, and click **OK** to confirm your selection. If the model contains a combination of geometry and mesh components, select one of the following from the prompt area: - Select **Geometry** to define the spring/dashpot for geometry or for a reference point. - Select **Mesh** to define the spring/dashpot for a mesh. - To select from a list of existing sets, do the following: 1. Click **Sets** on the right side of the prompt area to display the **Region Selection** dialog box containing a list of available sets. 2. Select the set of interest, and click **Continue**. **Note:**The default selection method is based on the selection method you most recently employed. To revert to the other method, click **Select in Viewport** or **Sets** on the right side of the prompt area. The **Edit Springs/Dashpots** dialog box appears.
4. In the **Direction** portion of the dialog box, do the following: - Click the arrow next to the **Degree of freedom** field, and select the degree of freedom with which the springs/dashpots are associated. - The global coordinate system determines the default spring/dashpot orientations. To specify an orientation for the springs/dashpots, click ![](../graphics/ico_selectBlue.png). Specify the orientation for the springs/dashpots using one of the following methods: - Click **Datum CSYS List** from the prompt area to select a name from a list of datum coordinate systems. - Select a datum coordinate system in the viewport. - Click **Use Global CSYS** from the prompt area to use the global coordinate system. Abaqus/CAE displays the local coordinate system specified for springs/dashpots in the viewport.
5. In the **Property** portion of the dialog box, check the appropriate box to include: - **Spring stiffness**. Enter the force per relative displacement for springs. - **Dashpot coefficient**. Enter the force per relative velocity for dashpots. If you define both spring and dashpot behaviors, they act in parallel.
6. Click **OK** to create the springs/dashpots and to close the **Edit Springs/Dashpots** dialog box. Symbols appear in the viewport that represent the springs/dashpots that you just created.

![](../graphics/images/black4rule.gif)For information on related topics, click any of the following items:- ["Editing the region to which springs and dashpots connecting points to ground are applied," Section 37.6](pt04ch37hla04.md)
- ["Controlling the display of attributes," Section 76.15](pt07ch76hla14.md)
- ["Symbols used to represent special engineering features," Section C.3](ap03s03.md)




