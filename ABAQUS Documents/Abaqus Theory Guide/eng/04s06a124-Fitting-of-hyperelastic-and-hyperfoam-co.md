# 4.6.2 Fitting of hyperelastic and hyperfoam constants

### 4.6.2 Fitting of hyperelastic and hyperfoam constants

**Products: **Abaqus/Standard  Abaqus/Explicit

In this section we will derive the equations needed for fitting the hyperelastic (polynomial, Ogden, Arruda-Boyce, and Van der Waals form) and hyperfoam constants to experimental test data. In addition, the procedures for checking the material stability using the Drucker criterion will be described.

For the hyperelastic models full incompressibility is assumed in fitting the hyperelastic constants to the test data, except in the volumetric test.
### Stress-strain relations for the polynomial strain energy potential

The hyperelastic polynomial form can be fitted by Abaqus up to order ![](../graphics/stm_eqn05962.gif). Since the Mooney-Rivlin potential corresponds to the case ![](../graphics/stm_eqn05955.gif), these remarks also apply by setting the higher-order coefficients to zero. The energy potential is as follows:

![](../graphics/stm_eqn06839.gif)

The deformation modes are characterized in terms of the principal stretches. The nominal stress-strain relations are now derived for the polynomial form with ![](../graphics/stm_eqn05962.gif).Uniaxial mode

![](../graphics/stm_eqn06840.gif)

The deviatoric strain invariants are

![](../graphics/stm_eqn06841.gif)We invoke the principle of virtual work to derive the nominal stress-strain relationship,

![](../graphics/stm_eqn06842.gif)and it follows that

![](../graphics/stm_eqn06843.gif)Equibiaxial mode

![](../graphics/stm_eqn06844.gif)

The deviatoric strain invariants are

![](../graphics/stm_eqn06845.gif)From virtual work

![](../graphics/stm_eqn06846.gif)and it follows that,

![](../graphics/stm_eqn06847.gif)Planar (pure shear) mode

![](../graphics/stm_eqn06848.gif)

The deviatoric strain invariants are

![](../graphics/stm_eqn06849.gif)From virtual work

![](../graphics/stm_eqn06850.gif)and it follows that,

![](../graphics/stm_eqn06851.gif)Volumetric mode

![](../graphics/stm_eqn06852.gif)

From virtual work

![](../graphics/stm_eqn06853.gif)and it follows that,

![](../graphics/stm_eqn06854.gif)

![](../graphics/stm_eqn06855.gif)
### Stress-strain relations for the reduced polynomial strain energy potential

The hyperelastic reduced polynomial form can be fitted by Abaqus up to order ![](../graphics/stm_eqn06856.gif). For ![](../graphics/stm_eqn06792.gif) the reduced polynomial is identical to the Yeoh model, and for ![](../graphics/stm_eqn05955.gif) the neo-Hookean model is retained; hence, the following also applies to these forms. The reduced polynomial energy potential is as follows:

![](../graphics/stm_eqn06786.gif)Following the arguments in the previous section, we derive the nominal stress-strain relations for the reduced polynomial.Uniaxial mode

![](../graphics/stm_eqn06857.gif)

![](../graphics/stm_eqn06858.gif)Equibiaxial mode

![](../graphics/stm_eqn06844.gif)

![](../graphics/stm_eqn06859.gif)Planar (pure shear) mode

![](../graphics/stm_eqn06848.gif)

![](../graphics/stm_eqn06860.gif)Volumetric mode

![](../graphics/stm_eqn06852.gif)

![](../graphics/stm_eqn06855.gif)
### Stress-strain relations for the hyperelastic Ogden strain energy potential

The hyperelastic Ogden form can be fitted up to order ![](../graphics/stm_eqn06856.gif):

![](../graphics/stm_eqn06861.gif)Following the same approach as for the polynomial form, we can derive the nominal stress-strain equations for the Ogden form.Uniaxial mode

![](../graphics/stm_eqn06862.gif)

![](../graphics/stm_eqn06863.gif)Equibiaxial mode

![](../graphics/stm_eqn06864.gif)

