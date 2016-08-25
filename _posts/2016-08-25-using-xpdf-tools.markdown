---
published: true
title: Using XPDF tools
layout: post
---
The  [XPDF](http://www.foolabs.com/xpdf/download.html) provides some really handy tools. Very notable one is __pdfimages__ which can extract images from the pdf files. Other useful tools include __pdftopng__ and __pdfdetach__ .

## xpdf

Xpdf  is a viewer for Portable Document Format (PDF) files.  (These are also sometimes also called 'Acrobat' files, from the  name  of  Adobe's
PDF  software.)   Xpdf runs under the X Window System on UNIX, VMS, and OS/2.

To run xpdf, simply type:

`xpdf file.pdf`

where file.pdf is your PDF file.  The file name can be  followed  by  a number specifying the page which should be displayed first, e.g.:

`xpdf file.pdf 18`

You  can  also  give a named destination, prefixed with '+' in place of the page number.  (This is only useful  with  PDF  files  that  provide named destination targets.)

You can also start xpdf without opening any files:

`xpdf`

## pdfimages

Pdfimages saves images from a Portable Document Format  (PDF)  file  asPortable Pixmap (PPM), Portable Bitmap (PBM), or JPEG files.

Pdfimages  reads  the  PDF file, scans one or more pages, PDF-file, and writes one PPM, PBM, or JPEG file for each image,  image-root-nnnn.xxx, where  nnnn  is the image number and xxx is the image type (.ppm, .pbm, .jpg).

NB: pdfimages extracts the raw image data from the  PDF  file,  without performing  any  additional  transforms.  Any rotation, clipping, color inversion, etc. done by the PDF content stream is ignored.

## pdfdetach

Pdfdetach lists or extracts embedded files (attachments) from a  Portable Document Format (PDF) file.

## pdftopng

Pdftopng converts  Portable  Document  Format  (PDF)  files  to  color,grayscale, or monochrome image files in Portable Network Graphics (PNG) format.

Pdftopng reads the PDF file, PDF-file, and writes one PNG file for eachpage,  PNG-root-nnnnnn.png,  where  nnnnnn is the page number.  If PNG root is '-', the image is sent to stdout (this is probably only  usefulwhen converting a single page).

## pdffonts

Pdffonts  lists the fonts used in a Portable Document Format (PDF) file along with various information for each font.

## pdftohtml

Pdftohtml converts Portable Document Format (PDF) files to HTML.

Pdftohtml reads the PDF file, PDF-file, and places  an  HTML  file  for each page, along with auxiliary images in the directory, HTML-dir.  The HTML directory will be created; if it already  exists,  pdftohtml  will report an error.


## xpdfrc

All  of the Xpdf tools read a single configuration file.  If you have a .xpdfrc file in your home directory, it will  be  read.   Otherwise,  a system-wide configuration file will be read from /usr/local/etc/xpdfrc, if it exists.  (This  is  its  default  location;  depending  on  build  options,  it  may  be  placed elsewhere.)  On Win32 systems, the xpdfrc file should be placed in the same directory as the executables.

The xpdfrc file consists of a series of configuration options, one  per line.   Blank  lines  and  lines  starting  with  a  '#' (comments) are ignored.

Arguments may be quoted, using  "double-quote"  characters,  e.g.,  for file names that contain spaces.

The  following  sections  list all of the configuration options, sorted into functional groups.  There is an examples section at the end.

## pdfinfo

Pdfinfo prints the contents of the 'Info' dictionary (plus  some  other useful information) from a Portable Document Format (PDF) file.

The 'Info' dictionary contains the following values:

title
subject
keywords
author
creator
producer
creation date
modification date

In addition, the following information is printed:

tagged (yes/no)
form (AcroForm / XFA / none)
page count
encrypted flag (yes/no)
print and copy permissions (if encrypted)
page size and rotation
file size
linearized (yes/no)
PDF version
metadata (only if requested)

## pdftotext

Pdftotext converts Portable Document Format (PDF) files to plain text.

Pdftotext reads the PDF file, PDF-file, and writes a text  file,  text-file.   If  text-file  is not specified, pdftotext converts file.pdf to
file.txt.  If text-file is '-', the text is sent to stdout.

## pdftoppm

Pdftoppm converts Portable Document Format (PDF) files to  color  image files  in Portable Pixmap (PPM) format, grayscale image files in Porta-
ble Graymap (PGM) format, or monochrome image files in Portable  Bitmap (PBM) format.

Pdftoppm reads the PDF file, PDF-file, and writes one PPM file for each page, PPM-root-nnnnnn.ppm, where nnnnnn is the page  number.   If  PPM-
root  is '-', the image is sent to stdout (this is probably only useful when converting a single page).

## pdftops

Pdftops converts Portable Document Format (PDF) files to PostScript  so they can be printed.

Pdftops reads the PDF file, PDF-file, and writes a PostScript file, PS-file.  If PS-file  is  not  specified,  pdftops  converts  file.pdf  to
file.ps  (or  file.eps  with  the -eps option).  If PS-file is '-', the PostScript is sent to stdout.