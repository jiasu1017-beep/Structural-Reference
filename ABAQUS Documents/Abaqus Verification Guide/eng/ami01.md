# Introduction







This is the Verification Guide for Abaqus. It contains a large number of test cases that serve as basic verification of these programs. Each test case verifies one or several well-defined options in the code. The test cases are sufficiently small that, in most cases, the correct results can be calculated by hand.

This guide is divided into chapters based on the type of capability that is tested. The problems in the element verification chapter test the element library extensively. Other chapters document tests of materials, procedures, user subroutines, miscellaneous options, and importing results from Abaqus/Explicit into Abaqus/Standard.

In addition to the [Abaqus Verification Guide](book01.md), there are two other guides that contain worked problems. The [Abaqus Benchmarks Guide](../bmk/bmk-link.md#bmk) contains benchmark problems (including the NAFEMS suite of test problems) and standard analyses used to evaluate the performance of Abaqus. The tests in this guide are multiple element tests of simple geometries or simplified versions of real problems. The [Abaqus Example Problems Guide](../exa/exa-link.md#exa) contains many solved examples that test the code with the type of problems that users are likely to solve. Many of these problems are quite difficult and test a combination of capabilities in the code.

The qualification process for new Abaqus releases includes running and verifying results for all problems in the [Abaqus Example Problems Guide](../exa/exa-link.md#exa), the [Abaqus Benchmarks Guide](../bmk/bmk-link.md#bmk), and the Abaqus Verification Guide.

It is important that a user become familiar with the [Abaqus Benchmarks Guide](../bmk/bmk-link.md#bmk), the [Abaqus Example Problems Guide](../exa/exa-link.md#exa), and the Abaqus Verification Guide before any analysis is done to determine the level of verification that has been done of the capabilities that will be used. The user should then decide whether any additional verification is necessary before starting the analysis.

All input files referred to in the guides are included with the Abaqus release in compressed archive files. The **abaqus fetch** utility is used to extract these input files for use. For example, to fetch input file [ec12afe1.inp](../eif/ec12afe1.inp) for ["Eigenvalue extraction for single unconstrained elements," Section 1.2.1](ch01s02abv01.md), type

```
abaqus fetch job=ec12afe1.inp
```

Parametric study script (`.psf`) and user subroutine (`.f`) files can be fetched in the same manner. All files for a particular problem can be obtained by leaving off the file extension. The **abaqus fetch** utility is explained in detail in ["Fetching sample input files," Section 3.2.16 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-int-dfetchproc).

It is sometimes useful to search the input files. The **findkeyword** utility is used to locate input files that contain user-specified input. This utility is defined in ["Querying the keyword/problem database," Section 3.2.15 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-int-dkeywordproc).



