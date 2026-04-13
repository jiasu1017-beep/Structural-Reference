# 54.5 Controlling report layout, width, format, and coordinate system







For tabular reports of *X–Y* data, field output, or probe values you can limit the width of the table; for example, to the number of characters your printer can support.

An *X–Y* data report can include one or multiple *X–Y* data objects. Similarly, a field output report can include one or multiple variables. For both types of reports, if you include multiple items, you can choose to present each item in its own table or to combine items into a single table. If you combine multiple items into a single table, additional columns of data are formed and the width of the table increases.

To combine *X–Y* data objects into a single table, Abaqus/CAE aligns the *X*-values of the data objects. If any data objects do not have matching *X*-values, you can choose to have Abaqus/CAE compute the missing points by interpolation and extrapolation. To learn more about interpolation and extrapolation, see ["Understanding X--Y data interpolation and extrapolation," Section 47.4.2](pt05ch47s03s02.md).

For field output reports Abaqus/CAE creates a separate table (of a single variable or of combined variables, according to your specification) for every region in the current display group. A region is a portion of your model that has compatible materials, section properties, and element types. Abaqus/CAE identifies the region associated with each table in the report. (For more information on display groups, see [Chapter 78, "Using display groups to display subsets of your model](pt07ch78.md)”; for more information on regions, see ["Understanding result value averaging," Section 42.6.2](pt05ch42s04s02.md).) 

For free body cuts Abaqus/CAE enables you to generate report output in either normal annotated format or in comma-separated value (CSV) format. In normal annotated format, results are presented so that they can be read easily; in CSV format, results are intended to be exported and read in spreadsheet applications. You can also report data from free body cuts in the global coordinate system or in the local coordinate systems for which they were defined. 

**To control report layout, width, format, and coordinate system:**

1. Locate the **Output Format** options. **For a report of X--Y data or field output:** From the main menu bar, select ****Report**![](../graphics/images/arrow.gif)**XY**** or ****Report**![](../graphics/images/arrow.gif)**Field Output****; then click the **Setup** tab in the dialog box that appears. The **Output Format** options are in the center of the page. **For a report of free body cuts:** From the main menu bar, select ****Report**![](../graphics/images/arrow.gif)**Free Body Cut****. The **Output Format** options are in the center of the page. **For a report of probe values:** From the main menu bar, select ****Tools**![](../graphics/images/arrow.gif)**Query****, then click **Probe values** in the dialog box that appears. The **Probe Values** dialog box appears. Move the cursor to probe the model or *X--Y* plot in the current viewport, then click mouse button 1 to store values of interest in the dialog box. When you are finished, click **Write to File**. The **Report Probe Values** dialog box appears; the **Output Format** options are in the center of the dialog.
2. For *X--Y* data reports or field output reports, select the **Layout** option of your choice: - Select **Single table for all *X--Y* data** (or **Single table for all field output variables**) to combine all of the selected data objects into a single table. For *X--Y* data reports, toggle **Interpolate between X values (if necessary)** on if you want Abaqus to compute missing points. When this option is toggled off, missing points (if any) appear as "No Value" in the table. - Select **Separate table for each *X--Y* data** (or **Separate table for each field output variable**) if you want each of the selected data objects to appear in its own table.
3. For *X--Y* data reports or field output reports, select the **Page width (characters)** option of your choice: - Select **No limit** to allow an unlimited table width. - Select **Specify** to limit the table's width. Then, in the **Specify** text field, enter the maximum number of characters that can appear along the width of the table.
4. For free body cut reports, perform the following: - Select either **Normal annotated format** or **Comma-separated values (CSV)** as the report format. - Select either **Global CSYS** or **Local CSYS** as the coordinate system for the free body cuts.

To generate your report, configure the remaining options in the dialog box; then click **Apply** (for *X–Y*, field output, or free body cut reports) or **OK** (for probe values reports). When you have finished, click **Cancel** to close the dialog box.
![](../graphics/images/black4rule.gif)For information on related topics, click any of the following items:- ["Overview of tabular report options," Section 54.2](pt05ch54s02.md)
- ["Formatting report values," Section 54.7](pt05ch54hla04.md)
- ["Understanding X--Y data interpolation and extrapolation," Section 47.4.2](pt05ch47s03s02.md)




