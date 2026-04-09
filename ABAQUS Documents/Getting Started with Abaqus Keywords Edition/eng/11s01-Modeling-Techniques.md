# 11.1 General analysis procedures

The starting point for each general step is the deformed state at the end of the last general step. Therefore, the state of the model evolves in a sequence of general steps as it responds to the loads defined in each step. Any initial conditions define the starting point for the first general step in the simulation.

All general analysis procedures share the same concepts for applying loads and defining "time."

## 11.1.1 Time in general analysis steps

Abaqus has two measures of time in a simulation. The *total time* increases throughout all general steps and is the accumulation of the total step time from each general step. Each step also has its own time scale (known as the *step time*), which begins at zero for each step. Time varying loads and boundary conditions can be specified in terms of either time scale. The time scales for an analysis whose history is divided into three steps, each 100 seconds long, are shown in [Figure 11-1](#gss-total-time).

**Figure 11-1** Step and total time for a simulation.

![Step and total time for a simulation](../graphics/gss-total-time-nls.png)

## 11.1.2 Specifying loads in general steps

In general steps the loads must be specified as total values, not incremental values. For example, if a concentrated load has a value of 1000 N in the first step and it is increased to 3000 N in the second general step, the magnitude given for the load in the two steps should be 1000 N and 3000 N, not 1000 N and 2000 N.

By default, all previously defined loads are propagated to the current step. In the current step you can define additional loads as well as modify any previously defined load (for example, change its magnitude or deactivate it). Any previously defined load that is not specifically modified in the current step continues to follow its associated amplitude definition, provided that the amplitude curve is defined in terms of total time; otherwise, the load is maintained at the magnitude it had at the end of the last general step.
