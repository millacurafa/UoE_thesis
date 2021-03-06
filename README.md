Template for a LaTeX PhD UoE Thesis.
====================================

Author: Magnus Hagdorn

This template setup allows you to produce:
* a thesis that adheres to the UoE regulations
  (at least my interpretations of them and no-one complained when
  I submitted mine)
* about using the logo: https://www.ed.ac.uk/communications-marketing/resources/university-brand
* a nicely formatted pdf version with and without hyperlinks of the same thesis
  and with single line spacing, etc
* individual documents for each chapter

Indivdual chapters reside in their own directories. (Re)-Define the macro `\dir`
to the relative path where files for the current chapter can be found. You can
then use `\dir` to include files or graphics, e.g.

```
\newcommand{\dir}{theory}
\input{\dir/theory.tex}
\includegraphics[width=0.7\textwidth]{\dir/figs/geek_flow_chart_nyt.png}
```

Using this macro allows you to distribute files over a number of directories.

The common directory
--------------------
This directory contains files used by all the documents:
* the packages.tex files contains a lits of packages used
* the definitions.tex file contains settings and macros

The preface directory
---------------------
contains files for the preface.

The template directory
----------------------
This directory should be copied for each chapter. Rename the sub directory 
accordingly. All files should be kept in this sub directory. If you want to
produce a document for the individual chapter, run latex on the chapter.tex
file.

Bibliography
------------
You can have your bibliography database `bibliography.bib` in any directory you
like as long as you set the `BIBINPUTS` environment variable to the directory
containing your bib files. 

The thesis directory
--------------------
This directory pulls files from the preface and the chapter directories together
to produce the complete thesis. There are 3 different top level files:
* latex ed_thesis.tex
  to produce official 1.5 (?) spaced thesis which adheres to the regulations
* latex nicepdf_thesis.tex
  to produce a dvi file to be processed using dvipdft. The resulting pdf will
  have colour hyperlinks.
* latex niceps_thesis.tex
  to produce a single spaced thesis without the hyperlinks for printing

All three top level files include the thesis.tex file. This file includes the
actual preface and chapter files. 

You can use the `\ifthenelse` macro to do specific things for either the standard
or nice thesis version, e.g.
```
\ifthenelse{\boolean{edthesis}}
 {
   Do something specific for the offical version 
}
{
   Do something else for the nice version
}
```

If you have any questions or problems contact it.geos@ed.ac.uk.

This template is licensed under Creative Commons CC BY-SA: https://creativecommons.org/licenses/by-sa/4.0/