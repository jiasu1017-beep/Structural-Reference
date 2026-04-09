# 1.2.1 Notation

### 1.2.1 Notation

**Products: **Abaqus/Standard  Abaqus/Explicit

Notation is often a serious obstacle that prevents an engineer from using advanced textbooks; for example, general curvilinear tensor analysis and functional analysis are both necessary in some of the theories used in Abaqus, but the unfamiliar notations commonly used in these areas often discourage the user from pursuing their study. The notation used in most of this guide (direct matrix notation) may be unfamiliar to some readers; but it is not difficult or time consuming to gain enough familiarity with the notation for it to be useful, and it is definitely worthwhile. This notation is commonly used in the modern engineering literature---it is a shorthand version of the familiar matrix notation used in many older engineering textbooks. The notation is appealing---once it is understood---because it allows the equations to be developed concisely, and the physical ideas can be perceived without the distraction of the complexities that arise from the choice of the particular basis system that will eventually be used to express the same concepts in component form. Because the notation has become so standard in the literature, the user who wishes or needs to read textbooks and papers that are related to the use of Abaqus will find that familiarity with this notation is desirable.

Both direct matrix notation and component form notation are used in the guide. Both notations are described in this section. Direct matrix notation is used whenever possible. However, vectors, matrices, and the higher-order tensors used in the theories must eventually be written in component form to store them as a set of numbers on the computer. Thus, both ways of writing these quantities will be needed in the guide.
### Basic quantities

The quantities needed to formulate the theory are scalars, vectors, second-order tensors (matrices), and---occasionally---fourth-order tensors (for example, the stress-strain transformation for linear elasticity). In direct matrix notation these are written as:| a scalar value | a |
| --- | --- |
| a vector | or |
| with the transpose | or |
| a second-order tensor or matrix | or |
| with the transpose | or |
| and |
| a fourth-order tensor |  |

Vectors and second-order tensors (matrices) are written in the same way: they are distinguished by the context. In direct matrix notation there is generally no need to indicate that a vector must be transposed. The context determines whether a vector is to be used as a "column" vector ![](../graphics/stm_eqn00001.gif) or as a "row" vector ![](../graphics/stm_eqn00003.gif). In this case the transpose superscript is only used to improve the readability of an expression. On the other hand, for second-order nonsymmetric tensors the addition of a transpose superscript will change the meaning of an expression.

This representation of vectors and tensors is very general and convenient for developing the theory so that the equations can be understood easily in terms of their physical meaning. However, in actual computations we have to work with individual numbers, so vectors and tensors must be expressed in terms of their components. These components are associated with an axis system that defines a set of base vectors at each point in space. The simplest axis system is rectangular Cartesian, because the base vectors are orthogonal unit vectors in the same direction at all points. Unfortunately, we need more generality than this because we will be dealing with shells and beams, where stress, strain, etc. are most conveniently described in terms of directions on the surface of the shell (or associated with the axis of the beam), and these usually change as we move around on the surface. To retain this necessary generality and express vectors and matrices in component form, we introduce a general set of base vectors, ![](../graphics/stm_eqn00008.gif), ![](../graphics/stm_eqn00009.gif), which are not necessarily orthogonal or of unit length but are sufficient to define the components of a vector (for this purpose they must not be parallel or have zero length). A vector ![](../graphics/stm_eqn00001.gif) can then be written

![](../graphics/stm_eqn00010.gif)where the numbers ![](../graphics/stm_eqn00011.gif), ![](../graphics/stm_eqn00012.gif), and ![](../graphics/stm_eqn00013.gif) are the components of ![](../graphics/stm_eqn00001.gif) associated with ![](../graphics/stm_eqn00014.gif), ![](../graphics/stm_eqn00015.gif), and ![](../graphics/stm_eqn00016.gif).

