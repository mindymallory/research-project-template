---
permalink: /need-word/
layout:    default
title:     Word
nobio:     true
output: md_document
---



Collaborating with Microsoft Word Users
=======================================

Many of us have colleagues who expect to recieve and be welcomed to edit
Microsoft Word documents. Fortunately, reproducability can be
maintained. With the `manuscript-example.Rmd` file open, notice that the
`knit PDF` button is actually a drop down menu and `knit Word` is an
option. If you click it, it will return to you a Microsoft Word document
that you can deliver to your colleague or professor.

They can be formatted with a .docx template. See the 'Style Reference\`
description on
[this](http://rmarkdown.rstudio.com/word_document_format.html) page.
Using the template will keep you having to format the whole thing every
time you update your colleagues and professors.

You might have noticed that there is also a `tablesandfigures.Rmd` file
in the root directory. This is for users who will need to produce Word
documents. I have found no clean way to produce decently formatted
tables and figures in Word using this method. I recommend keeping tables
and figures in a separate docuemnt that you always render as a PDF, and
a separate file for the manuscript text.

Equations are still a problem. Pandoc can interpret math symbols
surrounded by `$`, as `$\exp^{i \pi} = -1$` will be rendered as
exp<sup>*i**π*</sup> =  − 1. However, these equations are not
automatically numbered. To get automatically numbered equations that can
be cross-referenced, they must be produced with pure Latex code. As in,

`\begin{equation} \Delta y_t = \alpha + \gamma y_{t-1} + \delta_1 \Delta y_{t-1} + \dots + \delta_{p-1} \Delta y_{t-p-1} + \epsilon_t \end{equation}`

being rendered as,


Δ*y*<sub>*t*</sub> = *α* + *γ**y*<sub>*t* − 1</sub> + *δ*<sub>1</sub>Δ*y*<sub>*t* − 1</sub> + … + *δ*<sub>*p* − 1</sub>Δ*y*<sub>*t* − *p* − 1</sub> + *ϵ*<sub>*t*</sub>

The trouble is that Latex is ignored by pandoc when producing Word
documents so when you knit the Word document after writing your
equations in pure Latex, they will be missing from the Word docuemnt.
This means you will have to replace them in the Word document one way or
another. There is a reasonable workaround. [Iguana
Tex](http://www.jonathanleroux.org/software/iguanatex/) is a Microsoft
Powerpoint add-in that takes Latex equations and returns
copy-and-pasteable figures of typeset equations. I recommend creating
one new slide for each equation in your document, then use Iguana Tex to
obtain figures of your equations that can be pasted into the Word
document.
