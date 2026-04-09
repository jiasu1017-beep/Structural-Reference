## Appendix A: Example Files
This appendix contains the Python scripts that can be used to create complete models for the examples contained in this guide.  These files are also included with the Abaqus release; you can extract them from the compressed archive files using the **abaqus fetch** utility.
**To fetch a script:**
- At the operating system prompt, enter the command
```
abaqus fetch job=*file_name*
```
where *file_name* includes the extension `.py`.
**To run a script in Abaqus/CAE:**
- From the main menu bar, select **File**![](../images/arrow.gif)**Run Script**.
The **Run Script** dialog box appears.
- Choose the file from the list of available scripts, and click **OK**.

---

### A.1 Overhead hoist frame
gsi_frame_caemodel.py
```
#
# Getting Started with Abaqus: Interactive Edition
#
# Script for frame example
#
#
from abaqus import *
from abaqusConstants import *
session.viewports['Viewport: 1'].makeCurrent()
session.viewports['Viewport: 1'].maximize()
session.journalOptions.setValues(replayGeometry=COORDINATE,
recoverGeometry=COORDINATE)
from caeModules import *
from driverUtils import executeOnCaeStartup
executeOnCaeStartup()
Mdb()
mdb.models.changeKey(fromName='Model-1', toName='standard')
##
##  Sketch profile of frame
##
s = mdb.models['standard'].ConstrainedSketch(name='__profile__', sheetSize=4.0)
g, v, d, c = s.geometry, s.vertices, s.dimensions, s.constraints
s.setPrimaryObject(option=STANDALONE)
s.rectangle(point1=(-0.4, -0.2), point2=(0.4, 0.4))
s.delete(objectList=(c[18], c[21], c[19], c[20]))
s.ParallelConstraint(entity1=g.findAt((0.0, 0.4)), entity2=g.findAt((0.0,
-0.2)))
s.HorizontalDimension(vertex1=v.findAt((-0.4, 0.4)), vertex2=v.findAt((0.4,
0.4)), textPoint=(0.350665062665939, 0.510207295417786), value=1.0)
s.HorizontalDimension(vertex1=v.findAt((-0.4, -0.2)), vertex2=v.findAt((0.4,
-0.2)), textPoint=(0.299293786287308, -0.478947371244431), value=2.0)
s.ObliqueDimension(vertex1=v.findAt((0.4, 0.4)), vertex2=v.findAt((0.4,
-0.2)), textPoint=(0.589653432369232, 0.0547049306333065), value=1.0)
s.ObliqueDimension(vertex1=v.findAt((-1.6, -0.2)), vertex2=v.findAt((0.2,
0.4)), textPoint=(-0.524880945682526, 0.353907465934753), value=1.0)
session.viewports['Viewport: 1'].view.fitView()
s.Line(point1=(-0.45, 0.533012701892263), point2=(-0.15, -0.333012701892264))
s.CoincidentConstraint(entity1=v.findAt((-0.15, -0.333013)), entity2=g.findAt(
(0.05, -0.333013)), addUndoState=False)
s.Line(point1=(-0.15, -0.333012701892264), point2=(0.55, 0.533012701892263))
s.breakCurve(curve1=g.findAt((0.05, -0.333013)), point1=(-0.247599363327026,
-0.332068353891373), curve2=g.findAt((-0.3, 0.1)), point2=(
-0.158276319503784, -0.259217292070389))
s.EqualLengthConstraint(entity1=g.findAt((-0.3, 0.1)), entity2=g.findAt((0.2,
0.1)))
s.HorizontalConstraint(entity=g.findAt((-0.485701, -0.38399)))
s.HorizontalConstraint(entity=g.findAt((0.514299, -0.306365)))
p = mdb.models['standard'].Part(name='Frame', dimensionality=TWO_D_PLANAR,
type=DEFORMABLE_BODY)
p = mdb.models['standard'].parts['Frame']
p.BaseWire(sketch=s)
s.unsetPrimaryObject()
p = mdb.models['standard'].parts['Frame']
session.viewports['Viewport: 1'].setValues(displayedObject=p)
del mdb.models['standard'].sketches['__profile__']
##
##  Create material 'Steel'
##
mdb.models['standard'].Material('Steel')
mdb.models['standard'].materials['Steel'].Elastic(table=((200.E9, 0.3), ))
##
##  Create truss section
##
mdb.models['standard'].TrussSection(name='FrameSection', material='Steel',
area=1.963E-05)
##
##  Assign truss section
##
e = p.edges
edges = e
region = regionToolset.Region(edges=edges)
p.SectionAssignment(region=region, sectionName='FrameSection')
a = mdb.models['standard'].rootAssembly
session.viewports['Viewport: 1'].setValues(displayedObject=a)
##
##  Set coordinate system (done by default)
##
a = mdb.models['standard'].rootAssembly
a.DatumCsysByDefault(CARTESIAN)
##
##  Instance the frame
##
p = mdb.models['standard'].parts['Frame']
a.Instance(name='Frame-1', part=p, dependent=ON)
p1 = a.instances['Frame-1']
p1.translate(vector=(-0.035794, 0.331227, 0.0))
##
##  Create a static linear perturbation step
##
mdb.models['standard'].StaticLinearPerturbationStep(name='Apply load',
previous='Initial', description='10kN central load',
matrixSolver=SOLVER_DEFAULT)
session.viewports['Viewport: 1'].assemblyDisplay.setValues(step='Apply load')
mdb.models['standard'].fieldOutputRequests['F-Output-1'].setValues(
variables=PRESELECT, region=MODEL)
##
##  Apply concentrated force to bottom center
##
v = a.instances['Frame-1'].vertices
region=((v.findAt(((0.0, 0.0, 0.0), ), ), ), )
mdb.models['standard'].ConcentratedForce(name='Force',
createStepName='Apply load',
region=region, cf2=-10000.0)
##
##  Apply encastre bc to bottom left corner
##
region=(v.findAt(((-1.0, 0.0, 0.0), ), ), None, None, None)
mdb.models['standard'].EncastreBC(name='Fixed', createStepName='Initial',
region=region)
##
##  Apply roller bc to bottom right corner
##
region=(v.findAt(((1.0, 0.0, 0.0), ), ), None, None, None)
mdb.models['standard'].DisplacementBC(name='Roller',
createStepName='Initial', region=region, u2=0.0)
##
##  Assign global seed
##
p.seedPart(size=1.0)
##
##  Assign element type
##
elemType1 = mesh.ElemType(elemCode=T2D2)
e = p.edges
edges = e
pickedRegions =(edges, )
p.setElementType(regions=pickedRegions, elemTypes=(elemType1, ))
##
##  Generate mesh
##
p.generateMesh()
##
##  Create job
##
mdb.Job(name='Frame', model='standard',
description='Two-dimensional overhead hoist frame')
mdb.jobs['Frame'].setValues(echoPrint=ON, modelPrint=ON, contactPrint=ON,
historyPrint=ON)
session.viewports['Viewport: 1'].view.fitView()
##
##  Save model database
##
mdb.saveAs('Frame')
##
##  Create explicit dynamics model
##
mdb.Model(name='explicit', objectToCopy=mdb.models['standard'])
##
##  add density
##
mdb.models['explicit'].materials['Steel'].Density(table=((7800.0, ), ))
a = mdb.models['explicit'].rootAssembly
session.viewports['Viewport: 1'].setValues(displayedObject=a)
##
##  replace static step with explicit dynamics step
##  add new history output requests
##
mdb.models['explicit'].ExplicitDynamicsStep(name='Apply load',
previous='Initial', maintainAttributes=True, timePeriod=0.01)
v = a.instances['Frame-1'].vertices
verts = v.findAt(((0.0, 0.0, 0.0), ))
a.Set(vertices=verts, name='Center')
regionDef=mdb.models['explicit'].rootAssembly.sets['Center']
mdb.models['explicit'].historyOutputRequests['H-Output-1'].setValues(
variables=('UT', ), region=regionDef, frequency=1)
##
#  change element library to EXPLICIT
##
elemType1 = mesh.ElemType(elemCode=T2D2, elemLibrary=EXPLICIT)
p = mdb.models['explicit'].parts['Frame']
e = p.edges
edges = e
p.setElementType(regions=pickedRegions, elemTypes=(elemType1, ))
##
##  create job
##
mdb.Job(name='expFrame', model='explicit', type=ANALYSIS,
description='Two-dimensional overhead hoist frame-explicit dynamics')
a = mdb.models['standard'].rootAssembly
a.regenerate()
a = mdb.models['explicit'].rootAssembly
a.regenerate()
mdb.save()
```

---

### A.2 Connecting lug
gsi_lug_caemodel.py
```
#
# Getting Started with Abaqus: Interactive Edition
#
# Script for elastic lug example
#
from abaqus import *
from abaqusConstants import *
session.viewports['Viewport: 1'].makeCurrent()
session.viewports['Viewport: 1'].maximize()
session.journalOptions.setValues(replayGeometry=COORDINATE,
recoverGeometry=COORDINATE)
from caeModules import *
from driverUtils import executeOnCaeStartup
executeOnCaeStartup()
Mdb()
mdb.models.changeKey(fromName='Model-1', toName='standard')
session.viewports['Viewport: 1'].setValues(displayedObject=None)
##  Sketch profile of the lug
s = mdb.models['standard'].ConstrainedSketch(name='__profile__',
sheetSize=0.25)
g, v, d, c = s.geometry, s.vertices, s.dimensions, s.constraints
s.sketchOptions.setValues(decimalPlaces=3)
s.setPrimaryObject(option=STANDALONE)
s.rectangle(point1=(-0.0275, 0.0225), point2=(0.02125, -0.01375))
s.delete(objectList=(g.findAt((0.02125, 0.004375)), ))
s.EqualLengthConstraint(entity1=g.findAt((-0.003125, -0.01375)),
entity2=g.findAt((-0.003125, 0.0225)))
s.ObliqueDimension(vertex1=v.findAt((-0.0275, -0.01375)), vertex2=v.findAt((
0.02125, -0.01375)), textPoint=(-0.010330107063055, -0.023654306307435),
value=0.1)
s.move(vector=(-0.025625, 0.0), objectList=(g.findAt((-0.0275, 0.004375)),
g.findAt((0.0225, -0.01375)), g.findAt((0.0225, 0.0225))))
session.viewports['Viewport: 1'].view.fitView()
s.ObliqueDimension(vertex1=v.findAt((-0.053125, 0.0225)), vertex2=v.findAt((
-0.053125, -0.01375)), textPoint=(-0.0564765408635139,
0.00896133482456207), value=0.05)
session.viewports['Viewport: 1'].view.fitView()
session.viewports['Viewport: 1'].view.setValues(nearPlane=0.230597,
farPlane=0.279546, width=0.144889, height=0.121934)
s.Arc3Points(point1=(0.046875, 0.03625), point2=(0.046875, -0.01375), point3=(
0.0625, 0.02375))
s.TangentConstraint(entity1=g.findAt((-0.003125, 0.03625)), entity2=g.findAt((
0.0657, 0.01125)))
s.move(vector=(-0.001797, 0.0), objectList=(g.findAt((-0.053125, 0.01125)),
g.findAt((-0.003125, -0.01375)), g.findAt((-0.003125, 0.03625)), g.findAt((
0.071875, 0.01125))))
s.TangentConstraint(entity1=g.findAt((-0.004922, -0.01375)), entity2=g.findAt((
0.070078, 0.01125)))
session.viewports['Viewport: 1'].view.fitView()
s.RadialDimension(curve=g.findAt((0.070078, 0.01125)), textPoint=(
0.0655877739191055, -0.0193991288542748), radius=0.025)
d[2].setValues(reference=ON)
s.CircleByCenterPerimeter(center=(0.0425, 0.0125), point1=(0.0525, 0.01625))
s.ConcentricConstraint(entity1=g.findAt((0.0325, 0.00875)), entity2=g.findAt((
0.070078, 0.01125)))
s.RadialDimension(curve=g.findAt((0.035078, 0.0075)), textPoint=(
0.0297759883105755, 0.0219836011528969), radius=0.015)
s.VerticalDimension(vertex1=v.findAt((0.045078, 0.01125)), vertex2=v.findAt((
0.059123, 0.016517)), textPoint=(0.0632773488759995, 0.0129371425136924),
value=0.0)
s.VerticalDimension(vertex1=v.findAt((0.045078, 0.01125)), vertex2=v.findAt((
0.067003, 0.023263)), textPoint=(0.0746369957923889, 0.012744665145874),
value=0.0)
s.move(vector=(0.034922, 0.00375), objectList=(g.findAt((-0.054922, 0.01125)),
g.findAt((-0.004922, -0.01375)), g.findAt((-0.004922, 0.03625)),
g.findAt((0.070078, 0.01125)), g.findAt((0.030078, 0.01125))))
p = mdb.models['standard'].Part(name='Lug', dimensionality=THREE_D,
type=DEFORMABLE_BODY)
p = mdb.models['standard'].parts['Lug']
p.BaseSolidExtrude(sketch=s, depth=0.02)
s.unsetPrimaryObject()
p = mdb.models['standard'].parts['Lug']
session.viewports['Viewport: 1'].setValues(displayedObject=p)
del mdb.models['standard'].sketches['__profile__']
c, f, e, v, d  = p.cells, p.faces, p.edges, p.vertices, p.datums
##
##  Create material 'Steel'
##
mdb.models['standard'].Material('Steel')
mdb.models['standard'].materials['Steel'].Elastic(table=((200.0E9, 0.3), ))
##
##  Create solid section
##
mdb.models['standard'].HomogeneousSolidSection(name='LugSection',
material='Steel', thickness=1.0)
##
##  Assign solid section
##
c = p.cells
cells = c
region = regionToolset.Region(cells=cells)
p.SectionAssignment(region=region, sectionName='LugSection', offset=0.0)
##
##  Set coordinate system (done by default)
##
a = mdb.models['standard'].rootAssembly
a.DatumCsysByDefault(CARTESIAN)
##
##  Instance the lug
##
a.Instance(name='Lug-1', part=p, dependent=ON)
##
##  Create a static general step
##
mdb.models['standard'].StaticStep(name='LugLoad',
previous='Initial', description='Apply uniform pressure to the hole')
session.viewports['Viewport: 1'].assemblyDisplay.setValues(step='LugLoad')
##
##  Modify output requests
##
mdb.models['standard'].fieldOutputRequests['F-Output-1'].setValues(
variables=('S', 'U', 'RF', 'NFORC'), region=MODEL)
del mdb.models['standard'].historyOutputRequests['H-Output-1']
##
##  Apply encastre bc to left end
##
f = a.instances['Lug-1'].faces
faces = f.findAt(((-0.02, 0.006667, 0.013333), ))
region = regionToolset.Region(faces=faces)
mdb.models['standard'].EncastreBC(name='Fix left end',
createStepName='LugLoad', region=region)
session.viewports['Viewport: 1'].setValues(displayedObject=a)
session.viewports['Viewport: 1'].view.fitView()
session.viewports['Viewport: 1'].view.setValues(session.views['Iso'])
##
##  Partition the lug
##
c, f, e, v, d  = p.cells, p.faces, p.edges, p.vertices, p.datums
pickedCells = c.findAt(((-0.02, 0.006667, 0.013333), ))
p.PartitionCellByPlaneThreePoints(point1=v.findAt(coordinates=(0.095, 0.015,
0.02)), cells=pickedCells, point2=p.InterestingPoint(edge=e.findAt(
coordinates=(0.08, 0.03, 0.02)), rule=MIDDLE), point3=p.InterestingPoint(
edge=e.findAt(coordinates=(0.08, 0.03, 0.0)), rule=MIDDLE))
c, f, e, v, d  = p.cells, p.faces, p.edges, p.vertices, p.datums
##
##  Apply pressure load to bottom of hole
##
a.regenerate()
s = a.instances['Lug-1'].faces
side1Faces = s.findAt(((0.094968, 0.01402, 0.013333), ))
region = regionToolset.Region(side1Faces=side1Faces)
mdb.models['standard'].Pressure(name='Pressure load',
createStepName='LugLoad', region=region, magnitude=5.0E7)
##
##  Create partitions
##
pickedCells = c.findAt(((-0.02, 0.006667, 0.006667), ), ((-0.02, 0.023333,
0.013333), ))
p.PartitionCellByPlaneThreePoints(cells=pickedCells, point1=p.InterestingPoint(
edge=e.findAt(coordinates=(0.069393, 0.004393, 0.0)), rule=MIDDLE),
point2=p.InterestingPoint(edge=e.findAt(coordinates=(0.069393, 0.004393,
0.02)), rule=MIDDLE), point3=p.InterestingPoint(edge=e.findAt(
coordinates=(0.090607, 0.025607, 0.02)), rule=MIDDLE))
c, f, e, v, d  = p.cells, p.faces, p.edges, p.vertices, p.datums
p.DatumPointByEdgeParam(edge=e.findAt(coordinates=(0.055, -0.01, 0.02)),
parameter=0.25)
pickedCells = c.findAt(((-0.02, 0.006667, 0.006667), ), ((-0.02, 0.023333,
0.013333), ))
p.PartitionCellByPlanePointNormal(point=d[5], normal=e.findAt(coordinates=(
0.055, -0.01, 0.02)), cells=pickedCells)
c, f, e, v, d  = p.cells, p.faces, p.edges, p.vertices, p.datums
##
##  Assign global seed
##
p.seedPart(size=0.007)
import re, uti
if re.search('Student', uti.getProductVersion()):
p.seedPart(size=0.01)
##
##  Assign element type
##
elemType1 = mesh.ElemType(elemCode=C3D20R)
elemType2 = mesh.ElemType(elemCode=C3D15)
elemType3 = mesh.ElemType(elemCode=C3D10M)
cells = c
pickedRegions =(cells, )
p.setElementType(regions=pickedRegions, elemTypes=(elemType1, elemType2,
elemType3))
##
##  Generate the mesh
##
p.generateMesh()
session.viewports['Viewport: 1'].view.setValues(session.views['Iso'])
session.viewports['Viewport: 1'].assemblyDisplay.geometryOptions.setValues(
datumPoints=OFF)
##
##  Create job
##
a.regenerate()
mdb.Job(name='Lug', model='standard',
description='Linear Elastic Steel Connecting Lug')
##
##  Save model database
##
mdb.saveAs('Lug.cae')
##
##  Explicit dynamics model
##
mdb.Model(name='explicit', objectToCopy=mdb.models['standard'])
##
##  add density
##
mdb.models['explicit'].materials['Steel'].Density(table=((7800.0, ), ))
##
##  replace static step with explicit dynamics step
##
a = mdb.models['explicit'].rootAssembly
session.viewports['Viewport: 1'].setValues(displayedObject=a)
mdb.models['explicit'].ExplicitDynamicsStep(name='LugLoad',
previous='Initial', maintainAttributes=True, timePeriod=0.005)
##
##  change number of field output intervals to 125
##
mdb.models['explicit'].fieldOutputRequests['F-Output-1'].setValues(
numIntervals=125)
##
##  change element type to linear and library to EXPLICIT
##
elemType1 = mesh.ElemType(elemCode=C3D8R, elemLibrary=EXPLICIT,
hourglassControl=ENHANCED)
elemType2 = mesh.ElemType(elemCode=C3D6, elemLibrary=EXPLICIT)
elemType3 = mesh.ElemType(elemCode=C3D4, elemLibrary=EXPLICIT)
p = mdb.models['explicit'].parts['Lug']
c = p.cells
cells = c
pickedRegions =(cells, )
p.setElementType(regions=pickedRegions, elemTypes=(elemType1, elemType2,
elemType3))
if re.search('Student', uti.getProductVersion()):
p.seedPart(size=0.007)
p.generateMesh()
##
##  create job
##
mdb.Job(name='expLug', model='explicit', type=ANALYSIS,
description='dynamic analysis of lug')
a = mdb.models['standard'].rootAssembly
a.regenerate()
a = mdb.models['explicit'].rootAssembly
a.regenerate()
mdb.save()
```

---

### A.3 Skew plate
gsi_skewplate_caemodel.py
```
#
# Getting Started with Abaqus: Interactive Edition
#
# Script for linear skew plate example
#
from abaqus import *
from abaqusConstants import *
session.viewports['Viewport: 1'].makeCurrent()
session.viewports['Viewport: 1'].maximize()
session.journalOptions.setValues(replayGeometry=COORDINATE,
recoverGeometry=COORDINATE)
from caeModules import *
from driverUtils import executeOnCaeStartup
executeOnCaeStartup()
Mdb()
##
##  Sketch profile of the plate
##
s = mdb.models['Model-1'].ConstrainedSketch(name='__profile__', sheetSize=4.0)
g, v, d, c = s.geometry, s.vertices, s.dimensions, s.constraints
s.setPrimaryObject(option=STANDALONE)
s.rectangle(point1=(-0.275, 0.25), point2=(0.575, -0.25))
s.delete(objectList=(c[18], c[19], c[20], c[21], c[22]))
s.VerticalConstraint(entity=g.findAt((-0.275, 0.0)))
s.VerticalConstraint(entity=g.findAt((0.575, 0.0)))
s.ParallelConstraint(entity1=g.findAt((0.15, -0.25)), entity2=g.findAt((0.15,
0.25)))
s.ObliqueDimension(vertex1=v.findAt((-0.275, 0.25)), vertex2=v.findAt((-0.275,
-0.25)), textPoint=(-0.384168207645416, -0.039074968546629), value=0.4)
s.HorizontalDimension(vertex1=v.findAt((-0.275, -0.25)), vertex2=v.findAt((
0.575, -0.25)), textPoint=(0.502545475959778, -0.405263155698776),
value=1.0)
s.AngularDimension(line1=g.findAt((-0.275, -0.05)), line2=g.findAt((0.225,
-0.25)), textPoint=(-0.221120104193687, -0.173046261072159), value=60.0)
session.viewports['Viewport: 1'].view.fitView()
s.move(vector=(-0.725, 0.05), objectList=(g.findAt((-0.275, -0.05)), g.findAt((
0.225, 0.038675)), g.findAt((0.725, 0.52735)), g.findAt((0.225,
0.438675))))
p = mdb.models['Model-1'].Part(name='Plate', dimensionality=THREE_D,
type=DEFORMABLE_BODY)
p = mdb.models['Model-1'].parts['Plate']
p.BaseShell(sketch=s)
s.unsetPrimaryObject()
p = mdb.models['Model-1'].parts['Plate']
session.viewports['Viewport: 1'].setValues(displayedObject=p)
del mdb.models['Model-1'].sketches['__profile__']
##
##  Create material 'Metal'
##
mdb.models['Model-1'].Material('Metal')
mdb.models['Model-1'].materials['Metal'].Elastic(table=((30.0E9, 0.3), ))
##
##  Create shell section
##
mdb.models['Model-1'].HomogeneousShellSection(name='PlateSection',
preIntegrate=ON,
material='Metal', thickness=0.008,
poissonDefinition=DEFAULT, temperature=GRADIENT)
##
##  Create datum coordinate system
##
p1 = mdb.models['Model-1'].parts['Plate']
e = p1.edges
p1.DatumCsysByTwoLines(CARTESIAN, line1=e.findAt((-0.75,
-0.0556624327025937, 0.0), ), line2=e.findAt((0.0,
0.477350269189625, 0.0), ))
##
##  Assign material orientation to the plate
##
p0 = mdb.models['Model-1'].parts['Plate']
f = p0.faces
faces = f[0:1]
region=(None, None,
f.findAt(((-0.666666666666667,
0.125783423063208, 0.0), (0.0, 0.0, 1.0)), ), None)
datum = p0.datums[2]
p0.MaterialOrientation(region=region, localCsys=datum, axis=AXIS_3)
##
##  Assign section to the plate
##
p0 = mdb.models['Model-1'].parts['Plate']
f = p0.faces
faces = f[0:1]
region=(None, None,
f.findAt(((-0.666666666666667,
0.125783423063208, 0.0), (0.0, 0.0, 1.0)), ), None)
p0 = mdb.models['Model-1'].parts['Plate']
p0.SectionAssignment(region=region, sectionName='PlateSection')
a = mdb.models['Model-1'].rootAssembly
session.viewports['Viewport: 1'].setValues(displayedObject=a)
##
##  Set coordinate system (done by default)
##
a = mdb.models['Model-1'].rootAssembly
a.DatumCsysByDefault(CARTESIAN)
##
##  Instance the plate
##
p = mdb.models['Model-1'].parts['Plate']
a.Instance(name='Plate-1', part=p, dependent=ON)
##
##  Partition the plate
##
p = mdb.models['Model-1'].parts['Plate']
c, f, e, v, d  = p.cells, p.faces, p.edges, p.vertices, p.datums
faces=(f.findAt((
-0.666666666666667, 0.125783423063208, 0.0), (0.0, 0.0, 1.0)), )
p.PartitionFaceByShortestPath(faces=faces,
point1=p.InterestingPoint(e.findAt((-0.75,
-0.0556624327025937, 0.0), ), MIDDLE),
point2=p.InterestingPoint(e.findAt((-0.25,
0.63301270189222, 0.0), ), MIDDLE))
c, f, e, v, d  = p.cells, p.faces, p.edges, p.vertices, p.datums
##
##  Create geometry set 'MidSpan'
##
a = mdb.models['Model-1'].rootAssembly
e1 = a.instances['Plate-1'].edges
a.Set(edges=e1.findAt((
(-0.5, 0.188675134594813, 0.0), ), ), name='MidSpan')
##
##  Create geometry set 'EndA'
##
a = mdb.models['Model-1'].rootAssembly
e1 = a.instances['Plate-1'].edges
a.Set(edges=e1.findAt((
(-1.0, 0.1, 0.0), ), ), name='EndA')
##
##  Create geometry set 'EndB'
##
a = mdb.models['Model-1'].rootAssembly
e1 = a.instances['Plate-1'].edges
a.Set(edges=e1.findAt((
(0.0, 0.477350269189625, 0.0), ), ), name='EndB')
##
##  Create a static general step
##
mdb.models['Model-1'].StaticStep(name='Apply pressure',
previous='Initial', description='Uniform pressure(20 kPa) load',
timePeriod=1, adiabatic=OFF, maxNumInc=100,
stabilization=None, timeIncrementationMethod=AUTOMATIC, initialInc=1,
minInc=1e-05, maxInc=1, matrixSolver=SOLVER_DEFAULT, amplitude=RAMP,
extrapolation=LINEAR, fullyPlastic="")
session.viewports['Viewport: 1'].assemblyDisplay.setValues(
step='Apply pressure')
##
##  Modify output requests
##
mdb.models['Model-1'].fieldOutputRequests['F-Output-1'].setValues(
variables=('S', 'E', 'U', 'RF'))
a0=mdb.models['Model-1'].rootAssembly
regionDef=a0.sets['MidSpan']
mdb.models['Model-1'].historyOutputRequests['H-Output-1'].setValues(
variables=('U3',), region=regionDef)
session.viewports['Viewport: 1'].assemblyDisplay.setValues(loads=ON, bcs=ON,
predefinedFields=ON)
##
##  Apply bc in local CSYS to set EndB (right edge)
##
a0 = mdb.models['Model-1'].rootAssembly
region = a0.sets['EndB']
datum = mdb.models['Model-1'].rootAssembly.instances['Plate-1'].datums[2]
mdb.models['Model-1'].DisplacementBC(name='Rail boundary condition',
createStepName='Apply pressure', region=region, u2=0.0, u3=0.0, ur1=0.0,
ur2=0.0, ur3=0.0, localCsys=datum)
##
##  Apply encastre bc to set EndA (left edge)
##
a0 = mdb.models['Model-1'].rootAssembly
region = a0.sets['EndA']
mdb.models['Model-1'].EncastreBC(name='Fix left end',
createStepName='Apply pressure', region=region)
##
##  Apply pressure load
##
a0 = mdb.models['Model-1'].rootAssembly
f1 = a0.instances['Plate-1'].faces
region=((
f1.findAt(((
-0.666666666666667, 0.259116756396542, 0.0), (0.0, 0.0, 1.0)), ((
-0.333333333333333, 0.318233512793084, 0.0), (0.0, 0.0, 1.0)), ), SIDE1),
)
mdb.models['Model-1'].Pressure(name='Pressure',
createStepName='Apply pressure', region=region, magnitude=2.0E4)
session.viewports['Viewport: 1'].assemblyDisplay.setValues(mesh=ON, loads=OFF,
bcs=OFF, predefinedFields=OFF)
session.viewports['Viewport: 1'].assemblyDisplay.meshOptions.setValues(
meshTechnique=ON)
##
##  Assign global seed
##
p.seedPart(size=0.1)
##
##  Use structured meshing
##
f1 = p.faces
regions=(
f1.findAt((
-0.666666666666667, 0.259116756396542, 0.0), (0.0, 0.0, 1.0)),
f1.findAt((
-0.333333333333333, 0.318233512793084, 0.0), (0.0, 0.0, 1.0)))
p.setMeshControls(regions=regions, technique=STRUCTURED)
##
##  Assign element type
##
elemType1 = mesh.ElemType(elemCode=S8R5)
elemType2 = mesh.ElemType(elemCode=STRI65)
regions=(None, None,
f1.findAt(((
-0.666666666666667, 0.259116756396542, 0.0), (0.0, 0.0, 1.0)), ((
-0.333333333333333, 0.318233512793084, 0.0), (0.0, 0.0, 1.0)), ), None)
p.setElementType(regions=regions, elemTypes=(elemType1, elemType2))
##
##  Generate mesh
##
p.generateMesh()
session.viewports['Viewport: 1'].assemblyDisplay.setValues(mesh=OFF)
session.viewports['Viewport: 1'].assemblyDisplay.meshOptions.setValues(
meshTechnique=OFF)
##
##  Create job
##
mdb.Job(name='SkewPlate', model='Model-1',
description='Linear Elastic Skew Plate. 20 kPa Load.')
a = mdb.models['Model-1'].rootAssembly
a.regenerate()
##
##  Save model database
##
mdb.saveAs('SkewPlate.cae')
```

