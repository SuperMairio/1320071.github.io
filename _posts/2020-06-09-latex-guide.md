---
layout: post
title:  Simple Guide to Basic LaTeX
subtitle: For beginners and me, when I forget all the syntax after months of not touching Overleaf
date:   2020-06-09 16:04:51 +0100
tags: [Coding, LaTeX]
---

---


## Headers

![Headers](/assets/img/section.png)<br/>
`\section{}`<br/>
![Headers](/assets/img/subsection.png)<br/>
`\subsection{}`<br/>
![Headers](/assets/img/subsubsection.png)<br/>
`\subsubsection{}`<br/>
![Headers](/assets/img/paragraph.png) <br/>
`\paragraph{}`  

To remove the numbers from a header use an asterisk (`\section*{}`) this
will also remove it from the contents page.

---

## Text Sizes


![tiny](/assets/img/tiny.png)
`\tiny{}`

![scriptsize](/assets/img/scriptsize.png)
`\scriptsize{}` 

![footnotesize](/assets/img/footnote.png)
`\footnotesize{}`    

![small](/assets/img/small.png)
`\small{}`

![normal](/assets/img/normal.png)
`\normalsize{}`

![large1](/assets/img/large.png)
`\large{}`

![large2](/assets/img/large1.png)
`\Large{}`

![large3](/assets/img/large2.png)
`\LARGE{}`

![huge1](/assets/img/huge1.png)
`\huge{}`

![huge2](/assets/img/huge2.png)
`\Huge{}`



---

## Text Styles


**Bold**  `\textbf{}`

*Italic* `\textit{}`

<u>Underline</u> `\underline{}`

![slanted](/assets/img/slanted.png)  `\textsl{}` (Not the same as italic)

![smallcaps](/assets/img/smallcaps.png) `\textsc{}`

Medium `\mdseries{}` (Similar to normal and useful for headers)



---

## Colours


**Remember to use the American spelling!**<br/>
``\usepackage[dvipsnames]{xcolor}``<br/>
``\definecolor{MyFavouriteColour}{RGB}{252,252,37}``

When you want to use this colour just call it using `\color{}`, for
whole sections you can call this before the `\include` statement e.g.<br/>

`\color{MyFavouriteColour}`<br/>
`\include{Page.tex}`

This package also has a number of predefined colours like black, pink
and green which don't need defined just called.
`\color{pink}`



---

## Headers and Footers


To change the header or footer of your document
you first need `\usepackage{fancyhdr}`<br/>
Then you make the page style 'fancy' and remove the default header and
footers:<br/>
`\pagestyle{fancy}`<br/>
`\fancypagestyle{plain}{}`<br/>
`\fancyhf{}`<br/>
From here you can make the header and footer whatever you
want (l= left, c= centre, r= right)<br/>
`\fancyfoot[l]{blah}`<br/>
`\fancyfoot[c]{\thepage}`<br/>
`\fancyfoot[r]{\today}` `\lhead{blah}`<br/>
`\chead{Page\thepage}`<br/>
`\rhead{\today}`<br/>

`\thepage` gets the current page number and `\today`
gets the current date.



---

## Acronyms  


### <u>Defining</u>
`\usepackage{acronym}`<br/>
`\acrodef{OS}{Operating System}`

### <u>Using in text</u>
`\ac{OS}`<br/>
First use: Operating System (OS)<br/>
Other uses: OS 

`\acf{OS}`<br/>
Every use: Operating System (OS)

`\acl{OS}`<br/>
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
<<<<<<< HEAD


`\usepackage{multicols}`

`\begin{multicols}{number}`

`Stuff you want in multiple columns`

=======
`\usepackage{multicols}`<br/>
`\begin{multicols}{number}`<br/>
` Stuff you want in multiple columns`<br/>
>>>>>>> parent of 34f85f9... Minor fixes and added toc images
`\end{multicols}`



---

## Table of Contents


**Basic table of contents** <br/>
`\tableofcontents`<br/>
**Setting the depth of headers**: `\setcounter{tocdepth}{2}` (1= Shows
sections only, 2= Sections and Subsections etc)

**Standard table of contents** <br/>
![fulltoc](/assets/img/fullnumbers.png)

**Table of contents depth one** <br/>
![tocdepth1](/assets/img/halfnumbers.png)

If you have chosen to remove the section numbers from your headers you
can still include them in the table of contents by writing the following
line under the corresponding header:
`\addcontentsline{toc}{subsubsection}{Header name}`

**Un-numbered sections**  <br/>
![image](/assets/img/numberless.png)



---

## Images


**This uses the** *graphicx* **or** *graphics* **packages.**

