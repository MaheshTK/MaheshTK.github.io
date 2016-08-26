---
published: true
title: PDF cheat sheet combined
layout: post
---
| Join | `pdftk A=one.pdf B=two.pdf cat A1-5 A5 B6-20odd output out.pdf` |
| Rotate | `pdftk  A=one.pdf B=two.pdf cat A1-5east B5-endsouth output out.pdf` |
| Reverse | `pdftk A=one.pdf cat Aend-5 output out.pdf` |
| Extract images | `pdfimages one.pdf -j ../images` | 
| Image convert | `convert -density 300 -resize 200% one.pdf[2-3] -quality 80 out.jpg` |
| [crop](http://stackoverflow.com/questions/6183479/cropping-a-pdf-using-ghostscript-9-01,) or [pdfill](http://www.pdfill.com/pdf_tools_free.html)| `gswin32c.exe   -o cropped.pdf  -sDEVICE=pdfwrite -c "[/CropBox [24 72 559 794]" -c " /PAGES pdfmark"  -f uncropped-input.pdf` | 
| delete metadata | delete metadata |
| edit metadata | write metadata | |
| encrypt | | |
| limited priviledge | | |
| background | | |
| birst | | |