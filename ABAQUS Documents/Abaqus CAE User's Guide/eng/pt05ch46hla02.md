# 46.3 Producing a material orientation plot







A material orientation plot shows the material directions of the elements in a model at a specified step and frame and a specified section point. Abaqus/CAE represents the material orientations as triads at the element integration points. For more information on selecting the results step, see ["Selecting a specific results step and frame," Section 42.3.1](pt05ch42s01hlb01.md). For more information on selecting section point locations, see ["Selecting section point data by category" in "Selecting section point data," Section 42.5.9](pt05ch42s03s01.md#usv-res-visvariableshelldb).

**To produce a material orientation plot:**

1. [Open the output database](pt02ch09s06hlb02.md) containing your analysis results.
2. Select the results [step and frame](pt05ch42s01hlb01.md) to display.
3. Select the [section point](pt05ch54s03hlb03.md) to display.
4. Select the plot state--independent and material orientation plot [customization](pt05ch40s03s03.md) options you want.
5. From the main menu bar, select ****Plot**![](../graphics/images/arrow.gif)**Material Orientations**** and choose whether to plot the material orientations on the undeformed shape, the deformed shape, or both. **Tip:**You can also produce a material orientation plot using the deformed ![](../graphics/ico_plotMatOrientDeformed.png), undeformed ![](../graphics/ico_plotMatOrientUndeformed.png), or superimposed ![](../graphics/ico_plotMatOrientDefUndef.png) material orientation tools in the toolbox. The current viewport changes to display a customized material orientation plot. Abaqus automatically refreshes your material orientation plot each time you click **Apply** in the step and frame selector, section point selector, plot state--independent options, superimpose plot options (if applicable), or material orientation plot options dialog boxes.

![](../graphics/images/black4rule.gif)For information on related topics, click the following item: - ["Overview of material orientation plot options," Section 46.2](pt05ch46hla01.md)




