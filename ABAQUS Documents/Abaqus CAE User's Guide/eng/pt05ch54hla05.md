# 54.8 Reporting data values, minimums, maximums, and totals







For tabular reports of *X–Y* data or field output, you can include or suppress *X–Y* data or field output values, column minimum and maximum value summaries, and column totals. By default, Abaqus/CAE includes only the actual data values in reports of *X–Y* data. In reports of field output values, Abaqus/CAE includes by default the data values as well as column summaries and totals.

For tabular reports of probe values, Abaqus/CAE always includes the actual data values in the report. You can include or suppress column minimum and maximum value summaries and column totals for any columns in which such values would be meaningful.

**To report data values, minimums, maximums, and column totals:**

1. Locate the **Data** or **Data Values** options. **For a report of X--Y data or field output:** From the main menu bar, select ****Report**![](../graphics/images/arrow.gif)**XY**** or ****Report**![](../graphics/images/arrow.gif)**Field Output****; then click the **Setup** tab in the dialog box that appears. The **Data** options are at the bottom of the page. **For a report of probe values:** From the main menu bar, select ****Tools**![](../graphics/images/arrow.gif)**Query****, then click **Probe values** in the dialog box that appears. The **Probe Values** dialog box appears. Move the cursor to probe the model or *X--Y* plot in the current viewport, then click mouse button 1 to store values of interest in the dialog box. When you are finished, click **Write to File**. The **Report Probe Values** dialog box appears; the **Data Values** options are at the bottom of the dialog box.
2. For *X--Y* data reports or field output reports, you must choose one or more of the following items to include in your report: - Toggle **XY data** or **Field output** to include the actual *X--Y* data or field output values, respectively. Toggling this option off results in a report that consists of only the column total or min/max data you request. - Toggle **Column totals** to include totals for each column. - Toggle **Column min/max** to include a summary of the minimum and maximum value occurring in each column.

To generate your report, configure the remaining options in the dialog box; then click **Apply** (for *X–Y* reports or field output reports) or **OK** (for probe values reports). When you have finished, click **Cancel** to close the dialog box.
![](../graphics/images/black4rule.gif)For information on related topics, click the following item: - ["Overview of tabular report options," Section 54.2](pt05ch54s02.md)




