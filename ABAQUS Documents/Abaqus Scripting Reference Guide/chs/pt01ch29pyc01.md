# 29.1 Material 对象





Material 对象是用于指定材料的对象。Material 对象存储决定材料行为的各种设置。

材料通过组合一个或多个单独的 材料选项和子选项来创建。特定的材料选项通过成员与 Material 对象关联。例如：*acousticMedium* 成员可能包含一个 AcousticMedium 对象。没有选择使用 MaterialOption 抽象基类和 MaterialOptions 容器的替代方案，因为这会使执行一个 Material 对象不能包含两个 AcousticMedium 对象的规则变得更加困难。

**访问**

```
import material
mdb.models[*name*].materials[*name*]
import odbMaterial
session.odbs[*name*].materials[*name*]
```

### 29.1.1 Material(...)

此方法创建 Material 对象。

**路径**

```
mdb.models[*name*].Material
session.odbs[*name*].Material
```

**必需参数**

*name*

一个 String，指定新材料的名称。

**可选参数**

*description*

一个 String，指定材料的用户描述。默认值为空字符串。

*materialIdentifier*

一个 String，指定客户使用的材料标识符。默认值为空字符串。

**返回值**

一个 Material 对象。

**异常**

InvalidNameError。

### 29.1.2 materialsFromOdb(...)

此方法通过读取输出数据库创建 Material 对象。新材料被放入 `materials` 存储库中。

**路径**

```
mdb.models[*name*].materialsFromOdb
```

**必需参数**

*fileName*

一个 String，指定要读取的输出数据库文件的名称（包括 `.odb` 扩展名）。如果输出数据库文件位于另一个目录中，此 String 也可以是输出数据库文件的完整路径。

**可选参数**

无。

**返回值**

一个 Material 对象列表。

**异常**

无。

### 29.1.3 成员

