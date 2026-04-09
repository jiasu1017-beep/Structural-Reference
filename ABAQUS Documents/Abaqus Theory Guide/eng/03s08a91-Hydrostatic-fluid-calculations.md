# 3.8.1 Hydrostatic fluid calculations

### 3.8.1 Hydrostatic fluid calculations

**Products: **Abaqus/Standard  Abaqus/Explicit

Abaqus provides a capability that can be used to represent fluid-filled cavities under hydrostatic conditions. The capability provides the coupling between the deformation of the fluid-filled structure and the pressure exerted by the contained fluid on the boundary of the cavity. In Abaqus/Explicit the fluid must be compressible and the pressure is calculated from the cavity volume. In Abaqus/Standard the fluid inside the cavity can be compressible or incompressible, with the fluid volume given as a function of the fluid pressure, *p*; the fluid temperature, ![](../graphics/stm_eqn01111.gif); and the fluid mass, *m*, in the cavity:

![](../graphics/stm_eqn05015.gif)We refer to the incompressible case as a "hydraulic" fluid and to the compressible case as a "pneumatic" fluid. The volume, ![](../graphics/stm_eqn05016.gif), derived from the fluid pressure and temperature should equal the actual volume, *V*, of the cavity. In Abaqus/Standard this is achieved by augmenting the virtual work expression for the structure with the constraint equation

![](../graphics/stm_eqn05017.gif)and the virtual work contribution due to the cavity pressure:

![](../graphics/stm_eqn05018.gif)where ![](../graphics/stm_eqn05019.gif) is the augmented virtual work expression and ![](../graphics/stm_eqn05020.gif) is the virtual work expression for the structure without the cavity. The negative signs imply that an increase in the cavity volume releases energy from the fluid. This represents a mixed formulation in which the structural displacements and fluid pressure are primary variables. The rate of the augmented virtual work expression is obtained as

![](../graphics/stm_eqn05021.gif)Here, ![](../graphics/stm_eqn05022.gif) represents the pressure load stiffness, and ![](../graphics/stm_eqn05023.gif) is the volume-pressure compliance of the fluid.

Since the pressure is the same for all surface facets (or elements) in the cavity, the augmented virtual work expression can be written as the sum of the expressions for the individual surface facets:

![](../graphics/stm_eqn05024.gif)Moreover, since the temperature is the same for all cavity facets, the fluid volume can be calculated for each facet individually:

![](../graphics/stm_eqn05025.gif)where ![](../graphics/stm_eqn05026.gif) is the element mass. In the solution the actual volume of the element may be different from the element volume:

![](../graphics/stm_eqn05027.gif)however, the total fluid volume will match the volume of the cavity.
### Hydraulic fluid with thermal expansion

In Abaqus/Standard the fluid is incompressible by default and the fluid volume, ![](../graphics/stm_eqn05016.gif), is dependent upon temperature but independent of the fluid pressure:

![](../graphics/stm_eqn05028.gif)If compressibility is introduced, the fluid volume depends upon both the temperature and pressure:

![](../graphics/stm_eqn05029.gif)where *K* is the fluid bulk modulus and ![](../graphics/stm_eqn05030.gif) is the reference fluid density at zero pressure and the initial temperature.

The total fluid mass in the cavity is the sum of the fluid masses of the elements making up the cavity:

![](../graphics/stm_eqn05031.gif)The mass of a fluid element in the cavity, ![](../graphics/stm_eqn05026.gif), is calculated from the initial fluid density, ![](../graphics/stm_eqn05032.gif), and the initial element volume, ![](../graphics/stm_eqn05033.gif):

![](../graphics/stm_eqn05034.gif)where ![](../graphics/stm_eqn05035.gif) is the initial fluid pressure and ![](../graphics/stm_eqn05036.gif) is the initial temperature. The initial fluid density follows from the user-defined reference density, ![](../graphics/stm_eqn05030.gif):

![](../graphics/stm_eqn05037.gif)

The fluid density at the current pressure and temperature, ![](../graphics/stm_eqn05038.gif), is obtained as

![](../graphics/stm_eqn05039.gif)where ![](../graphics/stm_eqn05040.gif) is the reference temperature for the coefficient of thermal expansion and ![](../graphics/stm_eqn05041.gif) is the mean (secant) coefficient of thermal expansion, and it is assumed that ![](../graphics/stm_eqn05042.gif).

Thus, the fluid volume at the current pressure and temperature is

![](../graphics/stm_eqn05043.gif)This volume can be calculated on an element by element basis:

![](../graphics/stm_eqn05044.gif)

