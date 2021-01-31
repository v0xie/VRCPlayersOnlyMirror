# VRCPlayersOnlyMirror

Tired of having to choose between admiring the scenery in a nice map or staring at your own reflection? Now you can do both at the same time!
VRCPlayersOnlyMirror is a simple mirror prefab that shows players only without any background.
This is NOT a 2D camera cut out, it is a full 3D mirror.

  - Player reflections in mirrors without any background
  - Adjustable mirror transparency
  - Simple distance fade
  - Works on both PC and Quest worlds
  - Performance cost more or less the same as a LQ mirror, with 1 additional drawcall

# Requirements
  - VRChat SDK2 or SDK3

# How to

  - Import either the SDK2 or SDK3 unitypackage depending on your project
  - Example scene is provided as well as a prefab
  - The "TransparentBackground" is required for the mirror to work properly, however if you have other mirrors in your scene that are not using VRCPlayersOnlyMirror, consider putting it on a different layer and show it on VRCPlayersOnlyMirror's layers only. Other wise it will show up in other mirrors, such as a full mirror if VRCPlayersOnlyMirror is also on. Resize as needed.

# Shader Settings

  - **Base (RBG)** - Overlays a texture onto the reflection, same behavior as the default mirror shader
  - **Hide Background** - Hides the background, requires the TransparentBackground shader acting as a fake background for the mirror for this to work
  - **Transparency** - Adjust transparency of the mirror
  - **Transparency Mask** - Texture mask that adjusts the transparency of the mirror, goes from white for fully opauque, to fully transparent with black. Mainly used to adjust the transparency of the entire mirror in real time for SDK2 as you can't animate mirror material properties on SDK2. See Next section for more details.
  - **Distance Fade** - Distance before the mirror starts fading to zero alpha.
  - **Distance Fade Length** - The length of distance traveled needed the fade to zero alpha.

# SDK2

  - The camera and render texture is used to control the transparency of the mirror via a ui slider, as its not possible to animate mirror material properties on sdk2. 
  - If you have multiple mirrors and want independent transparency sliders, you will need to make separate materials, render textures and camera's for each of them

# Caveats
  
  - Most transparent materials will appear opaque in the mirror
  - Particles, additive materials etc will have black outlines
  - Opening the menu will cause the mirror transparency to temporarily be disabled
  - Transparent materials behind or in front of the mirror may overwrite or be overwritten by the mirror, adjusting the render queue can help, or as a last resort using stencils.