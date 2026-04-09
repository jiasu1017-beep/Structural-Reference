# 1.2 Getting started with Abaqus

This guide is an introductory text designed to give new users guidance in analyzing solid, shell, beam, and truss models with Abaqus/Standard and Abaqus/Explicit, and viewing the results in Abaqus/Viewer or another postprocessor. You do not need any previous knowledge of Abaqus to benefit from this guide, although some previous exposure to the finite element method is recommended. If you are already familiar with the Abaqus solver products (Abaqus/Standard or Abaqus/Explicit) but would like an introduction to the Abaqus/CAE interface, refer to the *Getting Started with Abaqus: Interactive Edition* guide.

This document covers primarily stress/displacement simulations, concentrating on both linear and nonlinear static analyses as well as dynamic analyses. An introduction to CFD analysis and modeling fluid-structure interaction is also included. Other types of simulations, such as heat transfer and mass diffusion, are not covered.

## 1.2.1 How to use this guide

Each of the chapters in this guide introduces one or more topics relevant to using Abaqus/Standard and Abaqus/Explicit. Throughout the guide the term Abaqus is used to refer collectively to both Abaqus/Standard and Abaqus/Explicit; the individual product names are used when information applies to only one product. Most chapters contain a short discussion of the topic or topics being considered and one or two tutorial examples. You should work through the examples carefully since they contain a great deal of practical advice on using Abaqus.

The capabilities of Abaqus/Standard and Abaqus/Explicit are introduced gradually in these examples. You may create input files using a text editor; however, using an interactive pre-processor facilitates model creation for these examples. Full versions of the input files that you create in each example are in [Appendix A, "Example Files"](ap01.html). If you have access to Abaqus/CAE, you can use the companion guide, [Getting Started with Abaqus: Interactive Edition](../gsa/gsa-link.htm#gsa), to perform all preprocessing and analysis steps using detailed Abaqus/CAE tutorials.

This chapter is a short introduction to Abaqus and this guide. [Chapter 2, "Abaqus Basics"](ch02.html), which is centered around a simple example, covers the basics of using Abaqus. By the end of [Chapter 2, "Abaqus Basics"](ch02.html), you will know the fundamentals of how to prepare a model for an Abaqus simulation, check the data, run the analysis job, and view the results.

[Chapter 3, "Finite Elements and Rigid Bodies"](ch07.html), presents an overview of the main element families available in Abaqus. The use of continuum (solid) elements, shell elements, and beam elements is discussed in [Chapter 4, "Using Continuum Elements"](ch04.html); [Chapter 5, "Using Shell Elements"](ch05.html); and [Chapter 6, "Using Beam Elements"](ch06.html); respectively.

Linear dynamic analyses are discussed in [Chapter 7, "Linear Dynamics"](ch07.html). [Chapter 8, "Nonlinearity"](ch08.html), introduces the concept of nonlinearity in general, and geometric nonlinearity in particular, and contains the first nonlinear Abaqus simulation. Nonlinear dynamic analyses are discussed in [Chapter 9, "Nonlinear Explicit Dynamics"](ch09.html), and material nonlinearity is introduced in [Chapter 10, "Materials"](ch10.html). [Chapter 11, "Multiple Step Analysis"](ch11.html), introduces the concept of multistep simulations, and [Chapter 12, "Contact"](ch12.html), discusses the many issues that arise in contact analyses. Using Abaqus/Explicit to solve quasi-static problems is presented in [Chapter 13, "Quasi-Static Analysis with Abaqus/Explicit"](ch13.html). The illustrative example is a sheet metal forming simulation, which requires importing between Abaqus/Explicit and Abaqus/Standard to perform the forming and springback analyses efficiently.

## 1.2.2 Conventions used in this guide

This guide adheres to the following conventions:

**Typographical conventions**

Different text styles are used in the tutorial examples to indicate specific actions or identify items.

* Input in `COURIER FONT` should be typed into Abaqus/Viewer or your computer exactly as shown. For example,

```
abaqus viewer
```

would be typed on your computer to run Abaqus/Viewer.

* Menu selections, tabs within dialog boxes, and labels of items on the screen in Abaqus/Viewer are indicated in bold:

```
**View** -> **Graphics Options**
**Contour Plot Options**
```

**View orientation triad**

By default, Abaqus/Viewer uses the alphabetical option, *x-y-z*, for labeling the view orientation triad. In general, this guide adopts the numerical option, 1-2-3, to permit direct correspondence with degree of freedom and output labeling.

## 1.2.3 Basic mouse actions

[Figure 1-2](#gst-mouse) shows the mouse button orientation for a left-handed and a right-handed 3-button mouse.

**Figure 1-2** Mouse buttons.

![Mouse buttons](../graphics/cnv-mouse-nls.png)

The following terms describe actions you perform using the mouse:

**Click**

Press and quickly release the mouse button. Unless otherwise specified, the instruction "click" means that you should click mouse button 1.

**Drag**

Press and hold down mouse button 1 while moving the mouse.

**Point**

Move the mouse until the cursor is over the desired item.

**Select**

Point to an item and then click mouse button 1.

**[Shift]+Click**

Press and hold the **[Shift]** key, click mouse button 1, and then release the **[Shift]** key.

**[Ctrl]+Click**

Press and hold the **[Ctrl]** key, click mouse button 1, and then release the **[Ctrl]** key.

Abaqus/Viewer is designed for use with a 3-button mouse. Accordingly, this guide refers to mouse buttons 1, 2, and 3 as shown in [Figure 1-2](#gst-mouse). However, you can use Abaqus/Viewer with a 2-button mouse as follows:

* The two mouse buttons are equivalent to mouse buttons 1 and 3 on a 3-button mouse.
* Pressing both mouse buttons simultaneously is equivalent to pressing mouse button 2 on a 3-button mouse.

> **Tip:** You are instructed to click mouse button 2 in procedures throughout this guide. Make sure that you configure mouse button 2 (or the wheel button) to act as a middle button click.
