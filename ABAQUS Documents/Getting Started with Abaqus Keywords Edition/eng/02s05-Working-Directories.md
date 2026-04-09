# 2.5 Summary

![](../images/blu4rule.gif)

- The Abaqus input file contains a complete description of the analysis model. It is the means of communication between the preprocessor (Abaqus/CAE, for example) and the analysis product (Abaqus/Standard or Abaqus/Explicit).
- The input file contains two sections: the model data defining the structure being analyzed and the history data defining what happens to the structure.
- Each section of the input file comprises a number of option blocks, each consisting of a keyword line, which may be followed by data lines.
- You can perform a **datacheck** analysis once you have created the input file. Error and warning messages are printed to the data file. After a successful **datacheck** analysis, estimates of the computer resources required for the simulation are printed to the data file.
- Use Abaqus/Viewer to verify the model geometry and boundary conditions graphically, using the output database file generated during the **datacheck** phase.
- It is often easiest to check for mistakes in material properties in the data (`.dat`) file; geometry, loads, and boundary conditions are more easily checked with a graphical postprocessor such as Abaqus/Viewer.
- Always check that the results satisfy basic engineering principles, such as equilibrium.
- Abaqus/Viewer allows you to visualize analysis results graphically in a variety of ways and also allows you to write tabular data reports.
- The choice between using implicit or explicit methods depends largely on the nature of the problem.