---

### A.4 Cargo crane
gsi_crane_caemodel.py
```
#
# Getting Started with Abaqus: Interactive Edition
#
# Script for static crane example
#
def GetBlockPosition(modelName, blockPrefix):
if blockPrefix == '':
return len(mdb.models[modelName].keywordBlock.sieBlocks)-1
pos = 0
for block in mdb.models[modelName].keywordBlock.sieBlocks:
if block[0:len(blockPrefix)].lower()==blockPrefix.lower():
return pos
pos=pos+1
return -1
from abaqus import *
from abaqusConstants import *
session.viewports['Viewport: 1'].makeCurrent()
session.viewports['Viewport: 1'].maximize()
from caeModules import *
from driverUtils import executeOnCaeStartup
executeOnCaeStartup()
Mdb()
session.viewports['Viewport: 1'].setValues(displayedObject=None)
##
##  Sketch profile of truss
##
p = mdb.models['Model-1'].Part(name='Truss', dimensionality=THREE_D,
type=DEFORMABLE_BODY)
p.ReferencePoint(point=(0.0, 0.0, 0.0))
p = mdb.models['Model-1'].parts['Truss']
session.viewports['Viewport: 1'].setValues(displayedObject=p)
d, r = p.datums, p.referencePoints
p.DatumPointByOffset(point=r[1], vector=(0.0, 1.0, 0.0))
p.DatumPointByOffset(point=r[1], vector=(8.0, 1.5, 0.9))
p.DatumPlaneByThreePoints(point1=r[1], point2=d[3], point3=d[2])
p.DatumAxisByPrincipalAxis(principalAxis=YAXIS)
session.viewports['Viewport: 1'].view.fitView()
t = p.MakeSketchTransform(sketchPlane=d[4], sketchUpEdge=d[5],
sketchPlaneSide=SIDE1, sketchOrientation=LEFT, origin=(0.0, 0.0, 0.0))
s = mdb.models['Model-1'].ConstrainedSketch(name='__profile__',
sheetSize=683.38, gridSpacing=17.08, transform=t)
g, v, d1, c = s.geometry, s.vertices, s.dimensions, s.constraints
s.setPrimaryObject(option=SUPERIMPOSE)
p = mdb.models['Model-1'].parts['Truss']
p.projectReferencesOntoSketch(sketch=s, filter=COPLANAR_EDGES)
session.viewports['Viewport: 1'].view.setValues(nearPlane=648.075,
farPlane=719.271, width=13.6266, height=9.28111, cameraPosition=(-71.5628,
0.978423, 679.645), cameraTarget=(4.83613, 0.978423, 0.544065))
s.Line(point1=(0.0, 0.0), point2=(8.05046582503149, 1.5))
s.CoincidentConstraint(entity1=v.findAt((0.0, 0.0)), entity2=g.findAt((0.0,
0.5)))
s.Line(point1=(8.05046582503149, 1.5), point2=(0.0, 1.0))
s.Line(point1=(0.0, 1.0), point2=(1.59409310185916, 0.297018794285658))
s.CoincidentConstraint(entity1=v.findAt((1.594093, 0.297019)),
entity2=g.findAt((4.025233, 0.75)))
s.Line(point1=(1.59409310185916, 0.297018794285658),
point2=(2.30592731982451, 1.14321701190598))
s.CoincidentConstraint(entity1=v.findAt((2.305927, 1.143217)),
entity2=g.findAt((4.025233, 1.25)))
s.Line(point1=(2.30592731982451, 1.14321701190598),
point2=(3.26033977276254, 0.607481575033539))
s.CoincidentConstraint(entity1=v.findAt((3.26034, 0.607482)),
entity2=g.findAt((4.025233, 0.75)))
s.Line(point1=(3.26033977276254, 0.607481575033539),
point2=(4.16525059699136, 1.25869624736747))
s.CoincidentConstraint(entity1=v.findAt((4.165251, 1.258696)),
entity2=g.findAt((4.025233, 1.25)))
s.Line(point1=(4.16525059699136, 1.25869624736747),
point2=(4.95150583156061, 0.922587451305882))
s.CoincidentConstraint(entity1=v.findAt((4.951506, 0.922587)),
entity2=g.findAt((4.025233, 0.75)))
s.breakCurve(curve1=g.findAt((4.025233, 0.75)),
point1=(0.733189206279801, 0.182644009590149),
curve2=g.findAt((1.95001, 0.720118)),
point2=(1.62787567272877, 0.433001518249512))
s.breakCurve(curve1=g.findAt((4.822279, 0.898509)),
point1=(2.34362044857835, 0.415118813514709),
curve2=g.findAt((2.783134, 0.875349)),
point2=(3.22040910681461, 0.701241612434387))
s.breakCurve(curve1=g.findAt((5.655403, 1.053741)),
point1=(4.04351950354929, 0.772772312164307),
curve2=g.findAt((4.558378, 1.090642)),
point2=(5.02767302451382, 0.95159912109375))
s.breakCurve(curve1=g.findAt((4.025233, 1.25)),
point1=(1.55629884485765, 1.09466052055359),
curve2=g.findAt((1.95001, 0.720118)),
point2=(2.32572264036564, 1.02312982082367))
s.breakCurve(curve1=g.findAt((5.178197, 1.321609)),
point1=(3.79300780849022, 1.23772192001343),
curve2=g.findAt((3.712795, 0.933089)),
point2=(4.168774592922, 1.18407392501831))
s.VerticalDimension(vertex1=v.findAt((0.0, 1.0)),
vertex2=v.findAt((0.0, 0.0)),
textPoint=(-0.304643334343144, 0.0216999053955078), value=1.0)
s.HorizontalDimension(vertex1=v.findAt((0.0, 0.0)),
vertex2=v.findAt((8.050466, 1.5)),
textPoint=(6.26233672422377, -0.443249702453613), value=8.05046582503149)
s.ParallelConstraint(entity1=g.findAt((1.152964, 1.071609)), entity2=g.findAt((
3.235589, 1.200957)))
s.ParallelConstraint(entity1=g.findAt((3.235589, 1.200957)), entity2=g.findAt((
6.107858, 1.379348)))
s.ParallelConstraint(entity1=g.findAt((0.797047, 0.148509)), entity2=g.findAt((
2.427216, 0.45225)))
s.ParallelConstraint(entity1=g.findAt((2.427216, 0.45225)), entity2=g.findAt((
4.105923, 0.765035)))
s.ParallelConstraint(entity1=g.findAt((4.105923, 0.765035)), entity2=g.findAt((
6.500986, 1.211294)))
s.EqualLengthConstraint(entity1=g.findAt((0.797047, 0.148509)),
entity2=g.findAt((2.427216, 0.45225)))
s.EqualLengthConstraint(entity1=g.findAt((2.39114, 0.445528)),
entity2=g.findAt((4.033769, 0.751591)))
s.EqualLengthConstraint(entity1=g.findAt((3.985233, 0.742547)),
entity2=g.findAt((6.416373, 1.195528)))
s.EqualLengthConstraint(entity1=g.findAt((1.152964, 1.071609)),
entity2=g.findAt((3.235589, 1.200957)))
s.EqualLengthConstraint(entity1=g.findAt((3.458891, 1.214826)),
entity2=g.findAt((6.33116, 1.393217)))
mdb.models['Model-1'].ConstrainedSketch(name='Truss', objectToCopy=s)
p = mdb.models['Model-1'].parts['Truss']
d = p.datums
p.Wire(sketchPlane=d[4], sketchUpEdge=d[5], sketchPlaneSide=SIDE1,
sketchOrientation=LEFT, sketch=s)
s.unsetPrimaryObject()
del mdb.models['Model-1'].sketches['__profile__']
session.viewports['Viewport: 1'].view.fitView()
p = mdb.models['Model-1'].parts['Truss']
d, r = p.datums, p.referencePoints
p.DatumPointByOffset(point=d[2], vector=(0.0, 0.0, 2.0))
p.DatumPointByOffset(point=r[1], vector=(0.0, 0.0, 2.0))
p.DatumPointByOffset(point=d[3], vector=(0.0, 0.0, 0.2))
p.DatumPlaneByThreePoints(point1=d[8], point2=d[9], point3=d[7])
t = p.MakeSketchTransform(sketchPlane=d[10], sketchUpEdge=d[5],
sketchPlaneSide=SIDE1, sketchOrientation=LEFT, origin=(4.122203, 0.75,
1.536252))
s = mdb.models['Model-1'].ConstrainedSketch(name='__profile__',
sheetSize=683.38, gridSpacing=17.08, transform=t)
g, v, d, c = s.geometry, s.vertices, s.dimensions, s.constraints
s.setPrimaryObject(option=SUPERIMPOSE)
p.projectReferencesOntoSketch(sketch=s, filter=COPLANAR_EDGES)
s.retrieveSketch(sketch=mdb.models['Model-1'].sketches['Truss'])
s.move(vector=(-4.14820681508444, -0.75), objectList=(g.findAt((0.0, 0.5)),
g.findAt((1.006308, 0.6875)), g.findAt((2.348053, 0.770833)), g.findAt((
3.354361, 0.958333)), g.findAt((4.696105, 1.041667)), g.findAt((5.702413,
1.229167)), g.findAt((1.006308, 0.1875)), g.findAt((3.018925, 0.5625)),
g.findAt((5.031541, 0.9375)), g.findAt((7.044158, 1.3125)), g.findAt((
1.341744, 1.083333)), g.findAt((6.708722, 1.416667)), g.findAt((4.025233,
1.25)), v.findAt((8.050466, 1.5)), v.findAt((0.0, 1.0))))
d = p.datums
p.Wire(sketchPlane=d[10], sketchUpEdge=d[5], sketchPlaneSide=SIDE1,
sketchOrientation=LEFT, sketch=s)
s.unsetPrimaryObject()
del mdb.models['Model-1'].sketches['__profile__']
##
##  dummy part
##
p = mdb.models['Model-1'].Part(name='Truss-all',
objectToCopy=mdb.models['Model-1'].parts['Truss'])
session.viewports['Viewport: 1'].setValues(displayedObject=p)
v = p.vertices
p.WirePolyLine(points=((v.findAt(coordinates=(2.0, 0.375, 1.775)), v.findAt(
coordinates=(2.0, 0.375, 0.225))), (v.findAt(coordinates=(2.0, 0.375,
0.225)), v.findAt(coordinates=(2.666667, 1.166667, 1.7))), (v.findAt(
coordinates=(2.666667, 1.166667, 1.7)), v.findAt(coordinates=(2.666667,
1.166667, 0.3))), (v.findAt(coordinates=(4.0, 0.75, 1.55)), v.findAt(
coordinates=(4.0, 0.75, 0.45))), (v.findAt(coordinates=(4.0, 0.75, 0.45)),
v.findAt(coordinates=(5.333333, 1.333333, 1.4))), (v.findAt(coordinates=(
5.333333, 1.333333, 1.4)), v.findAt(coordinates=(5.333333, 1.333333,
0.6))), (v.findAt(coordinates=(5.333333, 1.333333, 0.6)), v.findAt(
coordinates=(6.0, 1.125, 1.325))), (v.findAt(coordinates=(6.0, 1.125,
1.325)), v.findAt(coordinates=(6.0, 1.125, 0.675)))), mergeType=IMPRINT,
meshable=ON)
##
##  create cross brace part in the assembly module
##
a = mdb.models['Model-1'].rootAssembly
session.viewports['Viewport: 1'].setValues(displayedObject=a)
##  Set coordinate system (done by default)
a.DatumCsysByDefault(CARTESIAN)
p = mdb.models['Model-1'].parts['Truss']
a.Instance(name='Truss-1', part=p, dependent=ON)
p = mdb.models['Model-1'].parts['Truss-all']
a.Instance(name='Truss-all-1', part=p, dependent=ON)
a.PartFromBooleanCut(name='Cross brace',
instanceToBeCut=a.instances['Truss-all-1'],
cuttingInstances=(a.instances['Truss-1'], ))
p = mdb.models['Model-1'].parts['Cross brace']
a.Instance(name='Cross brace-1', part=p, dependent=ON)
a.suppressFeatures(('Truss-1', 'Truss-all-1', ))
a.features['Truss-1'].resume()
p = mdb.models['Model-1'].parts['Cross brace']
session.viewports['Viewport: 1'].setValues(displayedObject=p)
##
##  Create beam profiles and beam sections
##
mdb.models['Model-1'].BoxProfile(name='MainBoxProfile', b=0.05,
a=0.1, uniformThickness=ON, t1=0.005)
mdb.models['Model-1'].BoxProfile(name='BraceBoxProfile', b=0.03,
a=0.03, uniformThickness=ON, t1=0.003)
mdb.models['Model-1'].BeamSection(name='MainMemberSection',
profile='MainBoxProfile', poissonRatio=0.25,
integration=BEFORE_ANALYSIS, table=((2.e11, 8.e10),))
mdb.models['Model-1'].BeamSection(name='BracingSection',
profile='BraceBoxProfile', poissonRatio=0.25,
integration=BEFORE_ANALYSIS, table=((2.e11, 8.e10),))
##
##  Flip tangent directions
##
##p = mdb.models['Model-1'].parts['Truss']
##e = p.edges
##edges = e
##regions = regionToolset.Region(edges=edges)
##p.flipTangent(regions=regions)
####
##edges = e.findAt(((4.5, 0.84375, 0.50625), ), ((2.5, 0.46875, 0.28125), ), ((
##    0.5, 0.09375, 0.05625), ), ((4.5, 0.84375, 1.49375), ), ((2.5, 0.46875,
##    1.71875), ), ((0.5, 0.09375, 1.94375), ))
##regions = regionToolset.Region(edges=edges)
##p.flipTangent(regions=regions)
##
##  Assign beam sections to the cross brace
##
p = mdb.models['Model-1'].parts['Cross brace']
e = p.edges
edges = e.findAt(((2.666667, 1.166667, 1.35), ),
((2.166667, 0.572917, 0.59375), ), ((2.0, 0.375, 1.3875), ),
((6.0, 1.125, 1.1625), ), ((5.5, 1.28125, 0.78125), ),
((5.333333, 1.333333, 1.2), ), ((4.333333, 0.895833, 0.6875), ),
((4.0, 0.75, 1.275), ))
region = regionToolset.Region(edges=edges)
p.SectionAssignment(region=region, sectionName='BracingSection')
##
##  Assign beam sections to the internal bracing
##
p = mdb.models['Model-1'].parts['Truss']
e = p.edges
edges = e.findAt(((3.0, 1.0625, 0.3375), ), ((5.5, 1.28125, 0.61875), ),
((4.333333, 0.895833, 0.4875), ), ((0.5, 0.84375, 0.05625), ),
((2.166667, 0.572917, 0.24375), ), ((3.0, 1.0625, 1.6625), ),
((5.5, 1.28125, 1.38125), ), ((4.333333, 0.895833, 1.5125), ),
((0.5, 0.84375, 1.94375), ), ((2.166667, 0.572917, 1.75625), ))
region = regionToolset.Region(edges=edges)
p.SectionAssignment(region=region, sectionName='BracingSection')
##
##  Assign beam sections to the main members
##
p = mdb.models['Model-1'].parts['Truss']
e = p.edges
edges = e.findAt(((4.5, 0.84375, 0.50625), ), ((4.666667, 1.291667, 0.525), ),
((6.5, 1.21875, 0.73125), ), ((7.333333, 1.458333, 0.825), ),
((2.5, 0.46875, 0.28125), ), ((2.0, 1.125, 0.225), ),
((0.5, 0.09375, 0.05625), ), ((4.5, 0.84375, 1.49375), ),
((4.666667, 1.291667, 1.475), ), ((6.5, 1.21875, 1.26875), ),
((7.333333, 1.458333, 1.175), ), ((2.5, 0.46875, 1.71875), ),
((2.0, 1.125, 1.775), ), ((0.5, 0.09375, 1.94375), ))
region = regionToolset.Region(edges=edges)
p.SectionAssignment(region=region, sectionName='MainMemberSection')
##
##  Assign beam section orientations to truss 'B'
##
p = mdb.models['Model-1'].parts['Truss']
e = p.edges
edges = e.findAt(((4.5, 0.84375, 0.50625), ), ((3.0, 1.0625, 0.3375), ),
((4.666667, 1.291667, 0.525), ), ((5.5, 1.28125, 0.61875), ),
((6.5, 1.21875, 0.73125), ), ((7.333333, 1.458333, 0.825), ),
((4.333333, 0.895833, 0.4875), ), ((2.5, 0.46875, 0.28125), ),
((0.5, 0.84375, 0.05625), ), ((2.0, 1.125, 0.225), ),
((2.166667, 0.572917, 0.24375), ), ((0.5, 0.09375, 0.05625), ))
region=regionToolset.Region(edges=edges)
p.assignBeamSectionOrientation(region=region, method=N1_COSINES, n1=(-0.1118,
0.0, 0.9936))
##
##  Assign beam section orientations to truss 'A'
##
p = mdb.models['Model-1'].parts['Truss']
e = p.edges
edges = e.findAt(((4.5, 0.84375, 1.49375), ), ((3.0, 1.0625, 1.6625), ),
((4.666667, 1.291667, 1.475), ), ((5.5, 1.28125, 1.38125), ),
((6.5, 1.21875, 1.26875), ), ((7.333333, 1.458333, 1.175), ),
((4.333333, 0.895833, 1.5125), ), ((2.5, 0.46875, 1.71875), ),
((0.5, 0.84375, 1.94375), ), ((2.0, 1.125, 1.775), ),
((2.166667, 0.572917, 1.75625), ), ((0.5, 0.09375, 1.94375), ))
region=regionToolset.Region(edges=edges)
p.assignBeamSectionOrientation(region=region, method=N1_COSINES, n1=(-0.1118,
0.0, -0.9936))
##
##  Assign beam section orientations to 'Cross brace'
##
p = mdb.models['Model-1'].parts['Cross brace']
e = p.edges
edges = e.findAt(((2.666667, 1.166667, 1.35), ), ((2.166667, 0.572917,
0.59375), ), ((2.0, 0.375, 1.3875), ), ((6.0, 1.125, 1.1625), ), ((5.5,
1.28125, 0.78125), ), ((5.333333, 1.333333, 1.2), ), ((4.333333, 0.895833,
0.6875), ), ((4.0, 0.75, 1.275), ))
region=regionToolset.Region(edges=edges)
p.assignBeamSectionOrientation(region=region, method=N1_COSINES,
n1=(0.0, 1.0, 0.0))
session.viewports['Viewport: 1'].setValues(displayedObject=a)
a.regenerate()
##
##
session.viewports['Viewport: 1'].assemblyDisplay.setValues(
visibleInstances=('Truss-1', 'Cross brace-1'))
session.viewports['Viewport: 1'].assemblyDisplay.geometryOptions.setValues(
geometryEdgesInShaded=OFF, datumPoints=OFF, datumAxes=OFF, datumPlanes=OFF,
datumCoordSystems=OFF, referencePointLabels=OFF, referencePointSymbols=OFF)
##
##  Translate the truss
##
p = a.instances['Truss-1']
p.translate(vector=(0.0, -0.5, -1.0))
##
##  Translate the cross brace
##
p = a.instances['Cross brace-1']
p.translate(vector=(0.0, -0.5, -1.0))
##
##  Create geometry sets
##
session.viewports['Viewport: 1'].assemblyDisplay.setValues(
visibleInstances=('Truss-1', ))
session.viewports['Viewport: 1'].assemblyDisplay.geometryOptions.setValues(
datumPoints=OFF)
v = a.instances['Truss-1'].vertices
verts = v.findAt(((0.0, 0.5, -1.0), ), ((0.0, -0.5, -1.0), ), ((0.0, 0.5,
1.0), ), ((0.0, -0.5, 1.0), ))
a.Set(vertices=verts, name='Attach')
verts = v.findAt(((8.0, 1.0, 0.1), ))
a.Set(vertices=verts, name='Tip-a')
verts = v.findAt(((8.0, 1.0, -0.1), ))
a.Set(vertices=verts, name='Tip-b')
e = a.instances['Truss-1'].edges
edges = e.findAt(((6.5, 0.71875, 0.26875), ))
a.Set(edges=edges, name='Leg-a')
edges = e.findAt(((6.5, 0.71875, -0.26875), ))
a.Set(edges=edges, name='Leg-b')
edges = e.findAt(((4.333333, 0.395833, 0.5125), ))
a.Set(edges=edges, name='Inner-a')
edges = e.findAt(((4.333333, 0.395833, -0.5125), ))
a.Set(edges=edges, name='Inner-b')
session.viewports['Viewport: 1'].assemblyDisplay.setValues(
visibleInstances=('Cross brace-1', ))
session.viewports['Viewport: 1'].view.setValues(
cameraPosition=(7.4736, 8.3559, 20.002),
cameraUpVector=(-0.34023, 0.72044, -0.60432))
session.viewports['Viewport: 1'].assemblyDisplay.setValues(
visibleInstances=('Truss-1', 'Cross brace-1'))
session.viewports['Viewport: 1'].view.setValues(session.views['Iso'])
##
##  Create a static general step
##
mdb.models['Model-1'].StaticStep(name='Tip load',
previous='Initial', description='Static tip load on crane',
timePeriod=1, adiabatic=OFF, maxNumInc=100,
stabilization=None, timeIncrementationMethod=AUTOMATIC, initialInc=1,
minInc=1e-05, maxInc=1, matrixSolver=SOLVER_DEFAULT, amplitude=RAMP,
extrapolation=LINEAR, fullyPlastic="")
session.viewports['Viewport: 1'].assemblyDisplay.setValues(step='Tip load')
##
##  Modify output requests
##
mdb.models['Model-1'].fieldOutputRequests['F-Output-1'].setValues(
variables=('U', 'RF', 'SF'))
mdb.models['Model-1'].historyOutputRequests['H-Output-1'].setValues(
variables=PRESELECT)
##
##  Create constraints between the tips of the truss
##
session.viewports['Viewport: 1'].assemblyDisplay.setValues(interactions=ON)
mdb.models['Model-1'].Equation(name='TipConstraint-1',
terms=((1.0, 'Tip-a', 1), (-1.0, 'Tip-b', 1)))
mdb.models['Model-1'].Constraint('TipConstraint-2',
mdb.models['Model-1'].constraints['TipConstraint-1'])
mdb.models['Model-1'].constraints['TipConstraint-2'].setValues(
terms=((1.0, 'Tip-a', 2), (-1.0, 'Tip-b', 2)))
##
##  Create JOIN connectors between truss and bracing
##
v1 = a.instances['Cross brace-1'].vertices
v2 = a.instances['Truss-1'].vertices
a.WirePolyLine(points=((v1.findAt(coordinates=(2.0, -0.125, 0.775)), v2.findAt(
coordinates=(2.0, -0.125, 0.775))), (v1.findAt(coordinates=(2.666667,
0.666667, 0.7)), v2.findAt(coordinates=(2.666667, 0.666667, 0.7))), (
v1.findAt(coordinates=(2.0, -0.125, -0.775)), v2.findAt(coordinates=(2.0,
-0.125, -0.775))), (v1.findAt(coordinates=(2.666667, 0.666667, -0.7)),
v2.findAt(coordinates=(2.666667, 0.666667, -0.7))), (v1.findAt(
coordinates=(4.0, 0.25, -0.55)), v2.findAt(coordinates=(4.0, 0.25,
-0.55))), (v1.findAt(coordinates=(4.0, 0.25, 0.55)), v2.findAt(
coordinates=(4.0, 0.25, 0.55))), (v1.findAt(coordinates=(5.333333,
0.833333, 0.4)), v2.findAt(coordinates=(5.333333, 0.833333, 0.4))), (
v1.findAt(coordinates=(5.333333, 0.833333, -0.4)), v2.findAt(coordinates=(
5.333333, 0.833333, -0.4))), (v1.findAt(coordinates=(6.0, 0.625, -0.325)),
v2.findAt(coordinates=(6.0, 0.625, -0.325))), (v1.findAt(coordinates=(6.0,
0.625, 0.325)), v2.findAt(coordinates=(6.0, 0.625, 0.325)))),
mergeType=IMPRINT, meshable=OFF)
e1 = a.edges
edges1 = e1.findAt(((6.000025, 0.625, 0.325), ), ((6.000025, 0.625, -0.325), ),
((5.333358, 0.833333, -0.4), ), ((5.333358, 0.833333, 0.4), ), ((4.000025,
0.25, 0.55), ), ((4.000025, 0.25, -0.55), ), ((2.666692, 0.666667, -0.7),
), ((2.000025, -0.125, -0.775), ), ((2.666692, 0.666667, 0.7), ), ((
2.000025, -0.125, 0.775), ))
a.Set(edges=edges1, name='Wire-1-Edge-1')
mdb.models['Model-1'].ConnectorSection(name='ConnSect-1',
translationalType=JOIN)
region=a.sets['Wire-1-Edge-1']
a.SectionAssignment(sectionName='ConnSect-1', region=region)
session.viewports['Viewport: 1'].assemblyDisplay.setValues(loads=ON, bcs=ON,
predefinedFields=ON, interactions=OFF)
##
##  Apply encastre bc to set 'Attach'
##
region = a.sets['Attach']
mdb.models['Model-1'].EncastreBC(name='Fixed end', createStepName='Tip load',
region=region)
##
##  Apply concentrated force to set 'Tip-b'
##
region = a.sets['Tip-b']
mdb.models['Model-1'].ConcentratedForce(name='Tip load',
createStepName='Tip load', region=region, cf2=-10000.0)
##
##  Assign global seed
##
p = mdb.models['Model-1'].parts['Truss']
p.seedPart(size=2.0)
p = mdb.models['Model-1'].parts['Cross brace']
p.seedPart(size=2.0)
##
##  Assign element type
##
elemType1 = mesh.ElemType(elemCode=B33)
p = mdb.models['Model-1'].parts['Cross brace']
e = p.edges
edges = e
pickedRegions =(edges, )
p.setElementType(regions=pickedRegions, elemTypes=(elemType1, ))
p = mdb.models['Model-1'].parts['Truss']
e = p.edges
edges = e
pickedRegions =(edges, )
p.setElementType(regions=pickedRegions, elemTypes=(elemType1, ))
##
##  Generate mesh
##
p = mdb.models['Model-1'].parts['Truss']
p.generateMesh()
p = mdb.models['Model-1'].parts['Cross brace']
p.generateMesh()
##
##  Add keywords
##
mdb.models['Model-1'].keywordBlock.synchVersions()
mdb.models['Model-1'].keywordBlock.insert(GetBlockPosition('Model-1', '*End Assembly')-1, """*NORMAL, TYPE=ELEMENT
Inner-a,  Inner-a, -0.3962,  0.9171,  0.0446
Inner-b,  Inner-b,  0.3962, -0.9171,  0.0446
Leg-a,    Leg-a,   -0.1820,  0.9829,  0.0205
Leg-b,    Leg-b,    0.1820, -0.9829,  0.0205""")
##
##  Create job
##
mdb.Job(name='Crane', model='Model-1',
description='3-D model of light-service cargo crane')
a.regenerate()
session.viewports['Viewport: 1'].setValues(displayedObject=a)
##
##  Save model database
##
mdb.saveAs('Crane.cae')
```

