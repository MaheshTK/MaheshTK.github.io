---
published: true
title: Using Image Magick
layout: post
---
#### Using imagemagick for converting pdf file to image file

This command will convert page 3 to 6 to jpg file with name out + 4 digit suffix at resolution of 300 DPI.

`"C:\Program Files\ImageMagick-7.0.2-Q16\convert.exe" -density 300 one.pdf[2-5] out%04d.jpg`

#### Make a blank document 

`convert -size 2400x3300 canvas:white one.jpg`

#### Make a composite

`composite -geometry +625+500 dl1.jpg composite1.jpg`
`composite -geometry +625+1700 dl2.jpg composite.jpg`

#### Convert image format

`convert one.jpg out.png`
`convert one.png -quality 90 out.jpg`

#### Resize image

Convert with aspect ratio

`convert one.jpg -resize 200x100 out.jpg`

Force conversion size

`convert one.jpg -resize 200x100! out.jpg`

Resize to width 200 

`convert one.jpg -resize 200 out.jpg`

Resize to height 100

`convert one.jpg -resize x100 out.jpg`

#### Rotate image

`convert one.jpg -rotate 90 out.jpg`

#### Make a montage 

`montage -tile 4x4 -geometry 200x300+5+5 *.jpg out.jpg`
`montage -tile 5x1 -geometry 500x800+40 ale.jpg ale.jpg ale.jpg ale.jpg ale.jpg out1.jpg`
`montage -tile 6x1 -geometry 400x640+36 ale.jpg ale.jpg ale.jpg ale.jpg ale.jpg ale.jpg out2.jpg`
`montage -tile 8x1 -geometry 280x448+30 ale.jpg ale.jpg ale.jpg ale.jpg ale.jpg ale.jpg ale.jpg ale.jpg out4.jpg`
`montage -tile 1x6 -geometry +2+20 out1.jpg out1.jpg out2.jpg out2.jpg out4.jpg out4.jpg out5.j`


#### Crop all files in folder

`FOR /R %i in (*.jpg_.jpg_.jpg) do montage "%i" -gravity center -crop 600x600+0+0 "%i"_new.jpg`

Or can be done step by step

`FOR /R %i in (*.jpg) do convert "%i" -geometry 600^  "%i"_.jpg`
`FOR /R %i in (*_.jpg) do convert "%i" -geometry "x600<"  "%i"_.jpg`
`FOR /R %i in (*.jpg_.jpg_.jpg) do convert "%i" -gravity center -crop 600x600+0+0 "%i"_new.jpg`