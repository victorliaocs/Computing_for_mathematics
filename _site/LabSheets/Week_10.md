# Week 10 - LaTeX

Mathematicians, Computer Scientists, Physicists and others all need to present their research and this is usually through the written medium. Common word processors can be used for this but most prefer to use the typesetting language LaTeX (pronounced Lay-tech).

A typesetting language is a language that requires the user to write code that is then 'translated' to a form that is nice to read\text{ as shown in Figure \ref{W10-img01}}.

![\text{Typesetting languages}\ref{W10-img01}]({{site.baseurl}}/assets/Images/W10-img01.png)

A YouTube playlist with all the videos for this lab sheet can be found [here](http://www.youtube.com/playlist?list=PLnC5h3PY-znygZ2rYNaX7_8j2Duwh58cK).

1. **TICKABLE**  Open up TeXworks which should open a blank document. Write the following LaTeX code:

    {% highlight latex %}
    \documentclass{article}

    \begin{document}
    Hello, world!
    \end{document}
    {% endhighlight %}

    1. Save this document.
    2. Ensure the dropdown window has "pdfLaTeX" selected\text{ as shown in Figure \ref{W10-S01}}.
    3. Click on the green arrow (ctrl+T) to _compile_ this document which creates a pdf corresponding to your code.

    ![\text{The editor window}\label{W10-S01}](./Screenshots/W10-S01.png)

    **This is the most basic of LaTeX documents, everything else you do using LaTeX will be done through writing code in your TeX file.**

    There exists some good cloud based solutions to LaTeX. The advantages of these are usually:

    1. No local install of LaTeX needed;
    2. Often possible to have multiple authors collaborating on a document **at the same time**;
    3. Your files are always available to you.

    The main disadvantage is that you need an internet collection to use it. A good such site is [www.writelatex.org](writelatex.org). Feel free to either use TeXworks or writelatex throughout your learning of LaTeX.

    [Video hint](http://youtu.be/4B8Cmm9scmU)

2. **TICKABLE** The following keys are used to type text in a source file:

    {% highlight latex %}
    a-z A-Z 0-9
    + = * / ( ) [ ]
    {% endhighlight %}

    The following punctuation marks:

    {% highlight latex %}
    ' ? ! : ` ' -
    {% endhighlight %}

    Finally there are 13 special keys that are used in commands:

    {% highlight latex %}
    # $ % & ~ _ ^ \ { } @ " |
    {% endhighlight %}

    For example, `%` sign is used to denote comments in LaTeX (like `#` in Python or Sage). Modify your python script so that it looks like the following and compile it:


    {% highlight latex %}
    \documentclass{article} % There are various classes of documents, we will see a few later.

    \begin{document} % This line start the document
    Hello, world!
    \end{document}
    {% endhighlight %}

    [Video hint](http://youtu.be/xMujHplqFx0)

3. **TICKABLE** In general all the code that comes before the `\begin{document}` statement is called the 'preamble' and is used to set a title for the document, call certain packages as well as various other things. The following code (to be inserted in the preamble of your document) sets a title:


    {% highlight latex %}
    \title{Choose a title}
    \author{V Knight}
    \date{\today}
    {% endhighlight %}


    If you compile your document this won't include the title in the output. To do so you need to include the following line (in the main body):

    {% highlight latex %}
    \maketitle
    {% endhighlight %}

    [Video hint](http://youtu.be/bSJbxAWM5A8)

4. **TICKABLE** The following will add an abstract to your document:

    {% highlight latex %}
    \begin{abstract}
    This document contains some basic LaTeX code that will be useful to me in the future.
    \end{abstract}
    {% endhighlight %}

    [Video hint](http://youtu.be/d9WZFOSjIPA)

5. **TICKABLE** There are various ways to obtain lists:

    {% highlight latex %}
    \begin{itemize}
        \item Unorderd item number 1
        \item Unorderd item number 2
    \end{itemize}

    \begin{enumerate}
        \item Ordered item number 1
        \item Ordered item number 2
    \end{enumerate}
    {% endhighlight %}

    Note that in LaTeX indentation is not required it is just good practice. Unlike Python where specific environments are delimited by indentation levels, in LaTeX they are ended by specific end statements `\end{enumerate}`.

    [Video hint](http://youtu.be/AMisCNGM2G8)

6. **TICKABLE** The following code creates a simple table (note the `c`, `r`, and `l` tags that indicate text alignment, experiment by changing these):

    {% highlight latex %}
    \begin{tabular}{|l|c|r|}
        \hline
        Name & Gender & Start Time\\
        \hline
        Angelico & Male & 1100\\
        \hline
        Leanne & Female & 0830\\
        \hline
        Lisa & Female & 0730\\
        \hline
    \end{tabular}
    {% endhighlight %}

    In general in LaTeX `\\` is used to denote a 'new line'.

    [Video hint](http://youtu.be/OAgTXe5ShSI)

7. **TICKABLE** To include a picture is straightforward in LaTeX. We make use of the `graphicx` package. In LaTeX packages are included in the preamble using `usepackage`. Include the following in the preamble:

    {% highlight latex %}
    \usepackage{graphicx}
    {% endhighlight %}

    The following code (somewhere in the body) will include a picture:

    {% highlight latex %}
    \includegraphics{path_to_picture}
    {% endhighlight %}

    We can put this in the `center` environment to centre the picture:

    {% highlight latex %}
    \begin{center}
        \includegraphics{path_to_picture}
    \end{center}
    {% endhighlight %}

    (Images can be in jpg, png and pdf format when using the pdflatex compiler.)

    [Video hint](http://youtu.be/260odGNvPEc)


8. **TICKABLE** Graphs, pictures and diagrams can thus be created in any software of choice (Sage, inkscape, google drive etc...) and then included as required **but** it is often easier to draw a picture in LaTeX itself using code. A great package to do this with is `tikz`. Include the following in the preamble:

    {% highlight latex %}
    \usepackage{tikz}
    {% endhighlight %}

    Using this package we start a picture by setting up a tikzpicture environment.

    {% highlight latex %}
    \begin{tikzpicture}

    \end{tikzpicture}
    {% endhighlight %}

    We then draw various shapes and connectors using the `\draw` command including coordinates:

    {% highlight latex %}
    \begin{tikzpicture}
        \draw (0,0) -- (0,2); % This draws a line from (0,0) to (0,2)
        \draw (-1,1) -- (1,1); % This draws a line from (-1,1) to (1,1)
        \draw (0,0) -- (1,-1); % This draws a line from (0,0) to (1,-1)
        \draw (0,0) -- (-1,-1); % This draws a line from (0,0) to (-1,-1)
        \draw (0,2.5) circle(.5); % This draws a circle at (0,2.5) with radius .5
    \end{tikzpicture}
    {% endhighlight %}

    This is very much touching the surface of what can be down with tikz. The simplest next step is to include various color and thickness options:

    {% highlight latex %}
    \begin{tikzpicture}
        \draw [ultra thick] (0,0) -- (0,2); % This draws a line from (0,0) to (0,2)
        \draw [thin, color=blue] (-1,1) -- (1,1); % This draws a line from (-1,1) to (1,1)
        \draw [thick] (0,0) -- (1,-1); % This draws a line from (0,0) to (1,-1)
        \draw [thick] (0,0) -- (-1,-1); % This draws a line from (0,0) to (-1,-1)
        \draw [color=red, fill=green] (0,2.5) circle(.5); % This draws a circle at (0,2.5) with radius .5
    \end{tikzpicture}
    {% endhighlight %}

    A lot more can be done with tikz and there are a variety of great examples, tutorials online.

    [Video hint](http://youtu.be/fPpATcx-fVc)

9. **TICKABLE** It is possible to organise parts of a document using 'sections':

    {% highlight latex %}
    \section{My first section}

    This is a section with a few subsections.

    \subsection{A part of my first section}

    Here I could write about the problem I'm trying to solve.

    \subsection{Another part of my first section}

    In this subsection I could solve the problem.

    \subsubsection{Further fragmentation...}

    \section{My second section}

    etc...
    {% endhighlight %}

    We can include labels to sections so that we can refer to them:

    {% highlight latex %}
    \section{My first section}\label{first_section}

    \section{My second section}\label{second_section}

    In Section \ref{first_section} we saw that...
    {% endhighlight %}

    When compiling one needs to compile twice:

    1. The first time to find all the labels;
    2. The second time to match the labels to the references.

    If you are using writelatex then this happens automatically.

    Note, labels can be using in conjunction with `tabular` (for tables) and `figure` (for images) environments.

    [Video hint](http://youtu.be/E2xT0xNk8EU)

10. **TICKABLE** To create a bibliography we need to store the bibliographic information in a separate 'bibtex' file. In this file you include bibliographic information for the various references you might have.

    The following is the code for a book on LaTeX. Save the following in a separate file: `bibliography.bib`:

    {% highlight latex %}
    @book{Gratzer2007,
    author = {Gr\"{a}tzer, George},
    publisher = {Springer},
    title = {{More Math Into LaTeX: A Guide for
    Documentation and Presentation}},
    year = {2007}
    }
    {% endhighlight %}

    We can then reference the 'key' (for the above it is Gratzer2007) for any document in the bibliography file using the following:

    {% highlight latex %}
    A very helpful reference for LaTeX is \cite{Gratzer2007}.
    {% endhighlight %}

    Note that there are a variety of tools that will give you bibtex code for any given reference (Google Scholar, Zotero, Mendeley etc...).

    We need to however include a pointer towards the bibliography, at the end of the document include:

    {% highlight latex %}
    \bibliographystyle{plain}
    \bibliography{bibliography.bib}
    {% endhighlight %}

    We now need to compile a document twice (as above to find all internal references for sections, figure etc...) **and then** we compile the bibliography with `bibtex` and then we need to compile one last time to match the bibliography items with the citations\text{ as shown in Figure \ref{W10-img02}}.

    ![\text{The compilation process}\label{W10-img02}]({{site.baseurl}}/assets/Images/W10-img02.png)

    If you are using writelatex then this happens automatically.

    [Video hint](http://youtu.be/X-9T2Oaj-5A)

11. **TICKABLE** Typesetting mathematics is LaTeX's strength. Add the following to your document:

    {% highlight latex %}
    Mathematics can be typed in to \LaTeX\ as $x^2$ and/or \((a+b)^2=a^2+2ab+b^2\).
    {% endhighlight %}

    [Video hint](http://youtu.be/ef2p-rVJ2Vk)

12. **TICKABLE** The previous code showed how to include mathematics in text (_inline). We can also include mathematics in display mode. Add the following to your document:

    $$\sum_{i=1}^{n}i=\frac{n(n+1)}{2}$$

    [Video hint](http://youtu.be/cHuDdblKmjs)

13. **TICKABLE** Mathematics can also be included in equations and referred to as for sections, pictures etc:

    {% highlight latex %}
    \begin{equation}\label{my_first_equation}
    e=mc^2
    \end{equation}

    In equation (\ref{my_first_equation}) we have a very well known relationship!
    {% endhighlight %}

    [Video hint](http://youtu.be/_ZH0jwscSwk)

14. **TICKABLE** To include text within mathematics we can use the `text` command from the `amsmath` package:

    {% highlight latex %}
    $$x^2 = 1 \text{ implies} x=\pm1$$
    {% endhighlight %}

    (be sure to include `usepackage{amsmath}` in the preamble.)

    Another command that does this is `mbox` which does not require the amsmath package.

    [Video hint](http://youtu.be/408OEiq3ybU)

15. **TICKABLE** Arithmetic operators are quite simple in LaTeX. Try the following:

    {% highlight latex %}
    \begin{itemize}
        \item $a+b$
        \item $a-b$
        \item $-a$
        \item $ab$
        \item $a\cdot b$
        \item $a\times b$
        \item $a/b$
        \item ${a\over b}$
        \item $\frac{a}{b}$
    \end{itemize}
    {% endhighlight %}

    [Video hint](http://youtu.be/DiDe88f8jN0)

16. **TICKABLE** Experiment with the following to see how to obtain integrals in LaTeX:

    {% highlight latex %}
    $$\int_{0}^{\pi}x^2\,dx$$
    {% endhighlight %}

    [Video hint](http://youtu.be/Aezyj0OhDVM)

17. **TICKABLE** The following code gives a 3 by 2 matrix:

    {% highlight latex %}
    $$\begin{pmatrix}
    a&b\\
    c&d\\
    e&f\\
    \end{pmatrix}$$
    {% endhighlight %}

    Experiment with `\begin{matrix}` and `\begin{vmatrix}`.

    [Video hint](http://youtu.be/JDsirwrf1Bg)

18. **TICKABLE** It is possible to create aligned mathematics using:

    {% highlight latex %}
    \begin{align}
        (x+h)^2-x^2 & =x^2+2xh+h^2-x^2 \nonumber\\
                    & =2xh+h^2 \nonumber\\
                    & =h(2x+h) \nonumber
    \end{align}
    {% endhighlight %}

    Annotated text can also be added:

    {% highlight latex %}
    \begin{align}
        (x+h)^2-x^2 & = x^2+2xh+h^2-x^2 && \text{(by distributivity)}\\
                    & = 2xh+h^2         && \text{(by subtraction)}\\
                    & = h(2x+h)         && \text{(by factorisation)}
    \end{align}
    {% endhighlight %}

    [Video hint](http://youtu.be/AzFOqb9WKX4)

19. **TICKABLE** Finally we can create partitioned statements:

    {% highlight latex %}
    $$
    1+(-1)^n=\begin{cases}
                0, & \text{if $n$ odd}\\
                2, & \text{if $n$ even}
                \end{cases}
    $$
    {% endhighlight %}

    [Video hint](http://youtu.be/if7P-w6hHmw)

20. **TICKABLE** It is possible to create high quality presentation in LaTeX. To do this we use the `beamer` document class:

    {% highlight latex %}
    \documentclass{beamer}
    \begin{document}

    \frame{This is my first slide.}

    \frame{This is my second slide.}

    \end{document}
    {% endhighlight %}

    Try one of the following themes in the preamble of your document to change the look of your slides.

    {% highlight latex %}
    \usetheme{default}
    \usetheme{Boadilla}
    \usetheme{Madrid}
    \usetheme{Montpellier}
    \usetheme{Warsaw}
    \usetheme{Copenhagen}
    \usetheme{Goettingen}
    \usetheme{Hannover}
    \usetheme{Berkeley}
    {% endhighlight %}

    [Video hint](http://youtu.be/XrZRVGnFXw0)

21. **TICKABLE** Most of the LaTeX code you have learnt so far an be used without much change in a beamer presentation within the `frame` environment. There are however a few particularities:

    To make a title, you need to use the `\titlepage` instead of the `\maketitle` command:

    {% highlight latex %}
    \begin{frame}
        \titlepage
    \end{frame}
    {% endhighlight %}

    We can also have frame titles and sections as before in a Beamer document:

    {% highlight latex %}
    \frame{\frametitle{Overview}
        \tableofcontents
    }

    \section{Simple Beamer}
    \begin{frame}
        \frametitle{My first slide}
    \end{frame}
    {% endhighlight %}

    There are various other commands and tools that can be used in Beamer. In particular take a look at the `pause`, `only` and `onslide` commands.

    [Video hint](http://youtu.be/L3KGl2vn_iA)