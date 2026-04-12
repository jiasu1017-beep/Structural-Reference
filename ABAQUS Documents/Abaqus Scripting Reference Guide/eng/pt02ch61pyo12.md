# 61.12 JobData object







The JobData               object describes the context in which the analysis was run.

**Access**

```
odb.jobData()
```

### 61.12.1 Members

The JobData object has the following members:

**Prototype**

```
odb_String name() const; 
            odb_String analysisCode() const; 
            odb_String version() const; 
            odb_String dateRun() const; 
            odb_String machineName() const; 
            odb_String precision() const;
```

*name*

An odb_String specifying the name of the job.

*analysisCode*

An odb_Enum::odb_AnalysisCodeEnum specifying the analysis code. Possible values are odb_Enum::ABAQUS_STANDARD, odb_Enum::ABAQUS_EXPLICIT, and odb_Enum::UNKNOWN_ANALYSIS_CODE.

*precision*

An odb_Enum::odb_PrecisionEnum specifying the precision. Only odb_Enum::SINGLE_PRECISION                  is currently supported.                 Possible values are odb_Enum::DOUBLE_PRECISION and odb_Enum::SINGLE_PRECISION.

*version*

An odb_String specifying the release of the analysis code.

*creationTime*

An odb_String specifying the date and time at which the analysis was run.

*modificationTime*

An odb_String specifying the date and time at which the database was last modified.

*machineName*

An odb_String specifying the name of the machine on which the analysis was run.

*productAddOns*

An odb_String specifying an odb_Sequence of productAddOns. Possible values are: Possible values are odb_Enum::AQUA, odb_Enum::DESIGN, odb_Enum::BIORID, odb_Enum::CEL, odb_Enum::SOLITER, and odb_Enum::CAVPARALLEL.




