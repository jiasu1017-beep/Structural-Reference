# 44.4 Producing a contour plot of linear beam section stresses







If your model includes beam geometry and beam rendering is enabled for your session, you can display field output results along the beam cross-sections as contours. For nodal quantities and element integration point quantities, Abaqus/CAE displays contours that are constant through the thickness of the beam cross-section. For the element-based data, the contour reflects the currently selected section point. 

You can also create a contour plot that shows a more realistic stress distribution through the beam based on section force and section moment data, which Abaqus/CAE calculates using linear elastic solid mechanics theory. [Figure 44--3](pt05ch44hla03.md#usv-con-produce-beam-figure) shows an example of beam stresses through an I-beam. 

**Figure 44–3** Linear beam section stresses displayed for an I-beam cross-section. 

![](../graphics/rnb611-out-beamstress.png)

Beam stress contour plots are available only when the selected step and frame include data from the integrated output quantities SF (section force) and SM (section moment). Furthermore, these plots are available only for a subset of profiles in Abaqus/CAE:
- Thin-walled box profiles
- Thin-walled pipe profiles
- Circular profiles
- Rectangular profiles
- I-shaped profiles
- L-shaped profiles
- T-shaped profiles

Contour plot display is unavailable for beam geometry in your model that uses any other profile or for tapered beam geometry. 

Abaqus/CAE does not include beam element normals for eigenfrequency extraction in its calculations for beam cross section rendering, so you cannot visualize the torsional and out-of-plane modes for the beam elements in these plots. However, the torsional modes are calculated for the beam elements because the beam elements have torsional stiffness; this information is available in the data (`.dat`) file.

**To produce a contour plot of linear beam section stresses:**

1. Use the **File** menu to [open the output database](pt02ch09s06hlb02.md) containing your analysis results.
2. Use the **Result** menu to select the following: 1. The [step and frame](pt05ch42s01hlb01.md) to display. 2. The [primary field](pt05ch42s03hlb03.md) output variable to display. 3. The [deformed field](pt05ch42s03hlb04.md) output variable to display (for contours on the deformed shape only). 4. The [quantity to plot](pt05ch42s04hlb01.md) and [averaging](pt05ch42s04s02.md) options.
3. Select the plot state--independent and contour plot [customization options](pt05ch40s03s03.md) that you want.
4. From the **Output Variable** options, select **BEAM_STRESS**.
5. Choose the invariant or component for which you want to display contour data: - Select **Mises** from the **Invariant** options to display von Mises stress. - Select **S11** from the **Component** options to display axial stress along the beam. - Select **S12** from the **Component** options to display shear stress along the local beam section 2-axis caused by shear force and torsion. - Select **S13** from the **Component** options to display shear stress along the local beam section 1-axis caused by shear force and torsion.
6. From the main menu bar, select ****Plot**![](../graphics/images/arrow.gif)**Contours**** and choose whether to plot the contours on the undeformed shape, the deformed shape, or both. **Tip:**You can also produce a contour plot using the deformed ![](../graphics/ico_plotContourDeformed.png), undeformed ![](../graphics/ico_plotContourUndeformed.png), or superimposed ![](../graphics/ico_plotContourDefUndef.png) contour tools in the toolbox. The current viewport displays a customized contour plot of the specified field output variable at the specified step and frame of the current output database. Abaqus automatically refreshes your contour plot each time you click **Apply** in the step and frame selector, field output options, plot state--independent options, superimpose plot options (if applicable), or contour plot options dialog boxes.

![](../graphics/images/black4rule.gif)For information on related topics, click any of the following items:- ["Overview of contour plot options," Section 44.2](pt05ch44hla01.md)
- [Chapter 42, "Selecting model data and analysis results to plot](pt05ch42.md)"
- ["Producing a contour plot of linear beam section stresses," Section 44.4](pt05ch44hla03.md)




