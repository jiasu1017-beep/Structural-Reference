# 76.16 Saving your display options settings







If you change your display options settings (for example, if you change the render style or turn off the display of datum planes), you can store the new settings for future sessions. Abaqus/CAE saves your settings in a file called `abaqus_v6.14.gpr`. For more information, see ["Working with `abaqus_v6.14.gpr` files," Section 2.1.3](pt01ch02s01s03.md).

From the main menu bar, select ****File**![](../graphics/images/arrow.gif)**Save Display Options**** to save all the current display options settings. The **Save Display Options** dialog box appears and allows you to save the options in the current directory or in your home directory.

You can edit the `abaqus_v6.14.gpr` file using API commands in the Abaqus Scripting Interface; for more information, see ["Editing display preferences and GUI settings," Section 8.4 of the Abaqus Scripting User's Guide](../cmd/cmd-link.md#cmd-int-exa-caeprefsaccess). You can also delete the file to restore the default GUI and display options settings, and you can copy the file to other directories on your computer or transfer the file to a different computer. When you save your settings from `abaqus_v6.14.gpr`, Abaqus/CAE always saves all of the current settings and always overwrites all the settings that were previously saved. You cannot save only selected settings. You can use the **noSavedOptions** command line option to start Abaqus/CAE without loading the settings in `abaqus_v6.14.gpr`. For more information, see ["Starting Abaqus/CAE (or Abaqus/Viewer)," Section 2.1.1](pt01ch02s01s01.md).

Abaqus/CAE saves the following display options settings in `abaqus_v6.14.gpr`:
- Part and assembly display options; for example, render style, the visibility of prescribed conditions and the various types of datum geometry, and the display of mesh, element, and node labels.
- Graphics options and viewport annotation options. Abaqus/CAE also saves the perspective setting.
- Print options.
- Display options in the Visualization module; for example, the contour type for contour plots and the render style and fill color in the common plot options.
- Animation options in the Visualization module.
- Other options in the Visualization module, such as probe, field report, *X--Y* plot, and *X--Y* report options.