Fluid can be added to or removed from the cavity. The amount of fluid added is given as the change in (fluid) mass ![](../graphics/stm_eqn05045.gif). Consequently, the change of the fluid volume at the current cavity temperature is

![](../graphics/stm_eqn05046.gif)
### Ideal gas

In this case the fluid is compressible, and the volume is a function of the pressure and the temperature in the cavity:

![](../graphics/stm_eqn05047.gif)where, as before, the total fluid mass in the cavity is the sum of the masses of the elements in the cavity. The fluid is assumed to behave like an ideal gas; hence, the density of the fluid in the cavity can be calculated as

![](../graphics/stm_eqn05048.gif)where ![](../graphics/stm_eqn05049.gif) is the gas constant, ![](../graphics/stm_eqn05050.gif) is the temperature at absolute zero, and ![](../graphics/stm_eqn05051.gif) is the ambient pressure. The current fluid volume can again be calculated on an element by element basis:

![](../graphics/stm_eqn05052.gif)The corresponding volume-pressure compliance is

![](../graphics/stm_eqn05053.gif)Fluid can be added to or removed from the cavity. The amount of fluid added is again given as the change in (fluid) mass. Consequently, the change of the fluid volume at the current cavity temperature is

![](../graphics/stm_eqn05046.gif)
### Volume calculation

