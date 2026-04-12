# 60.1 Material 对象







Material 对象是用于指定材料的对象。Material 对象存储决定材料行为方式的各种设置。

材料通过组合一个或多个单独的材料选项和子选项来创建。特定材料选项通过成员与 Material 对象关联。例如：*acousticMedium* 成员可能包含 AcousticMedium 对象。拒绝采用 MaterialOption 抽象基类和 MaterialOptions 容器的替代方案是因为它会使执行以下事实变得更加困难：一个 Material 对象不能包含两个 AcousticMedium 对象（例如）。

**访问**

```
materialApi.materials()[*name*]
```

### 60.1.1 Material(...)

此方法创建 Material 对象。

**路径**

```
materialApi.Material
```

**原型**

```
odb_Material&
Material(const odb_String& name,
         const odb_String& description,
         const odb_String& materialIdentifier);
```

**必需参数**

*name*

一个 odb_String，指定新材料的名称。

**可选参数**

*description*

一个 odb_String，指定材料用户描述。默认值为空字符串。

*materialIdentifier*

一个 odb_String，指定供客户使用的材料标识符。默认值为空字符串。

**返回值**

Material 对象。

**异常**

InvalidNameError。

### 60.1.2 成员

Material 对象具有与 [Material](pt02ch60pyo01.md#ker-material-material-cpp) 方法的参数具有相同名称和描述的成员。

此外，Material 对象可以具有以下成员：

**原型**

```
odb_AcousticMedium acousticMedium() const;
odb_BrittleCracking brittleCracking() const;
odb_CapPlasticity capPlasticity() const;
odb_CastIronPlasticity castIronPlasticity() const;
odb_ClayPlasticity clayPlasticity() const;
odb_Concrete concrete() const;
odb_ConcreteDamagedPlasticity concreteDamagedPlasticity() const;
odb_Conductivity conductivity() const;
odb_Creep creep() const;
odb_CrushableFoam crushableFoam() const;
odb_DamageInitiation ductileDamageInitiation() const;
odb_DamageInitiation fldDamageInitiation() const;
odb_DamageInitiation flsdDamageInitiation() const;
odb_DamageInitiation johnsonCookDamageInitiation() const;
odb_DamageInitiation maxeDamageInitiation() const;
odb_DamageInitiation maxsDamageInitiation() const;
odb_DamageInitiation maxpeDamageInitiation() const;
odb_DamageInitiation maxpsDamageInitiation() const;
odb_DamageInitiation mkDamageInitiation() const;
odb_DamageInitiation msfldDamageInitiation() const;
odb_DamageInitiation quadeDamageInitiation() const;
odb_DamageInitiation quadsDamageInitiation() const;
odb_DamageInitiation shearDamageInitiation() const;
odb_DamageInitiation hashinDamageInitiation() const;
odb_Damping damping() const;
odb_DeformationPlasticity deformationPlasticity() const;
odb_Density density() const;
odb_Depvar depvar() const;
odb_Dielectric dielectric() const;
odb_Diffusivity diffusivity() const;
odb_DruckerPrager druckerPrager() const;
odb_Elastic elastic() const;
odb_ElectricalConductivity electricalConductivity() const;
odb_Eos eos() const;
odb_Expansion expansion() const;
odb_FluidLeakoff fluidLeakoff() const;
odb_GapFlow gapFlow() const;
odb_GasketThicknessBehavior gasketThicknessBehavior() const;
odb_GasketTransverseShearElastic gasketTransverseShearElastic() const;
odb_GasketMembraneElastic gasketMembraneElastic() const;
odb_Gel gel() const;
odb_HeatGeneration heatGeneration() const;
odb_Hyperelastic hyperelastic() const;
odb_Hyperfoam hyperfoam() const;
odb_Hypoelastic hypoelastic() const;
odb_InelasticHeatFraction inelasticHeatFraction() const;
odb_JouleHeatFraction jouleHeatFraction() const;
odb_LatentHeat latentHeat() const;
odb_LowDensityFoam lowDensityFoam() const;
odb_MagneticPermeability magneticPermeability() const;
odb_MohrCoulombPlasticity mohrCoulombPlasticity() const;
odb_MoistureSwelling moistureSwelling() const;
odb_MullinsEffect mullinsEffect() const;
odb_Permeability permeability() const;
odb_Piezoelectric piezoelectric() const;
odb_Plastic plastic() const;
odb_PoreFluidExpansion poreFluidExpansion() const;
odb_PorousBulkModuli porousBulkModuli() const;
odb_PorousElastic porousElastic() const;
odb_PorousMetalPlasticity porousMetalPlasticity() const;
odb_Regularization regularization() const;
odb_Solubility solubility() const;
odb_Sorption sorption() const;
odb_SpecificHeat specificHeat() const;
odb_Swelling swelling() const;
odb_UserDefinedField userDefinedField() const;
odb_UserMaterial userMaterial() const;
odb_UserOutputVariables userOutputVariables() const;
odb_Viscoelastic viscoelastic() const;
odb_Viscosity viscosity() const;
odb_Viscous viscous() const;
```

*acousticMedium*

一个 [AcousticMedium](pt02ch60pyo02.md) 对象。

*brittleCracking*

一个 [BrittleCracking](pt02ch60pyo05.md) 对象。

*capPlasticity*

一个 [CapPlasticity](pt02ch60pyo11.md) 对象。

*castIronPlasticity*

一个 [CastIronPlasticity](pt02ch60pyo13.md) 对象。

*clayPlasticity*

一个 [ClayPlasticity](pt02ch60pyo16.md) 对象。

*concrete*

一个 [Concrete](pt02ch60pyo18.md) 对象。

*concreteDamagedPlasticity*

一个 [ConcreteDamagedPlasticity](pt02ch60pyo21.md) 对象。

*conductivity*

一个 [Conductivity](pt02ch60pyo24.md) 对象。

*creep*

一个 [Creep](pt02ch60pyo26.md) 对象。

*crushableFoam*

一个 [CrushableFoam](pt02ch60pyo27.md) 对象。

*ductileDamageInitiation*

一个 [DamageInitiation](pt02ch60pyo32.md) 对象。

*fldDamageInitiation*

一个 [DamageInitiation](pt02ch60pyo32.md) 对象。

*flsdDamageInitiation*

一个 [DamageInitiation](pt02ch60pyo32.md) 对象。

*johnsonCookDamageInitiation*

一个 [DamageInitiation](pt02ch60pyo32.md) 对象。

*maxeDamageInitiation*

一个 [DamageInitiation](pt02ch60pyo32.md) 对象。

*maxsDamageInitiation*

一个 [DamageInitiation](pt02ch60pyo32.md) 对象。

*maxpeDamageInitiation*

一个 [DamageInitiation](pt02ch60pyo32.md) 对象。

*maxpsDamageInitiation*

一个 [DamageInitiation](pt02ch60pyo32.md) 对象。

*mkDamageInitiation*

一个 [DamageInitiation](pt02ch60pyo32.md) 对象。

*msfldDamageInitiation*

一个 [DamageInitiation](pt02ch60pyo32.md) 对象。

*quadeDamageInitiation*

一个 [DamageInitiation](pt02ch60pyo32.md) 对象。

*quadsDamageInitiation*

一个 [DamageInitiation](pt02ch60pyo32.md) 对象。

*shearDamageInitiation*

一个 [DamageInitiation](pt02ch60pyo32.md) 对象。

*hashinDamageInitiation*

一个 [DamageInitiation](pt02ch60pyo32.md) 对象。

*damping*

一个 [Damping](pt02ch60pyo35.md) 对象。

*deformationPlasticity*

一个 [DeformationPlasticity](pt02ch60pyo36.md) 对象。

*density*

一个 [Density](pt02ch60pyo37.md) 对象。

*depvar*

一个 [Depvar](pt02ch60pyo38.md) 对象。

*dielectric*

一个 [Dielectric](pt02ch60pyo40.md) 对象。

*diffusivity*

一个 [Diffusivity](pt02ch60pyo41.md) 对象。

*druckerPrager*

一个 [DruckerPrager](pt02ch60pyo42.md) 对象。

*elastic*

一个 [Elastic](pt02ch60pyo45.md) 对象。

*electricalConductivity*

一个 [ElectricalConductivity](pt02ch60pyo46.md) 对象。

*eos*

一个 [Eos](pt02ch60pyo47.md) 对象。

*expansion*

一个 [Expansion](pt02ch60pyo49.md) 对象。

*fluidLeakoff*

一个 [FluidLeakoff](pt02ch60pyo53.md) 对象。

*gapFlow*

一个 [GapFlow](pt02ch60pyo54.md) 对象。

*gasketThicknessBehavior*

一个 [GasketThicknessBehavior](pt02ch60pyo56.md) 对象。

*gasketTransverseShearElastic*

一个 [GasketTransverseShearElastic](pt02ch60pyo57.md) 对象。

*gasketMembraneElastic*

一个 [GasketMembraneElastic](pt02ch60pyo55.md) 对象。

*gel*

一个 [Gel](pt02ch60pyo58.md) 对象。

*heatGeneration*

一个 [HeatGeneration](pt02ch60pyo59.md) 对象。

*hyperelastic*

一个 [Hyperelastic](pt02ch60pyo60.md) 对象。

*hyperfoam*

一个 [Hyperfoam](pt02ch60pyo61.md) 对象。

*hypoelastic*

一个 [Hypoelastic](pt02ch60pyo62.md) 对象。

*inelasticHeatFraction*

一个 [InelasticHeatFraction](pt02ch60pyo64.md) 对象。

*jouleHeatFraction*

一个 [JouleHeatFraction](pt02ch60pyo65.md) 对象。

*latentHeat*

一个 [LatentHeat](pt02ch60pyo66.md) 对象。

*lowDensityFoam*

一个 [LowDensityFoam](pt02ch60pyo67.md) 对象。

*magneticPermeability*

一个 [MagneticPermeability](pt02ch60pyo68.md) 对象。

*mohrCoulombPlasticity*

一个 [MohrCoulombPlasticity](pt02ch60pyo70.md) 对象。

*moistureSwelling*

一个 [MoistureSwelling](pt02ch60pyo71.md) 对象。

*mullinsEffect*

一个 [MullinsEffect](pt02ch60pyo72.md) 对象。

*permeability*

一个 [Permeability](pt02ch60pyo74.md) 对象。

*piezoelectric*

一个 [Piezoelectric](pt02ch60pyo75.md) 对象。

*plastic*

一个 [Plastic](pt02ch60pyo77.md) 对象。

*poreFluidExpansion*

一个 [PoreFluidExpansion](pt02ch60pyo78.md) 对象。

*porousBulkModuli*

一个 [PorousBulkModuli](pt02ch60pyo79.md) 对象。

*porousElastic*

一个 [PorousElastic](pt02ch60pyo80.md) 对象。

*porousMetalPlasticity*

一个 [PorousMetalPlasticity](pt02ch60pyo82.md) 对象。

*regularization*

一个 [Regularization](pt02ch60pyo87.md) 对象。

*solubility*

一个 [Solubility](pt02ch60pyo92.md) 对象。

*sorption*

一个 [Sorption](pt02ch60pyo94.md) 对象。

*specificHeat*

一个 [SpecificHeat](pt02ch60pyo95.md) 对象。

*swelling*

一个 [Swelling](pt02ch60pyo96.md) 对象。

*userDefinedField*

一个 [UserDefinedField](pt02ch60pyo102.md) 对象。

*userMaterial*

一个 [UserMaterial](pt02ch60pyo103.md) 对象。

*userOutputVariables*

一个 [UserOutputVariables](pt02ch60pyo104.md) 对象。

*viscoelastic*

一个 [Viscoelastic](pt02ch60pyo106.md) 对象。

*viscosity*

一个 [Viscosity](pt02ch60pyo107.md) 对象。

*viscous*

一个 [Viscous](pt02ch60pyo108.md) 对象。

### 60.1.3 对应的分析关键字

| [*MATERIAL*](../key/key-link.md#usb-kws-mmaterial) |
| --- |

