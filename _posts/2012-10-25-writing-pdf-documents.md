---
title: Writing PDF Documents
layout: post
---

I have never been a great fan of the PDF document format, generally I don't care much for binary documents and dislike having to download/ pay for software to read something that could well be written in plain text. Sometimes however, it is necessary to attempt to protect the contents of a document such as your CV.

I used to use [pdfTeX](http://www.tug.org/applications/pdftex/) with [pandoc](http://johnmacfarlane.net/pandoc/) to write pdf files, which works fine and you can do all sorts of other handy things with these pieces of software. I recently needed to write a pdf on a new work machine with limited disk space, downloading the 2GB installer for mactex was not an option. I came across the brilliantly named [wkhtmltopdf](http://code.google.com/p/wkhtmltopdf/) which was a real help. Despite its name this is a really easy to use and install piece of software.

The project page for wkhtmltopdf mentions that the tool uses QT 4.4 for its WebKit widget, a benefit of this being a good standard of rendering and cross platform support. Thumbs up to the wkhtmltopdf authors for this very helpful and competitively lightweight tool.

[wkhtmltopdf](http://code.google.com/p/wkhtmltopdf/) http://code.google.com/p/wkhtmltopdf/
