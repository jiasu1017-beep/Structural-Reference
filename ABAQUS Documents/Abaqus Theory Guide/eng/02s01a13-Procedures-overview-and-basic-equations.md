# 2.1.1 Procedures: overview and basic equations

### 2.1.1 Procedures: overview and basic equations

Abaqus is designed as a flexible tool for finite element modeling. An important aspect of this flexibility is the manner in which Abaqus allows the user to step through the history to be analyzed. This is accomplished by defining *analysis procedures.*

A basic concept in Abaqus is the division of the problem history into *steps*. A step is any convenient phase of the history---a thermal transient, a creep hold, a dynamic transient, etc. In its simplest form in Abaqus/Standard, a "step" is just a static analysis of a load change from one magnitude to another.

In each "step" the user chooses a *procedure*, thus defining the type of analysis to be performed during the step: dynamic stress analysis, eigenvalue buckling, transient heat transfer analysis, etc. The procedure choice can be changed from step to step in any meaningful way. Since the state of the model (stresses, strains, temperatures, etc.) is updated throughout all analysis steps, the effects of previous history are always included in the response in each new step. Thus, for example, if natural frequency extraction is performed after a geometrically nonlinear static analysis step, the preload stiffness will be included.

Abaqus/Standard provides both linear and nonlinear response options. The program is truly integrated, so linear analysis is always considered as linear perturbation analysis about the state at the time when the linear analysis procedure is introduced. This linear perturbation approach allows general application of linear analysis techniques in cases where the linear response depends on preloading or the nonlinear response history of the model.

In nonlinear problems the objective is to obtain a convergent solution at a minimum cost. The nonlinear procedures in Abaqus/Standard offer two approaches to this. Direct user control of increment size is one choice, whereby the user specifies the incrementation scheme. Automatic control is the alternate approach: the user defines the step and specifies certain tolerances or error measures. Abaqus/Standard then automatically selects the increments as it develops the response in the step. This approach is usually more efficient, because the user cannot predict the response ahead of time. Automatic control is particularly valuable in cases where the time or load increment varies widely through the step, as is often the case in diffusion type problems (such as creep, heat transfer, and consolidation).

In Abaqus/Explicit the time incrementation is controlled by the stability limit of the central difference operator. The time incrementation scheme is, hence, fully automatic and requires no user intervention. User-specified time incrementation is not available because it would always be nonoptimal.

Abaqus/Standard and Abaqus/Explicit are separate program modules with different data structures; hence, the explicit dynamics procedure cannot be used in the same analysis as any of the procedures in Abaqus/Standard. However, Abaqus provides a capability to import a deformed mesh and associated material state from Abaqus/Explicit into Abaqus/Standard and vice versa. This procedure is described in "Transferring results between Abaqus/Explicit and Abaqus/Standard,"  Section 9.2.2 of the Abaqus Analysis User's Guide.

In this chapter the basic equations for the most important analysis procedures in Abaqus/Standard and Abaqus/Explicit are described. In some sections specific aspects of an analysis procedure (i.e., damping, cavity radiation, etc.) are discussed.
### Basic finite element equations

