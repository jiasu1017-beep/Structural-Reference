# 5.3 SIMULIA Co-Simulation Engine API availability







**Products: **Abaqus/Standard  Abaqus/Explicit  Abaqus/CFD  

**Benefits: **The SIMULIA Co-Simulation Engine API, which allows you to couple in-house codes with Abaqus solvers, is now generally available with the Abaqus media.

**Description: **The SIMULIA Co-Simulation Engine (CSE) API allows you to couple in-house codes with Abaqus solvers. Co-simulation and embedding the CSE API in client code are intended for advanced users who are familiar with Abaqus, their in-house software, the co-simulation technique, and programming. You are encouraged to discuss your co-simulation requirements with your SIMULIA local support office.

The CSE API kit is distributed with the Abaqus media. When you install Abaqus, the CSE API kit is installed in the following location:

```
*install_dir*/api/cse/6.14-*x*_*platform*_CSE-api.zip
```
For example, if you install Abaqus 6.14 in `C:\SIMULIA\Abaqus\6.14–1`, the CSE API kit for the Windows 64-bit platform is available in the following location:
```
C:\SIMULIA\Abaqus\6.14–1\api\cse\6.14-1_win86_64_CSE-api.zip
```
The `.zip` file contains the CSE API headers, libraries, documentation, and example problems.**References: **

**Abaqus Analysis User's Guide**
- [Chapter 17, "Co-simulation](../usb/usb-link.md#usbcosim)"

**Abaqus Installation and Licensing Guide**
- ["The Abaqus parent directory," Section B.2](../sgb/sgb-link.md#sgb-chp-directories-abaqus)




