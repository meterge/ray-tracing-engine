# Ray Tracing Engine

## Overview

This project is a basic ray tracing engine implemented in C++.

It was developed for the CENG 477 Introduction to Computer Graphics course at Middle East Technical University. The purpose of the project is to simulate light propagation in a 3D scene and render the scene as a 2D image using ray tracing.

The renderer takes an XML scene file as input and generates output images in PPM format.

## Features

* Ray tracing-based image rendering
* XML scene file input
* PPM image output
* Multiple camera support
* Sphere rendering
* Triangle rendering
* Mesh rendering
* Ray-object intersection tests
* Shadow ray computation
* Ambient lighting
* Point light sources
* Blinn-Phong shading model
* Specular highlights
* Mirror reflections
* Recursive reflection rays
* Background color handling
* Color clamping before writing the final image
* Shadow ray epsilon usage to avoid self-intersection artifacts

## Technologies Used

* C++
* Object-oriented programming
* Linear algebra
* Ray tracing
* Blinn-Phong illumination model
* PPM image format
* Makefile

## Build and Run

Clone the repository:

```bash
git clone https://github.com/meterge/ray-tracing-engine.git
cd ray-tracing-engine
```

Compile the project:

```bash
make
```

Run the ray tracer with an XML scene file:

```bash
./raytracer scene.xml
```

The rendered image will be saved as a `.ppm` file. The output filename is specified inside the XML scene file.

## Project Structure

```text
ray-tracing-engine/
├── README.md
├── Makefile
├── *.cpp
├── *.h
├── *.xml
└── outputs/
```

The exact file structure may differ depending on the included scene files and source files.

## Scene Description

The input scene is defined using an XML file. A scene may contain:

* Background color
* Shadow ray epsilon
* Maximum recursion depth
* One or more cameras
* Ambient light
* Point lights
* Materials
* Vertex data
* Meshes
* Triangles
* Spheres

Each camera can define a different view of the same scene. The renderer generates one output image for each camera configuration.

## Rendering Pipeline

For each pixel in the output image, a primary ray is generated from the camera through the image plane. The ray is tested against all objects in the scene.

If the ray intersects an object, the closest intersection point is selected and shaded using the material properties and light sources. Shadow rays are used to determine whether the point is blocked from each point light source.

For mirror-like materials, recursive reflection rays are generated up to the maximum recursion depth specified in the scene file.

If the ray does not intersect any object, the pixel is assigned the background color.

## Shading Model

The project uses the Blinn-Phong shading model.

The final color of an intersection point is computed using:

* Ambient contribution
* Diffuse contribution
* Specular contribution
* Mirror reflection contribution, if the material is reflective

Point light intensity decreases with distance according to inverse-square falloff.

## Example Usage

```bash
make
./raytracer inputs/simple_scene.xml
```

Example output:

```text
output.ppm
```

If needed, the generated `.ppm` file can be converted to `.png` using ImageMagick:

```bash
magick convert output.ppm output.png
```

## What I Learned

Through this project, I practiced:

* Implementing a ray tracing renderer from scratch
* Generating camera rays
* Computing ray-sphere intersections
* Computing ray-triangle intersections
* Calculating surface normals
* Applying the Blinn-Phong illumination model
* Handling point lights and ambient light
* Implementing shadows using shadow rays
* Avoiding self-intersection problems using epsilon offsets
* Implementing recursive mirror reflections
* Working with XML-based scene descriptions
* Producing rendered images in PPM format

## Notes

This project was developed for educational purposes as part of a computer graphics assignment.
