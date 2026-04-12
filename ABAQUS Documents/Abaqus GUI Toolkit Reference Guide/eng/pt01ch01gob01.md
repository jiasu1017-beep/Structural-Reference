# AFXApp







This class is responsible for providing some high-level GUI control methods. 
![](../graphics/gui-afxapp.png)

### AFXApp(appName=Abaqus/CAE, vendorName=SIMULIA, productName='', majorNumber=-1, minorNumber=-1, updateNumber=-1, prerelease=False)

Constructor.
| **Argument** | **Type** | **Default** | **Description** |
| --- | --- | --- | --- |
| appName | String | Abaqus/CAE | Application registry key. |
| vendorName | String | SIMULIA | Vendor registry key. |
| productName | String | '' | Product name. |
| majorNumber | Int | -1 | Version number. |
| minorNumber | Int | -1 | Release number. |
| updateNumber | Int | -1 | Update number. |
| prerelease | Bool | False | Official/Prerelease flag. |

### create()

Creates windows for the application.

Reimplemented from FXApp.

### getAFXMainWindow()

Returns a pointer to the AFXMainWindow.

### getBasePrerelease()

Returns True if the base product is a prerelease.

### getBaseProductName()

Returns the base product name.

### getBaseVersionNumbers(majorNumber, minorNumber, updateNumber)

Returns the base product's major, minor, and update numbers.
| **Argument** | **Type** | **Default** | **Description** |
| --- | --- | --- | --- |
| majorNumber | Int |  | Version number. |
| minorNumber | Int |  | Release number. |
| updateNumber | Int |  | Update number. |

### getKernelInitializationCommand()

Returns the command string that will be issued upon application startup.

### getPrerelease()

Returns True if this is a prerelease.

### getProductName()

Returns the product name.

### getVersionNumbers()

Returns the major, minor, and update numbers.

### init(argc, argv)

Initializes the application and connects to the kernel.
| **Argument** | **Type** | **Default** | **Description** |
| --- | --- | --- | --- |
| argc | Int |  |  |
| argv | String |  |  |

### isLocked()

Returns True if the GUI is locked or False if otherwise.

Reimplemented from FXApp.

### isProductCAE()

Returns True if the base product is Abaqus/CAE.

### isProductViewer()

Returns True if the base product is Abaqus/Viewer.

### isStudentEdition()

Returns True if the base product is a student edition.

### lock()

Locks the GUI (normally used during command and mode processing).

### run()

Runs the main application event loop until stop() is called,.

Reimplemented from FXApp.

### runUntil(condition)

Run an event loop till some flag becomes non-zero.

Reimplemented from FXApp.
| **Argument** | **Type** | **Default** | **Description** |
| --- | --- | --- | --- |
| condition | Int |  |  |

### unlock()

Unlocks the GUI.

### Class flags

### **Message ID's.**

| **ID_QUERY_GUILOCK** | Used to query whether the GUI is locked. |
| --- | --- |
| **ID_SHOW_HOURGLASS** | Used to change the cursor. |




