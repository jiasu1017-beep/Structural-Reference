# 6.&nbsp;Using Beam Elements

*Use beam elements to model structures in which one dimension (the length) is significantly greater than the other two dimensions and in which the longitudinal stress is most important. Beam theory is based on the assumption that the deformation of the structure can be determined entirely from variables that are functions of position along the structure's length. For beam theory to produce acceptable results, the cross-section dimensions should be less than 1/10 of the structure's typical axial dimension. The following are examples of typical axial dimensions:the distance between supports,the distance between gross changes in cross-section, andthe wavelength of the highest vibration mode of interest.Abaqus beam elements assume that plane sections perpendicular to the axis of the beam remain plane during deformation.Do not be confused into thinking that the cross-section dimensions should be less than 1/10 of a typical element length. A highly refined mesh may contain beam elements whose length is less than their cross-section dimensions, although this is not generally recommended&#8212;continuum elements may be more suitable in such a case.*

6.&nbsp;Using Beam Elements
Use beam elements to model structures in which one dimension (the length) is significantly greater than the other two dimensions and in which the longitudinal stress is most important. Beam theory is based on the assumption that the deformation of the structure can be determined entirely from variables that are functions of position along the structure's length. For beam theory to produce acceptable results, the cross-section dimensions should be less than 1/10 of the structure's typical axial dimension. The following are examples of typical axial dimensions:
-
the distance between supports,
-
the distance between gross changes in cross-section, and
-
the wavelength of the highest vibration mode of interest.
Abaqus beam elements assume that plane sections perpendicular to the axis of the beam remain plane during deformation.
Do not be confused into thinking that the cross-section dimensions should be less than 1/10 of a typical *element* length. A highly refined mesh may contain beam elements whose length is less than their cross-section dimensions, although this is not generally recommended&#8212;continuum elements may be more suitable in such a case.

## 6.1&nbsp;Beam cross-section geometry

*You can define the beam profile in one of three ways: by choosing from the Abaqus cross-section library and specifying the shape and dimensions of the beam cross-section; by defining a generalized beam profile using section engineering properties, such as area and moments of inertia; or by using a mesh of special two-dimensional elements for which geometric quantities are calculated numerically, called a meshed beam cross-section.Abaqus offers a variety of common cross-section shapes, as shown in Figure 6&#8211;1, should you decide to define the beam profile geometrically. You can also define almost any thin-walled cross-section using the arbitrary cross-section definition. For a detailed discussion of the beam cross-sections available in Abaqus, see &#8220;*

