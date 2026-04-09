# 5.8 Summary

---

- The cross-section behavior of shell elements can be determined using numerical integration through the shell thickness (`*SHELL SECTION`) or using a cross-section stiffness calculated at the beginning of the analysis (`*SHELL GENERAL SECTION`).
- `*SHELL GENERAL SECTION` is efficient, but it can be used only with linear materials. `*SHELL SECTION` can be used with both linear and nonlinear materials.
- Numerical integration is performed at a number of section points through the shell thickness. These section points are the locations at which element variables can be output. The default outermost section points lie on the surfaces of the shell.
- The direction of a shell element's normal determines the positive and negative surfaces of the element. To define contact and interpret element output correctly, you must know which surface is which. The shell normal also defines the direction of positive pressure loads applied to the element and can be plotted in Abaqus/Viewer.
- Shell elements use material directions local to each element. In large-displacement analyses the local material axes rotate with the element. `*ORIENTATION` can be used to define non-default local coordinate systems. The element variables, such as stress and strain, are output in the local directions.
- `*TRANSFORM` defines local coordinate systems for nodes. Concentrated loads and boundary conditions are applied in the local coordinate system. All printed nodal output, such as displacements, also refer to the local system by default.
- Symbol plots can help you visualize the results from a simulation. They are especially useful for visualizing the motion and load paths of a structure.
