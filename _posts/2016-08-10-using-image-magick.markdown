---
published: true
title: Using Image Magick
layout: post
---
#### Using imagemagick for converting pdf file to image file

It is possible to convert pdf file pages to image files at desired resolution and color depth. Following command will convert page 3 to 6 to jpg file with name out + 4 digit suffix at resolution of 300 DPI.

`"C:\Program Files\ImageMagick-7.0.2-Q16\convert.exe" -density 300 one.pdf[2-5] out%04d.jpg`

#### Make a blank document 

A blank document or a canvas can be created.

`convert -size 2400x3300 canvas:white one.jpg`

#### Make a composite

A composite image can be created by overlaying images over one another.

`composite -geometry +625+500 dl1.jpg composite1.jpg`

`composite -geometry +625+1700 dl2.jpg composite.jpg`

#### Convert image format

Images can be converted to different image format and different quality.

`convert one.jpg out.png`

`convert one.png -quality 90 out.jpg`

Image files can be converted to pdf files 

`convert one.jpg out.pdf`

To convert multiple JPEG images to individual PDF pages, use:

`convert *.jpg +adjoin page-%d.pdf`

#### Resize image

Images can be resized to desired resolution. Following command resizes image while maintaining aspect ratio while maintaining longest possible dimension. Instead of `200x100` specifying only width (`200`) or height (`x100) is also possible. For forcing size without aspect ratio use `200x100!` instead. Width or height can be referred as % values as well e.g. `200x50%' for specific ratio or `200%` for increasing image size by 200%.

`convert one.jpg -resize 200x100 out.jpg`

It is also possible to specify _enlarge only if_ size is smaller than specific value by operator `<` like `200x100<` or specify _shrink only if_ image is greater than specific value using operator `<` like `200x100>` .

#### Rotate image

`convert one.jpg -rotate 90 out.jpg`

#### Make a montage 

A regular montage of images can be created.

`montage -tile 4x4 -geometry 200x300+5+5 *.jpg out.jpg`

Following small script will generate the montage for passport size printing.

`montage -tile 5x1 -geometry 500x800+40 a.jpg a.jpg a.jpg a.jpg a.jpg out1.jpg`

`montage -tile 6x1 -geometry 400x640+36 a.jpg -duplicate 5 out2.jpg`

`montage -tile 8x1 -geometry 280x448+30 a.jpg -duplicate 7 out4.jpg`

`montage -tile 1x6 -geometry +2+20 out1.jpg out1.jpg out2.jpg out2.jpg out4.jpg out4.jpg out5.jpg`


#### Crop all files in folder

`FOR /R %i in (*.jpg_.jpg_.jpg) do montage "%i" -gravity center -crop 600x600+0+0 "%i"_new.jpg`

Or can be done step by step

`FOR /R %i in (*.jpg) do convert "%i" -geometry 600^  "%i"_.jpg`

`FOR /R %i in (*_.jpg) do convert "%i" -geometry "x600<"  "%i"_.jpg`

`FOR /R %i in (*.jpg_.jpg_.jpg) do convert "%i" -gravity center -crop 600x600+0+0 "%i"_new.jpg`