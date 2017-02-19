---
layout: post
title: How to add or remove a byte order mark
date: '2012-07-19T17:36:00+10:00'
tags: []
tumblr_url: http://speed-rs.tumblr.com/post/27543408832/how-to-add-or-remove-a-byte-order-mark
---

> A byte order mark (BOM) consists of the character code [...] at the beginning of a data stream, where it can be used as a signature defining the byte order and encoding form, primarily of unmarked plaintext files. Under some higher level protocols, use of a BOM may be mandatory (or prohibited) in the Unicode data stream defined in that protocol.

*Unicode, Inc.*[^1]

At the moment, I'm testing a few different scenarios where a client application uploads various XML files to a Java web service endpoint. Initially, this service didn't support files with or without a BOM (I can't remember which off the top of my head). At any rate, there's a need to produce sample files of both types; UTF-8 and UTF-8 with BOM.

For this example, I tested with both Notepad++[^2] (6.1) or Sublime Text 2 [^3] (2.0.1.2217).

1. Open file in your editor of choice.
1. Select the required encoding option:

   * In Notepad++, pick `Encoding` from the main menu and pick either `Encode in UTF-8` (implied *with* BOM) or `Encode in UTF-8 without BOM`.
   * In Sublime Test 2, pick `File > Save with Encoding` and pick either `UTF-8` (implied *without* BOM) or `UTF-8 with BOM`.

1. You will then need to double-check that you've saved the file to apply encoding changes.
1. To ensure that the BOM is now present or absent in your file, I recommend opening it up in a hex editor. There are many out there but I use the  HexView [^4] plugin:


        //With BOM:
        00000000:  efbb bf42 4f4d 2074 6573 7465    :...BOM test
        //Without BOM:
        00000000:  424f 4d20 7465 7374              :BOM test

You can clearly see that there is a preceeding byte sequence of `0xEF`,`0xBB` and `0xBF` [^5], as would be expected for a UTF-8 file with a BOM present.

[^1]: [http://www.unicode.org/faq/utf_bom.html#BOM](http://www.unicode.org/faq/utf_bom.html#BOM)

[^2]: [http://notepad-plus-plus.org/](http://notepad-plus-plus.org/) - An excellent text editor I've used for several years.

[^3]: [Sublime Text](http://www.sublimetext.com/) - Seems to be the flavour-of-the-month editor, recommended to me by <a href="https://twitter.com/gmrph">@gmrph. I've been pretty happy with it so far, especially in terms of it's [simplified package management](http://wbond.net/sublime_packages/package_control) abilities. It's also cross-platform!

[^4]: <a href="https://github.com/facelessuser/HexViewer">https://github.com/facelessuser/HexViewer</a> - A hex viewer for Sublime Text 2.

[^5]: <a href="http://www.unicode.org/faq/utf_bom.html#BOM">http://www.unicode.org/faq/utf_bom.html#BOM</a> - Q: When a BOM is used, is it only in 16-bit Unicode text?