---

### A.5 Cargo crane &#8211; dynamic loading
gsi_dyncrane_caemodel.py
```
#
# Getting Started with Abaqus: Interactive Edition
#
# Script for dynamic crane example
#
def GetBlockPosition(modelName, blockPrefix):
if blockPrefix == '':
return len(mdb.models[modelName].keywordBlock.sieBlocks)-1
pos = 0
for block in mdb.models[modelName].keywordBlock.sieBlocks:
if block[0:len(blockPrefix)].lower()==blockPrefix.lower():
return pos
pos=pos+1
return -1
from abaqus import *
from abaqusConstants import *
session.viewports['Viewport: 1'].makeCurrent()
session.viewports['Viewport: 1'].maximize()
from caeModules import *
from driverUtils import executeOnCaeStartup
executeOnCaeStartup()
Mdb()
mdb.models.changeKey(fromName='Model-1', toName='standard')
##
##  Sketch profile of truss
##
p = mdb.models['standard'].Part(name='Truss', dimensionality=THREE_D,
type=DEFORMABLE_BODY)
p.ReferencePoint(point=(0.0, 0.0, 0.0))
p = mdb.models['standard'].parts['Truss']
session.viewports['Viewport: 1'].setValues(displayedObject=p)
d, r = p.datums, p.referencePoints
p.DatumPointByOffset(point=r[1], vector=(0.0, 1.0, 0.0))
p.DatumPointByOffset(point=r[1], vector=(8.0, 1.5, 0.9))
p.DatumPlaneByThreePoints(point1=r[1], point2=d[3], point3=d[2])
p.DatumAxisByPrincipalAxis(principalAxis=YAXIS)
session.viewports['Viewport: 1'].view.fitView()
t = p.MakeSketchTransform(sketchPlane=d[4], sketchUpEdge=d[5],
sketchPlaneSide=SIDE1, sketchOrientation=LEFT, origin=(0.0, 0.0, 0.0))
s = mdb.models['standard'].ConstrainedSketch(name='__profile__',
sheetSize=683.38, gridSpacing=17.08, transform=t)
g, v, d1, c = s.geometry, s.vertices, s.dimensions, s.constraints
s.setPrimaryObject(option=SUPERIMPOSE)
p = mdb.models['standard'].parts['Truss']
p.projectReferencesOntoSketch(sketch=s, filter=COPLANAR_EDGES)
session.viewports['Viewport: 1'].view.setValues(nearPlane=648.075,
farPlane=719.271, width=13.6266, height=9.28111, cameraPosition=(-71.5628,
0.978423, 679.645), cameraTarget=(4.83613, 0.978423, 0.544065))
s.Line(point1=(0.0, 0.0), point2=(8.05046582503149, 1.5))
s.CoincidentConstraint(entity1=v.findAt((0.0, 0.0)), entity2=g.findAt((0.0,
0.5)))
s.Line(point1=(8.05046582503149, 1.5), point2=(0.0, 1.0))
s.Line(point1=(0.0, 1.0), point2=(1.59409310185916, 0.297018794285658))
s.CoincidentConstraint(entity1=v.findAt((1.594093, 0.297019)),
entity2=g.findAt((4.025233, 0.75)))
s.Line(point1=(1.59409310185916, 0.297018794285658),
point2=(2.30592731982451, 1.14321701190598))
s.CoincidentConstraint(entity1=v.findAt((2.305927, 1.143217)),
entity2=g.findAt((4.025233, 1.25)))
s.Line(point1=(2.30592731982451, 1.14321701190598),
point2=(3.26033977276254, 0.607481575033539))
s.CoincidentConstraint(entity1=v.findAt((3.26034, 0.607482)),
entity2=g.findAt((4.025233, 0.75)))
s.Line(point1=(3.26033977276254, 0.607481575033539),
point2=(4.16525059699136, 1.25869624736747))
s.CoincidentConstraint(entity1=v.findAt((4.165251, 1.258696)),
entity2=g.findAt((4.025233, 1.25)))
s.Line(point1=(4.16525059699136, 1.25869624736747),
point2=(4.95150583156061, 0.922587451305882))
s.CoincidentConstraint(entity1=v.findAt((4.951506, 0.922587)),
entity2=g.findAt((4.025233, 0.75)))
s.breakCurve(curve1=g.findAt((4.025233, 0.75)),
point1=(0.733189206279801, 0.182644009590149),
curve2=g.findAt((1.95001, 0.720118)),
point2=(1.62787567272877, 0.433001518249512))
s.breakCurve(curve1=g.findAt((4.822279, 0.898509)),
point1=(2.34362044857835, 0.415118813514709),
curve2=g.findAt((2.783134, 0.875349)),
point2=(3.22040910681461, 0.701241612434387))
s.breakCurve(curve1=g.findAt((5.655403, 1.053741)),
point1=(4.04351950354929, 0.772772312164307),
curve2=g.findAt((4.558378, 1.090642)),
point2=(5.02767302451382, 0.95159912109375))
s.breakCurve(curve1=g.findAt((4.025233, 1.25)),
point1=(1.55629884485765, 1.09466052055359),
curve2=g.findAt((1.95001, 0.720118)),
point2=(2.32572264036564, 1.02312982082367))
s.breakCurve(curve1=g.findAt((5.178197, 1.321609)),
point1=(3.79300780849022, 1.23772192001343),
curve2=g.findAt((3.712795, 0.933089)),
point2=(4.168774592922, 1.18407392501831))
s.VerticalDimension(vertex1=v.findAt((0.0, 1.0)),
vertex2=v.findAt((0.0, 0.0)),
textPoint=(-0.304643334343144, 0.0216999053955078), value=1.0)
s.HorizontalDimension(vertex1=v.findAt((0.0, 0.0)),
vertex2=v.findAt((8.050466, 1.5)),
textPoint=(6.26233672422377, -0.443249702453613), value=8.05046582503149)
s.ParallelConstraint(entity1=g.findAt((1.152964, 1.071609)), entity2=g.findAt((
3.235589, 1.200957)))
s.ParallelConstraint(entity1=g.findAt((3.235589, 1.200957)), entity2=g.findAt((
6.107858, 1.379348)))
s.ParallelConstraint(entity1=g.findAt((0.797047, 0.148509)), entity2=g.findAt((
2.427216, 0.45225)))
s.ParallelConstraint(entity1=g.findAt((2.427216, 0.45225)), entity2=g.findAt((
4.105923, 0.765035)))
s.ParallelConstraint(entity1=g.findAt((4.105923, 0.765035)), entity2=g.findAt((
6.500986, 1.211294)))
s.EqualLengthConstraint(entity1=g.findAt((0.797047, 0.148509)),
entity2=g.findAt((2.427216, 0.45225)))
s.EqualLengthConstraint(entity1=g.findAt((2.39114, 0.445528)),
entity2=g.findAt((4.033769, 0.751591)))
s.EqualLengthConstraint(entity1=g.findAt((3.985233, 0.742547)),
entity2=g.findAt((6.416373, 1.195528)))
s.EqualLengthConstraint(entity1=g.findAt((1.152964, 1.071609)),
entity2=g.findAt((3.235589, 1.200957)))
s.EqualLengthConstraint(entity1=g.findAt((3.458891, 1.214826)),
entity2=g.findAt((6.33116, 1.393217)))
mdb.models['standard'].ConstrainedSketch(name='Truss', objectToCopy=s)
p = mdb.models['standard'].parts['Truss']
d = p.datums
p.Wire(sketchPlane=d[4], sketchUpEdge=d[5], sketchPlaneSide=SIDE1,
sketchOrientation=LEFT, sketch=s)
s.unsetPrimaryObject()
del mdb.models['standard'].sketches['__profile__']
session.viewports['Viewport: 1'].view.fitView()
p = mdb.models['standard'].parts['Truss']
d, r = p.datums, p.referencePoints
p.DatumPointByOffset(point=d[2], vector=(0.0, 0.0, 2.0))
p.DatumPointByOffset(point=r[1], vector=(0.0, 0.0, 2.0))
p.DatumPointByOffset(point=d[3], vector=(0.0, 0.0, 0.2))
p.DatumPlaneByThreePoints(point1=d[8], point2=d[9], point3=d[7])
t = p.MakeSketchTransform(sketchPlane=d[10], sketchUpEdge=d[5],
sketchPlaneSide=SIDE1, sketchOrientation=LEFT, origin=(4.122203, 0.75,
1.536252))
s = mdb.models['standard'].ConstrainedSketch(name='__profile__',
sheetSize=683.38, gridSpacing=17.08, transform=t)
g, v, d, c = s.geometry, s.vertices, s.dimensions, s.constraints
s.setPrimaryObject(option=SUPERIMPOSE)
p.projectReferencesOntoSketch(sketch=s, filter=COPLANAR_EDGES)
s.retrieveSketch(sketch=mdb.models['standard'].sketches['Truss'])
s.move(vector=(-4.14820681508444, -0.75), objectList=(g.findAt((0.0, 0.5)),
g.findAt((1.006308, 0.6875)), g.findAt((2.348053, 0.770833)), g.findAt((
3.354361, 0.958333)), g.findAt((4.696105, 1.041667)), g.findAt((5.702413,
1.229167)), g.findAt((1.006308, 0.1875)), g.findAt((3.018925, 0.5625)),
g.findAt((5.031541, 0.9375)), g.findAt((7.044158, 1.3125)), g.findAt((
1.341744, 1.083333)), g.findAt((6.708722, 1.416667)), g.findAt((4.025233,
1.25)), v.findAt((8.050466, 1.5)), v.findAt((0.0, 1.0))))
d = p.datums
p.Wire(sketchPlane=d[10], sketchUpEdge=d[5], sketchPlaneSide=SIDE1,
sketchOrientation=LEFT, sketch=s)
s.unsetPrimaryObject()
del mdb.models['standard'].sketches['__profile__']
##
##  dummy part
##
p = mdb.models['standard'].Part(name='Truss-all',
objectToCopy=mdb.models['standard'].parts['Truss'])
session.viewports['Viewport: 1'].setValues(displayedObject=p)
v = p.vertices
p.WirePolyLine(points=((v.findAt(coordinates=(2.0, 0.375, 1.775)), v.findAt(
coordinates=(2.0, 0.375, 0.225))), (v.findAt(coordinates=(2.0, 0.375,
0.225)), v.findAt(coordinates=(2.666667, 1.166667, 1.7))), (v.findAt(
coordinates=(2.666667, 1.166667, 1.7)), v.findAt(coordinates=(2.666667,
1.166667, 0.3))), (v.findAt(coordinates=(4.0, 0.75, 1.55)), v.findAt(
coordinates=(4.0, 0.75, 0.45))), (v.findAt(coordinates=(4.0, 0.75, 0.45)),
v.findAt(coordinates=(5.333333, 1.333333, 1.4))), (v.findAt(coordinates=(
5.333333, 1.333333, 1.4)), v.findAt(coordinates=(5.333333, 1.333333,
0.6))), (v.findAt(coordinates=(5.333333, 1.333333, 0.6)), v.findAt(
coordinates=(6.0, 1.125, 1.325))), (v.findAt(coordinates=(6.0, 1.125,
1.325)), v.findAt(coordinates=(6.0, 1.125, 0.675)))), mergeType=IMPRINT,
meshable=ON)
##
##  create cross brace part in the assembly module
##
a = mdb.models['standard'].rootAssembly
session.viewports['Viewport: 1'].setValues(displayedObject=a)
##  Set coordinate system (done by default)
a.DatumCsysByDefault(CARTESIAN)
p = mdb.models['standard'].parts['Truss']
a.Instance(name='Truss-1', part=p, dependent=ON)
p = mdb.models['standard'].parts['Truss-all']
a.Instance(name='Truss-all-1', part=p, dependent=ON)
a.PartFromBooleanCut(name='Cross brace',
instanceToBeCut=a.instances['Truss-all-1'],
cuttingInstances=(a.instances['Truss-1'], ))
p = mdb.models['standard'].parts['Cross brace']
a.Instance(name='Cross brace-1', part=p, dependent=ON)
a.suppressFeatures(('Truss-1', 'Truss-all-1', ))
a.features['Truss-1'].resume()
p = mdb.models['standard'].parts['Cross brace']
session.viewports['Viewport: 1'].setValues(displayedObject=p)
##
##  Create beam profiles and beam sections
##
mdb.models['standard'].BoxProfile(name='MainBoxProfile', b=0.05,
a=0.1, uniformThickness=ON, t1=0.005)
mdb.models['standard'].BoxProfile(name='BraceBoxProfile', b=0.03,
a=0.03, uniformThickness=ON, t1=0.003)
mdb.models['standard'].BeamSection(name='MainMemberSection',
profile='MainBoxProfile', poissonRatio=0.25,
integration=BEFORE_ANALYSIS, table=((2.e11, 8.e10),))
mdb.models['standard'].sections['MainMemberSection'].setValues(density=7800.0)
mdb.models['standard'].BeamSection(name='BracingSection',
profile='BraceBoxProfile', poissonRatio=0.25,
integration=BEFORE_ANALYSIS, table=((2.e11, 8.e10),))
mdb.models['standard'].sections['BracingSection'].setValues(density=7800.0)
##
##  Flip tangent directions
##
##p = mdb.models['standard'].parts['Truss']
##e = p.edges
##edges = e
##regions = regionToolset.Region(edges=edges)
##p.flipTangent(regions=regions)
####
##edges = e.findAt(((4.5, 0.84375, 0.50625), ), ((2.5, 0.46875, 0.28125), ), ((
##    0.5, 0.09375, 0.05625), ), ((4.5, 0.84375, 1.49375), ), ((2.5, 0.46875,
##    1.71875), ), ((0.5, 0.09375, 1.94375), ))
##regions = regionToolset.Region(edges=edges)
##p.flipTangent(regions=regions)
##
##  Assign beam sections to the cross brace
##
p = mdb.models['standard'].parts['Cross brace']
e = p.edges
edges = e.findAt(((2.666667, 1.166667, 1.35), ),
((2.166667, 0.572917, 0.59375), ), ((2.0, 0.375, 1.3875), ),
((6.0, 1.125, 1.1625), ), ((5.5, 1.28125, 0.78125), ),
((5.333333, 1.333333, 1.2), ), ((4.333333, 0.895833, 0.6875), ),
((4.0, 0.75, 1.275), ))
region = regionToolset.Region(edges=edges)
p.SectionAssignment(region=region, sectionName='BracingSection')
##
##  Assign beam sections to the internal bracing
##
p = mdb.models['standard'].parts['Truss']
e = p.edges
edges = e.findAt(((3.0, 1.0625, 0.3375), ), ((5.5, 1.28125, 0.61875), ),
((4.333333, 0.895833, 0.4875), ), ((0.5, 0.84375, 0.05625), ),
((2.166667, 0.572917, 0.24375), ), ((3.0, 1.0625, 1.6625), ),
((5.5, 1.28125, 1.38125), ), ((4.333333, 0.895833, 1.5125), ),
((0.5, 0.84375, 1.94375), ), ((2.166667, 0.572917, 1.75625), ))
region = regionToolset.Region(edges=edges)
p.SectionAssignment(region=region, sectionName='BracingSection')
##
##  Assign beam sections to the main members
##
p = mdb.models['standard'].parts['Truss']
e = p.edges
edges = e.findAt(((4.5, 0.84375, 0.50625), ), ((4.666667, 1.291667, 0.525), ),
((6.5, 1.21875, 0.73125), ), ((7.333333, 1.458333, 0.825), ),
((2.5, 0.46875, 0.28125), ), ((2.0, 1.125, 0.225), ),
((0.5, 0.09375, 0.05625), ), ((4.5, 0.84375, 1.49375), ),
((4.666667, 1.291667, 1.475), ), ((6.5, 1.21875, 1.26875), ),
((7.333333, 1.458333, 1.175), ), ((2.5, 0.46875, 1.71875), ),
((2.0, 1.125, 1.775), ), ((0.5, 0.09375, 1.94375), ))
region = regionToolset.Region(edges=edges)
p.SectionAssignment(region=region, sectionName='MainMemberSection')
##
##  Assign beam section orientations to truss 'B'
##
p = mdb.models['standard'].parts['Truss']
e = p.edges
edges = e.findAt(((4.5, 0.84375, 0.50625), ), ((3.0, 1.0625, 0.3375), ),
((4.666667, 1.291667, 0.525), ), ((5.5, 1.28125, 0.61875), ),
((6.5, 1.21875, 0.73125), ), ((7.333333, 1.458333, 0.825), ),
((4.333333, 0.895833, 0.4875), ), ((2.5, 0.46875, 0.28125), ),
((0.5, 0.84375, 0.05625), ), ((2.0, 1.125, 0.225), ),
((2.166667, 0.572917, 0.24375), ), ((0.5, 0.09375, 0.05625), ))
region=regionToolset.Region(edges=edges)
p.assignBeamSectionOrientation(region=region, method=N1_COSINES, n1=(-0.1118,
0.0, 0.9936))
##
##  Assign beam section orientations to truss 'A'
##
p = mdb.models['standard'].parts['Truss']
e = p.edges
edges = e.findAt(((4.5, 0.84375, 1.49375), ), ((3.0, 1.0625, 1.6625), ),
((4.666667, 1.291667, 1.475), ), ((5.5, 1.28125, 1.38125), ),
((6.5, 1.21875, 1.26875), ), ((7.333333, 1.458333, 1.175), ),
((4.333333, 0.895833, 1.5125), ), ((2.5, 0.46875, 1.71875), ),
((0.5, 0.84375, 1.94375), ), ((2.0, 1.125, 1.775), ),
((2.166667, 0.572917, 1.75625), ), ((0.5, 0.09375, 1.94375), ))
region=regionToolset.Region(edges=edges)
p.assignBeamSectionOrientation(region=region, method=N1_COSINES, n1=(-0.1118,
0.0, -0.9936))
##
##  Assign beam section orientations to 'Cross brace'
##
p = mdb.models['standard'].parts['Cross brace']
e = p.edges
edges = e.findAt(((2.666667, 1.166667, 1.35), ), ((2.166667, 0.572917,
0.59375), ), ((2.0, 0.375, 1.3875), ), ((6.0, 1.125, 1.1625), ), ((5.5,
1.28125, 0.78125), ), ((5.333333, 1.333333, 1.2), ), ((4.333333, 0.895833,
0.6875), ), ((4.0, 0.75, 1.275), ))
region=regionToolset.Region(edges=edges)
p.assignBeamSectionOrientation(region=region, method=N1_COSINES,
n1=(0.0, 1.0, 0.0))
session.viewports['Viewport: 1'].setValues(displayedObject=a)
a.regenerate()
##
##
session.viewports['Viewport: 1'].assemblyDisplay.setValues(
visibleInstances=('Truss-1', 'Cross brace-1'))
session.viewports['Viewport: 1'].assemblyDisplay.geometryOptions.setValues(
geometryEdgesInShaded=OFF, datumPoints=OFF, datumAxes=OFF, datumPlanes=OFF,
datumCoordSystems=OFF, referencePointLabels=OFF, referencePointSymbols=OFF)
##
##  Translate the truss
##
p = a.instances['Truss-1']
p.translate(vector=(0.0, -0.5, -1.0))
##
##  Translate the cross brace
##
p = a.instances['Cross brace-1']
p.translate(vector=(0.0, -0.5, -1.0))
##
##  Create geometry sets
##
session.viewports['Viewport: 1'].assemblyDisplay.setValues(
visibleInstances=('Truss-1', ))
session.viewports['Viewport: 1'].assemblyDisplay.geometryOptions.setValues(
datumPoints=OFF)
v = a.instances['Truss-1'].vertices
verts = v.findAt(((0.0, 0.5, -1.0), ), ((0.0, -0.5, -1.0), ), ((0.0, 0.5,
1.0), ), ((0.0, -0.5, 1.0), ))
a.Set(vertices=verts, name='Attach')
verts = v.findAt(((8.0, 1.0, 0.1), ))
a.Set(vertices=verts, name='Tip-a')
verts = v.findAt(((8.0, 1.0, -0.1), ))
a.Set(vertices=verts, name='Tip-b')
e = a.instances['Truss-1'].edges
edges = e.findAt(((6.5, 0.71875, 0.26875), ))
a.Set(edges=edges, name='Leg-a')
edges = e.findAt(((6.5, 0.71875, -0.26875), ))
a.Set(edges=edges, name='Leg-b')
edges = e.findAt(((4.333333, 0.395833, 0.5125), ))
a.Set(edges=edges, name='Inner-a')
edges = e.findAt(((4.333333, 0.395833, -0.5125), ))
a.Set(edges=edges, name='Inner-b')
session.viewports['Viewport: 1'].assemblyDisplay.setValues(
visibleInstances=('Cross brace-1', ))
session.viewports['Viewport: 1'].view.setValues(
cameraPosition=(7.4736, 8.3559, 20.002),
cameraUpVector=(-0.34023, 0.72044, -0.60432))
session.viewports['Viewport: 1'].assemblyDisplay.setValues(
visibleInstances=('Truss-1', 'Cross brace-1'))
session.viewports['Viewport: 1'].view.setValues(session.views['Iso'])
##
##  Create a frequency extraction step
##
mdb.models['standard'].FrequencyStep(name='Extract frequencies',
previous='Initial',
description='First 30 modes', numEigen=30,
maxEigen=None, shift=None, eigensolver=LANCZOS, minEigen=None,
blockSize=DEFAULT, maxBlocks=DEFAULT)
session.viewports['Viewport: 1'].assemblyDisplay.setValues(
step='Extract frequencies')
##
##  Create a modal dynamics step
##
mdb.models['standard'].ModalDynamicsStep(name='Transient modal dynamics',
previous='Extract frequencies',
description='Crane Response to Dropped Load',
continueAnalysis=OFF, timePeriod=0.5, incSize=0.005, directDamping=((1,
30, 0.05), ), compositeDamping=None, rayleighDamping=None, amplitude=STEP)
session.viewports['Viewport: 1'].assemblyDisplay.setValues(
step='Transient modal dynamics')
##
##  Modify output requests
##
mdb.models['standard'].fieldOutputRequests['F-Output-2'].setValues(
variables=('U', ), frequency=5)
mdb.models['standard'].historyOutputRequests['H-Output-1'].setValues(
variables=('ALLIE', 'ALLKE', 'ALLVD'), frequency=1)
a0=mdb.models['standard'].rootAssembly
regionDef=a0.sets['Tip-a']
mdb.models['standard'].HistoryOutputRequest(name='H-Output-2',
createStepName='Transient modal dynamics',
variables=('U1', 'U2', 'U3'),
region=regionDef, frequency=1)
a0=mdb.models['standard'].rootAssembly
regionDef=a0.sets['Attach']
mdb.models['standard'].HistoryOutputRequest(name='H-Output-3',
createStepName='Transient modal dynamics',
variables=('RF1', 'RF2', 'RF3'),
region=regionDef, frequency=1)
##
##  Create constraints between the tips of the truss
##
session.viewports['Viewport: 1'].assemblyDisplay.setValues(interactions=ON)
mdb.models['standard'].Equation(name='TipConstraint-1',
terms=((1.0, 'Tip-a', 1), (-1.0, 'Tip-b', 1)))
mdb.models['standard'].Constraint('TipConstraint-2',
mdb.models['standard'].constraints['TipConstraint-1'])
mdb.models['standard'].constraints['TipConstraint-2'].setValues(
terms=((1.0, 'Tip-a', 2), (-1.0, 'Tip-b', 2)))
##
##  Create JOIN connectors between truss and bracing
##
v1 = a.instances['Cross brace-1'].vertices
v2 = a.instances['Truss-1'].vertices
a.WirePolyLine(points=((v1.findAt(coordinates=(2.0, -0.125, 0.775)), v2.findAt(
coordinates=(2.0, -0.125, 0.775))), (v1.findAt(coordinates=(2.666667,
0.666667, 0.7)), v2.findAt(coordinates=(2.666667, 0.666667, 0.7))), (
v1.findAt(coordinates=(2.0, -0.125, -0.775)), v2.findAt(coordinates=(2.0,
-0.125, -0.775))), (v1.findAt(coordinates=(2.666667, 0.666667, -0.7)),
v2.findAt(coordinates=(2.666667, 0.666667, -0.7))), (v1.findAt(
coordinates=(4.0, 0.25, -0.55)), v2.findAt(coordinates=(4.0, 0.25,
-0.55))), (v1.findAt(coordinates=(4.0, 0.25, 0.55)), v2.findAt(
coordinates=(4.0, 0.25, 0.55))), (v1.findAt(coordinates=(5.333333,
0.833333, 0.4)), v2.findAt(coordinates=(5.333333, 0.833333, 0.4))), (
v1.findAt(coordinates=(5.333333, 0.833333, -0.4)), v2.findAt(coordinates=(
5.333333, 0.833333, -0.4))), (v1.findAt(coordinates=(6.0, 0.625, -0.325)),
v2.findAt(coordinates=(6.0, 0.625, -0.325))), (v1.findAt(coordinates=(6.0,
0.625, 0.325)), v2.findAt(coordinates=(6.0, 0.625, 0.325)))),
mergeType=IMPRINT, meshable=OFF)
e1 = a.edges
edges1 = e1.findAt(((6.000025, 0.625, 0.325), ), ((6.000025, 0.625, -0.325), ),
((5.333358, 0.833333, -0.4), ), ((5.333358, 0.833333, 0.4), ), ((4.000025,
0.25, 0.55), ), ((4.000025, 0.25, -0.55), ), ((2.666692, 0.666667, -0.7),
), ((2.000025, -0.125, -0.775), ), ((2.666692, 0.666667, 0.7), ), ((
2.000025, -0.125, 0.775), ))
a.Set(edges=edges1, name='Wire-1-Edge-1')
mdb.models['standard'].ConnectorSection(name='ConnSect-1',
translationalType=JOIN)
region=a.sets['Wire-1-Edge-1']
a.SectionAssignment(sectionName='ConnSect-1', region=region)
session.viewports['Viewport: 1'].assemblyDisplay.setValues(loads=ON, bcs=ON,
predefinedFields=ON, interactions=OFF)
##
##  Apply encastre bc to set 'Attach'
##
session.viewports['Viewport: 1'].assemblyDisplay.setValues(
step='Extract frequencies')
a = mdb.models['standard'].rootAssembly
region = a.sets['Attach']
mdb.models['standard'].EncastreBC(name='Fixed end',
createStepName='Extract frequencies', region=region)
##
##  Create amplitude curve 'Bounce'
##
session.viewports['Viewport: 1'].assemblyDisplay.setValues(
step='Transient modal dynamics')
mdb.models['standard'].TabularAmplitude(name='Bounce', timeSpan=STEP,
smooth=0.25, data=((0.0, 0.0), (0.01, 1.0), (0.2, 1.0), (0.21, 0.0)))
##
##  Apply concentrated force to set 'Tip-b'
##
a = mdb.models['standard'].rootAssembly
region = a.sets['Tip-b']
mdb.models['standard'].ConcentratedForce(name='Tip load',
createStepName='Transient modal dynamics', region=region, cf2=-10000.0,
amplitude='Bounce')
##
##  Assign global seed
##
p = mdb.models['standard'].parts['Truss']
p.seedPart(size=2.0)
p = mdb.models['standard'].parts['Cross brace']
p.seedPart(size=2.0)
##
##  Assign element type
##
elemType1 = mesh.ElemType(elemCode=B33)
p = mdb.models['standard'].parts['Cross brace']
e = p.edges
edges = e
pickedRegions =(edges, )
p.setElementType(regions=pickedRegions, elemTypes=(elemType1, ))
p = mdb.models['standard'].parts['Truss']
e = p.edges
edges = e
pickedRegions =(edges, )
p.setElementType(regions=pickedRegions, elemTypes=(elemType1, ))
##
##  Generate mesh
##
p = mdb.models['standard'].parts['Truss']
p.generateMesh()
p = mdb.models['standard'].parts['Cross brace']
p.generateMesh()
##
##  Add keywords
##
mdb.models['standard'].keywordBlock.synchVersions()
mdb.models['standard'].keywordBlock.insert(GetBlockPosition('standard', '*End Assembly')-1, """*NORMAL, TYPE=ELEMENT
Inner-a,  Inner-a, -0.3962,  0.9171,  0.0446
Inner-b,  Inner-b,  0.3962, -0.9171,  0.0446
Leg-a,    Leg-a,   -0.1820,  0.9829,  0.0205
Leg-b,    Leg-b,    0.1820, -0.9829,  0.0205""")
##
##  Create job
##
mdb.Job(name='DynCrane', model='standard',
description='3-D model of light-service cargo crane')
a = mdb.models['standard'].rootAssembly
a.regenerate()
##
##  Save model database
##
mdb.saveAs('DynCrane.cae')
mdb.Model(name='explicit', objectToCopy=mdb.models['standard'])
a = mdb.models['explicit'].rootAssembly
session.viewports['Viewport: 1'].setValues(displayedObject=a)
##
##  delete modal dynamics step
##
del mdb.models['explicit'].steps['Transient modal dynamics']
##
##  replace frequency extraction step with explicit dynamics step
##
mdb.models['explicit'].ExplicitDynamicsStep(name='Extract frequencies',
previous='Initial', maintainAttributes=True, timePeriod=0.5, nlgeom=OFF)
##
##  rename explicit dynamics step
##
mdb.models['explicit'].steps.changeKey(fromName='Extract frequencies',
toName='Transient dynamics')
##
##  Redefine history output
##
regionDef=mdb.models['explicit'].rootAssembly.sets['Tip-a']
mdb.models['explicit'].HistoryOutputRequest(name='H-Output-2',
createStepName='Transient dynamics', variables=('U1', 'U2', 'U3'),
region=regionDef, sectionPoints=DEFAULT, rebar=EXCLUDE)
regionDef=mdb.models['explicit'].rootAssembly.sets['Attach']
mdb.models['explicit'].HistoryOutputRequest(name='H-Output-3',
createStepName='Transient dynamics', variables=('RF1', 'RF2', 'RF3'),
region=regionDef, sectionPoints=DEFAULT, rebar=EXCLUDE)
##
##  Add mass proportional damping
##
mdb.models['explicit'].sections['BracingSection'].setValues(poissonRatio=0.0,
density=7800.0, thermalExpansion=OFF, temperatureDependency=OFF,
dependencies=0, table=((2.e11, 8.e10), ),
alphaDamping=15.0, betaDamping=0.0, compositeDamping=0.0, centroid=(0.0,
0.0), shearCenter=(0.0, 0.0))
mdb.models['explicit'].sections['MainMemberSection'].setValues(
poissonRatio=0.0, density=7800.0, thermalExpansion=OFF,
temperatureDependency=OFF, dependencies=0, table=((2.e11,
8.e10), ), alphaDamping=15.0, betaDamping=0.0,
compositeDamping=0.0, centroid=(0.0, 0.0), shearCenter=(0.0, 0.0))
##
##  Redefine tip load
##
a = mdb.models['explicit'].rootAssembly
region = a.sets['Tip-b']
mdb.models['explicit'].ConcentratedForce(name='Load-1',
createStepName='Transient dynamics', region=region, cf2=-10000.0,
amplitude='Bounce', localCsys=None)
##
##  Change element library
##
elemType1 = mesh.ElemType(elemCode=B31, elemLibrary=EXPLICIT)
p = mdb.models['explicit'].parts['Cross brace']
e = p.edges
edges = e
pickedRegions =(edges, )
p.setElementType(regions=pickedRegions, elemTypes=(elemType1, ))
p = mdb.models['explicit'].parts['Truss']
elemType1 = mesh.ElemType(elemCode=B31, elemLibrary=EXPLICIT)
e = p.edges
edges = e
pickedRegions =(edges, )
p.setElementType(regions=pickedRegions, elemTypes=(elemType1, ))
a = mdb.models['explicit'].rootAssembly
a.regenerate()
##
##  Create explicit job
##
mdb.Job(name='expDynCrane', model='explicit', type=ANALYSIS)
a = mdb.models['standard'].rootAssembly
a.regenerate()
a = mdb.models['explicit'].rootAssembly
a.regenerate()
session.viewports['Viewport: 1'].setValues(displayedObject=a)
mdb.save()
```