![](../graphics/stm_eqn06865.gif)Planar (pure shear) mode

![](../graphics/stm_eqn06848.gif)

![](../graphics/stm_eqn06866.gif)Volumetric mode

![](../graphics/stm_eqn06852.gif)

![](../graphics/stm_eqn06855.gif)
### Stress-strain relations for the hyperelastic Arruda-Boyce strain energy potential

The hyperelastic Arruda-Boyce potential has the following form:

![](../graphics/stm_eqn06867.gif)where

![](../graphics/stm_eqn06868.gif)Following the same approach as for the polynomial form, we can derive the nominal stress-strain equations for the Arruda-Boyce potential.Uniaxial mode

![](../graphics/stm_eqn06857.gif)

![](../graphics/stm_eqn06869.gif)Equibiaxial mode

![](../graphics/stm_eqn06844.gif)

![](../graphics/stm_eqn06870.gif)Planar (pure shear) mode

![](../graphics/stm_eqn06848.gif)

![](../graphics/stm_eqn06871.gif)Volumetric mode

![](../graphics/stm_eqn06852.gif)

![](../graphics/stm_eqn06872.gif)
### Stress-strain relations for the hyperelastic Van der Waals energy potential

The hyperelastic Van der Waals potential, also known as the Kilian model, has the following form:

![](../graphics/stm_eqn06873.gif)where

![](../graphics/stm_eqn06820.gif)

Following the same approach as for the polynomial form, we can derive the nominal stress-strain relations for the Van der Waals form.Uniaxial mode

![](../graphics/stm_eqn06857.gif)

![](../graphics/stm_eqn06874.gif)Equibiaxial mode

![](../graphics/stm_eqn06844.gif)

![](../graphics/stm_eqn06875.gif)Planar (pure shear) mode

![](../graphics/stm_eqn06848.gif)

![](../graphics/stm_eqn06876.gif)Volumetric mode

![](../graphics/stm_eqn06852.gif)

![](../graphics/stm_eqn06877.gif)
### Stress-strain relations for the hyperfoam strain energy potential

The hyperfoam potential is a modified form of the Hill strain energy potential and can be fitted up to order ![](../graphics/stm_eqn06856.gif):

![](../graphics/stm_eqn06878.gif)

The deformation modes are characterized in terms of the principal stretches and the volume ratio *J*. The elastomeric foams are not incompressible: ![](../graphics/stm_eqn06879.gif). The transverse stretches ![](../graphics/stm_eqn06880.gif) and/or ![](../graphics/stm_eqn06881.gif) are independently specified in the test data either as individual values depending on the lateral deformations or through the definition of an effective Poisson's ratio.Uniaxial mode

![](../graphics/stm_eqn06882.gif)Equibiaxial mode

![](../graphics/stm_eqn06883.gif)Planar mode

![](../graphics/stm_eqn06884.gif)

The common nominal stress-strain relation for the three deformation modes above is

![](../graphics/stm_eqn06885.gif)where ![](../graphics/stm_eqn06886.gif) is the nominal stress and ![](../graphics/stm_eqn06887.gif) is the stretch in the direction of loading.Simple shear mode

The simple shear deformation is described in terms of the deformation gradient,

![](../graphics/stm_eqn06888.gif)where ![](../graphics/stm_eqn01256.gif) is the shear strain. Note also that for this deformation, ![](../graphics/stm_eqn06889.gif). The nominal shear stress ![](../graphics/stm_eqn06890.gif) is

![](../graphics/stm_eqn06891.gif)where ![](../graphics/stm_eqn06887.gif) are the principal stretches in the plane of shearing, related to the shear strain ![](../graphics/stm_eqn01256.gif) as follows:

![](../graphics/stm_eqn06892.gif)The stretch in the direction perpendicular to the plane of shearing is ![](../graphics/stm_eqn06893.gif).

The transverse stress ![](../graphics/stm_eqn06894.gif) developed during simple shear deformation (as a result of the Poynting effect) is

![](../graphics/stm_eqn06895.gif)Volumetric mode

The volumetric deformation is described as

