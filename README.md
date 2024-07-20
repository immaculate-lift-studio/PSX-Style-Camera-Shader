# PSX-Style-Camera-Shader
This is a Camera shader for Godot 4 to add distance fog with optional noise, color limiting, and dither. There are a lot of fragmented and partial solutions out there and I wanted to combine various techniques to make an easy to use quad-based shader. Each setting can be enabled/disabled and customized. I have tested this in small maps (100x100) as well as large maps (6000x6000) with no issues. 

For the fog, I took direct inspiration and direction from the excellent [Godot4-ScreenSpacePostFX-DepthFog]( https://github.com/zvodd/Godot4-ScreenSpacePostFX-DepthFog/tree/main) by zvodd. His technique is different (using viewports) and contains features mine does not, so please check it out! The color reduction and dithering techniques are my own. 

## Examples
### All effects turned on (screen shot from my WIP game)
![All Effects - RotorSim](https://github.com/GEG-fairbear8974/PSX-Style-Camera-Shader/assets/112404117/0b964ddf-a61a-4199-b144-f5da801dd831)
### Fog
![Fog](https://github.com/GEG-fairbear8974/PSX-Style-Camera-Shader/assets/112404117/6b3bef53-b1bb-454e-80c7-45fed66bd3d9)
### Fog and Noise
![Fog, Noise](https://github.com/GEG-fairbear8974/PSX-Style-Camera-Shader/assets/112404117/a12ad33b-573c-4dc2-9734-c0bab2b27147)
### Fog, Noise, Color Limiting
![Fog, Noise, Color Limiting](https://github.com/GEG-fairbear8974/PSX-Style-Camera-Shader/assets/112404117/d27d1869-8ebe-465b-8972-44c6a222a41f)
### Fog color can be changed
![Fog Pink](https://github.com/GEG-fairbear8974/PSX-Style-Camera-Shader/assets/112404117/e5e852ff-f5c5-4b0b-b006-81b7ee4950bc)

## Instructions
If downloading the project, just open up the camera_example.tscn and check out how it works. 

If starting from stratch, create a new 3D scene and add a camera. Create a new MeshInstance3D as a child of the camera, assign it a QuadMesh, then make the size 2x2. Check the box "flip faces". Move the mesh so it's in front of the camera very slightly. Then all you need to do is give the QuadMesh a new material -> New ShaderMaterial -> New Shader. Assign the psx_camera_shader.gdshader to the material and boom you're done. Check the shader parameters to make adjustments and edit everything:

## Variables
Enable Fog - Enables/disables fog  
Fog Color - Color of the fog  
Noise Color - Color of the noise overlayed on top of the fog  
Fog Distance - The distance in units away from the camera the fog is completely opaque  
Noise Enabled - Turns noise on/off
Fog Fade Range - How much distance the fog will take to fade to opaque  
Noise Time Fac - The amount and movement of the noise  
Enable Color Limitation - Enables/disables limiting the colors  
Color Levels - Amount of colors allowed onscreen if Enable Color Limitation is checked  
Enable Dithering - Enables/disables dithering  
Dither Strength - Higher number mean bigger dots  

## Tips
If you have any transparent objects in your scene (meshes, sprites, etc) this shader won't "see" them as the render mode doesn't allow alpha transparency. In order to have transparent objects been seen you must change the "Render Priority" of each object to a number higher than "0". Everything in the editor is set to "0" for a new project, so in most cases setting this to "1" for **Each** transparent object will be adequete.

## License
MIT. I hope this helps somebody in their Godot journey!
