# E







### eddy currents

Electric currents generated in a conductor that is placed in a time-varying magnetic field. Abaqus/Standard provides electromagnetic capabilities that can solve time-harmonic and transient eddy current problems.
For more information:- ["Eddy current analysis," Section 6.7.5 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-anl-aeddycurrent)

### edge parameter

A position along an edge, expressed as a fraction of its length. An edge parameter is used to partition an edge and to position a datum along an edge. Abaqus/CAE displays an arrow along the edge indicating the direction of increasing parameter value from the start vertex (corresponding to an edge parameter value of zero) to the end vertex (corresponding to a value of one).
For more information:- ["Creating a datum point by entering an edge parameter," Section 62.6.5 of the Abaqus/CAE User's Guide](../usi/usi-link.md#usi-dtm-point-edgeparam)

- ["Using the enter parameter method to partition edges," Section 70.5.2 of the Abaqus/CAE User's Guide](../usi/usi-link.md#usi-par-sptedgeparameterbtn)

### element set

A named collection of elements.
For more information:- ["Element definition," Section 2.2.1 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-int-ielement)

- [Chapter 73, "The Set and Surface toolsets," of the Abaqus/CAE User's Guide](../usi/usi-link.md#usi-set)

### Elysium Neutral file

A file format used to import geometry from the following CAD applications using the appropriate Elysium translator plug-in:
- NX using the Abaqus/CAE Associative Interface for NX.
- Pro/ENGINEER using the Pro/ENGINEER Associative Interface.

You can import parts in Elysium Neutral File format; however, you cannot export parts in Elysium Neutral File format.
For more information:- ["What kinds of files can be imported and exported from Abaqus/CAE?," Section 10.1.1 of the Abaqus/CAE User's Guide](../usi/usi-link.md#usi-imp-concepts-whatkind)

- ["Importing parts," Section 10.7.2 of the Abaqus/CAE User's Guide](../usi/usi-link.md#usi-dbs-import-part)

### encastre

A fixed displacement and rotation boundary condition.

### encrypt

To convert an Abaqus data file into an encoded, password-protected format that only authorized parties can access. The **abaqus encrypt** utility is intended for the encryption of data that you include by reference in input (`.inp`) files or other data files.
For more information:- ["Encrypting and decrypting Abaqus input data," Section 3.2.38 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-int-dencryptproc)

### EPS (Encapsulated PostScript)

A variation of PostScript that describes a single graphic designed to be included in a larger document without modification. Abaqus/CAE allows you to save images of selected viewports in EPS-format files.
For more information:- ["Printed image formats," Section 8.1.1 of the Abaqus/CAE User's Guide](../usi/usi-link.md#uss-pri-conc-gif)

### equation solver

The solution procedure for a linear system of equations in Abaqus/Standard. Available linear equation system solution techniques include the direct linear equation solver, the iterative linear equation solver, the subspace iteration eigenvalue solver, the Lanczos eigenvalue solver, and the AMS eigenvalue solver. 
For more information:- ["Direct linear equation solver," Section 6.1.5 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-anl-asolveroverview)

- ["Iterative linear equation solver," Section 6.1.6 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-anl-aitrsolveroverview)

- ["Selecting the eigenvalue extraction method" in "Eigenvalue buckling prediction," Section 6.2.3 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-anl-aeigenbuckling-eigensolver)

- ["Dynamic analysis procedures: overview," Section 6.3.1 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-anl-adynamicproc)

- ["Natural frequency extraction," Section 6.3.5 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-anl-afreqextraction)

### error indicator

A metric used during adaptive meshing to measure error in the base solution. An error indicator determines where a mesh needs refinement to achieve an error goal. 
For more information:- ["Selection of error indicators influencing adaptive remeshing," Section 12.3.2 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-anl-aadperrorindicators)

### error indicator output variable

An output variable selected to use in the calculation of the error indicator. Error indicator output variables have an “ERI” suffix; for example, MISESERI.
For more information:- ["Selection of error indicators influencing adaptive remeshing," Section 12.3.2 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-anl-aadperrorindicators)

### error target

A user-defined remeshing goal described as a percentage target for a normalized form of the error indicator output variable. The normalized form of the error indicator for a particular variable is the ratio of the value of the error indicator to the value of the base solution.
For more information:- ["Selection of error indicators influencing adaptive remeshing," Section 12.3.2 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-anl-aadperrorindicators)

### Eulerian analysis

A finite element technique in which materials can flow through the elements in a model's mesh. Abaqus offers two implementations of the Eulerian technique: pure Eulerian analysis and Arbitrary Lagrangian-Eulerian (ALE) adaptive meshing. In a pure Eulerian analysis the mesh is rigid and the model behavior is defined by the flow of material through the mesh. ALE adaptive meshing is a technique that combines the features of Lagrangian analysis and Eulerian analysis within the same mesh to maintain a high mesh quality during analyses involving large deformations.
For more information:- ["ALE adaptive meshing: overview," Section 12.2.1 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-anl-aaleover)

- ["Eulerian analysis," Section 14.1.1 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-anl-aeuleriananalysis)

- [Chapter 28, "Eulerian analyses," of the Abaqus/CAE User's Guide](../usi/usi-link.md#usi-adv-eulerian)

### Eulerian-Lagrangian analysis

A finite element technique that involves the interaction between pure Eulerian part instances and pure Lagrangian part instances within the same model. Contact can be defined between the elements in the Lagrangian part and the material boundaries in the Eulerian part.
For more information:- ["Eulerian analysis," Section 14.1.1 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-anl-aeuleriananalysis)

- [Chapter 28, "Eulerian analyses," of the Abaqus/CAE User's Guide](../usi/usi-link.md#usi-adv-eulerian)

### Eulerian part

A part that acts as a domain in which materials can flow in an Eulerian analysis. Any arbitrarily shaped three-dimensional part that you can create or import in Abaqus/CAE can be specified as an Eulerian part.
For more information:- ["Part types," Section 11.4.2 of the Abaqus/CAE User's Guide](../usi/usi-link.md#usi-prt-conc-type)

### extended functionality release

An Abaqus release that provides early access to a subset of features developed for the next general release. An extended functionality release is designated by the product name and release number followed by EF and a single digit, such as Abaqus 6.14-EF1 (extended functionality general release) and Abaqus 6.14-EF2 (extended functionality maintenance delivery). See also [general release](gl01gls08.md#gls-generalrelease) and [maintenance delivery](gl01gls14.md#gls-maintdelivery).