The hydrostatic fluid elements appear as surface elements that cover the cavity boundary, but they are actually volume elements when the cavity reference node is accounted for. [Figure 3.8.1&#8211;1](03s08a91-Hydrostatic-fluid-calculations.md) depicts the 4-node hydrostatic fluid volume element, F3D4. The dashed lines indicate that the element is actually pyramidal in shape.

Figure 3.8.1&#8211;1 F3D4 hydrostatic fluid element.

![](../graphics/stmf3d4-nls.png)

The volume, ![](../graphics/stm_eqn05054.gif), of each element must be calculated. The coordinates of any point on the base of the pyramid element can be found by

![](../graphics/stm_eqn05055.gif)where ![](../graphics/stm_eqn02249.gif) are the interpolation functions for the base of the pyramid ("Solid isoparametric quadrilaterals and hexahedra,"  Section 3.2.4), expressed in terms of parametric coordinates *g* and *h*; ![](../graphics/stm_eqn00996.gif) are the nodal coordinates; and the summation extends over all nodes on the base. For three-dimensional elements the Jacobian on the surface is calculated as

![](../graphics/stm_eqn05056.gif)The normal to the element face, ![](../graphics/stm_eqn00483.gif), multiplied by an infinitesimal area, ![](../graphics/stm_eqn02623.gif), of the element face is, hence, obtained as

![](../graphics/stm_eqn05057.gif)The infinitesimal volume, ![](../graphics/stm_eqn00798.gif), associated with this infinitesimal area is

![](../graphics/stm_eqn05058.gif)where ![](../graphics/stm_eqn05059.gif) is the position of the cavity reference node. The volume of the element, ![](../graphics/stm_eqn05054.gif), is then obtained by integration. For a quadrilateral base this yields

![](../graphics/stm_eqn05060.gif)The integration boundaries will be different for a triangular base. Introducing the relative position, ![](../graphics/stm_eqn05061.gif), this becomes

![](../graphics/stm_eqn05062.gif)The variation in the element volume is readily obtained as

![](../graphics/stm_eqn05063.gif)This expression includes contributions to the volume change due to variation in the "sides" of the pyramid element. Hence, the equivalent forces will also include the effect of the pressure on these sides. The pressure on the sides will be balanced by the pressure on the side of the adjacent pyramid element; hence, we only need to calculate the contribution from the pressure on the "base" of the pyramid. This can be done by separating the contributions by using partial integration, which yields

![](../graphics/stm_eqn05064.gif)The last two integrals represent the contributions on the sides of the pyramid; hence, the resulting expression is

![](../graphics/stm_eqn05065.gif)This equation can readily be obtained directly (see "Pressure load stiffness,"  Section 6.5.1).

The second variation of the expression for the volume is

![](../graphics/stm_eqn05066.gif)Similar expressions can be obtained for planar and axisymmetric fluid elements. For a planar element the volume is readily obtained as

![](../graphics/stm_eqn05067.gif)where ![](../graphics/stm_eqn00016.gif) is the unit vector in the direction perpendicular to the plane. Similarly, for axisymmetric elements

![](../graphics/stm_eqn05068.gif)The first and second variations are obtained in the same way as for three-dimensional elements.

The integrations can be carried out analytically. For example, for element type F3D4 the above expressions yield, after some manipulation,

![](../graphics/stm_eqn05069.gif)where ![](../graphics/stm_eqn05070.gif), ![](../graphics/stm_eqn05071.gif) denote the relative nodal coordinates. The first variation (involving the base only) is equal to

![](../graphics/stm_eqn05072.gif)and the second variation of the volume is

![](../graphics/stm_eqn05073.gif)
### Fluid exchange

Abaqus provides a capability that can be used to model fluid flow between two cavities or between a cavity and the outside world. This is typically used when the fluid has to flow through a narrow orifice. It is assumed that the mass flow rate, *q*, is a homogeneous function of the pressure difference, ![](../graphics/stm_eqn05074.gif). In addition, it is assumed that the flow rate may depend on the average temperature---![](../graphics/stm_eqn05075.gif)---and, for a compressible fluid, on the average pressure---![](../graphics/stm_eqn05076.gif):

![](../graphics/stm_eqn05077.gif)

The flow rate needs to be integrated over a finite increment. We assume that the dependence on the average pressure, ![](../graphics/stm_eqn05078.gif), is weak. Hence, we use a semi-implicit method: we use ![](../graphics/stm_eqn01051.gif) at the end of the increment and ![](../graphics/stm_eqn05079.gif) at the start of the increment. For the temperature we choose ![](../graphics/stm_eqn05080.gif) to be the average of ![](../graphics/stm_eqn05081.gif) at the start and end of the increment, because this is likely to be the most accurate. Hence, we obtain the mass flow as:

![](../graphics/stm_eqn05082.gif)

This mass change needs to be converted to a volume change in each cavity. It is assumed that the fluid in both cavities is the same, but the pressures (and possibly the temperatures) may be different. With use of the pressure and temperature-dependent density ![](../graphics/stm_eqn05083.gif) for each cavity *i*, the relations become

![](../graphics/stm_eqn05084.gif)and

![](../graphics/stm_eqn05085.gif)Observe that, except for isothermal incompressible fluids, the resulting matrix is nonsymmetric. For an incompressible fluid with thermal expansion, the nonsymmetric contribution is small and the equations can be symmetrized without significant degradation in convergence rate. For an ideal gas, the nonsymmetric terms can have a significant effect if the drop in pressure is large.

Many applications of fluid flow between cavities involve dynamic loading in the form of steady-state vibration; and often in such cases the dissipative losses in the link between the cavities must be modeled to obtain useful results. In most problems of this class the fluids on either side of the fluid link are first pressurized statically. In the implementation in Abaqus/Standard, it is assumed that the vibration amplitude is sufficiently small that the fluid link response in the dynamic phase of the problem can be treated as linear perturbations about the prepressurized state.

For small vibrations about a prepressurized state we linearize [Equation 3.8.1&#8211;1](03s08a91-Hydrostatic-fluid-calculations.md) to give

![](../graphics/stm_eqn05086.gif)The mass flow through the link can, therefore, be derived as follows:

![](../graphics/stm_eqn05087.gif)

Substituting the above expression for mass flow into [Equation 3.8.1&#8211;2](03s08a91-Hydrostatic-fluid-calculations.md) and noting that ![](../graphics/stm_eqn05088.gif) yields

![](../graphics/stm_eqn05089.gif)

In Abaqus this model is provided only for the direct-solution steady-state dynamic analysis procedure.
### Negative eigenvalues

It is possible that negative eigenvalues will be encountered in the solution of certain hydrostatic fluid element problems. With standard elements this can indicate that a bifurcation or buckling load has been exceeded. However, this is not necessarily true with hydrostatic fluid elements; negative eigenvalues can result solely from the numerical implementation.

Consider the simple hydrostatic fluid model depicted in [Figure 3.8.1&#8211;2](03s08a91-Hydrostatic-fluid-calculations.md).

Figure 3.8.1&#8211;2 Simple hydrostatic fluid model.

![](../graphics/stmsimplefluid-nls.png)If the fluid is considered incompressible, application of the downward force causes the fluid to compress vertically and expand horizontally, while maintaining the original fluid volume. Thus, the model can be adequately discretized as a three degree of freedom system: the horizontal displacement of the right platen, *u*; the vertical displacement of the top platen, *v*; and the fluid pressure, *p*. The corresponding system of equations in matrix form is

![](../graphics/stm_eqn05090.gif)

The equation solver processes the equations in sequence. Hence, it will process the ![](../graphics/stm_eqn05091.gif) submatrix relating the displacements to the forces prior to processing the constraints. This leads to a negative eigenvalue if ![](../graphics/stm_eqn05092.gif). However since the mode associated with the negative eigenvalue is subsequently constrained by the continuity equation, no instability occurs.
### Reference

### Reference

"Surface-based fluid cavities: overview,"  Section 11.5.1 of the Abaqus Analysis User's Guide