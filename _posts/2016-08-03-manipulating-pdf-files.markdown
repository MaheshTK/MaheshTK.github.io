---
published: true
title: Manipulating pdf files
layout: post
tags: [pdf, productivity, office]
categories: [office, productivity]
---
|<img src="https://upload.wikimedia.org/wikipedia/commons/e/ec/Pdf_by_mimooh.svg" alt="Drawing" style="width: 120px;"/>| This post pertains with one of most common office workflow issue : manipulating pdf files. Pdf is an ubiquitous format. It has replaced paper in modern offices. Interestingly, pdf files also offer all options, a paper document offers like combining, splitting, rotating and encrtpting. In this blog, an amazing tool called **pdftk** which has these capabilities and much more. Here we will concentrate on merging, splitting, bursting, rotating, encrypting and de-crypting pdf files.|

Slowly and steadily Portable Document Format AKA pdf has become de facto standard for sharing documents and for web publishing in last decade. A pdf file presents many advantages for transmitting documents. As the name indicates portability is the USP of this format. It frees from the most important worry while transmitting documents : whether the document will open at other end. That is what the crucial stage of communication : reception. While interpretation can be left to individual but pdf format will take care that the document will be open for interpretation. It also offers some other advantages such as small size, independence from originating format, web display and open ended format.

## The competition

There are two open softwares which can be used for these purposes.

[PDFTK](https://www.pdflabs.com/tools/pdftk-server/)

[CPDF](http://community.coherentpdf.com/)

The _**cpdf**_ is very powerful. However, it has limited free license which can only be used for personal and academic purposes only. 

The _**pdftk**_ has most commonly used functionalities except cropping and stamping. It is distributed under [GNU General Public License](https://www.gnu.org/licenses/gpl-3.0.en.html) making it possible to use for commercial purposes like in office work.

While CPDF is more powerful and is best choice for personal uses, PDFTK is a general purpose licence which can be used at any application. 

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

To extract only even pages from document

```pdftk A=one.pdf cat A1-20odd output output.pdf```

Write a report on PDF document metadata and bookmarks to report.txt

``pdftk in.pdf dump_data output report.txt``

### Combine two files to generate one output file.

There are various ways, which can be used to combine various files. One can select pdf files, respective page ranges, collate files, reverse page order and combination of all above.

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

### Add stamp or letterhead header to file

Watermark can be added in the background of pages using *background* command. This feature can also be used to add letterhead heading to the document pages. However, it shall be noted that the image is placed in the background. It shall be noted that this command takes first page of background file and use it for all pages in main document.

```pdftk in.pdf background back.pdf output out.pdf````

The *multibackground* command places each page of the background PDF to the corresponding page of the input PDF. If the input PDF has more pages than the stamp PDF, then the final stamp page is repeated across these remaining pages in the input PDF.

If the main file is not transparent, the background image will not be visible. For such cases, *stamp* command can be used.

```pdftk in.pdf stamp foreground.pdf output out.pdf````

### Encrypting and decrypting pdf files

This is next important function is ability to encrypt pdf files and control access to pdf files.

During encryption, two types of passwords can be specified. One is user password which is used for opening and limiting access to pdf file for the recipient. Other is owner password which provides master access.

Encrypt a PDF using 128-bit strength (the default), withhold all permissions (the default)

```pdftk one.pdf output output.pdf owner_pw ownpass```

Encrypt pdf with owner password but provide user password for opening file. It is also noted that input password can also be provided if input file is password protected.

```pdftk one.pdf input_pw A=foopass output output.pdf owner_pw ownerpass user_pw userpass```

Similarly, limited access can be provided by using allow parameter. These privileges include `Printing` , `DegradedPrinting` , `ModifyContents` , `CopyContents`, `AllFeatures`. One such example where degraded printing is allowed.

```pdftk 1.pdf output 1.128.pdf owner_pw foo user_pw baz allow printing```

### Other features

Extract metadata from pdf file

```pdftk in.pdf update_info in.info output out.pdf```

Place metadata to pdf file from txt file

```pdftk in.pdf update_info in.info output out.pdf```

The pdftk has other functionalities such as attaching files to pdf, unpacking files, compress or flatten pdf files. Since, these functions are not very common, these are not covered here.