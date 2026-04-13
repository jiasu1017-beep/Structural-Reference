# 47.3 Producing an X–Y plot







### 47.3 Producing an X--Y plot

To produce an *X–Y* plot, you first specify an *X–Y* data object. You can then choose to simply plot the specified *X–Y* data object or to save the data object and plot it later. 

History and field data objects can include complex numbers; you can control the displayed form of complex numbers using the **Result Options** dialog box. An abbreviation of the complex form is appended to the *Y*-axis title when you plot the variable and becomes part of the saved variable name. For example, if `S-Mises` is the selected field output variable and `Magnitude` is the complex form, the *Y*-axis title is `S-Mises CPX: Mg`. For more information on complex number forms in Abaqus/CAE, see ["Controlling the form of complex results," Section 42.6.9](pt05ch42s04hlb05.md).

Use one of the following methods to produce an *X–Y* plot:

**To produce an X–Y plot of history data from an output database:**

Select ****Tools**![](../graphics/images/arrow.gif)**XY Data**![](../graphics/images/arrow.gif)**Create**** from the main menu bar to launch the **Create XY Data** dialog box; then choose **ODB history output**. Click **Continue**. From the dialog box that appears, select one or more variables to plot and the step or steps of interest; then click **Plot**.

**Tip:**To launch the **Create XY Data** dialog box from the Results Tree, click mouse button 3 on the **XYData** container and select **Create** from the list that appears.

You can also specify history output by selecting ****Result**![](../graphics/images/arrow.gif)**History Output**** from the main menu bar.

**To produce an X–Y plot of field data from an output database:**

Select ****Tools**![](../graphics/images/arrow.gif)**XY Data**![](../graphics/images/arrow.gif)**Create**** from the main menu bar; then choose **ODB field output**. Click **Continue**. From the dialog box that appears, select one or more variables to plot, the location or locations from which to read the data, and the step or steps of interest; then click **Plot**.

**To produce an X–Y plot of output database results along a path through your model:**

To specify a path through your model, select ****Tools**![](../graphics/images/arrow.gif)**Path**![](../graphics/images/arrow.gif)**Create**** from the main menu bar; then configure the dialog boxes that appear. For more information, see ["Creating a path through your model," Section 48.2](pt05ch48s02.md).

After you have created the path, select ****Tools**![](../graphics/images/arrow.gif)**XY Data**![](../graphics/images/arrow.gif)**Create**** from the main menu bar. Choose **Path** as the source of the *X–Y* data object, then click **Continue**. Configure the dialog box that appears, then click **Plot**. For more information, see ["Obtaining X--Y data along a path," Section 48.3](pt05ch48s03.md). 

**To produce an X–Y plot of new data, not from an output database:**

Select ****Tools**![](../graphics/images/arrow.gif)**XY Data**![](../graphics/images/arrow.gif)**Create**** from the main menu bar. Choose either **Operate on XY data**, **ASCII file**, or **Keyboard** as the source of the *X–Y* data object; then click **Continue**. In the dialog box that appears, enter your *X–Y* data object; then click **Plot** (or **Plot Expression** in the **Operate on XY Data** dialog box).

**To produce an X–Y plot of one or more saved X–Y data objects:**

- To display a single *X--Y* data object, select ****Tools**![](../graphics/images/arrow.gif)**XY Data**![](../graphics/images/arrow.gif)**Plot**** from the main menu bar; and select the *X--Y* data object from the pull-right menu.
- To display multiple *X--Y* data objects on a single *X--Y* plot, select ****Tools**![](../graphics/images/arrow.gif)**XY Data**![](../graphics/images/arrow.gif)**Manager**** from the main menu bar. Select the *X--Y* data objects from the dialog box that appears; then click **Plot**.

You can also perform either of these actions from the Results Tree. To display a single *X–Y* data object using the Results Tree, expand the **XYData** container, click mouse button 3 on the *X–Y* data object you want to plot, and select **Plot** from the list that appears. To display multiple *X–Y* data objects using the Results Tree, highlight multiple *X–Y* objects under the **XYData** container, click mouse button 3 on one of the highlighted objects, and select **Plot** from the list that appears.

![](../graphics/images/black4rule.gif)For information on related topics, click any of the following items:- ["Understanding how to specify an X--Y data object," Section 47.1.2](pt05ch47s01s02.md)
- ["Understanding "Temp" and other X--Y data object names," Section 47.1.3](pt05ch47s01s03.md)
- ["Controlling the form of complex results," Section 42.6.9](pt05ch42s04hlb05.md)




