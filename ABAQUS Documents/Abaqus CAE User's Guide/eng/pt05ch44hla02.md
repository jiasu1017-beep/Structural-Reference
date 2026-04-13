# 44.3 Producing a contour plot







A contour plot can display either the values of an analysis variable at a specified step and frame of an output database or the values of selected attributes at a specified step of a model in the current model database. Abaqus/CAE represents the values as customized colored lines, colored bands, colored faces, or colored isosurfaces on your model or as colored tick marks on lines drawn normal to your model. For more information on selecting an analysis variable, see ["Selecting the primary field output variable," Section 42.5.3](pt05ch42s03hlb03.md). For more information on selecting a specific step and frame, see ["Selecting a specific results step and frame," Section 42.3.1](pt05ch42s01hlb01.md). To learn how to display the minimum and maximum values associated with your contour plot, see ["Customizing the legend," Section 56.1](pt05ch56s01.md).

If your model includes beam elements, some additional steps can be required for proper contour display. See ["Producing a contour plot of linear beam section stresses," Section 44.4](pt05ch44hla03.md).

If you are plotting data from a model database, specify only the primary field variable. 

**To produce a contour plot:**

1. Use the **File** menu to [open the model database or output database](pt02ch09s06hlb02.md) containing your model data or analysis results.
2. If you are plotting data from a model database, switch to the Visualization module, expand the **Model Database** container of the Results Tree, and select the model you want to use.
3. Use the **Result** menu to select the following: 1. The [step and frame](pt05ch42s01hlb01.md) to display (or just the step, if a model database is selected). 2. The [primary field](pt05ch42s03hlb03.md) output variable to display. 3. The [deformed field](pt05ch42s03hlb04.md) output variable to display (for contours on the deformed shape only). 4. The [quantity to plot](pt05ch42s04hlb01.md) and [averaging](pt05ch42s04s02.md) options (for output databases only).
4. Select the plot state--independent and contour plot [customization options](pt05ch40s03s03.md) that you want.
5. If your chosen field output variable includes complex numbers, select the [**Complex Form**](pt05ch42s04hlb05.md) tab in the **Result Options** dialog box to control the numeric form to display. Complex form options apply only to output databases.
6. From the main menu bar, select ****Plot**![](../graphics/images/arrow.gif)**Contours**** and choose whether to plot the contours on the undeformed shape, the deformed shape, or both. **Tip:**You can also produce a contour plot using the deformed ![](../graphics/ico_plotContourDeformed.png), undeformed ![](../graphics/ico_plotContourUndeformed.png), or superimposed ![](../graphics/ico_plotContourDefUndef.png) contour tools in the toolbox. The current viewport displays a customized contour plot of the specified field output variable at the specified step and frame of the current output database or at the specified step of the selected model in the current model database. Abaqus automatically refreshes your contour plot each time you click **Apply** in the step and frame selector, field output options, plot state--independent options, superimpose plot options (if applicable), or contour plot options dialog boxes.

![](../graphics/images/black4rule.gif)For information on related topics, click any of the following items:- ["Overview of contour plot options," Section 44.2](pt05ch44hla01.md)
- [Chapter 42, "Selecting model data and analysis results to plot](pt05ch42.md)"




