---
published: true
title: Manipulating pdf files
layout: post
tags: [pdf, productivity, office]
categories: [office, productivity]
---
|<img src="https://upload.wikimedia.org/wikipedia/commons/e/ec/Pdf_by_mimooh.svg" alt="Drawing" style="width: 120px;"/>| This post pertains with one of most common office workflow issue : manipulating pdf files. Pdf is an ubiquitous format. It has replaced paper in modern offices. Interestingly, pdf files also offer all options, a paper document offers like combining, splitting, rotating and encrtpting. In this blog, an amazing tool called **pdftk** which has these capabilities and much more. |

Slowly and steadily Portable Document Format AKA pdf has become de facto standard for sharing documents and for web publishing in last decade. A pdf file presents many advantages for transmitting documents. As the name indicates portability is the USP of this format. It frees from the most important worry while transmitting documents : whether the document will open at other end. That is what the crucial stage of communication : reception. While interpretation can be left to individual but pdf format will take care that the document will be open for interpretation. It also offers some other advantages such as small size, independence from originating format, web display and open ended format.

## Combine pdf files

There are various ways, which can be used to combine various files. One can select pdf files, respective page ranges, collate files, reverse page order and combination of all above.

#### Combine two files to generate one output file.
```pdftk one.pdf two.pdf cat output output.pdf ```
```pdftk A=one.pdf B=two.pdf cat A B output output.pdf```