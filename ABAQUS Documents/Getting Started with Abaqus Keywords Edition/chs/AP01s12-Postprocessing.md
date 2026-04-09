# A.12 管道系统的振动

## pipe.inp

```inp
*HEADING
5米长管道在拉力作用下的分析
管道外径180mm，内径140mm
国际单位制
**
** 节点坐标
**
*NODE
1,0.
61, 5.0
*NGEN
1,61
**
** 单元连接
**
*ELEMENT, TYPE=PIPE32
1, 1, 2, 3
*ELGEN, ELSET=PIPE
1, 30,2,1
**
*NSET, NSET=LEFT
1,
*NSET, NSET=RIGHT
61,
**
** 物理特性和材料特性
**
*BEAM SECTION, ELSET=PIPE, MATERIAL=STEEL, SECTION=PIPE
0.09, 0.02
0.0, 0.0, -1.0
*MATERIAL, NAME=STEEL
*ELASTIC
200.E9, 0.3
*DENSITY
7800.,
**
** 步骤1 - 通用步骤
**
*STEP, NLGEOM=YES
施加4.0 MN轴向拉力
*STATIC
0.1, 1.0
*BOUNDARY
LEFT, 1, 6
RIGHT, 2, 6
*CLOAD
RIGHT, 1, 4.0E6
*ELSET, ELSET=ELEMENT25
25,
*RESTART, WRITE, FREQUENCY=10
*OUTPUT, FIELD, FREQUENCY=10, VARIABLE=PRESELECT
*OUTPUT, HISTORY
*ELEMENT OUTPUT, ELSET=ELEMENT25
S, SINV
**********************************
** ABAQUS QA输出用途
**********************************
*NODE FILE, FREQ=10
U,
*EL FILE, FREQ=10
SINV, S
*END STEP
**
** 步骤2 - 线性扰动步骤
**
*STEP, PERTURBATION
提取模态和频率
*FREQUENCY
8,
*RESTART, WRITE
*OUTPUT, FIELD, VARIABLE=PRESELECT
**********************************
** ABAQUS QA输出用途
**********************************
*MODAL FILE
*END STEP
```

## pipe_2.inp

```inp
*HEADING
增加管道系统的拉力
并确定最低频率
*RESTART, READ
**
** 步骤3 - 通用步骤
**
*STEP, NLGEOM=YES
施加8 MN轴向拉力
*STATIC
0.1, 1.
*CLOAD
RIGHT, 1, 8.0E6
*RESTART, WRITE, FREQUENCY=10
*OUTPUT, FIELD, FREQUENCY=10, VARIABLE=PRESELECT
*OUTPUT, HISTORY
*ELEMENT OUTPUT, ELSET=ELEMENT25
S, SINV
*END STEP
**
** 步骤4 - 线性扰动步骤
**
*STEP, PERTURBATION
提取模态和频率
*FREQUENCY
8,
*RESTART, WRITE
*OUTPUT, FIELD, VARIABLE=PRESELECT
**********************************
** ABAQUS QA输出用途
**********************************
*MODAL FILE
*END STEP
```
