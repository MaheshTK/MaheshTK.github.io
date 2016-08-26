---
published: true
title: PDF cheat sheet combined
layout: post
---


| Join  <br /> Rotate  <br /> Reverse  <br />| `pdftk A=one.pdf B=two.pdf C=three.pdf cat A1 A2south A3-15oddwest B5-end Cend-1` | 
First page of A <br /> 
Page 2 of A rotated 180 degrees  <br /> 
Page 3-15 of A, selected odd pages and rotated clockwise 90 degrees  <br /> 
Pages 5 to end of document B  <br /> 
All pages of C in reverse oreder |
| Extract images | `pdfimages one.pdf -j ../images` | Extract all images of one.pdf |
| Image convert | `convert -density 300 -resize 200% one.pdf[2-3] -quality 80 out.jpg` | Convert page 2 and 3 to jpg image file |
| crop | crop | |
| delete metadata | delete metadata | |
| edit metadata | write metadata | |
| encrypt | | |
| limited priviledge | | |
| background | | |
| birst | | |