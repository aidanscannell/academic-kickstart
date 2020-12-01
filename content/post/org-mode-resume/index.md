+++
title = "Creating a CV/Resume in Org-Mode using LaTeX Templates"
author = ["Aidan Scannell"]
date = 2020-12-01
tags = ["emacs", "org-mode", "cv", "resume", "doom-emacs"]
draft = false
url_pdf = "post/org-mode-resume/resume.pdf"
url_code = "https://github.com/aidanscannell/my-org-resume"
+++

Over the last few years I have been trying to find the best tools for managing my CV/resume.
Previously I was maintaining a JSON file that I could export to pdf/html using [JSON Resume](https://jsonresume.org/) and [HackMyResume](https://github.com/hacksalot/HackMyResume).
They provide a well structured format (JSON Schema) for storing your CV data
and there are a range of [themes](https://jsonresume.org/themes/) that you can use to style your CV when exporting to pdf/html.
I personally think it's a great idea and I have been using it for the last couple of years.
However, when exporting to pdf/html I found that my CV data was being used slightly differently by each theme,
and I ended up managing multiple JSON files; one for each theme I wanted to use!
I also struggled exporting to a nicely formatted compact CV, and to be honest,
JSON is just a horrible format for humans to work with; you can't even comment out lines!
I would much prefer to manage a YAML or TOML file. I know you can export YAML/TOML to JSON
so you could probably quite easily work this into your CV workflow.

However, now that I have a personal website, I do not really need a html version of my CV;
I would much prefer a nicely formatted pdf.
Ideally, I would like to,

1.  have all of my CV data in a single file e.g. experience, education, achievements, etc,
2.  easily export the data to a nicely formatted CV (pdf),
3.  easily manage what content is exported,
    -   i.e. only export content relevant to a specific job.

I thought about making a theme for JSON Resume but now that I use Org-mode for writing all of my LaTeX documents,
writing my CV in Org-mode was all to appealing.
There are loads of great LaTeX CV templates out there which I want to be able use, for example,
[this AltaCV template](https://www.overleaf.com/latex/templates/altacv-template/trgqjpwnmtgv).
I have managed a LaTeX CV in the past and it ended up very messy.
Luckily, writing LaTeX documents in Org-mode is much easier and also provides all the extra features of Org-mode,
e.g. code folding, TODOs, running source code, tagging sections and much, much more!
In this post I want to show how any LaTeX CV template can easily be set up in org-mode and I will achieve this
via an example, [this AltaCV template](https://www.overleaf.com/latex/templates/altacv-template/trgqjpwnmtgv).

{{% toc %}}


## Structuring the Org Document {#structuring-the-org-document}

Before we dive into the details of configuring and writing our Org-mode CV, I want to
show how the org-mode document can be structured to make it easy to manage content.

The `:noexport:` tag allows trees and/or sub-trees to not be exported into the pdf.
I tag all of my configuration subtrees with `:noexport:` and all of the content
that I do not want to export for a particular job. For example, I might not want to
export a particular project or I might not want to export the publications section.

The `:ignore:` tag allows the contents of a tree or sub-tree to be exported without
exporting the heading. This is useful for giving the org-mode document good structure so
that it is easy to work with the file.
For example, I have a tree with the heading `Backmatter` and all that it contains is the
end column and end document commands (`\end{paracol}` and `\end{document}`). I do not like it when
the end document tag comes under the previous heading; what if I decide I do not want to export that section
or I delete it!
The `:ignore:` tag functionality is provided by the `ignore-headlines` function in the
`ox-extra` package. In [Doom Emacs](https://github.com/hlissner/doom-emacs) I import the function and activate it with:

```lisp
(after! org
  (use-package! ox-extra
    :config
    (ox-extras-activate '(latex-header-blocks ignore-headlines))))
```

Lovely stuff! Using these tags I structure my org mode document with
the following headings, subheadings and tags.

-   Config `:noexport:`
    -   LaTeX Config
    -   Exporter Settings
    -   Macros
-   CV Header `:ignore:`
    -   Photo & Tagline `:ignore:`
    -   Personal Info `:ignore:`
-   CV Column one `:ignore:`
    -   Experience
        -   PhD Researcher `:ignore:`
        -   Teaching Assistant `:ignore:`
    -   Projects
        -   Project 1 `:ignore:`
        -   Project 2 `:ignore:`
        -   Do not export this project `:noexport:`
    -   A day of my life `:noexport:`
    -   Publications `:noexport:`
    -   Volunteering
        -   FARSCOPE Course Rep `:ignore:`
        -   Code Club `:ignore:`
        -   Drivetrain `:ignore:`
        -   Snowboard Captain `:ignore:`
-   CV Column two `:ignore:`
    -   Skills
    -   Education
    -   My Life Philosophy `:noexport:`
    -   Achievements
    -   Languages `:noexport:`
    -   Referees
-   Backmatter `:ignore:`

I am using [this AltaCV LaTeX template](https://www.overleaf.com/latex/templates/altacv-template/trgqjpwnmtgv) which utilises columns to fit more content onto a single.
I separate the columns into their own trees which makes working with columns easy!
At the start of the `column one` tree I add the following LaTeX export block to configure two columns:

```lisp
#+begin_export latex
\begin{paracol}{2}
#+end_export
```

At the start of the `column two` tree I switch to the right column by adding the following:

```lisp
#+begin_export latex
\switchcolumn
#+end_export
```

And in the `Backmatter` tree I end the paracol and document environments.

```lisp
#+begin_export latex
\end{paracol}
\end{document}
#+end_export
```

Easy!


## Global Configuration for Org-Mode's LaTeX Exporter {#global-configuration-for-org-mode-s-latex-exporter}

In order to export to pdf via LaTeX you need to configure org-mode's LaTeX exporter.
Here is the part of my Doom Emacs config relevant to the org-mode LaTeX exporter.

```lisp
(after! org
  ;; Import ox-latex to get org-latex-classes and other funcitonality
  ;; for exporting to LaTeX from org
  (use-package! ox-latex
    :init
    ;; code here will run immediately
    :config
    ;; code here will run after the package is loaded
    (setq org-latex-pdf-process
          '("pdflatex -interaction nonstopmode -output-directory %o %f"
            "bibtex %b"
            "pdflatex -interaction nonstopmode -output-directory %o %f"
            "pdflatex -interaction nonstopmode -output-directory %o %f"))
    (setq org-latex-with-hyperref nil) ;; stop org adding hypersetup{author..} to latex export
    ;; (setq org-latex-prefer-user-labels t)

    ;; deleted unwanted file extensions after latexMK
    (setq org-latex-logfiles-extensions
          (quote ("lof" "lot" "tex~" "aux" "idx" "log" "out" "toc" "nav" "snm" "vrb" "dvi" "fdb_latexmk" "blg" "brf" "fls" "entoc" "ps" "spl" "bbl" "xmpi" "run.xml" "bcf" "acn" "acr" "alg" "glg" "gls" "ist")))

    (unless (boundp 'org-latex-classes)
      (setq org-latex-classes nil)))
```


## Local Configuration for Org-Mode CV File {#local-configuration-for-org-mode-cv-file}

Exporting an org file to LaTeX requires a LaTeX class to be defined in you Emacs config.
In particular, you need to append a template to `org-latex-classes`.
I copied the LaTeX preamble (everything before `\begin{document}`) from
[this AltaCV template](https://www.overleaf.com/latex/templates/altacv-template/trgqjpwnmtgv) and removed all of the package imports (`\usepackage{}`).
I do no want this LaTeX class to always be globally available through my Emacs config
as I will only be using it in this org file. So
instead of adding it in my Emacs config, I add it inside a source block in my resume file (`resume.org`),
under the `Config` heading;
as source blocks allows us to run `emacs-lisp` code inside the org file.
I use the following source block inside my `resume.org` file
to append the LaTeX class to the `org-latex-classes` variable:

```lisp
;; #+BEGIN_SRC emacs-lisp :exports none  :results none :eval always
(add-to-list 'org-latex-classes
             '("altacv" "\\documentclass[10pt,a4paper,ragged2e,withhyper]{altacv}

% Change the page layout if you need to
\\geometry{left=1.25cm,right=1.25cm,top=1.5cm,bottom=1.5cm,columnsep=1.2cm}

% Use roboto and lato for fonts
\\renewcommand{\\familydefault}{\\sfdefault}

% Change the colours if you want to
\\definecolor{SlateGrey}{HTML}{2E2E2E}
\\definecolor{LightGrey}{HTML}{666666}
\\definecolor{DarkPastelRed}{HTML}{450808}
\\definecolor{PastelRed}{HTML}{8F0D0D}
\\definecolor{GoldenEarth}{HTML}{E7D192}
\\colorlet{name}{black}
\\colorlet{tagline}{PastelRed}
\\colorlet{heading}{DarkPastelRed}
\\colorlet{headingrule}{GoldenEarth}
\\colorlet{subheading}{PastelRed}
\\colorlet{accent}{PastelRed}
\\colorlet{emphasis}{SlateGrey}
\\colorlet{body}{LightGrey}

% Change some fonts, if necessary
\\renewcommand{\\namefont}{\\Huge\\rmfamily\\bfseries}
\\renewcommand{\\personalinfofont}{\\footnotesize}
\\renewcommand{\\cvsectionfont}{\\LARGE\\rmfamily\\bfseries}
\\renewcommand{\\cvsubsectionfont}{\\large\\bfseries}

% Change the bullets for itemize and rating marker
% for \cvskill if you want to
\\renewcommand{\\itemmarker}{{\\small\\textbullet}}
\\renewcommand{\\ratingmarker}{\\faCircle}
"

               ("\\cvsection{%s}" . "\\cvsection*{%s}")))
;; #+END_SRC
```

> I have had to comment the begin/end source blocks so remember to uncomment them!
> I run the source block with `Ctrl-c Ctrl-c` when I want to work on my CV.
> It only needs to be done once for each Emacs session.

The `altacv` LaTeX class is now added to the list of templates.
I've named the class `altacv` so the LaTeX class is used by adding the following line to the org file:

```lisp
#+LATEX_HEADER: altacv
```


### Export Org-Mode Headings as Macros {#export-org-mode-headings-as-macros}

The [AltaCV LaTeX template](https://www.overleaf.com/latex/templates/altacv-template/trgqjpwnmtgv) defines a macro for a cv section so I set org headings to be exported as
a `cvsection` (in the previous source block) with the following,

```lisp
 ("\\cvsection{%s}" . "\\cvsection*{%s}")))
```

Now any `org-mode` heading, e.g.

```lisp
*Experience
```

will be exported to LaTeX as:

```lisp
\cvsection{Experience}
```


### LaTeX Packages {#latex-packages}

Whilst I was on a roll with emacs-lisp source blocks I decided to
import the LaTeX packages via the exporter. I did this by setting them in the latex exporter's
`org-latex-default-packages-alist` variable with:

```lisp
;; #+BEGIN_SRC emacs-lisp :exports none  :results none :eval always
(setq org-latex-packages-alist 'nil)
(setq org-latex-default-packages-alist
      '(("rm" "roboto"  t)
        ("defaultsans" "lato" t)
        ("" "paracol" t)
        ))
;; #+END_SRC
```

> Again, I had to comment the begin/end source blocks so remember to uncomment them!
> I run the source block with `Ctrl-c Ctrl-c` when I want to work on my CV.
> It only needs to be done once for each Emacs session.

The packages we need will now be added by the latex exporter.


### Org Export Settings {#org-export-settings}

I configure my name and the export file name by adding the following lines to the `Config`
tree:

```lisp
#+AUTHOR: Aidan Scannell
#+EXPORT_FILE_NAME: ./resume.pdf
```

I also ensure the exporter does not generate a table of contents (toc), doesn't export a title and sets
the number of headline levels to export to 1:

```lisp
#+OPTIONS: toc:nil title:nil H:1
```


### LaTeX Preamble {#latex-preamble}

I add the bibliography file containing my publications with the following

```lisp
#+LATEX_HEADER: \addbibresource{aidan.bib}
```

[The AltaCV LaTeX template](https://www.overleaf.com/latex/templates/altacv-template/trgqjpwnmtgv) splits the content into two columns using `\columnratio`
so I also add the following latex header:

```lisp
#+LATEX_HEADER: \columnratio{0.6} % Set the left/right column width ratio to 6:4.
```

I put all of this configuration in the `Config` tree in my Org file.


### Macros {#macros}

The [AltaCV LaTeX template](https://www.overleaf.com/latex/templates/altacv-template/trgqjpwnmtgv) defines four macros that I wanted to use.
These are for formatting the `cvevent`, `cvachievement`, `cvtag` and `divider` (horizontal dashed line).
I convert the LaTeX macros to [org-mode macros](https://orgmode.org/manual/Macro-Replacement.html) by adding the following lines:

```lisp
#+MACRO: cvevent \cvevent{$1}{$2}{$3}{$4}
#+MACRO: cvachievement \cvachievement{$1}{$2}{$3}{$4}
#+MACRO: cvtag \cvtag{$1}
#+MACRO: divider \par\divider
```

An org-mode macro can be used with three curly braces, the macro name and comma separated arguments, e.g:

```lisp
{{{cvevent(PhD Researcher, University of Bristol,Sept 2018 -- Ongoing, Bristol\, UK)}}}
```

This macro has 4 arguments and the comma in the location `Bristol, UK` has been escaped using a backslash.


#### cvevent {#cvevent}

I use the `cvevent` macro to format the title/organisation/date/location of
each entry of my work experience, projects, volunteering and education.
For example:

```lisp
{{{cvevent(PhD Researcher, University of Bristol,Sept 2018 -- Ongoing, Bristol\, UK)}}}
```


#### cvtag {#cvtag}

I use the `cvtag` macro to add nicely formatted tags at the bottom of each experience/project etc.
For example:

```lisp
{{{cvtag(Probabilistic modelling)}}}
{{{cvtag(Gaussian processes)}}}
{{{cvtag(Variational inference)}}}
```


#### cvachievement {#cvachievement}

I use the `cvachievement` macro to add each achievement, for example:

```lisp
{{{cvachievement(\faTrophy, Full Sporting Colours, Awarded full colours for outstanding achievements in snowboarding.)}}}
```


#### divider {#divider}

I use the `divider` macro to insert a horizontal dashed line between separate entries, for example:

```lisp
{{{cvachievement(\faTrophy, Full Sporting Colours, Awarded full colours for outstanding achievements in snowboarding.)}}}

{{{divider}}}

{{{cvachievement(\faCertificate, Starting To Teach, Acquired the knowledge and skills to establish myself as a confident\, enthusiastic and effective teacher who is able to engage\, encourage and develop students' learning.)}}}
```

Woop, that is all our configuring done!


## Content {#content}

I use LaTeX export blocks to configure parts of the [AltaCV LaTeX template](https://www.overleaf.com/latex/templates/altacv-template/trgqjpwnmtgv) that I will only be using once,
in particular, the CV header.


### Photo & Tagline {#photo-and-tagline}

I set my name, tag line and photo with the following LaTeX export block.

```lisp
      #+begin_export latex
      \name{Aidan Scannell}
      \photoR{2.8cm}{aidan_portrait.jpeg}
      \tagline{PhD Researcher}
      #+end_export
```


### Personal Info {#personal-info}

I configure my personal info and links with the following LaTeX export block.

```lisp
      #+begin_export latex
      \personalinfo{%
          \homepage{www.aidanscannell.com}
          \email{scannell.aidan@gmail.com}
          \phone{+44 787 558 3912}
          \location{Bristol, UK}
          \github{aidanscannell}
          \linkedin{aidan-scannell-82522789/}
      }
      \makecvheader
      #+end_export
```


### Publications {#publications}

In the publications section I use the following source block to format
the publications in my bib file:

```lisp
#+begin_export latex
\nocite{*}
\printbibliography[heading=pubtype,title={\printinfo{\faBook}{Books}},type=book]
\divider
\printbibliography[heading=pubtype,title={\printinfo{\faFile*[regular]}{Journal Articles}},type=article]
\divider
\printbibliography[heading=pubtype,title={\printinfo{\faUsers}{Conference Proceedings}},type=inproceedings]
#+end_export
```


## Conclusion {#conclusion}

I have tried to show how any LaTeX template can easily be set up in org-mode in order to reap the benefits of
noexport/ignore tags, tree/sub-tree folding, running source code etc.
I covered the majority of the configuration and showed how each part can be used to write content.
Of particular importance are the LaTeX macros as they govern the majority of the pretty formatting.
I showed how to convert LaTeX macros into org-mode macros and then how to use them.
Check out my [CV org file](https://github.com/aidanscannell/my-org-resume) to see everything put together (and any topics I forgot to mention).

I am really happy with how easy it was to take a LaTeX template and set it up in Org-mode.
I already think that managing this Org-mode CV is going to be much easier than my previous
JSON Resume/HackMyResume workflow.
You can see my CV [source files here](https://github.com/aidanscannell/my-org-resume) and a pdf generated from the source files
[here](./resume.pdf).
