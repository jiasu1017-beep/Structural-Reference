# 2.5.1 Eigenvalue extraction

### 2.5.1 Eigenvalue extraction

**Product: **Abaqus/Standard

There are many important areas of structural analysis in which it is essential to be able to extract the eigenvalues of the system and, hence, obtain its natural frequencies of vibration or investigate possible bifurcations that may be associated with kinematic instabilities. For example, structural evaluation for seismic events is often based on linear analysis, using the structure's modes up to a limiting cutoff frequency, which is usually taken as 33 Hz (cycles/second). Once the modes are available, their orthogonality property allows the linear response of the structure to be constructed as the response of a number of single degree of freedom systems. This opens the way to several response evaluation methods that are computationally inexpensive and provide useful insight into the structure's dynamic behavior. Several such methods are provided in Abaqus/Standard and are described in the following sections.

The mathematical eigenvalue problem is a classical field of study, and much work has been devoted to providing eigenvalue extraction methods. [Wilkinson's (1965)](07s01a01-References.md) book provides an excellent compendium on the problem. The eigenvalue problems arising out of finite element models are a particular case: they involve large but usually narrowly banded matrices, and only a small number of eigenpairs are usually required. For many important cases the matrices are symmetric. The eigenvalue problem for natural modes of small vibration of a finite element model is

![](../graphics/stm_eqn01082.gif)or, in classical matrix notation,

![](../graphics/stm_eqn01083.gif)where ![](../graphics/stm_eqn01084.gif) is the mass matrix, which is symmetric and positive definite in the problems of interest here; ![](../graphics/stm_eqn01085.gif) is the damping matrix; ![](../graphics/stm_eqn01086.gif) is the stiffness matrix, which may include large-displacement effects, such as "stress stiffening" (initial stress terms), and, therefore, may not be positive definite or symmetric; ![](../graphics/stm_eqn01087.gif) is the eigenvalue; and ![](../graphics/stm_eqn01088.gif) is the eigenvector---the mode of vibration. This equation is available immediately from a linear perturbation of the equilibrium equation of the system.

The eigensystem ([Equation 2.5.1&#8211;1](02s05a24-Eigenvalue-extraction.md)) in general will have complex eigenvalues and eigenvectors. This system can be symmetrized by assuming that ![](../graphics/stm_eqn01086.gif) is symmetric and by neglecting ![](../graphics/stm_eqn01085.gif) during eigenvalue extraction. The symmetrized system has real squared eigenvalues, ![](../graphics/stm_eqn01089.gif), and real eigenvectors only.

Typically, for symmetric eigenproblems we will also assume that ![](../graphics/stm_eqn01086.gif) is positive semidefinite. In this case ![](../graphics/stm_eqn01087.gif) becomes an imaginary eigenvalue, ![](../graphics/stm_eqn01090.gif), where ![](../graphics/stm_eqn01091.gif) is the circular frequency, and the eigenvalue problem can be written as

![](../graphics/stm_eqn01092.gif)If the model contains hybrid elements, contact pairs, or contact elements, the system of equations contains Lagrange multipliers and the stiffness matrix ![](../graphics/stm_eqn01086.gif) becomes indefinite. However, all the terms of the mass matrix corresponding to the Lagrange multipliers are equal to zero. Therefore, all the eigenvalues are imaginary, and the eigenvalue problem can still be written as [Equation 2.5.1&#8211;2](02s05a24-Eigenvalue-extraction.md).

Abaqus provides eigenvalue extraction procedures for both symmetric and complex eigenproblems. For symmetrized eigenproblems Abaqus/Standard offers two approaches: Lanczos and subspace iteration methods. For complex eigenproblems the subspace projection method is used.
### Eigenvalue extraction for symmetric systems

The structural eigenvalue problem has received considerable attention since the advent of finite element models. [Ramaswami (1979)](07s01a01-References.md) summarizes available methods for the problem: the most attractive appear to be the Lanczos method (see, for example, [Newman and Pipano, 1973](07s01a01-References.md); [Parlett, 1980](07s01a01-References.md)) and the subspace iteration method, a classical method that was introduced into finite element applications by [Bathe and Wilson (1972)](07s01a01-References.md).

Both the subspace iteration and the Lanczos methods, using the Householder and Q-R algorithm for the reduced eigenproblem, have been implemented in Abaqus/Standard. The various parts of these algorithms are discussed in the remainder of this section.Subspace iteration---the basic algorithm

The application of the subspace iteration method to eigenproblems arising from finite element models of the dynamic behavior of structures has been discussed by a number of authors---see [Ramaswami (1979)](07s01a01-References.md) for references. The basic idea is a simultaneous inverse power iteration. A small set of base vectors is created, thus defining a "subspace": this "subspace" is then transformed, by iteration, into the space containing the lowest few eigenvectors of the overall system.

Assume that, at the *i*-th iteration, a set of *m* vectors, ![](../graphics/stm_eqn01093.gif), ![](../graphics/stm_eqn01094.gif), exists, where *m* is less than the number of variables in the finite element model. These are considered as the "base vectors" that define the *m*-dimensional subspace out of the *n* dimensions defined by the variables in the finite element model. We arrange these vectors as the columns in the matrix ![](../graphics/stm_eqn01095.gif). The number of rows of ![](../graphics/stm_eqn01095.gif) is, thus, the size of the complete set of equations (the number of variables in the finite element model, *N*), and the number of columns is the dimension of the subspace, *m*.

The first step in the algorithm is to define a new set of base vectors by solving

![](../graphics/stm_eqn01096.gif)This operation, a generalized "inverse power sweep" with *m* vectors, involves the solution of the complete set of linear stiffness equations for several right-hand-side vectors (with, after the first iteration of the method, a previously decomposed matrix).

The stiffness and mass matrices of the structure are then projected onto the subspace by

![](../graphics/stm_eqn01097.gif)thus defining a mass matrix, ![](../graphics/stm_eqn01098.gif), and a stiffness matrix, ![](../graphics/stm_eqn01099.gif), in the subspace. These matrices are of dimension *m* by *m*. The eigenproblem

![](../graphics/stm_eqn01100.gif)is now solved completely in the subspace using the Householder and Q-R methods, which are discussed below.

The eigenvectors have now been defined in the reduced space and can be transformed back to the full space of the structural problem to define ![](../graphics/stm_eqn01101.gif) for the next iteration:

![](../graphics/stm_eqn01102.gif)where ![](../graphics/stm_eqn01103.gif). This completes an iteration.

With ![](../graphics/stm_eqn01104.gif) (a one-dimensional subspace), the method reduces to the simple "inverse power sweep" method (see [Wilkinson, 1965](07s01a01-References.md), or [Strang, 1976](07s01a01-References.md)).

The advantage of the subspace method is the extraction of the eigenvalues in reduced space, which will cause a rapid convergence to the eigenvectors in full space. The number of base vectors carried in the iterations and the choice of initial base vectors are, therefore, important for an economical solution. The convergence rate of a particular eigenvalue is proportional to ![](../graphics/stm_eqn01105.gif), where ![](../graphics/stm_eqn01106.gif) is the eigenvalue corresponding to the next vector, ![](../graphics/stm_eqn01107.gif) beyond the *m* vectors used to define the subspace. The default value of *m* used in Abaqus is ![](../graphics/stm_eqn01108.gif), where *p* is the number of eigenvectors requested. If more vectors are used, the number of required iterations is reduced, but each iteration takes longer because of the greater number of right-hand sides. Increasing *m* can sometimes improve the performance of the algorithm significantly.

The choice of starting vectors is also important. There is no requirement that these should be close to the eigenvectors for rapid convergence. The Householder and Q-R steps rotate the vectors into the eigenvectors as long as the base vectors span the space of the eigenvectors. The approach used is to choose initial vectors that span this space as completely as possible. The algorithm used in Abaqus/Standard for this purpose is that of [Bathe and Wilson (1972)](07s01a01-References.md). They recommend using the diagonal mass terms as one vector: the other vectors are unit vectors, providing a set of single unit entries at the nodes and the degrees of freedom with the largest mass terms. A check is made to ensure that all degrees of freedom are represented in these additional vectors.

This completes the description of the basic subspace iteration algorithm as it is implemented in Abaqus/Standard. The small eigenproblem, for which all eigenpairs must be found, is solved by the Householder and Q-R algorithms. These algorithms are described at the end of this section.Lanczos eigensolver

The implementation of the Lanczos eigensolver as a powerful tool for extraction of the extreme eigenvalues and the corresponding eigenvectors of a sparse symmetric generalized eigenproblem has been discussed by a number of authors; see, for example, [Parlett (1980)](07s01a01-References.md), [Parlett and Nour-Omid (1989)](07s01a01-References.md), [Simon (1984)](07s01a01-References.md), and [Ericsson and Ruhe (1980)](07s01a01-References.md). A shifted block Lanczos algorithm was developed and described in detail by [Grimes, Lewis, and Simon (1994)](07s01a01-References.md).

The Lanczos procedure in Abaqus/Standard consists of a set of Lanczos "runs," in each of which a set of iterations called steps is performed. For each Lanczos run the following spectral transformation is applied:

![](../graphics/stm_eqn01109.gif)where ![](../graphics/stm_eqn01110.gif) is the shift, ![](../graphics/stm_eqn01111.gif) is the eigenvalue, and ![](../graphics/stm_eqn01088.gif) is the eigenvector. This transformation allows rapid convergence to the desired eigenvalues. The eigenvectors of the symmetrized problem ([Equation 2.5.1&#8211;2](02s05a24-Eigenvalue-extraction.md)) and the transformed problem ([Equation 2.5.1&#8211;5](02s05a24-Eigenvalue-extraction.md)) are identical, while the eigenvalues of the original problem and the transformed problem are related in the following manner:

![](../graphics/stm_eqn01112.gif)

A Lanczos run will be terminated when its continuation is estimated to be inefficient. In general, only tens of eigenvalues (closest to the shift value) are computed in a single Lanczos run. The possibility of computing many eigenmodes by carrying out several runs with different shift values is an important feature of the Lanczos eigensolver.

Within each run a sequence of Krylov subspaces is created, and the best possible approximation of the eigenvectors on each subspace is computed in a series of "steps." In each Lanczos step the dimension of the subspace grows, allowing better approximation of the desired eigenvectors. This is in contrast to the subspace iteration method, in which the dimension of the subspace used to approximate the eigenvectors is fixed.

In theory the basic Lanczos process (in the assumption of "exact" computations without taking into account round-off errors) is able to determine only simple eigenvalues. The shifting strategy (and the Sturm sequence check as a part of it) detects missing modes and enforces computation of all the modes during the subsequent Lanczos runs. However, this strategy is expensive if the multiplicity of certain eigenvalues is high. Therefore, a "blocked" version of the Lanczos algorithm is implemented in Abaqus/Standard. The idea is to start with a block of orthogonal vectors and to increase the dimension of the Krylov subspaces by the block size at each Lanczos step. This approach allows automatic computation of all multiple eigenvalues if the largest multiplicity does not exceed the block size. Another important advantage of the blocked Lanczos method is that it allows efficient implementation of expensive computational kernels such as matrix-blocked vector multiplications, blocked back substitutions, and blocked vector products.

As discussed above, the Lanczos process consists of several Lanczos runs. Each Lanczos run is associated with some shift value that remains constant during the run. The initial shift value, ![](../graphics/stm_eqn01113.gif), is determined (by a heuristic approach) using the geometric mean of the centers of the Gershgorin circles, termed the "problem scale." At the beginning of each Lanczos run a factorization of the shifted matrix ![](../graphics/stm_eqn01114.gif) (where *p* is the run number) is carried out, after which a sequence of Lanczos steps is performed.

Each block Lanczos step *i* is implemented in Abaqus/Standard in the following manner:

Solve the system of linear equations with *b* right-hand sides (*b* is the Lanczos block size) using the factorized shifted matrix:

![](../graphics/stm_eqn01115.gif)where ![](../graphics/stm_eqn01095.gif) is a block of Lanczos vectors. The number of rows of ![](../graphics/stm_eqn01095.gif) is the number of variables in the finite element model, and the number of columns is the Lanczos block size *b*. The initial block of vectors ![](../graphics/stm_eqn01116.gif) is a set of random vectors orthonormalized using the procedure: ![](../graphics/stm_eqn01117.gif) where ![](../graphics/stm_eqn01118.gif) is the identity matrix.

Set the auxiliary block of vectors:

![](../graphics/stm_eqn01119.gif)where ![](../graphics/stm_eqn01120.gif) is a ![](../graphics/stm_eqn01121.gif) upper triangular matrix. ![](../graphics/stm_eqn01122.gif).

Compute the symmetric matrix ![](../graphics/stm_eqn01123.gif) of size *b*:

![](../graphics/stm_eqn01124.gif)

Formulate the Lanczos residual:

![](../graphics/stm_eqn01125.gif)

Normalize the residual. Compute a block of vectors, ![](../graphics/stm_eqn01126.gif), such that

![](../graphics/stm_eqn01127.gif)and

![](../graphics/stm_eqn01128.gif)where ![](../graphics/stm_eqn01129.gif) is a ![](../graphics/stm_eqn01121.gif) upper triangular matrix.

Estimate the loss of orthogonality between ![](../graphics/stm_eqn01126.gif) and ![](../graphics/stm_eqn01130.gif) for ![](../graphics/stm_eqn01131.gif), using the partial reorthogonalization technique; and perform reorthogonalization if necessary (see [Simon, 1984](07s01a01-References.md); [Grimes, Lewis, and Simon, 1994](07s01a01-References.md)).

Perform "local reorthogonalization": recompute ![](../graphics/stm_eqn01126.gif) to provide

![](../graphics/stm_eqn01132.gif)

Solve the following reduced eigenvalue problem for the band matrix ![](../graphics/stm_eqn01133.gif):

![](../graphics/stm_eqn01134.gif)where

![](../graphics/stm_eqn01135.gif)and ![](../graphics/stm_eqn01136.gif) and ![](../graphics/stm_eqn01137.gif) are, respectively, the matrices containing the eigenvectors and eigenvalues of the reduced eigenproblem. This problem is solved by the Householder and Q-R algorithms, which are discussed below.

Determine the error bounds in eigenvalue approximation for the symmetrized eigenvalue problem ([Equation 2.5.1&#8211;2](02s05a24-Eigenvalue-extraction.md)) (see [Parlett, 1980](07s01a01-References.md); [Grimes, Lewis, and Simon, 1994](07s01a01-References.md)). Check the termination conditions of the Lanczos run.The Lanczos run terminates if one of the following conditions is satisfied:

All the eigenvalues required for the current run are extracted.

The triangular matrix ![](../graphics/stm_eqn01129.gif) is singular or ill-conditioned.

The number of Lanczos steps exceeds the maximum number allowed.

Continuation of the current run is evaluated to be inefficient. This decision is based on the estimation of the "cost per eigenvalue" over the next few steps (the Lanczos run is continued as long as the cost per eigenvalue is decreasing).

After termination of each Lanczos run, the converged eigenvectors of the symmetrized problem ([Equation 2.5.1&#8211;2](02s05a24-Eigenvalue-extraction.md)) are recovered using the blocks of vectors ![](../graphics/stm_eqn01138.gif) and the eigenvectors ![](../graphics/stm_eqn01136.gif).

Once the Lanczos run for the shift ![](../graphics/stm_eqn01139.gif) is completed, the shift value ![](../graphics/stm_eqn01140.gif) is computed using the results of all the previous Lanczos runs. To describe the shifting strategy, the following concepts are introduced:

The "computational interval" is the interval between the minimum and maximum eigenvalues of interest. This interval can be finite (both ends are finite), semi-infinite (only one end is finite), or infinite (both ends are infinite). The "center point" is the point in the computational interval nearest to the desired eigenvalues.

The Sturm sequence number, ![](../graphics/stm_eqn01141.gif), of a real nonsingular symmetric matrix ![](../graphics/stm_eqn00147.gif) is the number of negative eigenvalues. This number is equal to the number of negative terms in the diagonal matrix ![](../graphics/stm_eqn01142.gif) of the Cholesky decomposition ![](../graphics/stm_eqn01143.gif) and is, therefore, available after the Cholesky decomposition is completed.

Let ![](../graphics/stm_eqn01113.gif) and ![](../graphics/stm_eqn01144.gif) be two shift values such that ![](../graphics/stm_eqn01145.gif) Then the number of eigenvalues of the symmetrized problem ([Equation 2.5.1&#8211;2](02s05a24-Eigenvalue-extraction.md), assuming that ![](../graphics/stm_eqn01084.gif) is positive definite or positive semidefinite) in the interval ![](../graphics/stm_eqn01146.gif) is equal to ![](../graphics/stm_eqn01147.gif) If this number is equal to the number of eigenvalues actually determined by the Lanczos algorithm, the interval ![](../graphics/stm_eqn01146.gif) is called "a trust interval." The trust interval containing the center point is referred to as "a primary trust interval" (denoted by the key "+" in the trust intervals list printed in the message file). The shifting strategy is aimed at constructing the primary trust interval inside the computational interval containing the required number of eigenvalues closest to the center point.

One of the most important features in the formulation of the shift update strategy is the concept of a "sentinel." The sentinels are the endpoints of the intervals containing exclusively converged eigenvalues closest to the current shift value (in each direction). The sentinels are computed during each Lanczos run and are updated at the end of each step after the eigenvalue analysis of the reduced matrix ![](../graphics/stm_eqn01133.gif) is completed. The basic assumption is that there are no missing eigenvalues inside the sentinels; therefore, they are excluded from the computation intervals for the upcoming Lanczos runs. This assumption is later verified on the basis of the Sturm sequence check, and a special procedure is activated if some eigenvalues are missing. If no missing eigenvalues are detected, the sentinels transform directly into the corresponding trust intervals.

The new shift values are selected on the basis of the nonconverged eigenvalue approximations after the Lanczos run is terminated. Assuming the same convergence properties for the upcoming runs, the new shift values are selected in such a way that the number of eigenvalues expected to be found in the upcoming runs will be close to the number of eigenvalues found inside the corresponding sentinels on the previous run.The Householder method with quarter rotation

The Householder method is used to reduce a general matrix to a symmetric tridiagonal form. A tridiagonal matrix is one whose only nonzero entries are on or immediately adjacent to the diagonal. The first step is to transform [Equation 2.5.1&#8211;4](02s05a24-Eigenvalue-extraction.md) to the form

![](../graphics/stm_eqn01148.gif)where ![](../graphics/stm_eqn01118.gif) is the identity matrix.

This is done by using a Cholesky decomposition of ![](../graphics/stm_eqn01098.gif) and then premultiplying and postmultiplying ![](../graphics/stm_eqn01099.gif) by the inverse of the lower and upper triangular matrices that are, thus, obtained:

![](../graphics/stm_eqn01149.gif)where

![](../graphics/stm_eqn01150.gif)

To preserve symmetry in ![](../graphics/stm_eqn00147.gif), it is necessary that the decomposition of ![](../graphics/stm_eqn01098.gif) result in two matrices that are the transpose of each other. A Cholesky decomposition produces the desired result but adds the requirement that the matrix ![](../graphics/stm_eqn01098.gif) be positive definite. ![](../graphics/stm_eqn01098.gif) should always be positive definite (because ![](../graphics/stm_eqn01084.gif) is positive definite in all of the problems considered here) if the base vectors defining the subspace are not linearly dependent across ![](../graphics/stm_eqn01084.gif). In practice the choices made for starting values of the base vectors usually satisfy this requirement, although cases can arise when this is not true. Then Abaqus/Standard will reduce the dimensionality of the subspace to obtain a positive definite ![](../graphics/stm_eqn01098.gif).

The Householder transformation starts with the matrix ![](../graphics/stm_eqn00147.gif) and, proceeding one column at a time, reduces all the entries outside the tridiagonal part of the matrix to zero by the transformation

![](../graphics/stm_eqn01151.gif)The matrix ![](../graphics/stm_eqn01152.gif) is of the form

![](../graphics/stm_eqn01153.gif)

For the first transformation ![](../graphics/stm_eqn01154.gif) is of the same order as ![](../graphics/stm_eqn00147.gif) and ![](../graphics/stm_eqn01152.gif); that is, ![](../graphics/stm_eqn01155.gif), the dimension of the subspace. However, each transformation reduces the order of ![](../graphics/stm_eqn01154.gif) by one, the leading parts of ![](../graphics/stm_eqn01152.gif) being 1 on the diagonal and 0 outside the diagonal, as illustrated above.

The matrix ![](../graphics/stm_eqn01154.gif) is obtained by the following algorithm:

If this is the *k*th iteration, write the *k*th column of ![](../graphics/stm_eqn01156.gif) below the diagonal as

![](../graphics/stm_eqn01157.gif)

Calculate the norm ![](../graphics/stm_eqn01158.gif)

Define a vector,

![](../graphics/stm_eqn01159.gif)

Then,

![](../graphics/stm_eqn01160.gif)This algorithm is developed in detail in [Strang's (1976)](07s01a01-References.md) book.

The Householder algorithm produces a symmetric tridiagonal matrix, which has the same eigenvalues as the original matrix, because the transformation ([Equation 2.5.1&#8211;6](02s05a24-Eigenvalue-extraction.md)) does not alter the eigenvalues.

The next step is to calculate the eigenvalues of the tridiagonal matrix. This is done by the Q-R algorithm. In this method the matrix ![](../graphics/stm_eqn00147.gif), which is now tridiagonal (although this is not a requirement for the method to work), is factored into ![](../graphics/stm_eqn01161.gif), where ![](../graphics/stm_eqn01162.gif) is an orthonormal matrix (that is, ![](../graphics/stm_eqn01163.gif)) and ![](../graphics/stm_eqn01164.gif) is an upper-triangular matrix (that is, all the terms in ![](../graphics/stm_eqn01164.gif) below the diagonal are zero).

The next matrix in the iteration is obtained by premultiplying and postmultiplying ![](../graphics/stm_eqn00147.gif) by ![](../graphics/stm_eqn01162.gif):

![](../graphics/stm_eqn01165.gif)Because ![](../graphics/stm_eqn01162.gif) is orthonormal, this will not affect the eigenvalues. This process gradually reduces the off-diagonal terms of ![](../graphics/stm_eqn00147.gif) so that the diagonal terms approach the eigenvalues. To speed up convergence, a method of shifting is introduced, leading to the following iterative loop:

![](../graphics/stm_eqn01166.gif)

![](../graphics/stm_eqn01167.gif)

![](../graphics/stm_eqn01168.gif)

![](../graphics/stm_eqn01169.gif)

The shift cannot be used until the iteration is converging toward an eigenvalue; but once that is obvious, the shift value ![](../graphics/stm_eqn01123.gif) can be set to the expected eigenvalue. This will lead to a significant improvement in the convergence rate. If the shift is done too early, with a value that is not close to an eigenvalue, it is quite possible that the process will converge to an incorrect number. The Q-R process will converge to the eigenvalues in ascending order; and as soon as an eigenvalue is obtained, the order of the matrix can be reduced by one.

The final step after the eigenvalues have been obtained is to calculate the eigenvectors by using the inverse power method to solve for an eigenvector, given any right-hand side:

![](../graphics/stm_eqn01170.gif)where ![](../graphics/stm_eqn00280.gif) is the eigenvalue just obtained and ![](../graphics/stm_eqn01171.gif) is any vector. Because the left-hand-side matrix is singular in the direction of the eigenvector ![](../graphics/stm_eqn01088.gif), this vector will be obtained regardless of the right-hand-side vector ![](../graphics/stm_eqn01171.gif), as long as ![](../graphics/stm_eqn01171.gif) is not orthogonal to the eigenvector. To ensure that consecutive vectors are orthogonal, especially in the case of multiple eigenvalues, ![](../graphics/stm_eqn01171.gif) is always chosen to be orthogonal to the previously extracted eigenvectors. Since ![](../graphics/stm_eqn01172.gif) is singular, a slight numerical shift must be included to decompose it and, thus, solve for ![](../graphics/stm_eqn01088.gif). In the standard notation used in this guide, the matrix of eigenvectors ![](../graphics/stm_eqn01173.gif) is written as ![](../graphics/stm_eqn01174.gif), where N refers to the nodal variable in the problem and ![](../graphics/stm_eqn01175.gif) is the mode number.
### Complex eigenvalue extraction

Abaqus/Standard offers the subspace projection method to solve for complex eigenvalues and right eigenvectors of the original eigenproblem ([Equation 2.5.1&#8211;1](02s05a24-Eigenvalue-extraction.md)).Subspace projection method

In the subspace projection method the original eigensystem ([Equation 2.5.1&#8211;1](02s05a24-Eigenvalue-extraction.md)) is projected onto a subspace spanned by the eigenvectors of the undamped, symmetric system ([Equation 2.5.1&#8211;2](02s05a24-Eigenvalue-extraction.md)). Thus, the symmetrized eigenproblem must be solved prior to the complex eigenvalue extraction procedure to create the subspace onto which the original system will be projected. Next, the original mass, damping, and stiffness matrices are projected onto the subspace of *N* eigenvectors:

![](../graphics/stm_eqn01176.gif)

![](../graphics/stm_eqn01177.gif)

![](../graphics/stm_eqn01178.gif)Then, we arrive at the following eigenproblem:

![](../graphics/stm_eqn01179.gif)Typically, the number of eigenvectors is relatively small; a few hundred is common. This small  complex eigenvalue system is solved using the standard QZ method for generalized nonsymmetric eigenproblems. Complex eigenvalues of the projected system are the approximation of the eigenvalues of the original system ([Equation 2.5.1&#8211;1](02s05a24-Eigenvalue-extraction.md)), but the right eigenvectors of the original system need to be recovered:

![](../graphics/stm_eqn01180.gif)where ![](../graphics/stm_eqn01181.gif) is the approximation of *k*-th right eigenvector of the original system.

The only energy density calculated in the eigenvalue extraction procedures is the elastic strain energy density, which for the complex eigenvalue extraction is defined as follows:

![](../graphics/stm_eqn01182.gif)where ![](../graphics/stm_eqn01183.gif) are real and imaginary components of the eigenstress tensor and ![](../graphics/stm_eqn01184.gif) are real and imaginary components of the eigenstrain tensor.
### References

### References

"Eigenvalue buckling prediction,"  Section 6.2.3 of the Abaqus Analysis User's Guide

"Natural frequency extraction,"  Section 6.3.5 of the Abaqus Analysis User's Guide

"Complex eigenvalue extraction,"  Section 6.3.6 of the Abaqus Analysis User's Guide