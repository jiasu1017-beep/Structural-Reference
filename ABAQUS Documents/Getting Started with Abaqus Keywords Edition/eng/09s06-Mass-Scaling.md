# 9.6 Energy balance

Energy output is often an important part of an Abaqus/Explicit analysis. Comparisons between various energy components can be used to help evaluate whether an analysis is yielding an appropriate response.

## 9.6.1 Statement of energy balance

An energy balance for the entire model can be written as

![](../graphics/gsk_eqn00217.gif)

where ![](../graphics/gsk_eqn00218.gif) is the internal energy, ![](../graphics/gsk_eqn00219.gif) is the viscous energy dissipated, ![](../graphics/gsk_eqn00220.gif) is the frictional energy dissipated, ![](../graphics/gsk_eqn00221.gif) is the kinetic energy, ![](../graphics/gsk_eqn00222.gif) is the internal heat energy, ![](../graphics/gsk_eqn00223.gif) is the work done by the externally applied loads, and ![](../graphics/gsk_eqn00224.gif), ![](../graphics/gsk_eqn00225.gif), and ![](../graphics/gsk_eqn00226.gif) are the work done by contact penalties, by constraint penalties, and by propelling added mass, respectively. ![](../graphics/gsk_eqn00227.gif) is the external heat energy through external fluxes. The sum of these energy components is ![](../graphics/gsk_eqn00228.gif), which should be constant. In the numerical model ![](../graphics/gsk_eqn00228.gif) is only approximately constant, generally with an error of less than 1%.

**Internal energy**

The internal energy is the sum of the recoverable elastic strain energy, ![](../graphics/gsk_eqn00229.gif); the energy dissipated through inelastic processes such as plasticity, ![](../graphics/gsk_eqn00230.gif); the energy dissipated through viscoelasticity or creep, ![](../graphics/gsk_eqn00231.gif); the artificial strain energy, ![](../graphics/gsk_eqn00232.gif); the energy dissipated through damage, ![](../graphics/gsk_eqn00233.gif); the energy dissipated through distortion control, ![](../graphics/gsk_eqn00234.gif); and the fluid cavity energy, ![](../graphics/gsk_eqn00235.gif):

![](../graphics/gsk_eqn00236.gif)

The artificial strain energy includes energy stored in hourglass resistances and transverse shear in shell and beam elements. Large values of artificial strain energy indicate that mesh refinement or other changes to the mesh are necessary.

**Viscous energy**

The viscous energy is the energy dissipated by damping mechanisms, including bulk viscosity damping and material damping. A fundamental variable in the global energy balance, viscous energy is not part of the energy dissipated through viscoelasticity or inelastic processes.

**External work of applied forces**

The external work is integrated forward continuously, defined entirely by nodal forces (moments) and displacements (rotations). Prescribed boundary conditions also contribute to the external work.

## 9.6.2 Output of the energy balance

Each of the energy quantities can be requested as output and can be plotted as time histories summed over the entire model, particular element sets, individual elements, or as energy density within each element. The variable names associated with the energy quantities summed over the entire model or element sets are as listed in Table 9-2.

**Table 9-2** Whole model energy output variables.

| Variable Name | Energy Quantity |
|---------------|-----------------|
| ALLIE | Internal energy, ![](../graphics/gsk_eqn00218.gif): ALLIE = ALLSE + ALLPD + ALLCD + ALLAE + ALLDMD + ALLDC + ALLFC. |
| ALLKE | Kinetic energy, ![](../graphics/gsk_eqn00221.gif). |
| ALLVD | Viscous dissipated energy, ![](../graphics/gsk_eqn00219.gif). |
| ALLFD | Frictional dissipated energy, ![](../graphics/gsk_eqn00220.gif). |
| ALLCD | Energy dissipated by viscoelasticity, ![](../graphics/gsk_eqn00231.gif). |
| ALLWK | Work of the external forces, ![](../graphics/gsk_eqn00223.gif). |
| ALLPW | Work done by contact penalties, ![](../graphics/gsk_eqn00224.gif). |
| ALLCW | Work done by constraint penalties, ![](../graphics/gsk_eqn00225.gif). |
| ALLMW | Work done by propelling added mass (due to mass scaling), ![](../graphics/gsk_eqn00226.gif). |
| ALLSE | Elastic strain energy, ![](../graphics/gsk_eqn00229.gif). |
| ALLPD | Inelastic dissipated energy, ![](../graphics/gsk_eqn00230.gif). |
| ALLAE | Artificial strain energy, ![](../graphics/gsk_eqn00232.gif). |
| ALLIHE | Internal heat energy, ![](../graphics/gsk_eqn00222.gif). |
| ALLHF | External heat energy through external fluxes, ![](../graphics/gsk_eqn00237.gif). |
| ALLDMD | Energy dissipated by damage, ![](../graphics/gsk_eqn00233.gif). |
| ALLDC | Energy dissipated by distortion control, ![](../graphics/gsk_eqn00234.gif). |
| ALLFC | Fluid cavity energy (negative of work done by fluid cavities), ![](../graphics/gsk_eqn00235.gif). |
| ETOTAL | Energy balance: ![](../graphics/gsk_eqn00238.gif) ![](../graphics/gsk_eqn00239.gif). |

In addition, Abaqus/Explicit can produce element-level energy output and energy density output, as listed in Table 9-3.

**Table 9-3** Whole element energy output variables.

| Variable Name | Whole Element Energy Quantity |
|---------------|-------------------------------|
| ELSE | Elastic strain energy. |
| ELPD | Plastic dissipated energy. |
| ELCD | Creep dissipated energy. |
| ELVD | Viscous dissipated energy. |
| ELASE | Artificial energy = drill energy + hourglass energy. |
| EKEDEN | Kinetic energy density in the element. |
| ESEDEN | Elastic strain energy density in the element. |
| EPDDEN | Plastic energy density dissipated in the element. |
| EASEDEN | Artificial strain energy density in the element. |
| ECDDEN | Creep strain energy density dissipated in the element. |
| EVDDEN | Viscous energy density dissipated in the element. |
| ELDMD | Energy dissipated in the element by damage. |