---

### A.6 Nonlinear skew plate
gsi_nlskewplate_caemodel.py
```
#
# Getting Started with Abaqus: Interactive Edition
#
# Script for nonlinear skew plate example
#
from abaqus import *
from abaqusConstants import *
session.viewports['Viewport: 1'].makeCurrent()
session.viewports['Viewport: 1'].maximize()
session.journalOptions.setValues(replayGeometry=COORDINATE,
recoverGeometry=COORDINATE)
from caeModules import *
from driverUtils import executeOnCaeStartup
executeOnCaeStartup()
Mdb()
##
##  Sketch profile of the plate
##
s = mdb.models['Model-1'].ConstrainedSketch(name='__profile__', sheetSize=4.0)
g, v, d, c = s.geometry, s.vertices, s.dimensions, s.constraints
s.setPrimaryObject(option=STANDALONE)
s.rectangle(point1=(-0.275, 0.25), point2=(0.575, -0.25))
s.delete(objectList=(c[18], c[19], c[20], c[21], c[22]))
s.VerticalConstraint(entity=g.findAt((-0.275, 0.0)))
s.VerticalConstraint(entity=g.findAt((0.575, 0.0)))
s.ParallelConstraint(entity1=g.findAt((0.15, -0.25)), entity2=g.findAt((0.15,
0.25)))
s.ObliqueDimension(vertex1=v.findAt((-0.275, 0.25)), vertex2=v.findAt((-0.275,
-0.25)), textPoint=(-0.384168207645416, -0.039074968546629), value=0.4)
s.HorizontalDimension(vertex1=v.findAt((-0.275, -0.25)), vertex2=v.findAt((
0.575, -0.25)), textPoint=(0.502545475959778, -0.405263155698776),
value=1.0)
s.AngularDimension(line1=g.findAt((-0.275, -0.05)), line2=g.findAt((0.225,
-0.25)), textPoint=(-0.221120104193687, -0.173046261072159), value=60.0)
session.viewports['Viewport: 1'].view.fitView()
s.move(vector=(-0.725, 0.05), objectList=(g.findAt((-0.275, -0.05)), g.findAt((
0.225, 0.038675)), g.findAt((0.725, 0.52735)), g.findAt((0.225,
0.438675))))
p = mdb.models['Model-1'].Part(name='Plate', dimensionality=THREE_D,
type=DEFORMABLE_BODY)
p = mdb.models['Model-1'].parts['Plate']
p.BaseShell(sketch=s)
s.unsetPrimaryObject()
p = mdb.models['Model-1'].parts['Plate']
session.viewports['Viewport: 1'].setValues(displayedObject=p)
del mdb.models['Model-1'].sketches['__profile__']
##
##  Create material 'Metal'
##
mdb.models['Model-1'].Material('Metal')
mdb.models['Model-1'].materials['Metal'].Elastic(table=((30.0E9, 0.3), ))
##
##  Create shell section
##
mdb.models['Model-1'].HomogeneousShellSection(name='PlateSection',
preIntegrate=ON,
material='Metal', thickness=0.008,
poissonDefinition=DEFAULT, temperature=GRADIENT)
##
##  Create datum coordinate system
##
p1 = mdb.models['Model-1'].parts['Plate']
e = p1.edges
p1.DatumCsysByTwoLines(CARTESIAN, line1=e.findAt((-0.75,
-0.0556624327025937, 0.0), ), line2=e.findAt((0.0,
0.477350269189625, 0.0), ))
##
##  Assign material orientation to the plate
##
p0 = mdb.models['Model-1'].parts['Plate']
f = p0.faces
faces = f[0:1]
region=(None, None,
f.findAt(((-0.666666666666667,
0.125783423063208, 0.0), (0.0, 0.0, 1.0)), ), None)
datum = p0.datums[2]
p0.MaterialOrientation(region=region, localCsys=datum, axis=AXIS_3)
##
##  Assign section to the plate
##
p0 = mdb.models['Model-1'].parts['Plate']
f = p0.faces
faces = f[0:1]
region=(None, None,
f.findAt(((-0.666666666666667,
0.125783423063208, 0.0), (0.0, 0.0, 1.0)), ), None)
p0 = mdb.models['Model-1'].parts['Plate']
p0.SectionAssignment(region=region, sectionName='PlateSection')
a = mdb.models['Model-1'].rootAssembly
session.viewports['Viewport: 1'].setValues(displayedObject=a)
##
##  Set coordinate system (done by default)
##
a = mdb.models['Model-1'].rootAssembly
a.DatumCsysByDefault(CARTESIAN)
##
##  Instance the plate
##
p = mdb.models['Model-1'].parts['Plate']
a.Instance(name='Plate-1', part=p, dependent=ON)
##
##  Partition the plate
##
p = mdb.models['Model-1'].parts['Plate']
c, f, e, v, d  = p.cells, p.faces, p.edges, p.vertices, p.datums
faces=(f.findAt((
-0.666666666666667, 0.125783423063208, 0.0), (0.0, 0.0, 1.0)), )
p.PartitionFaceByShortestPath(faces=faces,
point1=p.InterestingPoint(e.findAt((-0.75,
-0.0556624327025937, 0.0), ), MIDDLE),
point2=p.InterestingPoint(e.findAt((-0.25,
0.63301270189222, 0.0), ), MIDDLE))
c, f, e, v, d  = p.cells, p.faces, p.edges, p.vertices, p.datums
##
##  Create geometry set 'MidSpan'
##
a = mdb.models['Model-1'].rootAssembly
e1 = a.instances['Plate-1'].edges
a.Set(edges=e1.findAt((
(-0.5, 0.188675134594813, 0.0), ), ), name='MidSpan')
##
##  Create geometry set 'EndA'
##
a = mdb.models['Model-1'].rootAssembly
e1 = a.instances['Plate-1'].edges
a.Set(edges=e1.findAt((
(-1.0, 0.1, 0.0), ), ), name='EndA')
##
##  Create geometry set 'EndB'
##
a = mdb.models['Model-1'].rootAssembly
e1 = a.instances['Plate-1'].edges
a.Set(edges=e1.findAt((
(0.0, 0.477350269189625, 0.0), ), ), name='EndB')
##
##  Create a static general step
##
mdb.models['Model-1'].StaticStep(name='Apply pressure',
previous='Initial',
description='Nonlinear analysis: Uniform pressure (20 kPa) load',
timePeriod=1, adiabatic=OFF, maxNumInc=100,
stabilization=None, timeIncrementationMethod=AUTOMATIC, initialInc=0.1,
minInc=1e-05, maxInc=1, matrixSolver=SOLVER_DEFAULT, amplitude=RAMP,
extrapolation=LINEAR, fullyPlastic="", nlgeom=ON)
session.viewports['Viewport: 1'].assemblyDisplay.setValues(
step='Apply pressure')
##
##  Modify output requests
##
mdb.models['Model-1'].fieldOutputRequests['F-Output-1'].setValues(
variables=PRESELECT, frequency=2)
a0=mdb.models['Model-1'].rootAssembly
regionDef=a0.sets['MidSpan']
mdb.models['Model-1'].historyOutputRequests['H-Output-1'].setValues(
variables=('U3',), region=regionDef)
session.viewports['Viewport: 1'].assemblyDisplay.setValues(loads=ON, bcs=ON,
predefinedFields=ON)
##
##  Apply bc in local CSYS to set EndB (right edge)
##
a0 = mdb.models['Model-1'].rootAssembly
region = a0.sets['EndB']
datum = mdb.models['Model-1'].rootAssembly.instances['Plate-1'].datums[2]
mdb.models['Model-1'].DisplacementBC(name='Rail boundary condition',
createStepName='Apply pressure', region=region, u2=0.0, u3=0.0, ur1=0.0,
ur2=0.0, ur3=0.0, localCsys=datum)
##
##  Apply encastre bc to set EndA (left edge)
##
a0 = mdb.models['Model-1'].rootAssembly
region = a0.sets['EndA']
mdb.models['Model-1'].EncastreBC(name='Fix left end',
createStepName='Apply pressure', region=region)
##
##  Apply pressure load
##
a0 = mdb.models['Model-1'].rootAssembly
f1 = a0.instances['Plate-1'].faces
region=((
f1.findAt(((
-0.666666666666667, 0.259116756396542, 0.0), (0.0, 0.0, 1.0)), ((
-0.333333333333333, 0.318233512793084, 0.0), (0.0, 0.0, 1.0)), ), SIDE1),
)
mdb.models['Model-1'].Pressure(name='Pressure',
createStepName='Apply pressure', region=region, magnitude=2.0E4)
session.viewports['Viewport: 1'].assemblyDisplay.setValues(mesh=ON, loads=OFF,
bcs=OFF, predefinedFields=OFF)
session.viewports['Viewport: 1'].assemblyDisplay.meshOptions.setValues(
meshTechnique=ON)
##
##  Assign global seed
##
p.seedPart(size=0.1)
##
##  Use structured meshing
##
f1 = p.faces
regions=(
f1.findAt((
-0.666666666666667, 0.259116756396542, 0.0), (0.0, 0.0, 1.0)),
f1.findAt((
-0.333333333333333, 0.318233512793084, 0.0), (0.0, 0.0, 1.0)))
p.setMeshControls(regions=regions, technique=STRUCTURED)
##
##  Assign element type
##
elemType1 = mesh.ElemType(elemCode=S8R5)
elemType2 = mesh.ElemType(elemCode=STRI65)
regions=(None, None,
f1.findAt(((
-0.666666666666667, 0.259116756396542, 0.0), (0.0, 0.0, 1.0)), ((
-0.333333333333333, 0.318233512793084, 0.0), (0.0, 0.0, 1.0)), ), None)
p.setElementType(regions=regions, elemTypes=(elemType1, elemType2))
##
##  Generate mesh
##
p.generateMesh()
session.viewports['Viewport: 1'].assemblyDisplay.setValues(mesh=OFF)
session.viewports['Viewport: 1'].assemblyDisplay.meshOptions.setValues(
meshTechnique=OFF)
##
##  Create job
##
mdb.Job(name='NlSkewPlate', model='Model-1',
description='Nonlinear Elastic Skew Plate. 20 kPa Load.')
a = mdb.models['Model-1'].rootAssembly
a.regenerate()
##
##  Save model database
##
mdb.saveAs('NlSkewPlate.cae')
```

---

### A.7 Stress wave propagation in a bar
gxi_stresswave_caemodel.py
```
#
# Getting Started with Abaqus: Interactive Edition
#
# Replay file for stress wave in a bar example
#
from abaqus import *
from abaqusConstants import *
session.viewports['Viewport: 1'].makeCurrent()
session.viewports['Viewport: 1'].maximize()
from caeModules import *
from driverUtils import executeOnCaeStartup
executeOnCaeStartup()
Mdb()
s = mdb.models['Model-1'].ConstrainedSketch(name='__profile__', sheetSize=1.0)
g, v, d = s.geometry, s.vertices, s.dimensions
s.sketchOptions.setValues(sheetSize=1.0, gridSpacing=0.02, grid=ON,
gridFrequency=2, constructionGeometry=ON, dimensionTextHeight=0.02, decimalPlaces=2)
s.rectangle(point1=(-0.1, -0.1), point2=(0.1, 0.1))
p = mdb.models['Model-1'].Part(name='Bar', dimensionality=THREE_D, type=DEFORMABLE_BODY)
p = mdb.models['Model-1'].parts['Bar']
p.BaseSolidExtrude(sketch=s, depth=1.0)
session.viewports['Viewport: 1'].setValues(displayedObject=p)
del mdb.models['Model-1'].sketches['__profile__']
session.viewports['Viewport: 1'].partDisplay.setValues(renderStyle=SHADED)
mdb.models['Model-1'].Material('Steel')
mdb.models['Model-1'].materials['Steel'].Density(table=((7800.0, ), ))
mdb.models['Model-1'].materials['Steel'].Elastic(table=((207.0E9, 0.3), ))
mdb.models['Model-1'].HomogeneousSolidSection(name='BarSection',
material='Steel', thickness=1.0)
c = p.cells
cells = c
region =(None, None, None, cells)
p.SectionAssignment(region=region, sectionName='BarSection')
a = mdb.models['Model-1'].rootAssembly
session.viewports['Viewport: 1'].setValues(displayedObject=a)
a.DatumCsysByDefault(CARTESIAN)
a.Instance(name='Bar-1', part=p, dependent=ON)
session.viewports['Viewport: 1'].assemblyDisplay.setValues(renderStyle=SHADED)
e = a.instances['Bar-1'].edges
edges = e.findAt(((0.1, 0.1, 0.25), ))
a.Set(edges=edges, name='out')
f = a.instances['Bar-1'].faces
faces = f.findAt(((-0.1, 0.0333333333333333, 0.666666666666667), ))
a.Set(faces=faces, name='back')
faces = f.findAt(((0.1, -0.0333333333333333, 0.666666666666667), ))
a.Set(faces=faces, name='front')
faces = f.findAt(((-0.0333333333333333, -0.1, 0.666666666666667), ))
a.Set(faces=faces, name='bot')
faces = f.findAt(((0.0333333333333333, 0.1, 0.666666666666667), ))
a.Set(faces=faces, name='top')
faces = f.findAt(((0.0333333333333333, -0.0333333333333333, 0.0), ))
a.Set(faces=faces, name='fix')
side1Faces1 = f.findAt(((-0.0333333333333333, -0.0333333333333333, 1.0), ))
a.Surface(side1Faces=side1Faces1, name='load')
mdb.models['Model-1'].ExplicitDynamicsStep(name='BlastLoad', previous='Initial',
description='Apply pressure load pulse', timePeriod=0.0002,
adiabatic=OFF, timeIncrementationMethod=AUTOMATIC_GLOBAL, scaleFactor=1,
maxIncrement=None, massScaling=PREVIOUS_STEP, linearBulkViscosity=0.06,
quadBulkViscosity=0.0)
session.viewports['Viewport: 1'].assemblyDisplay.setValues(step='BlastLoad')
mdb.models['Model-1'].fieldOutputRequests['F-Output-1'].setValues(
numIntervals=4)
del mdb.models['Model-1'].historyOutputRequests['H-Output-1']
regionDef=mdb.models['Model-1'].rootAssembly.sets['out']
mdb.models['Model-1'].HistoryOutputRequest(name='H-Output-1',
createStepName='BlastLoad', variables=('S33', ), frequency=1,
region=regionDef)
session.viewports['Viewport: 1'].assemblyDisplay.setValues(loads=ON, bcs=ON,
predefinedFields=ON)
session.viewports['Viewport: 1'].view.setValues(session.views['Iso'])
region = a.sets['fix']
mdb.models['Model-1'].DisplacementBC(name='Fix right end', createStepName='Initial',
region=region, u1=0.0, u2=0.0, u3=0.0)
region = a.sets['back']
mdb.models['Model-1'].DisplacementBC(name='Restrain back face', createStepName='Initial',
region=region, u1=0.0)
region = a.sets['front']
mdb.models['Model-1'].DisplacementBC(name='Restrain front face', createStepName='Initial',
region=region, u1=0.0)
region = a.sets['bot']
mdb.models['Model-1'].DisplacementBC(name='Restrain bottom face', createStepName='Initial',
region=region, u2=0.0)
region = a.sets['top']
mdb.models['Model-1'].DisplacementBC(name='Restrain top face', createStepName='Initial',
region=region, u2=0.0)
mdb.models['Model-1'].TabularAmplitude(name='Blast', timeSpan=STEP,
smooth=0.25, data=((0.0, 1.0), (3.88e-05, 1.0), (3.89e-05, 0.0), (3.9e-05,     0.0)))
region = a.surfaces['load']
mdb.models['Model-1'].Pressure(name='Blast load', createStepName='BlastLoad',
region=region, magnitude=1.0E5, amplitude='Blast')
session.viewports['Viewport: 1'].assemblyDisplay.setValues(mesh=ON, loads=OFF,
bcs=OFF, predefinedFields=OFF)
session.viewports['Viewport: 1'].assemblyDisplay.meshOptions.setValues(
meshTechnique=ON)
p = mdb.models['Model-1'].parts['Bar']
p.seedPart(size=0.02)
import re, uti
if re.search('Student', uti.getProductVersion()):
p.seedPart(size=0.04)
elemType1 = mesh.ElemType(elemCode=C3D8R, elemLibrary=EXPLICIT,
kinematicSplit=AVERAGE_STRAIN, hourglassControl=RELAX_STIFFNESS)
elemType2 = mesh.ElemType(elemCode=C3D6, elemLibrary=EXPLICIT)
elemType3 = mesh.ElemType(elemCode=C3D4, elemLibrary=EXPLICIT)
c = p.cells
cells = c
regions =(None, None, None, cells)
p.setElementType(regions=regions, elemTypes=(elemType1, elemType2, elemType3))
p.generateMesh()
mdb.Job(name='Bar', model='Model-1', description='Stress wave propagation in a bar (SI units)')
a.regenerate()
mdb.saveAs('Bar')
```

---

### A.8 Connecting lug with plasticity
gsi_plasticlug_caemodel.py
```
#
# Getting Started with Abaqus: Interactive Edition
#
# Script for plastic lug example
#
from abaqus import *
from abaqusConstants import *
session.viewports['Viewport: 1'].makeCurrent()
session.viewports['Viewport: 1'].maximize()
session.journalOptions.setValues(replayGeometry=COORDINATE,
recoverGeometry=COORDINATE)
from caeModules import *
from driverUtils import executeOnCaeStartup
executeOnCaeStartup()
Mdb()
session.viewports['Viewport: 1'].setValues(displayedObject=None)
##  Sketch profile of the lug
s = mdb.models['Model-1'].ConstrainedSketch(name='__profile__',
sheetSize=0.25)
g, v, d, c = s.geometry, s.vertices, s.dimensions, s.constraints
s.sketchOptions.setValues(decimalPlaces=3)
s.setPrimaryObject(option=STANDALONE)
s.rectangle(point1=(-0.0275, 0.0225), point2=(0.02125, -0.01375))
s.delete(objectList=(g.findAt((0.02125, 0.004375)), ))
s.EqualLengthConstraint(entity1=g.findAt((-0.003125, -0.01375)),
entity2=g.findAt((-0.003125, 0.0225)))
s.ObliqueDimension(vertex1=v.findAt((-0.0275, -0.01375)), vertex2=v.findAt((
0.02125, -0.01375)), textPoint=(-0.010330107063055, -0.023654306307435),
value=0.1)
s.move(vector=(-0.025625, 0.0), objectList=(g.findAt((-0.0275, 0.004375)),
g.findAt((0.0225, -0.01375)), g.findAt((0.0225, 0.0225))))
session.viewports['Viewport: 1'].view.fitView()
s.ObliqueDimension(vertex1=v.findAt((-0.053125, 0.0225)), vertex2=v.findAt((
-0.053125, -0.01375)), textPoint=(-0.0564765408635139,
0.00896133482456207), value=0.05)
session.viewports['Viewport: 1'].view.fitView()
session.viewports['Viewport: 1'].view.setValues(nearPlane=0.230597,
farPlane=0.279546, width=0.144889, height=0.121934)
s.Arc3Points(point1=(0.046875, 0.03625), point2=(0.046875, -0.01375), point3=(
0.0625, 0.02375))
s.TangentConstraint(entity1=g.findAt((-0.003125, 0.03625)), entity2=g.findAt((
0.0657, 0.01125)))
s.move(vector=(-0.001797, 0.0), objectList=(g.findAt((-0.053125, 0.01125)),
g.findAt((-0.003125, -0.01375)), g.findAt((-0.003125, 0.03625)), g.findAt((
0.071875, 0.01125))))
s.TangentConstraint(entity1=g.findAt((-0.004922, -0.01375)), entity2=g.findAt((
0.070078, 0.01125)))
session.viewports['Viewport: 1'].view.fitView()
s.RadialDimension(curve=g.findAt((0.070078, 0.01125)), textPoint=(
0.0655877739191055, -0.0193991288542748), radius=0.025)
d[2].setValues(reference=ON)
s.CircleByCenterPerimeter(center=(0.0425, 0.0125), point1=(0.0525, 0.01625))
s.ConcentricConstraint(entity1=g.findAt((0.0325, 0.00875)), entity2=g.findAt((
0.070078, 0.01125)))
s.RadialDimension(curve=g.findAt((0.035078, 0.0075)), textPoint=(
0.0297759883105755, 0.0219836011528969), radius=0.015)
s.VerticalDimension(vertex1=v.findAt((0.045078, 0.01125)), vertex2=v.findAt((
0.059123, 0.016517)), textPoint=(0.0632773488759995, 0.0129371425136924),
value=0.0)
s.VerticalDimension(vertex1=v.findAt((0.045078, 0.01125)), vertex2=v.findAt((
0.067003, 0.023263)), textPoint=(0.0746369957923889, 0.012744665145874),
value=0.0)
s.move(vector=(0.034922, 0.00375), objectList=(g.findAt((-0.054922, 0.01125)),
g.findAt((-0.004922, -0.01375)), g.findAt((-0.004922, 0.03625)),
g.findAt((0.070078, 0.01125)), g.findAt((0.030078, 0.01125))))
p = mdb.models['Model-1'].Part(name='Lug', dimensionality=THREE_D,
type=DEFORMABLE_BODY)
p = mdb.models['Model-1'].parts['Lug']
p.BaseSolidExtrude(sketch=s, depth=0.02)
s.unsetPrimaryObject()
p = mdb.models['Model-1'].parts['Lug']
session.viewports['Viewport: 1'].setValues(displayedObject=p)
del mdb.models['Model-1'].sketches['__profile__']
c, f, e, v, d  = p.cells, p.faces, p.edges, p.vertices, p.datums
##
##  Create material 'Steel'
##
mdb.models['Model-1'].Material('Steel')
mdb.models['Model-1'].materials['Steel'].Elastic(table=((200.0E9, 0.3), ))
mdb.models['Model-1'].materials['Steel'].Plastic(table=((380.0E6, 0.0), (
580.0E6, 0.35)))
##
##  Create solid section
##
mdb.models['Model-1'].HomogeneousSolidSection(name='LugSection',
material='Steel', thickness=1.0)
##
##  Assign solid section
##
c = p.cells
cells = c
region = regionToolset.Region(cells=cells)
p.SectionAssignment(region=region, sectionName='LugSection', offset=0.0)
##
##  Set coordinate system (done by default)
##
a = mdb.models['Model-1'].rootAssembly
a.DatumCsysByDefault(CARTESIAN)
##
##  Instance the lug
##
a.Instance(name='Lug-1', part=p, dependent=ON)
##
##  Create a static general step
##
mdb.models['Model-1'].StaticStep(name='LugLoad',
previous='Initial', description='Apply uniform pressure to the hole',
initialInc=0.2)
session.viewports['Viewport: 1'].assemblyDisplay.setValues(step='LugLoad')
##
##  Apply encastre bc to left end
##
f = a.instances['Lug-1'].faces
faces = f.findAt(((-0.02, 0.006667, 0.013333), ))
region = regionToolset.Region(faces=faces)
mdb.models['Model-1'].EncastreBC(name='Fix left end',
createStepName='LugLoad', region=region)
session.viewports['Viewport: 1'].setValues(displayedObject=a)
session.viewports['Viewport: 1'].view.fitView()
session.viewports['Viewport: 1'].view.setValues(session.views['Iso'])
##
##  Partition the lug
##
c, f, e, v, d  = p.cells, p.faces, p.edges, p.vertices, p.datums
pickedCells = c.findAt(((-0.02, 0.006667, 0.013333), ))
p.PartitionCellByPlaneThreePoints(point1=v.findAt(coordinates=(0.095, 0.015,
0.02)), cells=pickedCells, point2=p.InterestingPoint(edge=e.findAt(
coordinates=(0.08, 0.03, 0.02)), rule=MIDDLE), point3=p.InterestingPoint(
edge=e.findAt(coordinates=(0.08, 0.03, 0.0)), rule=MIDDLE))
c, f, e, v, d  = p.cells, p.faces, p.edges, p.vertices, p.datums
##
##  Apply pressure load to bottom of hole
##
a.regenerate()
s = a.instances['Lug-1'].faces
side1Faces = s.findAt(((0.094968, 0.01402, 0.013333), ))
region = regionToolset.Region(side1Faces=side1Faces)
mdb.models['Model-1'].Pressure(name='Pressure load',
createStepName='LugLoad', region=region, magnitude=1.0E8)
##
##  Create partitions
##
pickedCells = c.findAt(((-0.02, 0.006667, 0.006667), ), ((-0.02, 0.023333,
0.013333), ))
p.PartitionCellByPlaneThreePoints(cells=pickedCells, point1=p.InterestingPoint(
edge=e.findAt(coordinates=(0.069393, 0.004393, 0.0)), rule=MIDDLE),
point2=p.InterestingPoint(edge=e.findAt(coordinates=(0.069393, 0.004393,
0.02)), rule=MIDDLE), point3=p.InterestingPoint(edge=e.findAt(
coordinates=(0.090607, 0.025607, 0.02)), rule=MIDDLE))
c, f, e, v, d  = p.cells, p.faces, p.edges, p.vertices, p.datums
p.DatumPointByEdgeParam(edge=e.findAt(coordinates=(0.055, -0.01, 0.02)),
parameter=0.25)
pickedCells = c.findAt(((-0.02, 0.006667, 0.006667), ), ((-0.02, 0.023333,
0.013333), ))
p.PartitionCellByPlanePointNormal(point=d[5], normal=e.findAt(coordinates=(
0.055, -0.01, 0.02)), cells=pickedCells)
c, f, e, v, d  = p.cells, p.faces, p.edges, p.vertices, p.datums
f = a.instances['Lug-1'].faces
faces = f.findAt(((-0.02, 0.006667, 0.006667), ), ((-0.02, 0.023333,
0.013333), ))
a.Set(faces=faces, name='BuiltIn')
e = a.instances['Lug-1'].edges
edges = e.findAt(((0.08, 0.0, 0.015), ))
a.Set(edges=edges, name='HoleBot')
##
##  Assign global seed
##
p.seedPart(size=0.007)
import re, uti
if re.search('Student', uti.getProductVersion()):
p.seedPart(size=0.01)
##
##  Assign element type
##
elemType1 = mesh.ElemType(elemCode=C3D20R)
elemType2 = mesh.ElemType(elemCode=C3D15)
elemType3 = mesh.ElemType(elemCode=C3D10M)
cells = c
pickedRegions =(cells, )
p.setElementType(regions=pickedRegions, elemTypes=(elemType1, elemType2,
elemType3))
##
##  Generate the mesh
##
p.generateMesh()
session.viewports['Viewport: 1'].view.setValues(session.views['Iso'])
session.viewports['Viewport: 1'].assemblyDisplay.geometryOptions.setValues(
datumPoints=OFF)
mdb.models['Model-1'].fieldOutputRequests['F-Output-1'].setValues(
variables=PRESELECT)
del mdb.models['Model-1'].historyOutputRequests['H-Output-1']
a.regenerate()
mdb.Job(name='PlasticLugHard', model='Model-1',
description='Elastic-Plastic Steel Connecting Lug')
a.regenerate()
session.viewports['Viewport: 1'].view.fitView()
session.viewports['Viewport: 1'].view.setValues(session.views['Iso'])
#
#  Save model database
#
mdb.saveAs('PlasticLug.cae')
```

