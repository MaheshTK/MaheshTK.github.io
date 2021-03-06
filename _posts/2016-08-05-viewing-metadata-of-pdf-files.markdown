---
published: true
title: Viewing metadata of pdf files
layout: post
---
The metadata hidden in the pdf files can reveal a lot of personal information, more than one may like. The corollary of this is the fact that if used properly, metadata can enrich the pdf experience by bundling structured data in the pdf file.

First step towards handling metadata is to identify which type of data is embedded in the file. For viewing metadata, [EXIFTOOL](http://www.sno.phy.queensu.ca/~phil/exiftool/) developed by Phil Harvey is an excellent tool. It is primarily useful for image files. However, it works equally well for pdf files as well.

## Installing and operating Exiftool

Exiftool can be downloaded [here](http://www.sno.phy.queensu.ca/~phil/exiftool/exiftool-10.25.zip).

It can be placed in system folder (usually C:\Windows folder) after renaming the executable from `exiftool(‑k).exe` to `exiftool.exe` to allow it to be run by typing `exiftool` at the command line.

Once done, fire commandline and start using Exiftool. I prefer to to open the desired folder in explorer, and then right click while holding SHIFT key. Then from context menu, select *open command line here*. 

## Using Exiftool for viewing pdf metadata

Type following in command line to view metadata.

```exiftool -a -g one.pdf ```

Extract metadata to text file

```exiftool -a -g one.pdf  > meta.txt```

To delete metadata of files 

```exiftool -all= one.pdf```

### Extract and update metadata through files.

Generate CSV file with common tags from all images in a directory

```exiftool -csv one.pdf > out.csv```

Update metadata for all images in a directory from CSV file

```exiftool -csv=out.csv one.pdf```

### Delete XMP data of file

For deleting XMP data 

```BeCyPDFMetaEdit one.pdf  -X 1```

### Using BeCyPDFMetaedit for writing metadata

Here `-EditMode 2` sets pdf file for complete rewrite. The `-e 3` sets to encryption. The `-p p` sets permission to degraded printing.

BeCyPDFMetaEdit one.pdf -EditMode 2 -T Title -S Subject -A Author -K Keywords -R Creator -P Producer -X 1 -PWD Open_pwd -e 3 -o Owner_PWD -u User_PWD -p p

[MetaData Extraction](http://www.forensicswiki.org/wiki/Document_Metadata_Extraction)