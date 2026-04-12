# 3.8 Writing optimization files







**Product: **Abaqus/CAE  

**Benefits: **You now create the files that are needed to run the optimization with an Abaqus execution procedure from the command line.

**Description: **When you are managing an optimization process, you can create copies of the optimization parameter (`.par`) file and the Abaqus input (`.inp`) file in your working directory. The parameter file contains parameters that are used to execute the optimization and contains information about the input file that is associated with the optimization; the input file, in turn, defines the Abaqus model you are optimizing. 

You can run the optimization from the command line with the following command: 

```
abaqus optimization -task *parameter file* -job *results folder*
```
The parameter file and the input file must be saved in the same directory. During the optimization, Abaqus creates the results folder in which the results of the optimization are stored.

**Abaqus/CAE Usage: **
```
Job module:
    ****Optimization**![](../graphics/images/arrow.gif)**Write Files****; **Name:** *optimization process name* 
```

**Reference: **

**Abaqus/CAE User's Guide**
- ["Creating the optimization files," Section 19.12.2](../usi/usi-link.md#usi-ana-optman-writefilesbtn)