---

### A.9 Blast loading on a stiffened plate
gxi_stiffplate_caemodel.py
```
#
# Getting Started with Abaqus: Interactive Edition
#
# Script for stiffened plate example
#
from abaqus import *
from abaqusConstants import *
session.viewports['Viewport: 1'].makeCurrent()
session.viewports['Viewport: 1'].maximize()
session.journalOptions.setValues(replayGeometry=COORDINATE,
recoverGeometry=COORDINATE)
from caeModules import *
from driverUtils import executeOnCaeStartup
executeOnCaeStartup()
Mdb()
s = mdb.models['Model-1'].ConstrainedSketch(name='__profile__', sheetSize=5.0)
g, v, d, c = s.geometry, s.vertices, s.dimensions, s.constraints
s.setPrimaryObject(option=STANDALONE)
s.Line(point1=(-0.65, 0.075), point2=(0.725000000046566, 0.075))
s.HorizontalConstraint(entity=g.findAt((0.0375, 0.075)), addUndoState=False)
s.Line(point1=(-0.325, 0.075), point2=(-0.325, 0.225000000046566))
s.VerticalConstraint(entity=g.findAt((-0.325, 0.15)), addUndoState=False)
s.PerpendicularConstraint(entity1=g.findAt((0.0375, 0.075)), entity2=g.findAt(
(-0.325, 0.15)), addUndoState=False)
s.CoincidentConstraint(entity1=v.findAt((-0.325, 0.075)), entity2=g.findAt((
0.0375, 0.075)), addUndoState=False)
s.Line(point1=(0.15, 0.075), point2=(0.15, 0.25))
s.VerticalConstraint(entity=g.findAt((0.15, 0.1625)), addUndoState=False)
s.PerpendicularConstraint(entity1=g.findAt((0.0375, 0.075)), entity2=g.findAt(
(0.15, 0.1625)), addUndoState=False)
s.CoincidentConstraint(entity1=v.findAt((0.15, 0.075)), entity2=g.findAt((
0.0375, 0.075)), addUndoState=False)
s.Line(point1=(0.55, 0.075), point2=(0.55, 0.25))
s.VerticalConstraint(entity=g.findAt((0.55, 0.1625)), addUndoState=False)
s.PerpendicularConstraint(entity1=g.findAt((0.0375, 0.075)), entity2=g.findAt(
(0.55, 0.1625)), addUndoState=False)
s.CoincidentConstraint(entity1=v.findAt((0.55, 0.075)), entity2=g.findAt((
0.0375, 0.075)), addUndoState=False)
s.EqualLengthConstraint(entity1=g.findAt((-0.325, 0.15)), entity2=g.findAt((
0.15, 0.1625)))
s.EqualLengthConstraint(entity1=g.findAt((0.15, 0.15625)), entity2=g.findAt((
0.55, 0.1625)), addUndoState=False)
s.ObliqueDimension(
vertex1=v.findAt((-0.325, 0.075)), vertex2=v.findAt((-0.325,
0.225)), textPoint=(-0.829278707504272, 0.192073285579681), value=0.1)
s.move(vector=(0.0, 0.025), objectList=(g.findAt((0.0375, 0.075)), g.findAt((
-0.325, 0.125)), g.findAt((0.15, 0.125)), g.findAt((0.55, 0.125))))
s.breakCurve(curve1=g.findAt((0.0375, 0.1)), point1=(-0.441734611988068,
0.0968574285507202), curve2=g.findAt((-0.325, 0.15)), point2=(
-0.326785087585449, 0.149390280246735))
s.breakCurve(curve1=g.findAt((0.2, 0.1)), point1=(0.00492632389068604,
0.106707394123077), curve2=g.findAt((0.15, 0.15)), point2=(
0.152718663215637, 0.155956923961639))
s.breakCurve(curve1=g.findAt((0.4375, 0.1)), point1=(0.415460348129272,
0.100140750408173), curve2=g.findAt((0.55, 0.15)), point2=(
0.556684136390686, 0.139540374279022))
s.HorizontalDimension(vertex1=v.findAt((-0.65, 0.1)), vertex2=v.findAt((0.725,
0.1)), textPoint=(0.458155989646912, -0.165806710720062), value=2.0)
s.EqualLengthConstraint(entity1=g.findAt((-0.8, 0.1)), entity2=g.findAt((
-0.0875, 0.1)))
s.EqualLengthConstraint(entity1=g.findAt((-0.0875, 0.1)), entity2=g.findAt((
0.35, 0.1)), addUndoState=False)
s.EqualLengthConstraint(entity1=g.findAt((0.3125, 0.1)), entity2=g.findAt((
0.9125, 0.1)), addUndoState=False)
s.move(vector=(0.0375, 0.0), objectList=(g.findAt((-0.325, 0.15)), g.findAt((
0.175, 0.15)), g.findAt((0.675, 0.15)), g.findAt((-0.575, 0.1)), g.findAt((
-0.075, 0.1)), g.findAt((0.425, 0.1)), g.findAt((0.925, 0.1))))
s.move(
vector=(-0.2125, -0.1),
objectList=(
g.findAt((-0.2875, 0.15)), g.findAt((0.2125, 0.15)),
g.findAt((0.7125, 0.15)), g.findAt((-0.5375, 0.1)),
g.findAt((-0.0375, 0.1)), g.findAt((0.4625, 0.1)),
g.findAt((0.9625, 0.1))))
p = mdb.models['Model-1'].Part(name='Plate', dimensionality=THREE_D,
type=DEFORMABLE_BODY)
p = mdb.models['Model-1'].parts['Plate']
p.BaseShellExtrude(sketch=s, depth=2.0)
s.unsetPrimaryObject()
p = mdb.models['Model-1'].parts['Plate']
session.viewports['Viewport: 1'].setValues(displayedObject=p)
del mdb.models['Model-1'].sketches['__profile__']
session.viewports['Viewport: 1'].setValues(displayedObject=p)
session.viewports['Viewport: 1'].partDisplay.setValues(renderStyle=SHADED)
mdb.models['Model-1'].Material('Steel')
mdb.models['Model-1'].materials['Steel'].Density(table=((7800.0, ), ))
mdb.models['Model-1'].materials['Steel'].Elastic(table=((210.0E9, 0.3), ))
mdb.models['Model-1'].materials['Steel'].Plastic(table=((300.0E6, 0.0),
(350.0E6, 0.025), (375.0E6, 0.1), (394.0E6, 0.2), (400.0E6, 0.35)))
mdb.models['Model-1'].HomogeneousShellSection(name='PlateSection',
preIntegrate=OFF, material='Steel', thickness=0.025,
poissonDefinition=DEFAULT, temperature=GRADIENT,
integrationRule=SIMPSON, numIntPts=5)
mdb.models['Model-1'].HomogeneousShellSection(name='StiffSection',
preIntegrate=OFF, material='Steel', thickness=0.0125,
poissonDefinition=DEFAULT, temperature=GRADIENT,
integrationRule=SIMPSON, numIntPts=5)
f = p.faces
faces = f.findAt(
((0.833333, 0.0, 1.333333), ),
((0.333333, 0.0, 1.333333), ),
((-0.166667, 0.0, 1.333333), ),
((-0.666667, 0.0, 1.333333), ))
region =(None, None, faces, None)
p.SectionAssignment(region=region, sectionName='PlateSection', offset=-0.5)
faces = f.findAt(
((-0.5, 0.066669, 1.333333), ),
((0.0, 0.066671, 1.333333), ),
((0.5, 0.066673, 1.333333), ))
region =(None, None, faces, None)
p.SectionAssignment(region=region, sectionName='StiffSection')
a = mdb.models['Model-1'].rootAssembly
session.viewports['Viewport: 1'].setValues(displayedObject=a)
a.DatumCsysByDefault(CARTESIAN)
a.Instance(name='Plate-1', part=p, dependent=ON)
session.viewports['Viewport: 1'].assemblyDisplay.setValues(renderStyle=SHADED)
p = mdb.models['Model-1'].parts['Plate']
e = p.edges
pickedEdges = e.findAt(((0.0, 0.0, 0.5), ))
p.PartitionEdgeByParam(edges=pickedEdges, parameter=0.5)
v = a.instances['Plate-1'].vertices
verts = v.findAt(((0.0, 0.0, 1.0), ))
a.Set(vertices=verts, name='Center')
e = a.instances['Plate-1'].edges
edges = e.findAt(
((0.875, 0.0, 2.0), ), ((0.625, 0.0, 0.0), ),
((1.0, 0.0, 0.5), ), ((0.375, 0.0, 2.0), ),
((0.125, 0.0, 0.0), ), ((-0.125, 0.0, 2.0), ),
((-0.375, 0.0, 0.0), ), ((-0.625, 0.0, 2.0), ),
((-1.0, 0.0, 0.5), ), ((-0.875, 0.0, 0.0), ))
a.Set(edges=edges, name='Edge')
session.viewports['Viewport: 1'].assemblyDisplay.setValues(loads=OFF, bcs=OFF,
predefinedFields=OFF)
mdb.models['Model-1'].ExplicitDynamicsStep(name='Blast', previous='Initial',
description='Apply blast loading', timePeriod=0.05, adiabatic=OFF,
timeIncrementationMethod=AUTOMATIC_GLOBAL, scaleFactor=1,
maxIncrement=None, massScaling=PREVIOUS_STEP, linearBulkViscosity=0.06,
quadBulkViscosity=1.2)
regionDef=a.sets['Center']
mdb.models['Model-1'].steps['Blast'].Monitor(dof=2, node=regionDef)
mdb.models['Model-1'].fieldOutputRequests['F-Output-1'].setValues(
numIntervals=25)
mdb.models['Model-1'].historyOutputRequests['H-Output-1'].setValues(
numIntervals=500)
regionDef=mdb.models['Model-1'].rootAssembly.sets['Center']
mdb.models['Model-1'].HistoryOutputRequest(name='Center-U2',
createStepName='Blast', variables=('U2', ), numIntervals=500,
region=regionDef)
session.viewports['Viewport: 1'].assemblyDisplay.setValues(loads=ON, bcs=ON,
predefinedFields=ON)
region = a.sets['Edge']
mdb.models['Model-1'].EncastreBC(name='Fix edges', createStepName='Initial',
region=region)
mdb.models['Model-1'].TabularAmplitude(name='Blast', timeSpan=STEP,
smooth=0.25, data=((0.0, 0.0), (0.001, 7.0E5), (0.01, 7.0E5),
(0.02, 0.0), (0.05, 0.0)))
s = a.instances['Plate-1'].faces
side1Faces = s.findAt(
((0.833333, 0.0, 1.333333), ),
((0.333333, 0.0, 1.333333), ),
((-0.166667, 0.0, 1.333333), ),
((-0.666667, 0.0, 1.333333), ))
region = regionToolset.Region(side1Faces=side1Faces)
mdb.models['Model-1'].Pressure(name='Pressure load', createStepName='Blast',
region=region, magnitude=1.0, amplitude='Blast')
session.viewports['Viewport: 1'].assemblyDisplay.setValues(mesh=ON)
session.viewports['Viewport: 1'].assemblyDisplay.meshOptions.setValues(
meshTechnique=ON)
p.seedPart(size=0.1)
e = p.edges
edges =(e.findAt(coordinates=(-0.5, 0.025, 2.0)), e.findAt(coordinates=(
0.0, 0.025, 2.0)), e.findAt(coordinates=(0.5, 0.025, 2.0)), e.findAt(
coordinates=(-0.5, 0.075, 0.0)), e.findAt(coordinates=(0.0, 0.075,
0.0)), e.findAt(coordinates=(0.5, 0.075, 0.0)))
p.seedEdgeByNumber(edges=edges, number=2)
elemType1 = mesh.ElemType(elemCode=S4R, elemLibrary=EXPLICIT,
hourglassControl=RELAX_STIFFNESS)
elemType2 = mesh.ElemType(elemCode=S3, elemLibrary=EXPLICIT)
f = p.faces
faces = f
regions =(None, None, faces, None)
p.setElementType(regions=regions, elemTypes=(elemType1, elemType2))
pickedRegions = f
p.setMeshControls(regions=pickedRegions, elemShape=QUAD, algorithm=MEDIAL_AXIS)
p.generateMesh()
session.viewports['Viewport: 1'].assemblyDisplay.setValues(renderStyle=SHADED)
mdb.Job(name='BlastLoad', model='Model-1')
mdb.jobs['BlastLoad'].setValues(description='Blast load on a flat plate with stiffeners: S4R elements (20x20 mesh) Normal stiffeners (20x2)')
a.regenerate()
mdb.saveAs('StiffPlate')
```

---

### A.10 Axisymmetric mount
gsi_mount_caemodel.py
```
#
# Getting Started with Abaqus: Interactive Edition
#
# Script for rubber mount example
#
from abaqus import *
from abaqusConstants import *
session.viewports['Viewport: 1'].makeCurrent()
session.viewports['Viewport: 1'].maximize()
session.journalOptions.setValues(replayGeometry=COORDINATE,
recoverGeometry=COORDINATE)
from caeModules import *
from driverUtils import executeOnCaeStartup
executeOnCaeStartup()
Mdb()
##
##  Sketch profile of the mount
##
s = mdb.models['Model-1'].ConstrainedSketch(name='__profile__', sheetSize=0.3)
g, v, d, c = s.geometry, s.vertices, s.dimensions, s.constraints
s.sketchOptions.setValues(decimalPlaces=3, viewStyle=AXISYM)
s.setPrimaryObject(option=STANDALONE)
s.ConstructionLine(point1=(0.0, -0.15), point2=(0.0, 0.15))
s.FixedConstraint(entity=g.findAt((0.0, 0.0)))
s.rectangle(point1=(0.01375, 0.035), point2=(0.04625, 0.0175))
s.DistanceDimension(entity1=g.findAt((0.0, 0.0)), entity2=v.findAt((0.01375,
0.0175)), textPoint=(0.012268845923245, 0.0116447377949953), value=0.01)
s.ObliqueDimension(vertex1=v.findAt((0.01, 0.035)), vertex2=v.findAt((0.01,
0.0175)), textPoint=(0.00531696528196335, 0.0242882780730724), value=0.03)
s.ObliqueDimension(vertex1=v.findAt((0.01, 0.0175)), vertex2=v.findAt((0.0425,
0.0175)), textPoint=(0.0255863033235073, 0.0116447377949953), value=0.05)
session.viewports['Viewport: 1'].view.fitView()
session.viewports['Viewport: 1'].view.setValues(nearPlane=0.128767,
farPlane=0.166316, width=0.111144, height=0.0935352)
s.CircleByCenterPerimeter(center=(0.07375, 0.04875), point1=(0.06, 0.0275))
s.CoincidentConstraint(entity1=v.findAt((0.06, 0.0275)), entity2=g.findAt((
0.06, 0.0325)), addUndoState=False)
s.DistanceDimension(entity1=g.findAt((0.0, 0.0)), entity2=v.findAt((0.07375,
0.04875)), textPoint=(0.0690968036651611, -0.00352155975997448), value=0.1)
session.viewports['Viewport: 1'].view.fitView()
s.VerticalDimension(vertex1=v.findAt((0.06, 0.0475)), vertex2=v.findAt((0.1,
0.04875)), textPoint=(0.117072999477386, 0.0480493120849133), value=0.0)
s.VerticalDimension(vertex1=v.findAt((0.06, 0.0275)), vertex2=v.findAt((0.06,
0.0175)), textPoint=(0.0739211142063141, 0.0188609156757593), value=0.005)
s.autoTrimCurve(curve1=g.findAt((0.14, 0.0725)), point1=(0.0657630488276482,
0.0819593593478203))
s.autoTrimCurve(curve1=g.findAt((0.06, 0.0325)), point1=(0.0606105849146843,
0.0390352495014668))
s.autoTrimCurve(curve1=g.findAt((0.035, 0.0475)), point1=(0.0567462332546711,
0.0471908301115036))
s.move(vector=(0.0, -0.0175), objectList=(g.findAt((0.01, 0.0325)), g.findAt((
0.035, 0.0175)), g.findAt((0.054658, 0.034496)), g.findAt((0.06, 0.02)),
g.findAt((0.031415, 0.0475))))
p = mdb.models['Model-1'].Part(name='Mount', dimensionality=AXISYMMETRIC,
type=DEFORMABLE_BODY)
p = mdb.models['Model-1'].parts['Mount']
p.BaseShell(sketch=s)
s.unsetPrimaryObject()
p = mdb.models['Model-1'].parts['Mount']
session.viewports['Viewport: 1'].setValues(displayedObject=p)
del mdb.models['Model-1'].sketches['__profile__']
##
##  Create material 'Rubber'
##
mdb.models['Model-1'].Material('Rubber')
mdb.models['Model-1'].materials['Rubber'].Hyperelastic(type=POLYNOMIAL,
table=())
mdb.models['Model-1'].materials['Rubber'].hyperelastic.UniaxialTestData(table=((
0.054E6, 0.0380), (0.152E6, 0.1338), (0.254E6, 0.2210), (0.362E6, 0.3450),
(0.459E6, 0.4600), (0.583E6, 0.6242), (0.656E6, 0.8510), (0.730E6,
1.4268)))
mdb.models['Model-1'].materials['Rubber'].hyperelastic.BiaxialTestData(table=((
0.089E6, 0.0200), (0.255E6, 0.1400), (0.503E6, 0.4200), (0.958E6, 1.4900),
(1.703E6, 2.7500), (2.413E6, 3.4500)))
mdb.models['Model-1'].materials['Rubber'].hyperelastic.PlanarTestData(table=((
0.055E6, 0.0690), (0.324E6, 0.2828), (0.758E6, 1.3862), (1.269E6, 3.0345),
(1.779E6, 4.0621)))
##
##  Create material 'Steel'
##
mdb.models['Model-1'].Material('Steel')
mdb.models['Model-1'].materials['Steel'].Elastic(table=((200.E9, 0.3), ))
##
##  Create solid sections for the rubber and steel
##
mdb.models['Model-1'].HomogeneousSolidSection(name='RubberSection',
material='Rubber', thickness=1.0)
mdb.models['Model-1'].HomogeneousSolidSection(name='SteelSection',
material='Steel', thickness=1.0)
##
##  Partition the part into two regions (rubber and steel regions)
##
c, f, e, v, d  = p.cells, p.faces, p.edges, p.vertices, p.datums
t = p.MakeSketchTransform(
sketchPlane=f.findAt(coordinates=(0.043333, 0.001667, 0.0),
normal=(0.0, 0.0, 1.0)), sketchPlaneSide=SIDE1,
origin=(0.033052, 0.014514, 0.0))
s = mdb.models['Model-1'].ConstrainedSketch(name='__profile__',
sheetSize=0.134, gridSpacing=0.003, transform=t)
g, v, d1, c = s.geometry, s.vertices, s.dimensions, s.constraints
s.sketchOptions.setValues(decimalPlaces=3)
s.setPrimaryObject(option=SUPERIMPOSE)
p.projectReferencesOntoSketch(sketch=s, filter=COPLANAR_EDGES)
s.Line(point1=(0.026948, -0.009514), point2=(-0.03, -0.009514))
s.HorizontalConstraint(entity=g.findAt((-0.001526, -0.009514)))
s.PerpendicularConstraint(entity1=g.findAt((0.026948, -0.012014)),
entity2=g.findAt((-0.001526, -0.009514)))
pickedFaces = f.findAt(((0.043333, 0.001667, 0.0), ))
p.PartitionFaceBySketch(faces=pickedFaces, sketch=s)
s.unsetPrimaryObject()
del mdb.models['Model-1'].sketches['__profile__']
c, f, e, v, d  = p.cells, p.faces, p.edges, p.vertices, p.datums
##
##  Assign rubber section
##
p = mdb.models['Model-1'].parts['Mount']
f = p.faces
faces = f.findAt(((0.042303, 0.006937, 0.0), ))
region = regionToolset.Region(faces=faces)
p.SectionAssignment(region=region, sectionName='RubberSection', offset=0.0)
##
##  Assign steel section
##
faces = f.findAt(((0.043333, 0.003333, 0.0), ))
region = regionToolset.Region(faces=faces)
p.SectionAssignment(region=region, sectionName='SteelSection', offset=0.0)
a = mdb.models['Model-1'].rootAssembly
session.viewports['Viewport: 1'].setValues(displayedObject=a)
##
##  Set coordinate system (done by default)
##
a.DatumCsysByDefault(CARTESIAN)
##
##  Instance the mount
##
p = mdb.models['Model-1'].parts['Mount']
a.Instance(name='Mount-1', part=p, dependent=ON)
##
##  Create geometry set 'Middle'
##
e = a.instances['Mount-1'].edges
edges = e.findAt(((0.020708, 0.03, 0.0), ))
a.Set(edges=edges, name='Middle')
##
##  Create geometry set 'Out'
##
v = a.instances['Mount-1'].vertices
verts = v.findAt(((0.01, 0.0, 0.0), ))
a.Set(vertices=verts, name='Out')
##
##  Create surface 'Bottom'
##
s = a.instances['Mount-1'].edges
side1Edges = s.findAt(((0.0475, 0.0, 0.0), ))
a.Surface(side1Edges=side1Edges, name='Bottom')
##
##  Create a static general step
##
mdb.models['Model-1'].StaticStep(name='Compress mount', previous='Initial',
description='Apply axial pressure load to mount', timePeriod=1,
adiabatic=OFF, maxNumInc=100, stabilization=None,
timeIncrementationMethod=AUTOMATIC,
initialInc=0.01, minInc=1e-05, maxInc=1, matrixSolver=SOLVER_DEFAULT,
amplitude=RAMP, extrapolation=LINEAR, fullyPlastic="", nlgeom=ON)
session.viewports['Viewport: 1'].assemblyDisplay.setValues(
step='Compress mount')
##
##  Modify output requests
##
mdb.models['Model-1'].fieldOutputRequests['F-Output-1'].setValues(
variables=('S', 'PE', 'PEEQ', 'PEMAG', 'NE', 'LE', 'U', 'RF',
'CF', 'CSTRESS', 'CDISP'))
regionDef=a.sets['Out']
mdb.models['Model-1'].HistoryOutputRequest(name='H-Output-1',
createStepName='Compress mount', variables=('U1', 'U2', 'U3'),
region=regionDef)
session.viewports['Viewport: 1'].assemblyDisplay.setValues(loads=ON, bcs=ON,
predefinedFields=ON)
##
##  Apply pressure load
##
region = a.surfaces['Bottom']
mdb.models['Model-1'].Pressure(name='Pressure',
createStepName='Compress mount', region=region, magnitude=500000.0)
##
##  Apply symmetry bc to set "Middle'
##
region = a.sets['Middle']
mdb.models['Model-1'].DisplacementBC(name='Symmetry',
createStepName='Compress mount', region=region, u2=0.0)
##
##  Suppress visibility of datum geometry
##
session.viewports['Viewport: 1'].assemblyDisplay.geometryOptions.setValues(
geometryEdgesInShaded=OFF, datumPoints=OFF, datumAxes=OFF, datumPlanes=OFF,
datumCoordSystems=OFF)
session.viewports['Viewport: 1'].assemblyDisplay.setValues(mesh=ON, loads=OFF,
bcs=OFF, predefinedFields=OFF)
session.viewports['Viewport: 1'].assemblyDisplay.meshOptions.setValues(
meshTechnique=ON)
##
##  Assign edge seeds
##
p = mdb.models['Model-1'].parts['Mount']
e = p.edges
pickedEdges = e.findAt(((0.0225, 0.005, 0.0), ), ((0.0475, 0.0, 0.0), ),
((0.020708, 0.03, 0.0), ))
p.seedEdgeByNumber(edges=pickedEdges, number=30)
pickedEdges = e.findAt(((0.053289, 0.023434, 0.0), ), ((0.01, 0.01125, 0.0), ))
p.seedEdgeByNumber(edges=pickedEdges, number=14)
pickedEdges = e.findAt(((0.01, 0.00125, 0.0), ), ((0.06, 0.00375, 0.0), ))
p.seedEdgeByNumber(edges=pickedEdges, number=1)
##
##  Use structured meshing
##
f = p.faces
pickedRegions = f
p.setMeshControls(regions=pickedRegions, technique=STRUCTURED)
##
##  Assign element type to the rubber
##
elemType1 = mesh.ElemType(elemCode=CAX4H, elemLibrary=STANDARD)
elemType2 = mesh.ElemType(elemCode=CAX3, elemLibrary=STANDARD)
faces = f.findAt(((0.042303, 0.006937, 0.0), ))
pickedRegions =(faces, )
p.setElementType(regions=pickedRegions, elemTypes=(elemType1, elemType2))
##
##  Assign element type to the steel
##
elemType1 = mesh.ElemType(elemCode=CAX4I, elemLibrary=STANDARD)
elemType2 = mesh.ElemType(elemCode=CAX3, elemLibrary=STANDARD)
faces = f.findAt(((0.043333, 0.003333, 0.0), ))
pickedRegions =(faces, )
p.setElementType(regions=pickedRegions, elemTypes=(elemType1, elemType2))
##
##  Generate mesh
##
p.generateMesh()
session.viewports['Viewport: 1'].assemblyDisplay.setValues(mesh=OFF)
session.viewports['Viewport: 1'].assemblyDisplay.meshOptions.setValues(
meshTechnique=OFF)
##
##  Create job
##
mdb.Job(name='Mount', model='Model-1',
description='Axisymmetric mount analysis under axial loading',
modelPrint=ON)
a = mdb.models['Model-1'].rootAssembly
a.regenerate()
##
##  Save model database
##
mdb.saveAs('Mount')
```

