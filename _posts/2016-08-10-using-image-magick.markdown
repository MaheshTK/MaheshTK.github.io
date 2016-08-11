---
published: true
title: Using Image Magick
layout: post
---
### Understanding critical options

#### Geometry

Geometry command specifies desired width and height of an image and other dimensional quantities. 

Dimensions are specified as `WIDTHxHEIGHT` and the meaning changes as per requirement. Let us take example of image of 600x400 and _geometry_ specification as 100x200.

| specification | description | Aspect Ratio | resulting image |
| `100x200` | Scaled as per specification. | Yes | 100 x 150 |
| `100x200!` | Forced scale as per specification. | No | 100 x 200 |
| `100x200^` | Scaled as per maximum dimension. | Yes | 133 x 200 |
| `100x200>` | Shrinked _only if larger_ than specification. | Yes  | 100 x 150 |
| `100x200<` | Enlarged _only if smaller_ than specification. | Yes  | 600 x 400 |
| `50%x200%` | Scaled as per percentage. | Yes | 300 x 200 |
| `200%x50%` | Scaled as per percentage. | Yes | 133 x 200 |
| `100` | Scaled as per length. | Yes | 100 x 150 |
| `x200` | Scaled as per height. | Yes | 133 x 200 |

The command _geometry_ specifies dimensions but where to put this image is specified by _offset_ . However, the offset needs to be with reference. This reference is provided by `gravity` or `region` or such commands. 

In above case, `100x200+10+20` will place the image at offset from upper left corner. 

#### Gravity 

The gravity command specifies where the gravity or reference of the image lies. Various options include `NorthWest`, `North`, `NorthEast`, `West`, `Center`, `East`, `SouthWest`, `South`, `SouthEast`. The reference of gravity changes as per the command like `crop` or `geometry` or `resize` etc. 

It is especially useful when using crop with reference from center. The use with geometry is explained as above.

#### Convert image format

Images can be converted to different image format and different quality.

`convert one.jpg out.png`

`convert one.png -quality 90 out.jpg`

Image files can be converted to pdf files 

`convert one.jpg out.pdf`

To convert multiple JPEG images to individual PDF pages, use:

`convert *.jpg +adjoin page-%d.pdf`

It is possible to convert pdf file pages to image files at desired resolution and color depth. Following command will convert page 3 to 6 to jpg file with name out + 4 digit suffix at resolution of 300 DPI.

`"C:\Program Files\ImageMagick-7.0.2-Q16\convert.exe" -density 300 one.pdf[2-5] out%04d.jpg`

#### Make a blank document or canvas

A blank document or a canvas can be created.

`convert -size 2400x3300 canvas:white one.jpg`

#### Make a composite

A composite image can be created by overlaying images over one another.

`composite -geometry +625+500 dl1.jpg composite1.jpg`

`composite -geometry +625+1700 dl2.jpg composite.jpg`

#### Resize image

Images can be resized to desired resolution. 

`convert one.jpg -resize 200x100 out.jpg`

For specification of dimensions refer the _geometry_ specification above.

#### Rotate image

Image can be rotated by this command.

`convert one.jpg -rotate 90 out.jpg`

#### Crop image

Images can be cropped. Also refer the commands like `density` , `page` , `gravity` and `geometry`.

`convert one.jpg -gravity center -crop 50% out.jpg`

#### Make a montage 

A regular montage of images can be created.

`montage -tile 4x4 -geometry 200x300+5+5 *.jpg out.jpg`

Following small script will generate the montage for passport size printing.

`montage -tile 5x1 -geometry 500x800+40 a.jpg a.jpg a.jpg a.jpg a.jpg out1.jpg`

`montage -tile 6x1 -geometry 400x640+36 a.jpg -duplicate 5 out2.jpg`

`montage -tile 8x1 -geometry 280x448+30 a.jpg -duplicate 7 out4.jpg`

`montage -tile 1x6 -geometry +2+20 out1.jpg out1.jpg out2.jpg out2.jpg out4.jpg out4.jpg out5.jpg`


#### Crop files



#### Crop all files in folder

`FOR /R %i in (*.jpg_.jpg_.jpg) do montage "%i" -gravity center -crop 600x600+0+0 "%i"_new.jpg`

Or can be done step by step

`FOR /R %i in (*.jpg) do convert "%i" -geometry 600^  "%i"_.jpg`

`FOR /R %i in (*_.jpg) do convert "%i" -geometry "x600<"  "%i"_.jpg`

`FOR /R %i in (*.jpg_.jpg_.jpg) do convert "%i" -gravity center -crop 600x600+0+0 "%i"_new.jpg`