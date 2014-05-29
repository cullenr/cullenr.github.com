---
title: Qt Cef Osx Window Initialisation
layout: post
---

I have been workiong on a CEF and Qt project. Just a note, its really important to intitalise the QWidget by adding it to the display list (e.g. `setCentralWidget(myCefWidget)`) before you call `SetAsChild(myCefWidget's NSView)` when creating a browser.