Material 对象具有与 [Material](pt01ch29pyo01.md#ker-material-material-pyc) 方法参数同名的成员，描述也相同。

此外，Material 对象可以具有以下成员：

*acousticMedium*

一个 [AcousticMedium](pt01ch29pyo02.md) 对象。

*brittleCracking*

一个 [BrittleCracking](pt01ch29pyo05.md) 对象。

*capPlasticity*

一个 [CapPlasticity](pt01ch29pyo11.md) 对象。

*castIronPlasticity*

一个 [CastIronPlasticity](pt01ch29pyo13.md) 对象。

*clayPlasticity*

一个 [ClayPlasticity](pt01ch29pyo16.md) 对象。

*concrete*

一个 [Concrete](pt01ch29pyo18.md) 对象。

*concreteDamagedPlasticity*

一个 [ConcreteDamagedPlasticity](pt01ch29pyo21.md) 对象。

*conductivity*

一个 [Conductivity](pt01ch29pyo24.md) 对象。

*creep*

一个 [Creep](pt01ch29pyo26.md) 对象。

*crushableFoam*

一个 [CrushableFoam](pt01ch29pyo27.md) 对象。

*ductileDamageInitiation*

一个 [DamageInitiation](pt01ch29pyo32.md) 对象。

*fldDamageInitiation*

一个 [DamageInitiation](pt01ch29pyo32.md) 对象。

*flsdDamageInitiation*

一个 [DamageInitiation](pt01ch29pyo32.md) 对象。

*johnsonCookDamageInitiation*

一个 [DamageInitiation](pt01ch29pyo32.md) 对象。

*maxeDamageInitiation*

一个 [DamageInitiation](pt01ch29pyo32.md) 对象。

*maxsDamageInitiation*

一个 [DamageInitiation](pt01ch29pyo32.md) 对象。

*maxpeDamageInitiation*

一个 [DamageInitiation](pt01ch29pyo32.md) 对象。

*maxpsDamageInitiation*

一个 [DamageInitiation](pt01ch29pyo32.md) 对象。

*mkDamageInitiation*

一个 [DamageInitiation](pt01ch29pyo32.md) 对象。

*msfldDamageInitiation*

一个 [DamageInitiation](pt01ch29pyo32.md) 对象。

*quadeDamageInitiation*

一个 [DamageInitiation](pt01ch29pyo32.md) 对象。

*quadsDamageInitiation*

一个 [DamageInitiation](pt01ch29pyo32.md) 对象。

*shearDamageInitiation*

一个 [DamageInitiation](pt01ch29pyo32.md) 对象。

*hashinDamageInitiation*

一个 [DamageInitiation](pt01ch29pyo32.md) 对象。

*damping*

一个 [Damping](pt01ch29pyo35.md) 对象。

*deformationPlasticity*

一个 [DeformationPlasticity](pt01ch29pyo36.md) 对象。

*density*

一个 [Density](pt01ch29pyo37.md) 对象。

*depvar*

一个 [Depvar](pt01ch29pyo38.md) 对象。

*dielectric*

一个 [Dielectric](pt01ch29pyo40.md) 对象。

*diffusivity*

一个 [Diffusivity](pt01ch29pyo41.md) 对象。

*druckerPrager*

一个 [DruckerPrager](pt01ch29pyo42.md) 对象。

*elastic*

一个 [Elastic](pt01ch29pyo45.md) 对象。

*electricalConductivity*

一个 [ElectricalConductivity](pt01ch29pyo46.md) 对象。

*eos*

一个 [Eos](pt01ch29pyo47.md) 对象。

*expansion*

一个 [Expansion](pt01ch29pyo49.md) 对象。

*fluidLeakoff*

一个 [FluidLeakoff](pt01ch29pyo53.md) 对象。

*gapFlow*

一个 [GapFlow](pt01ch29pyo54.md) 对象。

*gasketThicknessBehavior*

一个 [GasketThicknessBehavior](pt01ch29pyo56.md) 对象。

*gasketTransverseShearElastic*

一个 [GasketTransverseShearElastic](pt01ch29pyo57.md) 对象。

*gasketMembraneElastic*

一个 [GasketMembraneElastic](pt01ch29pyo55.md) 对象。

*gel*

一个 [Gel](pt01ch29pyo58.md) 对象。

*heatGeneration*

一个 [HeatGeneration](pt01ch29pyo59.md) 对象。

*hyperelastic*

一个 [Hyperelastic](pt01ch29pyo60.md) 对象。

*hyperfoam*

一个 [Hyperfoam](pt01ch29pyo61.md) 对象。

*hypoelastic*

一个 [Hypoelastic](pt01ch29pyo62.md) 对象。

*inelasticHeatFraction*

一个 [InelasticHeatFraction](pt01ch29pyo64.md) 对象。

*jouleHeatFraction*

一个 [JouleHeatFraction](pt01ch29pyo65.md) 对象。

*latentHeat*

一个 [LatentHeat](pt01ch29pyo66.md) 对象。

*lowDensityFoam*

一个 [LowDensityFoam](pt01ch29pyo67.md) 对象。

*magneticPermeability*

一个 [MagneticPermeability](pt01ch29pyo68.md) 对象。

*mohrCoulombPlasticity*

一个 [MohrCoulombPlasticity](pt01ch29pyo70.md) 对象。

*moistureSwelling*

一个 [MoistureSwelling](pt01ch29pyo71.md) 对象。

*mullinsEffect*

一个 [MullinsEffect](pt01ch29pyo72.md) 对象。

*permeability*

一个 [Permeability](pt01ch29pyo74.md) 对象。

*piezoelectric*

一个 [Piezoelectric](pt01ch29pyo75.md) 对象。

*plastic*

一个 [Plastic](pt01ch29pyo77.md) 对象。

*poreFluidExpansion*

一个 [PoreFluidExpansion](pt01ch29pyo78.md) 对象。

*porousBulkModuli*

一个 [PorousBulkModuli](pt01ch29pyo79.md) 对象。

*porousElastic*

一个 [PorousElastic](pt01ch29pyo80.md) 对象。

*porousMetalPlasticity*

一个 [PorousMetalPlasticity](pt01ch29pyo82.md) 对象。

*regularization*

一个 [Regularization](pt01ch29pyo87.md) 对象。

*solubility*

一个 [Solubility](pt01ch29pyo92.md) 对象。

*sorption*

一个 [Sorption](pt01ch29pyo94.md) 对象。

*specificHeat*

一个 [SpecificHeat](pt01ch29pyo95.md) 对象。

*swelling*

一个 [Swelling](pt01ch29pyo96.md) 对象。

*userDefinedField*

一个 [UserDefinedField](pt01ch29pyo102.md) 对象。

*userMaterial*

一个 [UserMaterial](pt01ch29pyo103.md) 对象。

*userOutputVariables*

一个 [UserOutputVariables](pt01ch29pyo104.md) 对象。

*viscoelastic*

一个 [Viscoelastic](pt01ch29pyo106.md) 对象。

*viscosity*

一个 [Viscosity](pt01ch29pyo107.md) 对象。

*viscous*

一个 [Viscous](pt01ch29pyo108.md) 对象。

### 29.1.4 对应的分析关键字

| [*MATERIAL](../key/key-link.md#usb-kws-mmaterial) |
| --- |




