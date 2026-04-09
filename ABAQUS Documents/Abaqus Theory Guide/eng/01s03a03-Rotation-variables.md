# 1.3.1 Rotation variables

### 1.3.1 Rotation variables

**Products: **Abaqus/Standard  Abaqus/Explicit

Since Abaqus contains such capabilities as structural elements (beams and shells) for which it is necessary to define arbitrarily large magnitudes of rotation, a convenient method for storing the rotation at a node is required. The components of a rotation vector ![](../graphics/stm_eqn00152.gif) are stored as the degrees of freedom 4, 5, and 6 at any node where a rotation is required.

The finite rotation vector, ![](../graphics/stm_eqn00152.gif), consists of a rotation magnitude, ![](../graphics/stm_eqn00153.gif), and a rotation axis or direction in space, ![](../graphics/stm_eqn00154.gif). Physically, the rotation ![](../graphics/stm_eqn00152.gif) is interpreted as a rotation by ![](../graphics/stm_eqn00155.gif) radians around the axis ![](../graphics/stm_eqn00156.gif). To characterize this finite rotation mathematically, the rotation vector ![](../graphics/stm_eqn00152.gif) is used to define an orthogonal transformation or rotation matrix. To do so, first define the skew-symmetric matrix ![](../graphics/stm_eqn00157.gif) associated with ![](../graphics/stm_eqn00152.gif) by the relationships

![](../graphics/stm_eqn00158.gif)![](../graphics/stm_eqn00152.gif) is called the axial vector of the skew-symmetric matrix ![](../graphics/stm_eqn00157.gif). In matrix components relative to the standard Euclidean basis, if ![](../graphics/stm_eqn00159.gif), then

![](../graphics/stm_eqn00160.gif)In what follows, ![](../graphics/stm_eqn00161.gif) will be used to denote the skew-symmetric matrix with axial vector ![](../graphics/stm_eqn00001.gif).

A well-known result from linear algebra is that the exponential of a skew-symmetric matrix ![](../graphics/stm_eqn00157.gif) is an orthogonal (rotation) matrix that produces the finite rotation ![](../graphics/stm_eqn00152.gif). Let the rotation matrix be ![](../graphics/stm_eqn00162.gif), such that ![](../graphics/stm_eqn00163.gif). Then by definition,

![](../graphics/stm_eqn00164.gif)However, the above infinite series has the following closed-form expression:

![](../graphics/stm_eqn00165.gif)

In components,

![](../graphics/stm_eqn00166.gif)where ![](../graphics/stm_eqn00167.gif) and ![](../graphics/stm_eqn00168.gif) is the alternator tensor, defined by

![](../graphics/stm_eqn00169.gif)It is this closed-form expression that allows the exact and numerically efficient geometric representation of finite rotations.
### Quaternion parametrization

Even though Abaqus stores and outputs the rotation vector, quaternion parameters prove to be an efficient and convenient way to treat finite rotations computationally. Let ![](../graphics/stm_eqn00170.gif) be a scalar, and let ![](../graphics/stm_eqn00171.gif) be a vector field. The quaternion ![](../graphics/stm_eqn00172.gif) is simply the pairing

![](../graphics/stm_eqn00173.gif)To associate ![](../graphics/stm_eqn00172.gif) with the finite rotation vector ![](../graphics/stm_eqn00152.gif), define the following:

![](../graphics/stm_eqn00174.gif)