![](../graphics/stm_eqn06896.gif)The pressure *p* is related to volume ratio *J* through

![](../graphics/stm_eqn06897.gif)
### Least squares fit

Given experimental data, the material constants are determined through a least-squares-fit procedure, which minimizes the relative error in stress. For the *n* nominal stress&#8211;nominal strain data pairs, the relative error measure *E* is minimized,

![](../graphics/stm_eqn06898.gif)where ![](../graphics/stm_eqn06899.gif) is a stress value from the test data and ![](../graphics/stm_eqn06900.gif) comes from one of the nominal stress expressions derived above.

The polynomial potential is linear in terms of the constants ![](../graphics/stm_eqn06773.gif); therefore, a linear least-squares procedure can be used. The Ogden, the Arruda-Boyce, and the Van der Waals potential are nonlinear in some of their coefficients, thus necessitating the use of a nonlinear least-squares procedure.
### Linear least squares fit for the polynomial model

For the full polynomial model we can rewrite the expressions for the ![](../graphics/stm_eqn06901.gif) derived above as

![](../graphics/stm_eqn06902.gif)where the ![](../graphics/stm_eqn06903.gif) are functions that depend on the stress state (uniaxial, biaxial, or planar), as explained above. ![](../graphics/stm_eqn05955.gif) for the first-order polynomial (or Mooney-Rivlin form), and ![](../graphics/stm_eqn05962.gif) for the second-order polynomial. To minimize the relative error, we need to set

![](../graphics/stm_eqn06904.gif)which leads to the following set of ![](../graphics/stm_eqn06905.gif) equations:

![](../graphics/stm_eqn06906.gif)This linear set of *M* equations can be solved readily to define the coefficients ![](../graphics/stm_eqn06773.gif).

To fit the volumetric coefficients, one needs to solve the system of *N* equations

![](../graphics/stm_eqn06907.gif)where

![](../graphics/stm_eqn06908.gif)and

![](../graphics/stm_eqn06909.gif)is given by the user. This system of equations can be solved readily for ![](../graphics/stm_eqn06774.gif).
### Linear least squares fit for the reduced polynomial model

For the reduced polynomial model we can rewrite the expressions for ![](../graphics/stm_eqn06901.gif) derived above as follows:

![](../graphics/stm_eqn06910.gif)where again the functions ![](../graphics/stm_eqn06911.gif) depend on the stress state and the stretch, as outlined above, and *N* is the order of the reduced polynomial, which can take values up to ![](../graphics/stm_eqn06856.gif). The following also applies to the Yeoh and neo-Hookean forms since these models are special cases of the reduced polynomial, with ![](../graphics/stm_eqn06792.gif) and ![](../graphics/stm_eqn05955.gif), respectively.

Following the same arguments as for the full polynomial, we arrive at the system of *N* equations

![](../graphics/stm_eqn06912.gif)This system of equations can be solved readily for the coefficients ![](../graphics/stm_eqn06913.gif). The volumetric coefficients are fitted with the same procedure as used for the general polynomial models.
### Nonlinear least squares fit

The Ogden, Arruda-Boyce, and Van der Waals potentials are nonlinear in some of their coefficients; hence, a nonlinear least-squares-fit procedure is required. We use the Marquard-Levenberg algorithm in the formulation by [Twizell and Ogden (1986)](07s01a01-References.md). Let ![](../graphics/stm_eqn06914.gif), ![](../graphics/stm_eqn06915.gif) be the coefficients of these hyperelastic models, where *m* is the number of coefficients contributing to the deviatoric behavior. Specifically, ![](../graphics/stm_eqn06916.gif) for the Ogden model, ![](../graphics/stm_eqn06917.gif) for the Arruda-Boyce model, and ![](../graphics/stm_eqn06918.gif) for the Van der Waals model. The coefficients are found by iterating the equation

![](../graphics/stm_eqn06919.gif)where *r* is the iteration count, *n* is the number of data points,

![](../graphics/stm_eqn06920.gif)is the vector of relative errors, and

![](../graphics/stm_eqn06921.gif)is the derivative of the vector of relative errors with respect to the coefficients ![](../graphics/stm_eqn06914.gif).

