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

### Operating single file

Extract some pages from file 

```pdftk one.pdf cat 1-12 24-end output output.pdf```

Reverse order of pages in file

```pdftk A=one.pdf cat Aend-1 output output.pdf```

Repair a PDF’s corrupted XREF table and stream lengths, if possible

```pdftk broken.pdf output fixed.pdf```

To split a pdf file into multiple documents with four digit (default) prefix

```pdftk one.pdf burst```

To specify specific digit prefix

```pdftk one.pdf burst output out%02d.pdf```

### Combine two files to generate one output file.

Combine two files

```pdftk one.pdf two.pdf cat output output.pdf```

Combine two files using handle

```pdftk A=one.pdf B=two.pdf cat A B output output.pdf```

Combine specific pages in different files

```pdftk A=one.pdf B=two.pdf cat A1-20 B21-end output output.pdf```

To combine multiple documents in a directory without listing each one, use wildcards (`*`):

```pdftk *.pdf cat output newfile.pdf```

### Rotate pages

For rotating pages, the normal orientation off pages is assumed vertical. It means at 12 O'clock position or towards north as seen on map. So, specify clockwise rotation, specify east. For anti-clockwise rotation, specify west and for 180 degree rotation, specify south. It will be clear from following examples.

Rotate first page clockwise.

```pdftk one.pdf cat cat 1east 2-end output out.pdf```

Rotate specific pages of different documents and combine them. 

```pdftk A=one.pdf B=two.pdf cat A1-12east A13-end Bsouth```