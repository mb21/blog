---
layout: post
title:  The sad state of automated layouting solutions
date:   2016-08-13
tags:   tech design
---

Back in 2007, I watched this [talk by Håkon Wium Lie, co-inventor of CSS, about his proprietary Prince XML](https://www.youtube.com/watch?v=vcXUrNSvjhU). Basically, he asks, why should you have to go around clicking on pages and menus in layout programs, if instead you could write down the rules for the layout once, then automate PDF generation by feeding it only new content whenever you need something printed. He’s talking about using CSS to layout structured text like HTML, of course.

Since then, I’ve been waiting for the future to arrive in the open source lands, where those of us live that don’t have a ton of cash and are crinching at the mere thought of vendor lock-in.


## InDesign

You would be forgiven to think for a moment about using Adobe InDesign in a headless mode (running on a server without a GUI) to layout documents in an automated fashion. But then you are quickly reminded that InDesign in general, and [InDesign scripting](http://stackoverflow.com/questions/22939280/indesign-server-pdf-creation) in particular, is basically a mess.


## CSS-based solutions

### [Prince](http://www.princexml.com)
- awesome
- proprietary and expensive

### [wkhtmltopdf](http://wkhtmltopdf.org/)
- based on the Qt WebKit rendering engine
- WebKit devs don’t see printing as a priority: CSS3 paged media is [not implemented since 2007](https://bugs.webkit.org/show_bug.cgi?id=15548)
- currently wkhtmltopdf [doesn’t even support hyphens](https://github.com/wkhtmltopdf/wkhtmltopdf/issues/1730), could [use JavaScript](https://github.com/mnater/Hyphenator) instead…?

### [WeasyPrint](http://weasyprint.org)
- CSS layout engine written in Python
- currently [doesn’t support CSS columns](https://github.com/Kozea/WeasyPrint/issues/60)
- doesn’t support JavaScript


## TeX

From [Why is TeX still used?](https://news.ycombinator.com/item?id=2326545)

> The reason TeX is still used is because it is open source and beautiful, because it is the best at handling mathematical notation, and because of its inertial dominance in math and the hard sciences in Academia. The reason TeX has so, so many fixable problems after 30 years is because there is no financial incentive for anyone to fix it.

> The core algorithms are pretty creaky as well. Knuth did a brilliant job coming up with efficient algorithms that could do a fairly good job at breaking lines/paragraphs/pages and could handle book-length documents even on 70s-era hardware, but they've had minimal improvement since then.

> All true. Also, the way indexes, table of contents, bibliographies and cross references work in LaTeX are unholy, fragile hacks. Foot- and endnotes could use some TLC. And on 2011-era hardware we really should have some approximation of globally optimal page breaking.

Never mind all the [other TeX variants](https://www.sharelatex.com/blog/2012/12/01/the-tex-family-tree-latex-pdftex-xelatex-luatex-context.html). [ConTeXt](http://wiki.contextgarden.net) is the least bad, but it’s still not CSS-based, which is for better or worse what everyone is familiar with.