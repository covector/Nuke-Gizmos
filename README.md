# Nuke-Gizmos
These gizmos only works with nuke non-commercial. They **cannot** be used in nuke commercial.
![Banner](banner.png)
# Effects

## Blob
*Fisheye lens effect.*<br />
Command: `blob` <br />
Dependency: None
![Blob demo](demo/Blob.png)
### Parameters
**BLOB**: The "blobness"

## Chromatic Aberration
*Chromatic aberration using translation or scaling*<br />
Command: `chromaa` <br />
Dependency: None
![Chromatic Aberration demo](demo/ChromaticAbberation.png)
### Parameters
**translateRED**: Position offset of the red channel<br />
**scaleRED**: Scale of the red channel<br />
**translateGREEN**: Position offset of the green channel<br />
**scaleGREEN**: Scale of the green channel<br />
**translateBLUE**: Position offset of the blue channel<br />
**scaleBLUE**: Scale of the blue channel<br />
**blu**r: Blurness of the red and blue channels

## Dispersion
*Chromatic dispersion.*<br />
Command: `disperse` <br />
Dependency: None
![Dispersion demo](demo/Dispersion.png)
### Parameters
**blob**: Intensity of the chromatic aberration<br />
**R blob**: Additional multiplier for the aberration of the red channel<br />
**G blob**: Additional multiplier for the aberration of the green channel<br />
**B blob**: Additional multiplier for the aberration of the blue channel<br />
**ray**: Amount of blurring between each aberrated channels<br />
**R ray**: Additional blurring on the red channel<br />
**G ray**: Additional blurring on the green channel<br />
**B ray**: Additional blurring on the blue channel<br />
**blur**: Blurness of the red and blue channels<br />
**blend**: Blending factor. Used with the `blend with` parameter<br />
**blend with**:<br />
chroma - Blend with the aberrated source<br />
source - Blend with the original unaberrated source

## Edge Glow
*Edge outline which glows and distort*<br />
Command: `edgeg` <br />
Dependency: None
![Edge Glow demo](demo/EdgeGlow.png)
### Parameters
**width**: Thickness of the Edge Glow<br />
**tint**: Color of the Edge Glow<br />
**amplitude**: Intensity of the distortion<br />
**scale**: Size of wrinkles on the Edge Glow<br />
**edge blur**: Blurring of the Edge Glow<br />
**small glow**: Radius of small bloom<br />
**large glow**: Radius of large bloom<br />
**speed**: Speed of distortion

## Mirror Wrapping
*Make the source seamless so black bars wouldn't appear during transformation*<br />
Command: `wrap` <br />
Dependency: None
![Mirror Wrapping demo](demo/MirrorWrapping.png)
### Parameters
(Same as the Transform node)
**translate**: Position offset<br />
**rotate**: Orientation<br />
**scale**: Size of output relative to the source<br />
**motionblur**: Amount of motion blur<br />
**shutter**: Amount of frame being considered in motion blur

# Transitions

## Spin
*Blurred spinning transition*<br />
Command: `tspin` <br />
Dependency: None
![Spin demo](demo/Spin.gif)
### Parameters
**transit**: Animate this parameter to create transition<br />
**curvature**: Rate of change of the rotating speed. Affect the middle part of the transition more when compared with `slope`<br />
**slope**: Rate of change of the rotating speed. Affect the start and end parts of the transition more when compared with `curvature`<br />
**motionblur**: Amount of motion blur<br />
**shutter**: Amount of frame being considered in motion blur

## Shake
*Sudden Shake*<br />
Command: `tshake` <br />
Dependency: None
![Shake demo](demo/Shake.gif)
### Parameters
**transit**: Animate this parameter to create transition<br />
**amplitude**: Shaking amplitude<br />
**frequency**: Shaking frequency (speed of shaking)<br />
**phase**: Random seed of the random shaking<br />
**decay**: The decaying rate of the amplitude<br />
**motionblur**: Amount of motion blur<br />
**shutter**: Amount of frame being considered in motion blur

## S-Zoom
*Shake and Zoom in transition*<br />
Command: `tszoom` <br />
Dependency: Dispersion, Mirror Wrapping
![Szoom demo](demo/Szoom.gif)
### Parameters
**transit**: Animate this parameter to create transition<br />
**motionblur**: Amount of motion blur<br />
**shutter**: Amount of frame being considered in motion blur<br />
**blob**: Maximum "blobness"<br />
**rotate**: Maximum rotation<br />
**scale**: Maximum scaling<br />
**curvature**: Rate of change of the quantity. Affect the middle part of the transition more when compared with `slope`<br />
**slope**: Rate of change of the quantity. Affect the start and end parts of the transition more when compared with `curvature`<br />
**frequency**: Shaking frequency (speed of shaking)<br />
**amplitude**: Shaking amplitude<br />
**decay**: The decaying rate of the amplitude<br />
**disperse**: Maximum "blobness" (rgb channels all blob in different direction)<br />
**ray**: Maximum blurring between each aberrated channels

## General Transition Node
*Can be used as any of the transitions from above. Also can be used to create custom transitions*<br />
Command: `gtn` <br />
Dependency: Spin, Shake, S-Zoom
### Parameters
**transit**: Animate this parameter to create transition<br />
**motionblur**: Amount of motion blur<br />
**shutter**: Amount of frame being considered in motion blur<br />
**curvature**: Rate of change of the quantity. Affect the middle part of the transition more when compared with `slope`<br />
**slope**: Rate of change of the quantity. Affect the start and end parts of the transition more when compared with `curvature`<br />
**transition**: The transition to be used<br />
**symmetric**: Can be used to create custom transitions outside this node. Symmetric means it goes from 0 to 1 then back to 0<br />
**asymmetric**: Can be used to create custom transitions outside this node. Asymmetric means it only goes from -1 to 1
