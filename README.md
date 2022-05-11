<h6 >
	<a href="https://github.com/ethangutknecht">↩ Back To Ethan Gutknecht's Profile</a>
</h6>

<h1 align="center">🎯 Raytracing Program</h1><br>
<table align="center">
	<tr>
		<th>
			Directory
		</th>
	</tr>
	<tr>
		<td>
			<a href="#-about-the-class">🎓 About The Class</a><br><br>
			<a href="#ℹ-about-the-program">ℹ About The Program</a><br><br>
			<a href="#-the-fancy-calculation-features">🧮 The Fancy Calculation Features</a>
			<ul>
				<li><a href="#-anti-aliasing">⭕ Anti-aliasing</a></li>
        <li><a href="#-cones--spotlights">💡 Cones & Spotlights</a></li>
        <li><a href="#-reflections">🔃 Reflections</a></li>
        <li><a href="#-shadows">🌇 Shadows</a></li>
        <li><a href="#-viewports">📷 Viewports</a></li>
        <li><a href="#-textures">🎨 Textures</a></li>
        <li><a href="#-transparency">🌫 Transparency</a></li>
			</ul>
      <a href="https://github.com/ethangutknecht/RaytracingProgram#-the-final-beautiful-renders">🏁 The Final Beautiful Renders</a><br><br>
		</td>
  	</tr>
</table><br>
<br><br>


| ⚠ ⚠ ⚠ ***DISCLAIMER*** ⚠ ⚠ ⚠
| :---:
| I AM ***UNABLE*** TO POST THE SOURCE CODE FOR THIS SPECIFIC PROJECT DUE TO THE PROFESSOR'S COPYRIGHT ON THE SKELETON THAT THE PROFESSOR ORIGINALLY GAVE


<br><br>

## 🎓 About The Class
#### CSE386 - The Foundation Of Computer Graphics 
I took this class in my junior year of college, and it brought a heavy focus on vectors and vector arithmetic. Mastering the skills of normalizing, morphing, and creating vectors was a dependency to do all of the fun stuff later down the road. We first learned about raytracing; this process takes every pixel and computes a color based on the “shapes” within the scene.  When comparing this algorithm to an “object-ordered” algorithm, it is much slower in computation time, but it gave me a great understanding of how 3D scenes are rendered on computers. Late in the class, we learned about “object-ordered rendering,” an algorithm that computes the color of shapes by object rather than by pixel. The course was a marathon rather than a sprint, as each topic was built on the other. Overall, it was an impeccable class, and I would recommend anyone to learn this stuff if they have the opportunity.


<br><br><br>
## ℹ About The Program
This program revolves around the concept of raytracing. Raytracing is a term for a *fancy* algorithm that renders 3D images in computer graphics. The algorithm takes a viewing ray for every pixel within the window, “shoots” them into the scene, and calculates a color for the corresponding pixel. For example, if a window has a size of 200px by 100px, there will be 20,000 pixels, thus 20,000 viewing rays. After all the viewing rays have been calculated for the window, the algorithm will show the frame. The calculation process for a single pixel can be as complex as you want it to be! For example, if I wanted my image to be super detailed, I could add shadows, reflections, anti-aliasing, transparent objects, etc. On the flip side, you can also make it very simple, only showing the ambient/silhouette of the things within the scene. The possibilities are truly endless. The process describes the flawless *elegancy* of programming.


<br><br><br>
## 🧮 The *Fancy* Calculation Features
### ⭕ Anti-aliasing
This is an elegant feature that you probably experience every day but are unaware it’s happening! This feature takes a nice ridged edge and will make it round with one simple calculation. There are many different intensities that you can choose to do, but for the sake of our program, we decided to use a three-by-three grid. This will take a pixel and get the sum of every pixel’s colors (RGB) by shooting extra viewing rays to the surrounding pixels. Afterward, it will take the current pixel and reassign it with the average color, creating those buttery smooth images. <br><br>
Example of a 3x3 grid:
| ↘ | ⬇ | ↙ 
| :---: | :---: | :---:
| ➡ | ⏹ | ⬅ 
| ↗ | ⬆ | ↖ 

