# 3.7 Specifying the rate at which optimization data are saved







**Product: **Abaqus/CAE  

**Benefits: **You now have more flexibility when specifying the rate at which the optimization process saves the files created by the Abaqus jobs, such as the status file, the message file, and the output database. 

**Description: **With previous releases of Abaqus/CAE you could choose to save analysis data from the Abaqus job either every design cycle or from the first and last design cycles when creating an optimization process. You can now specify the rate at which optimization data are saved as follows:
- after every design cycle,
- from the initial, first, or last design cycles, or
- after every *n* design cycles.

**Abaqus/CAE Usage: **
```
Job module:
    ****Optimization**![](../graphics/images/arrow.gif)**Create****, **Name:** *optimization process name*, **Optimization:** **Data save** 
```

**Reference: **

**Abaqus/CAE User's Guide**
- ["Creating and editing optimization processes," Section 19.12.1](../usi/usi-link.md#usi-ana-optman-createbtn)




