# 54.4 Specifying your report file name







Abaqus/CAE writes your tabular data report to the file name of your choice. If you choose to write your report to an existing file, you can further specify whether the new information should be appended to the current file contents or whether the file should be overwritten. The default is to append the new information.

**To specify your report file name:**

1. Locate the **File** options. **For a report of X--Y data or field output:** From the main menu bar, select ****Report**![](../graphics/images/arrow.gif)**XY**** or ****Report**![](../graphics/images/arrow.gif)**Field Output****; then click the **Setup** tab in the dialog box that appears. The **File** options are at the top of the page. **For a report of free body cuts:** From the main menu bar, select ****Report**![](../graphics/images/arrow.gif)**Free Body Cut****. The **File** options are at the top of the page. **For a report of probe values:** From the main menu bar, select ****Tools**![](../graphics/images/arrow.gif)**Query****, then click **Probe values** in the dialog box that appears. The **Probe Values** dialog box appears. Move the cursor to probe the model or *X--Y* plot in the current viewport, then click mouse button 1 to store values of interest in the dialog box. When you are finished, click **Write to File**. The **Report Probe Values** dialog box appears; the **File** options are at the top of the dialog.
2. To select a file name using the standard file browser, click **Select**. The **File Selection** dialog box appears. Use the dialog to filter and browse existing files. For more information on using this dialog box, see ["Using file selection dialog boxes," Section 3.2.10](pt01ch03s02s10.md). When you are finished, click **OK** to close the dialog box.
3. Type into the **Name** field the name of the file to which your report is to be written.
4. Toggle **Append to file** to append this report to the current contents (if any) of the file you have specified. When **Append to file** is off, existing file contents will be overwritten.

To generate your report, configure the remaining options in the dialog box; then click **Apply** (for *X–Y*, field output, or free body cuts) or **OK** (for probe values reports). When you have finished, click **Cancel** to close the dialog box.
![](../graphics/images/black4rule.gif)For information on related topics, click the following item: - ["Overview of tabular report options," Section 54.2](pt05ch54s02.md)




