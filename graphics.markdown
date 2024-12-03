---
# Feel free to add content and custom Front Matter to this file.
# To modify the layout, see https://jekyllrb.com/docs/themes/#overriding-theme-defaults

layout: page
title: "Graphics"
---
## Research
# 3D Vectorization
As my primary research project in the Geometry Collective, I have been working on a pipeline for 3D vectorization.
3D vectorization is the process of rendering a 3D scene to vector graphics, such as SVG.
Currently, my advisor, professor Keenan Crane, and I are working on a submission of the project to SIGGRAPH 2025.

The method works by first creating a wireframe rendering of the 3D scene.
Under normal perspective projection, this can be done easily by compution the projection of each edge.
Under more complex projections, such as a mirror projection under a spherical mirror, approximate edge projections can be computed using some sampling scheme.

With a wireframe rendering obtained, we can compute an occluded drawing with filled regions by computing the arrangment induced by the wireframe curves.
The regions in the arrangment can be identified with faces in the 3D input using raytracing.
We can then occlude faces by merging adjacent regions which are identified to the same face.
The merged regions give the occluded vector output, which can be saved as the SVG output.

The crux of the problem, and the main contribution of our research, is in computing the arrangment of these curves.
Existing methods, primarily based on the [Bentley-Ottmann sweepline algorithm](https://en.wikipedia.org/wiki/Bentley%E2%80%93Ottmann_algorithm), are often plagued by numerical issues.
These numerical issues are fixed by using arbitrary-precision floating point numbers, which are inefficient.

By contrast, our method computes the arrangment of curves by building a BSP tree over the set of curves.
We start with a single cell that contains all curves, and then recursively subdivide cells that contain multiple curves.
We continue this subdivision until we reach some maximum depth specified by the user.
At this point, cells containing multiple curves are identified as containing the intersection of two or more curves.

We can then finally compute the regions in the arrangment by ordering the curves at an intersection.
To compute this ordering, we look at the rotational ordering of the neighboring cells that the curves exit to.
If two curves exit to the same cell, we resolve the ambiguity by simply removing one of the curves from our arrangment.

Our method is efficient, and shifts all numerical robustness issues to the task of determining whether a curve intersects a cell.
Additionally, our method features other benefits, such as being able to handle intersection between multiple curve types (Bezier, circular, even SDF curves).
Lastly, the simplification step during curve ordering allows for a multi-resolution vectorization of scenes, where tiny elements get simplified away based on the user-specified maximum depth.

Below is an example output from our pipeline, rendered in SVG format.
![](/assets/parthenon.svg)

## Course Projects
# Vulkan Renderer
As a part of the [Real-Time Computer Graphics](http://graphics.cs.cmu.edu/courses/15-472-s24/) course at CMU, I wrote a full rendering engine completely from scratch using C++ and Vulkan.
The renderer supports frustum culling, PBR materials, normal and parallax occlusion mapping, pre-filtered environment maps, real-time point/spot/sun lights, and shadow mapping.
Additionally, for the final project of the course, I implemented parallax-corrected environment maps as described by Sebastian Lagarde in [a SIGGRAPH 2012 talk](https://seblagarde.wordpress.com/2012/11/28/siggraph-2012-talk/).
[The source code can be found on my Github](https://github.com/TheDevelo/vulkan-renderer).

![](/assets/renderer1.png)

![](/assets/renderer2.png)

# Specular Next Event Estimation

For the final project of the [Phyiscally-Based Rendering](http://graphics.cs.cmu.edu/courses/15-468/) course at CMU, I implemented the paper [Slope-Space Integrals for Specular Next Event Estimation](https://rgl.epfl.ch/publications/Loubet2020Slope) by Loubet et. al.
The method was implemented on top of a standard path tracer.

In order to perform specular next event estimation as described in the paper, we define a method for computing the specular contribution of a triangle by integrating in slope-space.
We can then importance sample a point on the triangle by using Newton's method to inversion sample the specular contribution.
In order to eliminate triangles with low specular contribution during importance sampling, we precompute a specular BVH, which bounds which regions have a high specular contribution from a given triangle.

My implementation of the method was one of two projects which won the technical award for the class final project competition.

<div style="text-align:center"><img src="/assets/snee.png" /></div>

## Hobby Projects
# Spline Generator
As a part of my Counter Strike level design, I wanted to easily create 3D models of spline curves that weave through my levels.
To help create these models, I wrote a tool that lets me freehand these splines easily, and then export them into a format that I could use in Counter Strike.
The tool uses a custom engine, loading the Counter Strike map format to allow me to visualize how the splines look within the environment.
I can easily add new points to my spline, as well as adjust the position and rotation of existing control points, all within the tool.
The tool is written in Rust and uses WebGPU to render both on native and the web. [The source code can be found here](https://github.com/TheDevelo/botpath-generator/tree/rust).

![](/assets/spline1.png)

![](/assets/spline2.png)
