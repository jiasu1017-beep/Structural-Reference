# 5.&nbsp;Using Shell Elements

*Use shell elements to model structures in which one dimension (the thickness) is significantly smaller than the other dimensions and in which the stresses in the thickness direction are negligible. A structure, such as a pressure vessel, whose thickness is less than 1/10 of a typical global structural dimension generally can be modeled with shell elements. The following are examples of typical global dimensions:the distance between supports,the distance between stiffeners or large changes in section thickness,the radius of curvature, andthe wavelength of the highest vibration mode of interest.Abaqus shell elements assume that plane sections perpendicular to the shell midsurface remain plane. Do not be confused into thinking that the thickness must be less than 1/10 of the element dimensions. A highly refined mesh may contain shell elements whose thickness is greater than their in-plane dimensions, although this is not generally recommended&#8212;continuum elements may be more suitable in such a case.*

5.&nbsp;Using Shell Elements
Use shell elements to model structures in which one dimension (the thickness) is significantly smaller than the other dimensions and in which the stresses in the thickness direction are negligible. A structure, such as a pressure vessel, whose thickness is less than 1/10 of a typical global structural dimension generally can be modeled with shell elements. The following are examples of typical global dimensions:
-
the distance between supports,
-
the distance between stiffeners or large changes in section thickness,
-
the radius of curvature, and
-
the wavelength of the highest vibration mode of interest.
Abaqus shell elements assume that plane sections perpendicular to the shell midsurface remain plane. Do not be confused into thinking that the thickness must be less than 1/10 of the *element* dimensions. A highly refined mesh may contain shell elements whose thickness is greater than their in-plane dimensions, although this is not generally recommended&#8212;continuum elements may be more suitable in such a case.

## 5.1&nbsp;Element geometry

*Two types of shell elements are available in Abaqus: conventional shell elements and continuum shell elements. Conventional shell elements discretize a reference surface by defining the element's planar dimensions, its surface normal, and its initial curvature. The nodes of a conventional shell element, however, do not define the shell thickness; the thickness is defined through section properties. Continuum shell elements, on the other hand, resemble three-dimensional solid elements in that they discretize an entire three-dimensional body yet are formulated so that their kinematic and constitutive behavior is similar to conventional shell elements. Continuum shell elements are more accurate in contact modeling than conventional shell elements, since they employ two-sided contact taking into account changes in thickness. For thin shell applications, however, conventional shell elements provide superior performance.In this guide only conventional shell elements are discussed. Henceforth, we will refer to them simply as &#8220;shell elements.&#8221; For more information on continuum shell elements, see &#8220;*

