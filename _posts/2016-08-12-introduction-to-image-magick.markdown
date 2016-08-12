---
published: true
title: Introduction to Image Magick
layout: post
---
The command in IM is of format
command { [-setting]... "image"|-operation }... "output_image"

#### Image settings

Setting are not actual operation, but settings for the image processing. 

| Operator settings | `-gravity -background -bordercolor -stroke -font -pointsize -strokewidth -box`  |
| Input settings | `-label -delay -dispose -page -comment -size` | 
| Output Settings | `-quality -loop -compression -format -path -transparent-color` | 
| Control & Debugging Settings | `-verbose -debug -warnings -quiet -monitor -regard-warnings` |

#### Simple image operators

These operations are carried out on input images.

| Image Creation | `image.png  xc:  canvas:  logo:  rose:  gradient:  radial-gradient:  plasma:  tile:  pattern:  label:  caption:  text:` |
| Basic | `-crop -trim -resize -scale -rotate -flip -flop -tile -pattern` |
| Sizing | `-liquid-resize -adaptive-resize -transpose -transverse -linear-stretch` |
| Writing | `-draw -annotate -magnify label:  caption:  text: `  |
| Blur | `-blur -gaussian-blur --radial-blur  -adaptive-blur -motion-blur`  |
| Sharpen | `-sharpen -unsharp -noise -adaptive-sharpen` |
| Filter | `-paint -sketch -charcoal -edge`  |
| Manipulation | `-raise -vignette -emboss -swirl -despeckle -distort -shade`  |
| Manipulation | `-implode -wave -convolve -shadow`  |
| Arithmatic | `-median -negate -separate -function -normalize -modulate -equalize`  |
| Colors | `-colors -map -alpha -colorspace -gamma -auto-level -auto-gamma`  |
| Contrast | `-contrast -contrast-stretch -contrast`  |
| Image whole | `-repage -border -frame -sample -thumbnail`  |
| Level | `-level -level-color -colorize`  |
| Coloring | `-tint -sparse-color -sepia-tone -solarize -recolor -opaque`  |
| Other | `-chop -morpohology -sigmoidial -transparent -ordered-dither -random-dither`  |
| other | `-poloroid -encipher -decipher -stegano -evaluate`  |

#### Multi File image operators

| Basic | `-append  -flatten   -composite -combine` |
| Advanced | `-mosaic  -layers   -fx  -coalesce  -clut  -average  -evaluate -sequence` |

#### Image stack operators

| Operators | `-delete  -insert  -swap  -reverse  -duplicate  -clone` |

#### Special operators

| Operator | `-geometry  -version  -list  -bench  -concurrent  -preview ` |

### Cheat sheet

| Convert image | `convert one.png -geometry 800x600 -quality 90 out.jpg` |
| Convert pdf | `convert -density 300 one.pdf[2-5] out%04d.jpg` |
| Blank Image | `convert -size 2400x3300 canvas:white one.jpg` |
| Resize | `convert one.jpg -resize 200x100 out.jpg` |
| Crop | `convert one.jpg -gravity center -crop 50%x20%+0+200 out.jpg` |

| Rotate | `convert one.jpg -rotate 90 out.jpg` |
| Montage | `montage -tile 4x4 -geometry 200x300+5+5 *.jpg out.jpg` |
| Filter | `convert one.jpg -charcoal 2 out.jpg` |
| `gravity` | Specifies reference for image manipulation. Options are eight directions (`northwest`, `north` etc. ) and `center`. This combined with offset (as in `geometry`) will define where operation happens. |
| `geometry` | Specifies desired width and height of an image and other dimensional quantities. it can be `100x200` (fit), `100x200^` (fit maximum), `100%x50%` (fit percentage), `100` (fit width), `x200` (fit height) or `100x200!` (stretch to fit). |