This section describes the basic equations for standard displacement-based finite element analysis. We begin with the equilibrium statement, written as the virtual work principle, [Equation 1.5.1&#8211;6](01s05a08-Equilibrium-and-virtual-work.md):

![](../graphics/stm_eqn00652.gif)

Following the discussion in "Equilibrium and virtual work,"  Section 1.5.1, the left-hand side of this equation (the internal virtual work rate term) is replaced with the integral over the reference volume of the virtual work rate per reference volume defined by any conjugate pairing of stress and strain:

![](../graphics/stm_eqn00653.gif)where ![](../graphics/stm_eqn00654.gif) and ![](../graphics/stm_eqn00404.gif) are any conjugate pairing of material stress and strain measures. The particular choice of ![](../graphics/stm_eqn00404.gif) depends on the individual element---see Chapter 3, "Elements."

The finite element interpolator can be written in general as

![](../graphics/stm_eqn00655.gif)where ![](../graphics/stm_eqn00656.gif) are interpolation functions that depend on some material coordinate system, ![](../graphics/stm_eqn00657.gif) are nodal variables, and the summation convention is adopted for the uppercase subscripts and superscripts that indicate nodal variables.

The virtual field, ![](../graphics/stm_eqn00658.gif), must be compatible with all kinematic constraints. Introducing the above interpolation constrains the displacement to have a certain spatial variation, so ![](../graphics/stm_eqn00658.gif) must also have the same spatial form:

![](../graphics/stm_eqn00659.gif)

The continuum variational statement [Equation 2.1.1&#8211;1](02s01a13-Procedures-overview-and-basic-equations.md) is, thus, approximated by a variation over the finite set ![](../graphics/stm_eqn00660.gif).

Now ![](../graphics/stm_eqn00661.gif) is the virtual rate of material strain associated with ![](../graphics/stm_eqn00658.gif), and because it is a rate form, it must be linear in ![](../graphics/stm_eqn00658.gif). Hence, the interpolation assumption gives

![](../graphics/stm_eqn00662.gif)where ![](../graphics/stm_eqn00663.gif) is a matrix that depends, in general, on the current position, ![](../graphics/stm_eqn00117.gif), of the material point being considered. The matrix ![](../graphics/stm_eqn00663.gif) that defines the strain variation from the variations of the kinematic variables is derivable immediately from the interpolation functions once the particular strain measure to be used is defined.

Without loss of generality we can write ![](../graphics/stm_eqn00664.gif), and---with this notation---the equilibrium equation is approximated as

![](../graphics/stm_eqn00665.gif)since the ![](../graphics/stm_eqn00660.gif) are independent variables, we can choose each one to be nonzero and all others zero in turn, to arrive at a system of nonlinear equilibrium equations:

![](../graphics/stm_eqn00666.gif)

This system of equations forms the basis for the (standard) assumed displacement finite element analysis procedure and is of the form

![](../graphics/stm_eqn00667.gif)discussed above. The above equations are valid for static and dynamic analysis if the body force is assumed to contain the inertia contribution. In dynamic analysis, however, the inertia contribution is more commonly considered separately, leading to the equations

![](../graphics/stm_eqn00668.gif)

For the Newton algorithm (or for the linear perturbation procedure) used in Abaqus/Standard, we need the Jacobian of the finite element equilibrium equations. To develop the Jacobian, we begin by taking the variation of [Equation 2.1.1&#8211;1](02s01a13-Procedures-overview-and-basic-equations.md), giving

![](../graphics/stm_eqn00669.gif)where ![](../graphics/stm_eqn00670.gif) represents the linear variation of the quantity ![](../graphics/stm_eqn00671.gif) with respect to the basic variables (the degrees of freedom of the finite element model). In the above expression ![](../graphics/stm_eqn00672.gif) is the volume change between the reference and the current volume occupied by a piece of the structure and, likewise, ![](../graphics/stm_eqn00673.gif) is the surface area ratio between the reference and the current configuration. The Jacobian matrix is obtained by restricting the above variation, allowing variations in the nodal variables, ![](../graphics/stm_eqn00657.gif), only. Let such a restricted variation be indicated by ![](../graphics/stm_eqn00674.gif). Examining [Equation 2.1.1&#8211;3](02s01a13-Procedures-overview-and-basic-equations.md) term by term with this in mind, we proceed as follows. The first term contains ![](../graphics/stm_eqn00675.gif). We now assume that the constitutive theory allows us to write

![](../graphics/stm_eqn00676.gif)where ![](../graphics/stm_eqn00677.gif) and ![](../graphics/stm_eqn00678.gif) are defined in terms of the current state, direction of straining, etc., and on the kinematic assumptions used to form the generalized strains. See Chapter 4, "Mechanical Constitutive Theories," for a detailed discussion of forming ![](../graphics/stm_eqn00677.gif) and ![](../graphics/stm_eqn00678.gif) for the material models currently available in Abaqus. From the choice of generalized strain measure and interpolation function,

![](../graphics/stm_eqn00679.gif)From the above constitutive assumption,

![](../graphics/stm_eqn00680.gif)Now, since ![](../graphics/stm_eqn00661.gif) is the first variation of ![](../graphics/stm_eqn00404.gif) with respect to nodal variables,

![](../graphics/stm_eqn00681.gif)Thus, the first term in the Jacobian matrix is

![](../graphics/stm_eqn00682.gif)the usual "small-displacement stiffness matrix," except that, since the strain measure ![](../graphics/stm_eqn00404.gif) will always be nonlinear in displacement, the ![](../graphics/stm_eqn00663.gif) in this term will be a function of displacement.

The second term in [Equation 2.1.1&#8211;3](02s01a13-Procedures-overview-and-basic-equations.md) is

![](../graphics/stm_eqn00683.gif)This is rewritten as

![](../graphics/stm_eqn00684.gif)which is

![](../graphics/stm_eqn00685.gif)This term contributes to the Jacobian and is the "initial stress matrix."

The external load rate terms in [Equation 2.1.1&#8211;3](02s01a13-Procedures-overview-and-basic-equations.md) are considered next. In general, these load vectors can be written

![](../graphics/stm_eqn00686.gif)where ![](../graphics/stm_eqn00280.gif) represents the externally prescribed loading parameters. Whether the load depends on position or not depends on the particular load type, but common types of loading (pressure, centrifugal load) do depend on position---for example, if ![](../graphics/stm_eqn00479.gif) is caused by pressure on the surface, ![](../graphics/stm_eqn00479.gif) depends on the pressure magnitude, on the direction of the normal to the surface, and on the current surface area: the latter two are functions of the current position of points on the surface. The variation of the load vector with nodal variables can then be written symbolically as

![](../graphics/stm_eqn00687.gif)

![](../graphics/stm_eqn00688.gif)and then writing

![](../graphics/stm_eqn00689.gif)where ![](../graphics/stm_eqn00690.gif) is obtained directly from the interpolation functions, we can write the Jacobian terms pertaining to the last four terms of [Equation 2.1.1&#8211;3](02s01a13-Procedures-overview-and-basic-equations.md) as

![](../graphics/stm_eqn00691.gif)

These are commonly called the "load stiffness matrix." The actual form of the load stiffness is very much dependent on the type of load being considered---see Chapter 3, "Elements," and [Hibbitt (1979)](07s01a01-References.md) for examples.

The complete Jacobian matrix is then

![](../graphics/stm_eqn00692.gif)

Thus, [Equation 2.1.1&#8211;2](02s01a13-Procedures-overview-and-basic-equations.md) and [Equation 2.1.1&#8211;4](02s01a13-Procedures-overview-and-basic-equations.md) provide the basis for the Newton incremental solution, given specification of the interpolation function and constitutive theories to be used.
### Reference

### Reference

"Defining an analysis,"  Section 6.1.2 of the Abaqus Analysis User's Guide