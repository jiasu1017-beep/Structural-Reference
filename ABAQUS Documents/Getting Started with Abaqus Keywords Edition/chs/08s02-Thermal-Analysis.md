# 8.2 非线性问题的求解

结构的非线性荷载-位移曲线如图8-7所示。

![图8-7](https://www.example.com/../graphics/gss-nonlinear-nls.png)

图8-7 非线性荷载-位移曲线。

分析的目标是确定这种响应。考虑作用在物体上的外力 *P* 和内（节点）力 *I*（分别如图8-8(a)和图8-8(b)所示）。

![图8-8](https://www.example.com/../graphics/gss-loads-nls.png)

图8-8 物体上的内力和外力。

作用在节点上的内力是由包含该节点的单元中的应力引起的。

为了使物体处于静力平衡状态，作用于每个节点上的净力必须为零。因此，静力平衡的基本表述是：内力 *I* 和外力 *P* 必须相互平衡：

![方程](https://www.example.com/../graphics/gsk_eqn00124.gif)

Abaqus/Standard 使用牛顿-拉弗森（Newton-Raphson）方法来获得非线性问题的求解。在非线性分析中，通常不能像线性问题那样通过求解单个方程组来计算解。相反，求解是通过逐渐和增量地施加指定荷载并趋向最终解来实现的。因此，Abaqus/Standard 将模拟分解为若干**荷载增量**，并在每个荷载增量结束时找到近似的平衡构型。Abaqus/Standard 通常需要多次迭代才能确定给定荷载增量可接受的解。所有增量响应的总和就是非线性分析的近似解。因此，Abaqus/Standard 结合了增量法和迭代法来求解非线性问题。

Abaqus/Explicit 通过显式地从上一个增量结束时的运动状态前进，来确定动力平衡方程 ![方程](https://www.example.com/../graphics/gsk_eqn00125.gif) 的解，而不需要迭代。显式求解不需要形成切线刚度矩阵。显式中心差分算子在增量开始时 *t* 满足动力平衡方程；在时间 *t* 计算的加速度用于将速度解推进到时间 ![方程](https://www.example.com/../graphics/gsk_eqn00126.gif)，并将位移解推进到时间 ![方程](https://www.example.com/../graphics/gsk_eqn00127.gif)。对于线性和非线性问题，显式方法都需要一个小的时间增量，其大小仅取决于模型的最高固有频率，而与荷载的类型和持续时间无关。模拟通常需要大量增量；然而，由于在每个增量中不需要求解全局方程组，显式方法的每增量成本比隐式方法要小得多。显式动态方法的小增量特征使 Abaqus/Explicit 非常适合非线性分析。

## 8.2.1 步骤、增量和迭代

本节介绍一些用于描述分析各部分的新术语。重要的是，您必须清楚理解分析**步骤**、荷载**增量**和**迭代**之间的区别。

- 模拟的荷载历史由一个或多个步骤组成。您定义步骤，通常包括分析过程选项、荷载选项和输出请求选项。不同的荷载、边界条件、分析过程选项和输出请求可以用于每个步骤。例如：

  - 步骤1：将板夹在刚性夹爪之间。
  - 步骤2：施加荷载使板变形。
  - 步骤3：找出变形板的固有频率。

- 增量是步骤的一部分。在非线性分析中，施加在步骤中的总荷载被分解成更小的增量，以便跟踪非线性求解路径。

  在 Abaqus/Standard 中，您建议第一个增量的大小，然后 Abaqus/Standard 自动选择后续增量的大小。在 Abaqus/Explicit 中，默认的时间步长控制是全自动的，不需要用户干预。由于显式方法是有条件稳定的，因此存在一个时间增量的稳定极限。稳定时间增量在第9章"非线性显式动力学"中讨论。

  在每个增量结束时，结构处于（近似）平衡状态，结果可以写入输出数据库、重启动文件、数据文件或结果文件。您选择将结果写入输出数据库文件的增量称为**帧**。

  Abaqus/Standard 和 Abaqus/Explicit 分析中与时间增量相关的问题完全不同，因为时间增量在 Abaqus/Explicit 中通常要小得多。

- 迭代是使用隐式方法求解增量时尝试寻找平衡解的过程。如果模型在迭代结束时未处于平衡状态，Abaqus/Standard 会尝试另一次迭代。随着每次迭代，Abaqus/Standard 获得的解应该更接近平衡；有时 Abaqus/Standard 可能需要多次迭代才能获得平衡解。当获得平衡解时，增量就完成了。结果只能在增量结束时请求。

  Abaqus/Explicit 不需要在增量中迭代来获得解。

## 8.2.2 Abaqus/Standard 中的平衡迭代和收敛

结构对一个小荷载增量 ![方程](https://www.example.com/../graphics/gsk_eqn00128.gif) 的非线性响应如图8-9所示。Abaqus/Standard 使用结构在 ![方程](https://www.example.com/../graphics/gsk_eqn00130.gif) 构型下的初始刚度 ![方程](https://www.example.com/../graphics/gsk_eqn00129.gif) 和 ![方程](https://www.example.com/../graphics/gsk_eqn00128.gif) 来计算结构的**位移修正值** ![方程](https://www.example.com/../graphics/gsk_eqn00131.gif)。使用 ![方程](https://www.example.com/../graphics/gsk_eqn00131.gif)，将结构的构型更新为 ![方程](https://www.example.com/../graphics/gsk_eqn00132.gif)。

![图8-9](https://www.example.com/../graphics/gss-first-iteration-nls.png)

图8-9 增量中的第一次迭代。

**收敛**

Abaqus/Standard 根据更新后的构型 ![方程](https://www.example.com/../graphics/gsk_eqn00132.gif) 为结构形成新的刚度 ![方程](https://www.example.com/../graphics/gsk_eqn00133.gif)。Abaqus/Standard 还在此更新构型中计算 ![方程](https://www.example.com/../graphics/gsk_eqn00134.gif)。现在可以计算出总施加荷载 *P* 与 ![方程](https://www.example.com/../graphics/gsk_eqn00134.gif) 之间的差值：

![方程](https://www.example.com/../graphics/gsk_eqn00135.gif)

其中 ![方程](https://www.example.com/../graphics/gsk_eqn00136.gif) 是迭代的**力残差**。

如果模型中每个自由度上的 ![方程](https://www.example.com/../graphics/gsk_eqn00136.gif) 为零，则图8-9中的点 *a* 将位于荷载-挠度曲线上，并且结构处于平衡状态。在非线性问题中，![方程](https://www.example.com/../graphics/gsk_eqn00136.gif) 等于零几乎是不可能的，因此 Abaqus/Standard 会将其与容差值进行比较。如果 ![方程](https://www.example.com/../graphics/gsk_eqn00136.gif) 小于此力残差容差，Abaqus/Standard 将接受结构的更新构型作为平衡解。默认情况下，此容差值设置为结构中平均力的0.5%，并在整个模拟过程中对时间进行平均。Abaqus/Standard 自动在整个模拟过程中计算此空间和时间平均力。

如果 ![方程](https://www.example.com/../graphics/gsk_eqn00136.gif) 小于当前容差值，则 *P* 和 ![方程](https://www.example.com/../graphics/gsk_eqn00134.gif) 处于平衡状态，并且 ![方程](https://www.example.com/../graphics/gsk_eqn00132.gif) 是结构在施加荷载下的有效平衡构型。但是，在 Abaqus/Standard 接受解之前，它还会检查位移修正值 ![方程](https://www.example.com/../graphics/gsk_eqn00131.gif) 是否相对于总增量位移 ![方程](https://www.example.com/../graphics/gsk_eqn00137.gif) 很小。如果 ![方程](https://www.example.com/../graphics/gsk_eqn00131.gif) 大于增量位移的1%，则 Abaqus/Standard 执行另一次迭代。在荷载增量的解被称为**收敛**之前，必须满足两个收敛检查。此规则的例外情况是**线性**增量的情况，线性增量定义为最大力残差小于时间平均力10⁻⁸倍的任何增量。任何通过如此严格的力残差与时间平均力比较的 case 都被认为是线性的，不需要进一步迭代。解被接受，无需对位移修正值的大小进行任何检查。

如果某次迭代的解不收敛，Abaqus/Standard 执行另一次迭代，尝试使内力和外力达到平衡。这第二次迭代使用在上一次迭代结束时计算的刚度 ![方程](https://www.example.com/../graphics/gsk_eqn00133.gif) 以及 ![方程](https://www.example.com/../graphics/gsk_eqn00136.gif) 来确定另一次使系统更接近平衡的位移修正值 ![方程](https://www.example.com/../graphics/gsk_eqn00138.gif)（图8-10中的点 *b*）。

![图8-10](https://www.example.com/../graphics/gss-second-iteration-nls.png)

图8-10 第二次迭代。

Abaqus/Standard 使用结构新构型 ![方程](https://www.example.com/../graphics/gsk_eqn00140.gif) 中的内力计算新的力残差 ![方程](https://www.example.com/../graphics/gsk_eqn00139.gif)。同样，任意自由度上最大力残差 ![方程](https://www.example.com/../graphics/gsk_eqn00139.gif) 与力残差容差进行比较，并且第二次迭代的位移修正值 ![方程](https://www.example.com/../graphics/gsk_eqn00138.gif) 与位移增量 ![方程](https://www.example.com/../graphics/gsk_eqn00141.gif) 进行比较。如果需要，Abaqus/Standard 执行进一步迭代。

对于非线性分析中的每次迭代，Abaqus/Standard 形成模型的刚度矩阵并求解方程组。这意味着每次迭代的计算成本相当于进行完整的线性分析。现在应该清楚了，Abaqus/Standard 中非线性分析的计算费用可能是线性分析的多倍。

使用 Abaqus/Standard 可以在每个收敛增量处保存结果。因此，非线性模拟可用的输出数据量可能是相同几何形状线性分析可用数据量的许多倍。在规划计算机资源时，请同时考虑这两个因素以及您想要执行的非线性模拟类型。

## 8.2.3 Abaqus/Standard 中的自动增量控制

Abaqus/Standard 自动调整荷载增量的大小，以便轻松高效地求解非线性问题。您只需要建议模拟中每个步骤的第一个增量的大小。此后，Abaqus/Standard 自动调整增量的大小。如果您未提供建议的初始增量大小，Abaqus/Standard 将尝试在第一个增量中施加步骤中定义的所有荷载。在高度非线性问题中，Abaqus/Standard 将不得不反复减小增量大小，从而浪费 CPU 时间。通常，为您提供合理的初始增量大小是有利的（参见8.4.1节"对输入文件的修改——历史数据"中的示例）；只有在非常轻微的非线性问题中，才能在单个增量中施加步骤中的所有荷载。

寻找荷载增量收敛解所需的迭代次数将根据系统的非线性程度而变化。默认情况下，如果解似乎发散，Abaqus/Standard 会放弃该增量，并将增量大小设置为其上一个值的25%重新开始。然后尝试用这个较小的荷载增量寻找收敛解。如果增量仍然无法收敛，Abaqus/Standard 再次减小增量大小。默认情况下，Abaqus/Standard 允许在停止分析之前每个增量最多五次减小增量大小。

在 Abaqus/Standard 中，您还可以添加 **INC** 参数来指定步骤期间允许的最大增量数。如果需要超过此限制的增量来完成步骤，Abaqus/Standard 将终止分析并显示错误消息。步骤的默认增量数为100；如果模拟中存在显著非线性，分析可能需要更多增量。**INC** 参数指定 Abaqus/Standard 可以使用的增量上限，而不是它必须使用的增量数。例如，涉及最多150个增量的几何非线性步骤应指定为：

```abaqus
*STEP, NLGEOM=YES, INC=150
```

在非线性分析中，步骤发生在有限的"时间"内，尽管这个"时间"在没有惯性效应或率相关行为的情况下没有物理意义。在 Abaqus/Standard 中，您需要在步骤中使用的过程选项的数据行上指定初始时间增量 ![方程](https://www.example.com/../graphics/gsk_eqn00142.gif) 和总步骤时间 ![方程](https://www.example.com/../graphics/gsk_eqn00143.gif)。例如，

![方程](https://www.example.com/../graphics/gss-c7-tot-step-input-nls.png)

定义了一个在1.0个时间单位内发生的静态分析，初始增量为0.1。初始时间增量与步骤时间的比值指定了在第一个增量中施加荷载的比例。初始荷载增量由下式给出：

![方程](https://www.example.com/../graphics/gsk_eqn00144.gif)

初始时间增量的选择在某些 Abaqus/Standard 非线性模拟中可能至关重要，但对于大多数分析，初始增量大小为总步骤时间的5%至10%通常就足够了。在静态模拟中，总步骤时间通常方便地设置为1.0，除非，例如，模型中包含率相关材料效应或阻尼器。当总步骤时间为1.0时，施加荷载的比例始终等于当前步骤时间；即，当步骤时间为0.5时，施加总荷载的50%。

尽管您必须在 Abaqus/Standard 中指定初始增量大小，但 Abaqus/Standard 自动控制后续增量的大小。这种增量大小的自动控制适用于使用 Abaqus/Standard 执行的大多数非线性模拟，尽管还有其他可用的增量大小控制。如果由于收敛问题导致的过度减小将增量大小降低到最小值以下，Abaqus/Standard 将终止分析。默认允许的最小时间增量 ![方程](https://www.example.com/../graphics/gsk_eqn00145.gif) 是总步骤时间的10⁻⁵倍。默认情况下，Abaqus/Standard 对增量大小 ![方程](https://www.example.com/../graphics/gsk_eqn00146.gif) 没有上限，除了总步骤时间。根据您的 Abaqus/Standard 模拟，您可能需要指定不同的最小和/或最大允许增量大小。例如，如果您知道如果施加过大的荷载增量，模拟可能无法获得解（可能是因为模型可能发生塑性变形），您可能希望减小 ![方程](https://www.example.com/../graphics/gsk_eqn00146.gif)。

如果增量在少于五次迭代中收敛，这表明解相当容易找到。因此，如果连续两个增量需要少于五次迭代来获得收敛解，Abaqus/Standard 自动将增量大小增加50%。

自动荷载增量方案的详细信息在消息文件中给出，详见8.4.3节"结果"。
