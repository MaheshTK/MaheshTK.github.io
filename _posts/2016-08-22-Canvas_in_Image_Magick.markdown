---
published: true
title: Create Canvas
layout: post
---
### Create solid canvas

A solid color canvas to be generated

`convert -size 100x100 xc:wheat  canvas_wheat.gif`

To change color of solid canvas

`convert canvas_khaki.gif -fill tomato -opaque khaki canvas_tomato.gif`

`-opaque color` -Change this color to the fill color within the image. So `-fill` need to be defined before.

The `-transparent` operator is exactly the same as -opaque but replaces the matching color with transparency rather than the current `-fill` color setting. 
The `-fuzz` setting can be used to match and replace colors similar to the one given.

Create Image of same size

`convert test.png  -alpha Opaque +level-colors Sienna  color_levelc.gif`

Blanking Image with Picked Color

`convert rose: -fx 'p{0,0}'  color_pick_fx.png`

Generate a yellow canvas...

`convert  test.png  -gamma -1,-1,0  -alpha off  yellow_gamma.png`

### Transparent Canvas

The fastest and easiest way is to just get IM to directly clear the image to transparency, using the "-alpha transparent" operator.

`convert test.png  -alpha transparent trans_alpha.png`

### Gradients of Color

This will generate vertical gradient from white to black.

`convert  -size 100x100 gradient:  gradient.jpg`

This will generate vertical gradient from blue to white (closest color end).

`convert  -size 100x100 gradient:blue  gradient.jpg`

This will generate two color gradient. You can enter a RGB color as well. 

`convert -size 100x100  gradient:tomato-steelblue  gradient_range5.jpg`

To create horizontal gradient just rotate the image.

`convert -size 50x500  gradient:tomato-steelblue  -rotate 90 gradient_range5.jpg`

Making rainbow color space

`convert -size 30x600 xc:red -colorspace HSB \`
`        gradient: -compose CopyRed -composite \`
`       -colorspace RGB -rotate 90  gradient_rainbow.jpg`

This first converts a highly saturated color (_red_) into HSL colorspace. That correctly sets the images saturation and brightness channels to the appropriate values. After this a gradient is generated and copied into the 'red' (or 'hue') channel of out HSL colorspace image. And hey presto when we convert the HSL image back to RGB, we get a full rainbox of bright fully-saturated colors.

Generate radial gradient images in a similar way.

`convert -size 1000x1000 radial-gradient:red-yellow  rgradient.jpg`

Reference :
[Image Magick](http://www.imagemagick.org/Usage/canvas/)



