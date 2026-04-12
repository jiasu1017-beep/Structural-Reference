# 11.4 Job execution control enhancements







**Products: **Abaqus/Standard  Abaqus/Explicit  Abaqus/CFD  

**Benefits: **You can now control job execution remotely; previously, you were required to execute job control commands on the machine running the analysis. In addition, two new command line options are available for network connections.

**Description: **The execution procedures for job execution control include **abaqus suspend**, **abaqus resume**, and **abaqus terminate**. These utilities are used to suspend, resume, and terminate Abaqus analysis jobs. You can now execute these commands remotely; you are not required to execute these commands on the machine running the analysis.

The **host** and **port** options are used to specify the host name and port number, respectively, for the connection running the analysis job. You can specify either the **job** option or the **host** and **port** options to suspend, resume, or terminate Abaqus analysis jobs.
**Reference: **

**Abaqus Analysis User's Guide**
- ["Job execution control," Section 3.2.39](../usb/usb-link.md#usb-int-dsuspend)




