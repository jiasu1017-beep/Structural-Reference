# 12.3 Output of last converged increment







**Product: **Abaqus/Standard  

**Benefits: **If a general step in an Abaqus/Standard analysis fails to converge, the results from the last converged increment are written to the output database. This can be helpful in diagnosing why convergence failed.

**Description: **The default output behavior has been modified to output the last converged increment when convergence is not achieved. The output is written only if there are convergence difficulties beyond the first increment. This default behavior is available for all general steps in Abaqus/Standard.
**Reference: **

**Abaqus Analysis User's Guide**
- ["Output to the output database," Section 4.1.3](../usb/usb-link.md#usb-out-odboutput)