In actual cases the ![](../graphics/stm_eqn00008.gif) are chosen for convenience (for example, see "Conventions,"  Section 1.2.2 of the Abaqus Analysis User's Guide, for a description of how base vectors are chosen for surface elements in Abaqus), and then the ![](../graphics/stm_eqn00017.gif) are obtained.

To save writing, we adopt the usual summation convention that a repeated index is summed---in this case over the range 1 to 3---so that the above equation is written

![](../graphics/stm_eqn00018.gif)Likewise, the component form of a matrix will be

![](../graphics/stm_eqn00019.gif)or, written out,

![](../graphics/stm_eqn00020.gif) Similarly, a fourth-order tensor can be written in component form as

![](../graphics/stm_eqn00021.gif)

While we will need such completely general base vectors for describing the stresses and strains on shells and beams, in many cases it is convenient to use rectangular Cartesian components so that the ![](../graphics/stm_eqn00008.gif) are orthogonal unit vectors. To distinguish this particular case, we will use Latin indices instead of Greek indices. Thus, ![](../graphics/stm_eqn00008.gif) are a set of general base vectors; while ![](../graphics/stm_eqn00022.gif) are rectangular Cartesian base vectors; and ![](../graphics/stm_eqn00017.gif) is the component of the vector ![](../graphics/stm_eqn00001.gif) along a general base vector, while ![](../graphics/stm_eqn00023.gif), ![](../graphics/stm_eqn00024.gif), is the component of ![](../graphics/stm_eqn00001.gif) along the *i*th Cartesian direction.

Vector and tensor concepts and their representation are discussed in many textbooks---see [Flugge (1972)](07s01a01-References.md), for example.
### Basic operations

The usual matrix and vector operators are indicated in this guide as follows:

Dot product of two vectors:

![](../graphics/stm_eqn00025.gif)

(The dot symbol defines this operation completely, regardless of whether ![](../graphics/stm_eqn00026.gif) or ![](../graphics/stm_eqn00027.gif) is transposed---i.e., ![](../graphics/stm_eqn00028.gif))

Cross product of two vectors:

![](../graphics/stm_eqn00029.gif)

Matrix multiplication:

![](../graphics/stm_eqn00030.gif)

(It is implicitly assumed that ![](../graphics/stm_eqn00026.gif) and ![](../graphics/stm_eqn00027.gif) are dimensioned correctly, as needed for the operation to make sense; in addition, if ![](../graphics/stm_eqn00026.gif) is a nonsymmetric tensor, ![](../graphics/stm_eqn00031.gif))

Scalar product of two matrices:

![](../graphics/stm_eqn00032.gif)

This operation means that corresponding conjugate components of the two matrices are multiplied as pairs and the products summed. Thus, for instance, if ![](../graphics/stm_eqn00026.gif) is the stress matrix, ![](../graphics/stm_eqn00033.gif), and ![](../graphics/stm_eqn00027.gif) the conjugate rate of strain matrix, ![](../graphics/stm_eqn00034.gif), then ![](../graphics/stm_eqn00035.gif) would give the rate of internal work per volume, ![](../graphics/stm_eqn00036.gif).

It is also necessary to define the dyadic product of two vectors:

![](../graphics/stm_eqn00037.gif)

This operation creates a second-order tensor (or dyad) out of two vectors. In component notation this notation is equivalent to ![](../graphics/stm_eqn00038.gif).

A matrix of derivatives,

![](../graphics/stm_eqn00039.gif)means

![](../graphics/stm_eqn00040.gif)Throughout this guide it will be assumed implicitly that, when a derivative is taken with respect to time, we mean the *material* time derivative; that is, the change in a variable with respect to time whilst looking at a particular material particle. When this is not the case for a particular equation, it will be stated explicitly when the equation appears.

Provided that we are careful about interpreting ![](../graphics/stm_eqn00041.gif) in the manner illustrated above, standard concepts of elementary calculus clearly hold; for example, if ![](../graphics/stm_eqn00001.gif) is a vector-valued function of the vector-valued function ![](../graphics/stm_eqn00026.gif), which in turn is a vector-valued function of ![](../graphics/stm_eqn00027.gif), that is ![](../graphics/stm_eqn00042.gif), then

![](../graphics/stm_eqn00043.gif)or, if ![](../graphics/stm_eqn00044.gif):

![](../graphics/stm_eqn00045.gif)

Due to these properties many useful results can be obtained quickly and expressed in a compact, easily understood, form.
### Components of a vector or a matrix in a coordinate system

In the previous section we introduced the idea that a vector ![](../graphics/stm_eqn00001.gif) or a matrix ![](../graphics/stm_eqn00001.gif) can be written in terms of components associated with some conveniently chosen set of base vectors, ![](../graphics/stm_eqn00008.gif). We now show how the components ![](../graphics/stm_eqn00017.gif) (or ![](../graphics/stm_eqn00046.gif)) are obtained. We can do so using the dot product. For each of the three base vectors, ![](../graphics/stm_eqn00047.gif), we define a conjugate base vector ![](../graphics/stm_eqn00048.gif), as follows. Choose ![](../graphics/stm_eqn00049.gif) as normal to ![](../graphics/stm_eqn00015.gif) and ![](../graphics/stm_eqn00016.gif), such that the dot product ![](../graphics/stm_eqn00050.gif). Similarly, choose ![](../graphics/stm_eqn00051.gif) normal to ![](../graphics/stm_eqn00016.gif) and ![](../graphics/stm_eqn00014.gif), such that ![](../graphics/stm_eqn00052.gif); and ![](../graphics/stm_eqn00053.gif) normal to ![](../graphics/stm_eqn00014.gif) and ![](../graphics/stm_eqn00015.gif), such that ![](../graphics/stm_eqn00054.gif). Thus,

![](../graphics/stm_eqn00055.gif)

![](../graphics/stm_eqn00056.gif)

![](../graphics/stm_eqn00057.gif)We can write this compactly as

![](../graphics/stm_eqn00058.gif)where ![](../graphics/stm_eqn00059.gif) if ![](../graphics/stm_eqn00060.gif), and ![](../graphics/stm_eqn00061.gif), otherwise. (![](../graphics/stm_eqn00062.gif) is called the "Kronecker delta.") In matrix notation ![](../graphics/stm_eqn00063.gif) is the unit matrix ![](../graphics/stm_eqn00064.gif): we can also write the above equation defining ![](../graphics/stm_eqn00049.gif), ![](../graphics/stm_eqn00051.gif), and ![](../graphics/stm_eqn00053.gif) in matrix form as

![](../graphics/stm_eqn00065.gif)so that, if one set of base vectors---![](../graphics/stm_eqn00022.gif), say---is known, the others are easily obtained.

With this additional set of base vectors, we can immediately obtain the components of a vector or a matrix as follows.

Consider a vector ![](../graphics/stm_eqn00001.gif). Then ![](../graphics/stm_eqn00066.gif) (writing ![](../graphics/stm_eqn00001.gif) in component form, using the basis vectors ![](../graphics/stm_eqn00067.gif)), and since ![](../graphics/stm_eqn00068.gif), only if ![](../graphics/stm_eqn00060.gif),

![](../graphics/stm_eqn00069.gif)In exactly the same way we could have written

![](../graphics/stm_eqn00070.gif) by expressing ![](../graphics/stm_eqn00001.gif) as components associated with the ![](../graphics/stm_eqn00048.gif) base vectors, ![](../graphics/stm_eqn00071.gif).

Similarly, for a matrix,

![](../graphics/stm_eqn00072.gif)and

![](../graphics/stm_eqn00073.gif)

These component definitions are particularly convenient for calculating the dot product of two vectors, for we can write

![](../graphics/stm_eqn00074.gif)which is

![](../graphics/stm_eqn00075.gif)

Similarly, the scalar product of two matrices is

![](../graphics/stm_eqn00076.gif)that is, we simply multiply corresponding entries in the ![](../graphics/stm_eqn00077.gif) and ![](../graphics/stm_eqn00078.gif) arrays, arranged as matrices, and then sum the products.

Finally, on the computer we need to store only one form of component: ![](../graphics/stm_eqn00079.gif), ![](../graphics/stm_eqn00077.gif) or ![](../graphics/stm_eqn00017.gif), ![](../graphics/stm_eqn00046.gif). We can always go from one to the other using the "metric tensor," ![](../graphics/stm_eqn00080.gif), and its inverse, ![](../graphics/stm_eqn00081.gif), which are defined as

![](../graphics/stm_eqn00082.gif)and

![](../graphics/stm_eqn00083.gif)

For

![](../graphics/stm_eqn00084.gif) Thus, ![](../graphics/stm_eqn00085.gif); similarly ![](../graphics/stm_eqn00086.gif), and, by extension, for matrices,

![](../graphics/stm_eqn00087.gif)and

![](../graphics/stm_eqn00088.gif)

The metric tensor and its inverse are symmetric:

![](../graphics/stm_eqn00089.gif)

The two sets of base vectors and components of vectors or matrices associated with them are named as follows:|  | are covariant base vectors, |
| --- | --- |
|  | are contravariant base vectors, |
|  | are covariant components of a vector (or matrix), |
|  | are contravariant components of a vector (or matrix). | Thus, the contravariant components are those associated with the covariant base vectors, ![](../graphics/stm_eqn00092.gif), and vice versa. The simplest case is when the basis is a set of orthogonal unit vectors (a rectangular Cartesian system) because then---from the definition ![](../graphics/stm_eqn00093.gif)---we see that ![](../graphics/stm_eqn00094.gif), and so ![](../graphics/stm_eqn00095.gif) and we need not distinguish the type of component. Whenever possible a rectangular Cartesian system is chosen, so the type of component need not be distinguished. This system is discussed in more detail in the sections on beam elements and shell elements.
### Components of a derivative

Consider a vector-valued function, ![](../graphics/stm_eqn00026.gif), which is expressed in component form on a basis system, ![](../graphics/stm_eqn00008.gif). Let the vector-valued function ![](../graphics/stm_eqn00001.gif) depend on ![](../graphics/stm_eqn00026.gif): ![](../graphics/stm_eqn00096.gif). Then

![](../graphics/stm_eqn00097.gif) so that the component of ![](../graphics/stm_eqn00098.gif) associated with a change ![](../graphics/stm_eqn00099.gif) is

![](../graphics/stm_eqn00100.gif)which we write, for convenience, as

![](../graphics/stm_eqn00101.gif)meaning

![](../graphics/stm_eqn00102.gif)

Now suppose ![](../graphics/stm_eqn00001.gif) is written on a different basis---![](../graphics/stm_eqn00103.gif), say---so that we store ![](../graphics/stm_eqn00001.gif) as the components

![](../graphics/stm_eqn00104.gif)Then

![](../graphics/stm_eqn00105.gif)

Typically we would then write

![](../graphics/stm_eqn00106.gif)where

![](../graphics/stm_eqn00107.gif)

Readers who are familiar with general curvilinear tensor analysis will recognize ![](../graphics/stm_eqn00108.gif) as the covariant derivative of ![](../graphics/stm_eqn00079.gif) with respect to ![](../graphics/stm_eqn00109.gif), often written as ![](../graphics/stm_eqn00110.gif). The advantage of the direct matrix notation is clear: because we can imagine ![](../graphics/stm_eqn00001.gif) and ![](../graphics/stm_eqn00026.gif) as vectors in space, we have a physical understanding of what we mean by ![](../graphics/stm_eqn00111.gif); it is the change in the vector-valued function ![](../graphics/stm_eqn00001.gif) as a function of another vector-valued function ![](../graphics/stm_eqn00026.gif). For computations we must express ![](../graphics/stm_eqn00001.gif) and ![](../graphics/stm_eqn00026.gif) in component form. Then

![](../graphics/stm_eqn00112.gif)provides the necessary components once we have chosen convenient basis systems: ![](../graphics/stm_eqn00008.gif) for ![](../graphics/stm_eqn00026.gif) and ![](../graphics/stm_eqn00103.gif) for ![](../graphics/stm_eqn00001.gif). Typically ![](../graphics/stm_eqn00008.gif) and ![](../graphics/stm_eqn00103.gif) will both be the simple rectangular Cartesian bases

![](../graphics/stm_eqn00113.gif)everywhere. But sometimes we must use more complicated basis systems---examples are when we need quantities associated with the surface of a general shell and when the symmetry of the geometry and, possibly, of the deformation makes it convenient to work in an axisymmetric system. The careful projection of the general results written in direct matrix notation onto the chosen basis system allows us to implement the theory for computation.

As an example, consider the usual expression for strain rate,

![](../graphics/stm_eqn00114.gif)which requires the matrix ![](../graphics/stm_eqn00115.gif) to be evaluated, where ![](../graphics/stm_eqn00116.gif) is the velocity of the material currently flowing through the point ![](../graphics/stm_eqn00117.gif) in space. Let us now derive the components of ![](../graphics/stm_eqn00118.gif) when the basis system for both ![](../graphics/stm_eqn00116.gif) and ![](../graphics/stm_eqn00117.gif) is the cylindrical system that we usually choose for axisymmetric problems, with the basis vectors

![](../graphics/stm_eqn00119.gif)(in Abaqus for axisymmetric cases we always take the components in this order---radial, axial, circumferential). These basis vectors are orthogonal and of unit length, so that ![](../graphics/stm_eqn00120.gif)

We consider position to be defined by the coordinates ![](../graphics/stm_eqn00121.gif), with

![](../graphics/stm_eqn00122.gif)so that

![](../graphics/stm_eqn00123.gif)

Thus,

![](../graphics/stm_eqn00124.gif)where

![](../graphics/stm_eqn00125.gif)so that

![](../graphics/stm_eqn00126.gif)We know that

![](../graphics/stm_eqn00127.gif)so that

![](../graphics/stm_eqn00128.gif)and thus,

![](../graphics/stm_eqn00129.gif)The components of the strain rate are thus

![](../graphics/stm_eqn00130.gif)

![](../graphics/stm_eqn00131.gif)and

![](../graphics/stm_eqn00132.gif)For the case of purely axisymmetric deformation, ![](../graphics/stm_eqn00133.gif) and ![](../graphics/stm_eqn00134.gif), so these results simplify to the familiar expressions

![](../graphics/stm_eqn00135.gif)

![](../graphics/stm_eqn00136.gif)

In summary, direct matrix notation allows us to obtain all our fundamental results without reference to any particular choice of coordinate system. Careful application of the concept of the covariant derivative then allows these general results to be projected into component form for computation.
### Virtual quantities

The concepts of virtual displacements and virtual work are fundamental to the development. Virtual quantities are infinitesimally small variations of physical measures, such as displacement, strain, velocity, and so on. The virtual variation of a scalar quantity *a* is indicated by ![](../graphics/stm_eqn00137.gif); of a vector or matrix ![](../graphics/stm_eqn00001.gif) by ![](../graphics/stm_eqn00138.gif).

We extend this notation to such expressions as

![](../graphics/stm_eqn00139.gif)which is the symmetric part of the spatial gradient of a virtual vector field ![](../graphics/stm_eqn00140.gif). This notation corresponds to the virtual rate of deformation (a measure of strain rate) if ![](../graphics/stm_eqn00140.gif) is a virtual velocity field.
### Initial and current positions

Most structural problems concern the description of the way a structure behaves as it is loaded and moves from its reference configuration. Thus, we often compare positions of a point in the current (deformed) configuration and a reference configuration that is usually chosen as the configuration when the structure is unloaded or, in the case of geotechnical problems, when the model is subject only to geostatic stresses. To distinguish these configurations, we use lowercase type (![](../graphics/stm_eqn00117.gif)) to indicate the current position and uppercase type (![](../graphics/stm_eqn00141.gif)) to indicate the initial position of the same material point in the same spatial coordinate frame. In Abaqus we almost always store the rectangular Cartesian components of ![](../graphics/stm_eqn00141.gif) and ![](../graphics/stm_eqn00117.gif). The exception is in axisymmetric structures, where radial (*r*) and axial (*z*) components are stored.
### Nodal variables

So far we have discussed quantities that are considered to be associated with all points in a model. The finite element approximation is based on assuming interpolations, by which displacement, position, and---often---other variables at any material point are defined by a finite number of nodal variables. In this guide we use uppercase superscripts to refer to individual nodal variables or nodal vectors and adopt the summation convention for these indices.

Hence, the interpolation can be written quite generally as

![](../graphics/stm_eqn00142.gif)where ![](../graphics/stm_eqn00001.gif) is some vector-valued function at any point in the structure; ![](../graphics/stm_eqn00143.gif), ![](../graphics/stm_eqn00144.gif) up to the total number of variables in the problem, is a set of *N* vector interpolation functions (these are functions of the material coordinates, ![](../graphics/stm_eqn00145.gif)); and ![](../graphics/stm_eqn00146.gif), ![](../graphics/stm_eqn00144.gif) is a set of nodal variables.

In some sections in this guide we need to describe operations on nodal variables for the complete system of finite element equations. In these sections we use the classical matrix-vector notation. In this notation ![](../graphics/stm_eqn00004.gif) represents a column vector containing nodal variables, ![](../graphics/stm_eqn00002.gif) represents a row vector, and a matrix is written as ![](../graphics/stm_eqn00147.gif). Common operations are the scalar product between two vectors,

![](../graphics/stm_eqn00148.gif)(which is equivalent to ![](../graphics/stm_eqn00149.gif) in index notation) and the matrix-vector product

![](../graphics/stm_eqn00150.gif)(which is equivalent to ![](../graphics/stm_eqn00151.gif) in index notation).