For ![](../graphics/stm_eqn02157.gif), the Newton algorithm is obtained; for very large values of ![](../graphics/stm_eqn01256.gif), the steepest descent method is obtained. Thus, the Marquard-Levenberg algorithm represents a compromise between these two approaches: the value of ![](../graphics/stm_eqn06922.gif) is increased if the error grows and is reduced otherwise.
### Nonlinear least squares fit for the Ogden model

After initializing the ![](../graphics/stm_eqn06923.gif), the parameters ![](../graphics/stm_eqn06924.gif) are found with a linear least squares fit. In the iterative procedure outlined above, the following derivatives are used:

![](../graphics/stm_eqn06925.gif)where

![](../graphics/stm_eqn06926.gif)
### Nonlinear least squares fit for the Arruda-Boyce model

The Arruda-Boyce model is linear in the shear modulus ![](../graphics/stm_eqn01087.gif) but nonlinear in the locking stretch ![](../graphics/stm_eqn06791.gif). The locking stretch is initialized as ![](../graphics/stm_eqn06927.gif), where ![](../graphics/stm_eqn06928.gif) is the maximum stretch in the user-specified test data. Given this locking stretch, the initial shear modulus, ![](../graphics/stm_eqn06929.gif), is obtained with a linear least squares fit.

In the iterative procedure outlined above, the following derivatives are used:

![](../graphics/stm_eqn06930.gif)

![](../graphics/stm_eqn06931.gif)
### Nonlinear least squares fit for the Van der Waals model

The Van der Waals model is linear in the shear modulus ![](../graphics/stm_eqn01087.gif) but nonlinear in the locking stretch ![](../graphics/stm_eqn06791.gif), the global interaction parameter *a*, and the mixture parameter ![](../graphics/stm_eqn01219.gif). The locking stretch is initialized as ![](../graphics/stm_eqn06932.gif), where ![](../graphics/stm_eqn06928.gif) is the maximum stretch in the user-specified test data. Given this guess for the locking stretch, we make use of an expression proposed by [Kilian et al. (1986)](07s01a01-References.md) to initialize the global interaction parameter

![](../graphics/stm_eqn06933.gif)The invariant mixture parameter is initialized to ![](../graphics/stm_eqn06934.gif). Given these initial values, the shear modulus, ![](../graphics/stm_eqn06929.gif), is initialized using a linear least-squares-fit procedure.

In the iterative procedure outlined above, the following derivatives are used:

![](../graphics/stm_eqn06935.gif)

![](../graphics/stm_eqn06936.gif)

![](../graphics/stm_eqn06937.gif)

![](../graphics/stm_eqn06938.gif)

In the derivatives of ![](../graphics/stm_eqn06939.gif)

![](../graphics/stm_eqn06940.gif)and

![](../graphics/stm_eqn06941.gif)

In the planar case ![](../graphics/stm_eqn06942.gif); hence, ![](../graphics/stm_eqn06939.gif) vanishes.
### Drucker stability check

Abaqus checks the Drucker stability of the material for the first three modes of deformation described above. The Drucker stability condition requires that the change in the Kirchhoff stress ![](../graphics/stm_eqn06943.gif) following from an infinitesimal change in the logarithmic strain ![](../graphics/stm_eqn06115.gif) satisfies the inequality

![](../graphics/stm_eqn06944.gif)

Using ![](../graphics/stm_eqn06945.gif), the inequality becomes

![](../graphics/stm_eqn06946.gif)thus requiring the tangential material stiffness ![](../graphics/stm_eqn00424.gif) to be positive definite for material stability to be satisfied.

For the isotropic elastic formulation considered here, the inequality can be represented in terms of the principal stresses and strains:

![](../graphics/stm_eqn06947.gif)Polynomial form

With the incompressibility assumption for the two hyperelastic models, the Kirchhoff stress is equal to the Cauchy stress: ![](../graphics/stm_eqn06948.gif) and, thus,