By trigonometric identities it follows that the orthogonal matrix ![](../graphics/stm_eqn00175.gif) in [Equation 1.3.1&#8211;1](01s03a03-Rotation-variables.md) is given in terms of ![](../graphics/stm_eqn00172.gif) as

![](../graphics/stm_eqn00176.gif)By the convention introduced above, ![](../graphics/stm_eqn00177.gif) is the skew-symmetric matrix with axial vector ![](../graphics/stm_eqn00178.gif).

For a more detailed discussion of quaternion algebra and its relation to other representations of finite rotations, see the discussion by [Spring (1986)](07s01a01-References.md).
### Compound rotations

A compound rotation is the successive application of two or more rotation fields. In geometrically linear problems compound rotations are obtained simply as the linear superposition of the individual (linearized) rotation vectors. This fact follows directly from the series expansion for ![](../graphics/stm_eqn00179.gif). Let ![](../graphics/stm_eqn00180.gif) and ![](../graphics/stm_eqn00181.gif) be infinitesimal rotations. Thus, ![](../graphics/stm_eqn00182.gif), ![](../graphics/stm_eqn00183.gif), and

![](../graphics/stm_eqn00184.gif)In geometrically nonlinear analysis compound rotations are no longer additive. Furthermore, they are not commutative; that is, the order of application is important. A significant exception occurs when the multiple rotations share the same rotation axis. This special case is investigated further below. A detailed example of a finite compound rotation is given in "Conventions,"  Section 1.2.2 of the Abaqus Analysis User's Guide.

Let ![](../graphics/stm_eqn00185.gif) be the orthogonal transformation representing the compound rotation defined as the product of a set of individual or incremental rotations ![](../graphics/stm_eqn00186.gif), for ![](../graphics/stm_eqn00187.gif). (For the case of specified boundary conditions ![](../graphics/stm_eqn00185.gif) is the final product after *i* steps of all the specified rotations ![](../graphics/stm_eqn00186.gif); for the iterative numerical solution procedure ![](../graphics/stm_eqn00185.gif) is the total rotation after *i* increments, where ![](../graphics/stm_eqn00186.gif), for ![](../graphics/stm_eqn00188.gif), is the converged rotation field solution at each increment.) By definition, the compound rotation is the product

![](../graphics/stm_eqn00189.gif)or equivalently by the recursion relation,

![](../graphics/stm_eqn00190.gif)It is important to note that ![](../graphics/stm_eqn00191.gif), which is interpreted as the finite rotation ![](../graphics/stm_eqn00192.gif) superposed on the finite rotation ![](../graphics/stm_eqn00162.gif), is different from ![](../graphics/stm_eqn00193.gif), which is interpreted as the finite rotation ![](../graphics/stm_eqn00162.gif) superposed on the finite rotation ![](../graphics/stm_eqn00192.gif).

Although compound rotations are defined in terms of orthogonal matrices, in a numerical context the rotation vectors (or equivalently the quaternion parameters) associated with the rotation matrices are the degrees of freedom. Compound rotations are performed as follows: Given a quaternion parametrization ![](../graphics/stm_eqn00194.gif) and an incremental (finite) rotation ![](../graphics/stm_eqn00195.gif), where ![](../graphics/stm_eqn00196.gif) is defined in terms of an incremental rotation vector ![](../graphics/stm_eqn00197.gif) by [Equation 1.3.1&#8211;2](01s03a03-Rotation-variables.md), the total or compound rotation is given by the quaternion ![](../graphics/stm_eqn00198.gif), which is calculated as

![](../graphics/stm_eqn00199.gif)Here ![](../graphics/stm_eqn00200.gif) denotes the quaternion product and is defined as

![](../graphics/stm_eqn00201.gif)

[Equation 1.3.1&#8211;4](01s03a03-Rotation-variables.md) allows for the update of rotation fields without ever calculating the orthogonal matrix from the quaternion and without performing a matrix multiplication. Furthermore, all operations are singularity free regardless of the magnitude of the incremental rotation field ![](../graphics/stm_eqn00197.gif). The final (total) rotation vector can be calculated from the quaternion ![](../graphics/stm_eqn00202.gif) by inverting [Equation 1.3.1&#8211;2](01s03a03-Rotation-variables.md).

For the special case when compound rotations share the same rotation axis, the compound rotation reduces to an additive form. Let ![](../graphics/stm_eqn00196.gif) and ![](../graphics/stm_eqn00172.gif) have the same rotation axis ![](../graphics/stm_eqn00156.gif). Then ![](../graphics/stm_eqn00203.gif), ![](../graphics/stm_eqn00204.gif), and

![](../graphics/stm_eqn00205.gif)which reduces to

![](../graphics/stm_eqn00206.gif)
### Rotation vector extraction

For output purposes it is necessary to extract the rotation vector corresponding to a given quaternion. The extraction procedure is as follows: Let ![](../graphics/stm_eqn00207.gif) be the quaternion, and let ![](../graphics/stm_eqn00152.gif) be the rotation vector. Thus,

![](../graphics/stm_eqn00208.gif)

It is important to note that the extraction of the rotation vector from the quaternion is not unique. The magnitude ![](../graphics/stm_eqn00209.gif) is determined only up to the addition of ![](../graphics/stm_eqn00210.gif), ![](../graphics/stm_eqn00211.gif) Abaqus will always choose that rotation vector such that ![](../graphics/stm_eqn00212.gif).
### Director and rotation field updates

As an example of the utility of the quaternion parameters, consider the incremental update of a director field for either a beam or shell analysis. At some stage of the solution the director field ![](../graphics/stm_eqn00213.gif), the quaternion parametrization of the rotation field ![](../graphics/stm_eqn00214.gif), and the incremental rotation field ![](../graphics/stm_eqn00215.gif) are known at increment *i*. To update the director field by the incremental rotation to increment ![](../graphics/stm_eqn00216.gif), proceed as follows: First calculate the quaternion parametrization of the incremental rotation:

![](../graphics/stm_eqn00217.gif)The director field at ![](../graphics/stm_eqn00216.gif) is then defined as ![](../graphics/stm_eqn00218.gif), where ![](../graphics/stm_eqn00219.gif) is calculated with [Equation 1.3.1&#8211;3](01s03a03-Rotation-variables.md). Thus, the director is calculated directly from the quaternion as

![](../graphics/stm_eqn00220.gif)Furthermore, the update of the rotation field is obtained by quaternion multiplication ![](../graphics/stm_eqn00221.gif) and is defined by

![](../graphics/stm_eqn00222.gif)
### Variations of the rotation field

In the development of the balance equations, it is necessary to calculate the variation of the rotation field. Consider the vector field ![](../graphics/stm_eqn00001.gif), which is obtained by rotation of the reference vector field ![](../graphics/stm_eqn00007.gif):

![](../graphics/stm_eqn00223.gif)Variations ![](../graphics/stm_eqn00224.gif) in this field are obtained as

![](../graphics/stm_eqn00225.gif)where ![](../graphics/stm_eqn00226.gif) is the linearized rotation matrix; that is, the variation of the orthogonal tensor ![](../graphics/stm_eqn00162.gif). On the other hand, the variation can be defined in terms of the linearized rotation field ![](../graphics/stm_eqn00227.gif):

![](../graphics/stm_eqn00228.gif)Consequently, it follows that

![](../graphics/stm_eqn00229.gif)It is important to note that the linearized rotation ![](../graphics/stm_eqn00227.gif), which is analogous to the angular velocity in dynamics, is *not* the variation of the rotation vector ![](../graphics/stm_eqn00152.gif). By a straightforward (but involved) calculation, it can be shown that the variation of the rotation vector (![](../graphics/stm_eqn00230.gif)) is related to the linearized rotation ![](../graphics/stm_eqn00227.gif) by

![](../graphics/stm_eqn00231.gif)where

![](../graphics/stm_eqn00232.gif)The inverse of ![](../graphics/stm_eqn00233.gif) is

![](../graphics/stm_eqn00234.gif)

Let ![](../graphics/stm_eqn00235.gif) represent an infinitesimal change in the rotation field. A direct calculation of the variation of ![](../graphics/stm_eqn00236.gif), which is equivalent to calculation of the second variation of either ![](../graphics/stm_eqn00162.gif) or ![](../graphics/stm_eqn00001.gif), leads to an expression that is not symmetric in the variations ![](../graphics/stm_eqn00227.gif) and the changes ![](../graphics/stm_eqn00236.gif). However, it is shown in [Simo (1992)](07s01a01-References.md) that the correct definition of the Hessian operator---that is, the "covariant" derivative of the weak form of the balance equations---requires only the symmetric part (with respect to the variations) of the second variation. Thus, without loss of generality, we can write

![](../graphics/stm_eqn00237.gif)Similarly, the second variation of the vector field rotated by ![](../graphics/stm_eqn00162.gif) can be written as

![](../graphics/stm_eqn00238.gif)
### Velocity and acceleration

Taking the time derivative of the rotation matrix, we find with the same arguments as used in the calculation of the variations that

![](../graphics/stm_eqn00239.gif)where ![](../graphics/stm_eqn00240.gif) is the angular velocity matrix. Equivalently, the first and second time derivative of ![](../graphics/stm_eqn00001.gif) are written as

![](../graphics/stm_eqn00241.gif)The instantaneous angular velocity vector ![](../graphics/stm_eqn00242.gif) is related to the time rate of change of the rotation vector by the relation

![](../graphics/stm_eqn00243.gif)where ![](../graphics/stm_eqn00233.gif) is given by [Equation 1.3.1&#8211;6](01s03a03-Rotation-variables.md).

In the linearization of the dynamic balance equations, it is necessary to calculate the variation of the angular velocity, ![](../graphics/stm_eqn00244.gif). This quantity, however, can be calculated only by linearizing the specific algorithm used for the time integration of the dynamic equations.
### Coupling of rotations: constant velocity joint

Next, a more rigorous treatment of the two-dimensional constant velocity joint described in "MPC,"  Section 1.1.14 of the Abaqus User Subroutines Reference Guide, is presented. This derivation exemplifies some of the issues associated with the treatment of finite rotations. "Uniform collapse of straight and curved pipe segments,"  Section 1.1.5 of the Abaqus Benchmarks Guide, deals with a different finite rotation constraint and tackles additional complications.

Let *a*, *b*, *c* (see [Figure 1.3.1&#8211;1](01s03a03-Rotation-variables.md)) be the nodes making up the joint, with *a* the dependent node.

Figure 1.3.1&#8211;1 Nonlinear MPC example---constant velocity joint.

![](../graphics/umpc-const-vel-joint.png)The joint is operated by prescribing an axial rotation ![](../graphics/stm_eqn00245.gif) at *c* and an out-of-plane rotation ![](../graphics/stm_eqn00246.gif) at *b*. The compounding of these two prescribed rotation fields will determine the total rotation at *a*. We can formally write this constraint as follows:

![](../graphics/stm_eqn00247.gif)The constraint can be written in terms of the rotation matrices as

![](../graphics/stm_eqn00248.gif)With the previously defined variational expressions, the constraint can be linearized as

![](../graphics/stm_eqn00249.gif)This expression can be simplified by right-multiplying the expression by ![](../graphics/stm_eqn00250.gif) and by making use of the constraint [Equation 1.3.1&#8211;7](01s03a03-Rotation-variables.md), which yields

![](../graphics/stm_eqn00251.gif)which can be written in vector form as

![](../graphics/stm_eqn00252.gif)Since

![](../graphics/stm_eqn00253.gif)the linearized constraint is indeed identical to the one derived based on simple linear considerations in the Abaqus Analysis User's Guide.

The linearized constraint is used for the calculation of equilibrium. It can also be used for the recovery of the dependent rotation, ![](../graphics/stm_eqn00254.gif), as is done in the Abaqus Analysis User's Guide. The resulting rotation will satisfy the constraint approximately (unless one of the angles ![](../graphics/stm_eqn00255.gif) or ![](../graphics/stm_eqn00256.gif) is constant, in which case the constraint is linear and the recovery is exact).

For an exact enforcement of the constraint, user subroutine MPC must define the components of the total rotation vector ![](../graphics/stm_eqn00254.gif) exactly. To do so, ![](../graphics/stm_eqn00254.gif) must be updated based on the current values of ![](../graphics/stm_eqn00257.gif) and ![](../graphics/stm_eqn00258.gif). This is most easily accomplished with the aid of the quaternion parameters. Let ![](../graphics/stm_eqn00259.gif) and ![](../graphics/stm_eqn00260.gif) be the quaternion parameterizations associated with the finite rotation vectors ![](../graphics/stm_eqn00257.gif) and ![](../graphics/stm_eqn00258.gif), respectively. The total compound rotation ![](../graphics/stm_eqn00254.gif) is given by the quaternion ![](../graphics/stm_eqn00261.gif), where

![](../graphics/stm_eqn00262.gif)according to the quaternion compound formula [Equation 1.3.1&#8211;4](01s03a03-Rotation-variables.md). The rotation vector ![](../graphics/stm_eqn00254.gif) is extracted from the quaternion ![](../graphics/stm_eqn00263.gif) as follows:

![](../graphics/stm_eqn00264.gif)where ![](../graphics/stm_eqn00265.gif) is the norm of the vector ![](../graphics/stm_eqn00266.gif).

"MPC,"  Section 1.1.14 of the Abaqus User Subroutines Reference Guide, shows the implementation of the linearized form of the constraint in user subroutine MPC. The implementation of the exact nonlinear constraint is shown below:

SUBROUTINE MPC(UE,A,JDOF,MDOF,N,JTYPE,X,U,UINIT,MAXDOF,LMPC,
* KSTEP,KINC,TIME,NT,NF,TEMP,FIELD)
C
INCLUDE 'ABA_PARAM.INC'
C
DIMENSION UE(MDOF), A(MDOF,MDOF,N), JDOF(MDOF,N), X(6,N),
* U(MAXDOF,N), UINIT(MAXDOF,N), TIME(2), TEMP(NT,N),
* FIELD(NF,NT,N)
PARAMETER( SMALL = 1.E-14 )
C
IF ( JTYPE .EQ. 1 ) THEN
A(1,1,1) =  1.
A(2,2,1) =  1.
A(3,3,1) =  1.
A(3,1,2) = -1.
A(1,1,3) = -COS(U(6,2))
A(2,1,3) = -SIN(U(6,2))
C
JDOF(1,1) = 4
JDOF(2,1) = 5
JDOF(3,1) = 6
JDOF(1,2) = 6
JDOF(1,3) = 4
C
CPHIB = COS(0.5*U(6,2))
SPHIB = SIN(0.5*U(6,2))
CPHIC = COS(0.5*U(4,3))
SPHIC = SIN(0.5*U(4,3))
C
QA0 = CPHIB*CPHIC
QAX = CPHIB*SPHIC
QAY = SPHIB*SPHIC
QAZ = CPHIB*SPHIC
C
QAMAG = SQRT( QAX*QAX + QAY*QAY + QAZ*QAZ )
IF ( QAMAG .GT. SMALL ) THEN
PHIA  = 2.*ATAN2( QAMAG , QA0 )
UE(1) = PHIA*QAX/QAMAG
UE(2) = PHIA*QAY/QAMAG
UE(3) = PHIA*QAZ/QAMAG
ELSE
UE(1) = 0.
UE(2) = 0.
UE(3) = 0.
END IF
END IF
C
RETURN
END
### Reference

### Reference

"Conventions,"  Section 1.2.2 of the Abaqus Analysis User's Guide