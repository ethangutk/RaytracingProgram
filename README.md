<br><br>


| ⚠ ⚠ ⚠ ***DISCLAIMER*** ⚠ ⚠ ⚠
| :---:
| I AM ***UNABLE*** TO POST THE SOURCE CODE FOR THIS SPECIFIC PROJECT DUE TO THE PROFESSOR'S COPYRIGHT ON THE SKELETON THAT WAS ORIGINALLY GIVEN


<br><br>
# Raytracing Program
## About The Class
#### CSE386 - The Foundation Of Computer Graphics 
I took this class my junior year of college and it brought heavy focus into vectors and vector arithmetic. Mastering the skills of normalizing, morphing, and creating vectors was a dependency to do all of the fun stuff later down the road. We first learned about raytracing, this process takes every pixel and computes a color based on the “shapes” within the scene.  When comparing this algorithm to an “object-ordered” algorithm, it is much slower in computation time but it gave me a great understanding of how 3D scenes are rendered on computers. Late in the class, we learned about “object-ordered rendering” which is an algorithm that computes the color of shapes by object rather than by pixel. The class was a marathon rather than a sprint as each topic built on the other. Overall, it was a really neat class and I would recommend anyone to learn this stuff if they have the opportunity to.


<br><br><br>
## About The Program
This program revolves around the concept of raytracing. Raytracing is a term for a *fancy* algorithm that renders 3D images in computer graphics. The algorithm takes a viewing ray for every pixel within the window and “shoots” them into the scene and calculates a color for the corresponding pixel. If a window has a size of 200px by 100px, there will be a total of 20,000 pixels, thus 20,000 viewing rays. After all of the viewing, rays have been calculated for the window, the frame will be shown. The calculation process for a single pixel can be as complex as you want it to be! For example, if I wanted my image to be super detailed, I could add shadows, reflections, anti-aliasing, transparent objects, and so much more. On the flip side, you can also make it very simple, only showing the ambient/silhouette of the objects within the scene. The possibilities are truly endless. The process describes the flawless *elegancy* of programming.


<br><br><br>
## The *Fancy* Calculation Features
### Anti-aliasing
This is a really neat feature that you probably experience every day but are not even aware of! This takes a nice ridged edge and will make it round with one simple calculation. There are many different intensities that you can choose to do but for the sake of our program, we decided to use a three-by-three grid. This will take a pixel and get the sum of the colors (RGB) of every pixel surrounding it by shooting extra viewing rays. Afterward, it will take the current pixel and reassign it with the average color, creating those buttery smooth images. <br><br>
Example of a 3x3 grid:
| ↘ | ⬇ | ↙ 
| :---: | :---: | :---:
| ➡ | ⏹ | ⬅ 
| ↗ | ⬆ | ↖ 

| Before | After
| :---: | :---:
| ![Before_Visual](https://github.com/ethangutknecht/RaytracingProgram/blob/main/Images/AA_Before.png?raw=true) |  ![After_Visual](https://github.com/ethangutknecht/RaytracingProgram/blob/main/Images/AA_After.png?raw=true)


<br><br>
### Cones & Spotlights
These two features go hand in hand. A cone is a smaller feature that uses the quadratic surface equation of a parabolic cylinder to create the shape’s properties. A little extra work is needed to let the program know to not keep producing the shape above the tip of the cone. A spotlight is simply a cone but, instead of a physical shape, it is light. Anything within the "light cone" will be illuminated but anything outside will show the object ambient. An index position, height, and radius of the base will be specified when creating the cone.


<br><br>
### Reflections
This is my favorite feature within this program. This feature ultimately allowed us to create mirrors within our scene. Here is the recursive process of how it works:
- Ray shoots and hits an object
- Reflection vector is shot away from the original hit object
- If the reflection vector hits another object, repeat. Otherwise, end
- Add each color * 0.3 to the final color

| Allowing 0 Recursions | Allowing 1 Recursion | Allowing 2 Recursions 
| :---: | :---: | :---:
| ![Image_1](https://github.com/ethangutknecht/RaytracingProgram/blob/main/Images/ReflectionsDemo_1.png?raw=true) | ![Image 2](https://github.com/ethangutknecht/RaytracingProgram/blob/main/Images/ReflectionsDemo_2.png?raw=true) | ![Image_3](https://github.com/ethangutknecht/RaytracingProgram/blob/main/Images/ReflectionsDemo_3.png?raw=true)

My program allows it to specify how many recursions to do, I personally always set it to three since doing more seems to diminish returns. Finally, I also had to take into consideration surface acne when coding this. So every hit is slightly moved above the surface by a very small factor of 0.01 units.

![Example_Of_Reflections](https://github.com/ethangutknecht/RaytracingProgram/blob/main/Images/ReflectionsExample.png?raw=true)


<br><br>
### Shadows
### Viewports
### Textures
### Transparency


<br><br><br>
## The *Beautiful* Renders ## 
![Image_1](https://github.com/ethangutknecht/RaytracingProgram/blob/main/Images/Image_1.png?raw=true)
![Image_2](https://github.com/ethangutknecht/RaytracingProgram/blob/main/Images/Image_2.png?raw=true)
![Image_3](https://github.com/ethangutknecht/RaytracingProgram/blob/main/Images/Image_3.png?raw=true)
![Image_4](https://github.com/ethangutknecht/RaytracingProgram/blob/main/Images/Image_4.png?raw=true)

<br><br><br>
- - - -

*Copyright © Ethan Gutknecht 2021*