---

### A.11 Vibration of a piping system
gsi_pipe_caemodel.py
```
#
# Getting Started with Abaqus: Interactive Edition
#
# Script for pipe example
#
#
from abaqus import *
from abaqusConstants import *
session.viewports['Viewport: 1'].makeCurrent()
session.viewports['Viewport: 1'].maximize()
session.journalOptions.setValues(replayGeometry=COORDINATE,
recoverGeometry=COORDINATE)
from caeModules import *
from driverUtils import executeOnCaeStartup
executeOnCaeStartup()
Mdb()
##
##  Rename the model 'Original'
##
session.viewports['Viewport: 1'].setValues(displayedObject=None)
mdb.models.changeKey('Model-1', 'Original')
##
##  Sketch profile of the pipe
##
s = mdb.models['Original'].ConstrainedSketch(name='__profile__',
sheetSize=20.0)
g, v, d = s.geometry, s.vertices, s.dimensions
s.sketchOptions.setValues(sheetSize=20.0, gridSpacing=0.5, grid=ON,
gridFrequency=2, constructionGeometry=ON, dimensionTextHeight=0.5,
decimalPlaces=2)
s.Line(point1=(0.0, 0.0), point2=(5.0, 0.0))
p = mdb.models['Original'].Part(name='Pipe', dimensionality=THREE_D,
type=DEFORMABLE_BODY)
p = mdb.models['Original'].parts['Pipe']
p.BaseWire(sketch=s)
session.viewports['Viewport: 1'].setValues(displayedObject=p)
del mdb.models['Original'].sketches['__profile__']
##
##  Create material 'Steel'
##
mdb.models['Original'].Material('Steel')
mdb.models['Original'].materials['Steel'].Elastic(table=((2.E+11, 0.3), ))
mdb.models['Original'].materials['Steel'].Density(table=((7800.0, ), ))
##
##  Create pipe profile and section
##
mdb.models['Original'].PipeProfile(name='PipeProfile', r=0.09, t=0.02)
mdb.models['Original'].BeamSection(name='PipeSection', profile='PipeProfile',
integration=DURING_ANALYSIS, material='Steel', temperatureVar=LINEAR)
##
##  Assign pipe section
##
e = p.edges
region=(None, e.findAt(((1.25, 0.0, 0.0), ), ), None, None)
p.SectionAssignment(region=region, sectionName='PipeSection')
##
##  Assign beam orientations
##
region=(None, e.findAt(((1.25, 0.0, 0.0), ), ), None, None)
p.assignBeamSectionOrientation(region=region, method=N1_COSINES,
n1=(0.0, 0.0, -1.0))
a = mdb.models['Original'].rootAssembly
session.viewports['Viewport: 1'].setValues(displayedObject=a)
##
##  Set coordinate system (done by default)
##
a.DatumCsysByDefault(CARTESIAN)
##
##  Instance the pipe
##
p = mdb.models['Original'].parts['Pipe']
a.Instance(name='Pipe-1', part=p, dependent=ON)
##
##  Create geometry set 'Left'
##
v = a.instances['Pipe-1'].vertices
a.Set(vertices=v.findAt(((0.0, 0.0, 0.0), ), ), name='Left')
##
##  Create geometry set 'Right'
##
a.Set(vertices=v.findAt(((5.0, 0.0, 0.0), ), ), name='Right')
##
##  Create a static general step
##
mdb.models['Original'].StaticStep(name='Pull I', previous='Initial',
description='Apply axial tensile load of 4.0 MN', timePeriod=1,
adiabatic=OFF, maxNumInc=100, stabilization=None,
timeIncrementationMethod=AUTOMATIC,
initialInc=0.1, minInc=1e-05, maxInc=1, matrixSolver=SOLVER_DEFAULT,
amplitude=RAMP, extrapolation=LINEAR, fullyPlastic="", nlgeom=ON)
session.viewports['Viewport: 1'].assemblyDisplay.setValues(step='Pull I')
##
##  Create a frequency extraction step
##
mdb.models['Original'].FrequencyStep(name='Frequency I', previous='Pull I',
description='Extract modes and frequencies', numEigen=8,
maxEigen=None, shift=None, vectors=16, maxIterations=30,
eigensolver=SUBSPACE)
session.viewports['Viewport: 1'].assemblyDisplay.setValues(step='Pull I')
##
##  Modify output requests
##
mdb.models['Original'].fieldOutputRequests['F-Output-1'].setValues(
variables=PRESELECT)
del mdb.models['Original'].historyOutputRequests['H-Output-1']
session.viewports['Viewport: 1'].assemblyDisplay.setValues(step='Frequency I')
mdb.models['Original'].fieldOutputRequests['F-Output-2'].setValues(
variables=PRESELECT)
mdb.models['Original'].steps['Pull I'].Restart(frequency=10, overlay=OFF)
mdb.models['Original'].steps['Frequency I'].Restart(frequency=1)
session.viewports['Viewport: 1'].assemblyDisplay.setValues(loads=ON, bcs=ON,
predefinedFields=ON)
session.viewports['Viewport: 1'].assemblyDisplay.setValues(step='Pull I')
##
##  Apply encastre bc to left end
##
region = a.sets['Left']
mdb.models['Original'].EncastreBC(name='Left end', createStepName='Pull I',
region=region)
##
##  Fix all dofs at right end except for U1
##
region = a.sets['Right']
mdb.models['Original'].DisplacementBC(name='Right end',
createStepName='Pull I',
region=region, u2=0.0, u3=0.0, ur1=0.0, ur2=0.0, ur3=0.0)
##
##  Apply concentrated force to right end
##
region = a.sets['Right']
mdb.models['Original'].ConcentratedForce(name='Force',
createStepName='Pull I', region=region, cf1=4.e6)
##
##  Assign edge seed
##
p = mdb.models['Original'].parts['Pipe']
e = p.edges
edges=(e.findAt((1.25, 0.0, 0.0), ), )
p.seedEdgeByNumber(edges=edges, number=30)
##
##  Assign element type
##
elemType1 = mesh.ElemType(elemCode=PIPE32)
regions=(None,
e.findAt(((1.25, 0.0, 0.0), ), ), None, None)
p.setElementType(regions=regions, elemTypes=(elemType1, ))
##
##  Generate mesh
##
p.generateMesh()
##
##  Create job
##
mdb.Job(name='Pipe', model='Original',
description='Analysis of a 5 meter long pipe under axial load')
##
##  Save model database
##
mdb.saveAs('Pipe')
##
##  Copy model to 'Restart'
##
mdb.Model('Restart', mdb.models['Original'])
##
##  Edit restart model attributes
##
mdb.models['Restart'].setValues(restartJob='Pipe', restartStep='Frequency I',
restartIncrement=STEP_END)
a = mdb.models['Restart'].rootAssembly
session.viewports['Viewport: 1'].setValues(displayedObject=a)
##
##  Create general static step; insert after previous frequency step
##
mdb.models['Restart'].StaticStep(name='Pull II', previous='Frequency I',
description='Apply axial tensile load of 8.0 MN', timePeriod=1,
adiabatic=OFF, maxNumInc=100,
stabilizationMethod=NONE, timeIncrementationMethod=AUTOMATIC,
initialInc=0.1, minInc=1e-05, maxInc=1, matrixSolver=SOLVER_DEFAULT,
amplitude=RAMP, extrapolation=LINEAR, fullyPlastic="")
session.viewports['Viewport: 1'].assemblyDisplay.setValues(step='Pull II')
##
##  Create frequency extraction step
##
mdb.models['Restart'].FrequencyStep(name='Frequency II', previous='Pull II',
description='Extract modes and frequencies', numEigen=8,
maxEigen=None, shift=None, vectors=16, maxIterations=30,
eigensolver=SUBSPACE)
##
##  Modify output requests
##
mdb.models['Restart'].steps['Pull II'].Restart(frequency=10, overlay=OFF)
mdb.models['Restart'].steps['Frequency II'].Restart(frequency=1)
session.viewports['Viewport: 1'].assemblyDisplay.setValues(step='Frequency II')
session.viewports['Viewport: 1'].assemblyDisplay.setValues(loads=ON, bcs=ON,
predefinedFields=ON)
session.viewports['Viewport: 1'].assemblyDisplay.setValues(step='Pull II')
##
##  Double the magnitude of the applied force
##  in the second general step
##
mdb.models['Restart'].loads['Force'].setValuesInStep(stepName='Pull II',
cf1=8.e6)
##
##  Create a restart analysis job
##
mdb.Job(name='PipeRestart', model='Restart', type=RESTART,
explicitPrecision=SINGLE,
description='Restart analysis of a 5 meter long pipe under axial load',
userSubroutine='', numCpus=1, scratch='', echoPrint=OFF,
modelPrint=OFF, contactPrint=OFF, historyPrint=OFF)
#
a = mdb.models['Original'].rootAssembly
a.regenerate()
a = mdb.models['Restart'].rootAssembly
a.regenerate()
##
##  Save model database
##
mdb.saveAs('Pipe')
```

---

### A.12 Forming a channel
gsi_channel_caemodel.py
```
#
# Getting Started with Abaqus
#
# Script for forming portion channel example
#
from abaqus import *
from abaqusConstants import *
session.viewports['Viewport: 1'].makeCurrent()
session.viewports['Viewport: 1'].maximize()
session.journalOptions.setValues(replayGeometry=COORDINATE,
recoverGeometry=COORDINATE)
from caeModules import *
from driverUtils import executeOnCaeStartup
executeOnCaeStartup()
Mdb()
mdb.models.changeKey(fromName='Model-1', toName='standard')
##
##  Sketch profile of blank
##
s = mdb.models['standard'].ConstrainedSketch(name='__profile__',
sheetSize=0.25)
g, v, d = s.geometry, s.vertices, s.dimensions
s.sketchOptions.setValues(sheetSize=0.25, gridSpacing=0.005, grid=ON,
gridFrequency=2, constructionGeometry=ON, dimensionTextHeight=0.005,
decimalPlaces=3)
s.Line(point1=(-0.05, -0.005), point2=(0.05, -0.005))
s.Line(point1=(0.05, -0.005), point2=(0.05, 0.005))
s.Line(point1=(0.05, 0.005), point2=(-0.05, 0.005))
s.Line(point1=(-0.05, 0.005), point2=(-0.05, -0.005))
s.HorizontalDimension(vertex1=v.findAt((-0.05, 0.005)), vertex2=v.findAt((
0.05, 0.005)), textPoint=(0.0457058809697628, 0.0127279916778207),
value=0.1)
s.FixedConstraint(entity=g.findAt((0.0, -0.005)))
s.PerpendicularConstraint(entity1=g.findAt((-0.05, 0.0)), entity2=g.findAt((
0.0, 0.005)))
s.PerpendicularConstraint(entity1=g.findAt((0.05, 0.0)), entity2=g.findAt((
0.0, 0.005)))
s.VerticalDimension(vertex1=v.findAt((-0.05, -0.005)), vertex2=v.findAt((
-0.05, 0.005)), textPoint=(-0.0521911755204201, 0.000539974775165319),
value=0.001)
p = mdb.models['standard'].Part(name='Blank', dimensionality=TWO_D_PLANAR,
type=DEFORMABLE_BODY)
p = mdb.models['standard'].parts['Blank']
p.BaseShell(sketch=s)
p = mdb.models['standard'].parts['Blank']
session.viewports['Viewport: 1'].setValues(displayedObject=p)
del mdb.models['standard'].sketches['__profile__']
##
##  Sketch profile of punch
##
s0 = mdb.models['standard'].ConstrainedSketch(name='__profile__', sheetSize=0.25)
g, v, d = s0.geometry, s0.vertices, s0.dimensions
s0.sketchOptions.setValues(sheetSize=0.25, gridSpacing=0.005, grid=ON,
gridFrequency=2, constructionGeometry=ON, dimensionTextHeight=0.005,
decimalPlaces=3)
s0.Line(point1=(-0.06, 0.0), point2=(0.0, 0.0))
s0.Line(point1=(0.0, 0.0), point2=(0.0, 0.06))
s0.FilletByRadius(radius=0.005, curve1=g.findAt((-0.03, 0.0)), nearPoint1=(
-0.00207383744418621, 0.000262239947915077), curve2=g.findAt((0.0, 0.03)),
nearPoint2=(-0.00016310065984726, 0.00246503762900829))
session.viewports['Viewport: 1'].view.fitView()
mdb.models['standard'].ConstrainedSketch(name='Punch', objectToCopy=s0)
p = mdb.models['standard'].Part(name='Punch', dimensionality=TWO_D_PLANAR,
type=ANALYTIC_RIGID_SURFACE)
p = mdb.models['standard'].parts['Punch']
p.AnalyticRigidSurf2DPlanar(sketch=s0)
p = mdb.models['standard'].parts['Punch']
session.viewports['Viewport: 1'].setValues(displayedObject=p)
del mdb.models['standard'].sketches['__profile__']
#
#   Create holder
#
s = mdb.models['standard'].ConstrainedSketch(name='__profile__',
sheetSize=0.25)
g, v, d, c = s.geometry, s.vertices, s.dimensions, s.constraints
s.sketchOptions.setValues(decimalPlaces=3)
s.setPrimaryObject(option=STANDALONE)
s.sketchOptions.setValues(gridOrigin=(-0.026910743678459, 0.026910743678459))
s.retrieveSketch(sketch=mdb.models['standard'].sketches['Punch'])
s.mirror(mirrorLine=g.findAt((0.0, 0.0325)), objectList=(g.findAt((-0.0325,
0.0)), g.findAt((0.0, 0.0325)), g.findAt((-0.001464, 0.001464))))
p = mdb.models['standard'].Part(name='Holder', dimensionality=TWO_D_PLANAR,
type=ANALYTIC_RIGID_SURFACE)
p = mdb.models['standard'].parts['Holder']
p.AnalyticRigidSurf2DPlanar(sketch=s)
s.unsetPrimaryObject()
p = mdb.models['standard'].parts['Holder']
session.viewports['Viewport: 1'].setValues(displayedObject=p)
del mdb.models['standard'].sketches['__profile__']
#
#   Create die
#
s = mdb.models['standard'].ConstrainedSketch(name='__profile__',
sheetSize=0.25)
g, v, d, c = s.geometry, s.vertices, s.dimensions, s.constraints
s.sketchOptions.setValues(decimalPlaces=3)
s.setPrimaryObject(option=STANDALONE)
s.sketchOptions.setValues(gridOrigin=(-0.026910743678459, 0.026910743678459))
s.retrieveSketch(sketch=mdb.models['standard'].sketches['Punch'])
s.mirror(mirrorLine=g.findAt((0.0, 0.0325)), objectList=(g.findAt((-0.0325,
0.0)), g.findAt((0.0, 0.0325)), g.findAt((-0.001464, 0.001464))))
s.mirror(mirrorLine=g.findAt((0.0325, 0.0)), objectList=(g.findAt((0.0325,
0.0)), g.findAt((0.0, 0.0325)), g.findAt((0.001464, 0.001464))))
p = mdb.models['standard'].Part(name='Die', dimensionality=TWO_D_PLANAR,
type=ANALYTIC_RIGID_SURFACE)
p = mdb.models['standard'].parts['Die']
p.AnalyticRigidSurf2DPlanar(sketch=s)
s.unsetPrimaryObject()
p = mdb.models['standard'].parts['Die']
session.viewports['Viewport: 1'].setValues(displayedObject=p)
del mdb.models['standard'].sketches['__profile__']
##
##  Add reference point to die
##
p = mdb.models['standard'].parts['Die']
e = p.edges
p.ReferencePoint(point=p.InterestingPoint(
edge=e.findAt(coordinates=(0.003087, -0.000381, 0.0)), rule=CENTER))
##
##  Add reference point to holder
##
p = mdb.models['standard'].parts['Holder']
e = p.edges
p.ReferencePoint(point=p.InterestingPoint(
edge=e.findAt(coordinates=(0.003087, 0.000381, 0.0)), rule=CENTER))
##
##  Add reference point to punch
##
p = mdb.models['standard'].parts['Punch']
e = p.edges
p.ReferencePoint(point=p.InterestingPoint(
edge=e.findAt(coordinates=(-0.003087, 0.000381, 0.0)), rule=CENTER))
##
##  Create material 'Steel'
##
mdb.models['standard'].Material('Steel')
mdb.models['standard'].materials['Steel'].Elastic(table=((2.1E11, 0.3), ))
mdb.models['standard'].materials['Steel'].Plastic(table=((400.E6, 0.0), (
420.E6, 0.02), (500.E6, 0.2), (600.E6, 0.5)))
##
##  Create and assign solid section to blank
##
mdb.models['standard'].HomogeneousSolidSection(name='BlankSection',
material='Steel', thickness=1.0)
p = mdb.models['standard'].parts['Blank']
f = p.faces
faces = f.findAt(((-0.016667, -0.004667, 0.0), ))
region = regionToolset.Region(faces=faces)
p = mdb.models['standard'].parts['Blank']
p.SectionAssignment(region=region, sectionName='BlankSection', offset=0.0)
##
##  Define datum coordinate system
##
p = mdb.models['standard'].parts['Blank']
p.DatumCsysByDefault(coordSysType=CARTESIAN)
##
##  Assign material orientation to blank
##
p = mdb.models['standard'].parts['Blank']
f = p.faces
faces = f.findAt(((-0.016667, -0.004667, 0.0), ))
region = regionToolset.Region(faces=faces)
datum = p.datums[3]
p.MaterialOrientation(region=region, localCsys=datum)
a = mdb.models['standard'].rootAssembly
session.viewports['Viewport: 1'].setValues(displayedObject=a)
##
##  Set coordinate system (done by default)
##
a = mdb.models['standard'].rootAssembly
a.DatumCsysByDefault(CARTESIAN)
##
##  Instance the blank
##
p = mdb.models['standard'].parts['Blank']
a.Instance(name='Blank-1', part=p, dependent=ON)
a = mdb.models['standard'].rootAssembly
##
##  Instance the punch
##
p = mdb.models['standard'].parts['Punch']
a.Instance(name='Punch-1', part=p, dependent=ON)
##
##  Translate the punch
##
a = mdb.models['standard'].rootAssembly
p = a.instances['Punch-1']
p.translate(vector=(0.116, 0.0, 0.0))
##
##   Edge to edge constraints between punch and blank
##
e11 = a.instances['Punch-1'].edges
e12 = a.instances['Blank-1'].edges
a.EdgeToEdge(movableAxis=e11.findAt(coordinates=(0.06975, 0.0, 0.0)),
fixedAxis=e12.findAt(coordinates=(0.025, -0.004, 0.0)), flip=ON,
clearance=0.0)
session.viewports['Viewport: 1'].view.fitView()
e11 = a.instances['Punch-1'].edges
e12 = a.instances['Blank-1'].edges
a.EdgeToEdge(movableAxis=e11.findAt(coordinates=(0.116, 0.01575, 0.0)),
fixedAxis=e12.findAt(coordinates=(-0.05, -0.00425, 0.0)), flip=ON,
clearance=-0.05)
##
##  Instance the holder
##
p = mdb.models['standard'].parts['Holder']
a.Instance(name='Holder-1', part=p, dependent=ON)
p = a.instances['Holder-1']
p.translate(vector=(0.056, 0.0, 0.0))
session.viewports['Viewport: 1'].view.fitView()
##
##   Edge to edge constraints between holder and punch
##
e11 = a.instances['Holder-1'].edges
e12 = a.instances['Punch-1'].edges
a.EdgeToEdge(movableAxis=e11.findAt(coordinates=(0.056, 0.01875, 0.0)),
fixedAxis=e12.findAt(coordinates=(0.0, 0.01575, 0.0)), flip=OFF,
clearance=0.001)
e11 = a.instances['Holder-1'].edges
e12 = a.instances['Blank-1'].edges
a.EdgeToEdge(movableAxis=e11.findAt(coordinates=(0.04725, 0.0, 0.0)),
fixedAxis=e12.findAt(coordinates=(0.025, -0.004, 0.0)), flip=OFF,
clearance=0.0)
##
##  Instance the die
##
p = mdb.models['standard'].parts['Die']
a.Instance(name='Die-1', part=p, dependent=ON)
p = a.instances['Die-1']
p.translate(vector=(0.067, 0.0, 0.0))
session.viewports['Viewport: 1'].view.fitView()
##
##   Edge to edge constraints between die and blank (horizontal)
##
e11 = a.instances['Die-1'].edges
e12 = a.instances['Blank-1'].edges
a.EdgeToEdge(movableAxis=e11.findAt(coordinates=(0.067, -0.01875, 0.0)),
fixedAxis=e12.findAt(coordinates=(-0.05, -0.00425, 0.0)), flip=OFF,
clearance=-0.051)
e11 = a.instances['Die-1'].edges
e12 = a.instances['Blank-1'].edges
a.EdgeToEdge(movableAxis=e11.findAt(coordinates=(0.04725, 0.0, 0.0)),
fixedAxis=e12.findAt(coordinates=(-0.025, -0.005, 0.0)), flip=ON,
clearance=0.0)
p = a.instances['Blank-1']
p.translate(vector=(0.0, 0.009, 0.0))
a = mdb.models['standard'].rootAssembly
a.regenerate()
#
#   Create geometry set RefPunch
#
a = mdb.models['standard'].rootAssembly
r1 = a.instances['Punch-1'].referencePoints
refPoints1 = (r1[2], )
a.Set(referencePoints=refPoints1, name='RefPunch')
#
#   Create geometry set RefHolder
#
a = mdb.models['standard'].rootAssembly
r1 = a.instances['Holder-1'].referencePoints
refPoints1 = (r1[2], )
a.Set(referencePoints=refPoints1, name='RefHolder')
#
#   Create geometry set RefDie
#
a = mdb.models['standard'].rootAssembly
r1 = a.instances['Die-1'].referencePoints
refPoints1 = (r1[2], )
a.Set(referencePoints=refPoints1, name='RefDie')
#
#   Reset view
#
session.viewports['Viewport: 1'].view.setValues(width=0.0066561,
height=0.0042551, cameraPosition=(-0.048954, 0.0037356, 0.34938),
cameraTarget=(-0.048954, 0.0037356, 0))
#
#   Create geometry set Center
#
a = mdb.models['standard'].rootAssembly
e = a.instances['Blank-1'].edges
edges = e.findAt(((-0.05, 0.00475, 0.0), ))
a.Set(edges=edges, name='Center')
#
#   Create surface BlankTop
#
a = mdb.models['standard'].rootAssembly
e1 = a.instances['Blank-1'].edges
a.Surface(name='BlankTop', side1Edges=e1.findAt(((0.025, 0.005, 0.0), ), ))
#
#   Create surface BlankBot
#
a = mdb.models['standard'].rootAssembly
e1 = a.instances['Blank-1'].edges
a.Surface(name='BlankBot', side1Edges=e1.findAt(((-0.025, 0.004, 0.0), ), ))
session.viewports['Viewport: 1'].view.fitView()
#
#   Create surface PunchSurf
#
s = a.instances['Punch-1'].edges
side2Edges1 = s.findAt(((0.0, 0.02375, 0.0), ))
a.Surface(side2Edges=side2Edges1, name='PunchSurf')
#
#   Create surface HolderSurf
#
s = a.instances['Holder-1'].edges
side1Edges = s.findAt(((0.001, 0.02375, 0.0), ))
a.Surface(side1Edges=side1Edges, name='HolderSurf')
#
#   Create surface DieSurf
#
s = a.instances['Die-1'].edges
side2Edges = s.findAt(((0.001, -0.01475, 0.0), ))
a.Surface(side2Edges=side2Edges, name='DieSurf')
##
##  Create two static general steps
##
mdb.models['standard'].StaticStep(name='Holder force',
previous='Initial',
description='Apply holder force', timePeriod=1,
adiabatic=OFF, maxNumInc=100, stabilization=None,
timeIncrementationMethod=AUTOMATIC,
initialInc=0.05, minInc=1e-05, maxInc=1, matrixSolver=SOLVER_DEFAULT,
amplitude=RAMP, extrapolation=LINEAR, nlgeom=ON)
mdb.models['standard'].StaticStep(name='Move punch',
previous='Holder force',
description='Apply punch stroke', timePeriod=1,
adiabatic=OFF, maxNumInc=1000, stabilization=None,
timeIncrementationMethod=AUTOMATIC,
initialInc=0.05, minInc=1e-05, maxInc=1, matrixSolver=SOLVER_DEFAULT,
amplitude=RAMP, extrapolation=LINEAR)
##
##  Modify output requests
##
mdb.models['standard'].fieldOutputRequests['F-Output-1'].setValues(
variables=PRESELECT, frequency=20)
regionDef=a.sets['RefPunch']
mdb.models['standard'].HistoryOutputRequest(name='H-Output-2',
createStepName='Holder force',
variables=('RF2', 'U2'),
region=regionDef)
##
##  Create degree of freedom monitor
##
mdb.models['standard'].steps['Holder force'].Monitor(dof=2,
node=regionDef, frequency=1)
mdb.models['standard'].steps['Move punch'].Monitor(dof=2,
node=regionDef, frequency=1)
##
##  Print diagnostic data for contact
##
mdb.models['standard'].steps['Holder force'].DiagnosticPrint(frequency=1,
contact=ON, plasticity=OFF, residual=ON, solve=OFF)
mdb.models['standard'].steps['Move punch'].DiagnosticPrint(frequency=1,
contact=ON, plasticity=OFF, residual=ON, solve=OFF)
##
##  Reset view
##
session.viewports['Viewport: 1'].view.setValues(width=0.025757,
height=0.016466, cameraPosition=(-0.04834, 0.0033255, 0.34366),
cameraTarget=(-0.04834, 0.0033255, 0))
session.viewports['Viewport: 1'].assemblyDisplay.setValues(interactions=ON)
session.viewports['Viewport: 1'].view.fitView()
session.viewports['Viewport: 1'].assemblyDisplay.setValues(step='Initial')
##
##  Create contact property 'Fric'
##
mdb.models['standard'].ContactProperty('Fric')
mdb.models['standard'].interactionProperties['Fric'].TangentialBehavior(
formulation=PENALTY, directionality=ISOTROPIC, slipRateDependency=OFF,
pressureDependency=OFF, temperatureDependency=OFF, dependencies=0,
table=((0.1, ), ), shearStressLimit=None, maximumElasticSlip=FRACTION,
fraction=0.005, elasticSlipStiffness=None)
##
##  Create contact property 'NoFric'
##
mdb.models['standard'].ContactProperty('NoFric')
mdb.models['standard'].interactionProperties['NoFric'].TangentialBehavior(
formulation=FRICTIONLESS)
##
##  Create contact interaction 'Punch-Blank'
##
region1=a.surfaces['PunchSurf']
region2=a.surfaces['BlankTop']
mdb.models['standard'].SurfaceToSurfaceContactStd(name='Punch-Blank',
createStepName='Initial', master=region1, slave=region2,
sliding=FINITE, interactionProperty='NoFric')
##
##  Create contact interaction 'Holder-Blank'
##
region1=a.surfaces['HolderSurf']
region2=a.surfaces['BlankTop']
mdb.models['standard'].SurfaceToSurfaceContactStd(name='Holder-Blank',
createStepName='Initial', master=region1, slave=region2,
sliding=FINITE, interactionProperty='Fric')
##
##  Create contact interaction 'Die-Blank'
##
region1=a.surfaces['DieSurf']
region2=a.surfaces['BlankBot']
mdb.models['standard'].SurfaceToSurfaceContactStd(name='Die-Blank',
createStepName='Initial', master=region1, slave=region2,
sliding=FINITE, interactionProperty='Fric')
mdb.models['standard'].StdContactControl(name='stabilize',
automaticTolerances=OFF,
stabilizeChoice=AUTOMATIC,
dampFactor=0.001)
mdb.models['standard'].interactions['Punch-Blank'].setValuesInStep(
stepName='Move punch', contactControls='stabilize')
##
##
session.viewports['Viewport: 1'].view.fitView()
##
##  Create BCs in step "Establish contact"
##
region = a.sets['Center']
mdb.models['standard'].XsymmBC(name='CenterBC',
createStepName='Holder force', region=region)
region = a.sets['RefDie']
mdb.models['standard'].DisplacementBC(name='RefDieBC',
createStepName='Holder force', region=region,
u1=0.0, u2=0.0, ur3=0.0)
region = a.sets['RefHolder']
mdb.models['standard'].DisplacementBC(name='RefHolderBC',
createStepName='Holder force', region=region,
u1=0.0, ur3=0.0)
region = a.sets['RefPunch']
mdb.models['standard'].DisplacementBC(name='RefPunchBC',
createStepName='Holder force', region=region,
u1=0.0, u2=0.0, ur3=0.0)
##
##  Add holder force
##
region = a.sets['RefHolder']
mdb.models['standard'].ConcentratedForce(name='RefHolderForce',
createStepName='Holder force', region=region, cf2=-440000.0)
##
##  Push punch down in step  "Move punch"
##
session.viewports['Viewport: 1'].assemblyDisplay.setValues(step='Move punch')
mdb.models['standard'].boundaryConditions['RefPunchBC'].setValuesInStep(
stepName='Move punch', u2=-0.03)
session.viewports['Viewport: 1'].view.fitView()
##
##  Assign edge seeds
##
p = mdb.models['standard'].parts['Blank']
e = p.edges
pickedEdges = e.findAt(((-0.025, -0.005, 0.0), ), ((0.025, -0.004, 0.0), ))
p.seedEdgeByNumber(edges=pickedEdges, number=100)
pickedEdges = e.findAt(((-0.05, -0.00425, 0.0), ), ((0.05, -0.00475, 0.0), ))
p.seedEdgeByNumber(edges=pickedEdges, number=4)
##
##  Assign element type
##
elemType1 = mesh.ElemType(elemCode=CPE4R, elemLibrary=STANDARD,
secondOrderAccuracy=OFF, hourglassControl=ENHANCED, distortionControl=OFF)
elemType2 = mesh.ElemType(elemCode=CPE3, elemLibrary=STANDARD)
f = p.faces
faces = f
pickedRegions =(faces, )
p.setElementType(regions=pickedRegions, elemTypes=(elemType1, elemType2))
##
##  Use structured meshing
##
f = p.faces
pickedRegions = f
p.setMeshControls(regions=pickedRegions, technique=STRUCTURED)
##
##  Generate mesh
##
p.generateMesh()
session.viewports['Viewport: 1'].assemblyDisplay.geometryOptions.setValues(
geometryEdgesInShaded=OFF, datumPoints=OFF, datumAxes=OFF, datumPlanes=OFF,
datumCoordSystems=OFF)
session.viewports['Viewport: 1'].assemblyDisplay.setValues(mesh=OFF)
session.viewports['Viewport: 1'].assemblyDisplay.meshOptions.setValues(
meshTechnique=OFF)
##
##  Create job
##
mdb.Job(name='Channel', model='standard',
description='Analysis of the forming of a channel-static')
##
##  Save model database
##
mdb.saveAs('Channel')
##
##
##  Create explicit dynamics model
##
mdb.Model(name='explicit', objectToCopy=mdb.models['standard'])
#: The model "explicit" has been created.
p = mdb.models['explicit'].parts['Blank']
session.viewports['Viewport: 1'].setValues(displayedObject=p)
##
##  add density
##
mdb.models['explicit'].materials['Steel'].Density(table=((7800.0, ), ))
p = mdb.models['explicit'].parts['Holder']
session.viewports['Viewport: 1'].setValues(displayedObject=p)
##
##  add point mass to holder
##
r = p.referencePoints
refPoints=(r[2], )
region = regionToolset.Region(referencePoints=refPoints)
mdb.models['explicit'].parts['Holder'].engineeringFeatures.PointMassInertia(
name='mass', region=region, mass=0.1, alpha=0.0,
composite=0.0)
a = mdb.models['explicit'].rootAssembly
session.viewports['Viewport: 1'].setValues(displayedObject=a)
##
##  delete all but first step
##
del mdb.models['explicit'].steps['Move punch']
##
##  define set containing blank
##
f1 = a.instances['Blank-1'].faces
faces1 = f1
a.Set(faces=faces1, name='blank')
##
##  replace the remaining static step with an explicit dynamics step
##
mdb.models['explicit'].ExplicitDynamicsStep(name='Holder force',
previous='Initial', maintainAttributes=True, timePeriod=0.0001)
##
##  create a second explicit dynamics step
##
mdb.models['explicit'].ExplicitDynamicsStep(name='Move punch',
previous='Holder force', timePeriod=0.007,
description='Apply punch stroke')
##
##  define mass scaling
##
regionDef=mdb.models['explicit'].rootAssembly.sets['blank']
mdb.models['explicit'].steps['Holder force'].setValues(massScaling=((
SEMI_AUTOMATIC, regionDef, AT_BEGINNING, 5.0, 0.0, None, 0, 0, 0.0,
0.0, 0, None), ))
##
##  request RF2, U2 history output for punch reference point
##
regionDef=mdb.models['explicit'].rootAssembly.sets['RefPunch']
mdb.models['explicit'].HistoryOutputRequest(name='H-Output-2',
createStepName='Holder force', variables=('U2', 'RF2'),
region=regionDef, sectionPoints=DEFAULT, rebar=EXCLUDE,
filter=ANTIALIASING)
##
##  define smooth step amplitude curves
##
mdb.models['explicit'].SmoothStepAmplitude(name='smooth1', timeSpan=STEP,
data=((0.0, 0.0), (0.0001, 1.0)))
mdb.models['explicit'].SmoothStepAmplitude(name='smooth2', timeSpan=STEP,
data=((0.0, 0.0), (0.007, 1.0)))
##
##  use smooth step amplitude for holder force
##
mdb.models['explicit'].loads['RefHolderForce'].setValues(amplitude='smooth1')
##
##  use smooth step amplitude for punch bc
##
mdb.models['explicit'].boundaryConditions['RefPunchBC'].setValuesInStep(
stepName='Move punch', u2=-0.030, amplitude='smooth2')
elemType1 = mesh.ElemType(elemCode=CPE4R, elemLibrary=EXPLICIT,
secondOrderAccuracy=OFF, hourglassControl=ENHANCED, distortionControl=OFF)
elemType2 = mesh.ElemType(elemCode=CPE3, elemLibrary=EXPLICIT)
p = mdb.models['explicit'].parts['Blank']
f = p.faces
faces = f
pickedRegions =(faces, )
p.setElementType(regions=pickedRegions, elemTypes=(elemType1, elemType2))
a.regenerate()
p.generateMesh()
##
##  create job
##
mdb.Job(name='expChannel', model='explicit',
description='Analysis of the forming of a channel-quasistatic')
a = mdb.models['standard'].rootAssembly
a.regenerate()
a = mdb.models['explicit'].rootAssembly
a.regenerate()
mdb.save()
```
gsi_channel_caemodel_spring.py
```
#
# Getting Started with Abaqus
#
# Script for springback portion of channel example
#
from abaqus import *
from abaqusConstants import *
session.viewports['Viewport: 1'].makeCurrent()
session.viewports['Viewport: 1'].maximize()
session.journalOptions.setValues(replayGeometry=COORDINATE,
recoverGeometry=COORDINATE)
from caeModules import *
from driverUtils import executeOnCaeStartup
executeOnCaeStartup()
Mdb()
a = mdb.models['Model-1'].rootAssembly
session.viewports['Viewport: 1'].setValues(displayedObject=a)
openMdb('Channel.cae')
a = mdb.models['explicit'].rootAssembly
session.viewports['Viewport: 1'].setValues(displayedObject=a)
##
##  Springback analysis model
##
mdb.Model(name='import', objectToCopy=mdb.models['explicit'])
a = mdb.models['import'].rootAssembly
session.viewports['Viewport: 1'].setValues(displayedObject=a)
a.deleteFeatures(('Punch-1', 'Holder-1', 'Die-1', ))
del mdb.models['import'].rootAssembly.sets['RefDie']
del mdb.models['import'].rootAssembly.sets['RefHolder']
del mdb.models['import'].rootAssembly.sets['RefPunch']
del mdb.models['import'].rootAssembly.surfaces['BlankBot']
del mdb.models['import'].rootAssembly.surfaces['BlankTop']
del mdb.models['import'].rootAssembly.surfaces['DieSurf']
del mdb.models['import'].rootAssembly.surfaces['HolderSurf']
del mdb.models['import'].rootAssembly.surfaces['PunchSurf']
mdb.models['import'].interactions.delete(
('Die-Blank', 'Holder-Blank', 'Punch-Blank', ))
del mdb.models['import'].interactionProperties['Fric']
del mdb.models['import'].interactionProperties['NoFric']
del mdb.models['import'].steps['Move punch']
del mdb.models['import'].steps['Holder force']
region = a.sets['Center']
mdb.models['import'].XsymmBC(name='BC-1', createStepName='Initial',
region=region)
a = mdb.models['import'].rootAssembly
n1 = a.instances['Blank-1'].nodes
nodes1 = n1[2:3]
a.Set(nodes=nodes1, name='MidLeft')
region = a.sets['MidLeft']
mdb.models['import'].VelocityBC(name='BC-2', createStepName='Initial',
region=region, v1=UNSET, v2=SET, vr3=UNSET, amplitude=UNSET,
distributionType=UNIFORM, localCsys=None)
mdb.models['import'].StaticStep(name='springback', previous='Initial',
initialInc=0.1, nlgeom=ON, stabilizationMagnitude=0.0002,
stabilizationMethod=DISSIPATED_ENERGY_FRACTION, adaptiveDampingRatio=0.0)
instances=(a.instances['Blank-1'], )
mdb.models['import'].InitialState(updateReferenceConfiguration=OFF,
fileName='expChannel', endStep=LAST_STEP, endIncrement=STEP_END,
name='Field-1', createStepName='Initial', instances=instances)
mdb.Job(name='springback', model='import',
description='Analysis of the forming of a channel-springback')
a = mdb.models['import'].rootAssembly
a.regenerate()
mdb.save()
```

