# 2.18.1 Design sensitivity analysis

### 2.18.1 Design sensitivity analysis

**Product: **Abaqus/Design

Abaqus/Design supports design sensitivity analysis (DSA) for static stress and frequency problems. DSA provides derivatives of certain response quantities with respect to specified input quantities. These derivatives are known as *sensitivities*. The responses available for DSA are a subset of the list of Abaqus output variables and are known as *design responses*; the specified input quantities are known as *design parameters*. Quantities that are functions of design parameters are referred to as being design dependent. The DSA theory is presented from the perspective of computing the required derivatives analytically, first for static stress analysis and then for frequency analysis. At the end of each section an alternative numerical approach based on this theory is discussed.
### DSA for static stress analysis

The equations pertaining to DSA can be derived based on a total displacement formulation or an incremental displacement formulation. The total displacement formulation is intended for history-independent problems, where the current state of the problem depends only on the total displacements. The incremental formulation is intended for history-dependent problems, where the current state of the problem depends on the state at the beginning of the increment and the incremental displacements.Total displacement DSA formulation for nonlinear equilibrium problems

Let *R* and *P* be the numbers of design responses and design parameters, respectively. Let each response ![](../graphics/stm_eqn02773.gif), ![](../graphics/stm_eqn02774.gif), be a function of design parameters ![](../graphics/stm_eqn02775.gif), ![](../graphics/stm_eqn02776.gif) and depend on them both explicitly and via the displacement field represented here by the nodal displacement vector ![](../graphics/stm_eqn00657.gif) (see the definition of finite element interpolation in "Procedures: overview and basic equations,"  Section 2.1.1),

![](../graphics/stm_eqn02777.gif)The dependence ![](../graphics/stm_eqn02778.gif) is only implicit; i.e., it is implied only by the design dependence of coefficients in the equilibrium equation system whose solution is ![](../graphics/stm_eqn00657.gif).

