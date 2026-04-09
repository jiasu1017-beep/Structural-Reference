# 1.1.1 Introduction: general

### 1.1.1 Introduction: general

The Abaqus finite element system includes:

Abaqus/Standard, a general-purpose finite element program;

Abaqus/Explicit, an explicit dynamics finite element program;

Abaqus/CAE, an interactive environment used to create finite element models, submit Abaqus analyses, monitor and diagnose jobs, and evaluate results; and

Abaqus/Viewer, a subset of Abaqus/CAE that contains only the postprocessing capabilities of the `Visualization` module.Several add-on options that are available only if your license includes them can be used to further extend the capabilities of Abaqus/Standard and Abaqus/Explicit.

The Abaqus/Aqua option works with Abaqus/Standard and Abaqus/Explicit. Abaqus/Aqua contains optional features that are specifically designed for the analysis of beam-like structures installed underwater and subject to loading by water currents and wave action.

The Abaqus/Design option enables you to perform design sensitivity analysis (DSA). The Abaqus/Design option works with Abaqus/Standard.

Abaqus/AMS is an optional eigensolver that works within Abaqus/Standard providing very fast solution of large symmetric eigenvalue problems.

The Abaqus co-simulation technique provides two applications, available as separate add-on capabilities, for coupling between Abaqus and third-party analysis programs.

Abaqus/Foundation is an optional subset of Abaqus/Standard that provides more cost-efficient access to the linear static and dynamic analysis functionality in Abaqus/Standard.

This guide describes the theories used in Abaqus. Many sections in this guide apply to both Abaqus/Standard and Abaqus/Explicit. Certain sections obviously apply only to either Abaqus/Standard or Abaqus/Explicit; for example, all sections in the chapter on procedures apply to Abaqus/Standard, except the section discussing the explicit dynamic integration procedure, which applies to Abaqus/Explicit. If it is not obvious to which program a section applies, it is clearly indicated.

The objective of this guide is to define the theories used in Abaqus that are generally not available in the standard textbooks on mechanics, structures, and finite elements but are well known to the engineer who uses Abaqus. The guide is intended as a reference document that defines what is available in the code. Nevertheless, it is written in such a way that it can also be used as a tutorial document by a reader who needs to obtain some background in an unfamiliar area. The material is presented in a way that should make it accessible to any user with an engineering background. Some of the theories may be relatively unfamiliar to such a user; for example, few engineering curricula provide extensive background in plasticity, shell theory, finite deformations of solids, or the analysis of porous media. Yet Abaqus contains capabilities for all of these models and many others. The guide is far from comprehensive in its coverage of such topics: in this sense it is only a reference volume. The user is strongly encouraged to pursue topics of interest through texts and papers. Chapter 7, "References," at the end of this guide lists references that should provide a starting point for obtaining such information. (Abaqus does not supply copies of papers that have appeared in publications other than those of Abaqus. EPRI reports can be obtained from Research Reports Center (RRC), Box 50490, Palo Alto, CA 94303.)

Chapter 1, "Introduction and Basic Equations," discusses the notation used in the guide, some basic concepts of kinematics and mechanics---such as rotations, stress, and equilibrium---as well as the basic equations of nonlinear finite element analysis. Chapter 2, "Procedures," describes the various analysis procedures (nonlinear static stress analysis, dynamics, eigenvalue extraction, etc.) that are available in Abaqus. Chapter 3, "Elements," describes the element formulations. Chapter 4, "Mechanical Constitutive Theories," describes the mechanical constitutive theories.

Chapter 5, "Interface Modeling," discusses the most important aspects of the contact/interaction formulation in Abaqus/Standard. Chapter 6, "Loading and Constraints," describes the formulation of some of the more complicated load types and multi-point constraints.