---

### A.13 Shearing of a lap joint
gsi_lap_joint_caemodel.py
```
#
# Getting Started with Abaqus: Interactive Edition
#
# Lap joint example
#
from abaqus import *
from abaqusConstants import *
session.viewports['Viewport: 1'].makeCurrent()
session.viewports['Viewport: 1'].maximize()
from caeModules import *
from driverUtils import executeOnCaeStartup
executeOnCaeStartup()
Mdb()
session.viewports['Viewport: 1'].setValues(displayedObject=None)
s = mdb.models['Model-1'].ConstrainedSketch(name='__profile__', sheetSize=30.0)
g, v, d, c = s.geometry, s.vertices, s.dimensions, s.constraints
s.setPrimaryObject(option=STANDALONE)
s.rectangle(point1=(0.0, 0.0), point2=(30.0, 10.0))
p = mdb.models['Model-1'].Part(name='plate', dimensionality=THREE_D,
type=DEFORMABLE_BODY)
p = mdb.models['Model-1'].parts['plate']
p.BaseSolidExtrude(sketch=s, depth=1.5)
s.unsetPrimaryObject()
p = mdb.models['Model-1'].parts['plate']
session.viewports['Viewport: 1'].setValues(displayedObject=p)
del mdb.models['Model-1'].sketches['__profile__']
p = mdb.models['Model-1'].parts['plate']
c, f, e, v, d  = p.cells, p.faces, p.edges, p.vertices, p.datums
t = p.MakeSketchTransform(sketchPlane=f.findAt(coordinates=(10.0, 3.333333,
1.5)), sketchUpEdge=e.findAt(coordinates=(30.0, 7.5, 1.5)),
sketchPlaneSide=SIDE1, sketchOrientation=RIGHT, origin=(15.0, 5.0, 1.5))
s = mdb.models['Model-1'].ConstrainedSketch(name='__profile__',
sheetSize=63.31, gridSpacing=1.58, transform=t)
g, v, d, c = s.geometry, s.vertices, s.dimensions, s.constraints
s.setPrimaryObject(option=SUPERIMPOSE)
p = mdb.models['Model-1'].parts['plate']
p.projectReferencesOntoSketch(sketch=s, filter=COPLANAR_EDGES)
s.CircleByCenterPerimeter(center=(-9.48, -5.0), point1=(-9.48, -7.9))
s.CoincidentConstraint(entity1=v.findAt((-9.48, -5.0)), entity2=g.findAt((0.0,
-5.0)))
s.HorizontalDimension(vertex1=v.findAt((-15.0, -5.0)), vertex2=v.findAt((
-9.48, -5.0)), textPoint=(-10.4236354827881, -9.93480682373047), value=7.5)
s.RadialDimension(curve=g.findAt((-7.5, -2.1)), textPoint=(-2.11909103393555,
-9.19041156768799), radius=2.5)
p.CutExtrude(sketchPlane=f.findAt(coordinates=(10.0, 3.333333, 1.5)),
sketchUpEdge=e.findAt(coordinates=(30.0, 7.5, 1.5)),
sketchPlaneSide=SIDE1, sketchOrientation=RIGHT, sketch=s,
flipExtrudeDirection=OFF)
s.unsetPrimaryObject()
del mdb.models['Model-1'].sketches['__profile__']
c, f, e, v, d  = p.cells, p.faces, p.edges, p.vertices, p.datums
s = mdb.models['Model-1'].ConstrainedSketch(name='__profile__',
sheetSize=20.0)
g, v, d, c = s.geometry, s.vertices, s.dimensions, s.constraints
s.setPrimaryObject(option=STANDALONE)
s.ConstructionLine(point1=(0.0, -10.0), point2=(0.0, 10.0))
s.FixedConstraint(entity=g.findAt((0.0, 0.0)))
s.Line(point1=(0.0, 2.5), point2=(0.0, -2.52870798110962))
s.VerticalConstraint(entity=g.findAt((0.0, -2.277273)), addUndoState=False)
s.ParallelConstraint(entity1=g.findAt((0.0, 2222231.04)), entity2=g.findAt((
0.0, -2.277273)), addUndoState=False)
s.CoincidentConstraint(entity1=v.findAt((0.0, 2.5)), entity2=g.findAt((0.0,
2222231.04)), addUndoState=False)
s.CoincidentConstraint(entity1=v.findAt((0.0, -2.528708)), entity2=g.findAt((
0.0, 2222231.04)), addUndoState=False)
s.Line(point1=(0.0, -2.52870798110962), point2=(2.625, -2.52870798110962))
s.HorizontalConstraint(entity=g.findAt((1.3125, -2.528708)),
addUndoState=False)
s.PerpendicularConstraint(entity1=g.findAt((0.0, -2.277273)),
entity2=g.findAt((1.3125, -2.528708)), addUndoState=False)
s.Line(point1=(2.625, -2.52870798110962), point2=(2.625, -1.625))
s.VerticalConstraint(entity=g.findAt((2.625, -2.076854)), addUndoState=False)
s.PerpendicularConstraint(entity1=g.findAt((1.3125, -2.528708)),
entity2=g.findAt((2.625, -2.076854)), addUndoState=False)
s.Line(point1=(2.625, -1.625), point2=(1.5, -1.625))
s.HorizontalConstraint(entity=g.findAt((2.0625, -1.625)), addUndoState=False)
s.PerpendicularConstraint(entity1=g.findAt((2.625, -2.076854)),
entity2=g.findAt((2.0625, -1.625)), addUndoState=False)
s.Line(point1=(1.5, -1.625), point2=(1.5, 1.75))
s.VerticalConstraint(entity=g.findAt((1.5, 0.0625)), addUndoState=False)
s.PerpendicularConstraint(entity1=g.findAt((2.0625, -1.625)),
entity2=g.findAt((1.5, 0.0625)), addUndoState=False)
s.Line(point1=(1.5, 1.75), point2=(2.625, 1.75))
s.HorizontalConstraint(entity=g.findAt((2.0625, 1.75)), addUndoState=False)
s.PerpendicularConstraint(entity1=g.findAt((1.5, 0.0625)), entity2=g.findAt((
2.0625, 1.75)), addUndoState=False)
s.Line(point1=(2.625, 1.75), point2=(2.625, 2.5))
s.VerticalConstraint(entity=g.findAt((2.625, 2.125)), addUndoState=False)
s.PerpendicularConstraint(entity1=g.findAt((2.0625, 1.75)), entity2=g.findAt((
2.625, 2.125)), addUndoState=False)
s.Line(point1=(2.625, 2.5), point2=(0.0, 2.5))
s.HorizontalConstraint(entity=g.findAt((1.3125, 2.5)), addUndoState=False)
s.PerpendicularConstraint(entity1=g.findAt((2.625, 2.125)), entity2=g.findAt((
1.3125, 2.5)), addUndoState=False)
s.EqualLengthConstraint(entity1=g.findAt((1.3125, -2.528708)),
entity2=g.findAt((1.3125, 2.5)))
s.ObliqueDimension(vertex1=v.findAt((0.0, -2.528708)), vertex2=v.findAt((
2.625, -2.528708)), textPoint=(0.781737446784973, -3.08692169189453),
value=4.0)
s.DistanceDimension(entity1=g.findAt((0.0, 2222231.04)), entity2=g.findAt((
1.5, 0.0625)), textPoint=(1.5, -1.02153098583221), value=2.5)
session.viewports['Viewport: 1'].view.fitView()
s.ObliqueDimension(vertex1=v.findAt((2.5, -1.625)), vertex2=v.findAt((2.5,
1.75)), textPoint=(3.08898115158081, 0.803566813468933), value=3.0)
s.EqualLengthConstraint(entity1=g.findAt((4.0, 2.125)), entity2=g.findAt((4.0,
-1.889354)))
s.ObliqueDimension(vertex1=v.findAt((4.0, 1.573764)), vertex2=v.findAt((4.0,
2.323764)), textPoint=(4.55753326416016, 1.82851922512054), value=1.5)
session.viewports['Viewport: 1'].view.fitView()
s.move(vector=(0.0, -1.07376400629679), objectList=(g.findAt((0.0,
1925933.568)), g.findAt((0.0, -2.866236)), g.findAt((2.0, -2.926236)),
g.findAt((4.0, -2.176236)), g.findAt((3.25, -1.426236)), g.findAt((2.5,
0.073764)), g.findAt((3.25, 1.573764)), g.findAt((4.0, 2.323764)),
g.findAt((2.0, 3.073764))))
session.viewports['Viewport: 1'].view.fitView()
p = mdb.models['Model-1'].Part(name='rivet', dimensionality=THREE_D,
type=DEFORMABLE_BODY)
p = mdb.models['Model-1'].parts['rivet']
p.BaseSolidRevolve(sketch=s, angle=180.0, flipRevolveDirection=OFF)
s.unsetPrimaryObject()
p = mdb.models['Model-1'].parts['rivet']
session.viewports['Viewport: 1'].setValues(displayedObject=p)
del mdb.models['Model-1'].sketches['__profile__']
p = mdb.models['Model-1'].parts['rivet']
c, d, e, f, v = p.cells, p.datums, p.edges, p.faces, p.vertices
p.Round(radius=0.75, edgeList=(e.findAt(coordinates=(2.828427, 2.0, 2.828427)),
))
c, f, e, v, d  = p.cells, p.faces, p.edges, p.vertices, p.datums
p.Chamfer(length=0.75, edgeList=(e.findAt(coordinates=(2.828427, -4.0,
2.828427)), ))
c, f, e, v, d  = p.cells, p.faces, p.edges, p.vertices, p.datums
a = mdb.models['Model-1'].rootAssembly
session.viewports['Viewport: 1'].setValues(displayedObject=a)
a.DatumCsysByDefault(CARTESIAN)
p = mdb.models['Model-1'].parts['plate']
a.Instance(name='plate-1', part=p, dependent=ON)
a.Instance(name='plate-2', part=p, dependent=ON)
p1 = a.instances['plate-2']
p1.translate(vector=(33.0, 0.0, 0.0))
a.rotate(
instanceList=('plate-2', ),
axisPoint=(33.0, 10.0, 1.5),
axisDirection=(0.0, -1.0, 0.0),
angle=180.0)
f1 = a.instances['plate-2'].faces
f2 = a.instances['plate-1'].faces
a.FaceToFace(
movablePlane=f1.findAt(coordinates=(25.633485, 4.98924, 3.0)),
fixedPlane=f2.findAt(coordinates=(22.0, 6.666667, 0.0)),
flip=ON,
clearance=0.0)
a.Coaxial(
movableAxis=f1.findAt(coordinates=(23.005337, 0.163274, -0.5)),
fixedAxis=f2.findAt(coordinates=(9.994663, 0.163274, 0.5)),
flip=ON)
p = mdb.models['Model-1'].parts['rivet']
a.Instance(name='rivet-1', part=p, dependent=ON)
p1 = a.instances['rivet-1']
p1.translate(vector=(34.8, 0.0, 0.0))
f1 = a.instances['rivet-1'].faces
f2 = a.instances['plate-2'].faces
a.Coaxial(
movableAxis=f1.findAt(coordinates=(32.305337, -0.5, 0.163274)),
fixedAxis=f2.findAt(coordinates=(5.005337, 0.163274, -0.5)),
flip=ON)
a.rotate(
instanceList=('rivet-1', ),
axisPoint=(7.5, 0.0, 1.5),
axisDirection=(0.0, 0.0, 1.5),
angle=180.0)
p = mdb.models['Model-1'].parts['plate']
c = p.cells
e = p.edges
pickedRegions = c.findAt(((3.333333, 0.0, 1.0), ))
p.setMeshControls(regions=pickedRegions, allowMapped=True)
p.seedPart(size=1.2, deviationFactor=0.1)
import re, uti
if re.search('Student', uti.getProductVersion()):
p.seedPart(size=1.75, deviationFactor=0.05)
elemType1 = mesh.ElemType(elemCode=C3D8I, elemLibrary=STANDARD,
secondOrderAccuracy=OFF, distortionControl=DEFAULT)
elemType2 = mesh.ElemType(elemCode=C3D6, elemLibrary=STANDARD)
elemType3 = mesh.ElemType(elemCode=C3D4, elemLibrary=STANDARD)
cells = c
pickedRegions =(cells, )
p.setElementType(
regions=pickedRegions,
elemTypes=(elemType1, elemType2, elemType3))
p.generateMesh()
p = mdb.models['Model-1'].parts['rivet']
c = p.cells
e = p.edges
p.seedPart(size=0.5, deviationFactor=0.1)
if re.search('Student', uti.getProductVersion()):
p.seedPart(size=1., deviationFactor=0.1)
pickedRegions = c.findAt(((2.139505, -4.0, 0.241064), ))
p.setMeshControls(
regions=pickedRegions,
elemShape=HEX_DOMINATED,
technique=SWEEP,
algorithm=ADVANCING_FRONT,
allowMapped=True)
elemType1 = mesh.ElemType(elemCode=C3D8R, elemLibrary=STANDARD,
kinematicSplit=AVERAGE_STRAIN, secondOrderAccuracy=OFF,
hourglassControl=DEFAULT, distortionControl=DEFAULT)
elemType2 = mesh.ElemType(elemCode=C3D6, elemLibrary=STANDARD)
elemType3 = mesh.ElemType(elemCode=C3D4, elemLibrary=STANDARD)
cells = c
pickedRegions =(cells, )
p.setElementType(
regions=pickedRegions,
elemTypes=(elemType1, elemType2, elemType3))
p.generateMesh()
a.regenerate()
f1 = a.instances['plate-2'].faces
faces1 = f1.findAt(((11.666667, 0.0, -1.0), ), ((-1.666667, 0.0, -0.5), ))
f2 = a.instances['plate-1'].faces
faces2 = f2.findAt(((3.333333, 0.0, 1.0), ), ((16.666667, 0.0, 0.5), ))
f3 = a.instances['rivet-1'].faces
faces3 = f3.findAt(((4.0, 0.0, -1.75), ), ((9.416667, 0.0, -2.5), ))
a.Set(faces=faces1+faces2+faces3, name='symm')
f1 = a.instances['plate-1'].faces
faces1 = f1.findAt(((30.0, 6.666667, 1.0), ))
a.Set(faces=faces1, name='pull')
f1 = a.instances['plate-2'].faces
faces1 = f1.findAt(((-15.0, 6.666667, -1.0), ))
a.Set(faces=faces1, name='fix')
v1 = a.instances['plate-2'].vertices
verts1 = v1.findAt(((-15.0, 0.0, -1.5), ))
a.Set(vertices=verts1, name='corner')
mdb.models['Model-1'].Material(name='aluminum')
mdb.models['Model-1'].materials['aluminum'].Density(table=((0.0028, ), ))
mdb.models['Model-1'].materials['aluminum'].Elastic(table=((71700.0, 0.33), ))
mdb.models['Model-1'].materials['aluminum'].Plastic(table=(
(350.0, 0.0),
(368.71, 0.001),
(376.5, 0.002),
(391.98, 0.005),
(403.15, 0.008),
(412.36, 0.011),
(422.87, 0.015),
(444.17, 0.025),
(461.5, 0.035),
(507.9, 0.07),
(581.5, 0.15),
(649.17, 0.25),
(704.22, 0.35),
(728.78, 0.4),
(751.85, 0.45),
(773.68, 0.5),
(794.44, 0.55),
(814.28, 0.6)))
mdb.models['Model-1'].Material(name='titanium')
mdb.models['Model-1'].materials['titanium'].Density(table=((0.0044, ), ))
mdb.models['Model-1'].materials['titanium'].Elastic(table=((112000.0, 0.34), ))
mdb.models['Model-1'].materials['titanium'].Plastic(table=(
(907.0, 0.0),
(934.86, 0.001),
(944.28, 0.002),
(961.77, 0.005),
(973.73, 0.008),
(983.28, 0.011),
(993.89, 0.015),
(1014.7, 0.025),
(1023.3, 0.03),
(1051.1, 0.05),
(1099.8, 0.1),
(1129.0, 0.14),
(1164.9, 0.2),
(1190.2, 0.25),
(1212.8, 0.3)))
mdb.models['Model-1'].HomogeneousSolidSection(
name='plate',
material='aluminum',
thickness=1.0)
p = mdb.models['Model-1'].parts['plate']
c = p.cells
cells = c
region = regionToolset.Region(cells=cells)
p.SectionAssignment(
region=region,
sectionName='plate',
offset=0.0)
mdb.models['Model-1'].HomogeneousSolidSection(
name='rivet',
material='titanium',
thickness=1.0)
p = mdb.models['Model-1'].parts['rivet']
c = p.cells
cells = c
region = regionToolset.Region(cells=cells)
p.SectionAssignment(
region=region,
sectionName='rivet',
offset=0.0)
a.regenerate()
session.viewports['Viewport: 1'].view.fitView()
mdb.models['Model-1'].StaticStep(
name='Step-1',
previous='Initial',
maxNumInc=100,
stabilizationMethod=NONE,
initialInc=0.05,
nlgeom=ON)
region = a.sets['fix']
mdb.models['Model-1'].DisplacementBC(
name='Fix',
createStepName='Step-1',
region=region,
u1=0.0)
region = a.sets['pull']
mdb.models['Model-1'].DisplacementBC(
name='Pull',
createStepName='Step-1',
region=region,
u1=2.5)
region = a.sets['symm']
mdb.models['Model-1'].DisplacementBC(
name='Symmetry',
createStepName='Step-1',
region=region,
u2=0.0)
region = a.sets['corner']
mdb.models['Model-1'].DisplacementBC(
name='RB',
createStepName='Step-1',
region=region,
u3=0.0)
mdb.models['Model-1'].ContactProperty('fric')
mdb.models['Model-1'].interactionProperties['fric'].TangentialBehavior(
formulation=PENALTY,
directionality=ISOTROPIC,
slipRateDependency=OFF,
pressureDependency=OFF,
temperatureDependency=OFF,
dependencies=0,
table=((0.05, ), ),
shearStressLimit=None,
maximumElasticSlip=FRACTION,
fraction=0.005,
elasticSlipStiffness=None)
mdb.models['Model-1'].ContactStd(name='Int-1', createStepName='Initial')
mdb.models['Model-1'].interactions['Int-1'].includedPairs.setValuesInStep(
stepName='Initial',
useAllstar=ON)
mdb.models['Model-1'].interactions['Int-1'].contactPropertyAssignments.appendInStep(
stepName='Initial',
assignments=((GLOBAL, SELF, 'fric'), ))
mdb.Job(
name='lap_joint',
model='Model-1',
type=ANALYSIS)
mdb.saveAs(pathName='lap_joint')
```
lap_joint_alum.txt
```
0.0000, 0.000000000
350.00, 0.004881450
368.71, 0.006142399
376.50, 0.007251046
391.98, 0.010466946
403.15, 0.013622734
412.36, 0.016751185
422.87, 0.020897768
444.17, 0.031194840
461.50, 0.041436541
507.90, 0.077083682
581.50, 0.158110181
649.17, 0.259053975
704.22, 0.359821757
728.78, 0.410164296
751.85, 0.460486053
773.68, 0.510790516
794.44, 0.561080056
814.28, 0.611356764
```
lap_joint_titanium.txt
```
0.0000, 0.000000000
907.00, 0.008098214
934.86, 0.009346964
944.28, 0.010431071
961.77, 0.013587232
973.73, 0.016694018
983.28, 0.019779286
993.89, 0.023874018
1014.7, 0.034059821
1023.3, 0.039136607
1051.1, 0.059384821
1099.8, 0.109819643
1129.0, 0.150080357
1164.9, 0.210400893
1190.2, 0.260626786
1212.8, 0.310828571
```

