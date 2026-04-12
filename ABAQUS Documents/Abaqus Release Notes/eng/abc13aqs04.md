# 13.4 Allocatable arrays







**Products: **Abaqus/Standard  Abaqus/Explicit  Abaqus/CFD  

**Benefits: **To facilitate data accumulation and transfer between user subroutines, Abaqus provides utility functions for users to create and manage their own dynamic storage in the form of allocatable arrays.  

**Description: **Two kinds of arrays are supported: global and thread-local.  

Global arrays are visible and accessible from all threads in an executable. To prevent race conditions, write access to these arrays from multiple threads must be protected by mutexes. Using mutexes on every access will incur a performance penalty. In some situations it is possible to avoid this by restricting all threads to operate on non-intersecting ranges of a global array. Another alternative is to use thread-local arrays.    

Thread-local arrays are local to a thread. Each thread holds its own private copy of an array. They are deliberately not shared, and, thus, do not need to be locked or protected from competing threads. In fact, one thread cannot cross-reference a local array of another thread. However, all user subroutines running in one thread can access all arrays of that thread. Without the need for locking, thread-local arrays can be accessed concurrently and, thus, are faster than global arrays.  

These arrays are meant as a thread-safe replacement for common blocks. You can create any number of global or thread local arrays, in either Fortran or C++. At the time of creation, you assign an integer ID to each. Later, in other user subroutines, you can reference these arrays simply by their IDs and use them as native C++ or Fortran arrays. 
**Reference: **

**Abaqus User Subroutines Reference Guide**
- ["Allocatable arrays," Section 2.1.23](../sub/sub-link.md#sub-utl-localarrays)




