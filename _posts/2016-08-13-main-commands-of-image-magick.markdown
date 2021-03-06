---
published: true
title: Main Commands of Image Magick
layout: post
---
### Setting

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

The gravity command specifies where the gravity or reference of the image lies. The reference of gravity changes as per the command like `crop` or `geometry` or `resize` etc. It tells the command to operate with respect to the reference set by _gravity_ . 

| `-gravity` _type_ | `NorthWest, North, NorthEast, West, Center, East, SouthWest, South, SouthEast` |
| | `convert image.png -gravity Center -crop 10x10-40+20 output.png` |
| | Above command establishes the center of image as reference. <br /> An area of 10x10 is cropped at right lower offset of -40+20. |

### Basic Transform 

#### Conversion of image 

Images can be converted to different image format and different quality.

convert one.jpg out.png

convert one.png -quality 90 out.jpg

Image files can be converted to pdf files

convert one.jpg out.pdf

To convert multiple JPEG images to individual PDF pages, use:

convert *.jpg +adjoin page-%d.pdf

It is possible to convert pdf file pages to image files at desired resolution and color depth. Following command will convert page 3 to 6 to jpg file with name out + 4 digit suffix at resolution of 300 DPI.

"C:\Program Files\ImageMagick-7.0.2-Q16\convert.exe" -density 300 one.pdf[2-5] out%04d.jpg





The gravity command specifies where the gravity or reference of the image lies. The reference of gravity changes as per the command like `crop` or `geometry` or `resize` etc. It tells the command to operate with respect to the reference set by _gravity_ . 

| `-gravity` _type_ | `NorthWest, North, NorthEast, West, Center, East, SouthWest, South, SouthEast` |
| | `convert image.png -gravity Center -crop 10x10-40+20 output.png` |
| | Above command establishes the center of image as reference. <br /> An area of 10x10 is cropped at right lower offset of -40+20. |