# 1.2 Abaqus products







Individual components of the Abaqus suite are described in this section. 

### Analysis

**Abaqus/Standard**: This general-purpose analysis product can solve a wide range of linear and nonlinear problems involving the static, dynamic, thermal, electrical, and electromagnetic response of components. Abaqus/Standard includes all analysis capabilities except those provided in the Abaqus/Explicit and Abaqus/CFD programs and the add-on analysis functionality described below.

**Abaqus/Explicit**: This product provides nonlinear, transient, dynamic analysis of solids and structures using explicit time integration. Its powerful contact capabilities, reliability, and computational efficiency on large models also make it highly effective for quasi-static applications involving discontinuous nonlinear behavior.

**Abaqus/CFD**: This product is a computational fluid dynamics program with support for preprocessing, simulation, and postprocessing in Abaqus/CAE. Abaqus/CFD provides scalable parallel CFD simulation capabilities to address a number of nonlinear coupled fluid-thermal and fluid-structural problems.

### Preprocessing and postprocessing

**Abaqus/CAE**: This product is a Complete Abaqus Environment that provides a simple, consistent interface for creating, submitting, monitoring, and evaluating results from Abaqus simulations. Abaqus/CAE is divided into modules, where each module defines a logical aspect of the modeling process; for example, defining the geometry, defining material properties, generating a mesh, submitting analysis jobs, and interpreting results.

**Abaqus/Viewer**: This subset of Abaqus/CAE contains only the postprocessing capabilities of the Visualization module. It uses the output database (`.odb`) to obtain results from the analysis products. The output database is a neutral binary file. Therefore, results from an Abaqus analysis run on any platform can be viewed on any other platform supporting Abaqus/Viewer. It provides deformed configuration, contour, vector, and *X–Y* plots, as well as animation of results.

### Add-on analysis

**Abaqus/Aqua**: This add-on analysis capability for Abaqus/Standard and Abaqus/Explicit provides a capability for calculating drag and buoyancy loads based on steady current, wave, and wind effects for modeling offshore piping and floating platform structures. Abaqus/Aqua is applicable for structures that can be idealized using line elements, including beam, pipe, and truss elements.

**Abaqus/Design**: This add-on analysis capability for Abaqus/Standard allows the user to perform design sensitivity analysis (DSA). The derivatives of output variables are calculated with respect to specified design parameters.

**Optimization Module**: This capability is available in Abaqus/CAE to perform shape and topology optimization. This functionality requires an additional license to submit an optimization process for analysis.

**Abaqus/Foundation**: This analysis option offers more efficient access to the linear static and dynamic analysis functionality in Abaqus/Standard.

**CZone for Abaqus**: This add-on capability for Abaqus/Explicit provides access to a state-of-the-art methodology for crush simulation based on CZone technology from Engenuity, Ltd. Targeted toward the design of composite components and assemblies, CZone for Abaqus provides for inclusion of material crush behavior in simulations of composite structures subjected to impact.

### Optional analysis functionality

**Abaqus/AMS**: This add-on analysis capability for Abaqus/Standard allows the user to select the automatic multi-level substructuring (AMS) eigensolver when performing a natural frequency extraction.

**Co-simulation with MpCCI**: This add-on analysis capability for Abaqus can be used to solve multiphysics problems by coupling Abaqus with any third-party analysis program that supports the MpCCI interface.

### Associative interfaces and geometry translators

**SIMULIA Associative Interface for Abaqus/CAE**: This add-on capability for Abaqus/CAE creates a connection between a CATIA V6 session and an Abaqus/CAE session. This connection can be used to transfer model information from CATIA V6 to Abaqus/CAE. Subsequent modifications to the model in CATIA V6 can be propagated to the Abaqus/CAE model while retaining any analysis features (such as loads or boundary conditions) that were defined on the model in Abaqus/CAE. The CATIA V6 model in an assembly file (`.eaf`) format can also be imported directly into Abaqus/CAE.

**CATIA V5 Associative Interface**: This add-on capability for Abaqus/CAE creates a connection between a CATIA V5 session and an Abaqus/CAE session. This connection can be used to transfer model information from CATIA V5 to Abaqus/CAE. Subsequent modifications to the model in CATIA V5 can be propagated to the Abaqus/CAE model while retaining any analysis features (such as loads or boundary conditions) that were defined on the model in Abaqus/CAE. The geometry of CATIA V5-format Part (`.CATPart`) and Product (`.CATProduct`) files can also be imported directly into Abaqus/CAE.

**SolidWorks Associative Interface**: This add-on capability for Abaqus/CAE creates a connection between a SolidWorks session and an Abaqus/CAE session. This connection can be used to transfer model information from SolidWorks to Abaqus/CAE. Subsequent modifications to the model in SolidWorks can be propagated to the Abaqus/CAE model while retaining any analysis features (such as loads or boundary conditions) that were defined on the model in Abaqus/CAE.

**Pro/ENGINEER Associative Interface**: This add-on capability for Abaqus/CAE creates a connection between a Pro/ENGINEER session and an Abaqus/CAE session. This connection can be used to transfer model information between Pro/ENGINEER and Abaqus/CAE. Modifications to the model in Pro/ENGINEER can be propagated to the Abaqus/CAE model without affecting any analysis features (such as loads or boundary conditions) that were defined on the model in Abaqus/CAE, and certain geometric modifications can be made in Abaqus/CAE and propagated to the model in Pro/ENGINEER.

