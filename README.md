# HW 1: WebGL Fireball

## Luke Kwon Assignment Detals
Link: https://lukekwon98.github.io/hw01-fireball/

### Fireball (Comet)
<img width="1195" height="711" alt="Screenshot 2026-09-21 at 2 19 18 PM" src="https://github.com/user-attachments/assets/eea0b7e9-e4be-4259-b8f2-0bee42562160" />

- Added static noise from a custom wave function (wavyFunc) to give the comet its initial structure
- Added an animated 3D Perlin-based FBM noise on top of the base structure to produce a fireball/comet like effect
- Added a color gradient to the comet, using the displacement of the original vertex position and the resulting position with noise applied
- Toolbox Functions used: Smoothstep, Impulse, Sin/Cos, Gain


### Interactivity
<img width="247" height="301" alt="Screenshot 2026-09-21 at 2 19 46 PM" src="https://github.com/user-attachments/assets/a187e994-95a9-48ed-9554-d1432ea9976c" />

- Added 4 color pickers that can change the color gradient of the comet
- Added 4 sliders that can control the influence of the comet tail, speed (frequency) of the noise, length of the comet, and animate the color gradient

### Background
<img width="2492" height="1554" alt="image" src="https://github.com/user-attachments/assets/8cbdd997-7d84-46b6-939e-c578bc037496" />
<img width="1056" height="819" alt="Screenshot 2026-09-21 at 2 20 38 PM" src="https://github.com/user-attachments/assets/c78b191e-e59d-42f2-b6d0-7b61dab2e2b0" />

- Created a giant sphere encapsulating the camera and the comet
- Used 3D Worley noise for stars and 3D FBM Perlin noise for the texture of the nebulae
- The overall shape of the nebulae was created using a separate 3D Perlin noise as a mask, which is animated using the time variable to make it appear to move.
- The 3D Worley noise was also animated using the time variable, giving the stars a twinkling effect.
- If you keep scrolling out, you can eventually see the universe from the outside.

## Objective
Get comfortable with using WebGL and its shaders to generate an interesting 3D, continuous surface using a multi-octave noise algorithm.


## Getting Started
- __Fork__ this repository
- Run `npm install` and `npm run dev` to set up the dependencies for this project
- Under the Github repo settings, navigate to "Build and deployment" -> "Source", and select **GitHub Actions**
- Push (or re-push) to `master`. The workflow will build your project and deploy it automatically. The project should be visible at http://username.github.io/repo-name.

## Assignment Details
- You will alter the vertex and fragment shaders used to render the Icosphere so that it looks like a fireball.
- Your vertex shader should apply a low-frequency, high-amplitude displacement of your sphere so as to make it less uniformly sphere-like. You might consider using a combination of sinusoidal functions for this purpose. We recommend a function of the form `f(x, y, z) = h` to displace your vertices along a vector, such as their surface normals.
- Your vertex shader should also apply a higher-frequency, lower-amplitude layer of fractal Brownian motion to apply a finer level of distortion on top of the high-amplitude displacement.
- Your fragment shader should apply a gradient of colors to your fireball's surface, where the fragment color is correlated in some way to the vertex shader's displacement.
- Both the vertex and fragment shaders should alter their output based on a uniform time variable (i.e. they should be animated). You might consider making a constant animation that causes the fireball's surface to roil, or you could make an animation loop in which the fireball repeatedly explodes.
- Across both shaders, you should make use of at least four of the functions discussed in the Toolbox Functions slides.

## Noise Application
View your noise in action by applying it as a displacement on the surface of your icosahedron, giving your icosahedron a bumpy, cloud-like appearance. Simply take the noise value as a height, and offset the vertices along the icosahedron's surface normals. You are, of course, free to alter the way your noise perturbs your icosahedron's surface as you see fit; we are simply recommending an easy way to visualize your noise. You could even apply a couple of different noise functions to perturb your surface to make it even less spherical.

In order to animate the vertex displacement, use time as the third dimension or as some offset to the (x, y, z) input to the noise function. Pass the current time since start of program as a uniform to the shaders.

For both visual impact and debugging help, also apply color to your geometry using the noise value at each point. There are several ways to do this. For example, you might use the noise value to create UV coordinates to read from a texture (say, a simple gradient image), or just compute the color by hand by lerping between values.

## Interactivity
Using dat.GUI, make at least THREE aspects of your demo interactive variables. For example, you could add a slider to adjust the strength or scale of the noise, change the number of noise octaves, etc.

Add a button that will restore your fireball to some nice-looking (courtesy of your art direction) defaults.

## Extra Spice
Choose one of the following options:

- Background (easy-hard depending on how fancy you get): Add an interesting background or a more complex scene to place your fireball in so it's not floating in a black void
- Custom mesh (easy): Figure out how to import a custom mesh rather than using an icosahedron for a fancy-shaped cloud.
- Mouse interactivity (medium): Find out how to get the current mouse position in your scene and use it to deform your cloud, such that users can deform the cloud with their cursor.
- Music (hard): Figure out a way to use music to drive your noise animation in some way, such that your noise cloud appears to dance.

## Submission
1. Create a pull request to this repository with your completed code.
2. Update README.md to contain a solid description of your project with a screenshot of some visuals, and a link to your live demo.
3. Submit the link to your pull request on Gradescope, and add a comment to your submission with a hyperlink to your live demo.
4. Include a link to your live site.

## Resources
- Javascript modules https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Statements/import
- Typescript https://www.typescriptlang.org/docs/home.html
- dat.gui https://workshop.chromeexperiments.com/examples/gui/
- glMatrix http://glmatrix.net/docs/
- WebGL
  - Interfaces https://developer.mozilla.org/en-US/docs/Web/API/WebGL_API
  - Types https://developer.mozilla.org/en-US/docs/Web/API/WebGL_API/Types
  - Constants https://developer.mozilla.org/en-US/docs/Web/API/WebGL_API/Constants