6.1&nbsp;Beam cross-section geometry
You can define the beam profile in one of three ways: by choosing from the Abaqus cross-section library and specifying the shape and dimensions of the beam cross-section; by defining a generalized beam profile using section engineering properties, such as area and moments of inertia; or by using a mesh of special two-dimensional elements for which geometric quantities are calculated numerically, called a meshed beam cross-section.
Abaqus offers a variety of common cross-section shapes, as shown in [Figure 6&#8211;1](ch06s01.html#gss-beamsection), should you decide to define the beam profile geometrically. You can also define almost any thin-walled cross-section using the arbitrary cross-section definition. For a detailed discussion of the beam cross-sections available in Abaqus, see &#8220;Beam cross-section library,&#8221;  Section 29.3.9 of the Abaqus Analysis User's Guide.
**Figure 6&#8211;1** Beam cross-sections.
../graphics/gss-beamsection-nls.png
If you define a beam profile using one of the built-in cross-sections in the Abaqus library, Abaqus/CAE prompts you for the required cross-section dimensions, which are different for each type of cross-section. When the beam profile is associated with a beam section property, you can specify whether to have the section engineering properties calculated during the analysis or to have Abaqus precompute them (at the beginning of the analysis). The former option can be used when the material behavior is either linear or nonlinear (for example, if the section stiffness changes due to inelastic yielding); the latter option is more efficient, however, for linear elastic material behavior.
Alternatively, you can provide the section engineering properties (area, moments of inertia, and torsional constants) instead of the cross-section dimensions. The material behavior may be either linear or nonlinear. Thus, you can combine the beam's geometry and material behavior to define its response to loads, which may be linear or nonlinear. See &#8220;Using a general beam section to define the section behavior,&#8221;  Section 29.3.7 of the Abaqus Analysis User's Guide, for further details.
In Abaqus/Standard you can also define beams with linearly tapered cross-sections. General beam sections with linear response and standard library sections are supported.
Meshed beam cross-sections allow a description of the beam cross-section that includes multiple materials and complex geometry. This type of beam profile is discussed further in &#8220;Meshed beam cross-sections,&#8221;  Section 10.6.1 of the Abaqus Analysis User's Guide.6.1.1&nbsp;Section points
When you define the beam cross-section using a built-in profile from the Abaqus cross-section library and request that section engineering properties be calculated during the analysis, Abaqus calculates the beam element's response at an array of section points throughout the beam cross-section. The number of section points, as well as the section point locations, are shown in &#8220;Beam cross-section library,&#8221;  Section 29.3.9 of the Abaqus Analysis User's Guide. Element output variables, such as stress and strain, are available at any of the section points; however, by default output is provided at only a select number of section points, as described in &#8220;Beam cross-section library,&#8221;  Section 29.3.9 of the Abaqus Analysis User's Guide. All the section points for a rectangular cross-section are shown in [Figure 6&#8211;2](ch06s01.html#gss-rectbeamelem).
**Figure 6&#8211;2** Integration and default section points in a B32 rectangular beam element.
../graphics/gss-rectbeamelem-nls.png
For this cross-section output is provided at points 1, 5, 21, and 25 by default. The beam element shown in [Figure 6&#8211;2](ch06s01.html#gss-rectbeamelem) uses a total of 50 section points, 25 at each of the two integration points, to calculate its stiffness.
When you request that the beam section properties be precomputed, Abaqus does not calculate the beam's response at the section points. Instead, it uses the section engineering properties to determine the section response. Therefore, Abaqus uses section points only as locations for output, and you need to specify the section points at which you desire output.6.1.2&nbsp;Cross-section orientation
You must define the orientation of a beam's cross-section in global Cartesian space. The local tangent along the beam element, ../graphics/gsa_eqn00045.gif, is defined as the vector along the element axis pointing from the first node of the element to the next node. The beam cross-section is perpendicular to this local tangent. The local (1&#8211;2) beam section axes are represented by the vectors ../graphics/gsa_eqn00046.gif and ../graphics/gsa_eqn00047.gif. The three vectors ../graphics/gsa_eqn00045.gif, ../graphics/gsa_eqn00046.gif, and ../graphics/gsa_eqn00047.gif form a local, right-handed, coordinate system (see [Figure 6&#8211;3](ch06s01.html#gss-crosssect-orient)).
**Figure 6&#8211;3** Orientation of the beam element tangent, ../graphics/gsa_eqn00045.gif, and beam section axes, ../graphics/gsa_eqn00046.gif and ../graphics/gsa_eqn00047.gif.
../graphics/gss-crosssect-orient-nls.png
The ../graphics/gsa_eqn00046.gif-direction is always (0.0, 0.0, 1.0) for two-dimensional beam elements.
For three-dimensional beam elements there are several ways to define the orientation of the local beam section axes. The first is to specify an extra node on the data line defining the element (this method requires manually editing the input file created by Abaqus/CAE). The vector, ../graphics/gsa_eqn00048.gif, from the first node in the beam element to this additional node (see [Figure 6&#8211;3](ch06s01.html#gss-crosssect-orient)), is used initially as an approximate ../graphics/gsa_eqn00046.gif-direction. Abaqus then defines the beam's ../graphics/gsa_eqn00047.gif-direction as ../graphics/gsa_eqn00049.gif. Having determined ../graphics/gsa_eqn00047.gif, Abaqus defines the actual ../graphics/gsa_eqn00046.gif-direction as ../graphics/gsa_eqn00050.gif. This procedure ensures that the local tangent and local beam section axes form an orthogonal system.
Alternatively, you can give an approximate ../graphics/gsa_eqn00046.gif-direction when you define the beam section properties in Abaqus/CAE. Abaqus then uses the procedure described above to calculate the actual beam section axes. If you specify both an extra node and an approximate ../graphics/gsa_eqn00046.gif-direction, the additional node method takes precedence. Abaqus uses the vector from the origin to the point (0.0, 0.0, 1.0) as the default ../graphics/gsa_eqn00046.gif-direction if you provide no approximate ../graphics/gsa_eqn00046.gif-direction.
There are two methods that can be used to override the ../graphics/gsa_eqn00047.gif-direction defined by Abaqus; both require editing the input file manually. One is to give the components of ../graphics/gsa_eqn00047.gif as the 4th, 5th, and 6th data values following the nodal coordinates. The alternative is to specify the normal direction directly with the *NORMAL option (this option can be added using the Abaqus/CAE **Keywords Editor**). If both methods are used, the latter takes precedence. Abaqus again defines the ../graphics/gsa_eqn00046.gif-direction as ../graphics/gsa_eqn00051.gif.
The ../graphics/gsa_eqn00047.gif-direction that you provide need not be orthogonal to the beam element tangent, ../graphics/gsa_eqn00045.gif. When you provide the ../graphics/gsa_eqn00047.gif-direction, the local beam element tangent is redefined as the value of the cross product ../graphics/gsa_eqn00052.gif. It is quite possible in this situation that the redefined local beam tangent, ../graphics/gsa_eqn00045.gif, will not align with the beam axis, as defined by the vector from the first to the second node. If the ../graphics/gsa_eqn00047.gif-direction subtends an angle greater than 20 with the plane perpendicular to the element axis, Abaqus issues a warning message in the data file.
The example presented in [&#8220;Example: cargo crane,&#8221;  Section 6.4](ch06s04.html), explains how to assign the beam cross-section orientation using Abaqus/CAE.6.1.3&nbsp;Beam element curvature
The curvature of beam elements is based on the orientation of the beam's ../graphics/gsa_eqn00047.gif-direction relative to the beam axis. If the ../graphics/gsa_eqn00047.gif-direction and the beam axis are not orthogonal (i.e., the beam axis and the tangent, ../graphics/gsa_eqn00045.gif, do not coincide), the beam element is considered to be curved initially. Since the behavior of curved beams is different from the behavior of straight beams, you should always check your model to ensure that the correct normals and, hence, the correct curvatures are used. For beams and shells Abaqus uses the same algorithm to determine the normals at nodes shared by several elements. A description is given in &#8220;Beam element cross-section orientation,&#8221;  Section 29.3.4 of the Abaqus Analysis User's Guide.
If you intend to model curved beam structures, you should use one of the two methods described earlier to define the ../graphics/gsa_eqn00047.gif-direction directly, allowing you great control in modeling the curvature. Even if you intend to model a structure made up of straight beams, curvature may be introduced as normals are averaged at shared nodes. You can rectify this problem by defining the beam normals directly as explained previously.6.1.4&nbsp;Nodal offsets in beam sections
When beam elements are used as stiffeners for shell models, it is convenient to have the beam and shell elements share the same nodes. By default, shell element nodes are located at the midplane of the shell, and beam element nodes are located somewhere in the cross-section of the beam. Hence, if the shell and beam elements share the same nodes, the shell and the beam stiffener will overlap unless the beam cross-section is offset from the location of the node (see [Figure 6&#8211;4](ch06s01.html#gss-nodaloffset)).
**Figure 6&#8211;4** Using beams as stiffeners for shell models: (a)&nbsp;without offset of beam sections; (b) with offset of beam sections.
../graphics/gss-nodaloffset-nls.png
With beam section types I, TRAPEZOID, and ARBITRARY it is possible to specify that the section geometry is located at some distance from the origin of the section's local coordinate system, which is located at the element's nodes. Since it is easy to offset beams with such cross-sections from their nodes, they can be used readily as stiffeners as shown in [Figure 6&#8211;4](ch06s01.html#gss-nodaloffset)(b). (If flange or web buckling of the stiffeners is important, shells should be used to model the stiffeners.)
The I-beam shown in [Figure 6&#8211;5](ch06s01.html#gss-ibeam) is attached to a shell 1.2 units thick. The beam section can be oriented as it is shown in the figure by defining the offset of the beam node from the bottom of the I-section. The offset in this case would be 0.6; i.e., one half of the shell thickness.
You can also specify the location of the centroid and shear center; these locations can be offset from the beam node, thus enabling you to model stiffeners readily.
**Figure 6&#8211;5** I-beam used as stiffener for a shell element.
../graphics/gss-ibeam-nls.png
It is also possible to define the beam nodes and shell nodes separately and connect the beam and shell using a rigid beam constraint between the two nodes. See &#8220;Linear constraint equations,&#8221;  Section 35.2.1 of the Abaqus Analysis User's Guide, for further details.

## 6.2&nbsp;Formulation and integration

*All beam elements in Abaqus are &#8220;beam-column&#8221; elements&#8212;meaning they allow axial, bending, and torsional deformation. The Timoshenko beam elements also consider the effects of transverse shear deformation.*

6.2&nbsp;Formulation and integration
All beam elements in Abaqus are &#8220;beam-column&#8221; elements&#8212;meaning they allow axial, bending, and torsional deformation. The Timoshenko beam elements also consider the effects of transverse shear deformation.6.2.1&nbsp;Shear deformation
The linear elements (B21 and B31) and the quadratic elements (B22 and B32) are shear deformable, Timoshenko beams; thus, they are suitable for modeling both stout members, in which shear deformation is important, and slender beams, in which shear deformation is not important. The cross-sections of these elements behave in the same manner as the cross-sections of the thick shell elements, as illustrated in [Figure 6&#8211;6](ch06s02.html#gss-transhellsect)(b) and discussed in [&#8220;Shell formulation &#8211; thick or thin,&#8221;  Section 5.2](ch05s02.html).
**Figure 6&#8211;6** Behavior of transverse beam sections in (a) slender beams and (b) thick beams.
../graphics/gss-transhellsect-nls.png
Abaqus assumes the transverse shear stiffness of these beam elements to be linear elastic and constant. In addition, these beams are formulated so that their cross-sectional area can change as a function of the axial deformation, an effect that is considered only in geometrically nonlinear simulations (see [Chapter 8, &#8220;Nonlinearity](ch08.html)&#8221;) in which the section Poisson's ratio has a nonzero value. These elements can provide useful results as long as the cross-section dimensions are less than 1/10 of the typical axial dimensions of the structure, which is generally considered to be the limit of the applicability of beam theory; if the beam cross-section does not remain plane under bending deformation, beam theory is not adequate to model the deformation.
The cubic elements available in Abaqus/Standard&#8212;the so-called Euler-Bernoulli beam elements (B23 and B33)&#8212;do not model shear flexibility. The cross-sections of these elements remain perpendicular to the beam axis (see [Figure 6&#8211;6](ch06s02.html#gss-transhellsect)(a)). Therefore, the cubic beam elements are most effective for modeling structures with relatively slender members. Since cubic elements model a cubic variation of displacement along their lengths, a structural member often can be modeled with a single cubic element for a static analysis and with a small number of elements for a dynamic analysis. These elements assume that shear deformations are negligible. Generally, if the cross-section dimensions are less than 1/15 of the typical axial dimensions of the structure, this assumption is valid.6.2.2&nbsp;Torsional response&#8212;warping
Structural members are often subjected to torsional moments, which occur in almost any three-dimensional frame structure. Loads that cause bending in one member may cause twisting in another, as shown in [Figure 6&#8211;7](ch06s02.html#gss-torsion).
**Figure 6&#8211;7** Torsion induced in a frame structure.
../graphics/gss-torsion-nls.pngThe response of a beam to torsion depends on the shape of its cross-section. Generally, torsion in a beam produces warping or nonuniform out-of-plane displacements in the cross-section. Abaqus considers the effects of torsion and warping only in the three-dimensional elements. The warping calculation assumes that the warping displacements are small. The following cross-sections behave differently under torsion: solid cross-sections; closed, thin-walled cross-sections; and open, thin-walled cross-sections.
**Solid cross-sections**
A solid, non-circular cross-section does not remain plane under torsion; instead, the section warps. Abaqus uses St.&nbsp;Venant warping theory to calculate a single component of shear strain caused by the warping at each section point in the cross-section. The warping in such solid cross-sections is considered unconstrained and creates negligible axial stresses. (Warping constraints would affect the solution only in the immediate vicinity of the constrained end.) The torsional stiffness of a beam with a solid cross-section depends on the shear modulus, *G*, of the material and the torsion constant, *J*, of the beam section. The torsion constant depends on the shape and the warping characteristics of the beam cross-section. Torsional loads that produce large amounts of inelastic deformation in the cross-section cannot be modeled accurately with this approach.
**Closed, thin-walled cross-sections**
Beams that have closed, thin-walled, non-circular cross-sections (BOX or HEX) have significant torsional stiffness and, thus, behave in a manner similar to solid sections. Abaqus assumes that warping in these sections is also unconstrained. The thin-walled nature of the cross-section allows Abaqus to consider the shear strains to be constant through the wall thickness. The thin-walled assumption is generally valid provided that the wall thickness is 1/10 a typical beam cross-section dimension. Examples of typical cross-section dimensions for thin-walled cross-sections include:
-
The diameter of a pipe section.
-
The length of an edge of a box section.
-
The typical edge length of an arbitrary section.
**Open, thin-walled cross-sections**
Open, thin-walled cross-sections are very flexible in torsion when warping is unconstrained, and the primary source of torsional stiffness in such structures is the constraint of the axial warping strains. Constraining the warping of open, thin-walled beams introduces axial stresses that can affect the beam's response to other loading types. Abaqus/Standard has shear deformable beam elements, B31OS and B32OS, which include the warping effects in open, thin-walled sections. These elements must be used when modeling structures with open, thin-walled cross-sections&#8212;such as a channel (defined as an ARBITRARY section) or an I-section&#8212;that are subjected to significant torsional loading.
The variation of the warping-induced axial deformation over the beam's cross-section is defined by the section's warping function. The magnitude of this function is treated as an extra degree of freedom, 7, in the open-section beam elements. Constraining this degree of freedom prevents warping at the nodes at which the constraints are applied.
So that the warping amplitude can be different in each branch, the junction between open-section beams in a frame structure generally should be modeled with separate nodes for each branch (see [Figure 6&#8211;8](ch06s02.html#gss-opensectbeam)).
**Figure 6&#8211;8** Connecting open-section beams.
../graphics/gss-opensectbeam-nls.png
However, if the connection is designed to prevent warping, all branches should share a common node, and the warping degree of freedom should be constrained.
A shear force that does not act through the beam's shear center produces torsion. The twisting moment is equal to the shear force multiplied by its eccentricity with respect to the shear center. Often, the centroid and the shear center do not coincide in open, thin-walled beam sections (see [Figure 6&#8211;9](ch06s02.html#gss-shear-centroid)). If the nodes are not located at the shear center of the cross-section, the section may twist under loading.
**Figure 6&#8211;9** Approximate locations of shear centers, *s*, and centroids, *c*, for a number of beam cross-sections.
../graphics/gss-shear-centroid.png

## 6.3&nbsp;Selecting beam elements

6.3&nbsp;Selecting beam elements
-
First-order, shear-deformable beam elements (B21, B31) should be used in any simulation that includes contact.
-
If the transverse shear deformation is important, use Timoshenko (quadratic) beam elements (B22, B32).
-
If the structure is either very rigid or very flexible, the hybrid beam elements (B21H, B32H, etc.) available in Abaqus/Standard should be used in geometrically nonlinear simulations.
-
The Euler-Bernoulli (cubic) beams (B23, B33) available in Abaqus/Standard are very accurate for simulations that include distributed loading, such as dynamic vibration analyses.
-
Structures with open, thin-walled cross-sections should be modeled with the elements that use open-section warping theory (B31OS, B32OS) available in Abaqus/Standard.

## 6.4&nbsp;Example: cargo crane

*A light-service, cargo crane is shown in Figure 6&#8211;10. You have been asked to determine the static deflections of the crane when it carries a load of 10&nbsp;kN. You should also identify the critical members and joints in the structure: i.e., those with the highest stresses and loads. Because this is a static analysis you will analyze the cargo crane using Abaqus/Standard.Figure 6&#8211;10*

6.4&nbsp;Example: cargo crane
A light-service, cargo crane is shown in [Figure 6&#8211;10](ch06s04.html#gss-cargo-static). You have been asked to determine the static deflections of the crane when it carries a load of 10&nbsp;kN. You should also identify the critical members and joints in the structure: i.e., those with the highest stresses and loads. Because this is a static analysis you will analyze the cargo crane using Abaqus/Standard.
**Figure 6&#8211;10** Sketch of a light-service cargo crane.
../graphics/gss-cargo.png
The crane consists of two truss structures joined together by cross bracing. The two main members in each truss structure are steel box beams (box cross-sections). Each truss structure is stiffened by internal bracing, which is welded to the main members. The cross bracing connecting the two truss structures is bolted to the truss structures. These connections can transmit little, if any, moment and, therefore, are treated as pinned joints. Both the internal bracing and cross bracing use steel box beams with smaller cross-sections than the main members of the truss structures. The two truss structures are connected at their ends (at point E) in such a way that allows independent movement in the 3-direction and all of the rotations, while constraining the displacements in the 1- and 2-directions to be the same. The crane is welded firmly to a massive structure at points A, B, C, and D. The dimensions of the crane are shown in [Figure 6&#8211;11](ch06s04.html#gss-cargo-crane-dim). In the following figures, truss&nbsp;A is the structure consisting of members AE, BE, and their internal bracing; and truss&nbsp;B consists of members CE, DE, and their internal bracing.
**Figure 6&#8211;11** Dimensions (in m) of the cargo crane.
../graphics/gss-cargo-crane-dim-nls.png
The ratio of the typical cross-section dimension to global axial length in the main members of the crane is much less than 1/15. The ratio is approximately 1/15 in the shortest member used for internal bracing. Therefore, it is valid to use beam elements to model the crane.6.4.1&nbsp;Preprocessing&#8212;creating the model with Abaqus/CAE
In this section we discuss how to use Abaqus/CAE to create the entire model for this simulation. Abaqus provides scripts that replicate the complete analysis model for this problem. Run one of these scripts if you encounter difficulties following the instructions given below or if you wish to check your work. Scripts are available in the following locations:
-
A Python script for this example is provided in [&#8220;Cargo crane,&#8221;  Section A.4](ap01s04.html). Instructions of how to fetch the script and run it within Abaqus/CAE are given in [Appendix A, &#8220;Example Files](ap01.html).&#8221;
-
A plug-in script for this example is available in the Abaqus/CAE Plug-in toolset. To run the script from Abaqus/CAE, select **Plug-ins**../images/arrow.gif**Abaqus**../images/arrow.gif**Getting Started**, highlight **Cargo crane**, and click **Run**. For more information about the Getting Started plug-ins, see &#8220;Running the Getting Started with Abaqus examples,&#8221;  Section 82.1 of the Abaqus/CAE User's Guide.
If you do not have access to Abaqus/CAE or another preprocessor, the input file required for this problem can be created manually, as discussed in &#8220;Example: cargo crane,&#8221;  Section 6.4 of Getting Started with Abaqus: Keywords Edition.
**Creating the parts**
The welded joints between the internal bracing and main members in the crane provide complete continuity of the translations and rotations from one region of the model to the next. Therefore, you need only a single geometric entity (i.e., vertex) at each welded joint in the model. A single part is used to represent the internal bracing and main members. For convenience, both truss structures will be treated as a single part.
The bolted joints, which connect the cross bracing to the truss structures, and the connection at the tip of the truss structures are different from the welded joint connections. Since these joints do not provide complete continuity for all degrees of freedom, separate vertices are needed for connection. Thus, the cross bracing must be treated as a separate part since distinct geometric entities are required to model the bolted joints. Appropriate constraints between the separate vertices must be specified.
We begin by discussing a technique to define the truss geometry. Since the two truss structures are identical, it is sufficient to define the base feature of the part using only the geometry of a single truss structure. The sketch of the truss geometry can be saved and then used to add the second truss structure to the part definition.
The dimensions shown in [Figure 6&#8211;11](ch06s04.html#gss-cargo-crane-dim) are relative to a global Cartesian coordinate system. The base feature, however, must be sketched in a local plane. To make the sketching easier, datum features will be used. A datum plane, parallel to one of the trusses (truss B in [Figure 6&#8211;10](ch06s04.html#gss-cargo-static), for example), will serve as the sketch plane. The orientation of the sketch plane will be defined using a datum axis.
**To define the geometry of a single truss:**
-
To create a datum plane, a part must first be created. A part consisting of a single reference point will serve this purpose. Begin by creating a three-dimensional deformable part using the point base feature. Set the approximate part size to `20.0`, and name the part `Truss`. Place the point at the origin. This point represents point D in [Figure 6&#8211;10](ch06s04.html#gss-cargo-static).
-
Using the **Create Datum Point: Offset From Point** tool ../graphics/ico_dtmPtOffsetPoint.png, create two datum points at distances of `(0, 1, 0)` and `(8, 1.5, 0.9)` from the reference point. These points represent points C and E, respectively, in [Figure 6&#8211;10](ch06s04.html#gss-cargo-static). Reset the view using the **Auto-Fit View** tool ../graphics/ico_viewFit.png in the **View Manipulation** toolbar to see the full model.
-
Using the **Create Datum Plane: 3 Points** tool ../graphics/ico_dtmPlaneThreePoints.png, create a datum plane to serve as the sketch plane. Select the reference point first, and then select the other two datum points in a counterclockwise fashion. Click mouse button 2 to exit the procedure.
Note:&nbsp;
While selecting the points in this way is not required, it will make certain operations that follow easier. For example, by selecting the points in a counterclockwise order, the normal to the plane points out of the viewport and the sketch plane will be oriented automatically in the 1&#8211;2 view in the Sketcher. If you select the points in a clockwise order, the plane's normal will point into the viewport and the sketch plane will have to be adjusted in the Sketcher.
-
Using the **Create Datum Axis: Principal Axis** tool ../graphics/ico_dtmAxisPrincipal.png, create a datum axis parallel to the **Y-Axis**. As noted earlier, this axis will be used to position the sketch plane.
-
You are now ready to sketch the geometry. Use the **Create Wire: Planar** tool ../graphics/ico_partWirePlanar.png to enter the Sketcher. Select the datum plane as the plane on which to sketch the wire geometry; select the datum axis as the axis that will appear vertical and to the left of the sketch. You may need to resize the view to select these entities.
-
Once in the Sketcher, use the **Sketcher Options** tool to modify the display. In the **General** tab, change the **Sheet size** to `20` and reduce the **Grid spacing** to `8`. Zoom in to see the datum points more clearly.
Note:&nbsp;
If the sketch plane is not oriented in the 1&#8211;2 plane, use the **Views** toolbar to change to the X&#8211;Y view.Using the **Create Lines: Connected** tool ../graphics/ico_sketchLines.png, sketch the lines representing the main truss, as shown in [Figure 6&#8211;12](ch06s04.html#gss-crane-partaa-c). The datum points that were projected are treated as fixed points in the sketch. Any line connected to one of these points effectively inherits a fixed constraint at that point.
**Figure 6&#8211;12** Main members of the truss.
../graphics/gss-crane-partaa-c.png
-
Next, create a series of connected lines as shown in [Figure 6&#8211;13](ch06s04.html#gss-crane-partb-c) to approximate the interior bracing of the truss.
**Figure 6&#8211;13** Rough layout of interior members.
../graphics/gss-crane-partb-c.pngAt this stage, the layout of the interior bracing is arbitrary and is intended only as a rough approximation of the true shape. The endpoints of the lines, however, must snap to the edges of the main truss members. This is indicated in the figure by the presence of small circles next to the intersections of the interior bracing with the main members. Avoid creating 90 angles because that will introduce unwanted additional constraints.
-
Split the edges of the main members at the points where they intersect the interior bracing.
-
Dimension the vertical distance between the left endpoints of the sketch and the horizontal distance between the reference point and the right endpoint of the sketch, as shown in [Figure 6&#8211;14](ch06s04.html#gss-crane-partbb-c). These dimensions will act as additional constraints on the sketch. Accept the values shown in the prompt area when creating the dimensions. These values represent the dimensions of the part, projected from the global Cartesian coordinate system (depicted in [Figure 6&#8211;11](ch06s04.html#gss-cargo-crane-dim)) to the local sketch plane.
**Figure 6&#8211;14** Dimensioned sketch.
../graphics/gss-crane-partbb-c.png
-
Apply parallel constraints to the segments of the top edge of the main member, then repeat this operation for the bottom edge of the main member. These constraints ensure that these line segments remain colinear.
-
To complete the sketch, recognize from [Figure 6&#8211;11](ch06s04.html#gss-cargo-crane-dim) that the interior bracing breaks the main members into equal length segments on both its top and bottom edges. Thus, impose equal length constraints on the segments of the top edge of the main member; repeat this operation for the bottom edge of the main member. The final sketch appears as shown in [Figure 6&#8211;15](ch06s04.html#gss-crane-partc-c).
**Figure 6&#8211;15** Final sketch of single truss structure.
../graphics/gss-crane-partc-c.png
-
Using the **Save Sketch As** tool ../graphics/ico_sketchSaveAs.png, save the sketch as `Truss`.
-
Click **Done** to exit the Sketcher and to save the base feature of the part.
The other truss will also be added as a planar wire feature by projecting the truss created here onto a new datum plane.
**To define the geometry of the second truss structure:**
-
Define three datum points using offsets from the end points of the truss, as shown in [Figure 6&#8211;16](ch06s04.html#gss-crane-parte-c). The offsets from the parent vertices are indicated in the figure. You may need to rotate your sketch to see the datum points.
**Figure 6&#8211;16** Datum points, plane, and axis.
../graphics/gss-crane-parte-c-nls.png
-
Create a datum plane using these three points. As before, the points defining the plane should be chosen in a counterclockwise order.
-
Use the **Create Wire: Planar** tool to add a feature to the part. Select the new datum plane as the sketch plane and the datum axis created earlier as the edge that will appear vertical and on the left of the sketch.
Note:&nbsp;
If the sketch plane is not oriented in the 1&#8211;2 plane, use the **Views** toolbar to change to the X&#8211;Y view.
-
Use the **Add Sketch** tool ../graphics/ico_sketchAdd.png to retrieve the truss sketch. Translate the sketch by selecting the vertex at the top left end of the new truss as the starting point of the translation vector and the datum point labeled `P` in [Figure 6&#8211;16](ch06s04.html#gss-crane-parte-c) as the endpoint of the vector. Zoom in and rotate the view as necessary to facilitate your selections.
Note:&nbsp;
If the points defining either the original or new datum plane were not selected in a counterclockwise order, you will have to mirror the sketch before translating it. If necessary, cancel the sketch retrieval operation, create the necessary construction line for mirroring, and retrieve the sketch again.
-
Click **Done** in the prompt area to exit the Sketcher.
The final truss part is shown in [Figure 6&#8211;17](ch06s04.html#gss-crane-datum-c). The visibility of all datum and reference geometry has been suppressed.
**Figure 6&#8211;17** Final geometry of the truss structures; highlighted vertices indicate the locations of the pin joints.
../graphics/gss-crane-datum-c-nls.png
Recall that the cross bracing must be treated as a separate part to properly represent the pin joints between it and the trusses. The easiest way to sketch the cross bracing, however, is to create wire features directly between the locations of the joints in the trusses. Thus, we will adopt the following method to create the cross bracing part: first, a copy of the truss part will be created and the wires representing the cross brace will be added to it (we cannot use this new part as is because the vertices at the joints are shared and, thus, cannot represent a pin joint); then, we will use the cut feature available in the Assembly module to perform a Boolean cut between the truss with the cross brace and the truss without the cross brace, leaving the cross brace geometry as a distinct part. The procedure is described in detail below.
**To create the cross brace geometry:**
-
In the Model Tree,  click mouse button 3 on the **Truss** item underneath the **Parts** container and select **Copy** from the menu that appears. In the **Part Copy** dialog box, name the new part `Truss-all`, and click **OK**.
-
The pin locations are highlighted in [Figure 6&#8211;17](ch06s04.html#gss-crane-datum-c). Use the **Create Wire: Point to Point** tool ../graphics/ico_partWirePoint.png. In the **Create Wire Feature** dialog box, accept the default setting of **Chained wires** and click ../graphics/ico_add.png to add the cross bracing geometry to the new part, as shown in [Figure 6&#8211;18](ch06s04.html#gss-crane-parth-c) (the vertices in this figure correspond to those labeled in [Figure 6&#8211;17](ch06s04.html#gss-crane-datum-c); the visibility of the truss in [Figure 6&#8211;18](ch06s04.html#gss-crane-parth-c) has been suppressed). Use the following coordinates to specify a similar view: **Viewpoint** (1.19, 5.18, 7.89), **Up vector** (0.40, 0.76, 0.51).
**Figure 6&#8211;18** Cross bracing geometry.
../graphics/gss-crane-parth-c.png
Tip:&nbsp;
If you make a mistake while connecting the cross bracing geometry, you can delete a line using the **Delete Feature** tool ../graphics/ico_featureDelete.png; you cannot recover deleted features.
-
Create an instance of each part (`Truss` and `Truss-all`).
-
From the main menu bar of the Assembly module, select **Instance**../images/arrow.gif**Merge/Cut**. In the **Merge/Cut Instances** dialog box, name the new part `Cross brace`, select **Cut geometry** in the **Operations** field, and click **Continue**.
-
In the prompt area, click **Instances**. Select `Truss-all-1` as the instance to be cut. Similarly, select `Truss-1` as the instance that will make the cut.
After the cut is made, a new part named `Cross brace` is created that contains only the cross brace geometry. The current model assembly contains only an instance of this part; the original part instances are suppressed by default. Since we will need to use the original truss in the model assembly, click mouse button 3 on **Truss-1** underneath the **Instances** container and select **Resume** from the menu that appears to resume this part instance.
We now define the beam section properties.
**Defining beam section properties**
Since the material behavior in this simulation is assumed to be linear elastic, it is more efficient from a computational point of view to precompute the beam section properties. Assume the trusses and bracing are made of a mild strength steel with ../graphics/gsa_eqn00053.gif = 200.0  109&nbsp;Pa, ../graphics/gsa_eqn00054.gif = 0.25, and ../graphics/gsa_eqn00055.gif = 80.0  109&nbsp;Pa. All the beams in this structure have a box-shaped cross-section.
A box-section is shown in [Figure 6&#8211;19](ch06s04.html#gss-localbeam). The dimensions shown in [Figure 6&#8211;19](ch06s04.html#gss-localbeam) are for the main members of the two trusses in the crane. The dimensions of the beam sections for the bracing members are shown in [Figure 6&#8211;20](ch06s04.html#gss-crosssect-geom).
**Figure 6&#8211;19** Cross-section geometry and dimensions (in m) of the main members.
../graphics/gss-localbeam-nls.png
**Figure 6&#8211;20** Cross-section geometry and dimensions (in m) of the internal and cross bracing members.
../graphics/gss-crosssect-geom-nls.png
**To define the beam section properties:**
-
In the Model Tree,  double-click the **Profiles** container to create a box profile for the main members of the truss structures; then, create a second profile for the internal and cross bracing. Name the profiles `MainBoxProfile` and `BraceBoxProfile`, respectively. Use the dimensions shown in [Figure 6&#8211;19](ch06s04.html#gss-localbeam) and [Figure 6&#8211;20](ch06s04.html#gss-crosssect-geom) to complete the profile definitions.
-
Create one **Beam** section for the main members of the truss structures and one for the internal and cross bracing. Name the sections `MainMemberSection` and `BracingSection`, respectively.
-
For both section definitions, specify that section integration will be performed before the analysis. When this type of section integration is chosen, material properties are defined as part of the section definition rather than in a separate material definition.
-
Choose `MainBoxProfile` for the main members' section definition, and `BraceBoxProfile` for the bracing section definition.
-
Click the **Basic** tab, and enter the Young's and shear moduli noted earlier in the appropriate fields of the data table.
-
Enter the **Section Poisson's ratio** in the appropriate text field of the **Edit Beam Section** dialog box.
-
Assign `MainMemberSection` to the geometry regions representing the main members of the trusses and `BracingSection` to the regions representing the internal and cross bracing members. Use the **Part** list located in the context bar to retrieve each part. You can ignore the `Truss-all` part since it is no longer needed.
**Defining beam section orientations**
The beam section axes for the main members should be oriented such that the beam 1-axis is orthogonal to the plane of the truss structures shown in the elevation view ([Figure 6&#8211;11](ch06s04.html#gss-cargo-crane-dim)) and the beam 2-axis is orthogonal to the elements in that plane. The approximate ../graphics/gsa_eqn00046.gif-vector for the internal truss bracing is the same as for the main members of the respective truss structures.
In its local coordinate system, the `Truss` part is oriented as shown in [Figure 6&#8211;21](ch06s04.html#gss-crane-n1main-c).
**Figure 6&#8211;21** Orientation of the truss in its local coordinate system.
../graphics/gss-crane-n1main-c.pngFrom the main menu bar of the Property module, select **Assign**../images/arrow.gif**Beam Section Orientation** to specify an approximate ../graphics/gsa_eqn00046.gif-vector for each truss structure. As noted earlier, the direction of this vector should be orthogonal to the plane of the truss. Thus, for truss B, the approximate ../graphics/gsa_eqn00046.gif = (0.1118, 0.0, 0.9936); while for the other truss structure (truss A), the approximate ../graphics/gsa_eqn00046.gif = (0.1118, 0.0, 0.9936).
You may want to check that your beam sections and orientations are correct. From the main menu bar, select **View**../images/arrow.gif**Part Display Options** and toggle on **Render beam profiles** to see a graphical representation of the beam profile. Toggle off **Render beam profiles** before continuing with the rest of the example. This functionality is also available in the Visualization module through the **ODB Display Options** dialog box.
From the main menu bar, select **Assign**../images/arrow.gif**Element Tangent** to specify the beam tangent directions. Flip the tangent directions as necessary so that they appear as shown in [Figure 6&#8211;22](ch06s04.html#gsi-beamtangents).
**Figure 6&#8211;22** Beam tangent directions.
../graphics/gsi-beamtangents.png
While both the cross bracing and the bracing within each truss structure have the same beam section geometry, they do not share the same orientation of the beam section axes. Since the square cross bracing members are subjected to primarily axial loading, their deformation is not sensitive to cross-section orientation; thus, we make some assumptions so that the orientation of the cross-bracing is somewhat easier to specify. All of the beam normals (../graphics/gsa_eqn00047.gif-vectors) should lie approximately in the plane of the plan view of the cargo crane (see [Figure 6&#8211;11](ch06s04.html#gss-cargo-crane-dim)). This plane is skewed slightly from the global 1&#8211;3 plane. A simple method for defining such an orientation is to provide an approximate ../graphics/gsa_eqn00046.gif-vector that is orthogonal to this plane. The vector should be nearly parallel to the global 2-direction. Therefore, specify ../graphics/gsa_eqn00046.gif = (0.0, 1.0, 0.0) for the cross bracing so that it is aligned with the part (and as we shall see later, global) *y*-axis.
**Beam normals**
In this model you will have a modeling error if you provide data that only define the orientation of the approximate ../graphics/gsa_eqn00046.gif-vector. Unless overridden, the averaging of beam normals (see [&#8220;Beam element curvature,&#8221;  Section 6.1.3](ch06s01.html#gsa-bms-beamelmcurv)) causes Abaqus to use incorrect geometry for the cargo crane model. To see this, you can use the Visualization module to display the beam section axes and beam tangent vectors (see [&#8220;Postprocessing,&#8221;  Section 6.4.2](ch06s04.html#gsa-bms-postprocessing)). Without any further modification to the beam normal directions, the normals in the crane model would appear to be correct in the Visualization module; yet, they would be, in fact, slightly incorrect.
[Figure 6&#8211;23](ch06s04.html#gss-crane-normal-c) shows the geometry of the truss structure.
**Figure 6&#8211;23** Locations where beam normals should be specified.
../graphics/gss-crane-normal-c.pngReferring to this figure, the correct geometry for the crane model requires three independent beam normals at vertex V1: one each for regions R1 and R2 and a single normal for regions R3 and R4. Using the Abaqus logic for averaging normals, it becomes readily apparent that the beam normal at vertex V1 in region R2 would be averaged with the normals at this point for the adjacent regions. In this case the important part of the averaging logic is that normals that subtend an angle less than 20 with the reference normal are averaged with the reference normal to define a new reference normal. Assume the original reference normal at this point is the normal for regions R3 and R4. Since the normal at vertex V1 in region R2 subtends an angle less than 20 with the original reference normal, it is averaged with the original normal to define a new reference normal at that location. On the other hand, since the normal at vertex V1  in region R1 subtends an angle of approximately 30 with the original reference normal, it will have an independent normal.
As a result of the incorrect average normal, the elements created on regions R2, R3, and R4 that share the node created at vertex V1 would have an intended geometry that exhibits curvature from one end of the element to the other. To prevent Abaqus from applying its averaging algorithm, specify the normal directions explicitly at positions where the subtended angle between adjacent regions will be less than 20. In this problem you must specify the normal positions for the corresponding regions on both sides of the crane.
There is also a problem with the normals at vertex V2 at the tip of the truss structure, again because the angle between the two regions attached to this vertex is less than 20. Since we are modeling straight beams, the normals are constant at both ends of each beam. This can be corrected by explicitly specifying the beam normal direction. As before, you must do this for the corresponding regions on both sides of the crane.
Currently, the only way to specify beam normal directions in Abaqus/CAE is with the **Keywords Editor**. The **Keywords Editor** is a specialized text editor that allows you to modify the Abaqus input file generated by Abaqus/CAE before submitting it for analysis. Thus, it allows you to add Abaqus/Standard or Abaqus/Explicit functionality when such functionality is not supported by the current release of Abaqus/CAE. For more information on the **Keywords Editor**, see &#8220;Adding unsupported keywords to your Abaqus/CAE model,&#8221;  Section 9.10.1 of the Abaqus/CAE User's Guide.
You will specify the beam normal directions later.
**Creating assembly-level sets**
We now focus on assembling the model. Since the parts are already aligned with the global Cartesian coordinate system shown in [Figure 6&#8211;11](ch06s04.html#gss-cargo-crane-dim), no further manipulations of the parts are necessary.
At this point, however, it is convenient to define assembly-level geometry sets that will be used later. In the Model Tree, expand the **Assembly** container and double-click **Sets**. Define a geometry set containing the vertices corresponding to points A through D (refer to [Figure 6&#8211;10](ch06s04.html#gss-cargo-static) for the exact locations), and name the set `Attach`. When defining this set, be sure to select the vertices of the truss and not reference points. You may need to use the **Selection** toolbar to aid in your selection.
In addition, create sets at the vertices located at the tips of the trusses (location E in [Figure 6&#8211;10](ch06s04.html#gss-cargo-static)). Name the sets `Tip-a` and `Tip-b`, with `Tip-a` being the geometry set associated with truss A (see [Figure 6&#8211;17](ch06s04.html#gss-crane-datum-c)). Finally, create a set for each region where beam normals will be specified, referring to [Figure 6&#8211;17](ch06s04.html#gss-crane-datum-c) and [Figure 6&#8211;23](ch06s04.html#gss-crane-normal-c). For truss A, create a set named `Inner-a` for the region indicated by R2 and a set named `Leg-a` for the region indicated by R5; create corresponding sets `Inner-b` and `Leg-b` for truss B.
**Creating a step definition and specifying output**
Create a single static, general step. Name the step `Tip load`, and enter the following step description: `Static tip load on crane`.
Write the displacements (U) and reaction forces and moments (RF) at the nodes and the section forces and moments (SF) in the elements to the output database as field output for postprocessing with Abaqus/CAE.
**Defining constraint equations**
Constraints between nodal degrees of freedom are specified in the Interaction module. The form of each equation is
../graphics/gsa_eqn00056.gifwhere ../graphics/gsa_eqn00057.gif is the coefficient associated with degree of freedom ../graphics/gsa_eqn00058.gif.
In the crane model the tips of the two trusses are connected together such that degrees of freedom 1 and 2 (the translations in the 1- and 2-directions) of each tip node are equal, while the other degrees of freedom (3&#8211;6) are independent. We need two linear constraints, one equating degree of freedom&nbsp;1 at the two vertices and the other equating degree of freedom 2.
**To create linear equations:**
-
In the Model Tree, double-click the **Constraints** container. Name the constraint `TipConstraint-1`, and specify an equation constraint.
-
In the **Edit Constraint** dialog box, enter a coefficient of `1.0`, the set name `Tip-a`, and degree of freedom `1` in the first row. In the second row, enter a coefficient of `-1.0`, the set name `Tip-b`, and degree of freedom `1`. Click **OK**.
This defines the constraint equation for degree of freedom 1.
Note:&nbsp;
Text input is case-sensitive in Abaqus/CAE.
-
Click mouse button 3 on the **TipConstraint-1** item underneath the **Constraints** container, and select **Copy** from the menu that appears. Copy `TipConstraint-1` to `TipConstraint-2`.
-
Double-click **TipConstraint-2** underneath the **Constraints** container to edit it. Change the degree of freedom on both lines to `2`.
The degrees of freedom associated with the first set defined in an equation are eliminated from the stiffness matrix. Therefore, this set should not appear in other constraint equations, and boundary conditions should not be applied to the eliminated degrees of freedom.
**Modeling the pin joint between the cross bracing and the trusses**
The cross bracing, unlike the internal truss bracing, is bolted to the truss members. You can assume that these bolted connections are unable to transmit rotations or torsion. The duplicate vertices that were defined at these locations are needed to define this constraint. In Abaqus such constraints can be defined using multi-point constraints, constraint equations, or connectors. In this example the last approach is adopted.
Connectors allow you to model a connection between any two points in a model assembly (or between any single point in the assembly and the ground). A large library of connectors is available in Abaqus. See &#8220;Connector element library,&#8221;  Section 31.1.4 of the Abaqus Analysis User's Guide, for a complete list and a description of each connector type.
The JOIN connector will be used to model the bolted connection. The pinned joint created by this connector constrains the displacements to be equal but the rotations (if they exist) remain independent.
In Abaqus/CAE connectors are modeled using connector section assignments. You create an assembly-level wire feature to define the connector geometry and a connector section to define the connection type. You can model connectors at all of the pin joints using one connector section assignment. You create the connector section assignment by selecting multiple wires and specifying a connector section to assign to the selected wires (similar to the association between elements and their section properties). For connections between coincident points, a specialized tool is available to simplify the modeling process. This tool is used here.
**To define the connectors:**
-
From the main menu bar in the Interaction module, select **Connector**../images/arrow.gif**Coincident Builder**.
-
Use the **Selection** toolbar to restrict your selection to **Vertices**.
-
In the viewport, drag the cursor around the entire model, then click **Done** in the prompt area.
Ten pairs of points should appear in the **Coincident Point Builder** table. Each corresponds to one of the pin joint locations labeled `a`&#8211;`j` in [Figure 6&#8211;17](ch06s04.html#gss-crane-datum-c).
-
In the **Coincident Point Builder** dialog box, click ../graphics/ico_connectorSection.png to create a section property.
-
In the **Create Connector Section** dialog box, select **Basic** as the **Connection Category**. From the list of available translational types, select **Join**. Accept all other defaults, and click **Continue**.
-
No additional section specifications are required. Thus, in the connector section editor that appears, click **OK**.
-
Click **OK** in the **Coincident Point Builder** dialog box to create the connections.
**Defining loads and boundary conditions**
A total load of 10 kN is applied in the negative *y*-direction to the ends of the truss. Recall there is a constraint equation connecting the *y*-displacement of sets `Tip-a` and `Tip-b`, where the degree of freedom for set `Tip-a` is eliminated from the system equations. Thus, apply the load as a concentrated force of magnitude `&#8211;10000` to set `Tip-b`. Name the load `Tip load`. Because of the constraint, the load will be carried equally by both trusses.
The crane is attached firmly to the parent structure. Create an encastre boundary condition named `Fixed end`, and apply it to set `Attach`.
**Creating the mesh**
The cargo crane will be modeled with three-dimensional, slender, cubic beam elements (B33). The cubic interpolation in these elements allows us to use a single element for each member and still obtain accurate results under the applied bending load. The mesh that you should use in this simulation is shown in [Figure 6&#8211;24](ch06s04.html#gss-cargo-crane).
**Figure 6&#8211;24** Mesh for cargo crane.
../graphics/gss-cargo-crane-v.png
In the Model Tree,  expand the **Truss** item underneath the **Parts** container. Then double-click **Mesh** in the list that appears. Specify a global part seed of `2.0` for all regions. Repeat this for the part named **Cross brace**.
Tip:&nbsp;
In the context bar of the Mesh module, select the appropriate part from the **Object** pull-down list to switch between the parts more readily. Mesh both part instances with linear cubic beams in space (B33 elements).
**Using the Keywords Editor and defining the job**
You will now add the keyword options that are necessary to complete the model definition (namely, the option to define beam normal directions) using the **Keywords Editor**. Refer to the Abaqus Keywords Reference Guide for a description of the required syntax, if necessary.
**To add options in the Keywords Editor:**
-
In the Model Tree, click mouse button 3 on **Model-1** and select **Edit Keywords** from the menu that appears.
The **Edit Keywords** dialog box appears containing the input file that has been generated for your model.
-
In the **Keywords Editor** each keyword is displayed in its own block. Only text blocks with a white background can be edited. Select the text block that appears just prior to the *END ASSEMBLY option. Click **Add After** to add an empty block of text.
-
In the block of text that appears, enter the following:```
*NORMAL, TYPE=ELEMENT
Inner-a,  Inner-a, -0.3962,  0.9171,  0.0446
Inner-b,  Inner-b,  0.3962, -0.9171,  0.0446
Leg-a,    Leg-a,   -0.1820,  0.9829,  0.0205
Leg-b,    Leg-b,    0.1820, -0.9829,  0.0205
```
Tip:&nbsp;
Copy and paste data from one location in a text block to another.
-
When you have finished, click **OK** to exit the **Keywords Editor**.
Before continuing, rename the model to `Static`. This model will later form the basis of the model used in the crane example discussed in [Chapter 7, &#8220;Linear Dynamics](ch07.html).&#8221;
Save your model in a model database file named `Crane.cae`, and create a job named `Crane`.
Submit the job for analysis, and monitor the solution progress. If any modeling errors are encountered, correct them; investigate the cause of any warning messages, taking appropriate action as necessary.6.4.2&nbsp;Postprocessing
Switch to the Visualization module, and open the file `Crane.odb`. Abaqus displays an undeformed shape plot of the crane model.
**Plotting the deformed model shape**
To begin this exercise, plot the deformed model shape with the undeformed model shape superimposed on it. Specify a nondefault view using (0, 0, 1) as the *X*-, *Y*-, and *Z*-coordinates of the viewpoint vector and (0, 1, 0) as the *X*-, *Y*-, and *Z*-coordinates of the up vector.
Tip:&nbsp;
You can also display the model using this view by clicking ../graphics/ico_viewFront.png from the **Views** toolbar.
The undeformed shape of the crane superimposed upon the deformed shape is shown in [Figure 6&#8211;25](ch06s04.html#gss-displaced-hoist).
**Figure 6&#8211;25** Deformed shape of cargo crane.
../graphics/gss-displaced-hoist-c.png
**Using display groups to plot element and node sets**
You can use display groups to plot existing node and element sets; you can also create display groups by selecting nodes or elements directly from the viewport. You will create a display group containing only the elements associated with the main members in truss structure A.
**To create and plot a display group:**
-
In the Results Tree, expand the **Sections** container underneath the output database file named `Crane.odb`.
-
To facilitate your selection, change the view back to the default isometric view using the ../graphics/ico_viewIso.png tool in the **Views** toolbar.
Tip:&nbsp;
If the **Views** toolbar is not visible, select **View**../images/arrow.gif**Toolbars**../images/arrow.gif**Views** from the main menu bar.
-
In succession, click the items in the container until the elements associated with the main members in truss A are highlighted in the viewport. Click mouse button 3 on this item and select **Replace** from the menu that appears.
Abaqus/CAE now displays only this group of elements.
-
To save this group,  double-click **Display Groups** in the Results Tree; or use the ../graphics/ico_displayGroupCreate.png tool in the **Display Group** toolbar.
The **Create Display Group** dialog box appears.
-
In the **Create Display Group** dialog box, click **Save As** and enter `MainA` as the name for your display group.
-
Click **Dismiss** to close the **Create Display Group** dialog box.
This display group now appears underneath the **Display Groups** container in the  Results Tree.
**Beam cross-section orientation**
You will now plot the section axes and beam tangents on the undeformed model shape.
**To plot the beam section axes:**
-
From the main menu bar, select **Plot**../images/arrow.gif**Undeformed Shape**; or use the ../graphics/ico_plotUndeformed.png tool in the toolbox to display only the undeformed model shape.
-
From the main menu bar, select **Options**../images/arrow.gif**Common**; then, click the **Normals** tab in the dialog box that appears.
-
Toggle on **Show normals**, and accept the default setting of **On elements**.
-
In the **Style** area at the bottom of the **Normals** page, specify the **Length** to be **Long**.
-
Click **OK**.
The section axes and beam tangents are displayed on the undeformed shape.
The resulting plot is shown in [Figure 6&#8211;26](ch06s04.html#gss-beamsectaxes). The text annotations in [Figure 6&#8211;26](ch06s04.html#gss-beamsectaxes) that identify the section axes and beam tangent will not appear in your image. The vector showing the local beam 1-axis, ../graphics/gsa_eqn00046.gif, is blue; the vector showing the beam 2-axis, ../graphics/gsa_eqn00047.gif, is red; and the vector showing the beam tangent, ../graphics/gsa_eqn00045.gif, is white.
**Figure 6&#8211;26** Plot of beam section axes and tangents for elements in display group `MainA`.
../graphics/gss-beamsectaxes-v-nls.png
**Rendering beam profiles**
You will now display an idealized representation of the beam profile and contour the stress results.
**To render beam profiles:**
-
From the main menu bar, select **View**../images/arrow.gif**ODB Display Options**.
The **ODB Display Options** dialog box appears.
-
In the **General** tabbed page, toggle on **Render beam profiles** and accept the default scale factor of 1.
-
Click **OK**.
Abaqus/CAE displays beam profiles with the appropriate dimensions and in the correct orientations. [Figure 6&#8211;27](ch06s04.html#usi-prp-cargocrane) shows the beam profiles on the whole model. Your changes are saved for the duration of the session.
-
Click ../graphics/ico_plotContourDeformed.png to contour the Mises stress on the rendered profile.
**Figure 6&#8211;27** Cargo crane with beam profiles displayed.
../graphics/usi-prp-cargocrane.png
**Creating a hard copy**
You can save the current image to a file for hard-copy output.
**To create a PostScript file of the current image:**
-
From the main menu bar, select **File**../images/arrow.gif**Print**.
The **Print** dialog box appears.
-
From the **Settings** area in the **Print** dialog box, select **Black&amp;White** as the **Rendition** type; and toggle on **File** as the **Destination**.
-
Select **PS** as the **Format**, and enter `beam.ps` as the **File name**.
-
Click ../graphics/ico_selectionOptions.png.
The **PostScript Options** dialog box appears.
-
From the **PostScript Options** dialog box, select **600 dpi** as the **Resolution**; and toggle off **Print date**.
-
Click **OK** to apply your selections and to close the dialog box.
-
In the **Print** dialog box, click **OK**.
Abaqus/CAE creates a PostScript file of the current image and saves it in your working directory as `beam.ps`. You can print this file using your system's command for printing PostScript files.
**Displacement summary**
Write a summary of the displacements of all nodes in display group `MainA` to a file named `crane.rpt`. The peak displacement at the tip of the crane in the 2-direction is 0.0188&nbsp;m.
**Section forces and moments**
Abaqus can provide output for structural elements in terms of forces and moments acting on the cross-section at a given point. These section forces and moments are defined in the local beam coordinate system. Toggle off the rendering of beam profiles, then contour the section moment about the beam 1-axis in the elements in display group `MainA`. For clarity, reset the view so that the elements are displayed in the 1&#8211;2 plane.
**To create a &#8220;bending moment&#8221;-type contour plot:**
-
From the list of variable types on the left side of the **Field Output** toolbar, select **Primary**.
-
From the list of output variables in the center of the toolbar, select **SM**.
Abaqus/CAE automatically selects **SM1**, the first component name in the list on the right side of the **Field Output** toolbar, and displays a contour plot of the bending moment about the beam 1-axis on the deformed model shape. The deformation scale factor is chosen automatically since geometric nonlinearity was not considered in the analysis.
-
Open the **Common Plot Options** dialog box, and select a **Uniform** deformation scale factor of `1.0`.
Color contour plots of this type typically are not very useful for one-dimensional elements such as beams. A more useful plot is a &#8220;bending moment&#8221;-type plot, which you can produce using the contour options.
-
From the main menu bar, select **Options**../images/arrow.gif**Contour**; or use the **Contour Options** ../graphics/ico_plotContourOptions.png tool in the toolbox.
The **Contour Plot Options** dialog box appears; by default, the **Basic** tab is selected.
-
In the **Contour Type** field, toggle on **Show tick marks for line elements**.
-
Click **OK**.
The plot shown in [Figure 6&#8211;28](ch06s04.html#gss-beambending) appears. The magnitude of the variable at each node is now indicated by the position at which the contour curve intersects a &#8220;tick mark&#8221; drawn perpendicular to the element. This &#8220;bending moment&#8221;-type plot can be used for any variable (not just bending moments) for any one-dimensional element, including trusses and axisymmetric shells as well as beams.
**Figure 6&#8211;28** Bending moment diagram (moment about beam 1-axis) for elements in display group `MainA`. The locations with the highest stress (created by the bending of the elements) are indicated.
../graphics/gss-beambending-c.png

## 6.5&nbsp;Related Abaqus examples

6.5&nbsp;Related Abaqus examples
-
&#8220;Detroit Edison pipe whip experiment,&#8221;  Section 2.1.2 of the Abaqus Example Problems Guide
-
&#8220;Buckling analysis of beams,&#8221;  Section 1.2.1 of the Abaqus Benchmarks Guide
-
&#8220;Crash simulation of a motor vehicle,&#8221;  Section 1.3.14 of the Abaqus Benchmarks Guide
-
&#8220;Geometrically nonlinear analysis of a cantilever beam,&#8221;  Section 2.1.2 of the Abaqus Benchmarks Guide

## 6.6&nbsp;Suggested reading

6.6&nbsp;Suggested reading
**Basic beam theory**
-
Timoshenko, S., *Strength of Materials: Part II*, Krieger Publishing Co., 1958.
-
Oden, J. T. and E. A. Ripperger, *Mechanics of Elastic Structures*, McGraw-Hill, 1981.
**Basic computational beam theory**
-
Cook, R. D., D. S. Malkus, and M. E. Plesha, *Concepts and Applications of Finite Element Analysis*, John Wiley &amp; Sons, 1989.
-
Hughes, T. J. R., *The Finite Element Method*, Prentice-Hall Inc., 1987.

## 6.7&nbsp;Summary

6.7&nbsp;Summary
-
The behavior of beam elements can be determined by numerical integration of the section or can be given directly in terms of area, moments of inertia, and torsional constant.
-
When defining beam cross-section properties numerically, you can have the section properties calculated once at the beginning of the analysis (linear elastic material behavior is assumed) or throughout the analysis (linear or nonlinear material behavior is permitted).
-
Abaqus includes a number of standard cross-section shapes. Other shapes, provided they are &#8220;thin-walled,&#8221;&nbsp;can be modeled using the ARBITRARY cross-section.
-
The orientation of the cross-section must be defined either by specifying a third node or by defining a normal vector as part of the element property definition. The normals can be plotted in the Visualization module of Abaqus/CAE.
-
The beam cross-section can be offset from the nodes that define the beam. This procedure is useful in modeling stiffeners on shells.
-
The linear and quadratic beams include the effects of shear deformation. The cubic beams in Abaqus/Standard do not account for shear flexibility. The open-section beam elements in Abaqus/Standard correctly model the effects of torsion and warping (including warping constraints) in thin-walled, open sections.
-
Multi-point constraints, constraint equations, and connectors can be used to connect degrees of freedom at nodes to model pinned connections, rigid links, etc.
-
&#8220;Bending moment&#8221;-type plots allow the results of one-dimensional elements, such as beams, to be visualized easily.
-
Display options allow you to render beam profiles for an enhanced graphical representation of the model.
-
Hard copies of Abaqus/CAE plots can be obtained in PostScript (PS), Encapsulated PostScript (EPS), Tag Image File Format (TIFF), Portable Network Graphics (PNG), and Scalable Vector Graphics (SVG) formats.

