# Introduction







This is the Example Problems Guide for Abaqus. It contains many solved examples that illustrate the use of the program for common types of problems. Some of the problems are quite difficult and require combinations of the capabilities in the code.

The problems have been chosen to serve two purposes: to verify the capabilities in Abaqus by exercising the code on nontrivial cases and to provide guidance to users who must work on a class of problems with which they are relatively unfamiliar. In each worked example the discussion in the guide states why the example is included and leads the reader through the standard approach to an analysis: element and mesh selection, material model, and a discussion of the results. Many of these problems are worked with different element types, mesh densities, and other variations.

Input data files for all of the analyses are included with the Abaqus release in compressed archive files. The **abaqus fetch** utility is used to extract these input files for use. For example, to fetch input file [boltpipeflange_3d_cyclsym.inp](../eif/boltpipeflange_3d_cyclsym.inp), type

```
abaqus fetch job=boltpipeflange_3d_cyclsym.inp
```

Parametric study script (`.psf`) and user subroutine (`.f`) files can be fetched in the same manner. All files for a particular problem can be obtained by leaving off the file extension. The **abaqus fetch** utility is explained in detail in ["Fetching sample input files," Section 3.2.16 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-int-dfetchproc).

It is sometimes useful to search the input files. The **findkeyword** utility is used to locate input files that contain user-specified input. This utility is defined in ["Querying the keyword/problem database," Section 3.2.15 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-int-dkeywordproc).

To reproduce the graphical representation of the solution reported in some of the examples, the output frequency used in the input files may need to be increased. For example, in ["Linear analysis of the Indian Point reactor feedwater line," Section 2.2.2](ch02s02aex81.md), the figures that appear in the guide can be obtained only if the solution is written to the results file every increment; that is, if the input files are changed to read 

```
*NODE FILE, ..., FREQUENCY=1
```

instead of `FREQUENCY=100` as appears now.

In addition to the Abaqus Example Problems Guide, there are two other guides that contain worked problems. The [Abaqus Benchmarks Guide](../bmk/bmk-link.md#bmk) contains benchmark problems (including the NAFEMS suite of test problems) and standard analyses used to evaluate the performance of Abaqus. The tests in this guide are multiple element tests of simple geometries or simplified versions of real problems. The [Abaqus Verification Guide](../ver/ver-link.md#ver) contains a large number of examples that are intended as elementary verification of the basic modeling capabilities.

The qualification process for new Abaqus releases includes running and verifying results for all problems in the [Abaqus Example Problems Guide](book01.md), the [Abaqus Benchmarks Guide](../bmk/bmk-link.md#bmk), and the [Abaqus Verification Guide](../ver/ver-link.md#ver).