**Abaqus/CAE Associative Interface for NX**: This add-on capability for Abaqus/CAE creates a connection between an NX session and an Abaqus/CAE session. This connection can be used to transfer model data and to propagate design changes between NX and Abaqus/CAE. The Abaqus/CAE Associative Interface for NX can be purchased and downloaded from Elysium Inc. ([www.elysiuminc.com](http://www.elysiuminc.com)).

**Geometry Translator for CATIA V4**: This add-on capability allows the user to import the geometry of CATIA V4-format parts and CATIA V4 assemblies (`.model`, `.catdata`, and `.exp` files) directly into Abaqus/CAE.

**Geometry Translator for Parasolid**: This add-on capability allows the user to import the geometry of Parasolid-format parts and Parasolid assemblies (`.x_t`, `.x_b`, and `.xmt` files) directly into Abaqus/CAE.

### Translator utilities

- Abaqus translators are provided with the release. They are invoked through the Abaqus execution procedure (the "driver"). The translators and the commands to invoke them are described below: - **abaqus fromansys** translates an ANSYS input file to an Abaqus input file. - **abaqus fromdyna** translates an LS-DYNA keyword file to an Abaqus input file. - **abaqus fromnastran** translates a Nastran bulk data file to an Abaqus input file. - **abaqus frompamcrash** translates a PAM-CRASH input file to a partial Abaqus input file. - **abaqus fromradioss** translates a RADIOSS input file to a partial Abaqus input file. - **abaqus adams** translates the results in an Abaqus SIM database file into an MSC.ADAMS modal neutral (`.mnf`) file, the format required by ADAMS/Flex. - **abaqus moldflow** translates finite element model information from a Moldflow analysis into a partial Abaqus input file. - **abaqus tonastran** translates an Abaqus input file to Nastran bulk data file format. - **abaqus toOutput2** translates an Abaqus output database file to the Nastran Output2 file format. - **abaqus tozaero** enables you to exchange aeroelastic data between the Abaqus and ZAERO analysis products.

### Other utilities

- Additional programs are included with the release. They are all invoked through the Abaqus execution procedure (the "driver"). The utilities and the commands to invoke these programs are described below: - **abaqus append** joins separate results files into a single file. - **abaqus ascfil** translates Abaqus results files between ASCII and binary formats, which is useful for moving results files between different computer types. - **abaqus cosimulation** runs a co-simulation using a single command where the analysis job options specify two Abaqus jobs. - **abaqus cse** runs the SIMULIA Co-Simulation Engine (CSE) Director process that governs co-simulation between Abaqus and third-party solvers. Typically, when performing a co-simulation between Abaqus solvers only, you are not required to invoke the CSE Director process; it is invoked automatically when you run the Abaqus co-simulation procedure using **abaqus cosimulation**. - **abaqus doc** accesses the Abaqus documentation collection using a web browser. - **abaqus dymola** runs a co-simulation between an Abaqus/Standard or Abaqus/Explicit model and a model exported from Dymola. - **abaqus emloads** converts results output from an electromagnetic analysis for use as loads in a subsequent analysis. - **abaqus encrypt** creates an encoded, password-protected version of an Abaqus input file, while **abaqus decrypt** converts an encrypted file back into its original, unencoded format. - **abaqus fetch** extracts example input files from the libraries included with the release. - **abaqus findkeyword** provides a list of sample problems that use the specified Abaqus options. This utility will help users find examples of features they may be using for the first time. - **abaqus free** converts all fixed format data in an input file to free format. - **abaqus licensing** provides management and monitoring tools for FLEXnet and Dassault Systmes (DS) licensing. - **abaqus make** compiles and links user-written postprocessing programs for Abaqus and creates user-defined libraries of Abaqus/Standard and Abaqus/Explicit user subroutines. - **abaqus mtxasm** assembles element matrices contained in a SIM document and, optionally, writes the assembled matrices to text files. - **abaqus networkDBConnector** creates a connection to a network ODB server that can be used to access a remote output database. - **abaqus restartjoin** appends an output database file produced by a restart analysis of a model to the output database produced by the original analysis of that model. - **abaqus odbcombine** combines the results data in two or more Abaqus output database files into a single output database file. - **abaqus odbreport** creates organized reports of output database information in text, HTML, or CSV file formats. - **abaqus python** accesses the Python interpreter. - **abaqus resume** resumes an Abaqus analysis job. - **abaqus script** initiates a Python scripting session. - **abaqus sim_version** converts a SIM database file from one release to another, queries a SIM database file for its SIM release level, or determines the SIM release level of the current code you are using. - **abaqus substructurecombine** combines the model and results data produced by two of a model's substructures into a single output database file. - **abaqus suspend** suspends an Abaqus analysis job. - **abaqus terminate** terminates an Abaqus analysis job. - **abaqus upgrade** upgrades an input file or output database file from previous versions of Abaqus to the current version.

### Platform support

Analysis products (Abaqus/Standard, Abaqus/Explicit, and Abaqus/CFD) and interactive products (Abaqus/CAE and Abaqus/Viewer) are supported on the following platforms:
- Windows/x86-64
- Linux/x86-64

### Changes to documentation

Because the translation functionality in the Abaqus Interface for Moldflow has been integrated into Abaqus/Standard as the **abaqus moldflow** execution procedure, the Abaqus Interface for Moldflow User's Guide has been removed from the Abaqus documentation collection. For information about running the **abaqus moldflow** execution procedure, see ["Translating Moldflow data to Abaqus input files," Section 3.2.37](../usb/usb-link.md#usb-int-dmflabaproc) of the [Abaqus Analysis User's Guide](../usb/usb-link.md#usb). For translation examples, see ["Moldflow translation examples," Section 1.3.19](../exa/exa-link.md#exa-sta-moldflow) of the [Abaqus Example Problems Guide](../exa/exa-link.md#exa).




