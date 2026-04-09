# 附录B 在Abaqus/CAE中创建和分析简单模型

本附录介绍如何在Abaqus/CAE中创建一个简单的静态分析模型，包括建模、分析和后处理的基本流程。

---

## B.1 问题描述

创建一个悬臂梁模型：
- 长度：1.0 m
- 横截面：矩形 0.05m × 0.1m
- 材料：钢材（弹性模量 200 GPa，泊松比 0.3）
- 边界条件：左端固定
- 载荷：自由端施加 1000 N 垂直向下的集中力

---

## B.2 创建零件

### 步骤 1：启动 Abaqus/CAE

```
ABAQUS/CAE
```

### 步骤 2：创建新模型

1. 在开始页面选择 **Model Database**
2. 选择 **Standard** 分析产品
3. 点击 **OK** 创建新模型

### 步骤 3：创建几何零件

1. 在 **Model Tree** 中展开 **Parts** 节点
2. 右键点击 **Parts** 选择 **Create**
3. 在对话框中设置：
   - 名称：`Beam`
   - 建模空间：`2D Planar`
   - 类型：`Deformable body`
   - 近似尺寸：`2.0`
4. 点击 **Continue** 进入草图环境

### 步骤 4：绘制梁截面

1. 使用 **Rectangle** 工具绘制矩形
2. 点击第一点 `(0, 0)` 和第二点 `(1.0, 0.1)`
3. 添加尺寸标注
4. 点击 **Done** 完成草图

### 步骤 5：拉伸生成三维几何

1. 系统自动进入 **Part** 模块
2. 在 **Feature** 工具栏点击 **Extrude**
3. 设置拉伸深度：`0.05 m`
4. 点击 **OK** 生成零件

---

## B.3 创建材料

### 步骤 1：进入材料模块

在 **Module** 下拉菜单中选择 **Property**

### 步骤 2：定义材料

1. 在 **Material** 菜单中选择 **Create**
2. 名称输入：`Steel`
3. 在 **General** 目录下选择 **Elasticity** → **Elastic**
4. 输入参数：
   - 弹性模量：`200E9` Pa
   - 泊松比：`0.3`
5. 点击 **OK**

### 步骤 3：创建截面

1. 在 **Section** 菜单中选择 **Create**
2. 名称输入：`BeamSection`
3. 类别：`Beam`
4. 类型：`Box`
5. 点击 **Continue**
6. 输入几何参数：
   - a = 0.025 m（半宽）
   - b = 0.05 m（半高）
   - 壁厚 t = 0.005 m
7. 点击 **OK**

### 步骤 4：分配截面

1. 在 **Section** 菜单中选择 **Assign Section**
2. 选择整个梁零件
3. 点击 **OK** 应用截面

---

## B.4 创建装配件

### 步骤 1：进入装配模块

在 **Module** 下拉菜单中选择 **Assembly**

### 步骤 2：创建装配件

1. 在 **Instance** 菜单中选择 **Create**
2. 选择零件 `Beam`
3. 选择 `Dependent` 选项
4. 点击 **OK** 创建实例

---

## B.5 定义分析步骤

### 步骤 1：进入步骤模块

在 **Module** 下拉菜单中选择 **Step**

### 步骤 2：创建分析步骤

1. 在 **Step** 菜单中选择 **Create**
2. 名称输入：`ApplyLoad`
3. 程序类型：`Static General`
4. 点击 **Continue**
5. 在 **Basic** 选项卡中：
   - 描述：`Cantilever beam loading`
   - 时间周期：`1.0`
6. 点击 **OK**

---

## B.6 定义边界条件和载荷

### 步骤 1：进入加载模块

在 **Module** 下拉菜单中选择 **Load**

### 步骤 2：施加边界条件

1. 在 **BC** 菜单中选择 **Create**
2. 名称输入：`Fixed`
3. 步骤选择：`ApplyLoad`
4. 类别：`Mechanical`
5. 类型：`Displacement/Rotation`
6. 点击 **Continue**
7. 选择梁的左端面
8. 勾选 `U1 = U2 = U3 = UR1 = UR2 = UR3 = 0`
9. 点击 **OK**

### 步骤 3：施加载荷

1. 在 **Load** 菜单中选择 **Create**
2. 名称输入：`Force`
3. 步骤选择：`ApplyLoad`
4. 类别：`Mechanical`
5. 类型：`Concentrated Force`
6. 点击 **Continue**
7. 选择梁的自由端面
8. 输入 `CF2 = -1000`（负值表示向下）
9. 点击 **OK**

---

## B.7 网格划分

### 步骤 1：进入网格模块

在 **Module** 下拉菜单中选择 **Mesh**

### 步骤 2：设置网格参数

1. 在 **Mesh** 菜单中选择 **Controls**
2. 选择整个梁
3. 技术选择：`Structured`
4. 点击 **OK**

### 步骤 3：设置单元类型

1. 在 **Mesh** 菜单中选择 **Element Type**
2. 选择整个梁
3. 单元族：`B32`（二次梁单元）
4. 点击 **OK**

### 步骤 4：生成网格

在 **Mesh** 菜单中选择 **Seed & Part**
- 全局种子大小：`0.05`

在 **Mesh** 菜单中选择 **Mesh Part**
- 点击 **Yes** 确认

---

## B.8 创建和提交分析作业

### 步骤 1：进入作业模块

在 **Module** 下拉菜单中选择 **Job**

### 步骤 2：创建分析作业

1. 在 **Job** 菜单中选择 **Create**
2. 名称输入：`BeamAnalysis`
3. 模型选择：`Model-1`
4. 点击 **OK**

### 步骤 3：提交分析

1. 在 **Job** 菜单中选择 **Submit**
2. 系统开始分析，计算完成后显示 `Completed`
3. 点击 **OK**

---

## B.9 后处理

### 步骤 1：进入可视化模块

在 **Module** 下拉菜单中选择 **Visualization**

### 步骤 2：查看变形图

1. 在 **Result** 菜单中选择 **Plot Contours**
2. 系统显示梁的位移云图

### 步骤 3：查看应力结果

1. 在 **Result** 菜单中选择 **Field Output**
2. 选择 `Mises stress (S-Mises)`
3. 点击 **OK**

### 步骤 4：查询数值结果

1. 在 **Tools** 菜单中选择 **Query**
2. 选择 `Probe`
3. 选择要查询的节点或单元
4. 系统显示详细的数值结果

---

## B.10 本章小结

本附录演示了在Abaqus/CAE中创建简单静态分析模型的完整流程：

1. 创建几何零件
2. 定义材料和截面
3. 装配模型
4. 创建分析步骤
5. 施加边界条件和载荷
6. 网格划分
7. 提交分析作业
8. 后处理查看结果

这些基本操作是进行更复杂有限元分析的基础。

---

*本文档由ABAQUS Getting Started with Abaqus: Interactive Edition (6.14) 翻译生成*