---

### A.14 Circuit board drop test
gxi_circuit_caemodel.py
```
#
# Getting Started with Abaqus: Interactive Edition
#
# Script for circuit board drop test example
#
from abaqus import *
from abaqusConstants import *
backwardCompatibility.setValues(includeDeprecated=True, reportDeprecated=False)
session.viewports['Viewport: 1'].makeCurrent()
session.viewports['Viewport: 1'].maximize()
session.journalOptions.setValues(replayGeometry=COORDINATE,
recoverGeometry=COORDINATE)
from caeModules import *
from driverUtils import executeOnCaeStartup
executeOnCaeStartup()
Mdb()
session.viewports['Viewport: 1'].setValues(displayedObject=None)
mdb.models.changeKey(fromName='Model-1', toName='circuitBoard')
s = mdb.models['circuitBoard'].ConstrainedSketch(name='__profile__',
sheetSize=0.1)
g, v, d = s.geometry, s.vertices, s.dimensions
s.sketchOptions.setValues(sheetSize=0.1, gridSpacing=0.002, grid=ON,
gridFrequency=2, constructionGeometry=ON, dimensionTextHeight=0.002,
decimalPlaces=3)
s.rectangle(point1=(-0.01, -0.012), point2=(0.01, 0.012))
p = mdb.models['circuitBoard'].Part(name='Packaging', dimensionality=THREE_D,
type=DEFORMABLE_BODY)
p = mdb.models['circuitBoard'].parts['Packaging']
p.BaseSolidExtrude(sketch=s, depth=0.11)
s.unsetPrimaryObject()
session.viewports['Viewport: 1'].setValues(displayedObject=p)
del mdb.models['circuitBoard'].sketches['__profile__']
p = mdb.models['circuitBoard'].parts['Packaging']
session.viewports['Viewport: 1'].setValues(displayedObject=p)
p = mdb.models['circuitBoard'].parts['Packaging']
f, e = p.faces, p.edges
t = p.MakeSketchTransform(sketchPlane=f.findAt(coordinates=(-0.003333, -0.004,
0.11)), sketchUpEdge=e.findAt(coordinates=(0.01, 0.006, 0.11)),
sketchPlaneSide=SIDE1, sketchOrientation=RIGHT, origin=(0.0, 0.0, 0.11))
s = mdb.models['circuitBoard'].ConstrainedSketch(name='__profile__',
sheetSize=0.228, gridSpacing=0.005, transform=t)
g, v, d, c = s.geometry, s.vertices, s.dimensions, s.constraints
s.sketchOptions.setValues(decimalPlaces=3)
s.setPrimaryObject(option=SUPERIMPOSE)
p = mdb.models['circuitBoard'].parts['Packaging']
p.projectReferencesOntoSketch(sketch=s, filter=COPLANAR_EDGES)
s.ConstructionLine(point1=(0.0, 0.0), angle=90.0)
s.VerticalConstraint(entity=g.findAt((0.0, 0.5)), addUndoState=False)
s.FixedConstraint(entity=g.findAt((0.0, 0.5)))
session.viewports['Viewport: 1'].view.setValues(nearPlane=0.0543671,
farPlane=0.180597, width=0.0480393, height=0.0404284)
s.rectangle(point1=(-0.0025, 0.01625), point2=(0.0025, 0.005))
s.SymmetryConstraint(entity1=g.findAt((-0.0025, 0.010625)), entity2=g.findAt((
0.0025, 0.010625)), symmetryAxis=g.findAt((0.0, 0.5)))
s.ObliqueDimension(vertex1=v.findAt((-0.0025, 0.005)), vertex2=v.findAt((
0.0025, 0.005)), textPoint=(0.0015479710418731, 0.00119286333210766),
value=0.002)
s.VerticalDimension(vertex1=v.findAt((0.01, 0.012)), vertex2=v.findAt((0.001,
0.005)), textPoint=(0.013351246714592, 0.00686702458187938), value=0.012)
p = mdb.models['circuitBoard'].parts['Packaging']
f1, e1 = p.faces, p.edges
p.CutExtrude(sketchPlane=f1.findAt(coordinates=(-0.003333, -0.004, 0.11)),
sketchUpEdge=e1.findAt(coordinates=(0.01, 0.006, 0.11)),
sketchPlaneSide=SIDE1, sketchOrientation=RIGHT, sketch=s,
flipExtrudeDirection=OFF)
s.unsetPrimaryObject()
del mdb.models['circuitBoard'].sketches['__profile__']
p.DatumPointByMidPoint(point1=p.InterestingPoint(edge=e.findAt(coordinates=(
0.0005, 0.0, 0.11)), rule=MIDDLE), point2=p.InterestingPoint(
edge=e.findAt(coordinates=(-0.0005, 0.0, 0.0)), rule=MIDDLE))
s = mdb.models['circuitBoard'].Sketch(name='__profile__', sheetSize=0.5)
g, v, d = s.geometry, s.vertices, s.dimensions
s.sketchOptions.setValues(sheetSize=0.5, gridSpacing=0.01, grid=ON,
gridFrequency=2, constructionGeometry=ON, dimensionTextHeight=0.01,
decimalPlaces=3)
s.rectangle(point1=(0.0, 0.0), point2=(0.1, 0.15))
session.viewports['Viewport: 1'].view.fitView()
p = mdb.models['circuitBoard'].Part(name='Board', dimensionality=THREE_D,
type=DEFORMABLE_BODY)
p = mdb.models['circuitBoard'].parts['Board']
p.BaseShell(sketch=s)
p = mdb.models['circuitBoard'].parts['Board']
session.viewports['Viewport: 1'].setValues(displayedObject=p)
del mdb.models['circuitBoard'].sketches['__profile__']
p = mdb.models['circuitBoard'].parts['Board']
v = p.vertices
p.DatumPointByOffset(point=v.findAt(coordinates=(0.0, 0.0, 0.0)), vector=(
0.01, 0.135, 0.0))
p.DatumPointByOffset(point=v.findAt(coordinates=(0.0, 0.0, 0.0)), vector=(
0.07, 0.09, 0.0))
p.DatumPointByOffset(point=v.findAt(coordinates=(0.0, 0.0, 0.0)), vector=(
0.08, 0.03, 0.0))
s = mdb.models['circuitBoard'].Sketch(name='__profile__', sheetSize=0.5)
g, v, d = s.geometry, s.vertices, s.dimensions
s.sketchOptions.setValues(sheetSize=0.5, gridSpacing=0.01, grid=ON,
gridFrequency=2, constructionGeometry=ON, dimensionTextHeight=0.01,
decimalPlaces=3)
s.rectangle(point1=(-0.1, -0.1), point2=(0.1, 0.1))
p = mdb.models['circuitBoard'].Part(name='Floor', dimensionality=THREE_D,
type=DISCRETE_RIGID_SURFACE)
p = mdb.models['circuitBoard'].parts['Floor']
p.BaseShell(sketch=s)
p = mdb.models['circuitBoard'].parts['Floor']
session.viewports['Viewport: 1'].setValues(displayedObject=p)
del mdb.models['circuitBoard'].sketches['__profile__']
p = mdb.models['circuitBoard'].parts['Floor']
p.ReferencePoint(point=(0.0, 0.0, 0.0))
session.viewports['Viewport: 1'].setValues(displayedObject=p)
mdb.models['circuitBoard'].Material('PCB')
mdb.models['circuitBoard'].materials['PCB'].Elastic(table=((45.e9, 0.3), ))
mdb.models['circuitBoard'].materials['PCB'].Density(table=((500.0, ), ))
mdb.models['circuitBoard'].Material('Foam')
mdb.models['circuitBoard'].materials['Foam'].Elastic(table=((3.e6, 0.0), ))
mdb.models['circuitBoard'].materials['Foam'].Density(table=((100.0, ), ))
mdb.models['circuitBoard'].materials['Foam'].CrushableFoam(table=((1.1, 0.1),))
mdb.models['circuitBoard'].materials['Foam'].crushableFoam.CrushableFoamHardening(table=(
(220000.0, 0.0), (246510.0, 0.1), (272940.0, 0.2), (299020.0, 0.3),
(324550.0, 0.4), (349350.0, 0.5), (373260.0, 0.6), (396170.0, 0.7),
(418010.0, 0.8), (438720.0, 0.9), (458270.0, 1.0), (493840.0, 1.2),
(524840.0, 1.4), (551530.0, 1.6), (574310.0, 1.8), (593590.0, 2.0),
(629360.0, 2.5), (651990.0, 3.0), (683340.0, 5.0), (688330.0, 10.0)))
mdb.models['circuitBoard'].HomogeneousShellSection(name='BoardSection',
preIntegrate=OFF, material='PCB', thickness=0.002,
poissonDefinition=DEFAULT, temperature=GRADIENT, integrationRule=SIMPSON,
numIntPts=5)
mdb.models['circuitBoard'].HomogeneousSolidSection(name='FoamSection',
material='Foam', thickness=1.0)
p = mdb.models['circuitBoard'].parts['Board']
session.viewports['Viewport: 1'].setValues(displayedObject=p)
f = p.faces
faces = f
region = regionToolset.Region(faces=faces)
p.SectionAssignment(region=region, sectionName='BoardSection')
p = mdb.models['circuitBoard'].parts['Packaging']
session.viewports['Viewport: 1'].setValues(displayedObject=p)
c = p.cells
cells = c
region = regionToolset.Region(cells=cells)
p.SectionAssignment(region=region, sectionName='FoamSection')
p = mdb.models['circuitBoard'].parts['Board']
session.viewports['Viewport: 1'].setValues(displayedObject=p)
e = p.edges
p.DatumCsysByTwoLines(CARTESIAN,
line1=e.findAt(coordinates=(0.025, 0.0, 0.0)),
line2=e.findAt(coordinates=(0.1, 0.0375, 0.0)), name='Datum csys-1')
f = p.faces
faces = f
region = regionToolset.Region(faces=faces)
datums = p.datums[6]
p.MaterialOrientation(region=region, localCsys=datums, axis=AXIS_3)
a = mdb.models['circuitBoard'].rootAssembly
session.viewports['Viewport: 1'].setValues(displayedObject=a)
a.DatumCsysByDefault(CARTESIAN)
p = mdb.models['circuitBoard'].parts['Floor']
a.Instance(name='Floor-1', part=p, dependent=ON)
a.DatumPointByCoordinate(coords=(0.0, 0.0, 0.0))
a.DatumPointByCoordinate(coords=(0.5, 0.707, 0.25))
d = a.datums
a.DatumAxisByTwoPoint(point1=d[4], point2=d[5])
p = mdb.models['circuitBoard'].parts['Packaging']
a.Instance(name='Packaging-1', part=p, dependent=ON)
mdb.models['circuitBoard'].rootAssembly.setValues(
regenerateConstraintsTogether=OFF)
e = a.instances['Packaging-1'].edges
d = a.datums
a.EdgeToEdge(movableAxis=e.findAt(coordinates=(-0.01, -0.012, 0.0275)),
fixedAxis=d[6], flip=ON)
a.DatumPointByCoordinate(coords=(-0.5, 0.707, -0.5))
d = a.datums
a.DatumPlaneByLinePoint(line=d[6], point=d[10])
f = a.instances['Packaging-1'].faces
d = a.datums
a.FaceToFace(movablePlane=f.findAt(coordinates=(0.0179891354276455,
0.00658330416135736, 0.012563775694313)), fixedPlane=d[11], flip=ON,
clearance=0.0)
v = a.instances['Packaging-1'].vertices
r = a.instances['Floor-1'].referencePoints
a.CoincidentPoint(movablePoint=v.findAt(coordinates=(-0.0303476233973587,
-0.0429115394838653, -0.0151738116986794)), fixedPoint=r[2])
p = a.instances['Packaging-1']
p.ConvertConstraints()
p = a.instances['Floor-1']
p.translate(vector=(0.0, 0.0, -0.0001))
p = mdb.models['circuitBoard'].parts['Board']
a.Instance(name='Board-1', part=p, dependent=ON)
p = a.instances['Board-1']
p.translate(vector=(0.51, 0.0, 0.0))
f1 = a.instances['Board-1'].faces
f2 = a.instances['Packaging-1'].faces
a.ParallelFace(movablePlane=f1.findAt(coordinates=(0.543333333333333, 0.05,
0.0), normal=(0.0, 0.0, 1.0)), fixedPlane=f2.findAt(coordinates=(
0.0272382919150449, 0.0177981609225068, 0.0273814785169062)), flip=OFF)
e1 = a.instances['Board-1'].edges
e2 = a.instances['Packaging-1'].edges
a.ParallelEdge(movableAxis=e1.findAt(coordinates=(0.596604525482204,
0.137963003192081, 0.0307533566177196)), fixedAxis=e2.findAt(coordinates=(
0.0431590254312432, 0.0559914769973559, 0.0527683904196429)), flip=OFF)
e1 = a.instances['Board-1'].edges
d1 = a.instances['Packaging-1'].datums
a.CoincidentPoint(fixedPoint=d1[3],
movablePoint=a.instances['Board-1'].InterestingPoint(
edge=e1.findAt(coordinates=(0.652343827802905, 0.0916453486569404,
-0.0804357827095802)), rule=MIDDLE))
d = a.instances['Board-1'].datums
a.ReferencePoint(point=d[2])
a.ReferencePoint(point=d[3])
a.ReferencePoint(point=d[4])
r = a.referencePoints
refPoints1=(r[19], )
a.Set(referencePoints=refPoints1, name='TopChip')
refPoints1=(r[20], )
a.Set(referencePoints=refPoints1, name='MidChip')
refPoints1=(r[21], )
a.Set(referencePoints=refPoints1, name='BotChip')
refPoints1=(r[21], )
a.Set(referencePoints=refPoints1, name='BotChip-all')
refPoints1=(r[21], )
a.Set(referencePoints=refPoints1, name='BotChip-largeInc')
e = a.instances['Board-1'].edges
edges = e.findAt(((0.0153385555521983, 0.0191710250695974,
0.0232637166281098), ))
a.Set(edges=edges, name='BotBoard')
region=a.sets['TopChip']
mdb.models['circuitBoard'].rootAssembly.engineeringFeatures.PointMassInertia(
name='MassTopChip', region=region, mass=0.005, alpha=0.0, composite=0.0)
region=a.sets['MidChip']
mdb.models['circuitBoard'].rootAssembly.engineeringFeatures.PointMassInertia(
name='MassMidChip', region=region, mass=0.005, alpha=0.0, composite=0.0)
region=a.sets['BotChip']
mdb.models['circuitBoard'].rootAssembly.engineeringFeatures.PointMassInertia(
name='MassBotChip', region=region, mass=0.005, alpha=0.0, composite=0.0)
mdb.models['circuitBoard'].ExplicitDynamicsStep(name='Drop',
previous='Initial', timePeriod=0.02, massScaling=PREVIOUS_STEP)
regionDef=mdb.models['circuitBoard'].rootAssembly.sets['TopChip']
mdb.models['circuitBoard'].HistoryOutputRequest(name='H-Output-TopChip',
createStepName='Drop', variables=('A3', 'V3', 'U3' ),
timeInterval=0.00007, region=regionDef)
mdb.models['circuitBoard'].HistoryOutputRequest('H-Output-MidChip',
mdb.models['circuitBoard'].historyOutputRequests['H-Output-TopChip'])
regionDef=mdb.models['circuitBoard'].rootAssembly.sets['MidChip']
mdb.models['circuitBoard'].historyOutputRequests['H-Output-MidChip'].setValues(
region=regionDef)
mdb.models['circuitBoard'].HistoryOutputRequest('H-Output-BotChip',
mdb.models['circuitBoard'].historyOutputRequests['H-Output-MidChip'])
regionDef=mdb.models['circuitBoard'].rootAssembly.sets['BotChip']
mdb.models['circuitBoard'].historyOutputRequests['H-Output-BotChip'].setValues(
region=regionDef)
mdb.models['circuitBoard'].HistoryOutputRequest('H-Output-BotChip-Antialiasing',
mdb.models['circuitBoard'].historyOutputRequests['H-Output-BotChip'])
mdb.models['circuitBoard'].historyOutputRequests['H-Output-BotChip-Antialiasing'].setValues(
filter=ANTIALIASING)
mdb.models['circuitBoard'].HistoryOutputRequest('H-Output-BotChip-all',
mdb.models['circuitBoard'].historyOutputRequests['H-Output-BotChip'])
regionDef=mdb.models['circuitBoard'].rootAssembly.sets['BotChip-all']
mdb.models['circuitBoard'].historyOutputRequests['H-Output-BotChip-all'].setValues(
frequency=1, region=regionDef)
mdb.models['circuitBoard'].HistoryOutputRequest('H-Output-BotChip-largeInc',
mdb.models['circuitBoard'].historyOutputRequests['H-Output-BotChip'])
regionDef=mdb.models['circuitBoard'].rootAssembly.sets['BotChip-largeInc']
mdb.models['circuitBoard'].historyOutputRequests['H-Output-BotChip-largeInc'].setValues(
timeInterval=0.0007, region=regionDef, filter=ANTIALIASING)
regionDef=mdb.models['circuitBoard'].rootAssembly.sets['BotBoard']
mdb.models['circuitBoard'].HistoryOutputRequest(name='H-Output-BotBoard',
createStepName='Drop', variables=('LE11', 'LE22', 'LE12', 'LEP'),
timeInterval=0.00007, region=regionDef, sectionPoints=(5, ), filter=ANTIALIASING)
mdb.models['circuitBoard'].ContactProperty('Fric')
mdb.models['circuitBoard'].interactionProperties['Fric'].TangentialBehavior(
formulation=PENALTY, directionality=ISOTROPIC, slipRateDependency=OFF,
pressureDependency=OFF, temperatureDependency=OFF, dependencies=0, table=((
0.3, ), ), shearStressLimit=None, maximumElasticSlip=FRACTION,
fraction=0.005, elasticSlipStiffness=None)
mdb.models['circuitBoard'].ContactExp(name='All', createStepName='Drop')
mdb.models['circuitBoard'].interactions['All'].includedPairs.setValuesInStep(
stepName='Drop', useAllstar=ON)
mdb.models['circuitBoard'].interactions['All'].contactPropertyAssignments.appendInStep(
stepName='Drop', assignments=((GLOBAL, SELF, 'Fric'), ))
s = a.instances['Board-1'].faces
side12Faces = s
a.Surface(side12Faces=side12Faces, name='Board')
region1=a.surfaces['Board']
region2=a.sets['TopChip']
mdb.models['circuitBoard'].Tie(name='TopChip', master=region1, slave=region2,
positionToleranceMethod=COMPUTED, adjust=ON, tieRotations=OFF)
region1=a.surfaces['Board']
region2=a.sets['MidChip']
mdb.models['circuitBoard'].Tie(name='MidChip', master=region1, slave=region2,
positionToleranceMethod=COMPUTED, adjust=ON, tieRotations=OFF)
region1=a.surfaces['Board']
region2=a.sets['BotChip']
mdb.models['circuitBoard'].Tie(name='BotChip', master=region1, slave=region2,
positionToleranceMethod=COMPUTED, adjust=ON, tieRotations=OFF)
r = a.instances['Floor-1'].referencePoints
refPoints1=(r[2], )
a.Set(referencePoints=refPoints1, name='floorRefPt')
region = a.sets['floorRefPt']
mdb.models['circuitBoard'].EncastreBC(name='BC-1', createStepName='Initial',
region=region)
c = a.instances['Packaging-1'].cells
cells = c
f = a.instances['Packaging-1'].faces
faces1 = f
e = a.instances['Packaging-1'].edges
edges1 = e
v = a.instances['Packaging-1'].vertices
verts = v
f = a.instances['Board-1'].faces
faces2 = f
e = a.instances['Board-1'].edges
edges2 = e
r = a.referencePoints
refPoints=(r[19], r[20], r[21], )
region = regionToolset.Region(vertices=verts, edges=edges1+edges2,
faces=faces1+faces2, cells=cells, referencePoints=refPoints)
mdb.models['circuitBoard'].Velocity(name='Field-1', region=region,
velocity1=0.0, velocity2=0.0, velocity3=-4.43, omega=0.0)
p = mdb.models['circuitBoard'].parts['Board']
e = p.edges
pickedEdges = e.findAt(((0.025, 0.0, 0.0), ), ((0.1, 0.0375, 0.0), ), ((0.0,
0.1125, 0.0), ), ((0.075, 0.15, 0.0), ))
p.seedEdgeByNumber(edges=pickedEdges, number=10)
f = p.faces
faces = f
p.setMeshControls(regions=faces, technique=SWEEP)
elemType1 = mesh.ElemType(elemCode=S4R, elemLibrary=EXPLICIT,
secondOrderAccuracy=OFF, hourglassControl=RELAX_STIFFNESS)
elemType2 = mesh.ElemType(elemCode=S3R, elemLibrary=EXPLICIT)
regions =(faces, )
p.setElementType(regions=regions, elemTypes=(elemType1, elemType2))
p.generateMesh()
##
p = mdb.models['circuitBoard'].parts['Floor']
p.seedPart(size=1.0)
elemType1 = mesh.ElemType(elemCode=R3D4, elemLibrary=EXPLICIT)
elemType2 = mesh.ElemType(elemCode=R3D3, elemLibrary=EXPLICIT)
f = p.faces
faces = f
regions =(faces, )
p.setElementType(regions=regions, elemTypes=(elemType1, elemType2))
p.generateMesh()
##
p = mdb.models['circuitBoard'].parts['Packaging']
e = p.edges
edges =(e.findAt(coordinates=(0.0005, 0.0, 0.11)), )
p.seedEdgeByNumber(edges=edges, number=1)
edges = e.findAt(((0.001, 0.009, 0.11), ), ((-0.001, 0.003, 0.11), ), ((
-0.00775, 0.012, 0.11), ), ((0.00325, 0.012, 0.11), ))
p.seedEdgeByNumber(edges=edges, number=3)
edges = e.findAt(((0.01, 0.006, 0.11), ))
p.seedEdgeByNumber(edges=edges, number=6)
edges = e.findAt(((0.005, -0.012, 0.11), ))
p.seedEdgeByNumber(edges=edges, number=7)
edges = e.findAt(((0.01, 0.012, 0.0275), ))
p.seedEdgeByNumber(edges=edges, number=15)
import re, uti
if re.search('Student', uti.getProductVersion()):
p.seedEdgeByNumber(edges=edges, number=12)
elemType1 = mesh.ElemType(elemCode=C3D8R, elemLibrary=EXPLICIT,
kinematicSplit=AVERAGE_STRAIN, secondOrderAccuracy=OFF,
hourglassControl=ENHANCED)
elemType2 = mesh.ElemType(elemCode=C3D6, elemLibrary=EXPLICIT)
elemType3 = mesh.ElemType(elemCode=C3D4, elemLibrary=EXPLICIT)
c = p.cells
cells = c
regions =(cells, )
p.setElementType(regions=regions, elemTypes=(elemType1, elemType2, elemType3))
pickedRegions = c
p.setMeshControls(regions=pickedRegions, algorithm=MEDIAL_AXIS)
p.generateMesh()
##
session.viewports['Viewport: 1'].assemblyDisplay.setValues(mesh=OFF)
session.viewports['Viewport: 1'].assemblyDisplay.meshOptions.setValues(
meshTechnique=OFF)
mdb.Job(name='Circuit', model='circuitBoard', type=ANALYSIS,
explicitPrecision=DOUBLE, description='Circuit board drop test')
session.viewports['Viewport: 1'].view.fitView()
a.regenerate()
session.viewports['Viewport: 1'].setValues(displayedObject=a)
session.viewports['Viewport: 1'].view.setValues(session.views['Bottom'])
session.viewports['Viewport: 1'].assemblyDisplay.geometryOptions.setValues(
datumPoints=OFF, datumAxes=OFF, datumPlanes=OFF, datumCoordSystems=OFF)
session.viewports['Viewport: 1'].view.fitView()
mdb.saveAs('Circuit')
```