| Before | After
| :---: | :---:
| ![Before_Visual](https://github.com/ethangutknecht/RaytracingProgram/blob/main/Images/AA_Before.png?raw=true) |  ![After_Visual](https://github.com/ethangutknecht/RaytracingProgram/blob/main/Images/AA_After.png?raw=true)


<br><br>
### 💡 Cones & Spotlights
These two features go hand in hand. A cone is a minor feature that uses the quadratic surface equation of a parabolic cylinder to create the shape’s properties. A little extra work is needed to let the program know not to keep producing the shape above the tip of the cone. A spotlight is simply a cone, but it is light instead of a physical form. Anything within the "light cone" will be illuminated, but anything outside will show the object ambient. An index position, height, and radius of the base will be specified when creating the cone.


<br><br>
### 🔃 Reflections
This is my favorite feature of this program. This feature ultimately allowed us to create mirrors within our scene. Here is the recursive process of how it works:
- Ray shoots and hits an object
- Reflection vector is shot away from the original hit object
- If the reflection vector hits another object, repeat. Otherwise, end
- Add each color * 0.3 to the final color

| Allowing 0 Recursions | Allowing 1 Recursion | Allowing 2 Recursions 
| :---: | :---: | :---:
| ![Image_1](https://github.com/ethangutknecht/RaytracingProgram/blob/main/Images/ReflectionsDemo_1.png?raw=true) | ![Image 2](https://github.com/ethangutknecht/RaytracingProgram/blob/main/Images/ReflectionsDemo_2.png?raw=true) | ![Image_3](https://github.com/ethangutknecht/RaytracingProgram/blob/main/Images/ReflectionsDemo_3.png?raw=true)

My program allows it to specify how many recursions to do. I always set it to three since doing more seems to diminish returns. Finally, I also had to consider surface acne when coding this. So every hit is slightly moved above the surface by a tiny factor of 0.01 units.<br><br>
**Example Of Surface Acne:**<br>
![Example_Of_Surface_Acne](https://github.com/ethangutknecht/RaytracingProgram/blob/main/Images/SurfaceAcne.png?raw=true)
<br><br>
**Example Of Reflections:**<br>
![Example_Of_Reflections](https://github.com/ethangutknecht/RaytracingProgram/blob/main/Images/ReflectionsExample.png?raw=true)


<br><br>
### 🌇 Shadows
The shadows make the lights and objects in the scene feel real. When a ray hits an object, it will shoot rays at every light object. If those rays intersect with another opaque object and the light intensity is large enough, it will produce a shadow for the other opaque object. This also calculates multiple lights in the scene so that the shadow is accurate. These rays that shoot out to the light object are called shadow feelers. Surface acne will also be considered, thus moving the hit 0.01 units above each surface. <br>
| Before | After
| :---: | :---:
| ![Before_Visual](https://github.com/ethangutknecht/RaytracingProgram/blob/main/Images/Shadows_Before.png?raw=true) |  ![After_Visual](https://github.com/ethangutknecht/RaytracingProgram/blob/main/Images/Shadows_After.png?raw=true)


<br><br>
### 📷 Viewports
This feature allows you to look at multiple different camera angles simultaneously. This will split the window into different sections, rending the same scene from multiple camera angles. How does it work? It calls the render frame function many times and specifies how big the size of the render should be. It will also determine where those pixels should be based on the start position. 

Rendering Sections | Camera Positions
| :---: | :---:
| ![Sections](https://github.com/ethangutknecht/RaytracingProgram/blob/main/Images/ViewPorts_Example2.png?raw=true) |  ![Cam_Positions](https://github.com/ethangutknecht/RaytracingProgram/blob/main/Images/Viewports_Example3.png?raw=true)

<br>**Example Of Viewports:**<br>
![Example_Of_Viewports](https://github.com/ethangutknecht/RaytracingProgram/blob/main/Images/ViewPorts_Example1.png?raw=true)


<br><br>
### 🎨 Textures
Textures are pretty simple. Put an image on an object. It becomes pretty easy for objects like a plane or a single side of a cube. The challenge comes when you map the object onto a 3D surface. I used mapping an American flag onto a cylinder's side as an example. This wraps the flag around the cylinder, similar to how you would do with a can of soup. Next, there had to be some computations involving mapping the size of the image in pixels to [0, 1]. Once that mapping computation is complete, it’s pretty simple to find what color that pixel needs based on the image map, lighting, etc.

<br><br>
### 🌫 Transparency
Transparency is one feature that takes the program from good to great. In this program, we have a set of opaque objects and a set of transparent objects. When a viewing ray hits a transparent object, it will continue to shoot past, looking for more objects. There are different cases:
- Hits another opaque object
- Hits the "sky" or no object
- Hits another transparent object

We would combine the colors with whatever it hit and the transparent object's color based on these cases. Overall, the entities behind a transparent object would look like a tint varying by how transparent the object is. In the example below, the red plane intersects the scene making everything "behind" the red plane have a red tint.

<br>**Example Of Transparency:**<br>
![Example_Of_Viewports](https://github.com/ethangutknecht/RaytracingProgram/blob/main/Images/Transparency_Example1.png?raw=true)


<br><br><br><br>

- - - -

<br>

<p align="center">
  ...🥁now lets put it all together...drumroll please🥁...
</p>

<br>

- - - -


<br><br><br><br>

## 🏁 The Final *Beautiful* Renders
![Image_1](https://github.com/ethangutknecht/RaytracingProgram/blob/main/Images/Image_1.png?raw=true)
![Image_2](https://github.com/ethangutknecht/RaytracingProgram/blob/main/Images/Image_2.png?raw=true)
![Image_3](https://github.com/ethangutknecht/RaytracingProgram/blob/main/Images/Image_3.png?raw=true)
![Image_4](https://github.com/ethangutknecht/RaytracingProgram/blob/main/Images/Image_4.png?raw=true)

<br><br><br>

- - - -
<h6 align="center">
	<a align="center" href="#-raytracing-program">⬆ Back To The Top </a>
</h6>

- - - -

<h6 align="center">
	<a href="https://github.com/ethangutknecht">↩ Back To Ethan Gutknecht's Profile</a>
</h6>

- - - -

<h6 align="center">
  Copyright © Ethan Gutknecht 2022
</h6>





