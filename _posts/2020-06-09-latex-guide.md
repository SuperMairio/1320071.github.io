---
layout: post
title:  Simple Guide to Basic LaTeX
subtitle: For beginners and me, when I forget all the syntax after months of not touching Overleaf
date:   2020-06-09 16:04:51 +0100
tags: [Coding, LaTeX]
---

## Headers

![Headers](assets/img/section.png)  \
`\section{}` \
![Headers](assets/img/subsection.png) \
`\subsection{}` \
![Headers](assets/img/subsubsection.png)  \
`\subsubsection{}` \
![Headers](assets/img/paragraph.png)
`\paragraph{}`  

To remove the numbers from a header use an asterisk (`\section*{}`) this
will also remove it from the contents page.

---

## Text Sizes


![tiny](assets/img/tiny.png)
`\tiny{}`

![scriptsize](assets/img/scriptsize.png)
`\scriptsize{}` 

![footnotesize](assets/img/footnote.png)
`\footnotesize{}`    

![small](assets/img/small.png)
`\small{}`

![normal](assets/img/normal.png)
`\normalsize{}`

![large1](assets/img/large.png)
`\large{}`

![large2](assets/img/large1.png)
`\Large{}`

![large3](assets/img/large2.png)
`\LARGE{}`

![huge1](assets/img/huge1.png)
`\huge{}`

![huge2](assets/img/huge2.png)
`\Huge{}`

---

## Text Styles

**Bold**  `\textbf{}`

*Italic* `\textit{}`

<u>Underline</u> `\underline{}`

![slanted](assets/img/slanted.png)  `\textsl{}` (Not the same as italic)

![smallcaps](assets/img/smallcaps.png) `\textsc{}`

Medium `\mdseries{}` (Similar to normal and useful for headers)

---

## Colours
**Remember to use the American spelling!** \
``\usepackage[dvipsnames]{xcolor}`` \
``\definecolor{MyFavouriteColour}{RGB}{252,252,37}``

When you want to use this colour just call it using `\color{}`, for
whole sections you can call this before the `\include` statement e.g. \

`\color{MyFavouriteColour}` \
`\include{Page.tex}`

This package also has a number of predefined colours like black, pink
and green which don't need defined just called.
`\color{pink}`

---

## Headers and Footers
To change the header or footer of your document
you first need `\usepackage{fancyhdr}`\
Then you make the page style 'fancy' and remove the default header and
footers:\
`\pagestyle{fancy}`\
`\fancypagestyle{plain}{}`\
`\fancyhf{}` \
From here you can make the header and footer whatever you
want (l= left, c= centre, r= right)\
`\fancyfoot[l]{blah}`\
`\fancyfoot[c]{Page \thepage}`\
`\fancyfoot[r]{\today}` `\lhead{blah}`\
`\chead{Page \thepage}`\
`\rhead{\today}` \

`\thepage` gets the current page number and `\today`
gets the current date.

---

## Acronyms  
### <u>Defining</u>
`\usepackage{acronym}`\
`\acrodef{OS}{Operating System}`

### <u>Using in text</u>
`\ac{OS}`\
First use: Operating System (OS)\
Other uses: OS 

`\acf{OS}`\
Every use: Operating System (OS)

`\acl{OS}`\
Every use: Operating System

### <u>Including Files</u>
**Use separate .tex files for every section!!**

It makes it easier for you to find things rather than having to go
through one massive file and just looks so much neater if you're using
overleaf. It is also very easy to do just create your file in the same
folder as your main and use this command: `\include{name.tex}`

---

## Line Spacing

**New line**
`\\` or `\smallskip` or `\newline` 

**New paragraph**
`\medbreak`

**New page**
`\newpage`

---

## Columns
`\usepackage{multicols}` \
`\begin{multicols}{number}` \
` Stuff you want in multiple columns ` \
`\end{multicols}`

---

## Table of Contents

**Basic table of contents**: `\tableofcontents`\
**Setting the depth of headers**: `\setcounter{tocdepth}{2}` (1= Shows
sections only, 2= Sections and Subsections etc)

**Standard table of contents**
![fulltoc](assets/img/fullnumbers.png)

**Table of contents depth one**
![tocdepth1](assets/img/halfnumbers.png)

If you have chosen to remove the section numbers from your headers you
can still include them in the table of contents by writing the following
line under the corresponding header:
`\addcontentsline{toc}{subsubsection}{Header name}`

**Un-numbered sections** 
![image](assets/img/numberless.png)

---

## assets/img  
**This uses the** *graphicx* **or** *graphics* **packages.**

