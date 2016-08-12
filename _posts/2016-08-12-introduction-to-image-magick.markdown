---
published: true
title: Introduction to Image Magick
layout: post
---
The command in IM is of format
command { [-setting]... "image"|-operation }... "output_image"

#### Image settings

Setting are not actual operation, but settings for the image processing. 

| Operator settings | `-gravity` `-background`  `-bordercolor`  `-stroke`  `-font`  `-pointsize`  `-strokewidth`  `-box` etc. |

| Input settings | `-label`  `-delay`  `-dispose`  `-page`  `-comment`  `-size` | 

| Output Settings | `-quality`  `-loop`  `-compression`  `-format`  `-path`  `-transparent-color` | 

| Control & Debugging Settings | `-verbose`  `-debug`  `-warnings`  `-quiet`  `-monitor`  `-regard-warnings` |

#### Simple image operators

These operations are carried out on input images.

| Image Creation | `image.png  xc:  canvas:  logo:  rose:  gradient:  radial-gradient:  plasma:  tile:  pattern:  label:  caption:  text:` |

| Simple Processing | 

| Basic | `-crop -trim -resize -scale -rotate -flip -flop` |

| Sizing | `-liquid-resize -adaptive-resize -transpose -transverse -linear-stretch` |

| Writing | `-draw -annotate -magnify`  |

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

| Advanced | `-mosaic  -layers   -fx  -coalesce  -clut  -average  -evaluate-sequence |

#### Image stack operators

| Operators | `-delete  -insert  -swap  -reverse  -duplicate  -clone` |

#### Special operators

| Operator | `-geometry  -version  -list  -bench  -concurrent  -preview ` 








