[![Build Status](https://travis-ci.org/WhereowareFED/WhereowareFED.github.io.svg?branch=master "Build Status")](https://travis-ci.org/WhereowareFED/WhereowareFED.github.io)

# Whereoware Front-End Development Documentation
This repository contains the documentation for front end development at Whereoware on the EPiServer platform. Before contributing, please read the note on [Jekyll's issues with UTF-8 byte order marks (BOMs)](#utf-8-byte-order-marks).

## Troubleshooting build errors: Most common issues
If the pages are not displaying correctly (not taking the markup, missing templates, etc.) or you can't get the repository to build, check the [build logs on Travis CI](https://travis-ci.org/WhereowareFED/WhereowareFED.github.io). Below are some of the issues you'll probably run into first.

 - [UTF-8 byte order marks](#utf-8-byte-order-marks)
 - [Tabs vs. spaces in YAML front matter](#tabs-vs-spaces-in-yaml-front-matter)

### UTF-8 byte order marks
One of the most common issues that keeps Jekyll from working properly is a natural consequence of writing the documentation on Windows: Jekyll can't use files that contain a UTF-8 byte order mark (BOM). So when saving any file that is used by Jekyll, make sure the encoding is **UTF-8 (without BOM)**. If your editor has options for "UTF-8 *with* BOM" and just plain "UTF-8", then select "UTF-8".

#### In Visual Studio
Visual Studio will, by default, automatically encode any files that it touches with a BOM, even if the editor that created the file was using a different encoding. This can be disabled in any version of Visual Studio with the following steps:

 1. Make sure that you have a file open in Visual Studio, and that the file's tab has focus -- the menu option we need won't be available unless this is the case (i.e. if you're on the Source Control Explorer tab).
 2. Go to **File** > **Advanced Save Options...**
 3. In the **Encoding** field, you'll see that "Unicode (UTF-8 with signature) - Codepoint 65001" is currently selected. You'll have to scroll down to find the option we want: **Unicode (UTF-8 _without_ signature) - Codepage 65001**.
 4. Click **OK**, make some change to the file that would allow you to save it, and then save it.

### Tabs vs. spaces in YAML front matter
Some editors will automatically prefer tab characters for indentation rather than individual spaces. However, when writing pages in Jekyll, the [**YAML front matter**](http://jekyllrb.com/docs/frontmatter/) (which all pages in Jekyll must include, even if the front matter empty) must use **two space characters** for each level of indentation, not tabs. If tabs are used, the front matter won't be processed and the page won't be rendered properly.

The best way to counteract this is honestly just to double-check before saving, even if you copied and pasted the front matter from somewhere else.

#### In Visual Studio
Visual Studio's default behavior is to use spaces rather than tabs, but its global default is 4 spaces per level of indentation. It's probably not worth it to change that default to 2 spaces per tab, but if it won't affect your coding style, here's how:

 1. Go to **Tools** > **Options...**
 2. In the navigation tree on the left side of the Options dialog, go to **Text Editor** > **HTML** > **Tabs**.
 3. Change both the **Tab size** and **Indent size** to 2.