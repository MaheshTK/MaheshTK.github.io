---
published: true
title: PDF cheat sheet combined
layout: post
---
| Join | `pdftk A=one.pdf B=two.pdf cat A1-5 A5 B6-20odd output out.pdf` |
| Rotate | `pdftk  A=one.pdf B=two.pdf cat A1-5east B5-endsouth output out.pdf` |
| Reverse | `pdftk A=one.pdf cat Aend-5 output out.pdf` |
| Extract images | `pdfimages -f 10 -l 18 -j one.pdf ../images` | 
| Image convert | `convert -density 300 -resize 200% one.pdf[2-3] -quality 80 out.jpg` |
| Convert pdf to png image | `pdftopng -f 10 -l 18 -r 300 -gray one.pdf ../images` |
| Convert pdf to text | `pdftotext -f 10 -l 18 one.pdf` |
| Encrypt | `pdftk one.pdf output output.pdf owner_pw ownpass` |
| Special Encrypt | `pdftk one.pdf output out.pdf owner_pw foo user_pw baz allow printing` |

| Add stamp or watermark | `pdftk one.pdf background back.pdf output out.pdf`` |
| Extract metadata to text file | `exiftool -a -g one.pdf > meta.txt` |
| Delete metadata of files | `exiftool -all= one.pdf` |
| Deleting XMP data | `BeCyPDFMetaEdit one.pdf -X 1` |
| [crop](http://stackoverflow.com/questions/6183479/cropping-a-pdf-using-ghostscript-9-01,) or [pdfill](http://www.pdfill.com/pdf_tools_free.html)| `gswin32c.exe   -o cropped.pdf  -sDEVICE=pdfwrite -c "[/CropBox [24 72 559 794]" -c " /PAGES pdfmark"  -f uncropped-input.pdf` | 


[ghostscript](http://www.peteryu.ca/tutorials/publishing/pdf_manipulation_tips)