### <u>Changing image size</u>
This can be done using scale or giving exact width and height
measurements.<br/>
`\includegraphics[scale=1.5]{image.png}`<br/>
`\includegraphics[scale=1.5, angle=45]{image.png}`<br/>
`\includegraphics[width=10cm]{image.png}`<br/>
`\includegraphics[width=10cm, height=5cm]{image.png}`

### <u>Fixing image location</u>
`\begin{figure}[x]`<br/>
**h** : Place image roughly in same order as it appears in source
(sometimes LaTeX decides no and puts it somewhere else)<br/>
**t** : Place at top of page<br/>
**b** : Place at bottom of page<br/>
**p** : Puts on separate page for /assets/img only<br/>
**!** : Overrides what LaTeX thinks is right e.g. \[h!\] places it where you specify exactly<br/>
**H** : Same as \[h!\] but requires the float package and I find is more precise.

### <u>Captions and labels</u>
`\caption{caption text}`<br/>
Captions label imagesand automatically increment figure number so you don't have to. To make sure you always reference the correct figure use labels, in the figure tags include the line
`\label{fig:short snappy name}`.<br/>
Then you can call in inline using
`\pageref{fig:short snappy name}` and if you add/delete images it will
update the figure number accordingly.

### <u>Example</u>
`\usepackage{graphicx}`<br/>
`\usepackage{float}`<br/>

`\begin{figure}[H]`<br/>
`\centering`<br/>
`\includegraphics[size parameters]{path\imageName.png}`<br/>
`\caption{Hello I am a caption}`<br/>
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
**Horizontal borders**: `\hline`. Must have a `\\` directly before it.<br/>
(If you want to make a horizontal line in your document outside of
tables you can use `\noindent\hrulefill`)

### <u>Text alignment</u>
`\begin{tabular}{x}`<br/>
**c** = centre<br/>
**r** = right<br/>
**l** = left<br/>
**p{xcm}** = top<br/>
**b{xcm}** = bottom<br/>
**m{xcm}** = middle

For p, b and m a value in centimetres must also be provided.

### <u>Merging cells</u>

**Columns**<br/>
`\multicolumn{number of columns}{alignment type}{column text}`<br/>

**Rows**<br/>
`\usepackage{multirow}` **must be included first before this can be used.**
`\multirow{number of rows}{width of row}{row text}` 
<br/>For the row width `*` can be used to just merge the rows to the size of the others.

### <u>Example</u>
![table](/assets/img/table.png) 

`\begin{tabular}{|c|c|c|}`<br/>
`\hline`<br/>
`\multicolumn{2}{|c|}{\textbf{Multi column}} & \textbf{Single column} \\`<br/>
`\hline`<br/>
`123 & This is a row & \multirow{3}{*}{Multi row}\\`<br/>
`234 & This is another row &\\`<br/>
`345 & And another one &\\`<br/>
`\hline`<br/>
`\end{tabular}` 



---

## Including Code


### <u>Code Blocks</u> 

`\usepackage{minted} `<br/>
`\begin{minted}`
`[options]{language}`
            
`#code`

`\end{minted}`

### <u>Inline Code</u>
`\mint{language}| code |`<br/>
**Pros** = Lots of pretty colours<br/>
**Cons** = Creates blank space on top and bottom of it

`\verb+ code +`<br/>
**Pros** = Can be put in the middle of a sentence<br/>
**Cons** = No pretty colours :(

### <u>Some Options</u>
`linenos`: Numbers the lines.<br/>
`breaklines`: Cuts up long lines so that they don't go over the page
width.<br/>
`frame= x`: Adds a border around the code snippet, x can be lines,
leftline, topline, bottomline and single.<br/>
`framesep= xmm`: Padding around border.<br/>
`bgcolor= colourName`: Changes background colour<br/>
`showspaces`: Makes spaces visible<br/>
`rulecolor= colorName`: Changes the border colour.

### <u>Changing colour scheme</u>
`\usemintedstyle{styleName}`<br/>
There are a number of different options but here are three of my
favourite ones:

**rrt**<br/>
![rrt](/assets/img/rrt.png)

**perldoc**<br/>
![perldoc](/assets/img/perldoc.png)

**friendly**<br/>
![friendly](/assets/img/friendly.png)


### <u>Listings</u>
Similar to captions on images but can also create a table
of listings which gives the location of all of the code snippets in the
document. Underneath your code snippet place the following:

`\begin{listing}[H]`<br/>
`\caption{Hello}`<br/>
`\label{listing:number}`<br/>
`\end{listing}`

To create a table of listings use this command:<br/>
`\renewcommand\listoflistingscaption{Title here}`<br/>
`\listoflistings`