![](../graphics/stm_eqn06949.gif)In addition, we can choose any value for the hydrostatic pressure without affecting the strains. For the stability calculation a convenient choice is ![](../graphics/stm_eqn06950.gif), which gives us

![](../graphics/stm_eqn06951.gif)The infinitesimal strain changes are related to the changes in stretch ratios by the equations

![](../graphics/stm_eqn06952.gif)The stresses follow from the strain energy, which in turn follow from the changes in the strain invariants or in the stretches.

The relation between changes in the stress and changes in strain are described by the matrix equation

![](../graphics/stm_eqn06953.gif)where

![](../graphics/stm_eqn06954.gif)

![](../graphics/stm_eqn06955.gif)

![](../graphics/stm_eqn06956.gif)

For material stability ![](../graphics/stm_eqn00424.gif) must be positive definite; thus, it is necessary that

![](../graphics/stm_eqn06957.gif)

![](../graphics/stm_eqn06958.gif)for all relevant values of ![](../graphics/stm_eqn06959.gif), ![](../graphics/stm_eqn06880.gif), and ![](../graphics/stm_eqn06881.gif).Ogden form

For the Ogden form we follow the same approach as the polynomial form. Using ![](../graphics/stm_eqn06960.gif), we have

![](../graphics/stm_eqn06961.gif)

![](../graphics/stm_eqn06962.gif)

![](../graphics/stm_eqn06963.gif)and the material stiffness ![](../graphics/stm_eqn00424.gif) that we check for positive definiteness is

![](../graphics/stm_eqn06964.gif)Arruda-Boyce form

For positive values of the shear modulus, ![](../graphics/stm_eqn01087.gif), and the locking stretch, ![](../graphics/stm_eqn06791.gif), the Arruda-Boyce form is always stable. Hence, it suffices to check the coefficients to determine whether the material satisfies Drucker stability.Van der Waals form

When the Van der Waals model is employed in its admissible stretch range given by ![](../graphics/stm_eqn06965.gif), its stability depends on the global interaction parameter, *a*, for positive values of the initial shear modulus, ![](../graphics/stm_eqn01087.gif), and the locking stretch, ![](../graphics/stm_eqn06791.gif). To verify the Drucker stability of the Van der Waals model, we can employ the equations derived for the polynomial models by making use of the fact that

![](../graphics/stm_eqn06966.gif)To determine the admissible stretch range, we need to find the two positive real-valued roots neighboring ![](../graphics/stm_eqn00381.gif) of the equation

![](../graphics/stm_eqn06967.gif)for each of the three stress states---uniaxial, biaxial, and planar---by using a simple bisection method.Hyperfoam

The Kirchhoff stress-strain relation for the uniaxial, biaxial, planar, and volumetric deformation modes is

![](../graphics/stm_eqn06968.gif)Taking the total differential of ![](../graphics/stm_eqn06969.gif) and using ![](../graphics/stm_eqn06970.gif),

![](../graphics/stm_eqn06971.gif)Since we cannot use the incompressibility assumption, we have to use all three principal stress and strain components and a ![](../graphics/stm_eqn00335.gif) ![](../graphics/stm_eqn00424.gif) matrix,

![](../graphics/stm_eqn06972.gif)Specifically,

![](../graphics/stm_eqn06973.gif)where ![](../graphics/stm_eqn06974.gif),

For the simple shear case the principal stretches ![](../graphics/stm_eqn06959.gif) and ![](../graphics/stm_eqn06880.gif) are computed from the shear strain ![](../graphics/stm_eqn01256.gif) (as given in an earlier expression). Thus, the same form of equations is used in checking material stability during simple shear deformation.

For material stability (i.e., for ![](../graphics/stm_eqn00424.gif) to be positive definite) the following conditions must be satisfied:

![](../graphics/stm_eqn06975.gif)

![](../graphics/stm_eqn06976.gif)

![](../graphics/stm_eqn06977.gif)
### References

### References

"Hyperelastic behavior of rubberlike materials,"  Section 22.5.1 of the Abaqus Analysis User's Guide

"Hyperelastic behavior in elastomeric foams,"  Section 22.5.2 of the Abaqus Analysis User's Guide