Assume that we have solved an equilibrium problem defined by [Equation 2.1.1&#8211;2](02s01a13.md) at the end of an increment and that we have the converged solution ![](../graphics/stm_eqn00657.gif) as well as values of all responses. Sensitivity of a response ![](../graphics/stm_eqn02779.gif) with respect to design parameter ![](../graphics/stm_eqn02780.gif) is defined as

![](../graphics/stm_eqn02781.gif)All but one quantity in the above equation can be determined explicitly given the equilibrium solution. The only unknown is ![](../graphics/stm_eqn02782.gif); to compute it, an additional system of equations has to be solved.

Rewrite [Equation 2.1.1&#8211;2](02s01a13.md) in the form

![](../graphics/stm_eqn02783.gif)where

![](../graphics/stm_eqn02784.gif)All the quantities in the above equation are assumed to depend on design parameters ![](../graphics/stm_eqn02780.gif) explicitly or via displacement field ![](../graphics/stm_eqn00657.gif). Differentiation of the above two equations with respect to design parameters leads to the following equation:

![](../graphics/stm_eqn02785.gif)in which

![](../graphics/stm_eqn02786.gif)is the tangent stiffness (Jacobian) matrix defined in [Equation 2.1.1&#8211;4](02s01a13.md) and ![](../graphics/stm_eqn02787.gif) is an explicitly determinable quantity. Substituting [Equation 2.18.1&#8211;3](02s18a57.md) into [Equation 2.18.1&#8211;1](02s18a57.md), we obtain

![](../graphics/stm_eqn02788.gif)which is the solution of the total displacement DSA problem.

The DSA algorithm used in Abaqus is known as the *direct differentiation method* (DDM) and consists of the following operations. After the converged equilibrium solution is obtained, the three arrays ![](../graphics/stm_eqn02789.gif), ![](../graphics/stm_eqn02790.gif), and ![](../graphics/stm_eqn02791.gif) have to be computed in an element-by-element manner. ![](../graphics/stm_eqn02791.gif) is often called the pseudoload since it becomes the right-hand side of the DSA problem. The final DSA solution is obtained by solving the system of [Equation 2.18.1&#8211;3](02s18a57.md) for each ![](../graphics/stm_eqn02776.gif) with respect to the unknown vectors of nodal displacement sensitivity ![](../graphics/stm_eqn02792.gif). The displacement sensitivities are then substituted into [Equation 2.18.1&#8211;1](02s18a57.md) to compute ![](../graphics/stm_eqn02793.gif).

The coefficient matrix ![](../graphics/stm_eqn02794.gif) used in the DSA computations is simply the last tangent stiffness matrix used in the equilibrium iterative algorithm. At the stage of the DSA computations this matrix is still available in the decomposed form and can be retrieved easily to perform the back substitutions for the DSA right-hand-side vectors. This makes the DSA module a very efficient add-on to the equilibrium analysis enabling sensitivity computations at a relatively low cost.Incremental displacement DSA formulation for history-dependent equilibrium problems

The formulation of DSA presented above provides a brief introduction to the way DSA is implemented in Abaqus; however, due to some simplifications, the discussion is not relevant to a large number of nonlinear mechanical problems, especially those involving history-dependent behavior of the structure modeled. The main difficulty in such problems is that many quantities necessary to compute the residual ![](../graphics/stm_eqn00694.gif) in [Equation 2.18.1&#8211;2](02s18a57.md) or to define design responses do not lend themselves to be expressed as functions of total displacement ![](../graphics/stm_eqn00657.gif). Rather, at each time increment they are functions of certain state variables at the beginning of the increment (referred to as the time instant *t*) and of the incremental displacements, ![](../graphics/stm_eqn02795.gif):

![](../graphics/stm_eqn02796.gif)

![](../graphics/stm_eqn02797.gif)see, for example, [Kleiber et al. (1997)](07s01a01-References.md). The notation ![](../graphics/stm_eqn02798.gif) stands for a set of state variables ![](../graphics/stm_eqn02799.gif) that may include tensors (stress, back stress, etc.) as well as scalar quantities (equivalent plastic strain, etc.) defined for a particular material point at time *t*. Some responses may also depend directly on the displacement ![](../graphics/stm_eqn00657.gif), and the beginning-of-the-increment value of ![](../graphics/stm_eqn00657.gif) will, generally, also enter into the set ![](../graphics/stm_eqn02798.gif).

In such a case [Equation 2.18.1&#8211;4](02s18a57.md) takes the following form:

![](../graphics/stm_eqn02800.gif)where

![](../graphics/stm_eqn02801.gif)denotes the *explicit design derivative* of a quantity ![](../graphics/stm_eqn02802.gif).

The fundamental difference, from the point of view of the DSA solution algorithm, between the total and incremental approach is that in the latter case all state variables ![](../graphics/stm_eqn02799.gif) effectively become additional, or *internal*, design responses, whose sensitivities must be computed and updated at the end of each time increment to proceed with the DSA in the next increment. The number of such internal responses may be significant with obvious effects both on the computational time and memory requirement.

The DSA solution procedure is similar to that in the total displacement approach. After the equilibrium computations are complete, the arrays of explicit design derivatives ![](../graphics/stm_eqn02803.gif), ![](../graphics/stm_eqn02804.gif) (the pseudoload), and the derivatives with respect to displacements ![](../graphics/stm_eqn02805.gif) are assembled in the element loop. The set of design responses ![](../graphics/stm_eqn02773.gif), ![](../graphics/stm_eqn02774.gif), includes in this case all the scalars and tensor components of ![](../graphics/stm_eqn02799.gif). In the direct differentiation method the following system of equations is solved for each design parameter ![](../graphics/stm_eqn02780.gif):

![](../graphics/stm_eqn02806.gif)and the solution vectors are substituted into [Equation 2.18.1&#8211;5](02s18a57.md).Computational approach

The derivatives required for DSA can be computed analytically or numerically. In the analytical approach the finite element equations are differentiated exactly, following the theory described in the previous sections. This approach is difficult to implement, but it is efficient and yields exact sensitivities. In the numerical approach some or all of the required derivatives are computed using the finite difference technique. The numerical approach can be further subdivided into the *overall* or *global* finite difference approach and the *semi-analytic* approach. In the global finite difference approach the response sensitivities with respect to a particular design parameter are obtained by perturbing that design parameter a number of times (depending on the finite difference technique) and performing an entire equilibrium analysis for each perturbation. The responses are retained for each analysis and then differenced to obtain the response sensitivities. This approach is computationally expensive since an entire equilibrium problem must be solved for each perturbation, but it is easily implemented. The semi-analytic approach is used in Abaqus and can be viewed as a compromise between the analytic and global finite difference approaches. In the semi-analytic approach the DSA element vectors are obtained by differencing; but, like the analytic approach, the DSA solution is obtained by back-substitution against ![](../graphics/stm_eqn02794.gif). The advantage of the semi-analytic approach is that it is much easier to implement than the analytic approach and much more efficient than the global finite difference approach. The details of this method are described in the following paragraphs.

The objective of the semi-analytic approach is to compute the DSA vectors ![](../graphics/stm_eqn02804.gif) and ![](../graphics/stm_eqn02807.gif) numerically by finite differencing. For simplicity, assume that the finite difference technique is central difference such that for a given function ![](../graphics/stm_eqn02808.gif), the derivative of *A* with respect to *x* is

![](../graphics/stm_eqn02809.gif)where ![](../graphics/stm_eqn02810.gif) is the perturbation of *x*.

For generality, consider the history-dependent case. To approximate the explicit design derivatives of ![](../graphics/stm_eqn02811.gif), the incremental displacement is held constant while a positive perturbation ![](../graphics/stm_eqn02812.gif) is applied to each design parameter ![](../graphics/stm_eqn02780.gif). In this way perturbed values of ![](../graphics/stm_eqn02811.gif) are obtained as

![](../graphics/stm_eqn02813.gif)The change in the state corresponding to a perturbation in the design parameters is approximated by

![](../graphics/stm_eqn02814.gif)The above process is repeated for a negative perturbation (![](../graphics/stm_eqn02815.gif)), after which the results are differenced to arrive at the explicit design derivative ![](../graphics/stm_eqn02804.gif).

Once the (incremental) displacement sensitivities are found, the response sensitivities ![](../graphics/stm_eqn02816.gif) can be obtained using

![](../graphics/stm_eqn02817.gif) where

![](../graphics/stm_eqn02818.gif) The process is repeated for a negative perturbation of ![](../graphics/stm_eqn02780.gif), and the results are differenced.

The finite difference interval must be chosen carefully. If the interval is too small, round-off or *cancellation* errors occur due to loss of precision during the differencing operations. On the other hand, if the interval is too large, *truncation* errors may occur. Truncation errors arise from the fact that differencing formulas are based on truncated Taylor series expansions. Abaqus will automatically choose a perturbation size that provides the best compromise between cancellation and truncation errors.
### DSA for frequency analysis

This discussion will build upon the concepts and terminology described above, so it is recommended that the previous section be read first. The discussion below is divided into two sections depending on the characteristics of the eigenvalue problem: distinct eigenvalues and repeated eigenvalues.Distinct eigenvalue case

The theory presented below assumes that all the eigenvalues are distinct (i.e., no repeated eigenvalues). If this is not the case, further manipulations are required to obtain the eigenvalue and eigenvector sensitivities corresponding to the repeated eigenvalues, and the following equations for the sensitivities will be incorrect. The repeated eigenvalue case is considered in the next section.

Performing a frequency analysis means solving the following eigenvalue problem (see "Eigenvalue extraction,"  Section 2.5.1):

![](../graphics/stm_eqn02819.gif)where ![](../graphics/stm_eqn00280.gif) represents the eigenvalues, ![](../graphics/stm_eqn02820.gif) represents the eigenvectors, and ![](../graphics/stm_eqn01186.gif) is the mass matrix. In addition, the eigenvectors are scaled such that either

![](../graphics/stm_eqn02821.gif) or

![](../graphics/stm_eqn02822.gif)for each mode. The default is the first scaling scheme. To obtain eigenvalue and eigenvector sensitivities, first differentiate [Equation 2.18.1&#8211;6](02s18a57.md) with respect to design parameter ![](../graphics/stm_eqn02780.gif) to obtain the following equation:

![](../graphics/stm_eqn02823.gif)where ![](../graphics/stm_eqn00904.gif) represents a particular mode number.

Pre-multiplying by ![](../graphics/stm_eqn02824.gif), making use of [Equation 2.18.1&#8211;6](02s18a57.md), and manipulating the result gives the eigenvalue sensitivities:

![](../graphics/stm_eqn02825.gif)Except for the mass and stiffness derivatives, all quantities in this equation are known once the eigenvalue problem has been solved.Repeated eigenvalue case

This section outlines the formulation used to obtain eigenvalue sensitivities for repeated eigenvalues. Further information can be found in the papers by [Mills-Curran](07s01a01-References.md) (1988) and [Shaw](07s01a01-References.md) (1991). When an eigenvalue ![](../graphics/stm_eqn00280.gif) repeats *R* times, the eigenvectors ![](../graphics/stm_eqn02826.gif) associated with ![](../graphics/stm_eqn00280.gif) are linearly independent but not unique---any linear combination of these eigenvectors is also an eigenvector. Because of this non-uniqueness, the eigenvectors may not be continuous or differentiable in the design parameter. However, a set of *R* eigenvectors ![](../graphics/stm_eqn02827.gif) that are continuous and differentiable can be obtained by an orthogonal transformation:

![](../graphics/stm_eqn02828.gif)where ![](../graphics/stm_eqn02829.gif), and ![](../graphics/stm_eqn00007.gif) is to be determined. Replacing the eigenvectors ![](../graphics/stm_eqn02830.gif) with the eigenvectors ![](../graphics/stm_eqn02831.gif) in [Equation 2.18.1&#8211;9](02s18a57.md) and premultiplying by ![](../graphics/stm_eqn02832.gif) yields in matrix notation:

![](../graphics/stm_eqn02833.gif)where ![](../graphics/stm_eqn02834.gif), ![](../graphics/stm_eqn02835.gif) is a diagonal matrix,

![](../graphics/stm_eqn02836.gif)and

![](../graphics/stm_eqn02837.gif)[Equation 2.18.1&#8211;12](02s18a57.md) is recognized as an ![](../graphics/stm_eqn02838.gif) reduced eigenvalue problem whose *R* eigenvalues ![](../graphics/stm_eqn02835.gif) are the eigenvalue sensitivities associated with the repeated eigenvalue ![](../graphics/stm_eqn00280.gif) and whose eigenvectors are ![](../graphics/stm_eqn00007.gif). *N* sensitivities are obtained for the single eigenvalue ![](../graphics/stm_eqn00280.gif). The physical interpertation of this is that a perturbation in the design parameter may cause the original repeated mode to branch into as many as *N* distinct modes (imagine a beam with a circular cross-section perturbed into an elliptical section; the repeated modes associated with the original symmetry of the section now split into distinct modes associated with the minor and major axes of the ellipse).Computational approach

A semi-analytic approach is used to compute the eigenvalue sensitivities. The basic idea of this approach, as outlined in the section on static DSA, is to compute some of the required intermediate derivatives using finite differencing. In the context of DSA for frequency procedures this means that the derivatives of the mass and stiffness matrices are computed using finite differencing.
### Choosing the finite difference interval

Abaqus uses a heuristic algorithm to automatically determine the perturbation sizes to be used in the differencing scheme. The objective of the algorithm is to select the perturbation sizes that lead to accurately computed derivatives. This is done on an element to element basis, so it is possible for a given design parameter that the perturbation size for one element will be different from that of another element. The selection of the perturbation sizes is based on the behavior of a scalar metric ![](../graphics/stm_eqn02839.gif) for each design parameter ![](../graphics/stm_eqn02780.gif). This metric must be both convenient and representative of the terms that are numerically differenced. It is chosen as follows:

Static steps. For static steps the scalar metric is chosen as the norm of the element pseudoload:

![](../graphics/stm_eqn02840.gif)Since an accurate pseudoload is necessary to obtain an accurate sensitivity solution, the norm of the pseudoload is an appropriate choice for ![](../graphics/stm_eqn02839.gif). This choice is also convenient since the pseudoload has to be computed in any case.

Frequency steps. For frequency steps the scalar metric is chosen as the projection of the matrix ![](../graphics/stm_eqn02841.gif) onto an eigenvector ![](../graphics/stm_eqn02842.gif):

![](../graphics/stm_eqn02843.gif)The choice of ![](../graphics/stm_eqn02842.gif) depends on whether a given mode ![](../graphics/stm_eqn00904.gif) has a distinct eigenvalue or is associated with a repeated eigenvalue.

If mode ![](../graphics/stm_eqn00904.gif) has a distinct eigenvalue, ![](../graphics/stm_eqn02842.gif) is taken as ![](../graphics/stm_eqn02824.gif). Consequently, ![](../graphics/stm_eqn02839.gif) becomes simply the numerator of [Equation 2.18.1&#8211;10](02s18a57.md). Therefore, ![](../graphics/stm_eqn02839.gif) is a direct measure of the magnitude of the eigenvalue sensitivity and is also convenient since this term already must be calculated to obtain the eigenvalue sensitivity.

Unlike the distinct eigenvalue case, the sensitivities of a repeated eigenvalue cannot be treated independently. The sensitivities of a repeated eigenvalue are extracted simultaneously from the same reduced eigenvalue system, and this system is obtained by numerical differencing (recall [Equation 2.18.1&#8211;12](02s18a57.md) and [Equation 2.18.1&#8211;13](02s18a57.md)). Consequently a single perturbation size (for each design parameter) must be used to obtain all sensitivities of a repeated eigenvalue. To calculate the single perturbation size, a single scalar metric is obtained by taking ![](../graphics/stm_eqn02842.gif) as the sum of the eigenvectors associated with the repeated eigenvalue. The calculation of ![](../graphics/stm_eqn02839.gif) is similar to the calculation of the matrix ![](../graphics/stm_eqn02644.gif) (the only term in the reduced eigenvalue system obtained by numerical differencing); therefore, this choice ![](../graphics/stm_eqn02839.gif) is both representative of the repeated eigenvalue case and involves differencing calculations that are already being done to obtain the reduced eigenvalue system.The basic idea of the algorithm is compute the scalar metric ![](../graphics/stm_eqn02839.gif) for a range of perturbation sizes ![](../graphics/stm_eqn02844.gif), ![](../graphics/stm_eqn02845.gif), which vary by orders of magnitude. For each ![](../graphics/stm_eqn02844.gif), a corresponding ![](../graphics/stm_eqn02846.gif) is computed. The relative change in ![](../graphics/stm_eqn02839.gif) between consecutive perturbation sizes, calculated as ![](../graphics/stm_eqn02847.gif), is used to measure how close a perturbation size is to optimum. In this range of perturbation sizes the one that yields the smallest relative change, denoted as ![](../graphics/stm_eqn02848.gif), is identified as the best perturbation size, ![](../graphics/stm_eqn02849.gif). If ![](../graphics/stm_eqn02848.gif) is not less than a specified tolerance, the range of perturbation sizes is expanded (up to a certain limit), and the testing continues. It is important to realize that ![](../graphics/stm_eqn02850.gif) is not used directly in assessing the accuracy of the numerical differentiation but rather is intended as a means for determining the optimum perturbation size. Thus, a tighter tolerance on ![](../graphics/stm_eqn02848.gif) causes the algorithm to expend more effort in finding an optimum perturbation size but does not guarantee more accurate sensitivities.
### Reference

### Reference

"Design sensitivity analysis,"  Section 19.1.1 of the Abaqus Analysis User's Guide