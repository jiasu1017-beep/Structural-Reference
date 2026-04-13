# 33.5 Defining heat capacitance







You can define concentrated heat capacitance at a point on a part or on an assembly. For more information, see ["Point capacitance," Section 30.4.1 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-elm-ecapacitance).

**To define heat capacitance:**

1. From the main menu bar in the Property module or the Interaction module, select ****Special**![](../graphics/images/arrow.gif)**Inertia**![](../graphics/images/arrow.gif)**Create****.
2. In the **Create Inertia** dialog box that appears, name the inertia, select **Heat capacitance**, and click **Continue**.
3. Select the points for which you want to define heat capacitance using one of the following methods: - Select the points in the viewport. When you have finished selecting, click mouse button 2. If the model contains a combination of orphan mesh elements and geometry, select one of the following from the prompt area: - Select **Geometry** to define heat capacitance for the geometric portions of a part or assembly or for a reference point. - Select **Mesh** to define heat capacitance for orphan mesh components. You can use the angle method to select a group of nodes from an orphan mesh. For more information, see ["Using the angle and feature edge method to select multiple objects," Section 6.2.3](pt01ch06s02hlb03.md). - To select from a list of existing sets, do the following: 1. Click **Sets** on the right side of the prompt area to display the **Region Selection** dialog box containing a list of available sets. 2. Select the set of interest, and click **Continue**. **Note:**The default selection method is based on the selection method you most recently employed. To revert to the other method, click **Select in Viewport** or **Sets** on the right side of the prompt area. The **Edit Inertia** dialog box appears. The region to which you are applying the heat capacitance is highlighted in the viewport.
4. If desired, toggle on **Use temperature-dependent data** and enter the temperature.
5. If desired, specify the **Number of field variables** and enter the value for the first field variable, the value of the second field variable, etc.
6. In the **Data** table, enter the following: **Capacitance** Enter the capacitance magnitude, ![](../graphics/usi_eqn00716.gif) (density specific heat volume).
7. Click **OK** to save your data and to close the dialog box. Symbols appear in the viewport that represent the heat capacitance that you just created.

![](../graphics/images/black4rule.gif)For information on related topics, click any of the following items:- ["Controlling the display of attributes," Section 76.15](pt07ch76hla14.md)
- ["Symbols used to represent special engineering features," Section C.3](ap03s03.md)




