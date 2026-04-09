# 4.&nbsp;Using Continuum Elements

*The continuum (solid) family of stress/displacement elements is the most comprehensive of the element libraries in Abaqus. There are some differences in the solid element libraries available in Abaqus/Standard and Abaqus/Explicit.Abaqus/Standard solid element libraryThe Abaqus/Standard solid element library includes first-order (linear) interpolation elements and second-order (quadratic) interpolation elements in two or three dimensions using either full or reduced integration. Triangles and quadrilaterals are available in two dimensions; and tetrahedra, triangular wedges, and hexahedra (&#8220;bricks&#8221;) are provided in three dimensions. Modified second-order triangular and tetrahedral elements are also provided.In addition, hybrid and incompatible mode elements are available in Abaqus/Standard.Abaqus/Explicit solid element libraryThe Abaqus/Explicit solid element library includes reduced-integration first-order (linear) interpolation elements in two or three dimensions. Modified second-order interpolation triangles and tetrahedra are also available. Full integration or regular second-order elements are not available in Abaqus/Explicit, with the exception of the fully integrated first-order hexahedral element (an incompatible mode version of this element is also available).For detailed information on the options available for continuum elements, please see &#8220;*

4.&nbsp;Using Continuum Elements
The continuum (solid) family of stress/displacement elements is the most comprehensive of the element libraries in Abaqus. There are some differences in the solid element libraries available in Abaqus/Standard and Abaqus/Explicit.
**Abaqus/Standard solid element library**
The Abaqus/Standard solid element library includes first-order (linear) interpolation elements and second-order (quadratic) interpolation elements in two or three dimensions using either full or reduced integration. Triangles and quadrilaterals are available in two dimensions; and tetrahedra, triangular wedges, and hexahedra (&#8220;bricks&#8221;) are provided in three dimensions. Modified second-order triangular and tetrahedral elements are also provided.
In addition, hybrid and incompatible mode elements are available in Abaqus/Standard.
**Abaqus/Explicit solid element library**
The Abaqus/Explicit solid element library includes reduced-integration first-order (linear) interpolation elements in two or three dimensions. Modified second-order interpolation triangles and tetrahedra are also available. Full integration or regular second-order elements are not available in Abaqus/Explicit, with the exception of the fully integrated first-order hexahedral element (an incompatible mode version of this element is also available).For detailed information on the options available for continuum elements, please see &#8220;Solid (continuum) elements,&#8221;  Section 28.1.1 of the Abaqus Analysis User's Guide.
When the permutations of all these various element options are made, the total number of solid elements available to you is large&#8212;over 20 just for three-dimensional models. The accuracy of your simulation will depend strongly on the type of element you use in your model. The thought of choosing which of these elements is best for your model may seem daunting, especially at first. However, you will come to view this selection as a 20+ piece tool set that provides you with the ability to choose just the right tool, or element, for a particular job.
This chapter discusses the effect that different element formulations and levels of integration have on the accuracy of a particular analysis. Some general guidelines for selecting continuum elements are also given. These provide the foundation upon which you can build your knowledge as you gain more experience using Abaqus. The example at the end of this section will allow you to put this knowledge to use as you build and analyze a connecting lug.

## 4.1&nbsp;Element formulation and integration

*The influence that the order of the element (linear or quadratic), the element formulation, and the level of integration have on the accuracy of a structural simulation will be demonstrated by considering a static analysis of the cantilever beam shown in Figure 4&#8211;1. Figure 4&#8211;1*

4.1&nbsp;Element formulation and integration
The influence that the order of the element (linear or quadratic), the element formulation, and the level of integration have on the accuracy of a structural simulation will be demonstrated by considering a static analysis of the cantilever beam shown in [Figure 4&#8211;1](ch04s01.html#gss-pointload).
**Figure 4&#8211;1** Cantilever beam under a point load *P* at its free end.
../graphics/gss-pointload.pngThis is a classic test used to assess the behavior of a given finite element. Since the beam is relatively slender, we would normally model it with beam elements. However, it is used here to help assess the effectiveness of various solid elements.
The beam is 150 mm long, 2.5 mm wide, and 5 mm deep; built-in at one end; and carrying a tip load of 5 N at the free end. The material has a Young's modulus, *E*, of 70 GPa and a Poisson's ratio of 0.0. Using beam theory, the static deflection of the tip of the beam for a load *P* is given as
../graphics/gsa_eqn00030.gifwhere ../graphics/gsa_eqn00031.gif, *l* is the length, *b* is the width, and *d* is the depth of the beam.
For ../graphics/gsa_eqn00032.gif 5 N the tip deflection is 3.09 mm.4.1.1&nbsp;Full integration
The expression &#8220;full integration&#8221; refers to the number of Gauss points required to integrate the polynomial terms in an element's stiffness matrix exactly when the element has a regular shape. For hexahedral and quadrilateral elements a &#8220;regular shape&#8221; means that the edges are straight and meet at right angles and that any edge nodes are at the midpoint of the edge. Fully integrated, linear elements use two integration points in each direction. Thus, the three-dimensional element C3D8 uses a 2  2  2 array of integration points in the element. Fully integrated, quadratic elements (available only in Abaqus/Standard) use three integration points in each direction. The locations of the integration points in fully integrated, two-dimensional, quadrilateral elements are shown in [Figure 4&#8211;2](ch04s01.html#gss-linear-quad).
**Figure 4&#8211;2** Integration points in fully integrated, two-dimensional, quadrilateral elements.
../graphics/gss-linear-quad-nls.png
Several different finite element meshes were used in Abaqus/Standard simulations of the cantilever beam problem, as shown in [Figure 4&#8211;3](ch04s01.html#gss-four-meshes). The simulations use either linear or quadratic, fully integrated elements and illustrate the effects of both the order of the element (first versus second) and the mesh density on the accuracy of the results.
**Figure 4&#8211;3** Meshes used for the cantilever beam simulations.
../graphics/gss-four-meshes.png
The ratios of the tip displacements for the various simulations to the beam-theory value of 3.09&nbsp;mm are shown in [Table 4&#8211;1](ch04s01.html#gss-continuum-table-beam).
**Table 4&#8211;1** Normalized tip displacements with fully-integrated elements.
The linear elements CPS4 and C3D8 underpredict the deflection so badly that the results are unusable. The results are least accurate with coarse meshes, but even a fine mesh (8  24) still predicts a tip displacement that is only 56% of the theoretical value. Notice that for the linear, fully integrated elements it makes no difference how many elements there are through the thickness of the beam. The underprediction of tip deflection is caused by *shear locking*, which is a problem with all fully integrated, first-order, solid elements.
As we have seen, shear locking causes the elements to be too stiff in bending. It is explained as follows. Consider a small piece of material in a structure subject to pure bending. The material will distort as shown in [Figure 4&#8211;4](ch04s01.html#gss-deform).
**Figure 4&#8211;4** Deformation of material subjected to bending moment *M*.
../graphics/gss-deform.pngLines initially parallel to the horizontal axis take on constant curvature, and lines through the thickness remain straight. The angle between the horizontal and vertical lines remains at 90.
The edges of a linear element are unable to curve; therefore, if the small piece of material is modeled using a single element, its deformed shape is like that shown in [Figure 4&#8211;5](ch04s01.html#gss-linear-elem).
**Figure 4&#8211;5** Deformation of a fully integrated, linear element subjected to bending moment *M*.
../graphics/gss-linear-elem.png
For visualization, dotted lines that pass through the integration points are plotted. It is apparent that the upper line has increased in length, indicating that the direct stress in the 1-direction, ../graphics/gsa_eqn00028.gif, is tensile. Similarly, the length of the lower dotted line has decreased, indicating that ../graphics/gsa_eqn00028.gif is compressive. The length of the vertical dotted lines has not changed (assuming that displacements are small); therefore, ../graphics/gsa_eqn00033.gif at all integration points is zero. All this is consistent with the expected state of stress of a small piece of material subjected to pure bending. However, at each integration point the angle between the vertical and horizontal lines, which was initially 90, has changed. This indicates that the shear stress, ../graphics/gsa_eqn00029.gif, at these points is nonzero. This is incorrect: the shear stress in a piece of material under pure bending is zero.
This spurious shear stress arises because the edges of the element are unable to curve. Its presence means that strain energy is creating shearing deformation rather than the intended bending deformation, so the overall deflections are less: the element is too stiff.
Shear locking only affects the performance of fully integrated, linear elements subjected to bending loads. These elements function perfectly well under direct or shear loads. Shear locking is not a problem for quadratic elements since their edges are able to curve (see [Figure 4&#8211;6](ch04s01.html#gss-quad-elem)). The predicted tip displacements for the quadratic elements shown in [Table 4&#8211;1](ch04s01.html#gss-continuum-table-beam) are close to the theoretical value. However, quadratic elements will also exhibit some locking if they are distorted or if the bending stress has a gradient, both of which can occur in practical problems.
**Figure 4&#8211;6** Deformation of a fully integrated, quadratic element subjected to bending moment *M*.
../graphics/gss-quad-elem.png
Fully integrated, linear elements should be used only when you are fairly certain that the loads will produce minimal bending in your model. Use a different element type if you have doubts about the type of deformation the loading will create. Fully integrated, quadratic elements can also lock under complex states of stress; thus, you should check the results carefully if they are used exclusively in your model. However, they are very useful for modeling areas where there are local stress concentrations.
*Volumetric locking* is another form of overconstraint that occurs in fully integrated elements when the material behavior is (almost) incompressible. It causes overly stiff behavior for deformations that should cause no volume changes. It is discussed further in [Chapter 10, &#8220;Materials](ch10.html).&#8221;4.1.2&nbsp;Reduced integration
Only quadrilateral and hexahedral elements can use a reduced-integration scheme; all wedge, tetrahedral, and triangular solid elements use full integration, although they can be used in the same mesh with reduced-integration hexahedral or quadrilateral elements.
Reduced-integration elements use one fewer integration point in each direction than the fully integrated elements. Reduced-integration, linear elements have just a single integration point located at the element's centroid. (Actually, these first-order elements in Abaqus use the more accurate &#8220;uniform strain&#8221; formulation, where average values of the strain components are computed for the element. This distinction is not important for this discussion.) The locations of the integration points for reduced-integration, quadrilateral elements are shown in [Figure 4&#8211;7](ch04s01.html#gss-reduced).
**Figure 4&#8211;7** Integration points in two-dimensional elements with reduced integration.
../graphics/gss-reduced-nls.png
Abaqus simulations of the cantilever beam problem were performed using the reduced-integration versions of the same four elements utilized previously and using the four finite element meshes shown in [Figure 4&#8211;3](ch04s01.html#gss-four-meshes). The results from these simulations are presented in [Table 4&#8211;2](ch04s01.html#gss-continuum-table-mesh).
**Table 4&#8211;2** Normalized tip displacements with reduced-integration elements.
Linear reduced-integration elements tend to be too flexible because they suffer from their own numerical problem called *hourglassing*. Again, consider a single reduced-integration element modeling a small piece of material subjected to pure bending (see [Figure 4&#8211;8](ch04s01.html#gss-reduced-integration)).
**Figure 4&#8211;8** Deformation of a linear element with reduced integration subjected to bending moment *M*.
../graphics/gss-reduced-integration.png
Neither of the dotted visualization lines has changed in length, and the angle between them is also unchanged, which means that all components of stress at the element's single integration point are zero. This bending mode of deformation is thus a zero-energy mode because no strain energy is generated by this element distortion. The element is unable to resist this type of deformation since it has no stiffness in this mode. In coarse meshes this zero-energy mode can propagate through the mesh, producing meaningless results.
In Abaqus a small amount of artificial &#8220;hourglass stiffness&#8221; is introduced in first-order reduced-integration elements to limit the propagation of hourglass modes. This stiffness is more effective at limiting the hourglass modes when more elements are used in the model, which means that linear reduced-integration elements can give acceptable results as long as a reasonably fine mesh is used. The errors seen with the finer meshes of linear reduced-integration elements (see [Table 4&#8211;2](ch04s01.html#gss-continuum-table-mesh)) are within an acceptable range for many applications. The results suggest that at least four elements should be used through the thickness when modeling any structures carrying bending loads with this type of element. When a single linear reduced-integration element is used through the thickness of the beam, all the integration points lie on the neutral axis and the model is unable to resist bending loads. (These cases are marked with a * in [Table 4&#8211;2](ch04s01.html#gss-continuum-table-mesh).)
Linear reduced-integration elements are very tolerant of distortion; therefore, use a fine mesh of these elements in any simulation where the distortion levels may be very high.
The quadratic reduced-integration elements available in Abaqus/Standard also have hourglass modes. However, the modes are almost impossible to propagate in a normal mesh and are rarely a problem if the mesh is sufficiently fine. The 1&nbsp;&nbsp;6 mesh of C3D20R elements fails to converge because of hourglassing unless two elements are used through the width, but the more refined meshes do not fail even when only one element is used through the width. Quadratic reduced-integration elements are not susceptible to locking, even when subjected to complicated states of stress. Therefore, these elements are generally the best choice for most general stress/displacement simulations, except in large-displacement simulations involving very large strains and in some types of contact analyses.4.1.3&nbsp;Incompatible mode elements
The incompatible mode elements, available primarily in Abaqus/Standard, are an attempt to overcome the problems of shear locking in fully integrated, first-order elements. Since shear locking is caused by the inability of the element's displacement field to model the kinematics associated with bending, additional degrees of freedom, which enhance the element's deformation gradient, are introduced into the first-order element. These enhancements to the deformation gradient allow a first-order element to have a linear variation of the deformation gradient across the element's domain as shown in [Figure 4&#8211;9](ch04s01.html#gss-deform-gradient)(a). The standard element formulation results in a constant deformation gradient across the element as shown in [Figure 4&#8211;9](ch04s01.html#gss-deform-gradient)(b), resulting in the nonzero shear stress associated with shear locking.
**Figure 4&#8211;9** Variation of deformation gradient in (a) an incompatible mode (enhanced deformation gradient) element and (b) a first-order element using a standard formulation.
../graphics/gss-deform-gradient.png These enhancements to the deformation gradient are entirely internal to an element and are not associated with nodes positioned along the element edges. Unlike incompatible mode formulations that enhance the displacement field directly, the formulation used in Abaqus does not result in overlapping material or a hole along the boundary between two elements, as shown in [Figure 4&#8211;10](ch04s01.html#gss-kinematic).
**Figure 4&#8211;10** Potential kinematic incompatibility between incompatible mode elements that use enhanced displacement fields rather than enhanced deformation gradients. Abaqus uses the latter formulation for its incompatible mode elements.
../graphics/gss-kinematic-nls.pngFurthermore, the formulation used in Abaqus is extended easily to nonlinear, finite-strain simulations, something which is not as easy with the enhanced displacement field elements.
Incompatible mode elements can produce results in bending problems that are comparable to quadratic elements but at significantly lower computational cost. However, they are sensitive to element distortions. [Figure 4&#8211;11](ch04s01.html#gss-distort-mesh) shows the cantilever beam modeled with deliberately distorted incompatible mode elements: in one case with &#8220;parallel&#8221; distortion and in the other with &#8220;trapezoidal&#8221; distortion.
**Figure 4&#8211;11** Distorted meshes of incompatible mode elements.
../graphics/gss-distort-mesh-nls.png
[Figure 4&#8211;12](ch04s01.html#gss-mode-elem) shows the tip displacements for the cantilever beam models. The tip displacements are normalized with respect to the analytical solution and plotted against the level of element distortion.
**Figure 4&#8211;12** Effect of parallel and trapezoidal distortion of incompatible mode elements.
../graphics/gss-mode-elem-v-nls.pngThree types of plane stress elements in Abaqus/Standard are compared: the fully integrated, linear element; the reduced-integration, quadratic element; and the linear, incompatible mode element. The fully integrated, linear elements produce poor results in all cases, as expected. On the other hand, the reduced-integration, quadratic elements give very good results that do not deteriorate until the elements are badly distorted.
When the incompatible mode elements are rectangular, even a mesh with just one element through the thickness of the cantilever gives results that are very close to the theoretical value. However, even quite small levels of trapezoidal distortion make the elements much too stiff. Parallel distortion also reduces the accuracy of the element but to a lesser extent.
Incompatible mode elements are useful because they can provide high accuracy at a low cost if they are used appropriately. However, care must be taken to ensure that the element distortions are small, which may be difficult when meshing complex geometries; therefore, you should again consider using the reduced-integration, quadratic elements in models with such geometries because they show much less sensitivity to mesh distortion. In a severely distorted mesh, however, simply changing the element type will generally not produce accurate results. The mesh distortion should be minimized as much as possible to improve the accuracy of the results.4.1.4&nbsp;Hybrid elements
A hybrid element formulation is available for just about every type of continuum element in Abaqus/Standard, including all reduced-integration and incompatible mode elements. Hybrid elements are not available in Abaqus/Explicit. Elements using this formulation have the letter &#8220;H&#8221; in their names.
Hybrid elements are used when the material behavior is incompressible (Poisson's ratio = 0.5) or very close to incompressible (Poisson's ratio &gt; 0.475). Rubber is an example of a material with incompressible material behavior. An incompressible material response cannot be modeled with regular elements (except in the case of plane stress) because the pressure stress in the element is indeterminate. Consider an element under uniform hydrostatic pressure ([Figure 4&#8211;13](ch04s01.html#gss-hydrostatic)).
**Figure 4&#8211;13** Element under hydrostatic pressure.
../graphics/gss-hydrostatic-nls.png
If the material is incompressible, its volume cannot change under this loading. Therefore, the pressure stress cannot be computed from the displacements of the nodes; and, thus, a pure displacement formulation is inadequate for any element with incompressible material behavior.
Hybrid elements include an additional degree of freedom that determines the pressure stress in the element directly. The nodal displacements are used only to calculate the deviatoric (shear) strains and stresses.
A more detailed description of the analysis of rubber materials is given in [Chapter 10, &#8220;Materials](ch10.html).&#8221;

## 4.2&nbsp;Selecting continuum elements

4.2&nbsp;Selecting continuum elements
The correct choice of element for a particular simulation is vital if accurate results are to be obtained at a reasonable cost. You will undoubtedly develop your own guidelines for selecting elements for your own particular applications as you become more experienced in using Abaqus. However, as you begin to use Abaqus, the guidelines given here may be helpful.
The following recommendations apply to both Abaqus/Standard and Abaqus/Explicit:
-
Minimize the mesh distortion as much as possible. Coarse meshes with distorted linear elements can give very poor results.
-
Use a fine mesh of linear, reduced-integration elements (CAX4R, CPE4R, CPS4R, C3D8R, etc.) for simulations involving very large mesh distortions (large-strain analysis).
-
In three dimensions use hexahedral (brick-shaped) elements wherever possible. They give the best results for the minimum cost. Complex geometries can be difficult to mesh completely with hexahedrons; therefore, wedge and tetrahedral elements may be necessary. The linear versions of these elements, C3D4 and C3D6, are poor elements (fine meshes are needed to obtain accurate results); as a result, these elements should generally be used only when necessary to complete a mesh, and, even then, they should be far from any areas where accurate results are needed.
-
Some preprocessors contain free-meshing algorithms that mesh arbitrary geometries with tetrahedral elements. The quadratic tetrahedral elements in Abaqus/Standard (C3D10 or C3D10I) are suitable for general usage; but when used with contact, they should be used only with the &#8220;surface-to-surface&#8221; contact discretization. An alternative to these elements is the modified quadratic tetrahedral element (C3D10M) available in both analysis products. This element is robust for large-deformation problems and contact problems using either the traditional &#8220;node-to-surface&#8221; or the &#8220;surface-to-surface&#8221; contact discretization and exhibits minimal shear and volumetric locking. With either type of element, however, the analysis will take longer to run than an equivalent mesh of hexahedral elements. You should not use a mesh containing only linear tetrahedral elements (C3D4): the results will be inaccurate unless you use an extremely large number of elements.
Abaqus/Standard users should also consider the following recommendations:
-
Use quadratic, reduced-integration elements (CAX8R, CPE8R, CPS8R, C3D20R, etc.) for general analysis work, unless you need to model very large strains or have a simulation with complex, changing contact conditions.
-
Use quadratic, fully integrated elements (CAX8, CPE8, CPS8, C3D20, etc.) locally where stress concentrations may exist. They provide the best resolution of the stress gradients at the lowest cost.
-
For contact problems use a fine mesh of linear, reduced-integration elements or incompatible mode elements (CAX4I, CPE4I, CPS4I, C3D8I, etc.). See [Chapter 12, &#8220;Contact](ch12.html).&#8221;

## 4.3&nbsp;Example: connecting lug

*In this example you will use three-dimensional, continuum elements to model the connecting lug shown in Figure 4&#8211;14.Figure 4&#8211;14*

4.3&nbsp;Example: connecting lug
In this example you will use three-dimensional, continuum elements to model the connecting lug shown in [Figure 4&#8211;14](ch04s03.html#gss-connecting-lug).
**Figure 4&#8211;14** Sketch of the connecting lug.
../graphics/gss-connecting-lug-nls.png
The lug is welded firmly to a massive structure at one end. The other end contains a hole. When it is in service, a bolt will be placed through the hole of the lug. You have been asked to determine the static deflection of the lug when a 30 kN load is applied to the bolt in the negative 2-direction. Because the goal of this analysis is to examine the static response of the lug, you should use Abaqus/Standard as your analysis product. You decide to simplify this problem by making the following assumptions:
-
Rather than include the complex bolt-lug interaction in the model, you will use a distributed pressure over the bottom half of the hole to load the connecting lug (see [Figure 4&#8211;14](ch04s03.html#gss-connecting-lug)).
-
You will neglect the variation of pressure magnitude around the circumference of the hole and use a uniform pressure.
-
The magnitude of the applied uniform pressure will be 50&nbsp;MPa: 30&nbsp;kN/ (2  0.015&nbsp;m&nbsp;  &nbsp;0.02&nbsp;m).
After examining the static response of the lug, you will modify the model and use Abaqus/Explicit to study the transient dynamic effects resulting from sudden loading of the lug.4.3.1&nbsp;Preprocessing&#8212;creating the model with Abaqus/CAE
In this section we discuss how to use Abaqus/CAE to create the entire model for this simulation. Abaqus provides scripts that replicate the complete analysis model for this problem. Run one of these scripts if you encounter difficulties following the instructions given below or if you wish to check your work. Scripts are available in the following locations:
-
A Python script for this example is provided in [&#8220;Connecting lug,&#8221;  Section A.2](ap01s02.html). Instructions on how to fetch the script and run it within Abaqus/CAE are given in [Appendix A, &#8220;Example Files](ap01.html).&#8221;
-
A plug-in script for this example is available in the Abaqus/CAE Plug-in toolset. To run the script from Abaqus/CAE, select **Plug-ins**../images/arrow.gif**Abaqus**../images/arrow.gif**Getting Started**; highlight **Connecting lug**; and click **Run**. For more information about the Getting Started plug-ins, see &#8220;Running the Getting Started with Abaqus examples,&#8221;  Section 82.1 of the Abaqus/CAE User's Guide.
If you do not have access to Abaqus/CAE or another preprocessor, the input file required for this problem can be created manually, as discussed in &#8220;Example: connecting lug,&#8221;  Section 4.3 of Getting Started with Abaqus: Keywords Edition.
**Starting Abaqus/CAE**
Start Abaqus/CAE by typing```
`*abaqus* cae`
```at the operating system prompt, where `*abaqus*` is the command used to run Abaqus on your system. From the **Create Model Database** options in the **Start Session** dialog box that appears, select **With Standard/Explicit Model**.
**Defining the model geometry**
As always, the first step in creating the model is to define its geometry. In this example you will create a three-dimensional, deformable body with a solid, extruded base feature. You will first sketch the two-dimensional profile of the lug and then extrude it.
You need to decide what system of units to use in your model. The SI system of meters, seconds, and kilograms is recommended; but you can use another system if you prefer.
**To create a part:**
-
In the **Create Part** dialog box, name the part `Lug` and accept the default settings of a three-dimensional, deformable body and a solid, extruded base feature. In the **Approximate size** text field, type `0.250`. This value is twice the largest dimension of the part. Click **Continue** to exit the **Create Part** dialog box.
-
Use the dimensions given in [Figure 4&#8211;14](ch04s03.html#gss-connecting-lug) to sketch the profile of the lug. The following possible approach can be used:
-
Create an arbitrary rectangle using the **Create Lines: Rectangle** tool. Delete the right vertical edge, and assign an **Equal length** constraint to the top and bottom edges using the constraints tool ../graphics/ico_sketchConstraint.png . Use the dimensions tool ../graphics/ico_sketchDimOblique.png to adjust the profile so that it is 0.100 m long  0.050 m wide, as shown in [Figure 4&#8211;15](ch04s03.html#gss-lug-parta-c).
**Figure 4&#8211;15** Open rectangle  (with grid spacing doubled).
../graphics/gss-lug-parta-c.png
Note:&nbsp;
The figures in this section include dimensions and constraints for the purpose of controlling the shape of the sketch. As seen previously, these tools are accessible from the Sketcher toolbox. These tools are also accessible by selecting **Add**../images/arrow.gif**Constraint** and **Add**../images/arrow.gif**Dimension**, respectively, from the main menu bar.
You can edit the dimension values as you add them to the sketch, or you can edit the value of existing dimensions by selecting **Edit**../images/arrow.gif**Dimension** from the main menu bar or by using the **Edit Dimension Value** ../graphics/ico_sketchDimensionEdit.png tool.
-
Close the profile by adding a semicircular arc, as shown in [Figure 4&#8211;16](ch04s03.html#gss-lug-partb-c), using the **Create Arc: Thru 3 points** tool, ../graphics/ico_sketchArcThreePts.png.
**Figure 4&#8211;16** Rounded end (with grid spacing doubled).
../graphics/gss-lug-partb-c.png Select the two vertices at the open end of the rectangle as the endpoints of the arc, starting with the top one. Select any point to the right of the sketch as a point that lies on the arc. Define **Tangent** constraints between the ends of the arc and the horizontal lines to refine the sketch. In [Figure 4&#8211;16](ch04s03.html#gss-lug-partb-c) the radial dimension of the arc is enclosed in parentheses, indicating that it is used only for reference purposes. To change any dimension to a reference value, simply edit the dimension and toggle on **Reference** in the **Edit Dimension** dialog box.
-
Sketch a circle of radius 0.015 m, as shown in [Figure 4&#8211;17](ch04s03.html#gss-lug-partc-c), using the **Create Circle: Center and Perimeter** tool, ../graphics/ico_sketchCircle.png.
**Figure 4&#8211;17** Lug hole (with grid spacing doubled).
../graphics/gss-lug-partc-c.pngPlace the center of the circle to coincide approximately with the center of the arc created in the previous step. The perimeter point should be placed to the right of the center point. Apply a **Concentric** constraint to the arc and the circle. Use the **Add Dimension** ../graphics/ico_sketchDimOblique.png tool to change the value of the radius to 0.015 m.
-
The perimeter points of the circles should be on the same horizontal plane as the circle center points (as in [Figure 4&#8211;17](ch04s03.html#gss-lug-partc-c)). If these points do not line up correctly, dimension the vertical distance between the center of each circle and its perimeter point so that the distance is 0.
Note:&nbsp;
When you mesh a part, Abaqus/CAE places nodes wherever vertices appear along an edge; therefore, the location of the vertex on the circumference of the circle influences the final mesh. Placing it on the same horizontal plane as the center point results in a higher quality mesh.
-
Click **Done** in the prompt area when you are finished sketching the profile.
The **Edit Base Extrusion** dialog box appears. To complete the part definition, you must specify the distance over which the profile will be extruded.
-
In the dialog box, enter an extrusion distance of `0.020` m and click **OK**.
Abaqus/CAE exits the Sketcher and displays the part.
**Defining the material and section properties**
The next step in creating the model involves defining and assigning material and section properties to the part. Each region of a deformable body must refer to a section property, which includes the material definition. In this model you will create a single linear elastic material with a Young's modulus *E* = 200 GPa and Poisson's ratio ../graphics/gsa_eqn00034.gif = 0.3.
**To define material properties:**
-
In the Model Tree, double-click the **Materials** container to create a new material definition.
-
In the material editor that appears,  name the material `Steel` and select **Mechanical**../images/arrow.gif**Elasticity**../images/arrow.gif**Elastic**. Enter `200.0E9` for the **Young's Modulus** and `0.3` for the **Poisson's Ratio**. Click **OK**.
**To define section properties:**
-
In the Model Tree, double-click the **Sections** container to create a new section definition. Accept the default solid, homogeneous section type; and name the section `LugSection`. Click **Continue**.
-
In the **Edit Section** dialog box that appears, accept **Steel** as the material and click **OK**.
**To assign section properties:**
-
In the Model Tree, expand the **Lug** item underneath the **Parts** container and double-click **Section Assignments** in the list of part attributes that appears.
-
Select the entire part as the region to which the section will be assigned by clicking on it. When the part is highlighted, click **Done** in the prompt area.
-
In the **Edit Section Assignment** dialog box that appears, accept **LugSection** as the section definition, and click **OK**.
**Creating an assembly**
An assembly contains all the geometry included in the finite element model. Each Abaqus/CAE model contains a single assembly. The assembly is initially empty, even though you have already created a part. You will create an instance of the part in the Assembly module to include it in your model.
**To instance a part:**
-
In the Model Tree, expand the **Assembly** container and double-click **Instances** in the list that appears  to create an instance of the part.
-
In the **Create Instance** dialog box, select **Lug** from the **Parts** list and click **OK**.
The model is oriented by default so that the global 1-axis lies along the length of the lug, the global 2-axis is vertical, and the global 3-axis lies in the thickness direction.
**Defining steps and specifying output requests**
You will now define the analysis steps. Since interactions, loads, and boundary conditions can be step dependent, analysis steps must be defined before these can be specified. For this simulation you will define a single static, general step. In addition, you will specify output requests for your analysis. These requests will include output to the output database (`.odb`) file.
**To define a step:**
-
In the Model Tree, double-click the **Steps** container to create an analysis step. In the **Create Step** dialog box that appears, name the step `LugLoad` and accept the **General** procedure type. From the list of available procedure options, accept **Static, General**. Click **Continue**.
-
In the **Edit Step** dialog box that appears, enter the following step description: `Apply uniform pressure to the hole`. Accept the default settings, and click **OK**.
Since you will use the Visualization module to postprocess the results, you must specify the output data you wish to have written to the output database file. Default history and field output requests are selected automatically by Abaqus/CAE for each procedure type. Edit these requests so that only the displacements, stresses, and reaction forces are written as field data to the output database file.
To specify output requests to the .odb file:
-
In the Model Tree, click mouse button 3 on the **Field Output Requests** container and select **Manager** from the menu that appears.
-
In the **Field Output Requests Manager** that appears, select the cell labeled `Created` in the column labeled **LugLoad** if it is not already selected. The information at the bottom of the dialog box indicates that preselected default field output requests have been made for this step.
-
On the right side of the dialog box, click **Edit** to change the field output requests. In the **Edit Field Output Request** dialog box that appears:
-
Click the arrow next to **Stresses** to show the list of available stress output. Accept the default selection of stress components and invariants.
-
Under **Forces/Reactions**, make the following changes:
-
Toggle off concentrated force and moment output (CF).
-
Toggle on nodal forces due to element stresses (NFORC).
-
Toggle off **Strains** and **Contact**.
-
Accept the default **Displacement/Velocity/Acceleration** output.
-
Click **OK**, and click **Dismiss** to close the **Field Output Requests Manager**.
Note:&nbsp;
The option **Exterior only** in the **Edit Field Output Request** dialog box can be used to restrict field output to nodes and elements that belong to the exterior of three-dimensional elements in a model; this option reduces the size of the output database file.
-
Delete all history output requests. In the Model Tree, click mouse button 3 on the **History Output Requests** container and select **Manager** to open the **History Output Requests Manager**. In the **History Output Requests Manager**, select the cell labeled `Created` in the column labeled **LugLoad** if it is not already selected. At the bottom of the dialog box, click **Delete** and click **Yes** in the warning dialog box that appears. Click **Dismiss** to close the **History Output Requests Manager**.
**Prescribing boundary conditions and applied loads**
In this model the left-hand end of the connecting lug needs to be constrained in all three directions. This region is where the lug is attached to its parent structure (see [Figure 4&#8211;18](ch04s03.html#gss-lug-bcregion-c)). In Abaqus/CAE boundary conditions are applied to geometric regions of a part rather than to the finite element mesh itself. This association between boundary conditions and part geometry makes it very easy to vary the mesh without having to respecify the boundary conditions. The same holds true for load definitions.
**Figure 4&#8211;18** Built-in end of the connecting lug.
../graphics/gss-lug-bcregion-c.png
**To prescribe boundary conditions:**
-
In the Model Tree, double-click the **BCs** container to prescribe boundary conditions on the model. In the **Create Boundary Condition** dialog box that appears, name the boundary condition `Fix left end`, and select `LugLoad` as the step in which it will be applied (since it is a fixed condition, it can be applied either in the initial step or the analysis step; here we choose the analysis step for convenience). Accept **Mechanical** as the category and `Symmetry/Antisymmetry/Encastre` as the type. Click **Continue**.
-
You may need to rotate the view to facilitate your selection in the following steps. Select **View**../images/arrow.gif**Rotate** from the main menu bar (or use the ../graphics/ico_viewRotate.png tool from the **View Manipulation** toolbar) and drag the cursor over the virtual trackball in the viewport. The view rotates interactively; try dragging the cursor inside and outside the virtual trackball to see the difference in behavior. Click mouse button 2 to exit the rotate view tool before proceeding.
-
Select the left end of the lug (indicated in [Figure 4&#8211;18](ch04s03.html#gss-lug-bcregion-c)) using the cursor. Click **Done** in the prompt area when the appropriate region is highlighted in the viewport, and toggle on **ENCASTRE** in the **Edit Boundary Condition** dialog box that appears. Click **OK** to apply the boundary condition.
Arrows appear on the face indicating the constrained degrees of freedom. The encastre boundary condition constrains all active structural degrees of freedom in the region specified; after the part is meshed and the job is created, this constraint will be applied to all the nodes that occupy the region.
The lug carries a pressure of 50 MPa distributed around the bottom half of the hole. To apply the load correctly, however, the part must first be partitioned (i.e., divided) so that the hole is composed of two regions: a top half and a bottom half.
You use the Partition toolset to divide a part or assembly into regions. Partitioning is used for many reasons; it is commonly used for the purposes of defining material boundaries, indicating the location of loads and constraints (as in this example), and refining the mesh. An example of the use of partitioning for meshing purposes is discussed in the next section. For more information on partitioning, see Chapter 70, &#8220;The Partition toolset,&#8221; of the Abaqus/CAE User's Guide.
Dependent part instances cannot be modified at the assembly level (e.g., they cannot be partitioned in an assembly-level module). The reason for this restriction is that all dependent instances of a part must have identical geometry so they can share the same mesh topology as the original part. Thus, any change to a dependent part instance has to be made to the original part itself (i.e., at the part level). In contrast, independent part instances may be partitioned at the assembly level. In this example a dependent part instance (the default) was created; the corresponding partitioning instructions follow.
**To partition a dependent part instance:**
-
In the Model Tree, double-click the **Lug** item in the **Parts** container to make it current.
-
Use the **Partition Cell: Define Cutting Plane** tool ../graphics/ico_ptnCellCuttingPlane.png to divide the part in half. Use the **3 Points** method to define the cutting plane. When you are prompted to select a point, Abaqus/CAE highlights the points you can select: vertices, datum points, edge midpoints, or arc centers. In this model the points used to define the cutting plane are indicated in [Figure 4&#8211;19](ch04s03.html#gss-lug-partit1-c). Again, you may need to rotate the view to facilitate your selection.
**Figure 4&#8211;19** Points used to define the cutting plane.
../graphics/gss-lug-partit1-c-nls.png
-
Click **Create Partition** in the prompt area after you have finished selecting the points.
**To apply a pressure load:**
-
In the Model Tree, double-click the **Loads** container to prescribe the pressure load. In the **Create Load** dialog box that appears, name the load `Pressure load` and select `LugLoad ` as the step in which it will be applied. Select **Mechanical** as the category and **Pressure** as the type. Click **Continue**.
-
Select the surface associated with the bottom half of the hole using the cursor; the region is highlighted in [Figure 4&#8211;20](ch04s03.html#gss-lug-press-c). When the appropriate surface is selected, click **Done** in the prompt area.
**Figure 4&#8211;20** Surface to which pressure will be applied.
../graphics/gss-lug-press-c.png
-
Specify a uniform pressure of `5.0E7` in the **Edit Load** dialog box, accept the default **Amplitude**, and click **OK** to apply the load.
Arrows appear on the bottom half of the hole indicating the applied load.
**Designing the mesh: partitioning and creating the mesh**
You need to consider the type of element that will be used before you start building the mesh for a particular problem. For example, a suitable mesh design that uses quadratic elements may very well be unsuitable if you change to linear, reduced-integration elements. For this example use 20-node hexahedral elements with reduced integration (C3D20R). Once you have selected the element type, you can design the mesh for the connecting lug. The most important decision regarding the mesh design for this example is how many elements to use around the circumference of the lug's hole. A possible mesh for the connecting lug is shown in [Figure 4&#8211;21](ch04s03.html#gss-lug-mesh-c).
**Figure 4&#8211;21** Suggested mesh of C3D20R elements for the connecting lug model.
../graphics/gss-lug-mesh-c.png
Another thing to consider when designing a mesh is the type of results you want from the simulation. The mesh in [Figure 4&#8211;21](ch04s03.html#gss-lug-mesh-c) is rather coarse and, therefore, unlikely to yield accurate stresses. Four quadratic elements per 90 is the minimum number that should be considered for a problem such as this one; using twice that many is recommended to obtain reasonably accurate stress results. However, this mesh should be adequate to predict the overall level of deformation in the lug under the applied loads, which is what you were asked to determine. The influence of increasing the mesh density used in this simulation is discussed in [&#8220;Mesh convergence,&#8221;  Section 4.4](ch04s04.html).
Abaqus/CAE offers a variety of meshing techniques to mesh models of different topologies. The different meshing techniques provide varying levels of automation and user control. The following three types of mesh generation techniques are available:
**Structured meshing**
Structured meshing applies preestablished mesh patterns to particular model topologies. Complex models must generally be partitioned into simpler regions to use this technique.
**Swept meshing**
Swept meshing extrudes an internally generated mesh along a sweep path or revolves it around an axis of revolution. Like structured meshing, swept meshing is limited to models with specific topologies and geometries.
**Free meshing**
The free meshing technique is the most flexible meshing technique. It uses no preestablished mesh patterns and can be applied to almost any model shape.
**Bottom-up meshing**
You use the bottom-up meshing technique to create a hexahedral or hex-dominated mesh on a solid region that is unmeshable or difficult to mesh using the automated top-down meshing techniques. Bottom-up meshing is a manual process that allows you to select the method and parameters that Abaqus/CAE uses to build up a solid mesh of hexahedral elements. Bottom-up meshing is not discussed in any of the examples in this guide.
When you enter the Mesh module, Abaqus/CAE color codes regions of the model according to the methods it will use to generate a mesh:
-
Green indicates that a region can be meshed using structured methods.
-
Yellow indicates that a region can be meshed using sweep methods.
-
Pink indicates that a region can be meshed using the free method.
-
Tan indicates that the region can be meshed using the bottom-up method.
-
Orange indicates that a region cannot be meshed using the default element shape assignment and must be partitioned further.
Dependent part instances are colored blue at the assembly level. You must switch to a part-level view to mesh a dependent part instance.
In this problem you will create a structured mesh. You will find that the model must first be partitioned further to use this mesh technique. After the partitions have been created, a global part seed will be assigned and the mesh will be created.
**To partition the lug:**
-
In the Model Tree,  expand the **Lug** item underneath the **Parts** container and double-click **Mesh** in the menu that appears.
The part is colored yellow initially, indicating that with the default set of mesh controls, a hexahedral mesh can be created only using a swept mesh technique. Additional cell partitions are required to permit structured meshing. Two partitions will be created. The first partition permits structured meshing to be used, and the second improves the overall quality of the mesh.
Note:&nbsp;
The ** Object** field that appears in the context bar automatically displays the part so that you can partition the geometry directly within the Mesh module. The ability to switch between individual parts and the model assembly within the same module is available only in the Mesh module. This feature allows you to partition both dependent and independent part instances in the same module for the purpose of meshing. In all other modules, partitioning must be done strictly at the part level for dependent instances (as was done earlier when the pressure load was applied) or at the assembly level for independent part instances.
-
Partition both regions of the lug vertically by defining a cutting plane through the three points shown in [Figure 4&#8211;22](ch04s03.html#gss-lug-partit2-c) (use **[Shift]****+Click** to select both regions simultaneously).
**Figure 4&#8211;22** First partition to permit structured meshing.
../graphics/gss-lug-partit2-c.png
-
Select **Tools**../images/arrow.gif**Datum** from the main menu bar, and create a datum point 0.075 m from the left end of the lug (as shown in [Figure 4&#8211;23](ch04s03.html#gss-lug-partit3-c)) using the **Offset from point** method.
**Figure 4&#8211;23** Second partition to improve the mesh quality.
../graphics/gss-lug-partit3-c-nls.png
-
Create the second vertical partition by using the **Point &amp; Normal** method to define a cutting plane that is through the datum point you just created and normal to the centerline of the lug (as shown in [Figure 4&#8211;23](ch04s03.html#gss-lug-partit3-c)).
The partitioned lug appears as in [Figure 4&#8211;24](ch04s03.html#gss-lug-partit4-c).
**Figure 4&#8211;24** Final partitioned lug.
../graphics/gss-lug-partit4-c.pngAfter you have partitioned the lug, all part regions should be colored green, which (based on the current mesh controls) indicates structured hexahedral element meshing will be used everywhere.
**To assign a global part seed and create the mesh:**
-
From the main menu bar, select **Seed**../images/arrow.gif**Part**, and specify a target global element size of `0.007`. Seeds appear on all the edges.
-
From the main menu bar, select **Mesh**../images/arrow.gif**Element Type** to choose the element type for the part. Because of the partitions you have created, the part is now composed of several regions.
-
Use the cursor to draw a box around the entire part and, thus, select all regions of the part. Click **Done** in the prompt area.
-
In the **Element Type** dialog box that appears, select the **Standard** element library, **3D Stress** family, **Quadratic** geometric order, and **Hex**, **Reduced integration** element. Click **OK** to accept the choice of C3D20R as the element type.
Note:&nbsp;
If you are using the Abaqus Student Edition, using second-order elements with a global seed size of 0.007 results in a mesh that exceeds the model size limits of the product. Either use first-order elements (C3D8R) with a global seed size of 0.007 or second-order elements with a global seed size of 0.01.
-
From the main menu bar, select **Mesh**../images/arrow.gif**Part**. Click **Yes** in the prompt area to mesh the part instance.
**Creating, running, and monitoring a job**
At this point the only task remaining to complete the model is defining the job. The job can then be submitted from within Abaqus/CAE and the solution progress monitored interactively.
Before continuing, rename the model to `Elastic` by clicking mouse button 3 on **Model-1** in the Model Tree and selecting **Rename** from the menu that appears. This model will later form the basis of the model used in the lug example discussed in [Chapter 10, &#8220;Materials](ch10.html).&#8221;
**To create a job:**
-
In the Model Tree, double-click the **Jobs** container to create a job. Name the job `Lug`, and click **Continue**.
-
In the **Edit Job** dialog box, enter the following description: `Linear Elastic Steel Connecting Lug`.
-
Accept the default job settings, and click **OK**.
Save your model in a model database file named `Lug.cae`.
**To run the job:**
-
In the Model Tree, click mouse button 3 on the job named **Lug** and select **Submit** to submit your job for analysis.
A dialog box appears to warn you that history output has not been requested for the **LugLoad** step. Click **Yes** to continue with the job submission.
-
In the Model Tree, click mouse button 3 on the job named **Lug** and select **Monitor** from the menu that appears to open the job monitor.
At the top of the dialog box, a summary of the solution progress is included. This summary is updated continuously as the analysis progresses. Any errors and/or warnings that are encountered during the analysis are noted in the appropriate tabbed pages. If any errors are encountered, correct the model and rerun the simulation. Be sure to investigate the cause of any warning messages and take appropriate action; recall that some warning messages can be ignored safely while others require corrective action.
-
When the job has completed, click **Dismiss** to close the job monitor.
4.3.2&nbsp;Postprocessing&#8212;visualizing the results
In the Model Tree, click mouse button 3 on the job named **Lug** and select **Results** to enter the Visualization module and automatically open the output database (`.odb`) file created by this job. Alternatively, from the **Module** list located in the context bar, select **Visualization** to enter the Visualization module; open the `.odb` file by selecting **File**../images/arrow.gif**Open** from the main menu bar and double-clicking on the appropriate file.
**Plotting the deformed shape**
From the main menu bar, select **Plot**../images/arrow.gif**Deformed Shape**; or use the ../graphics/ico_plotDeformed.png tool in the toolbox. [Figure 4&#8211;25](ch04s03.html#gsa-displacedshape-c) displays the deformed model shape at the end of the analysis. What is the displacement magnification level?
**Figure 4&#8211;25** Deformed model shape of connecting lug (shaded).
../graphics/gss-displacedshape-c-nls.png
**Changing the view**
The default view is isometric. You can change the view using the options in the **View** menu or the view tools in the **View Manipulation** toolbar. You can also specify a view by entering values for rotation angles, viewpoint, zoom factor, or fraction of viewport to pan. Direct view manipulation is also available using the 3D compass.
**To manipulate the view using the 3D compass:**
-
Click and drag one of the straight axes of the 3D compass to pan along an axis.
-
Click and drag any of the quarter-circular faces on the 3D compass to pan along a plane.
-
Click and drag one of the three arcs along the perimeter of the 3D compass to rotate the model about the axis that is perpendicular to the plane containing the arc.
-
Click and drag the free rotation handle (the point at the top of the 3D compass) to rotate the model freely about its pivot point.
-
Click the label for any of the axes on the 3D compass to select a predefined view (the selected axis is perpendicular to the plane of the viewport).
-
Double-click anywhere on the 3D compass to specify a view.
Most of the views in this guide are specified directly. This is to allow you to confirm the state of your model by checking against the images in the guide. You are encouraged, however, to practice using the above methods to manipulate your views as you deem fit.
**To specify the view:**
-
From the main menu bar, select **View**../images/arrow.gif**Specify** (or double-click the 3D compass).
The **Specify View** dialog box appears.
-
From the list of available methods, select **Viewpoint**.
In the **Viewpoint** method, you enter three values representing the *X*-, *Y*-, and *Z*-position of an observer. You can also specify an up vector. Abaqus positions your model so that this vector points upward.
-
Enter the *X*-, *Y*-, and *Z*-coordinates of the viewpoint vector as `1, 1, 3` and the coordinates of the up vector as `0, 1, 0`.
-
Click **OK**.
Abaqus/CAE displays your model in the specified view, as shown in [Figure 4&#8211;26](ch04s03.html#gss-shaded-plot-c).
**Figure 4&#8211;26** Deformed model shape viewed from specified viewpoint.
../graphics/gss-shaded-plot-c-nls.png
**Visible edges**
Several options are available for choosing which edges will be visible in the model display. The previous plots show all exterior edges of the model; [Figure 4&#8211;27](ch04s03.html#gss-wireframe-c) displays only feature edges.
**Figure 4&#8211;27** Deformed shape with only feature edges visible.
../graphics/gss-wireframe-c-nls.png
**To display only feature edges:**
-
From the main menu bar, select **Options**../images/arrow.gif**Common**.
The **Common Plot Options** dialog box appears.
-
Click the **Basic** tab if it is not already selected.
-
From the **Visible Edges** options, choose **Feature edges**.
-
Click **Apply**.
The deformed plot in the current viewport changes to display only feature edges, as shown in [Figure 4&#8211;27](ch04s03.html#gss-wireframe-c).
**Render style**
A shaded plot is a filled plot in which a lightsource appears to be directed at the model. This is the default render style and can be very useful when viewing complex three-dimensional models. Three other render styles provide additional display options: wireframe, hidden line, and filled. You can select a render style from the **Common Plot Options** dialog box or from the tools on the **Render Style** toolbar: wireframe ../graphics/ico_displayWire.png, hidden line ../graphics/ico_displayHidden.png, filled ../graphics/ico_displayFilled.png, and shaded ../graphics/ico_displayShaded.png. To display the wireframe plot shown in [Figure 4&#8211;28](ch04s03.html#gss-wireframe-all-c), select **Exterior edges** in the **Common Plot Options** dialog box, click **OK** to close the dialog box, and select wireframe plotting by clicking the ../graphics/ico_displayWire.png tool. All subsequent plots will be displayed in the wireframe render style until you select another render style.
**Figure 4&#8211;28** Wireframe plot.
../graphics/gss-wireframe-all-c-nls.png
A wireframe model showing internal edges can be visually confusing for complex three-dimensional models. You can use the other render style tools to select the hidden line and filled render styles, shown in [Figure 4&#8211;29](ch04s03.html#gss-lineplot-c) and [Figure 4&#8211;30](ch04s03.html#gss-elem-plot-c), respectively. These render styles are more useful when viewing complex three-dimensional models.
**Figure 4&#8211;29** Hidden line plot.
../graphics/gss-lineplot-c-nls.png
**Figure 4&#8211;30** Filled element plot.
../graphics/gss-elem-plot-c-nls.png
**Contour plots**
Contour plots display the variation of a variable across the surface of a model. You can create filled or shaded contour plots of field output results from the output database.
**To generate a contour plot of the Mises stress:**
-
From the main menu bar, select **Plot**../images/arrow.gif**Contours**../images/arrow.gif**On Deformed Shape**.
The filled contour plot shown in [Figure 4&#8211;31](ch04s03.html#gss-mises-filled-v) appears.
The Mises stress, `S Mises`, indicated in the legend title is the default variable chosen by Abaqus for this analysis. You can select a different variable to plot.
**Figure 4&#8211;31** Filled contour plot of Mises stress.
../graphics/gss-mises-filled-c-nls.png
-
From the main menu bar, select **Result**../images/arrow.gif**Field Output**.
The **Field Output** dialog box appears; by default, the **Primary Variable** tab is selected.
-
From the list of available output variables, select a new variable to plot.
-
Click **OK**.
The contour plot in the current viewport changes to reflect your selection.
Tip:&nbsp;
You can also use the **Field Output** toolbar, located above the viewport, to change the displayed field output variable. For more information, see &#8220;Using the field output toolbar,&#8221;  Section 42.5.2 of the Abaqus/CAE User's Guide.
Abaqus/CAE offers many options to customize contour plots. To see the available options, click the **Contour Options** ../graphics/ico_plotContourOptions.png tool in the toolbox. By default, Abaqus/CAE automatically computes the minimum and maximum values shown in your contour plots and evenly divides the range between these values into 12 intervals. You can control the minimum and maximum values Abaqus/CAE displays (for example, to examine variations within a fixed set of bounds), as well as the number of intervals.
**To generate a customized contour plot:**
-
In the **Basic** tabbed page of the **Contour Plot Options** dialog box, drag the **Contour Intervals** slider to change the number of intervals to nine.
-
In the **Limits** tabbed page of the **Contour Plot Options** dialog box, choose **Specify** beside **Max**; then enter a maximum value of `400E+6`.
-
Choose **Specify** beside **Min**; then enter a minimum value of `60E+6`.
-
Click **OK**.
Abaqus/CAE displays your model with the specified contour option settings, as shown in [Figure 4&#8211;32](ch04s03.html#gss-mises-custom-v) (this figure shows Mises stress; your plot will show whichever output variable you have chosen). These settings remain in effect for all subsequent contour plots until you change them or reset them to their default values.
**Figure 4&#8211;32** Customized plot of Mises stress.
../graphics/gss-mises-custom-c-nls.png
**Displaying contour results on interior surfaces**
You can cut your model such that interior surfaces are made visible. For example, you may want to examine the stress distribution in the interior of a part. View cuts can be created for such purposes. Here, a simple planar cut is made through the lug to view the Mises stress distribution through the thickness of the part.
Note:&nbsp;
View cuts are also available throughout the other modules of Abaqus/CAE. They are illustrated here for convenience.
**To create a view cut:**
-
From the main menu bar, select **Tools**../images/arrow.gif**View Cut**../images/arrow.gif**Create**.
-
In the dialog box that appears, accept the default name and shape. Enter `0,0,0` as the **Origin** of the plane (i.e., a point through which the plane will pass), `1,0,1` as the **Normal axis** to the plane, and `0,1,0` as **Axis 2** of the plane.
-
Click **OK** to close the dialog box and to make the view cut.
The view appears as shown in [Figure 4&#8211;33](ch04s03.html#gsa-cutting-plane).
**Figure 4&#8211;33** Mises stress through the lug thickness.
../graphics/gsa-cutting-plane-nls.pngFrom the main menu bar, select **Tools**../images/arrow.gif**View Cut**../images/arrow.gif**Manager** to open the **View Cut Manager**. By default, the regions on and below the cut are displayed (as indicated by the check marks beneath the **on cut** ../graphics/visG_CutOn.png and **below cut** ../graphics/visG_CutBelow.png symbols). To translate or rotate the cut, choose **Translate** or **Rotate** from the list of available motions and enter a value or drag the slider at the bottom of the **View Cut Manager**.
-
To view the full model again, toggle off **Cut-4** in the **View Cut Manager**.
For more information on view cuts, see Chapter 80, &#8220;Cutting through a model,&#8221; of the Abaqus/CAE User's Guide.
**Maximum and minimum values**
The maximum and minimum values of a variable in a model can be determined easily.
**To display the minimum and maximum values of a contour variable:**
-
From the main menu bar, select **Viewport**../images/arrow.gif**Viewport Annotation Options**; then click the **Legend** tab in the dialog box that appears.
The **Legend** options become available.
-
Toggle on **Show min/max values**.
-
Click **OK**.
The contour legend changes to report the minimum and maximum contour values.
One of the goals of this example is to determine the deflection of the lug in the negative 2-direction. You can contour the displacement component of the lug in the 2-direction to determine its peak displacement in the vertical direction as follows. In the **Contour Plot Options** dialog box, click **Defaults** to reset the minimum and maximum contour values and the number of intervals to their default values before proceeding.
**To contour the displacement of the connecting lug in the 2-direction:**
-
From the list of variable types on the left side of the **Field Output** toolbar, select **Primary** if it is not already selected.
Tip:&nbsp;
You can click ../graphics/ico_fieldOutput.png on the left side of the **Field Output** toolbar to make your selections from the **Field Output** dialog box instead of the toolbar. If you use the dialog box, you must click **Apply** or **OK** for Abaqus/CAE  to display your selections in the viewport.
-
From the list of available output variables in the center of the toolbar, select output variable&nbsp;**U**.
-
From the list of available components and invariants on the right side of the **Field Output** toolbar, select **U2**.
What is the maximum displacement value in the negative 2-direction?
**Displaying a subset of the model**
By default, Abaqus/CAE displays your entire model; however, you can choose to display a subset of your model called a display group. This subset can contain any combination of part instances, geometry (cells, faces, or edges), elements, nodes, and surfaces from the current model or output database. For the connecting lug model you will create a display group consisting of the elements at the bottom of the hole. Since a pressure load was applied to this region, an internal set is created by Abaqus that can be used for visualization purposes.
**To display a subset of the model:**
-
In the Results Tree, double-click ** Display Groups**.
The **Create Display Group** dialog box opens.
-
From the **Item** list, select **Elements**. From the **Method** list, select **Internal sets**.
Once you have selected these items, the list on the right-hand side of the **Create Display Group** dialog box shows the available selections.
-
Using this list, identify the set that contains the elements at the bottom of the hole. Toggle on **Highlight items in viewport** below the list so that the outlines of the elements in the selected set are highlighted in red.
-
When the highlighted set corresponds to the group of elements at the bottom of the hole, click **Replace** ../graphics/ico_displayGroupReplace.png to replace the current model display with this element set.
Abaqus/CAE displays the specified subset of your model.
-
Click **Dismiss** to close the **Create Display Group** dialog box.
When creating an Abaqus model, you may want to determine the face labels for a solid element. For example, you may want to verify that the correct load ID was used when applying pressure loads or when defining surfaces for contact. In such situations you can use the Visualization module to display the mesh after you have run a **datacheck** analysis that creates an output database file.
**To display the face identification labels and element numbers on the undeformed model shape:**
-
From the main menu bar, select **Options**../images/arrow.gif**Common**.
The **Common Plot Options** dialog box appears.
-
Set the render style to filled; all visible element edges will be displayed for convenience.
-
Toggle on **Filled** under **Render Style**.
-
Toggle on **All edges** under **Visible Edges**.
-
Click the **Labels** tab, and toggle on **Show element labels** and **Show face labels**.
-
Click **Apply** to apply the plot options.
-
From the main menu bar, select **Plot**../images/arrow.gif**Undeformed Shape**; or use the ../graphics/ico_plotUndeformed.png tool in the toolbox.
Abaqus/CAE displays the element and face identification labels in the current display group.
-
Click **Defaults** in the **Common Plot Options** dialog box to restore the default plot settings and then click **OK** to close the dialog box.
**Displaying a free body cut**
You can define a free body cut to view the resultant forces and moments transmitted across a selected surface of a model. Force vectors are displayed with a single arrowhead and moment vectors with a double arrowhead.
**To create a free body cut:**
-
To display the entire model in the viewport, select **Tools**../images/arrow.gif**Display Group**../images/arrow.gif**Plot**../images/arrow.gif**All** from the main menu bar.
-
From the main menu bar, select **Tools**../images/arrow.gif**Free Body Cut**../images/arrow.gif**Manager**.
-
Click **Create** in the **Free Body Cut Manager**.
-
From the dialog box that appears, select **3D element faces** as the **Selection method** and click **Continue**.
-
In the **Free Body Cross-Section** dialog box, select **Surfaces** as the **Item** and **Pick from viewport** as the **Method**.
-
In the prompt area, set the selection method to **by angle** and accept the default angle.
-
Select the surface, highlighted in [Figure 4&#8211;34](ch04s03.html#gss-fbd-face), to define the free body cut cross-section.
-
From the **Selection** toolbar, toggle off the **Select the Entity Closest to the Screen** tool ../graphics/ico_filterVisible.png and ensure that the **Select From All Entities** tool ../graphics/ico_filterBothIntExt.png is selected.
-
As you move the cursor in the viewport, Abaqus/CAE highlights all of the potential selections and adds ellipsis marks (...) next to the cursor arrow to indicate an ambiguous selection. Position the cursor so that one of the faces of the desired surface is highlighted, and click to display the first surface selection.
**Figure 4&#8211;34** The free body cross-section.
../graphics/gss-fbd-face.png
-
Use the **Next** and **Previous** buttons to cycle through the possible selections until the appropriate vertical surface is highlighted, and click **OK**.
-
Click **Done** in the prompt area to indicate your selection is complete. Click **OK** in the **Free Body Cross-Section** dialog box.
-
In the **Edit Free Body Cut** dialog box, accept the default settings for the **Summation Point** and the **Component Resolution**. Click **OK** to close the dialog box.
-
Click **Options** in the **Free Body Cut Manager**.
-
From the **Free Body Plot Options** dialog box, select the **Force** tab in the **Color &amp; Style** tabbed page. Click the resultant color sample ../graphics/usi-colorsample.png to change the color of the resultant force arrow.
-
Once you have selected a new color for the resultant force arrow, click **OK** in the **Free Body Plot Options** dialog box and click **Dismiss** in the **Free Body Cut Manager**.
The free body cut is displayed in the viewport, as shown in [Figure 4&#8211;35](ch04s03.html#gss-fbd-result).
**Figure 4&#8211;35** Free body cut displayed on the connecting lug.
../graphics/gss-fbd-result.png
**Generating tabular data reports for subsets of the model**
Tabular output data can be generated for selected regions of the model very easily using Abaqus/CAE. This is achieved using display groups in conjunction with the report generation feature. For the connecting lug problem we will generate the following tabular data reports:
-
Stresses in the elements at the built-in end of the lug (to determine the maximum stress in the lug)
-
Reaction forces at the built-in end of the lug (to check that the reaction forces at the constraints balance the applied loads)
-
Vertical displacements at the bottom of the hole (to determine the deflection of the lug when the load is applied)
Since we did not create geometry sets corresponding to these regions, each of these reports will be generated using display groups whose contents are selected in the viewport. Thus, begin by creating and saving display groups for each region of interest.
**To create and save a display group containing the elements at the built-in end:**
-
In the Results Tree, double-click ** Display Groups**.
-
Choose **Elements** from the **Item** list and **Pick from viewport** as the selection method.
-
Restore the option to select entities closest to the screen.
-
In the prompt area, set the selection method to **by angle**; and click the built-in face of the lug. Click **Done** when all the elements at the built-in face of the lug are highlighted in the viewport. In the **Create Display Group** dialog box, click **Save Selection As**. Save the display group as `built-in elements`.
**To create and save a display group containing the nodes at the built-in end:**
-
In the **Create Display Group** dialog box, choose **Nodes** from the **Item** list and **Pick from viewport** as the selection method.
-
In the prompt area, set the selection method to **by angle**; and click the built-in face of the lug. Click **Done** when all the nodes on the built-in face of the lug are highlighted in the viewport. In the **Create Display Group** dialog box, click **Save Selection As**. Save the display group as `built-in nodes`.
**To create and save a display group containing the nodes at the bottom of the hole:**
-
In the **Create Display Group** dialog box, click **Edit Selection** to select a different group of nodes.
-
In the prompt area, set the selection method to **individually**; and select the nodes at the bottom of the hole in the lug, as indicated in [Figure 4&#8211;36](ch04s03.html#gss-lug-bottomnodes-c). Click **Done** when all the nodes on the bottom of the hole are highlighted in the viewport. In the **Create Display Group** dialog box, click **Save Selection As**. Save the display group as `nodes at hole bottom`.
**Figure 4&#8211;36** Nodes in display group `nodes at hole bottom`.
../graphics/gss-lug-bottomnodes-c-nls.png
Now generate the reports.
**To generate field data reports:**
-
In the Results Tree, click mouse button 3 on **built-in elements** underneath the ** Display Groups** container. In the menu that appears, select **Plot** to make it the current display group.
-
From the main menu bar, select **Report**../images/arrow.gif**Field Output**.
-
In the **Variable** tabbed page of the **Report Field Output** dialog box, accept the default position labeled **Integration Point**. Click the triangle next to **S: Stress components** to expand the list of available variables. From this list, select **Mises** and the six individual stress components: **S11**, **S22**, **S33**, **S12**, **S13**, and **S23**.
-
In the **Setup** tabbed page, name the report `Lug.rpt`. In the **Data** region at the bottom of the page, toggle off **Column totals**.
-
Click **Apply**.
-
In the Results Tree, click mouse button 3 on **built-in nodes** underneath the ** Display Groups** container. In the menu that appears, select **Plot** to make it the current display group. (To see the nodes, toggle on ** Show node symbols** in the **Common Plot Options** dialog box.)
-
In the **Variable** tabbed page of the **Report Field Output** dialog box, change the position to **Unique Nodal**. Toggle off **S: Stress components**, and select **RF1**, **RF2**, and **RF3** from the list of available **RF: Reaction force** variables.
-
In the **Data** region at the bottom of the **Setup** tabbed page, toggle on **Column totals**.
-
Click **Apply**.
-
In the Results Tree, click mouse button 3 on **nodes at hole bottom** underneath the ** Display Groups** container. In the menu that appears, select **Plot** to make it the current display group.
-
In the **Variable** tabbed page of the **Report Field Output** dialog box, toggle off **RF: Reaction force**, and select **U2** from the list of available **U: Spatial displacement** variables.
-
In the **Data** region at the bottom of the **Setup** tabbed page, toggle off **Column totals**.
-
Click **OK**.
Open the file `Lug.rpt` in a text editor. A portion of the table of element stresses is shown below. The element data are given at the element integration points. The integration point associated with a given element is noted under the column labeled `Int Pt`. The bottom of the table contains information on the maximum and minimum stress values in this group of elements. The results indicate that the maximum Mises stress at the built-in end is approximately 330 MPa. Your results may differ slightly if your mesh is not identical to the one used here.```
Field Output Report
Source 1
---------
ODB: Lug.odb
Step: LugLoad
Frame: Increment      1: Step Time =    1.000
Loc 1 : Integration point values from source 1
Output sorted by column "Element Label".
Field Output reported at integration points for part: LUG-1
Element   Int      S.Mises        S.S11        S.S22        S.S33        S.S12
Label     Pt        @Loc 1       @Loc 1       @Loc 1       @Loc 1       @Loc 1
------------------------------------------------------------------------------
S.S13        S.S23
@Loc 1       @Loc 1
--------------------------
31     1    84.0567E+06  76.2075E+06   14.021E+06 -274.446E+03 -26.4339E+06
-159.756E+03  1.70193E+06
31     2    88.1108E+06  79.9769E+06  16.7815E+06  5.07167E+06 -30.8241E+06
3.045E+06  2.20251E+06
31     3    71.0378E+06  87.4511E+06  30.5433E+06  22.7759E+06 -11.8374E+06
17.114E+06  1.47033E+06
31     4    64.3978E+06  76.4473E+06  26.1412E+06  19.0617E+06 -18.6815E+06
7.36221E+06  411.436E+03
31     5    48.4688E+06  20.2162E+06  4.20669E+06  68.3536E+03 -25.8284E+06
-78.8286E+03  1.65403E+06
31     6    55.6407E+06  21.1693E+06  4.87661E+06  1.46182E+06 -30.2661E+06
796.514E+03   2.0911E+06
31     7    25.1732E+06  22.9107E+06  7.96147E+06  5.89815E+06 -10.1069E+06
4.55755E+06  1.45446E+06
31     8    32.8268E+06   19.928E+06  6.76018E+06  4.88587E+06 -16.9708E+06
1.9631E+06  378.549E+03
.
.
198     1    239.655E+06 -247.046E+06 -20.9897E+06 -13.4824E+06  -38.331E+06
7.48079E+06  -1.1505E+06
198     2    237.839E+06 -235.534E+06 -13.8995E+06  2.83029E+06  -33.891E+06
-1.25472E+06 -1.57941E+06
198     3    190.507E+06 -228.049E+06 -53.1236E+06 -51.1938E+06 -37.0096E+06
20.3556E+06 -419.555E+03
198     4    219.144E+06 -259.016E+06 -65.4028E+06  -61.292E+06 -30.1529E+06
48.227E+06 -2.60239E+06
198     5    322.607E+06 -330.074E+06 -2.82071E+06 -14.7802E+06 -12.9162E+06
9.1461E+06 -189.416E+03
198     6    320.169E+06 -316.345E+06  1.80108E+06  4.87007E+06 -9.15387E+06
-4.10769E+06 -1.03378E+06
198     7    300.073E+06 -364.931E+06 -95.1687E+06 -93.2852E+06 -69.7659E+06
26.8241E+06 -343.386E+03
198     8    331.098E+06 -399.004E+06 -109.695E+06 -104.075E+06 -62.7377E+06
64.3938E+06 -2.63754E+06
Minimum      25.1732E+06 -399.004E+06 -109.695E+06 -122.144E+06 -72.2982E+06
-64.4051E+06 -2.63899E+06
At Element        33          196          198          197           98
99           99
Int Pt         8            7            8            8            4
4            4
Maximum      331.159E+06  399.073E+06  109.719E+06  122.172E+06 -9.15387E+06
64.4051E+06    2.639E+06
At Element        97           99           99           98          196
97           97
Int Pt         3            4            4            4            5
3            3
```
How does the maximum value of Mises stress compare to the value reported in the contour plot generated earlier? Do the two maximum values correspond to the same point in the model? The Mises stresses shown in the contour plot have been extrapolated to the nodes, whereas the stresses written to the report file for this problem correspond to the element integration points. Therefore, the location of the maximum Mises stress in the report file is not exactly the same as the location of the maximum Mises stress in the contour plot. This difference can be resolved by requesting that stress output at the nodes (extrapolated from the element integration points and averaged over all elements containing a given node) be written to the report file. If the difference is large enough to be of concern, this is an indication that the mesh may be too coarse.
The table listing the reaction forces at the constrained nodes is shown below. The `Total` entry at the bottom of the table contains the net reaction force components for this group of nodes. The results confirm that the total reaction force in the 2-direction at the constrained nodes is equal and opposite to the applied load of 30 kN in that direction. ```
Field Output Report
Source 1
---------
ODB: Lug.odb
Step: LugLoad
Frame: Increment      1: Step Time =    1.000
Loc 1 : Nodal values from source 1
Output sorted by column "Node Label".
Field Output reported at nodes for part: LUG-1
Node          RF.RF1          RF.RF2          RF.RF3
Label          @Loc 1          @Loc 1          @Loc 1
----------------------------------------------------------------
3    -60.6106E-03        -118.486    -31.3131E-03
4    -60.6102E-03        -118.486     31.3133E-03
6         538.194         289.574         382.416
7         538.194         289.574        -382.416
11        -538.255         289.563        -382.329
.
.
1334     5.90186E+03         216.099     1.63004E+03
1336     6.60254E+03     1.81494E+03     -45.543E-06
1337     9.81613E+03         692.328        -791.954
1339     6.35335E+03      1.7276E+03        -331.533
1340     5.90186E+03         216.098    -1.63004E+03
Minimum           -9.81734E+03        -264.368    -1.63023E+03
At Node             953             258             950
Maximum            9.81613E+03     1.81556E+03     1.63022E+03
At Node            1337             951             956
Total    -912.953E-06     30.0000E+03    -46.7648E-06
```The table showing the displacements of the nodes along the bottom of the hole (listed below) indicates that the bottom of the hole in the lug has displaced about 0.3 mm. ```
Field Output Report
Source 1
---------
ODB: Lug.odb
Step: LugLoad
Frame: Increment      1: Step Time =    1.000
Loc 1 : Nodal values from source 1
Output sorted by column "Node Label".
Field Output reported at nodes for part: LUG-1
Node            U.U2
Label          @Loc 1
--------------------------------
23    -314.158E-06
24    -314.158E-06
143      -314.2E-06
144      -314.2E-06
1522    -314.163E-06
1526    -314.211E-06
1529    -314.163E-06
Minimum           -314.211E-06
At Node            1526
Maximum           -314.158E-06
At Node              23
```4.3.3&nbsp;Rerunning the analysis using Abaqus/Explicit
You will now evaluate the dynamic response of the lug when the same load is applied suddenly. Of special interest is the transient response of the lug. You will have to modify the model for the Abaqus/Explicit analysis. Before proceeding, copy the existing model to a new model named `Explicit`. Make all subsequent changes to the `Explicit` model  (you may want to collapse the **Elastic** model to avoid confusion). Before running the job you will need to add a density definition to the material model, change the step type, and change the element type. In addition, you should make modifications to the field output requests.
**To modify the model:**
-
Edit the material definition for **Steel** to include a mass density of `7800`.
-
Replace the static step named **LugLoad** with a dynamic, explicit step. Enter `Dynamic lug loading` as the step description, and enter `0.005` s for the time period of the step.
-
Edit the field output request named **F-Output-1**. In the **Edit Field Output Request** dialog box, enter `125` as the number of equally spaced intervals for saving output.
-
Accept the default history output request.
-
Change the element type used to mesh the lug. In the **Element Type** dialog box, select the **Explicit** element library, **3D Stress** family, and **Linear** geometric order. In addition, select enhanced hourglass control for the **Hex** shape. The selected element type is C3D8R.
-
Create and submit a job named **expLug** using the model named `Explicit`.
-
Monitor the progress of the job.
At the top of the **expLug Monitor** dialog box, a summary of the solution progress is included. This summary is updated continuously as the analysis progresses. Any errors and/or warnings that are encountered during the analysis are noted in the appropriate tabbed pages. If any errors are encountered, correct the model and rerun the simulation. Be sure to investigate the cause of any warning messages and take appropriate action; recall that some warning messages can be ignored safely while others require corrective action.
4.3.4&nbsp;Postprocessing the dynamic analysis results
In the static analysis performed with Abaqus/Standard you examined the deformed shape of the lug as well as stress and displacement output. For the Abaqus/Explicit analysis you can similarly examine the deformed shape, stresses, and displacements in the lug. Because transient dynamic effects may result from a sudden loading, you should also examine the time histories for internal and kinetic energy, displacement, and Mises stress.
Open the output database (`.odb`) file created by this job.
**Plotting the deformed shape**
From the main menu bar, select **Plot**../images/arrow.gif**Deformed Shape**; or use the ../graphics/ico_plotDeformed.png tool in the toolbox. [Figure 4&#8211;37](ch04s03.html#gsa-displaced-exp) displays the deformed model shape at the end of the analysis.
**Figure 4&#8211;37** Deformed model shape for the explicit analysis (shaded).
../graphics/gsa-displaced-exp-nls.pngAs discussed earlier, Abaqus/Explicit assumes large deformation theory by default; thus, the deformation scale factor is automatically set to 1. If the displacements are too small to be seen, scaling can be applied to aid the study of the response.
To see the vibrations in the lug more clearly, change the deformation scale factor to 50. In addition, animate the time history of the deformed shape of the lug and decrease the frame rate of the time history animation.
The time history animation of the deformed shape of the lug shows that the suddenly applied load induces vibrations in the lug. Additional insights about the behavior of the lug under this type of loading can be gained by plotting the kinetic energy, internal energy, displacement, and stress in the lug as a function of time. Some of the questions to consider are:
-
Is energy conserved?
-
Was large-displacement theory necessary for this analysis?
-
Are the peak stresses reasonable? Will the material yield?
**X&#8211;Y plotting**
X&#8211;Y plots can display the variation of a variable as a function of time. You can create X&#8211;Y plots from field and history output.
**To create X&#8211;Y plots of the internal and kinetic energy as a function of time:**
-
In the Results Tree, expand the **History Output** container underneath the output database named `expLug.odb`.
-
The list of all the variables in the history portion of the output database appears; these are the only history output variables you can plot.
From the list of available output variables, double-click **ALLIE** to plot the internal energy for the whole model.
Abaqus reads the data for the curve from the output database file and plots the graph shown in [Figure 4&#8211;38](ch04s03.html#gsa-lugexp-allie).
**Figure 4&#8211;38** Internal energy for the whole model.
../graphics/gsa-lugexp-allie-nls.png
-
Repeat this procedure to plot **ALLKE**, the kinetic energy for the whole model (shown in [Figure 4&#8211;39](ch04s03.html#gsa-lugexp-allke)).
**Figure 4&#8211;39** Kinetic energy for the whole model.
../graphics/gsa-lug-allke-nls.png
Both the internal energy and the kinetic energy show oscillations that reflect the vibrations of the lug. Throughout the simulation, kinetic energy is transformed into internal (strain) energy and vice-versa. Since the material is linear elastic, total energy is conserved. This can be seen by plotting `ETOTAL`, the total energy of the system, together with `ALLIE` and `ALLKE`. The value of `ETOTAL` is approximately zero throughout the course of the analysis. Energy balances in dynamic analysis are discussed further in [Chapter 9, &#8220;Nonlinear Explicit Dynamics](ch09.html).&#8221;
We will examine the nodal displacements at the bottom of the lug hole to evaluate the significance of geometrically nonlinear effects in this simulation.
**To generate a plot of displacement versus time:**
-
Plot the deformed shape of the lug. In the Results Tree, double-click ** XY Data**.
-
In the **Create XY Data** dialog box that appears, select **ODB field output** as the source and click **Continue**.
-
In the **XY Data from ODB Field Output** dialog box that appears, select **Unique Nodal** as the type of position from which the *X&#8211;Y* data should be read.
-
Click the arrow next to **U: Spatial displacement** and toggle on **U2** as the displacement variable for the *X&#8211;Y* data.
-
Select the **Elements/Nodes** tab. Choose **Pick from viewport** as the selection method for identifying the node for which you want *X&#8211;Y* data.
-
Click **Edit Selection**. In the viewport, select one of the nodes on the bottom of the hole as shown in [Figure 4&#8211;40](ch04s03.html#gsa-lugexp-node) (if necessary, change the render style to facilitate your selection). Click **Done** in the prompt area.
**Figure 4&#8211;40** Selected node at the bottom of the hole.
../graphics/gsa-lugexp-node.png
-
Click **Plot** in the **XY Data from ODB Field Output** dialog box to plot the nodal displacement as a function of time.
The history of the oscillation, as shown in [Figure 4&#8211;41](ch04s03.html#gsa-lugexp-nodaldisp), indicates that the displacements are small (relative to the structure's dimensions).
**Figure 4&#8211;41** Displacement of a node at the bottom of the hole.
../graphics/gsa-lug-nodaldisp.png
Thus, this problem could have been solved adequately using small-deformation theory. This would have reduced the computational cost of the simulation without significantly affecting the results. Nonlinear geometric effects are discussed further in [Chapter 8, &#8220;Nonlinearity](ch08.html).&#8221;
We are also interested in the stress history of the connecting lug. The area of the lug near the built-in end is of particular interest because the peak stresses expected to occur there may cause yielding in the material.
**To generate a plot of Mises stress versus time:**
-
Plot the deformed shape of the lug again.
-
Select the **Variables** tab in the **XY Data from ODB Field Output** dialog box. Deselect **U2** as the variable for the *X&#8211;Y* data plot.
-
Change the **Position** field to **Integration Point**.
-
Click the arrow next to **S: Stress components** and toggle on **Mises** as the stress variable for the *X&#8211;Y* data.
-
Select the **Elements/Nodes** tab. Choose **Pick from viewport** as the selection method for identifying the element for which you want X&#8211;Y data.
-
Click **Edit Selection**. In the viewport, select one of the elements near the built-in end of the lug as shown in [Figure 4&#8211;42](ch04s03.html#gsa-lugexp-elem). Click **Done** in the prompt area.
**Figure 4&#8211;42** Selected element near the built-in end of the lug (hidden).
../graphics/gsa-lugexp-elem.png
-
Click **Plot** in the **XY Data from ODB Field Output** dialog box to plot the Mises stress at the selected element as a function of time.
The peak Mises stress is on the order of 550 MPa, as shown in [Figure 4&#8211;43](ch04s03.html#gsa-lugexp-stresshist). This value is larger than the typical yield strength of steel. Thus, the material would have yielded before experiencing such a large stress state. Material nonlinearity is discussed further in [Chapter 10, &#8220;Materials](ch10.html).&#8221;
**Figure 4&#8211;43** Mises stress near the built-in end of the lug.
../graphics/gsa-lug-stresshist.png

## 4.4&nbsp;Mesh convergence

4.4&nbsp;Mesh convergence
It is important that you use a sufficiently refined mesh to ensure that the results from your Abaqus simulation are adequate. Coarse meshes can yield inaccurate results in analyses using implicit or explicit methods. The numerical solution provided by your model will tend toward a unique value as you increase the mesh density. The computer resources required to run your simulation also increase as the mesh is refined. The mesh is said to be converged when further mesh refinement produces a negligible change in the solution.
As you gain experience, you will learn to judge what level of refinement produces a suitable mesh to give acceptable results for most simulations. However, it is always good practice to perform a mesh convergence study, where you simulate the same problem with a finer mesh and compare the results. You can have confidence that your model is producing a mathematically accurate solution if the two meshes give essentially the same result.
Mesh convergence is an important consideration in both Abaqus/Standard and Abaqus/Explicit. The connecting lug will be used as an example of a mesh refinement study by further analyzing the connecting lug in Abaqus/Standard using four different mesh densities ([Figure 4&#8211;44](ch04s04.html#gsa-diff-mesh)). The number of elements used in each mesh is indicated in the figure.
**Figure 4&#8211;44** Different meshes for the connecting lug problem.
../graphics/gss-diff-mesh-nls.png
Note:&nbsp;
The meshes in [Figure 4&#8211;44](ch04s04.html#gsa-diff-mesh) can be obtained by further partitioning, as indicated in [Figure 4&#8211;45](ch04s04.html#gsa-diff-mesh-partitions), with appropriate mesh seeding.
**Figure 4&#8211;45** Additional partitions for the connecting lug.
../graphics/gsa-diff-mesh-partitions.png
We consider the influence of the mesh density on three particular results from this model:
-
The displacement of the bottom of the hole.
-
The peak Mises stress at the stress concentration on the bottom surface of the hole.
-
The peak Mises stress where the lug is attached to the parent structure.
The locations where the results are compared are shown in [Figure 4&#8211;46](ch04s04.html#gss-mises-annotated-c).
**Figure 4&#8211;46** Locations where results are compared in the mesh refinement study.
../graphics/gss-mises-annotated-c-nls.pngThe results for each of the four mesh densities are compared in [Table 4&#8211;3](ch04s04.html#gss-continuum-table-study), along with the CPU time required to run each simulation.
**Table 4&#8211;3** Results of mesh refinement study.
The coarse mesh predicts less accurate displacements at the bottom of hole, but the normal, fine, and very fine meshes all predict similar results. The normal mesh is, therefore, converged as far as the displacements are concerned. The convergence of the results is plotted in [Figure 4&#8211;47](ch04s04.html#gss-mesh-refinement-v).
**Figure 4&#8211;47** Convergence of results in mesh refinement study.
../graphics/gss-mesh-refinement-v-nls.png
All the results are normalized with respect to the values predicted by the coarse mesh. The peak stress on the bottom of the hole converges much more slowly than the displacements because stress and strain are calculated from the displacement gradients; thus, a much finer mesh is required to predict accurate displacement gradients than is needed to calculate accurate displacements.
Mesh refinement significantly changes the stress calculated at the attachment of the connecting lug; it continues to increase with continued mesh refinement. A stress singularity exists at the corner of the lug where it attaches to the parent structure. Theoretically the stress is infinite at this location; therefore, increasing the mesh density will not produce a converged stress value at this location. This singularity occurs because of the idealizations used in the finite element model. The connection between the lug and the parent structure has been modeled as a sharp corner, and the parent structure has been modeled as rigid. These idealizations lead to the stress singularity. In reality there probably will be a small fillet between the lug and the parent structure, and the parent structure will be deformable, not rigid. If the exact stress in this location is required, the fillet between the components must be modeled accurately (see [Figure 4&#8211;48](ch04s04.html#gss-fillet)) and the stiffness of the parent structure must also be considered.
**Figure 4&#8211;48** Idealizing a fillet as a sharp corner.
../graphics/gss-fillet-nls.png
It is common to omit small details like fillet radii from a finite element model to simplify the analysis and to keep the model size reasonable. However, the introduction of any sharp corner into a model will lead to a stress singularity at that location. This normally has a negligible effect on the overall response of the model, but the predicted stresses close to the singularity will be inaccurate.
For complex, three-dimensional simulations the available computer resources often dictate a practical limit on the mesh density that you can use. In this case you must use the results from the analysis carefully. Coarse meshes are often adequate to predict trends and to compare how different concepts behave relative to each other. However, you should use the actual magnitudes of displacement and stress calculated with a coarse mesh with caution.
It is rarely necessary to use a uniformly fine mesh throughout the structure being analyzed. You should use a fine mesh mainly in the areas of high stress gradients and use a coarser mesh in areas of low stress gradients or where the magnitude of the stresses is not of interest. For example, [Figure 4&#8211;49](ch04s04.html#gss-mesh-refine) shows a mesh that is designed to give an accurate prediction of the stress concentration at the bottom of the hole.
**Figure 4&#8211;49** Mesh refined around the hole.
../graphics/gss-mesh-refine.png
A fine mesh is used only in the region of high stress gradients, and a coarse mesh is used elsewhere. The results from an Abaqus/Standard simulation with this locally refined mesh are shown in [Table 4&#8211;4](ch04s04.html#gss-continuum-table-refine). This table shows that the results are comparable to those from the very fine mesh, but the simulation with the locally refined mesh required considerably less CPU time than the analysis with the very fine mesh.
**Table 4&#8211;4** Comparison of very fine and locally refined meshes.
You can often predict the locations of the highly stressed regions of a model&#8212;and, hence, the regions where a fine mesh is required&#8212;using your knowledge of similar components or with hand calculations. This information can also be gained by using a coarse mesh initially to identify the regions of high stress and then refining the mesh in these regions. The latter procedure is carried out easily using preprocessors like Abaqus/CAE where the complete numerical model (i.e., material properties, boundary conditions, loads, etc.) can be defined based on the geometry of the structure. It is simple to mesh the geometry coarsely for the initial simulation and then to refine the mesh in the appropriate regions, as indicated by the results from the coarse simulation.
Abaqus provides an advanced feature, called submodeling, that allows you to obtain more detailed (and accurate) results in a region of interest in the structure. The solution from a coarse mesh of the entire structure is used to &#8220;drive&#8221; a detailed local analysis that uses a fine mesh in this region of interest. (This topic is beyond the scope of this guide. See &#8220;Submodeling: overview,&#8221;  Section 10.2.1 of the Abaqus Analysis User's Guide, for further details.)

## 4.5&nbsp;Related Abaqus examples

4.5&nbsp;Related Abaqus examples
If you are interested in learning more about using continuum elements in Abaqus, you should examine the following problems:
-
&#8220;Geometrically nonlinear analysis of a cantilever beam,&#8221;  Section 2.1.2 of the Abaqus Benchmarks Guide
-
&#8220;Spherical cavity in an infinite medium,&#8221;  Section 2.2.4 of the Abaqus Benchmarks Guide
-
&#8220;Performance of continuum and shell elements for linear analysis of bending problems,&#8221;  Section 2.3.5 of the Abaqus Benchmarks Guide

## 4.6&nbsp;Suggested reading

4.6&nbsp;Suggested reading
The volume of literature that has been written on the finite element method and the applications of finite element analysis is enormous. In most of the remaining chapters of this guide, a list of suggested books and articles is provided so that you can explore the topics in more depth if you wish. While the advanced references will not be of interest to most users, they provide detailed theoretical information for the interested user.
**General texts on the finite element method**
-
NAFEMS Ltd., *A Finite Element Primer*, 1986.
-
Becker, E. B., G. F. Carey, and J. T. Oden, *Finite Elements: An Introduction,* Prentice-Hall, 1981.
-
Carey, G. F., and J. T. Oden, *Finite Elements: A Second Course,* Prentice-Hall, 1983.
-
Cook, R. D., D. S. Malkus, and M. E. Plesha, *Concepts and Applications of Finite Element Analysis,* John Wiley &amp; Sons, 1989.
-
Hughes, T. J. R., *The Finite Element Method*, Prentice-Hall, Inc., 1987.
-
Zienkiewicz, O. C., and R. L. Taylor, *The Finite Element Method: Volumes I, II, and III*, Butterworth-Heinemann, 2000.
**Performance of linear solid elements**
-
Prathap, G., &#8220;The Poor Bending Response of the Four-Node Plane Stress Quadrilaterals,&#8221; International Journal for Numerical Methods in Engineering, vol. 21, 825&#8211;835, 1985.
**Hourglass control in solid elements**
-
Belytschko, T., W. K. Liu, and J. M. Kennedy, &#8220;Hourglass Control in Linear and Nonlinear Problems,&#8221; Computer Methods in Applied Mechanics and Engineering, vol. 43, 251&#8211;276, 1984.
-
Flanagan, D. P., and T. Belytschko, &#8220;A Uniform Strain Hexahedron and Quadrilateral with Hourglass Control,&#8221; International Journal for Numerical Methods in Engineering, vol. 17, 679&#8211;706, 1981.
-
Puso, M. A., &#8220;A Highly Efficient Enhanced Assumed Strain Physically Stabilized Hexahedral Element,&#8221; International Journal for Numerical Methods in Engineering, vol. 49, 1029&#8211;1064, 2000.
**Incompatible mode elements**
-
Simo, J. C. and M. S. Rifai, &#8220;A Class of Assumed Strain Methods and the Method of Incompatible Modes,&#8221; International Journal for Numerical Methods in Engineering, vol. 29, 1595&#8211;1638, 1990.

## 4.7&nbsp;Summary

4.7&nbsp;Summary
-
The formulation and order of integration used in a continuum element can have a significant effect on the accuracy and cost of the analysis.
-
First-order (linear) elements using full integration are prone to shear locking and normally should not be used.
-
First-order, reduced-integration elements are prone to hourglassing; sufficient mesh refinement minimizes this problem.
-
When using first-order, reduced-integration elements in a simulation where bending deformation will occur, use at least four elements through the thickness.
-
Hourglassing is rarely a problem in the second-order, reduced-integration elements in Abaqus/Standard. You should consider using these elements for most general applications when there is no contact.
-
The accuracy of the incompatible mode elements available in Abaqus/Standard&nbsp;is strongly influenced by the amount of element distortion.
-
The numerical accuracy of the results depends on the mesh that has been used. Ideally a mesh refinement study should be carried out to ensure that the mesh provides a unique solution to the problem. However, remember that using a converged mesh does not ensure that the results from the finite element simulation will match the actual behavior of the physical problem: that also depends on other approximations and idealizations in the model.
-
In general, refine the mesh mainly in regions where you want accurate results; a finer mesh is required to predict accurate stresses than is needed to calculate accurate displacements.
-
Advanced features such as submodeling are available in Abaqus to help you to obtain useful results for complex simulations.

