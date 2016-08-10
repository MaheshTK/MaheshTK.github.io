---
published: true
title: Manipulating pdf files using pdftk
layout: post
tags: [pdf, productivity, office]
categories: [office, productivity]
---
|<img src="https://upload.wikimedia.org/wikipedia/commons/e/ec/Pdf_by_mimooh.svg" alt="Drawing" style="width: 120px;"/>| This post pertains with one of most common office workflow issue : manipulating pdf files. Pdf is an ubiquitous format. It has replaced paper in modern offices. Interestingly, pdf files also offer all options, a paper document offers like combining, splitting, rotating and encrtpting. In this blog, an amazing tool called **pdftk** which has these capabilities and much more. Here we will concentrate on merging, splitting, bursting, rotating, encrypting and de-crypting pdf files.|

Slowly and steadily Portable Document Format AKA pdf has become de facto standard for sharing documents and for web publishing in last decade. A pdf file presents many advantages for transmitting documents. As the name indicates portability is the USP of this format. It frees from the most important worry while transmitting documents : whether the document will open at other end. That is what the crucial stage of communication : reception. While interpretation can be left to individual but pdf format will take care that the document will be open for interpretation. It also offers some other advantages such as small size, independence from originating format, web display and open ended format.

The other convenience of pdf files is that these can be treated the same way, as a paper documents can be used. It is possible to bundle together pdfs, crop them, split them and encrypt them. However, for all these advanced operations, special pdf editors are required. The most common editors like [Adobe Acrobat Professional](https://creative.adobe.com/products/acrobat) are pretty steeply priced.

It is perfectly possible to develope a workflow which consists of purely free or open source programs and it can be as powerful or better than these commercial products. 

There are many free pdf readers available including those provided by big commercial products. The [Adobe Acrobat Reader](https://get.adobe.com/reader/) and [PDF-XChange Viewer](http://www.tracker-software.com/product/pdf-xchange-viewer) are such examples. My personal choice is [Foxit Reader](https://www.foxitsoftware.com/products/pdf-reader/) which comes bundled with pretty good pdf printer.

## The competition

However, for manipulating pdf files, very few user friendly options are available. There are two commandline tools which I have found out to be excellent choice for manipulating pdf files. 

[PDFTK](https://www.pdflabs.com/tools/pdftk-server/)

[CPDF](http://community.coherentpdf.com/)

The _**cpdf**_ is very powerful. However, it has limited free license which can only be used for personal and academic purposes only. 

The _**pdftk**_ has most commonly used functionalities except cropping and stamping. It is distributed under [GNU General Public License](https://www.gnu.org/licenses/gpl-3.0.en.html) making it possible to use for commercial purposes like in office work.

While CPDF is more powerful and is best choice for personal uses, PDFTK is a general purpose licence which can be used at any application. 

The main advantage of these programs is that these are free, portable, efficient and powerful. It is also possible to use a scripting language to batch process files.

### Cheat sheet

|Combine| ```pdftk A=one.pdf B=two.pdf cat A B output output.pdf```|
|Special Combine|```pdftk A=one.pdf B=two.pdf cat A1-20 B21-end output output.pdf```|
|Combine all|`pdftk *.pdf cat output newfile.pdf`|
|Extract|```pdftk one.pdf cat 1-12 24-end output output.pdf```|
|Rotate|```pdftk one.pdf cat cat 1east 2-end output out.pdf```|
|Burst|```pdftk one.pdf burst```|
|Encrypt|`pdftk one.pdf output output.pdf owner_pw ownpass`|
|Special Encrypt|`pdftk one.pdf output out.pdf owner_pw foo user_pw baz allow printing`|

### Installation

PDFtk Server is command-line tool for working with PDFs. Though named as server, it also works fine as stand alone program on desktops. It can be downloaded [here](https://www.pdflabs.com/tools/pdftk-server/). 

Once installed it is available at command line. In case of any issue, copy pdftk.exe and dll file to system folder (usually C:\Windows\). 

Command line can be invoked in many ways. One of the simplest way is to open through explorer. Open the working folder, right click while pressing SHIFT key. From context menu, select *Open command window here*. Voila !! command line with curser at present folder is open. Just start typing the commands.

### Basic command structure

Simple command for pdftk looks like

`pdftk <input files> <operation> <arguments> output <output fiename> `

A more complicated command looks like

`pdftk <input files> input_pw <password> <operation> <arguments> output <output fiename> encrypt_128 owner_pw <password> user_pw <password> verbose dont_ask`

### How to specify input files

The input files can be specified as a lateral list for example

`one.pdf two.pdf three.pdf`

`*.pdf`

`"C:\test file\one.pdf" two.pdf`

Note that in all examples, the files referred from the parent folder. However, for third example, the absolute path is given. Also note the double quotes (" ") as the folder path contains a space character. Similarly, it is also possible to provide relative path.

It is very convenient to provide handles to input files as these can be convenient to use the handles in specifying operations on the files. 

`A=one.pdf B=two.pdf` 

In case, the input file is encrypted, the password shall be provided. These are taken in order by default. Otherwise, password can be provided as per handle as `input_pw  A=passwordA B=passwordB`

### How to specify output file range

Page range can be specified using the page numbers of file with or without handles. To specify page 12 to 24 command as follows.

`12-24` or `A12-24`

Use `end` as suffix to specify last page of the file. Use `r` as prefix to specify reverse order of pages. Use `odd` and `even' to specify odd or even pages of the document. Like,

`A1-12 A14-end` to exclude page 13 

`r3-r1` to specify last three pages of the document.

`Aend-1` will select all pages in reverse order.

`A2-30evenleft` will select even pages in page range 2 to 30 and rotate them by 90 degrees counterclockwise.

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

### Combine files 

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

### Add stamp or letterhead header 

Watermark can be added in the background of pages using *background* command. This feature can also be used to add letterhead heading to the document pages. However, it shall be noted that the image is placed in the background. It shall be noted that this command takes first page of background file and use it for all pages in main document.

```pdftk one.pdf background back.pdf output out.pdf````

The *multibackground* command places each page of the background PDF to the corresponding page of the input PDF. If the input PDF has more pages than the stamp PDF, then the final stamp page is repeated across these remaining pages in the input PDF.

If the main file is not transparent, the background image will not be visible. For such cases, *stamp* command can be used.

```pdftk one.pdf stamp foreground.pdf output out.pdf````

### Encrypting and decrypting pdf files

This is next important function is ability to encrypt pdf files and control access to pdf files.

During encryption, two types of passwords can be specified. One is user password which is used for opening and limiting access to pdf file for the recipient. Other is owner password which provides master access.

Encrypt a PDF using 128-bit strength (the default), withhold all permissions (the default)

```pdftk one.pdf output output.pdf owner_pw ownpass```

Encrypt pdf with owner password but provide user password for opening file. It is also noted that input password can also be provided if input file is password protected.

```pdftk one.pdf input_pw A=foopass output output.pdf owner_pw ownerpass user_pw userpass```

Similarly, limited access can be provided by using allow parameter. These privileges include `Printing` , `DegradedPrinting` , `ModifyContents` , `CopyContents`, `AllFeatures`. One such example where degraded printing is allowed.

```pdftk one.pdf output out.pdf owner_pw foo user_pw baz allow printing```

### Other features

Extract metadata from pdf file

```pdftk one.pdf update_info in.info output out.pdf```

Place metadata to pdf file from txt file

```pdftk one.pdf update_info in.info output out.pdf```

The pdftk has other functionalities such as attaching files to pdf, unpacking files, compress or flatten pdf files. Since, these functions are not very common, these are not covered here.

### Limitations of pdftk

Of course, nothing in life is perfect. Especially if it is free. Pdftk has its own limitations. Though, over time user becomes comfortable with command line after initial period of hesitation, it may be considered restraining by many.

One important functionality missing from pdftk is ability to crop pages. Ability to convert to image files and linearisation is also missing.

### Conclusion

Apart from these two limitations, pdftk is indeed an extremely powerful tool capable of batch scripting. Once you get hang of it, its difficult to part ways from it.