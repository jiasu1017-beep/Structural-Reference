# 26.5 Queue object







A Queue object tells the job where and how to submit a job remotely. A Queue object can be used as the *queue* argument to the `Job` method.

**Access**

```
import job
session.queues[*name*]
```

### 26.5.1 Queue(...)

This method creates a Queue object. 

**Note:**Remote queues are available only on UNIX platforms.

**Path**

```
session.Queue
```

**Required arguments**

*name*

A String specifying the name of the new Queue object.

*queueName*

A String specifying the name of the remote analysis queue.

**Optional arguments**

*hostName*

A String specifying the name of the remote host. The default value is an empty string.

*fileCopy*

A Boolean specifying if the results files are to be copied from the remote machine to the local machine. The default value is ON.

*directory*

A String specifying the remote location for the execution of the simulation. The default value is an empty string.

*driver*

A String specifying the designation of the remote driver. The default value is "abaqus".

*localPlatform*

A SymbolicConstant specifying the type of operating system on the local machine. Possible values are UNIX and WINDOWS. The default value is WINDOWS.

*remotePlatform*

A SymbolicConstant specifying the type of operating system on the remote machine. The default value is UNIX.

*filesToCopy*

A sequence of Strings specifying the files to be copied from the remote location to the local machine. The default value is ('log', 'dat', 'msg', 'sta', 'odb', 'ipm', 'res', 'abq', 'pac', '023', 'sel').

*description*

A String specifying a description of the queue. The default value is an empty string.

**Return value**

A Queue object.

**Exceptions**

If *fileCopy*=ON and *hostName* is empty:

```
Remote queue host name is not set.
```

If *fileCopy*=ON and *directory* is empty:

```
Directory in which to run the job on the remote computer is not set.
```

### 26.5.2 Members

The Queue object has members with the same names and descriptions as the arguments to the [Queue](pt01ch26pyo05.md#ker-queue-queue-pyc) method.




