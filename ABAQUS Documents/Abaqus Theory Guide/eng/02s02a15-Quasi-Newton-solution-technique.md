# 2.2.2 Quasi-Newton solution technique

### 2.2.2 Quasi-Newton solution technique

**Product: **Abaqus/Standard

A major contribution to the computational effort involved in nonlinear analysis is the solution of the nonlinear equations ([Equation 2.2.1&#8211;1](02s02a14-Nonlinear-solution-methods-in-AbaqusStan.md)). In most cases Abaqus/Standard uses Newton's method to solve these equations, as described in "Nonlinear solution methods in Abaqus/Standard,"  Section 2.2.1. The principal advantage of Newton's method is its quadratic convergence rate when the approximation at iteration *i* is within the "radius of convergence"---that is, when the gradients defined by ![](../graphics/stm_eqn00718.gif) provide an improvement to the solution. The method has two major disadvantages: the Jacobian matrix has to be calculated, and this same matrix has to be solved. The calculation of the Jacobian matrix is a problem because, in many important cases, it is difficult to derive the form of the matrix algebraically. The solution of the Jacobian is a problem because of the computational effort involved: as the problem size increases, the direct solution of the linear equations can dominate the entire computational effort.

There are a number of important nonlinear applications where the Jacobian is symmetric, is fairly well conditioned, and does not change greatly from one iteration to the next. Examples are implicit dynamic time integration with small time increments relative to the periods of the natural vibrations that participate in the response or small-displacement elastic-plastic analysis where the yielding is confined (such as occurs in many practical fracture mechanics applications). In such cases, especially when the problem is large, it can be less expensive to use an alternative to the Newton approach to the solution of the nonlinear equations. The "quasi-Newton" methods are such an approach; and [Matthies and Strang (1979)](07s01a01-References.md) have shown that, for systems of equations with a symmetric Jacobian matrix, the BFGS (Broyden, Fletcher, Goldfarb, Shanno) method can be written in a simple form that is especially effective on the computer and is successful in such applications. This method is implemented in Abaqus/Standard and is described in this section. The user must select this method explicitly: by default, Abaqus/Standard uses the standard Newton method.

The basis of quasi-Newton methods is to obtain a series of improved approximations to the Jacobian matrix, ![](../graphics/stm_eqn00719.gif), that satisfy the secant condition:

![](../graphics/stm_eqn00720.gif)so that ![](../graphics/stm_eqn00721.gif) approaches ![](../graphics/stm_eqn00722.gif) as the iterations proceed. [Equation 2.2.2&#8211;1](02s02a15-Quasi-Newton-solution-technique.md) is the basic quasi-Newton equation.

For convenience we define the change in the residual from one iteration to the next as

![](../graphics/stm_eqn00723.gif)so that [Equation 2.2.2&#8211;1](02s02a15-Quasi-Newton-solution-technique.md) can be written

![](../graphics/stm_eqn00724.gif)where ![](../graphics/stm_eqn00725.gif) is the correction to the solution from the previous iteration, defined in "Nonlinear solution methods in Abaqus/Standard,"  Section 2.2.1.

Matthies and Strang's implementation of the BFGS method is a computationally inexpensive method of creating a series of approximations to ![](../graphics/stm_eqn00726.gif) that satisfy [Equation 2.2.2&#8211;1](02s02a15-Quasi-Newton-solution-technique.md) and retain the symmetry and positive definiteness of ![](../graphics/stm_eqn00721.gif). They accomplish this by updating ![](../graphics/stm_eqn00727.gif) to ![](../graphics/stm_eqn00726.gif) using a "product plus increment" form:

![](../graphics/stm_eqn00728.gif)where

![](../graphics/stm_eqn00729.gif)

In the actual implementation of this version of the BFGS method, each ![](../graphics/stm_eqn00730.gif) is not stored: rather, a "kernel" matrix, ![](../graphics/stm_eqn00731.gif), is used (as the decomposition of ![](../graphics/stm_eqn00732.gif)), and the update is accomplished by premultiplication of the kernel matrix by the terms

![](../graphics/stm_eqn00733.gif)and postmultiplication of the kernel matrix by the terms

![](../graphics/stm_eqn00734.gif)for ![](../graphics/stm_eqn00735.gif). Because of the form of these terms, the premultiplication and postmultiplication operations result in inner products of vectors and the scaling of vectors by constants: it is this organization that makes the method computationally attractive. However, too many such products (![](../graphics/stm_eqn00736.gif) being bigger than, say, 5&#8211;10) are not attractive, so usually a new kernel matrix is formed and stored after some iterations. In the Abaqus/Standard implementation the kernel is the actual Jacobian matrix ![](../graphics/stm_eqn00737.gif). It is formed whenever a specified number of iterations have been done without obtaining a convergent solution; the default number of iterations is 8. Abaqus/Standard does not reform the kernel unless this value is exceeded, so the same kernel can be used for several increments if the BFGS updates are successful.

In general, the rate of convergence of the quasi-Newton method is slower than the quadratic rate of convergence of Newton's method, though faster than the linear rate of convergence of the modified Newton method.
### Reference

### Reference

"Convergence criteria for nonlinear problems,"  Section 7.2.3 of the Abaqus Analysis User's Guide