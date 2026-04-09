# 7.8 与直接时间积分的比较

由于这是瞬态动力学分析，自然要考虑结果与使用运动方程直接积分获得的结果进行比较。直接积分可以使用隐式（Abaqus/Standard）或显式（Abaqus/Explicit）方法进行。在此我们将分析扩展为使用显式动力学过程。

与前面给出的结果进行直接比较是不可能的，因为B33单元类型和直接模态阻尼在Abaqus/Explicit中不可用。因此，在Abaqus/Explicit分析中，单元类型改为B31，并用瑞利阻尼替代直接模态阻尼。

将 `dynamics.inp` 另存为 `dynamics_xpl.inp`。后续所有更改都应针对 `dynamics_xpl.inp` 进行。

**修改模型：**

1. 将模型中所有单元的单元类型改为B31。可以通过修改 `*ELEMENT` 选项上的 `TYPE` 参数来进行此更改：
   ```doc
   *ELEMENT, TYPE=B31
   ```

2. 在支撑截面属性中添加质量 proportional 阻尼。为此，请在支撑截面的材料数据选项块末尾添加 `*DAMPING` 选项：
   ```doc
   *DAMPING, ALPHA=15.
   ```
   此语句指定alpha阻尼值为15，其余阻尼量为0。

   这些值在结构低频和高频的临界阻尼值之间产生了合理的折衷。对于三个最低固有频率，<img height="17" width="8" src="../graphics/gsk_eqn00116.gif"> 的有效值大于0.05，但如图7-10所示，前两个模态对响应的贡献不大。对于其余模态，<img height="17" width="8" src="../graphics/gsk_eqn00116.gif"> 的值小于0.05。<img height="17" width="8" src="../graphics/gsk_eqn00116.gif"> 随固有频率的变化如图7-12所示。

   **图7-12** 阻尼对结果的影响。

   ![图7-12 阻尼对结果的影响](../graphics/gsa-dyncrane-damping-nls.png)

3. 对主构件截面属性重复上一步。

4. 删除两个分析步骤。

5. 创建单个显式动力学步骤，并指定时间周期为 0.5 s。此外，编辑步骤以使用线性几何，将 `*STEP` 选项上的 `NLGEOM`=NO 进行设置（这将导致线性分析）。对于您的仿真，定义显式动力学步骤的选项块应类似于以下内容：
   ```doc
   *STEP, NLGEOM=NO
   Direct integration transient dynamic analysis
   *DYNAMIC, EXPLICIT
   , 0.5
   *BULK VISCOSITY
   0.06, 1.2
   ```

6. 重新定义尖端载荷。

   此仿真的 `*CLOAD` 选项块为：
   ```doc
   *CLOAD, AMPLITUDE=BOUNCE
   104, 2, -1.0E4
   ```

7. 重新定义节点集 `TIP` 以仅包含节点104。

   创建默认场输出请求和两个历史输出请求。在第一个请求中，请求集合 `TIP` 的位移历史；在第二个请求中，请求集合 `ATTACH` 的反力历史。

   对于您的仿真，定义输出请求的选项块应类似于以下内容：
   ```doc
   *NSET, NSET=TIP
   104,
   *OUTPUT, FIELD, VARIABLE=PRESELECT
   *OUTPUT, HISTORY, VARIABLE=PRESELECT
   *NODE OUTPUT, NSET=TIP
   U,
   *NODE OUTPUT, NSET=ATTACH
   RF,
   ```

   使用以下命令终止步骤：
   ```doc
   *END STEP
   ```

8. 将输入文件另存为 `dynamics_xpl.inp` 并提交分析：
   ```doc
   abaqus job=dynamics_xpl.inp
   ```

作业完成后，导航到包含输出数据库文件 `dynamics_xpl.odb` 的目录，并在操作系统提示符下键入命令：
```doc
abaqus viewer odb=dynamics_xpl
```
在Abaqus/Viewer中检查结果。特别要将之前从Abaqus/Standard获得的尖端位移历史与从Abaqus/Explicit获得的结果进行比较。如图7-13所示，响应存在微小差异。这些差异是由于模态动力学分析使用了不同的单元类型和阻尼类型造成的。事实上，如果修改Abaqus/Standard分析以使用B31单元和质量proportional阻尼，则两种分析产品产生的结果几乎无法区分（见图7-13），这证实了模态动力学过程的准确性。

**图7-13** Abaqus/Standard与Abaqus/Explicit获得的尖端位移比较。

![图7-13 Abaqus/Standard与Abaqus/Explicit获得的尖端位移比较](../graphics/gsa-dyncrane-compare-nls.png)