### <u>Changing image size</u>
This can be done using scale or giving exact width and height
measurements.\
`\includegraphics[scale=1.5]{image.png}`\
`\includegraphics[scale=1.5, angle=45]{image.png}`\
`\includegraphics[width=10cm]{image.png}`\
`\includegraphics[width=10cm, height=5cm]{image.png}`

### <u>Fixing image location</u>
`\begin{figure}[x]`\
**h** : Place image roughly in same order as it appears in source
(sometimes LaTeX decides no and puts it somewhere else)\
**t** : Place at top of page\
**b** : Place at bottom of page\
**p** : Puts on separate page for assets/img only\
**!** : Overrides what LaTeX thinks is right e.g. \[h!\] places it where you specify exactly\
**H** : Same as \[h!\] but requires the float package and I find is more precise.

### <u>Captions and labels</u>
`\caption{caption text}`\
Captions label imagesand automatically increment figure number so you don't have to. To make sure you always reference the correct figure use labels, in the figure tags include the line
`\label{fig:short snappy name}`. \
Then you can call in inline using
`\pageref{fig:short snappy name}` and if you add/delete images it will
update the figure number accordingly.

### <u>Example</u>
`\usepackage{graphicx}` \
`\usepackage{float}` \

`\begin{figure}[H]` \
`\centering` \
`\includegraphics[size parameters]{path\imageName.png}` \
`\caption{Hello I am a caption}` \
`\end{figure}`

---

## Tables  
For tables you have three options:

1.  Use the Google Sheets LaTeX plugin or other converter

2.  Use an image of your table instead

3.  Do it by hand and want to die

The first method is *highly* recommended and some aesthetic adjustments
can easily be made to add borders and text styles.

### <u>Adding borders</u> 

**Vertical borders**:`|` before and after each column where a border is
required
**Horizontal borders**: `\hline`. Must have a `\\` directly before it. \
(If you want to make a horizontal line in your document outside of
tables you can use `\noindent\hrulefill`)

### <u>Text alignment</u>
`\begin{tabular}{x}` \
**c** = centre\
**r** = right\
**l** = left\
**p{xcm}** = top\
**b{xcm}** = bottom\
**m{xcm}** = middle

For p, b and m a value in centimetres must also be provided.

### <u>Merging cells</u>

**Columns** \
`\multicolumn{number of columns}{alignment type}{column text}`  \

**Rows** \
`\usepackage{multirow}` **must be included first before this can be used.**
`\multirow{number of rows}{width of row}{row text}` For the row width `*`
can be used to just merge the rows to the size of the others.\

### <u>Example</u>
![table](assets/img/table.png) 

`\begin{tabular}{|c|c|c|}` \
`\hline` \
`\multicolumn{2}{|c|}{\textbf{Multi column}} & \textbf{Single column} \\` \
`\hline` \
`123 & This is a row & \multirow{3}{*}{Multi row}\\` \
`234 & This is another row &\\` \
`345 & And another one &\\` \
`\hline` \
`\end{tabular}` 

---

## Including Code

### <u>Code Blocks</u> 

`\usepackage{minted} ` \
`\begin{minted}`
`[options]{language}`
            
`#code`

`\end{minted}`

### <u>Inline Code</u>
`\mint{language}| code |` \
**Pros** = Lots of pretty colours \
**Cons** = Creates blank space on top and bottom of it

`\verb+ code +` \
**Pros** = Can be put in the middle of a sentence \
**Cons** = No pretty colours :(

### <u>Some Options</u>
`linenos`: Numbers the lines.\
`breaklines`: Cuts up long lines so that they don't go over the page
width.\
`frame= x`: Adds a border around the code snippet, x can be lines,
leftline, topline, bottomline and single.\
`framesep= xmm`: Padding around border.\
`bgcolor= colourName`: Changes background colour\
`showspaces`: Makes spaces visible\
`rulecolor= colorName`: Changes the border colour.

### <u>Changing colour scheme</u>
`\usemintedstyle{styleName}`\
There are a number of different options but here are three of my
favourite ones:

**rrt**  \
![rrt](assets/img/rrt.png)

**perldoc** \
![perldoc](assets/img/perldoc.png)

**friendly** \
![friendly](assets/img/friendly.png)


### <u>Listings</u>
Similar to captions on images but can also create a table
of listings which gives the location of all of the code snippets in the
document. Underneath your code snippet place the following:

`\begin{listing}[H]` \
`\caption{Hello}` \
`\label{listing:number}` \
`\end{listing}`

To create a table of listings use this command: \
`\renewcommand\listoflistingscaption{Title here}` \
`\listoflistings`