5.1&nbsp;Element geometry
Two types of shell elements are available in Abaqus: conventional shell elements and continuum shell elements. Conventional shell elements discretize a reference surface by defining the element's planar dimensions, its surface normal, and its initial curvature. The nodes of a conventional shell element, however, do not define the shell thickness; the thickness is defined through section properties. Continuum shell elements, on the other hand, resemble three-dimensional solid elements in that they discretize an entire three-dimensional body yet are formulated so that their kinematic and constitutive behavior is similar to conventional shell elements. Continuum shell elements are more accurate in contact modeling than conventional shell elements, since they employ two-sided contact taking into account changes in thickness. For thin shell applications, however, conventional shell elements provide superior performance.
In this guide only conventional shell elements are discussed. Henceforth, we will refer to them simply as &#8220;shell elements.&#8221; For more information on continuum shell elements, see &#8220;Shell elements: overview,&#8221;  Section 29.6.1 of the Abaqus Analysis User's Guide.5.1.1&nbsp;Shell thickness and section points
The shell thickness is required to describe the shell cross-section and must be specified. In addition to specifying the shell thickness, you can choose to have the stiffness of the cross-section calculated during the analysis or once at the beginning of the analysis.
If you choose to have the stiffness calculated during the analysis, Abaqus uses numerical integration to calculate the stresses and strains independently at each section point (integration point) through the thickness of the shell, thus allowing nonlinear material behavior. For example, an elastic-plastic shell may yield at the outer section points while remaining elastic at the inner section points. The location of the single integration point in an S4R (4-node, reduced integration) element and the configuration of the section points through the shell thickness are shown in [Figure 5&#8211;1](ch05s01.html#gss-integrated-shell).
**Figure 5&#8211;1** Configuration of section points in a numerically integrated shell.
../graphics/gss-integrated-shell-nls.png
You can specify any odd number of section points through the shell thickness when the properties are integrated during the analysis. By default, Abaqus uses five section points through the thickness of a homogeneous shell, which is sufficient for most nonlinear design problems. However, you should use more section points in some complicated simulations, especially when you anticipate reversed plastic bending (nine is normally sufficient in this case). For linear problems three section points provide exact integration through the thickness. However, calculating the material stiffness once at the beginning of the analysis is more efficient for linear elastic shells.
The material behavior must be linear elastic when the stiffness of the cross-section is calculated only at the beginning of the simulation. In this case all calculations are done in terms of the resultant forces and moments across the entire cross-section. If you request stress or strain output, Abaqus provides default output for the bottom surface, the midplane, and the top surface.5.1.2&nbsp;Shell normals and shell surfaces
The connectivity of the shell element defines the direction of the positive normal, as shown in [Figure 5&#8211;2](ch05s01.html#gss-posi-normals).
**Figure 5&#8211;2** Positive normals for shells.
../graphics/gss-posi-normals-nls.png
For axisymmetric shell elements the positive normal direction is defined by a 90 counterclockwise rotation from the direction going from node 1 to node 2. For three-dimensional shell elements the positive normal is given by the right-hand rule going around the nodes in the order in which they appear in the element definition.
The &#8220;top&#8221; surface of a shell is the surface in the positive normal direction and is called the SPOS face for contact definition. The &#8220;bottom&#8221; surface is in the negative direction along the normal and is called the SNEG face for contact definition. Normals should be consistent among adjoining shell elements.
The positive normal direction defines the convention for element-based pressure load application and output of quantities that vary through the shell thickness. A positive element-based pressure load applied to a shell element produces a load that acts in the direction of the positive normal. (The element-based pressure load convention for shell elements is opposite to that for continuum elements; the surface-based pressure load conventions for shell and continuum elements are identical. For more on the difference between element-based and surface-based distributed loads, see &#8220;Distributed loads,&#8221;  Section 34.4.3 of the Abaqus Analysis User's Guide.)5.1.3&nbsp;Initial shell curvature
Shells in Abaqus (with the exception of element types S3/S3R, S3RS, S4R, S4RS, S4RSW, and STRI3) are formulated as true curved shell elements; true curved shell elements require special attention to accurate calculation of the initial surface curvature. Abaqus automatically calculates the surface normals at the nodes of every shell element to estimate the initial curvature of the shell. The surface normal at each node is determined using a fairly elaborate algorithm, which is discussed in detail in &#8220;Defining the initial geometry of conventional shell elements,&#8221;  Section 29.6.3 of the Abaqus Analysis User's Guide.
With a coarse mesh as shown in [Figure 5&#8211;3](ch05s01.html#gss-refine), Abaqus may determine several independent surface normals at the same node for adjoining elements. Physically, multiple normals at a single node mean that there is a fold line between the elements sharing the node. While it is possible that you intend to model such a structure, it is more likely that you intend to model a smoothly curved shell; Abaqus will try to smooth the shell by creating an averaged normal at a node.
**Figure 5&#8211;3** Effect of mesh refinement on the nodal surface normals.
../graphics/gss-refine-nls.png
The basic smoothing algorithm used is as follows: if the normals at a node for each shell element attached to the node are within 20 of each other, the normals will be averaged. The averaged normal will be used at that node for all elements attached to the node. If Abaqus cannot smooth the shell, a warning message is issued in the data (`.dat`) file.
There are two methods that can be used to override the default algorithm. To introduce fold lines into a curved shell or to model a curved shell with a coarse mesh, either give the components of ../graphics/gsa_eqn00035.gif as the 4th, 5th, and 6th data values following the nodal coordinates (this method requires manually editing the input file created by Abaqus/CAE in a text editor); or specify the normal direction directly with the *NORMAL option (this option can be added using the Abaqus/CAE **Keywords Editor**; see [&#8220;Cross-section orientation,&#8221;  Section 6.1.2](ch06s01.html#gsa-bms-crosssectorient)). If both methods are used, the latter takes precedence. See &#8220;Defining the initial geometry of conventional shell elements,&#8221;  Section 29.6.3 of the Abaqus Analysis User's Guide, for further details.5.1.4&nbsp;Reference surface offsets
The reference surface of the shell is defined by the shell element's nodes and normal definitions. When modeling with shell elements, the reference surface is typically coincident with the shell's midsurface. However, many situations arise in which it is more convenient to define the reference surface as offset from the shell's midsurface. For example, surfaces created in CAD packages usually represent either the top or bottom surface of the shell body. In this case it may be easier to define the reference surface to be coincident with the CAD surface and, therefore, offset from the shell's midsurface.
Shell offsets can also be used to define a more precise surface geometry for contact problems where shell thickness is important. Another situation where the offset from the midsurface may be important is when a shell with continuously varying thickness is modeled. In this case defining the nodes at the shell midplane can be difficult. If one surface is smooth while the other is rough, as in some aircraft structures, it is easiest to use shell offsets to define the nodes at the smooth surface.
Offsets can be introduced by specifying an offset value, which is defined as the distance (measured as a fraction of the shell's thickness) from the shell's midsurface to the reference surface containing the element's nodes. Positive values of the offset are in the positive normal direction. When the offset is set equal to 0.5 or SPOS, the top surface of the shell is the reference surface. When the offset is set equal to &#8211;0.5 or SNEG, the bottom surface is the reference surface. The default offset is 0, which indicates that the middle surface of the shell is the reference surface. These three reference surface offset settings are shown in [Figure 5&#8211;4](ch05s01.html#gss-shelloffset) for a mesh where the nodal positions are adjusted to keep the position of the midsurface constant.
**Figure 5&#8211;4** Schematic of shell offsets for offset values of 0, &#8211;0.5, and +0.5.
../graphics/shelloffset-nls.png
The degrees of freedom for the shell are associated with the reference surface. The element's area and all kinematic quantities are calculated there. Large offset values for curved shells may lead to a surface integration error, affecting the stiffness, mass, and rotary inertia for the shell section. For stability purposes Abaqus/Explicit also automatically augments the rotary inertia used for shell elements on the order of the offset squared, which may result in errors in the dynamics for large offsets. When large offsets from the shell's midsurface are necessary, use multi-point constraints or rigid body constraints instead.

## 5.2&nbsp;Shell formulation &#8211; thick or thin

5.2&nbsp;Shell formulation &#8211; thick or thin
Shell problems generally fall into one of two categories: thin shell problems and thick shell problems. Thick shell problems assume that the effects of transverse shear deformation are important to the solution. Thin shell problems, on the other hand, assume that transverse shear deformation is small enough to be neglected. [Figure 5&#8211;5](ch05s02.html#gss-transhellsect-shell)(a) illustrates the transverse shear behavior of thin shells: material lines that are initially normal to the shell surface remain straight and normal throughout the deformation. Hence, transverse shear strains are assumed to vanish (../graphics/gsa_eqn00036.gif). [Figure 5&#8211;5](ch05s02.html#gss-transhellsect-shell)(b) illustrates the transverse shear behavior of thick shells: material lines that are initially normal to the shell surface do not necessarily remain normal to the surface throughout the deformation, thus adding transverse shear flexibility (../graphics/gsa_eqn00037.gif).
**Figure 5&#8211;5** Behavior of transverse shell sections in (a) thin shells and (b) thick shells.
../graphics/gss-transhellsect-nls.png
Abaqus offers multiple classes of shell elements, distinguished by the element's applicability to thin and thick shell problems. General-purpose shell elements are valid for use with both thick and thin shell problems. In certain cases, for specific applications, enhanced performance can be obtained by using the special-purpose shell elements available in Abaqus/Standard.
The special-purpose shell elements fall into two categories: thin-only shell elements and thick-only shell elements. All special-purpose shell elements provide for arbitrarily large rotations but only small strains. The thin-only shell elements enforce the Kirchhoff constraint; that is, plane sections normal to the midsection of the shell remain normal to the midsurface. The Kirchhoff constraint is enforced either analytically in the element formulation (STRI3) or numerically through the use of a penalty constraint. The thick-only shell elements are second-order quadrilaterals that may produce more accurate results than the general-purpose shell elements in small-strain applications where the loading is such that the solution is smoothly varying over the span of the shell.
To decide if a given application is a thin or thick shell problem, we can offer a few guidelines. For thick shells transverse shear flexibility is important, while for thin shells it is negligible. The significance of transverse shear in a shell can be estimated by its thickness-to-span ratio. A shell made of a single isotropic material with a ratio greater than 1/15 is considered &#8220;thick&#8221;; if the ratio is less than 1/15, the shell is considered &#8220;thin.&#8221; These estimates are approximate; you should always check the transverse shear effects in your model to verify the assumed shell behavior. Since transverse shear flexibility can be significant in laminated composite shell structures, this ratio should be much smaller for &#8220;thin&#8221; shell theory to apply. Composite shells with very compliant interior layers (so-called &#8220;sandwich&#8221; composites) have very low transverse shear stiffness and should almost always be modeled with &#8220;thick&#8221; shells; if the assumption of plane sections remaining plane is violated, continuum elements should be used. See &#8220;Shell section behavior,&#8221;  Section 29.6.4 of the Abaqus Analysis User's Guide, for details on checking the validity of using shell theory.
Transverse shear force and strain are available for general-purpose and thick-only shell elements. For three-dimensional elements, estimates of transverse shear stress are provided. The calculation of these stresses neglects coupling between bending and twisting deformation and assumes small spatial gradients of material properties and bending moments.

## 5.3&nbsp;Shell material directions

*Shell elements, unlike continuum elements, use material directions local to each element. Anisotropic material data, such as that for fiber-reinforced composites, and element output variables, such as stress and strain, are defined in terms of these local material directions. In large-displacement analyses the local material axes on a shell surface rotate with the average motion of the material at each integration point.*

5.3&nbsp;Shell material directions
Shell elements, unlike continuum elements, use material directions local to each element. Anisotropic material data, such as that for fiber-reinforced composites, and element output variables, such as stress and strain, are defined in terms of these local material directions. In large-displacement analyses the local material axes on a shell surface rotate with the average motion of the material at each integration point.5.3.1&nbsp;Default local material directions
The local material 1- and 2-directions lie in the plane of the shell. The default local 1-direction is the projection of the global 1-axis onto the shell surface. If the global 1-axis is normal to the shell surface, the local 1-direction is the projection of the global 3-axis onto the shell surface. The local 2-direction is perpendicular to the local 1-direction in the surface of the shell, so that the local 1-direction, local 2-direction, and the positive normal to the surface form a right-handed set (see [Figure 5&#8211;6](ch05s03.html#gss-localshell)).
**Figure 5&#8211;6** Default local shell material directions.
../graphics/gss-localshell-nls.png
The default set of local material directions can sometimes cause problems; a case in point is the cylinder shown in [Figure 5&#8211;7](ch05s03.html#gss-one-direct).
**Figure 5&#8211;7** Default local material 1-direction in a cylinder.
../graphics/gss-one-direct.pngFor most of the elements in the figure the local 1-direction is circumferential. However, there is a line of elements that are normal to the global 1-axis. For these elements the local 1-direction is the projection of the global 3-axis onto the shell, making the local 1-direction axial instead of circumferential. A contour plot of the direct stress in the local 1-direction, ../graphics/gsa_eqn00028.gif, looks very strange, since for most elements ../graphics/gsa_eqn00028.gif is the circumferential stress, whereas for some elements it is the axial stress. In such cases it is necessary to define more appropriate local directions for the model, as discussed in the next section.5.3.2&nbsp;Creating alternative material directions
You can replace the global Cartesian coordinate system with a local rectangular, cylindrical, or spherical coordinate system, as shown in [Figure 5&#8211;8](ch05s03.html#gss-coord-system).
**Figure 5&#8211;8** Definition of local coordinate systems.
../graphics/gss-coord-system-nls.png
You define the orientation of the local (../graphics/gsa_eqn00038.gif, ../graphics/gsa_eqn00039.gif, ../graphics/gsa_eqn00040.gif) coordinate system, as well as which of the local axes corresponds to which material direction. Thus, you must specify the local axis (1, 2, or 3) that is closest to being normal to the shell's surface. Abaqus follows a cyclic permutation (1, 2, 3) of the axes and projects the axis following your selection onto the shell region to form the material 1-direction. For example, if you choose the ../graphics/gsa_eqn00038.gif-axis, Abaqus projects the ../graphics/gsa_eqn00039.gif-axis onto the shell to form the material 1-direction. The material 2-direction is defined by the cross product of the shell normal and the material 1-direction. Normally, the final material 2-direction and the projection of the other local axis, in this case the ../graphics/gsa_eqn00040.gif-axis, will not coincide for curved shells.
If these local axes do not create the desired material directions, you can specify a rotation about the selected axis. The other two local axes are rotated by this amount before they are projected onto the shell's surface to give the final material directions. For the projections to be interpreted easily, the selected axis should be as close as possible to the shell normal.
For example, if the centerline of the cylinder shown in [Figure 5&#8211;7](ch05s03.html#gss-one-direct) coincides with the global 3-axis, local material directions can be defined such that the local material 1-direction is always circumferential and the corresponding local material 2-direction is always axial. The procedure is described below.
**To define local material directions:**
-
From the main menu bar of the Property module, select **Tools**../images/arrow.gif**Datum** and define a cylindrical datum coordinate system.
-
Select **Assign**../images/arrow.gif**Material Orientation** to assign a local material orientation to your part. When prompted to select a coordinate system, select the datum coordinate system defined in the previous step. The approximate shell normal direction is **Axis 1**; no additional rotation is necessary.

## 5.4&nbsp;Selecting shell elements

5.4&nbsp;Selecting shell elements
-
The linear, finite-membrane-strain, fully integrated, quadrilateral shell element (S4) can be used when greater solution accuracy is desired, for problems prone to membrane- or bending-mode hourglassing, or for problems where in-plane bending is expected.
-
The linear, finite-membrane-strain, reduced-integration, quadrilateral shell element (S4R) is robust and is suitable for a wide range of applications.
-
The linear, finite-membrane-strain, triangular shell elements (S3/S3R) can be used as general-purpose elements. A refined mesh may be needed to capture bending deformations or high strain gradients because of the constant strain approximation in the elements.
-
To account for the influence of shear flexibility in laminated composite shell models, use the shell elements suitable for modeling thick shells (S4, S4R, S3/S3R, S8R); check that the assumption of plane sections remaining plane is satisfied.
-
Quadratic shell elements, either quadrilateral or triangular, are very effective for general, small-strain, thin-shell applications. These elements are not susceptible to shear or membrane locking.
-
If you must use second-order elements in contact simulations, do not use the quadratic, triangular shell element (STRI65). Use the 9-node, quadrilateral shell element (S9R5) instead.
-
For very large models that will experience only geometrically linear behavior, the linear, thin-shell element (S4R5) will generally be more cost-effective than the general-purpose shell elements.
-
The small membrane strain elements are effective for explicit dynamics problems involving small membrane strains and arbitrarily large rotations.

## 5.5&nbsp;Example: skew plate

*You have been asked to model the plate shown in Figure 5&#8211;9. Figure 5&#8211;9*

5.5&nbsp;Example: skew plate
You have been asked to model the plate shown in [Figure 5&#8211;9](ch05s05.html#gss-skewed-plate).
**Figure 5&#8211;9** Sketch of the skew plate.
../graphics/gss-skewed-plate-nls.pngIt is skewed 30 to the global 1-axis, is built-in at one end, and is constrained to move on rails parallel to the plate axis at the other end. You are to determine the midspan deflection when the plate carries a uniform pressure. You are also to assess whether a linear analysis is valid for this problem. You will perform an analysis using Abaqus/Standard.5.5.1&nbsp;Preprocessing&#8212;creating the model with Abaqus/CAE
Use Abaqus/CAE to create the entire model for this simulation. Abaqus provides scripts that replicate the complete analysis model for this problem. Run one of these scripts if you encounter difficulties following the instructions given below or if you wish to check your work. Scripts are available in the following locations:
-
A Python script for this example is provided in [&#8220;Skew plate,&#8221;  Section A.3](ap01s03.html). Instructions on how to fetch the script and run it within Abaqus/CAE are given in [Appendix A, &#8220;Example Files](ap01.html).&#8221;
-
A plug-in script for this example is available in the Abaqus/CAE Plug-in toolset. To run the script from Abaqus/CAE, select **Plug-ins**../images/arrow.gif**Abaqus**../images/arrow.gif**Getting Started**; highlight **Skew plate**; and click **Run**. For more information about the Getting Started plug-ins, see &#8220;Running the Getting Started with Abaqus examples,&#8221;  Section 82.1 of the Abaqus/CAE User's Guide.
If you do not have access to Abaqus/CAE or another preprocessor, the input file required for this problem can be created manually, as discussed in &#8220;Example: skew plate,&#8221;  Section 5.5 of Getting Started with Abaqus: Keywords Edition.
Before you start to build the model, decide on a system of units. The dimensions are given in cm, but the loading and material properties are given in MPa and GPa. Since these are not consistent units, you must choose a consistent system to use in your model and convert the necessary input data. In the following discussion newtons, meters, kilograms, and seconds are used.
**Defining the model geometry**
Start Abaqus/CAE, and create a three-dimensional, deformable body with a planar shell base feature. Name the part `Plate`, and specify an approximate part size of `4.0`. A suggested approach to creating the part geometry is outlined in the following procedure:
**To sketch the plate geometry:**
-
In the Sketcher, create an arbitrary rectangle using the **Create Lines: Rectangle (4 Lines)** tool.
-
Delete all constraints automatically imposed by the sketcher (four perpendicular constraints and one horizontal constraint).
-
Constrain the left and right edges to remain vertical and the bottom and top edges to be parallel.
-
Dimension the left edge by selecting the line and assign it a value of `0.4` m.
-
Dimension the bottom edge. Select the vertices of the line rather than the line itself to define a horizontal dimension. Set the horizontal distance between the vertices to `1.0` m.
Note:&nbsp;
If you were to dimension the line itself, you would control only the length of the line (in whatever orientation it assumes).
-
Dimension the angle between the left and bottom edges. Select the left and bottom edges in succession, and set the value of the angle to `60`.
The final sketch is shown in [Figure 5&#8211;10](ch05s05.html#gss-skewplate-part-c).
**Figure 5&#8211;10** Sketch of the plate geometry (with grid spacing doubled).
../graphics/gss-skewplate-part-c.png
-
In the prompt area, click **Done** to finish the sketch.
**Defining the material and section properties and the local material directions**
The plate is made of an isotropic, linear elastic material with a Young's modulus *E* = 30  109 Pa and a Poisson's ratio ../graphics/gsa_eqn00034.gif = 0.3. Create the material definition; name the material `Metal`.
The orientation of the structure in the global coordinate system is shown in [Figure 5&#8211;9](ch05s05.html#gss-skewed-plate). The global Cartesian coordinate system defines the default material directions, but the plate is skewed relative to this system. It will not be easy to interpret the results of the simulation if you use the default material directions because the direct stress in the material 1-direction, ../graphics/gsa_eqn00028.gif, will contain contributions from both the axial stress, produced by the bending of the plate, and the stress transverse to the axis of the plate. It will be easier to interpret the results if the material directions are aligned with the axis of the plate and the transverse direction. Therefore, a local rectangular coordinate system is needed in which the local ../graphics/gsa_eqn00038.gif-direction lies along the axis of the plate (i.e., at 30 to the global 1-axis) and the local ../graphics/gsa_eqn00039.gif-direction is also in the plane of the plate. Following the instructions given below, define the shell section properties in a local (nondefault) material coordinate system.
**To define shell section properties and local material directions:**
-
Define a homogeneous shell section named `PlateSection`. Specify that section integration be performed before the analysis since the material is linear elastic, and accept the default idealization option of **No idealization**. Assign a shell thickness of `0.8E-2` and the `Metal` material definition to the section.
-
Define a rectangular datum coordinate system as shown in [Figure 5&#8211;11](ch05s05.html#gss-skewplate-datumcsys-c) using the **Create Datum CSYS: 2 Lines** tool ../graphics/ico_dtmCsysTwoLines.png.
**Figure 5&#8211;11** Datum coordinate system used to define local material directions.
../graphics/gss-skewplate-datumcsys-c-nls.png
-
From the main menu bar of the Property module, select **Assign**../images/arrow.gif**Material Orientation** and select the entire part as the region to which local material directions will be applied. In the viewport, select the datum coordinate system created earlier. Select **Axis 3** for the direction of the approximate shell normal. No additional rotation is needed about this axis.
Tip:&nbsp;
To verify that the local material directions have been assigned correctly, select **Tools**../images/arrow.gif**Query** from the main menu bar and perform a property query on the material orientations. Triads appear in the viewport indicating the material orientation of the region you select.
Once the part has been meshed and elements have been created in the model, all element variables will be defined in this local coordinate system.
-
Assign the section definition to the plate. Accept **Middle surface** as the shell offset definition.
**Creating an assembly, defining an analysis step, and specifying output requests**
Create a dependent instance of the plate.
You will partition the plate in half at its midspan; this will allow you to define a set there. You will also define additional assembly-level sets to facilitate other output request and boundary condition definitions.
**To partition the plate and define geometry sets:**
-
In the Model Tree, double-click the **Plate** item in the **Parts** container to make it current.
-
Partition the plate in half using the **Partition Face: Use Shortest Path Between 2 Points** tool, ../graphics/ico_ptnFaceTwoPoints.png. Use the midpoints of the skewed edges of the plate to create the partition shown in [Figure 5&#8211;12](ch05s05.html#gss-skewplate-partit-c).
**Figure 5&#8211;12** Partition used to define a geometry set at the plate midspan.
../graphics/gss-skewplate-partit-c-nls.png
-
In the Model Tree, expand the **Assembly** container and double-click the **Sets** item to create a geometry set for the midspan named `MidSpan`. Similarly, create sets for the left and right edges of the plate and name them `EndA` and `EndB`, respectively. The locations of these three sets are indicated in [Figure 5&#8211;12](ch05s05.html#gss-skewplate-partit-c).
Tip:&nbsp;
Geometry sets can be reviewed by expanding the **Sets** item underneath the **Assembly** container in the Model Tree and then double-clicking on the set name in the list that appears. The selected set is highlighted in the viewport, and its definition can be edited if necessary.
Next, create a single static, general step. Name the step `Apply Pressure`, and specify the following step description: `Uniform pressure (20 kPa) load`. Accept all the default settings for the step.
Among the output you will need are the nodal displacements, reaction forces, and element stresses as field data. These data will be used to create deformed shape plots, contour plots, and tabular data reports in the Visualization module. You will also want to write the displacements at the midspan as history data to create *X&#8211;Y* plots in the Visualization module.
**To change the default output requests:**
-
Edit the field output request so that only the nodal displacements, reaction forces, and element stresses and strains for the whole model are written as field data to the `.odb` file.
-
Edit the history output request so that only the vertical nodal displacements **U3** for the set named `MidSpan` are written as history data to the `.odb` file.
**Prescribing boundary conditions and applied loads**
As shown in [Figure 5&#8211;9](ch05s05.html#gss-skewed-plate), the left end of the plate is completely fixed; the right end is constrained to move on rails that are parallel to the axis of the plate. Since the latter boundary condition direction does not coincide with the global axes, you must define a local coordinate system that has an axis aligned with the plate. You can use the datum coordinate system that you created earlier to define the local material directions.
**To assign boundary conditions in a local coordinate system:**
-
In the Model Tree, double-click the **BCs** container and define a **Displacement/Rotation** mechanical boundary condition named `Rail boundary condition` in the `Apply Pressure` step.
In this example you will assign boundary conditions to sets rather than to regions selected directly in the viewport. Thus, when prompted for the regions to which the boundary condition will be applied, click **Sets** in the prompt area of the viewport.
-
From the **Region Selection** dialog box that appears, select set **EndB**. Toggle on **Highlight selections in viewport** to make sure the correct set is selected. The right edge of the plate should be highlighted. Click **Continue**.
-
In the **Edit Boundary Condition** dialog box, click ../graphics/ico_selectBlue.png to specify the local coordinate system in which the boundary condition will be applied. In the viewport, select the datum coordinate system that was created earlier to define the local directions. The local 1-direction is aligned with the plate axis.
-
In the **Edit Boundary Condition** dialog box, fix all degrees of freedom except for **U1**.
The right edge of the plate is now constrained to move only in the direction of the plate axis. Once the plate has been meshed and nodes have been generated in the model, all printed nodal output quantities associated with this region (displacements, velocities, reaction forces, etc.) will be defined in this local coordinate system.
Complete the boundary condition definition by fixing all degrees of freedom at the left edge of the plate (set **EndA**). Name this boundary condition `Fix left end`. Use the default global directions for this boundary condition.
Finally, define a uniform pressure load across the top of the shell named `Pressure`. Select both regions of the part using **[Shift]****+Click** and then click **Done**. When prompted to choose a side for the shell or internal faces, select **Brown**, which corresponds to the top side of the plate. You may need to rotate the view to more clearly distinguish the top side of the plate. Specify a load magnitude of `2.E4` Pa.
**Creating the mesh and defining a job**
[Figure 5&#8211;13](ch05s05.html#gss-skewplate-mesh-c) shows the suggested mesh for this simulation.
**Figure 5&#8211;13** Suggested mesh design for the skew plate simulation.
../graphics/gss-skewplate-mesh-c.png
You must answer the following questions before selecting an element type: Is the plate thin or thick? Are the strains small or large? The plate is quite thin, with a thickness-to-minimum span ratio of 0.02. (The thickness is 0.8 cm and the minimum span is 40 cm.) While we cannot readily predict the magnitude of the strains in the structure, we think that the strains will be small. Based on this information, choose quadratic shell elements (S8R5) because they give accurate results for thin shells in small-strain simulations. For further details on shell element selection, refer to &#8220;Choosing a shell element,&#8221;  Section 29.6.2 of the Abaqus Analysis User's Guide.
In the Model Tree,  expand the **Plate** item underneath the **Parts** container and double-click **Mesh** in the list that appears. Seed the part using a global element size of `0.1`. Create a quadrilateral mesh using quadratic, reduced-integration shell elements with five degrees of freedom per node (S8R5).
Before proceeding, rename the model to `Linear`. This model will later form the basis of the model used in the skew plate example discussed in [Chapter 8, &#8220;Nonlinearity](ch08.html).&#8221;
Define a job named `SkewPlate` with the following description: ```
Linear Elastic Skew Plate. 20 kPa Load.
``` Save your model in a model database file named `SkewPlate.cae`.
Submit the job for analysis, and monitor the solution progress; correct any modeling errors detected by the analysis product, and investigate the cause of any warnings.5.5.2&nbsp;Postprocessing
This section discusses postprocessing with Abaqus/CAE. Both contour and symbol plots are useful for visualizing shell analysis results. Since contour plotting was discussed in detail in [Chapter 4, &#8220;Using Continuum Elements](ch04.html),&#8221; we use symbol plots here.
In the **Module** list located in the context bar, click **Visualization** to enter the Visualization module. Then, open the `.odb` file created by this job (`SkewPlate.odb`).
By default, Abaqus/CAE plots the undeformed shape of the model.
**Element normals**
Use the undeformed shape plot to check the model definition. Check that the element normals for the skew-plate model were defined correctly and point in the positive 3-direction.
**To display the element normals:**
-
From the main menu bar, select **Options**../images/arrow.gif**Common**; or use the ../graphics/ico_plotCommonOptions.png tool in the toolbox.
The **Common Plot Options** dialog box appears.
-
Click the **Normals** tab.
-
Toggle on **Show normals**, and accept the default setting of **On elements**.
-
Click **OK** to apply the settings and to close the dialog box.
The default view is isometric. You can change the view using the options in the view menu or the view tools (such as ../graphics/ico_viewRotate.png) from the **View Manipulation** toolbar.
**To change the view:**
-
From the main menu bar, select **View**../images/arrow.gif**Specify**.
The **Specify View** dialog box appears.
-
From the list of available methods, select **Viewpoint**.
-
Enter the ../graphics/gsa_eqn00041.gif-, ../graphics/gsa_eqn00042.gif- and ../graphics/gsa_eqn00043.gif-coordinates of the viewpoint vector as `0.2, 1, 0.8` and the coordinates of the up vector as `0, 0, 1`.
-
Click **OK**.
Abaqus/CAE displays your model in the specified view, as shown in [Figure 5&#8211;14](ch05s05.html#gss-normals-c).
**Figure 5&#8211;14** Shell element normals in the skew plate model.
../graphics/gss-normals-c.png
**Symbol plots**
Symbol plots display the specified variable as a vector originating from the node or element integration points. You can produce symbol plots of most tensor- and vector-valued variables. The exceptions are mainly nonmechanical output variables and element results stored at nodes, such as nodal forces. The relative size of the arrows indicates the relative magnitude of the results, and the vectors are oriented along the global direction of the results. The symbol plot legend shows how each arrow color corresponds to a specific range of values. You can plot results for the resultant of variables such as displacement (U), reaction force (RF), etc.; or you can plot individual components of these variables.
Before proceeding, suppress the visibility of the element normals.
**To generate a symbol plot of the displacement:**
-
From the list of variable types on the left side of the **Field Output** toolbar, select **Symbol**.
-
From the list of output variables in the center of the toolbar, select **U**.
-
From the list of vector quantities and selected components,  select **U3**.
Abaqus/CAE displays a symbol plot of the displacement vector resultant on the deformed model shape.
-
The default shaded render style obscures the arrows. An unobstructed view of the arrows can be obtained by changing the render style to **Wireframe** using the** Common Plot Options** dialog box. If the element normals are still visible, you should turn them off at this time.
-
The symbol plot can also be based on the undeformed model shape. From the main menu bar, select **Plot**../images/arrow.gif**Symbols**../images/arrow.gif**On Undeformed Shape**.
A symbol plot on the undeformed model shape appears, as shown in [Figure 5&#8211;15](ch05s05.html#gss-displacement).
**Figure 5&#8211;15** Symbol plot of displacement.
../graphics/gss-displacement-c.png
You can plot principal values of tensor variables such as stress using symbol plots. A symbol plot of the principal values of stress yields three vectors at every integration point, each corresponding to a principal value oriented along the corresponding principal direction. Compressive values are indicated by arrows pointing toward the integration point, and tensile values are indicated by arrows pointing away from the integration point. You can also plot individual principal values.
**To generate a symbol plot of the principal stresses:**
-
From the list of variable types on the left side of the **Field Output** toolbar, select **Symbol**.
-
From the list of output variables in the center of the toolbar, select **S**.
-
From the list of tensor quantities and components, select **ALL_PRINCIPAL_COMPONENTS** as the tensor quantity.
Abaqus/CAE displays a symbol plot of principal stresses.
-
From the main menu bar, select **Options**../images/arrow.gif**Symbol**; or use the **Symbol Options** ../graphics/ico_plotSymbolOptions.png tool in the toolbox to change the arrow length.
The **Symbol Plot Options** dialog box appears.
-
In the **Color &amp; Style** page, click the **Tensor** tab.
-
Drag the **Size** slider to select `2` as the arrow length.
-
Click **OK** to apply the settings and to close the dialog box.
The symbol plot shown in [Figure 5&#8211;16](ch05s05.html#gss-vector-plot) appears.
**Figure 5&#8211;16** Symbol plot of principal stresses on the bottom surface of the plate.
../graphics/gss-vector-plot-c.png
-
The principal stresses are displayed at section point 1 by default. To plot stresses at nondefault section points, select **Result**../images/arrow.gif**Section Points** from the main menu bar to open the **Section Points** dialog box.
-
Select the desired nondefault section point for plotting.
-
In a complex model, the element edges can obscure the symbol plots. To suppress the display of the element edges, choose **Feature edges** in the **Basic** tabbed page of the **Common Plot Options** dialog box.
[Figure 5&#8211;17](ch05s05.html#gss-perimeter) shows a symbol plot of the principal stresses at the default section point with only feature edges visible.
**Figure 5&#8211;17** Symbol plot of principal stresses using feature edges.
../graphics/gss-perimeter-c.png
**Material directions**
Abaqus/CAE also allows you visualize the element material directions. This feature is particularly useful if you would like to verify that the material directions were assigned correctly in the simulation.
**To plot the material directions:**
-
From the main menu bar, select **Plot**../images/arrow.gif**Material Orientations**../images/arrow.gif**On Undeformed Shape**; or use the ../graphics/ico_plotMatOrientUndeformed.png tool in the toolbox.
The material orientation directions are plotted on the undeformed shape. By default, the triads that represent the material orientation directions are plotted without arrowheads.
-
From the main menu bar, select **Options**../images/arrow.gif**Material Orientation**; or use the **Material Orientation Options** ../graphics/ico_plotMatOrientOptions.png tool in the toolbox to display the triads with arrowheads.
The **Material Orientation Plot Options** dialog box appears.
-
Set the **Arrowhead** option to use filled arrowheads in the triad.
-
Click **OK** to apply the settings and to close the dialog box.
-
Use the predefined views available in the **Views** toolbar to display the plate as shown in [Figure 5&#8211;18](ch05s05.html#gss-orientation). In this figure, perspective is turned off. To turn off perspective, click the ../graphics/ico_viewParallel.png tool in the **View Options** toolbar.
Tip:&nbsp;
If the **Views** toolbar is not visible, select **View**../images/arrow.gif**Toolbars**../images/arrow.gif**Views** from the main menu bar.
By default, the material 1-direction is colored blue, the material 2-direction is colored yellow, and, if it is present, the material 3-direction is colored red.
**Figure 5&#8211;18** Plot of material orientation directions in the plate.
../graphics/gss-orientation-c.png
**Evaluating results based on tabular data**
Additional postprocessing can be performed by examining printed data. With the aid of display groups, create a tabular data report of the whole model element stresses (components **S11**, **S22**, and **S12**), the reaction forces and moments at the supported nodes (sets **EndA** and **EndB**), and the displacements of the midspan nodes (set **MidSpan**). The stress data are shown below.```
Field Output Report
Source 1
---------
ODB: SkewPlate.odb
Step: Apply pressure
Frame: Increment      1: Step Time =    1.000
Loc 1 : Integration point values at shell general ... : SNEG, (fraction = -1.0)
Loc 2 : Integration point values at shell general ... : SPOS, (fraction =  1.0)
Output sorted by column "Element Label".
Field Output reported at integration points for part: PLATE-1
Element    Int          S.S11         S.S11         S.S22         S.S22         S.S12         S.S12
Label     Pt         @Loc 1        @Loc 2        @Loc 1        @Loc 2        @Loc 1        @Loc 2
-----------------------------------------------------------------------------------------------------
1      1   79.7614E+06  -79.7614E+06    1.1085E+06   -1.1085E+06  -5.86291E+06   5.86291E+06
1      2   83.7703E+06  -83.7703E+06   7.14559E+06  -7.14559E+06  -8.00706E+06   8.00706E+06
1      3   66.9385E+06  -66.9385E+06   2.79241E+06  -2.79241E+06  -1.98396E+06   1.98396E+06
1      4   72.3479E+06  -72.3479E+06   5.05957E+06  -5.05957E+06   -7.0819E+06    7.0819E+06
.
.
48      1  -142.755E+06   142.755E+06  -56.0747E+06   56.0747E+06    21.007E+06   -21.007E+06
48      2  -118.848E+06   118.848E+06  -7.21449E+06   7.21449E+06   4.00065E+06  -4.00065E+06
48      3   -187.19E+06    187.19E+06   -103.31E+06    103.31E+06    50.352E+06   -50.352E+06
48      4  -238.323E+06   238.323E+06  -84.7331E+06   84.7331E+06   70.0676E+06  -70.0676E+06
Minimum         -238.323E+06  -90.2378E+06   -103.31E+06  -10.5216E+06   -18.865E+06  -70.0676E+06
At Element            48             4            24             2            12            48
Int Pt             4             4             3             2             4             4
Maximum          90.2378E+06   238.323E+06   10.5216E+06    103.31E+06   70.0676E+06    18.865E+06
At Element             4            48             2            24            48            12
Int Pt             4             4             2             3             4             4
```The locations `Loc 1` and `Loc 2` identify the section point in the element where the stress was calculated. `Loc 1` (corresponding to section point&nbsp;1) lies on the SNEG surface of the shell, and `Loc 2` (corresponding to section point&nbsp;3) lies on the SPOS surface. Local material directions have been used for the element: the stresses refer to a local coordinate system.
Check that the small-strain assumption was valid for this simulation. The axial strain corresponding to the peak stress is ../graphics/gsa_eqn00044.gif 0.008. Because the strain is typically considered small if it is less than 4 or 5%, a strain of 0.8% is well within the appropriate range to be modeled with S8R5 elements.
The reaction forces and moments are reported in the following table: ```
Field Output Report
Source 1
---------
ODB: SkewPlate.odb
Step: Apply pressure
Frame: Increment      1: Step Time =    1.000
Loc 1 : Nodal values from source 1
Output sorted by column "Node Label".
Field Output reported at nodes for part: PLATE-1
Node       RF.RF1       RF.RF2       RF.RF3       RM.RM1       RM.RM2       RM.RM3
Label       @Loc 1       @Loc 1       @Loc 1       @Loc 1       @Loc 1       @Loc 1
-------------------------------------------------------------------------------------
3           0.           0.      37.3924      -1.5991     -76.4939           0.
4           0.           0.     -109.834      1.77236 -324.424E-03           0.
5           0.           0.      37.3918      1.59909      76.4939           0.
6           0.           0.     -109.834     -1.77236  324.411E-03           0.
15           0.           0.      73.6366      8.75019     -62.2243           0.
16           0.           0.      260.424      6.95105     -51.1181           0.
17           0.           0.      239.685      6.56987     -35.4374           0.
28           0.           0.      73.6366     -8.75019      62.2243           0.
29           0.           0.      260.424     -6.95105      51.1181           0.
30           0.           0.      239.685     -6.56988      35.4374           0.
116           0.           0.      6.15382       7.5915     -36.4274           0.
119           0.           0.      455.132      6.80781      -88.237           0.
121           0.           0.      750.805      8.31069     -126.462           0.
123           0.           0.   2.2866E+03      31.0977     -205.818           0.
170           0.           0.        6.154      -7.5915      36.4274           0.
173           0.           0.      455.133     -6.80782       88.237           0.
175           0.           0.      750.805     -8.31069      126.462           0.
177           0.           0.   2.2866E+03     -31.0977      205.818           0.
Minimum         0.           0.     -109.834     -31.0977     -205.818           0.
At Node    177          177            6          177          123          177
Maximum         0.           0.   2.2866E+03      31.0977      205.818           0.
At Node    177          177          177          123          177          177
Total     0.           0.  8.00000E+03 -39.2199E-06 -5.00679E-06           0.
```The reaction forces are written in the global coordinate system. Check that the sum of the reaction forces and reaction moments with the corresponding applied loads is zero. The nonzero reaction force in the 3-direction equilibrates the vertical force of the pressure load (20 kPa  1.0 m  0.4 m). In addition to the reaction forces, the pressure load causes self-equilibrating reaction moments at the constrained rotational degrees of freedom.
This example was run as a linear analysis, in which it is assumed that the nodal displacements are small relative to the characteristic structural dimensions. The midspan deflection across the plate, as indicated in the table of displacements (not shown here), is approximately 5.4 cm, or roughly 5% of the plate's length. However, it is questionable whether the displacements are sufficiently small for a linear analysis to provide accurate results. Nonlinear effects in the structure may be important, so we need to run a nonlinear analysis to further investigate this example. Geometrically nonlinear analyses are discussed in [Chapter 8, &#8220;Nonlinearity](ch08.html).&#8221;

## 5.6&nbsp;Related Abaqus examples

5.6&nbsp;Related Abaqus examples
-
&#8220;Pressurized fuel tank with variable shell thickness,&#8221;  Section 2.1.6 of the Abaqus Example Problems Guide
-
&#8220;Analysis of an anisotropic layered plate,&#8221;  Section 1.1.2 of the Abaqus Benchmarks Guide
-
&#8220;Buckling of a simply supported square plate,&#8221;  Section 1.2.4 of the Abaqus Benchmarks Guide
-
&#8220;The barrel vault roof problem,&#8221;  Section 2.3.1 of the Abaqus Benchmarks Guide

## 5.7&nbsp;Suggested reading

5.7&nbsp;Suggested reading
The following references provide a more in-depth treatment of the theoretical and computational aspects of shell theory.
**Basic shell theory**
-
Timoshenko, S., *Strength of Materials: Part II*, Krieger Publishing Co., 1958.
-
Timoshenko, S. and S. W. Krieger, *Theory of Plates and Shells*, McGraw-Hill, Inc., 1959.
-
Ugural, A. C., *Stresses in Plates and Shells*, McGraw-Hill, Inc., 1981.
**Basic computational shell theory**
-
Cook, R. D., D. S. Malkus, and M. E. Plesha, *Concepts and Applications of Finite Element Analysis*, John Wiley &amp; Sons, 1989.
-
Hughes, T. J. R., *The Finite Element Method*, Prentice-Hall, Inc., 1987.
**Advanced shell theory**
-
Budiansky, B., and J. L. Sanders, &#8220;On the `Best' First-Order Linear Shell Theory,&#8221; Progress in Applied Mechanics, The Prager Anniversary Volume, 129&#8211;140, 1963.
**Advanced computational shell theory**
-
Ashwell, D. G., and R. H. Gallagher, *Finite Elements for Thin Shells and Curved Members*, John Wiley &amp; Sons, 1976.
-
Hughes, T. J. R., T. E. Tezduyar, &#8220;Finite Elements Based upon Mindlin Plate Theory with Particular Reference to the Four-Node Bilinear Isoparametric Element,&#8221; Journal of Applied Mechanics, 587&#8211;596, 1981.
-
Simo, J. C., D. D. Fox, and M. S. Rifai, &#8220;On a Stress Resultant Geometrically Exact Shell Model. Part III: Computational Aspects of the Nonlinear Theory,&#8221; Computer Methods in Applied Mechanics and Engineering, vol. 79, 21&#8211;70, 1990.

## 5.8&nbsp;Summary

5.8&nbsp;Summary
-
The cross-section behavior of shell elements can be determined using numerical integration through the shell thickness or using a cross-section stiffness calculated at the beginning of the analysis.
-
Calculating the cross-section stiffness at the beginning of the analysis is efficient, but only linear materials can be considered when this is done; calculating the cross-section stiffness during the analysis using numerical integration allows both linear and nonlinear materials to be used.
-
Numerical integration is performed at a number of section points through the shell thickness. These section points are the locations at which element variables can be output. The default outermost section points lie on the surfaces of the shell.
-
The direction of a shell element's normal determines the positive and negative surfaces of the element. To define contact and interpret element output correctly, you must know which surface is which. The shell normal can be plotted in the Visualization module of Abaqus/CAE.
-
Shell elements use material directions local to each element. In large-displacement analyses the local material axes rotate with the element. Nondefault local coordinate systems can be defined. The element variables, such as stress and strain, are output in the local directions.
-
Local coordinate systems for nodes can also be defined. Concentrated loads and boundary conditions are applied in the local coordinate system. All printed nodal output, such as displacements, also refer to the local system by default.
-
Symbol plots can help you visualize the results from a simulation. They are especially useful for visualizing the motion and load paths of a structure.

