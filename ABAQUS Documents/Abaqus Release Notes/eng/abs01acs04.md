# 15.4 Changes in Abaqus output variable identifiers







This section summarizes the changes and the additions that have been made to output variable identifiers used in Abaqus.

| #### Element integration point variables: |
| --- |
| **new** | **(S)(E)** | MMIXDME |
|  |  | Mode mix ratio during damage evolution. |
| **new** | **(S)(E)** | MMIXDMI |
|  |  | Mode mix ratio at damage initiation. |
| **new** | **(E)** | PEEQR |
|  |  | Equivalent plastic strain rate. |
| #### Whole element variables: |
| **new** | **(S)** | ALEAKVRBXFEM |
|  |  | Accumulated leak-off flow volume at the bottom cracked surface of the enriched element. |
| **new** | **(S)** | ALEAKVRTXFEM |
|  |  | Accumulated leak-off flow volume at the top cracked surface of the enriched element. |
| **new** | **(S)** | GFVRXFEM |
|  |  | Gap fluid volume rate of the enriched element. |
| **new** | **(S)** | LEAKVRBXFEM |
|  |  | Leak-off flow rate at the bottom cracked surface of the enriched element. |
| **new** | **(S)** | LEAKVRTXFEM |
|  |  | Leak-off flow rate at the top cracked surface of the enriched element. |
| **new** | **(S)** | PFOPENXFEM |
|  |  | Fracture opening of the enriched element. |
| **new** | **(S)** | PORPRES |
|  |  | Fluid pressure of the enriched element. |
| #### Nodal variables: |
| **new** | **(E)** | AMAG |
|  |  | Magnitude of translational accelerations. |
| **new** | **(S)** | CLINELOAD |
|  |  | Contact load due to line contact from edge-to-surface and radial edge-to-edge constraints in units of force per length. The normal (CLINELOADN) and frictional shear (CLINELOADT) components are available only for general contact to the `.odb` file. |
| **new** | **(S)** | CPOINTLOAD |
|  |  | Contact load in units of force due to point contact from edge-to-edge constraints using the cross formulation. The normal (CPOINTLOADN) and frictional shear (CPOINTLOADT) components are available only for general contact to the `.odb` file. |
| **new** | **(E)** | RFMAG |
|  |  | Magnitude of reaction forces. |
| **new** | **(E)** | UMAG |
|  |  | Magnitude of translational displacements. |
| **new** | **(E)** | VMAG |
|  |  | Magnitude of translational velocities. |
| #### Surface variables-nodal quantities: |
| **new** | **(S)** | CRKDISP |
|  |  | Crack opening and relative tangential motions on cracked surfaces in enriched elements. |
| **mod** | **(S)** | CSDMG |
|  |  | Damage variable for cracked surfaces in enriched elements. |
| #### Total energy output quantities: |
| **new** | **(S)** | ALLCCDW |
|  |  | Contact constraint discontinuity work. |
| **new** | **(S)** | ALLCCE |
|  |  | The sum of ALLCCEN and ALLCCET. |
| **new** | **(S)** | ALLCCEN |
|  |  | Contact constraint elastic energy in normal direction due to penalty constraint enforcement. |
| **new** | **(S)** | ALLCCET |
|  |  | Contact constraint elastic energy in tangential direction due to friction penalty constraint enforcement. |
| **new** | **(S)** | ALLCCSD |
|  |  | The sum of ALLCCSDN and ALLCCSDT. |
| **new** | **(S)** | ALLCCSDN |
|  |  | Contact constraint stabilization dissipation in normal direction. |
| **new** | **(S)** | ALLCCSDT |
|  |  | Contact constraint stabilization dissipation in tangential direction. |
| #### State and field variables: |
| **rem** | **(C)** | ENSTROPHY |
|  |  | Enstrophy per unit mass. |
| **rem** | **(C)** | HELICITY |
|  |  | Dot product of vorticity and velocity. |
| **new** | **(C)** | QCRIT |
|  |  | Coherent structure visualizator, known as Qcriteria. |
| #### Turbulence variables: |
| **new** | **(C)** | TURBOMEGA |
|  |  | Specific turbulent energy dissipation rate. |
| **new** | **(C)** | TURBVISCOSITYRATIO |
|  |  | Eddy to molecular viscosity ratio. |




