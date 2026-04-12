# 12.1 Writing results from an Abaqus analysis to a SIM database







**Products: **Abaqus/Standard  Abaqus/Explicit  Abaqus/CFD  Abaqus/CAE  

**Benefits: **You can now write results to a SIM database (`.sim`) file, which allows you to import the results of an Abaqus analysis into the Physics Results Explorer app on the 3DEXPERIENCE Platform for high-performance postprocessing.

**Description: **The new SIM database (`*job-name*.sim`) is the file format used to exchange bulky FEA data between 3DEXPERIENCE Platform apps and computationally intensive components like implicit and explicit solvers. For example, the Physics Results Explorer app uses the SIM database for high-performance postprocessing of analysis results.

The Abaqus output database is now available in two formats, ODB and SIM. By default, the results output is created in ODB format. Only results in SIM format can be imported into the 3DEXPERIENCE Platform for high-performance postprocessing. For Abaqus/Standard and Abaqus/Explicit analyses the new **resultsformat** command line option provides control over the output format for Abaqus results, including writing results in both formats. For Abaqus/CFD analyses you use the **field** and **history** command line options to write results in SIM format.

Your choice of output format depends on your level of experience with high-performance visualization, the Physics Results Explorer app, and your postprocessing needs.
- If you are still learning to use high-performance visualization and you want to compare your results with Abaqus/Viewer, write results in both formats.
- If the model is large and you need the improved performance of the Physics Results Explorer app, as well as the capabilities of Abaqus/Viewer, write results in both formats.
- If you are confident that the high-performance visualization features in the Physics Results Explorer app provide all the capabilities you need, write results in SIM format.

A subset of options in Abaqus/Standard and Abaqus/Explicit are not supported for analyses that produce results in SIM format; Abaqus/CFD has no restrictions on output in SIM format. If you include one or more of these options or parameters in your analysis and write results in SIM format or both formats, the analysis will either terminate with errors or produce limited results. For more information, see ["Limitations when writing results in SIM format" in "Output," Section 4.1.1](../usb/usb-link.md#usb-out-ooutput-sim-limitations) of the [Abaqus Analysis User's Guide](../usb/usb-link.md#usb).

**Abaqus/CAE Usage: **
```
Job module:
    ****Job**![](../graphics/images/arrow.gif)**Edit****: **General** tabbed page: **Results Format**: **ODB**, **SIM**, or **Both** (Abaqus/Standard 
    and Abaqus/Explicit only)
```

**References: **

**Abaqus Analysis User's Guide**
- ["Abaqus/Standard, Abaqus/Explicit, and Abaqus/CFD execution," Section 3.2.2](../usb/usb-link.md#usb-int-danalysisproc)
- ["Output," Section 4.1.1](../usb/usb-link.md#usb-out-ooutput)

**Abaqus/CAE User's Guide**
- ["The job editor," Section 19.2.4](../usi/usi-link.md#usi-ana-conc-unjobset)




