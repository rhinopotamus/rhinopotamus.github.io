---
layout: post
title:  "Asides in the margin in PreTeXt pdfs"
tags: pretext 
katex: True
---

here is my (under-construction) post about how I made asides appear in the margin of pretext-generated pdfs 

```xsl
<xsl:template match="aside" mode="environment">
    <xsl:text>%% aside: un-numbered margin note&#xa;</xsl:text>
    <xsl:text>\usepackage{marginnote}&#xa;</xsl:text>
    <xsl:text>\tcbset{ asidestyle/.style={&#xa;</xsl:text>
    <xsl:text>enhanced jigsaw, size=fbox,&#xa;</xsl:text>
    <xsl:text>colframe=black, colback=white,&#xa;</xsl:text>
    <xsl:text>boxrule=1pt, leftrule=0pt, rightrule=0pt,&#xa;</xsl:text>
    <xsl:text>arc=0pt, outer arc=1pt, boxsep=1pt, top=1pt, bottom=1pt,&#xa;</xsl:text>
    <xsl:text>nobeforeafter, width=\marginparwidth, fontupper=\scriptsize,&#xa;</xsl:text>
    <xsl:text>if odd page or oneside={flushleft upper}{flushright upper} } }&#xa;</xsl:text>
    <xsl:text>\NewDocumentEnvironment{aside}{m m m +b}&#xa;</xsl:text>
    <xsl:text>{\marginnote{\begin{tcolorbox}[&#xa;</xsl:text>
    <xsl:text>phantomlabel={#3}, asidestyle] #4 \end{tcolorbox} } }&#xa;</xsl:text>
    <xsl:text>{}&#xa;</xsl:text>
</xsl:template>
```

could work for all aside-like but I only use asides

by default, asides get dumped into plain text with no particular styling

xelatex and pdflatex behave differently wrt the \marginnote command so you have to use pdflatex

pretext-generated aside signature is {m m m +b}

an empty title fucks up the styling

may have to swap flushright and flushleft depending on your document

may need to fiddle with marginparwidth depending on how you're using geometry