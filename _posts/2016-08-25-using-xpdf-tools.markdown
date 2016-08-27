---
published: true
title: Using XPDF tools
layout: post
---
The  [XPDF](http://www.foolabs.com/xpdf/download.html) provides some really handy tools. Very notable one is __pdfimages__ which can extract images from the pdf files. Other useful tools include __pdftopng__ and __pdfdetach__ .

## xpdf

Xpdf  is a viewer for Portable Document Format (PDF) files.  To run xpdf to open file.pdf at page 18, type:

`xpdf file.pdf 18`

## Options used in xpdf tools

In general format of command is like 

`pdftool [options] input.pdf output_directory`

The common commands are listed below.

| `-f number` | page number of _f_irst page to be operated |
| `-l number` | page number of _l_ast page to be operated |
| `-j` | Images in DCT format are  saved  as  _J_PEG  files else in PBM/PPM format. |
| `-r number` | Specifies the _r_esolution, in DPI.  The default is 150 DPI. |
| `-mono` |  Generate a monochrome image (instead of a color image). |
| `-gray` | Generate a grayscale image (instead of a color image). |

## pdfimages

Pdfimages saves images from a Portable Document Format  (PDF)  file  as Portable Pixmap (PPM), Portable Bitmap (PBM), or JPEG files. Pdfimages  reads  the  PDF file, scans one or more pages, PDF-file, and writes one PPM, PBM, or JPEG file for each image,  image-root-nnnn.xxx, where  nnnn  is the image number and xxx is the image type (.ppm, .pbm, .jpg). It may be noted that pdfimages extracts the raw image data from the  PDF  file,  without performing  any  additional  transforms.  Any rotation, clipping, color inversion, etc. done by the PDF content stream is ignored.

`pdfimages one.pdf ../images`

`pdfimages -f 10 -l 18 -j -opw owner_pwd upw user_pwd one.pdf ../images'

## pdftopng

Pdftopng converts  Portable  Document  Format  (PDF)  files  to  color,grayscale, or monochrome image files in Portable Network Graphics (PNG) format. Pdftopng reads the PDF file, PDF-file, and writes one PNG file for eachpage,  PNG-root-nnnnnn.png,  where  nnnnnn is the page number.  If PNG root is '-', the image is sent to stdout (this is probably only  usefulwhen converting a single page).

`pdftopng one.pdf ../images`

`pdftopng -f 10 -l 18 -r 300 -gray one.pdf ../images`

## pdfdetach

Pdfdetach lists or extracts embedded files (attachments) from a  Portable Document Format (PDF) file.

`pdfdetach one.pdf`

`pdfdetach -saveall -o ../images -opw owner_pwd upw user_pwd one.pdf `

## pdffonts

Pdffonts  lists the fonts used in a Portable Document Format (PDF) file along with various information for each font.

## pdftohtml

Pdftohtml converts Portable Document Format (PDF) files to HTML. Pdftohtml reads the PDF file, PDF-file, and places  an  HTML  file  for each page, along with auxiliary images in the directory, HTML-dir.  

## pdfinfo

Pdfinfo prints the contents of the 'Info' dictionary (plus  some  other useful information) from a Portable Document Format (PDF) file.

The 'Info' dictionary contains the following values:

    title    subject    keywords    author    creator    producer    creation date    modification_date

In addition, the following information is printed:

    tagged (yes/no)	form (AcroForm / XFA / none)    page count    encrypted flag (yes/no)
    print and copy permissions (if encrypted)    page size and rotation    file size
    linearized (yes/no)    PDF version    metadata (only if requested)

## pdftotext

Pdftotext converts Portable Document Format (PDF) files to plain text. Pdftotext reads the PDF file, PDF-file, and writes a text  file,  text-file.   If  text-file  is not specified, pdftotext converts file.pdf to file.txt.  If text-file is '-', the text is sent to stdout.

`pdftotext -f 10 -l 18 one.pdf`

`pdftotext -layout -table -raw -opw owner_pwd upw user_pwd one.pdf ../text/out.txt`


## pdftoppm

Pdftoppm converts Portable Document Format (PDF) files to  color  image files  in Portable Pixmap (PPM) format, grayscale image files in Porta-ble Graymap (PGM) format, or monochrome image files in Portable  Bitmap (PBM) format. Pdftoppm reads the PDF file, PDF-file, and writes one PPM file for each page, PPM-root-nnnnnn.ppm, where nnnnnn is the page  number.   If  PPM-root  is '-', the image is sent to stdout (this is probably only useful when converting a single page). For command structure refer `pdftopng`.

## pdftops

Pdftops converts Portable Document Format (PDF) files to PostScript  so they can be printed. Pdftops reads the PDF file, PDF-file, and writes a PostScript file, PS-file.  If PS-file  is  not  specified,  pdftops  converts  file.pdf  to file.ps  (or  file.eps  with  the -eps option).  If PS-file is '-', the PostScript is sent to stdout.