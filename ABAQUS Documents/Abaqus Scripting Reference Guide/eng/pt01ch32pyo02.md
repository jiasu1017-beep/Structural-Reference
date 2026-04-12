# 32.2 MonitorMgr object







An instance of the MonitorMgr object is created when you import the abaqus module. No other instance of the MonitorMgr object is required. (This MonitorMgr object is not to be confused with the degree of freedom (DOF) monitor that is constructed from the [Step](pt01ch49pyo01.md) object.)

**Access**

```
monitorManager
```

### 32.2.1 addMessageCallback(...)

This method specifies a callback function that will be called when the specified message is received from the analysis product.

For more information, see ["An example of a callback function," Section 6.8.3 of the Abaqus Scripting User's Guide](../cmd/cmd-link.md#cmd-int-acl-callback).

**Required arguments**

*jobName*

A String specifying the name of the job to be monitored or the SymbolicConstant ANY_JOB.

*messageType*

A SymbolicConstant specifying which message type will call this callback. Possible values are:
- ABORTED
- ANY_JOB
- ANY_MESSAGE_TYPE
- COMPLETED
- END_STEP
- ERROR
- HEADING
- HEALER_JOB
- HEALER_TYPE
- INTERRUPTED
- ITERATION
- JOB_ABORTED
- JOB_COMPLETED
- JOB_INTERRUPTED
- JOB_SUBMITTED
- MONITOR_DATA
- ODB_FILE
- ODB_FRAME
- SIMULATION_ABORTED
- SIMULATION_COMPLETED
- SIMULATION_INTERRUPTED
- SIMULATION_SUBMITTED
- STARTED
- STATUS
- STEP
- WARNING

*callback*

A Python function to be called. The interface definition of the callback function is :

```
def onMessage(*jobName*, *messageType*, *data*, *userData*)
```

- *jobName* is a String.
- *messageType* is a SymbolicConstant with possible values as listed previously for the `addMessageCallback` method.
- *data* is a [DataObject](pt01ch32pyo01.md) object.
- *userData* is the object passed as the *userData* argument to the `addMessageCallback` method.

**Optional argument**

*userData*

Any Python object or `None`. This object is passed to the callback function.

**Return value**

None

**Exceptions**

None.

### 32.2.2 removeMessageCallback(...)

This method removes a callback function. You specify the callback function to remove using the same arguments you used to add the callback.

**Required arguments**

*jobName*

A String specifying the name of the job to be monitored or the SymbolicConstant ANY_JOB.

*messageType*

A SymbolicConstant specifying which message type will call this callback. Possible values are:
- ABORTED
- ANY_JOB
- ANY_MESSAGE_TYPE
- COMPLETED
- END_STEP
- ERROR
- HEADING
- HEALER_JOB
- HEALER_TYPE
- INTERRUPTED
- ITERATION
- JOB_ABORTED
- JOB_COMPLETED
- JOB_INTERRUPTED
- JOB_SUBMITTED
- MONITOR_DATA
- ODB_FILE
- ODB_FRAME
- SIMULATION_ABORTED
- SIMULATION_COMPLETED
- SIMULATION_INTERRUPTED
- SIMULATION_SUBMITTED
- STARTED
- STATUS
- STEP
- WARNING

*callback*

A Python function to be called; it must be the same as the *callback* argument specified in the original call to `addMessageCallback`.

*userData*

Any Python object or `None`; it must be the same as the *userData* argument specified in the original call to `addMessageCallback`.

**Optional arguments**

None.

**Return value**

None

**Exceptions**

None.

### 32.2.3 checkMonitorStatus()

This method raises a MonitorError exception if the monitoring status is not ENABLED. 

**Arguments**

None.

**Return value**

None

**Exceptions**

MonitorError:

```
Status is not ENABLED
```

### 32.2.4 Members

The MonitorMgr object has no members.




