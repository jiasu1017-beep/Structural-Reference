# 13.5 Parallel user subroutines







**Products: **Abaqus/Standard  Abaqus/Explicit  Abaqus/CFD  

**Benefits: **  Parallel user subroutines are supported in all parallel modes: thread-parallel and MPI-parallel.  

**Description: **Infrastructural and procedural changes have been put in place to support parallel execution of Abaqus User Subroutines.  

For threads, a number of parallel primitives has been exposed in Fortran that allow you to write safe multithreaded code in Fortran. These primitives have also been exposed in the C++, although this language has its own facilities for writing multithreaded code.  

For MPI, full native support has been enabled and provided for both Fortran and C++. All MPI calls are available from within Abaqus user subroutines.  

Special arrangement have been made to provide thread-shared and thread-local storage for users' needs.
**References: **

**Abaqus Analysis User's Guide**
- ["Parallel execution: overview," Section 3.5.1](../usb/usb-link.md#usb-int-aparallelmodes)

**Abaqus User Subroutines Reference Guide**
- ["Allocatable arrays," Section 2.1.23](../sub/sub-link.md#sub-utl-localarrays)




