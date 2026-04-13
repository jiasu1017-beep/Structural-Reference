# 76.10 Controlling the display of individual coordinate systems







You can highlight, display, and hide individual coordinate systems in the viewport. Abaqus/CAE provides the following display options during modeling and postprocessing: 

**Controlling display of datum coordinate systems during modeling**

All datum geometry you create, including datum coordinate systems, are considered features of the part or assembly to which they apply. Abaqus/CAE provides shortcuts for datum coordinate systems and other features in the Model Tree under the **Features** container for the part or assembly. You can highlight an individual datum coordinate system by clicking its shortcut in the Model Tree; when highlighted, a coordinate system is rendered in red in the viewport and its title is displayed. To hide or display the coordinate system in the viewport, click mouse button 3 on the shortcut and select **Suppress** or **Resume**.

You can also control the display of individual datum coordinate systems by adding them to display groups. See ["Managing display groups," Section 78.2](pt07ch78s02.md), for more information.

**Controlling display of any coordinate system during postprocessing**

In the Visualization module the available coordinate systems are divided into two groups: ODB coordinate systems, which are part of the output database file; and session coordinate systems, which are created during postprocessing. Session coordinate systems apply to one output database only and persist only for your Abaqus/CAE session, unless you move the session coordinate system to the output database. See ["Saving a coordinate system to an output database file," Section 42.8.6](pt05ch42s06hlb05.md).

You can highlight, display, or hide individual coordinate systems using either of the following techniques:
- All available coordinate systems have shortcuts in the Results Tree under the **ODB Coordinate Systems** and **Session Coordinate Systems** containers. You can click any shortcut to highlight that coordinate system in the viewport; when highlighted, a coordinate system is rendered in red in the viewport and its title is displayed. You can also display or hide any coordinate system by clicking mouse button 3 on the shortcut and selecting a Boolean operator from the list that appears.
- You can control the display of ODB coordinate systems and session coordinate systems by adding them to display groups, which can be displayed or hidden using the Boolean display options. See ["Managing display groups," Section 78.2](pt07ch78s02.md), for more information.

The **Coordinate System Manager** also provides information about the ODB coordinate systems and session coordinate systems for the selected output database. You cannot change the display of coordinate systems from this manager, but you can rename or delete them. See ["Creating coordinate systems during postprocessing," Section 42.8](pt05ch42s06.md).

![](../graphics/images/black4rule.gif)For information on related topics, click any of the following items:- ["Creating coordinate systems during postprocessing," Section 42.8](pt05ch42s06.md)
- ["Creating datum coordinate systems," Section 62.9](pt06ch62s09.md)
- [Chapter 76, "Customizing geometry and mesh display](pt07ch76.md)"




