# Introduction







This is the Benchmarks Guide for Abaqus. It contains benchmark problems (including the NAFEMS suite of test problems) and standard analyses used to evaluate the performance of Abaqus. The tests in this guide are multiple element tests of simple geometries or simplified versions of real problems.

In addition to the Benchmarks Guide there are two other guides that contain worked problems. The [Abaqus Example Problems Guide](../exa/exa-link.md#exa) contains many solved examples that test the code with the type of problems users are likely to solve. Many of these problems are quite difficult and test a combination of capabilities in the code. The [Abaqus Verification Guide](../ver/ver-link.md#ver) contains a large number of examples that are intended as elementary verification of the basic modeling capabilities in Abaqus.

The qualification process for new Abaqus releases includes running and verifying results for all problems in the [Abaqus Example Problems Guide](../exa/exa-link.md#exa), the [Abaqus Benchmarks Guide](book01.md), and the [Abaqus Verification Guide](../ver/ver-link.md#ver).

All input files referred to in the guides are included with the Abaqus release in compressed archive files. The **abaqus fetch** utility is used to extract these input files for use. For example, to fetch input file [barrelvault_s8r5_reg22.inp](../eif/barrelvault_s8r5_reg22.inp), type

```
abaqus fetch job=barrelvault_s8r5_reg22.inp
```
Parametric study script (`.psf`) and user subroutine (`.f`) files can be fetched in the same manner. All files for a particular problem can be obtained by leaving off the file extension. The **abaqus fetch** utility is explained in detail in ["Fetching sample input files," Section 3.2.16 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-int-dfetchproc).

It is sometimes useful to search the input files. The **findkeyword** utility is used to locate input files that contain user-specified input. This utility is defined in ["Querying the keyword/problem database," Section 3.2.15 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-int-dkeywordproc).



