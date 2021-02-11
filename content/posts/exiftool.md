---
title: "Exiftool"
date: 2018-04-30T21:10:32-07:00
tags: [tools]
draft: false
---

*exiftool* is a wonderful tool if you like custom renaming of files. It also supports HEIC files (the default format for apple iphones) these days.
sample usages below.

Rename jpg etc based on DateTimeOriginal exif tag  inside the image
```
exiftool -r '-FileName<DateTimeOriginal' -d %Y/%m/%Y-%m-%d_%H-%M-%S%%-c.%%e  -ext JPG -ext PNG -ext jpeg -ext HEIC  -ext GIF .
```

For files which dont have DateTimeOriginal tag rename jpg etc based on FileModifyDate
```
exiftool -r "-FileName<FileModifyDate" -d 'Unknown/%%f%%-c.%%e' -if 'not $DateTimeOriginal' -ext JPG -ext PNG -ext jpeg -ext HEIC -ext GIF .
```

Rename Video files based on MediaCreateDate exif tag  inside the video
```
exiftool -r '-FileName<MediaCreateDate' -d %Y/%m/%Y-%m-%d_%H-%M-%S%%-c.%%e -ext MOV -ext mp4 -ext MP4 .
```

For files which dont have MediaCreateDate tag rename movie etc based on FileModifyDate
```
exiftool -r "-FileName<FileModifyDate" -d 'Unknown/%%f%%-c.%%e' -if 'not $MediaCreateDate' -ext MOV -ext mp4 -ext MP4 .
```

For some files have MediaCreateDate tag set to 00 rename movie etc based on FileModifyDate
```
exiftool -r "-FileName<FileModifyDate" -d 'Unknown/%%f%%-c.%%e' -if '$MediaCreateDate eq "0000:00:00 00:00:00"' -ext MOV -ext mp4 -ext MP4 .
```
