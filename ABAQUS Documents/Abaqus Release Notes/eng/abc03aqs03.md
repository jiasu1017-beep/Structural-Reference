# 3.3 Viewing the progression of an optimization by combining output database files







**Product: **Abaqus/CAE  

**Benefits: **Each design cycle of an optimization process now creates a separate output database file. To view the results of the optimization in the Visualization module, you must combine the separate output database files with the optimization results into a single output database file.

**Description: ** Previous releases of Abaqus/CAE stored the analysis results from each design cycle into a single output database file, resulting in very large output database files that consumed a lot of disk space and were slow to process. By default, Abaqus/CAE continues to save optimization data after every design cycle in optimization files. However, the individual output database files created during each design cycle are now saved only at specified intervals. Alternatively, you can control the rate at which analysis data is saved in output database files as follows:
- after every design cycle,
- from the initial, first, or last design cycles, or
- after every *n* design cycles.

To view the results of an optimization in the Visualization module, you must first combine the separate output database files and the optimization files into a single output database file. When you merge output database files, you can select the steps and load cases to merge; you can also select the field variables to include in the combined output database file. In addition, if your optimization process included multiple models, you can select the models to include; Abaqus/CAE creates a combined output database file for each model.

**Abaqus/CAE Usage: **
```
Job module:
    ****Optimization**![](../graphics/images/arrow.gif)**Combine****, **Name:** *design response name*
```

**Reference: **

**Abaqus/CAE User's Guide**
- ["Combining optimization results," Section 19.12.8](../usi/usi-link.md#usi-ana-optman-combinebtn)




