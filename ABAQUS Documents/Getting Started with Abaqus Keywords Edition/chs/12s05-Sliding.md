# 12.5 Abaqus/Standard中刚性曲面建模问题

在Abaqus/Standard中涉及刚性曲面的接触问题建模时，有许多需要考虑的问题。这些问题在《Abaqus Analysis User's Guide》第39.1.2节"与Abaqus/Standard中接触建模相关的常见困难"中有详细讨论，但这里仅描述其中一些更重要的问题。

- 刚性曲面在接触相互作用中始终作为主曲面。
- 刚性曲面应该足够大，以确保从属节点不会滑落并"落在"曲面后面。如果发生这种情况，求解通常将无法收敛。扩展刚性曲面或在周边包括尖角（见图12-10）将防止从属节点落在主曲面后面。

**图12-10** 扩展刚性曲面以防止收敛问题。

![../graphics/gss-rigidsurf-nls.png](../graphics/gss-rigidsurf-nls.png)

- 变形网格必须足够精细，以便与刚性曲面上的任何特征相互作用。如果将与它接触的变形单元的尺寸是20mm宽，而刚性曲面上却有10mm宽的特征，这是没有意义的：刚性特征将只是穿透变形曲面，如图12-11所示。

**图12-11** 刚性曲面上小特征的建模。

![../graphics/gss-modelrigidsurf-nls.png](../graphics/gss-modelrigidsurf-nls.png)

使用足够精细的变形曲面网格，Abaqus/Standard将防止刚性曲面穿透从属曲面。

- Abaqus/Standard中的接触算法要求接触相互作用的主曲面必须是光滑的。刚性曲面始终是主曲面，因此应该始终被光滑处理。Abaqus/Standard不会光滑离散的刚性曲面。离散刚性曲面的光滑程度由网格细化程度控制。解析刚性曲面可以通过定义倒角半径来光滑处理，该半径用于光滑刚性曲面定义中的任何尖角（见图12-12）。

**图12-12** 光滑解析刚性曲面。

![../graphics/gss-smoothingsurf-nls.png](../graphics/gss-smoothingsurf-nls.png)

- 刚性曲面法线必须始终指向与其相互作用的变形曲面。如果不这样做，Abaqus/Standard将检测到变形曲面上所有节点的严重过盈接触；模拟可能会因收敛困难而终止。

解析刚性曲面的法线定义为从形成曲面的每条线和圆弧段的起点到终点的向量逆时针旋转90°得到的方向（见图12-13）。

**图12-13** 解析刚性曲面的法线。

![../graphics/gss-normals-analrigsurf-nls.png](../graphics/gss-normals-analrigsurf-nls.png)

由刚性单元创建的刚性曲面的法线由创建曲面时指定的面定义。
