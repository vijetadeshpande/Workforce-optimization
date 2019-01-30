# Workforce optimization for emergency care

 Default to the notebook output style

    


% Inherit from the specified cell style.




    
\documentclass[11pt]{article}

    
    
    \usepackage[T1]{fontenc}
    % Nicer default font (+ math font) than Computer Modern for most use cases
    \usepackage{mathpazo}

    % Basic figure setup, for now with no caption control since it's done
    % automatically by Pandoc (which extracts ![](path) syntax from Markdown).
    \usepackage{graphicx}
    % We will generate all images so they have a width \maxwidth. This means
    % that they will get their normal width if they fit onto the page, but
    % are scaled down if they would overflow the margins.
    \makeatletter
    \def\maxwidth{\ifdim\Gin@nat@width>\linewidth\linewidth
    \else\Gin@nat@width\fi}
    \makeatother
    \let\Oldincludegraphics\includegraphics
    % Set max figure width to be 80% of text width, for now hardcoded.
    \renewcommand{\includegraphics}[1]{\Oldincludegraphics[width=.8\maxwidth]{#1}}
    % Ensure that by default, figures have no caption (until we provide a
    % proper Figure object with a Caption API and a way to capture that
    % in the conversion process - todo).
    \usepackage{caption}
    \DeclareCaptionLabelFormat{nolabel}{}
    \captionsetup{labelformat=nolabel}

    \usepackage{adjustbox} % Used to constrain images to a maximum size 
    \usepackage{xcolor} % Allow colors to be defined
    \usepackage{enumerate} % Needed for markdown enumerations to work
    \usepackage{geometry} % Used to adjust the document margins
    \usepackage{amsmath} % Equations
    \usepackage{amssymb} % Equations
    \usepackage{textcomp} % defines textquotesingle
    % Hack from http://tex.stackexchange.com/a/47451/13684:
    \AtBeginDocument{%
        \def\PYZsq{\textquotesingle}% Upright quotes in Pygmentized code
    }
    \usepackage{upquote} % Upright quotes for verbatim code
    \usepackage{eurosym} % defines \euro
    \usepackage[mathletters]{ucs} % Extended unicode (utf-8) support
    \usepackage[utf8x]{inputenc} % Allow utf-8 characters in the tex document
    \usepackage{fancyvrb} % verbatim replacement that allows latex
    \usepackage{grffile} % extends the file name processing of package graphics 
                         % to support a larger range 
    % The hyperref package gives us a pdf with properly built
    % internal navigation ('pdf bookmarks' for the table of contents,
    % internal cross-reference links, web links for URLs, etc.)
    \usepackage{hyperref}
    \usepackage{longtable} % longtable support required by pandoc >1.10
    \usepackage{booktabs}  % table support for pandoc > 1.12.2
    \usepackage[inline]{enumitem} % IRkernel/repr support (it uses the enumerate* environment)
    \usepackage[normalem]{ulem} % ulem is needed to support strikethroughs (\sout)
                                % normalem makes italics be italics, not underlines
    

    
    
    % Colors for the hyperref package
    \definecolor{urlcolor}{rgb}{0,.145,.698}
    \definecolor{linkcolor}{rgb}{.71,0.21,0.01}
    \definecolor{citecolor}{rgb}{.12,.54,.11}

    % ANSI colors
    \definecolor{ansi-black}{HTML}{3E424D}
    \definecolor{ansi-black-intense}{HTML}{282C36}
    \definecolor{ansi-red}{HTML}{E75C58}
    \definecolor{ansi-red-intense}{HTML}{B22B31}
    \definecolor{ansi-green}{HTML}{00A250}
    \definecolor{ansi-green-intense}{HTML}{007427}
    \definecolor{ansi-yellow}{HTML}{DDB62B}
    \definecolor{ansi-yellow-intense}{HTML}{B27D12}
    \definecolor{ansi-blue}{HTML}{208FFB}
    \definecolor{ansi-blue-intense}{HTML}{0065CA}
    \definecolor{ansi-magenta}{HTML}{D160C4}
    \definecolor{ansi-magenta-intense}{HTML}{A03196}
    \definecolor{ansi-cyan}{HTML}{60C6C8}
    \definecolor{ansi-cyan-intense}{HTML}{258F8F}
    \definecolor{ansi-white}{HTML}{C5C1B4}
    \definecolor{ansi-white-intense}{HTML}{A1A6B2}

    % commands and environments needed by pandoc snippets
    % extracted from the output of `pandoc -s`
    \providecommand{\tightlist}{%
      \setlength{\itemsep}{0pt}\setlength{\parskip}{0pt}}
    \DefineVerbatimEnvironment{Highlighting}{Verbatim}{commandchars=\\\{\}}
    % Add ',fontsize=\small' for more characters per line
    \newenvironment{Shaded}{}{}
    \newcommand{\KeywordTok}[1]{\textcolor[rgb]{0.00,0.44,0.13}{\textbf{{#1}}}}
    \newcommand{\DataTypeTok}[1]{\textcolor[rgb]{0.56,0.13,0.00}{{#1}}}
    \newcommand{\DecValTok}[1]{\textcolor[rgb]{0.25,0.63,0.44}{{#1}}}
    \newcommand{\BaseNTok}[1]{\textcolor[rgb]{0.25,0.63,0.44}{{#1}}}
    \newcommand{\FloatTok}[1]{\textcolor[rgb]{0.25,0.63,0.44}{{#1}}}
    \newcommand{\CharTok}[1]{\textcolor[rgb]{0.25,0.44,0.63}{{#1}}}
    \newcommand{\StringTok}[1]{\textcolor[rgb]{0.25,0.44,0.63}{{#1}}}
    \newcommand{\CommentTok}[1]{\textcolor[rgb]{0.38,0.63,0.69}{\textit{{#1}}}}
    \newcommand{\OtherTok}[1]{\textcolor[rgb]{0.00,0.44,0.13}{{#1}}}
    \newcommand{\AlertTok}[1]{\textcolor[rgb]{1.00,0.00,0.00}{\textbf{{#1}}}}
    \newcommand{\FunctionTok}[1]{\textcolor[rgb]{0.02,0.16,0.49}{{#1}}}
    \newcommand{\RegionMarkerTok}[1]{{#1}}
    \newcommand{\ErrorTok}[1]{\textcolor[rgb]{1.00,0.00,0.00}{\textbf{{#1}}}}
    \newcommand{\NormalTok}[1]{{#1}}
    
    % Additional commands for more recent versions of Pandoc
    \newcommand{\ConstantTok}[1]{\textcolor[rgb]{0.53,0.00,0.00}{{#1}}}
    \newcommand{\SpecialCharTok}[1]{\textcolor[rgb]{0.25,0.44,0.63}{{#1}}}
    \newcommand{\VerbatimStringTok}[1]{\textcolor[rgb]{0.25,0.44,0.63}{{#1}}}
    \newcommand{\SpecialStringTok}[1]{\textcolor[rgb]{0.73,0.40,0.53}{{#1}}}
    \newcommand{\ImportTok}[1]{{#1}}
    \newcommand{\DocumentationTok}[1]{\textcolor[rgb]{0.73,0.13,0.13}{\textit{{#1}}}}
    \newcommand{\AnnotationTok}[1]{\textcolor[rgb]{0.38,0.63,0.69}{\textbf{\textit{{#1}}}}}
    \newcommand{\CommentVarTok}[1]{\textcolor[rgb]{0.38,0.63,0.69}{\textbf{\textit{{#1}}}}}
    \newcommand{\VariableTok}[1]{\textcolor[rgb]{0.10,0.09,0.49}{{#1}}}
    \newcommand{\ControlFlowTok}[1]{\textcolor[rgb]{0.00,0.44,0.13}{\textbf{{#1}}}}
    \newcommand{\OperatorTok}[1]{\textcolor[rgb]{0.40,0.40,0.40}{{#1}}}
    \newcommand{\BuiltInTok}[1]{{#1}}
    \newcommand{\ExtensionTok}[1]{{#1}}
    \newcommand{\PreprocessorTok}[1]{\textcolor[rgb]{0.74,0.48,0.00}{{#1}}}
    \newcommand{\AttributeTok}[1]{\textcolor[rgb]{0.49,0.56,0.16}{{#1}}}
    \newcommand{\InformationTok}[1]{\textcolor[rgb]{0.38,0.63,0.69}{\textbf{\textit{{#1}}}}}
    \newcommand{\WarningTok}[1]{\textcolor[rgb]{0.38,0.63,0.69}{\textbf{\textit{{#1}}}}}
    
    
    % Define a nice break command that doesn't care if a line doesn't already
    % exist.
    \def\br{\hspace*{\fill} \\* }
    % Math Jax compatability definitions
    \def\gt{>}
    \def\lt{<}
    % Document parameters
    \title{Optimization of Multistage Logistics Chain Network}
    
    
    

    % Pygments definitions
    
\makeatletter
\def\PY@reset{\let\PY@it=\relax \let\PY@bf=\relax%
    \let\PY@ul=\relax \let\PY@tc=\relax%
    \let\PY@bc=\relax \let\PY@ff=\relax}
\def\PY@tok#1{\csname PY@tok@#1\endcsname}
\def\PY@toks#1+{\ifx\relax#1\empty\else%
    \PY@tok{#1}\expandafter\PY@toks\fi}
\def\PY@do#1{\PY@bc{\PY@tc{\PY@ul{%
    \PY@it{\PY@bf{\PY@ff{#1}}}}}}}
\def\PY#1#2{\PY@reset\PY@toks#1+\relax+\PY@do{#2}}

\expandafter\def\csname PY@tok@gd\endcsname{\def\PY@tc##1{\textcolor[rgb]{0.63,0.00,0.00}{##1}}}
\expandafter\def\csname PY@tok@gu\endcsname{\let\PY@bf=\textbf\def\PY@tc##1{\textcolor[rgb]{0.50,0.00,0.50}{##1}}}
\expandafter\def\csname PY@tok@gt\endcsname{\def\PY@tc##1{\textcolor[rgb]{0.00,0.27,0.87}{##1}}}
\expandafter\def\csname PY@tok@gs\endcsname{\let\PY@bf=\textbf}
\expandafter\def\csname PY@tok@gr\endcsname{\def\PY@tc##1{\textcolor[rgb]{1.00,0.00,0.00}{##1}}}
\expandafter\def\csname PY@tok@cm\endcsname{\let\PY@it=\textit\def\PY@tc##1{\textcolor[rgb]{0.25,0.50,0.50}{##1}}}
\expandafter\def\csname PY@tok@vg\endcsname{\def\PY@tc##1{\textcolor[rgb]{0.10,0.09,0.49}{##1}}}
\expandafter\def\csname PY@tok@vi\endcsname{\def\PY@tc##1{\textcolor[rgb]{0.10,0.09,0.49}{##1}}}
\expandafter\def\csname PY@tok@vm\endcsname{\def\PY@tc##1{\textcolor[rgb]{0.10,0.09,0.49}{##1}}}
\expandafter\def\csname PY@tok@mh\endcsname{\def\PY@tc##1{\textcolor[rgb]{0.40,0.40,0.40}{##1}}}
\expandafter\def\csname PY@tok@cs\endcsname{\let\PY@it=\textit\def\PY@tc##1{\textcolor[rgb]{0.25,0.50,0.50}{##1}}}
\expandafter\def\csname PY@tok@ge\endcsname{\let\PY@it=\textit}
\expandafter\def\csname PY@tok@vc\endcsname{\def\PY@tc##1{\textcolor[rgb]{0.10,0.09,0.49}{##1}}}
\expandafter\def\csname PY@tok@il\endcsname{\def\PY@tc##1{\textcolor[rgb]{0.40,0.40,0.40}{##1}}}
\expandafter\def\csname PY@tok@go\endcsname{\def\PY@tc##1{\textcolor[rgb]{0.53,0.53,0.53}{##1}}}
\expandafter\def\csname PY@tok@cp\endcsname{\def\PY@tc##1{\textcolor[rgb]{0.74,0.48,0.00}{##1}}}
\expandafter\def\csname PY@tok@gi\endcsname{\def\PY@tc##1{\textcolor[rgb]{0.00,0.63,0.00}{##1}}}
\expandafter\def\csname PY@tok@gh\endcsname{\let\PY@bf=\textbf\def\PY@tc##1{\textcolor[rgb]{0.00,0.00,0.50}{##1}}}
\expandafter\def\csname PY@tok@ni\endcsname{\let\PY@bf=\textbf\def\PY@tc##1{\textcolor[rgb]{0.60,0.60,0.60}{##1}}}
\expandafter\def\csname PY@tok@nl\endcsname{\def\PY@tc##1{\textcolor[rgb]{0.63,0.63,0.00}{##1}}}
\expandafter\def\csname PY@tok@nn\endcsname{\let\PY@bf=\textbf\def\PY@tc##1{\textcolor[rgb]{0.00,0.00,1.00}{##1}}}
\expandafter\def\csname PY@tok@no\endcsname{\def\PY@tc##1{\textcolor[rgb]{0.53,0.00,0.00}{##1}}}
\expandafter\def\csname PY@tok@na\endcsname{\def\PY@tc##1{\textcolor[rgb]{0.49,0.56,0.16}{##1}}}
\expandafter\def\csname PY@tok@nb\endcsname{\def\PY@tc##1{\textcolor[rgb]{0.00,0.50,0.00}{##1}}}
\expandafter\def\csname PY@tok@nc\endcsname{\let\PY@bf=\textbf\def\PY@tc##1{\textcolor[rgb]{0.00,0.00,1.00}{##1}}}
\expandafter\def\csname PY@tok@nd\endcsname{\def\PY@tc##1{\textcolor[rgb]{0.67,0.13,1.00}{##1}}}
\expandafter\def\csname PY@tok@ne\endcsname{\let\PY@bf=\textbf\def\PY@tc##1{\textcolor[rgb]{0.82,0.25,0.23}{##1}}}
\expandafter\def\csname PY@tok@nf\endcsname{\def\PY@tc##1{\textcolor[rgb]{0.00,0.00,1.00}{##1}}}
\expandafter\def\csname PY@tok@si\endcsname{\let\PY@bf=\textbf\def\PY@tc##1{\textcolor[rgb]{0.73,0.40,0.53}{##1}}}
\expandafter\def\csname PY@tok@s2\endcsname{\def\PY@tc##1{\textcolor[rgb]{0.73,0.13,0.13}{##1}}}
\expandafter\def\csname PY@tok@nt\endcsname{\let\PY@bf=\textbf\def\PY@tc##1{\textcolor[rgb]{0.00,0.50,0.00}{##1}}}
\expandafter\def\csname PY@tok@nv\endcsname{\def\PY@tc##1{\textcolor[rgb]{0.10,0.09,0.49}{##1}}}
\expandafter\def\csname PY@tok@s1\endcsname{\def\PY@tc##1{\textcolor[rgb]{0.73,0.13,0.13}{##1}}}
\expandafter\def\csname PY@tok@dl\endcsname{\def\PY@tc##1{\textcolor[rgb]{0.73,0.13,0.13}{##1}}}
\expandafter\def\csname PY@tok@ch\endcsname{\let\PY@it=\textit\def\PY@tc##1{\textcolor[rgb]{0.25,0.50,0.50}{##1}}}
\expandafter\def\csname PY@tok@m\endcsname{\def\PY@tc##1{\textcolor[rgb]{0.40,0.40,0.40}{##1}}}
\expandafter\def\csname PY@tok@gp\endcsname{\let\PY@bf=\textbf\def\PY@tc##1{\textcolor[rgb]{0.00,0.00,0.50}{##1}}}
\expandafter\def\csname PY@tok@sh\endcsname{\def\PY@tc##1{\textcolor[rgb]{0.73,0.13,0.13}{##1}}}
\expandafter\def\csname PY@tok@ow\endcsname{\let\PY@bf=\textbf\def\PY@tc##1{\textcolor[rgb]{0.67,0.13,1.00}{##1}}}
\expandafter\def\csname PY@tok@sx\endcsname{\def\PY@tc##1{\textcolor[rgb]{0.00,0.50,0.00}{##1}}}
\expandafter\def\csname PY@tok@bp\endcsname{\def\PY@tc##1{\textcolor[rgb]{0.00,0.50,0.00}{##1}}}
\expandafter\def\csname PY@tok@c1\endcsname{\let\PY@it=\textit\def\PY@tc##1{\textcolor[rgb]{0.25,0.50,0.50}{##1}}}
\expandafter\def\csname PY@tok@fm\endcsname{\def\PY@tc##1{\textcolor[rgb]{0.00,0.00,1.00}{##1}}}
\expandafter\def\csname PY@tok@o\endcsname{\def\PY@tc##1{\textcolor[rgb]{0.40,0.40,0.40}{##1}}}
\expandafter\def\csname PY@tok@kc\endcsname{\let\PY@bf=\textbf\def\PY@tc##1{\textcolor[rgb]{0.00,0.50,0.00}{##1}}}
\expandafter\def\csname PY@tok@c\endcsname{\let\PY@it=\textit\def\PY@tc##1{\textcolor[rgb]{0.25,0.50,0.50}{##1}}}
\expandafter\def\csname PY@tok@mf\endcsname{\def\PY@tc##1{\textcolor[rgb]{0.40,0.40,0.40}{##1}}}
\expandafter\def\csname PY@tok@err\endcsname{\def\PY@bc##1{\setlength{\fboxsep}{0pt}\fcolorbox[rgb]{1.00,0.00,0.00}{1,1,1}{\strut ##1}}}
\expandafter\def\csname PY@tok@mb\endcsname{\def\PY@tc##1{\textcolor[rgb]{0.40,0.40,0.40}{##1}}}
\expandafter\def\csname PY@tok@ss\endcsname{\def\PY@tc##1{\textcolor[rgb]{0.10,0.09,0.49}{##1}}}
\expandafter\def\csname PY@tok@sr\endcsname{\def\PY@tc##1{\textcolor[rgb]{0.73,0.40,0.53}{##1}}}
\expandafter\def\csname PY@tok@mo\endcsname{\def\PY@tc##1{\textcolor[rgb]{0.40,0.40,0.40}{##1}}}
\expandafter\def\csname PY@tok@kd\endcsname{\let\PY@bf=\textbf\def\PY@tc##1{\textcolor[rgb]{0.00,0.50,0.00}{##1}}}
\expandafter\def\csname PY@tok@mi\endcsname{\def\PY@tc##1{\textcolor[rgb]{0.40,0.40,0.40}{##1}}}
\expandafter\def\csname PY@tok@kn\endcsname{\let\PY@bf=\textbf\def\PY@tc##1{\textcolor[rgb]{0.00,0.50,0.00}{##1}}}
\expandafter\def\csname PY@tok@cpf\endcsname{\let\PY@it=\textit\def\PY@tc##1{\textcolor[rgb]{0.25,0.50,0.50}{##1}}}
\expandafter\def\csname PY@tok@kr\endcsname{\let\PY@bf=\textbf\def\PY@tc##1{\textcolor[rgb]{0.00,0.50,0.00}{##1}}}
\expandafter\def\csname PY@tok@s\endcsname{\def\PY@tc##1{\textcolor[rgb]{0.73,0.13,0.13}{##1}}}
\expandafter\def\csname PY@tok@kp\endcsname{\def\PY@tc##1{\textcolor[rgb]{0.00,0.50,0.00}{##1}}}
\expandafter\def\csname PY@tok@w\endcsname{\def\PY@tc##1{\textcolor[rgb]{0.73,0.73,0.73}{##1}}}
\expandafter\def\csname PY@tok@kt\endcsname{\def\PY@tc##1{\textcolor[rgb]{0.69,0.00,0.25}{##1}}}
\expandafter\def\csname PY@tok@sc\endcsname{\def\PY@tc##1{\textcolor[rgb]{0.73,0.13,0.13}{##1}}}
\expandafter\def\csname PY@tok@sb\endcsname{\def\PY@tc##1{\textcolor[rgb]{0.73,0.13,0.13}{##1}}}
\expandafter\def\csname PY@tok@sa\endcsname{\def\PY@tc##1{\textcolor[rgb]{0.73,0.13,0.13}{##1}}}
\expandafter\def\csname PY@tok@k\endcsname{\let\PY@bf=\textbf\def\PY@tc##1{\textcolor[rgb]{0.00,0.50,0.00}{##1}}}
\expandafter\def\csname PY@tok@se\endcsname{\let\PY@bf=\textbf\def\PY@tc##1{\textcolor[rgb]{0.73,0.40,0.13}{##1}}}
\expandafter\def\csname PY@tok@sd\endcsname{\let\PY@it=\textit\def\PY@tc##1{\textcolor[rgb]{0.73,0.13,0.13}{##1}}}

\def\PYZbs{\char`\\}
\def\PYZus{\char`\_}
\def\PYZob{\char`\{}
\def\PYZcb{\char`\}}
\def\PYZca{\char`\^}
\def\PYZam{\char`\&}
\def\PYZlt{\char`\<}
\def\PYZgt{\char`\>}
\def\PYZsh{\char`\#}
\def\PYZpc{\char`\%}
\def\PYZdl{\char`\$}
\def\PYZhy{\char`\-}
\def\PYZsq{\char`\'}
\def\PYZdq{\char`\"}
\def\PYZti{\char`\~}
% for compatibility with earlier versions
\def\PYZat{@}
\def\PYZlb{[}
\def\PYZrb{]}
\makeatother


    % Exact colors from NB
    \definecolor{incolor}{rgb}{0.0, 0.0, 0.5}
    \definecolor{outcolor}{rgb}{0.545, 0.0, 0.0}



    
    % Prevent overflowing lines due to hard-to-break entities
    \sloppy 
    % Setup hyperref package
    \hypersetup{
      breaklinks=true,  % so long urls are correctly broken across lines
      colorlinks=true,
      urlcolor=urlcolor,
      linkcolor=linkcolor,
      citecolor=citecolor,
      }
    % Slightly bigger margins than the latex defaults
    
    \geometry{verbose,tmargin=1in,bmargin=1in,lmargin=1in,rmargin=1in}
    
    

    \begin{document}
    
    
    \maketitle
    
    

    
    \section{Optimization of Multistage Logistics Chain
Network:}\label{optimization-of-multistage-logistics-chain-network}

\paragraph{Overview:}\label{overview}

The logistics problem in the process of satifying consumer demand with
the limited supply has many elements to it, e.g. facility location,
optimal distribution etc. Facility location and supply network
optimization do not, in many cases, capture the true essence of real
life logistics problem. Many companies deal with multi-stage logistics
problem where optimizing the production quantity, distribution network
and supply network is required. Here, in this project we are considering
a multi-stage logistics problem which involves optimization of
production quatity, distribution network and supply network. To make
this problem closer to the real life situation we also have capacity
constraints on supply quatity, production quantity and number of
facilities (production plants and distribution centers) to be chosen
from the given set of possible facility locations. Hence, this problem
can viewed as a combination of multiple choice Knapsack and Capacited
location-allocation problem.

The formulated problem has following decision variables, 1. \(x_{i,j}\)
= quantity to be produced at plant 'j' with supply from 'ith' supplier
2. \(y_{j,k}\) = quantity to be sent to distribution center 'k' from the
plant 'j' 3. \(z_{k,l}\) = quantity to be supplied to 'lth' demand point
from the distribution center 'k' 4. \(w_{j}\) = binary variable for
plant 'j' 5. \(z_{k}\) = binary variable for distribution center 'k'

The objective function is conprised of following costs, 1. Cost of
production 2. Cost of distribution 3. Cost of supply 4. Fixed cost for
production plant and distribution center

And the constraints capture the following bounds 1. Supply capacity of
each supplier 2. Production capacity for each plant 3. Storage capacity
of distribution center 4. Demand satisfaction 5. Total number of plants
and distribution center selected in satisfying demand

The 0-1 Mixed Interger Linear formulation for the problem is defined in
the next cell and after that we create and solve a mathematical model
with help Gurobi.

    \subsection{Mathematical Model}\label{mathematical-model}

\begin{equation}
min \quad \sum_{i,j} s_{i,j}x_{i,j} + \sum_{j,k} t_{j,k}y_{j,k} + \sum_{k,l} u_{k,l}z_{k,l} + \sum_{j} f_{j}w_{j} + \sum_{k} g_{k}z_{k}
\end{equation}

such that,

\begin{equation}
\sum_{j} x_{i,j} <= a_{i}, \forall i
\end{equation}

\begin{equation}
\sum_{k} y_{j,k} <= b_{j}w_{j},  \forall j
\end{equation}

\begin{equation}
\sum_{j} w_{j} <= P 
\end{equation}

\begin{equation}
\sum_{l} z_{k,l} <= c_{k}z_{k}, \forall k
\end{equation}

\begin{equation}
\sum_{k} z_{k} <= W
\end{equation}

\begin{equation}
\sum_{k} z_{k,l} >= d_{l}, \forall l
\end{equation}

\(w_{j}, z_{k}\) = {[}0, 1{]}, \(\forall j, k\),
\(x_{i,j}, y_{j,k}, z_{k,l} >= 0\), \(\forall i, j, k, l\)

    \begin{Verbatim}[commandchars=\\\{\}]
{\color{incolor}In [{\color{incolor}1}]:} \PY{c+c1}{\PYZsh{} import libraries}
        \PY{k+kn}{from} \PY{n+nn}{gurobipy} \PY{k+kn}{import} \PY{o}{*}
        \PY{k+kn}{import} \PY{n+nn}{numpy} \PY{k+kn}{as} \PY{n+nn}{np}
        \PY{k+kn}{import} \PY{n+nn}{pandas} \PY{k+kn}{as} \PY{n+nn}{pd}
        \PY{k+kn}{import} \PY{n+nn}{sys}
\end{Verbatim}


    \begin{Verbatim}[commandchars=\\\{\}]
{\color{incolor}In [{\color{incolor}2}]:} \PY{c+c1}{\PYZsh{} defining dictionary for RHS}
        \PY{n}{RHS\PYZus{}m} \PY{o}{=} \PY{p}{\PYZob{}}
            \PY{l+s+s2}{\PYZdq{}}\PY{l+s+s2}{cap\PYZus{}supply}\PY{l+s+s2}{\PYZdq{}}\PY{p}{:} \PY{p}{[}\PY{l+m+mi}{500}\PY{p}{,} \PY{l+m+mi}{650}\PY{p}{,} \PY{l+m+mi}{390}\PY{p}{]}\PY{p}{,}
            \PY{l+s+s2}{\PYZdq{}}\PY{l+s+s2}{cap\PYZus{}plant}\PY{l+s+s2}{\PYZdq{}} \PY{p}{:} \PY{p}{[}\PY{l+m+mi}{400}\PY{p}{,} \PY{l+m+mi}{550}\PY{p}{,} \PY{l+m+mi}{490}\PY{p}{,} \PY{l+m+mi}{300}\PY{p}{,} \PY{l+m+mi}{500}\PY{p}{]}\PY{p}{,}
            \PY{l+s+s2}{\PYZdq{}}\PY{l+s+s2}{cap\PYZus{}dc}\PY{l+s+s2}{\PYZdq{}}    \PY{p}{:} \PY{p}{[}\PY{l+m+mi}{530}\PY{p}{,} \PY{l+m+mi}{590}\PY{p}{,} \PY{l+m+mi}{400}\PY{p}{,} \PY{l+m+mi}{370}\PY{p}{,} \PY{l+m+mi}{580}\PY{p}{]}\PY{p}{,}
            \PY{l+s+s2}{\PYZdq{}}\PY{l+s+s2}{demand}\PY{l+s+s2}{\PYZdq{}}    \PY{p}{:} \PY{p}{[}\PY{l+m+mi}{460}\PY{p}{,} \PY{l+m+mi}{330}\PY{p}{,} \PY{l+m+mi}{450}\PY{p}{,} \PY{l+m+mi}{300}\PY{p}{]}
        \PY{p}{\PYZcb{}}
        
        \PY{c+c1}{\PYZsh{} some other parameters}
        \PY{n}{parameters} \PY{o}{=} \PY{p}{\PYZob{}}
            \PY{l+s+s2}{\PYZdq{}}\PY{l+s+s2}{suppliers}\PY{l+s+s2}{\PYZdq{}}        \PY{p}{:} \PY{l+m+mi}{3}\PY{p}{,}
            \PY{l+s+s2}{\PYZdq{}}\PY{l+s+s2}{locations\PYZus{}plant}\PY{l+s+s2}{\PYZdq{}}  \PY{p}{:} \PY{l+m+mi}{5}\PY{p}{,}
            \PY{l+s+s2}{\PYZdq{}}\PY{l+s+s2}{locations\PYZus{}dc}\PY{l+s+s2}{\PYZdq{}}     \PY{p}{:} \PY{l+m+mi}{5}\PY{p}{,}
            \PY{l+s+s2}{\PYZdq{}}\PY{l+s+s2}{locations\PYZus{}demand}\PY{l+s+s2}{\PYZdq{}} \PY{p}{:} \PY{l+m+mi}{4}\PY{p}{,}
            \PY{l+s+s2}{\PYZdq{}}\PY{l+s+s2}{ub\PYZus{}plant}\PY{l+s+s2}{\PYZdq{}}         \PY{p}{:} \PY{l+m+mi}{4}\PY{p}{,}
            \PY{l+s+s2}{\PYZdq{}}\PY{l+s+s2}{ub\PYZus{}dc}\PY{l+s+s2}{\PYZdq{}}            \PY{p}{:} \PY{l+m+mi}{4}
        \PY{p}{\PYZcb{}}
        
        \PY{c+c1}{\PYZsh{} defining dictionary for unit prod cost, distribution cost and supply cost}
        \PY{c+c1}{\PYZsh{} we define the cost parameters as dictionary having the same keys as the respective }
        \PY{c+c1}{\PYZsh{} variable, because it becomes very easy to use such dictionaries to generate linear}
        \PY{c+c1}{\PYZsh{} expressions for defining objective fucntion}
        \PY{n}{cost\PYZus{}array\PYZus{}p} \PY{o}{=} \PY{p}{[}\PY{p}{[}\PY{l+m+mi}{5}\PY{p}{,}\PY{l+m+mi}{6}\PY{p}{,}\PY{l+m+mi}{4}\PY{p}{,}\PY{l+m+mi}{7}\PY{p}{,}\PY{l+m+mi}{5}\PY{p}{]}\PY{p}{,}\PY{p}{[}\PY{l+m+mi}{6}\PY{p}{,}\PY{l+m+mi}{5}\PY{p}{,}\PY{l+m+mi}{6}\PY{p}{,}\PY{l+m+mi}{6}\PY{p}{,}\PY{l+m+mi}{8}\PY{p}{]}\PY{p}{,}\PY{p}{[}\PY{l+m+mi}{7}\PY{p}{,}\PY{l+m+mi}{6}\PY{p}{,}\PY{l+m+mi}{3}\PY{p}{,}\PY{l+m+mi}{9}\PY{p}{,}\PY{l+m+mi}{6}\PY{p}{]}\PY{p}{]}
        \PY{n}{cost\PYZus{}array\PYZus{}d} \PY{o}{=} \PY{p}{[}\PY{p}{[}\PY{l+m+mi}{5}\PY{p}{,}\PY{l+m+mi}{8}\PY{p}{,}\PY{l+m+mi}{5}\PY{p}{,}\PY{l+m+mi}{8}\PY{p}{,}\PY{l+m+mi}{5}\PY{p}{]}\PY{p}{,}\PY{p}{[}\PY{l+m+mi}{8}\PY{p}{,}\PY{l+m+mi}{7}\PY{p}{,}\PY{l+m+mi}{8}\PY{p}{,}\PY{l+m+mi}{6}\PY{p}{,}\PY{l+m+mi}{8}\PY{p}{]}\PY{p}{,}\PY{p}{[}\PY{l+m+mi}{4}\PY{p}{,}\PY{l+m+mi}{7}\PY{p}{,}\PY{l+m+mi}{4}\PY{p}{,}\PY{l+m+mi}{5}\PY{p}{,}\PY{l+m+mi}{4}\PY{p}{]}\PY{p}{,}\PY{p}{[}\PY{l+m+mi}{3}\PY{p}{,}\PY{l+m+mi}{5}\PY{p}{,}\PY{l+m+mi}{3}\PY{p}{,}\PY{l+m+mi}{5}\PY{p}{,}\PY{l+m+mi}{3}\PY{p}{]}\PY{p}{,}\PY{p}{[}\PY{l+m+mi}{5}\PY{p}{,}\PY{l+m+mi}{6}\PY{p}{,}\PY{l+m+mi}{6}\PY{p}{,}\PY{l+m+mi}{8}\PY{p}{,}\PY{l+m+mi}{3}\PY{p}{]}\PY{p}{]}
        \PY{n}{cost\PYZus{}array\PYZus{}s} \PY{o}{=} \PY{p}{[}\PY{p}{[}\PY{l+m+mi}{7}\PY{p}{,}\PY{l+m+mi}{4}\PY{p}{,}\PY{l+m+mi}{5}\PY{p}{,}\PY{l+m+mi}{6}\PY{p}{]}\PY{p}{,}\PY{p}{[}\PY{l+m+mi}{5}\PY{p}{,}\PY{l+m+mi}{4}\PY{p}{,}\PY{l+m+mi}{6}\PY{p}{,}\PY{l+m+mi}{7}\PY{p}{]}\PY{p}{,}\PY{p}{[}\PY{l+m+mi}{7}\PY{p}{,}\PY{l+m+mi}{5}\PY{p}{,}\PY{l+m+mi}{3}\PY{p}{,}\PY{l+m+mi}{6}\PY{p}{]}\PY{p}{,}\PY{p}{[}\PY{l+m+mi}{3}\PY{p}{,}\PY{l+m+mi}{5}\PY{p}{,}\PY{l+m+mi}{6}\PY{p}{,}\PY{l+m+mi}{4}\PY{p}{]}\PY{p}{,}\PY{p}{[}\PY{l+m+mi}{4}\PY{p}{,}\PY{l+m+mi}{6}\PY{p}{,}\PY{l+m+mi}{5}\PY{p}{,}\PY{l+m+mi}{7}\PY{p}{]}\PY{p}{]}
        \PY{n}{prod\PYZus{}c}\PY{p}{,} \PY{n}{dist\PYZus{}c}\PY{p}{,} \PY{n}{supp\PYZus{}c} \PY{o}{=} \PY{p}{\PYZob{}}\PY{p}{\PYZcb{}}\PY{p}{,} \PY{p}{\PYZob{}}\PY{p}{\PYZcb{}}\PY{p}{,} \PY{p}{\PYZob{}}\PY{p}{\PYZcb{}}
        
        \PY{k}{for} \PY{n}{i} \PY{o+ow}{in} \PY{n+nb}{range}\PY{p}{(}\PY{n}{parameters}\PY{p}{[}\PY{l+s+s2}{\PYZdq{}}\PY{l+s+s2}{suppliers}\PY{l+s+s2}{\PYZdq{}}\PY{p}{]}\PY{p}{)}\PY{p}{:}
            \PY{k}{for} \PY{n}{j} \PY{o+ow}{in} \PY{n+nb}{range}\PY{p}{(}\PY{n}{parameters}\PY{p}{[}\PY{l+s+s2}{\PYZdq{}}\PY{l+s+s2}{locations\PYZus{}plant}\PY{l+s+s2}{\PYZdq{}}\PY{p}{]}\PY{p}{)}\PY{p}{:}
                \PY{n}{prod\PYZus{}c}\PY{p}{[}\PY{p}{(}\PY{n}{i}\PY{p}{,}\PY{n}{j}\PY{p}{)}\PY{p}{]} \PY{o}{=} \PY{n}{cost\PYZus{}array\PYZus{}p}\PY{p}{[}\PY{n}{i}\PY{p}{]}\PY{p}{[}\PY{n}{j}\PY{p}{]}
                
        \PY{k}{for} \PY{n}{i} \PY{o+ow}{in} \PY{n+nb}{range}\PY{p}{(}\PY{n}{parameters}\PY{p}{[}\PY{l+s+s2}{\PYZdq{}}\PY{l+s+s2}{locations\PYZus{}plant}\PY{l+s+s2}{\PYZdq{}}\PY{p}{]}\PY{p}{)}\PY{p}{:}
            \PY{k}{for} \PY{n}{j} \PY{o+ow}{in} \PY{n+nb}{range}\PY{p}{(}\PY{n}{parameters}\PY{p}{[}\PY{l+s+s2}{\PYZdq{}}\PY{l+s+s2}{locations\PYZus{}dc}\PY{l+s+s2}{\PYZdq{}}\PY{p}{]}\PY{p}{)}\PY{p}{:}
                \PY{n}{dist\PYZus{}c}\PY{p}{[}\PY{p}{(}\PY{n}{i}\PY{p}{,}\PY{n}{j}\PY{p}{)}\PY{p}{]} \PY{o}{=} \PY{n}{cost\PYZus{}array\PYZus{}d}\PY{p}{[}\PY{n}{i}\PY{p}{]}\PY{p}{[}\PY{n}{j}\PY{p}{]}
                
        \PY{k}{for} \PY{n}{i} \PY{o+ow}{in} \PY{n+nb}{range}\PY{p}{(}\PY{n}{parameters}\PY{p}{[}\PY{l+s+s2}{\PYZdq{}}\PY{l+s+s2}{locations\PYZus{}dc}\PY{l+s+s2}{\PYZdq{}}\PY{p}{]}\PY{p}{)}\PY{p}{:}
            \PY{k}{for} \PY{n}{j} \PY{o+ow}{in} \PY{n+nb}{range}\PY{p}{(}\PY{n}{parameters}\PY{p}{[}\PY{l+s+s2}{\PYZdq{}}\PY{l+s+s2}{locations\PYZus{}demand}\PY{l+s+s2}{\PYZdq{}}\PY{p}{]}\PY{p}{)}\PY{p}{:}
                \PY{n}{supp\PYZus{}c}\PY{p}{[}\PY{p}{(}\PY{n}{i}\PY{p}{,}\PY{n}{j}\PY{p}{)}\PY{p}{]} \PY{o}{=} \PY{n}{cost\PYZus{}array\PYZus{}s}\PY{p}{[}\PY{n}{i}\PY{p}{]}\PY{p}{[}\PY{n}{j}\PY{p}{]}
                
        \PY{c+c1}{\PYZsh{} defining dictionary for fixed costs}
        \PY{n}{fixed\PYZus{}p}\PY{p}{,} \PY{n}{fixed\PYZus{}dc} \PY{o}{=} \PY{p}{\PYZob{}}\PY{p}{\PYZcb{}}\PY{p}{,} \PY{p}{\PYZob{}}\PY{p}{\PYZcb{}}
        \PY{n}{fixed\PYZus{}p\PYZus{}array}     \PY{o}{=} \PY{p}{[}\PY{l+m+mi}{1800}\PY{p}{,} \PY{l+m+mi}{900}\PY{p}{,} \PY{l+m+mi}{2100}\PY{p}{,} \PY{l+m+mi}{1100}\PY{p}{,} \PY{l+m+mi}{900}\PY{p}{]}
        \PY{n}{fixed\PYZus{}dc\PYZus{}array}    \PY{o}{=} \PY{p}{[}\PY{l+m+mi}{1000}\PY{p}{,} \PY{l+m+mi}{900}\PY{p}{,} \PY{l+m+mi}{1600}\PY{p}{,} \PY{l+m+mi}{1500}\PY{p}{,} \PY{l+m+mi}{1400}\PY{p}{]}
        
        \PY{k}{for} \PY{n}{i} \PY{o+ow}{in} \PY{n+nb}{range}\PY{p}{(}\PY{n}{parameters}\PY{p}{[}\PY{l+s+s2}{\PYZdq{}}\PY{l+s+s2}{locations\PYZus{}plant}\PY{l+s+s2}{\PYZdq{}}\PY{p}{]}\PY{p}{)}\PY{p}{:}
            \PY{n}{fixed\PYZus{}p}\PY{p}{[}\PY{p}{(}\PY{n}{i}\PY{p}{)}\PY{p}{]} \PY{o}{=} \PY{n}{fixed\PYZus{}p\PYZus{}array}\PY{p}{[}\PY{n}{i}\PY{p}{]}
            
        \PY{k}{for} \PY{n}{i} \PY{o+ow}{in} \PY{n+nb}{range}\PY{p}{(}\PY{n}{parameters}\PY{p}{[}\PY{l+s+s2}{\PYZdq{}}\PY{l+s+s2}{locations\PYZus{}dc}\PY{l+s+s2}{\PYZdq{}}\PY{p}{]}\PY{p}{)}\PY{p}{:}
            \PY{n}{fixed\PYZus{}dc}\PY{p}{[}\PY{p}{(}\PY{n}{i}\PY{p}{)}\PY{p}{]} \PY{o}{=} \PY{n}{fixed\PYZus{}dc\PYZus{}array}\PY{p}{[}\PY{n}{i}\PY{p}{]}
                
        \PY{c+c1}{\PYZsh{} defining dictionary for costs}
        \PY{n}{costs} \PY{o}{=} \PY{p}{\PYZob{}}
            \PY{l+s+s2}{\PYZdq{}}\PY{l+s+s2}{unit\PYZus{}prod\PYZus{}cost}\PY{l+s+s2}{\PYZdq{}}   \PY{p}{:} \PY{n}{prod\PYZus{}c}\PY{p}{,}
            \PY{l+s+s2}{\PYZdq{}}\PY{l+s+s2}{unit\PYZus{}dist\PYZus{}cost}\PY{l+s+s2}{\PYZdq{}}   \PY{p}{:} \PY{n}{dist\PYZus{}c}\PY{p}{,}
            \PY{l+s+s2}{\PYZdq{}}\PY{l+s+s2}{unit\PYZus{}supply\PYZus{}cost}\PY{l+s+s2}{\PYZdq{}} \PY{p}{:} \PY{n}{supp\PYZus{}c}\PY{p}{,}
            \PY{l+s+s2}{\PYZdq{}}\PY{l+s+s2}{fixed\PYZus{}plant}\PY{l+s+s2}{\PYZdq{}}      \PY{p}{:} \PY{n}{fixed\PYZus{}p}\PY{p}{,}
            \PY{l+s+s2}{\PYZdq{}}\PY{l+s+s2}{fixed\PYZus{}dc}\PY{l+s+s2}{\PYZdq{}}         \PY{p}{:} \PY{n}{fixed\PYZus{}dc}
        \PY{p}{\PYZcb{}}
\end{Verbatim}


    \begin{Verbatim}[commandchars=\\\{\}]
{\color{incolor}In [{\color{incolor}4}]:} \PY{c+c1}{\PYZsh{} Test Cell}
        
        \PY{c+c1}{\PYZsh{}print(prod\PYZus{}c.keys())}
\end{Verbatim}


    \begin{Verbatim}[commandchars=\\\{\}]
{\color{incolor}In [{\color{incolor}72}]:} \PY{c+c1}{\PYZsh{} In Gurobi, to create a model out of a formulation requires following steps to be done,}
         \PY{c+c1}{\PYZsh{} 1. Create an empty model}
         \PY{c+c1}{\PYZsh{} 2. Define variables, add to model, update model}
         \PY{c+c1}{\PYZsh{} 3. Define constraints, add to model, update model}
         \PY{c+c1}{\PYZsh{} 4. Define objective function, add to model, update model}
         
         \PY{c+c1}{\PYZsh{} In this cell we\PYZsq{}ll define first three}
         
         \PY{c+c1}{\PYZsh{} function for model}
         \PY{k}{def} \PY{n+nf}{get\PYZus{}empty\PYZus{}model}\PY{p}{(}\PY{p}{)}\PY{p}{:}
             
             \PY{c+c1}{\PYZsh{} define empty model}
             \PY{n}{m} \PY{o}{=} \PY{n}{Model}\PY{p}{(}\PY{p}{)}
             \PY{k}{return} \PY{n}{m}
         
         \PY{c+c1}{\PYZsh{} function for variables}
         \PY{k}{def} \PY{n+nf}{get\PYZus{}decision\PYZus{}var}\PY{p}{(}\PY{n}{m}\PY{p}{,} \PY{n}{paramaeters}\PY{p}{,} \PY{n}{RHS\PYZus{}m}\PY{p}{)}\PY{p}{:}
             
             \PY{c+c1}{\PYZsh{} production var}
             \PY{c+c1}{\PYZsh{} x = m.addVars(parameters[\PYZdq{}suppliers\PYZdq{}], parameters[\PYZdq{}locations\PYZus{}plant\PYZdq{}], lb = 0, vtype = GRB.INTEGER)}
             \PY{n}{x} \PY{o}{=} \PY{p}{\PYZob{}}\PY{p}{\PYZcb{}}
             \PY{k}{for} \PY{n}{i} \PY{o+ow}{in} \PY{n+nb}{range}\PY{p}{(}\PY{n}{parameters}\PY{p}{[}\PY{l+s+s2}{\PYZdq{}}\PY{l+s+s2}{suppliers}\PY{l+s+s2}{\PYZdq{}}\PY{p}{]}\PY{p}{)}\PY{p}{:}
                 \PY{k}{for} \PY{n}{j} \PY{o+ow}{in} \PY{n+nb}{range}\PY{p}{(}\PY{n}{parameters}\PY{p}{[}\PY{l+s+s2}{\PYZdq{}}\PY{l+s+s2}{locations\PYZus{}plant}\PY{l+s+s2}{\PYZdq{}}\PY{p}{]}\PY{p}{)}\PY{p}{:}
                     \PY{n}{x}\PY{p}{[}\PY{p}{(}\PY{n}{i}\PY{p}{,}\PY{n}{j}\PY{p}{)}\PY{p}{]} \PY{o}{=} \PY{n}{m}\PY{o}{.}\PY{n}{addVar}\PY{p}{(}\PY{n}{lb} \PY{o}{=} \PY{l+m+mi}{0}\PY{p}{,} \PY{n}{ub} \PY{o}{=} \PY{n}{RHS\PYZus{}m}\PY{p}{[}\PY{l+s+s2}{\PYZdq{}}\PY{l+s+s2}{cap\PYZus{}supply}\PY{l+s+s2}{\PYZdq{}}\PY{p}{]}\PY{p}{[}\PY{n}{i}\PY{p}{]}\PY{p}{,} \PY{n}{vtype} \PY{o}{=} \PY{n}{GRB}\PY{o}{.}\PY{n}{INTEGER}\PY{p}{,}
                                         \PY{n}{name} \PY{o}{=} \PY{l+s+s2}{\PYZdq{}}\PY{l+s+s2}{X(}\PY{l+s+si}{\PYZpc{}d}\PY{l+s+s2}{, }\PY{l+s+si}{\PYZpc{}d}\PY{l+s+s2}{)}\PY{l+s+s2}{\PYZdq{}}\PY{o}{\PYZpc{}}\PY{p}{(}\PY{n}{i}\PY{p}{,}\PY{n}{j}\PY{p}{)}\PY{p}{)}
                     
             
             \PY{c+c1}{\PYZsh{} distribution var}
             \PY{c+c1}{\PYZsh{}y = m.addVars(parameters[\PYZdq{}locations\PYZus{}plant\PYZdq{}], parameters[\PYZdq{}locations\PYZus{}dc\PYZdq{}], lb = 0, vtype = GRB.INTEGER)}
             \PY{n}{y} \PY{o}{=} \PY{p}{\PYZob{}}\PY{p}{\PYZcb{}}
             \PY{k}{for} \PY{n}{i} \PY{o+ow}{in} \PY{n+nb}{range}\PY{p}{(}\PY{n}{parameters}\PY{p}{[}\PY{l+s+s2}{\PYZdq{}}\PY{l+s+s2}{locations\PYZus{}plant}\PY{l+s+s2}{\PYZdq{}}\PY{p}{]}\PY{p}{)}\PY{p}{:}
                 \PY{k}{for} \PY{n}{j} \PY{o+ow}{in} \PY{n+nb}{range}\PY{p}{(}\PY{n}{parameters}\PY{p}{[}\PY{l+s+s2}{\PYZdq{}}\PY{l+s+s2}{locations\PYZus{}dc}\PY{l+s+s2}{\PYZdq{}}\PY{p}{]}\PY{p}{)}\PY{p}{:}
                     \PY{n}{y}\PY{p}{[}\PY{p}{(}\PY{n}{i}\PY{p}{,}\PY{n}{j}\PY{p}{)}\PY{p}{]} \PY{o}{=} \PY{n}{m}\PY{o}{.}\PY{n}{addVar}\PY{p}{(}\PY{n}{lb} \PY{o}{=} \PY{l+m+mi}{0}\PY{p}{,} \PY{n}{ub} \PY{o}{=} \PY{n}{RHS\PYZus{}m}\PY{p}{[}\PY{l+s+s2}{\PYZdq{}}\PY{l+s+s2}{cap\PYZus{}plant}\PY{l+s+s2}{\PYZdq{}}\PY{p}{]}\PY{p}{[}\PY{n}{i}\PY{p}{]}\PY{p}{,} \PY{n}{vtype} \PY{o}{=} \PY{n}{GRB}\PY{o}{.}\PY{n}{INTEGER}\PY{p}{,}
                                         \PY{n}{name} \PY{o}{=} \PY{l+s+s2}{\PYZdq{}}\PY{l+s+s2}{Y(}\PY{l+s+si}{\PYZpc{}d}\PY{l+s+s2}{, }\PY{l+s+si}{\PYZpc{}d}\PY{l+s+s2}{)}\PY{l+s+s2}{\PYZdq{}}\PY{o}{\PYZpc{}}\PY{p}{(}\PY{n}{i}\PY{p}{,}\PY{n}{j}\PY{p}{)}\PY{p}{)}
             
             \PY{c+c1}{\PYZsh{} supply var}
             \PY{c+c1}{\PYZsh{}z = m.addVars(parameters[\PYZdq{}locations\PYZus{}dc\PYZdq{}], parameters[\PYZdq{}locations\PYZus{}demand\PYZdq{}], lb = 0, vtype = GRB.INTEGER)}
             \PY{n}{z} \PY{o}{=} \PY{p}{\PYZob{}}\PY{p}{\PYZcb{}}
             \PY{k}{for} \PY{n}{i} \PY{o+ow}{in} \PY{n+nb}{range}\PY{p}{(}\PY{n}{parameters}\PY{p}{[}\PY{l+s+s2}{\PYZdq{}}\PY{l+s+s2}{locations\PYZus{}dc}\PY{l+s+s2}{\PYZdq{}}\PY{p}{]}\PY{p}{)}\PY{p}{:}
                 \PY{k}{for} \PY{n}{j} \PY{o+ow}{in} \PY{n+nb}{range}\PY{p}{(}\PY{n}{parameters}\PY{p}{[}\PY{l+s+s2}{\PYZdq{}}\PY{l+s+s2}{locations\PYZus{}demand}\PY{l+s+s2}{\PYZdq{}}\PY{p}{]}\PY{p}{)}\PY{p}{:}
                     \PY{n}{z}\PY{p}{[}\PY{p}{(}\PY{n}{i}\PY{p}{,}\PY{n}{j}\PY{p}{)}\PY{p}{]} \PY{o}{=} \PY{n}{m}\PY{o}{.}\PY{n}{addVar}\PY{p}{(}\PY{n}{lb} \PY{o}{=} \PY{l+m+mi}{0}\PY{p}{,} \PY{n}{ub} \PY{o}{=} \PY{n}{RHS\PYZus{}m}\PY{p}{[}\PY{l+s+s2}{\PYZdq{}}\PY{l+s+s2}{cap\PYZus{}dc}\PY{l+s+s2}{\PYZdq{}}\PY{p}{]}\PY{p}{[}\PY{n}{i}\PY{p}{]}\PY{p}{,} \PY{n}{vtype} \PY{o}{=} \PY{n}{GRB}\PY{o}{.}\PY{n}{INTEGER}\PY{p}{,}
                                         \PY{n}{name} \PY{o}{=} \PY{l+s+s2}{\PYZdq{}}\PY{l+s+s2}{Z(}\PY{l+s+si}{\PYZpc{}d}\PY{l+s+s2}{, }\PY{l+s+si}{\PYZpc{}d}\PY{l+s+s2}{)}\PY{l+s+s2}{\PYZdq{}}\PY{o}{\PYZpc{}}\PY{p}{(}\PY{n}{i}\PY{p}{,}\PY{n}{j}\PY{p}{)}\PY{p}{)}
             
             \PY{c+c1}{\PYZsh{} binary for plant selection}
             \PY{c+c1}{\PYZsh{}binary\PYZus{}plant = m.addVars(parameters[\PYZdq{}locations\PYZus{}plant\PYZdq{}], 1, lb = 0, vtype = GRB.BINARY)}
             \PY{n}{binary\PYZus{}plant} \PY{o}{=} \PY{p}{\PYZob{}}\PY{p}{\PYZcb{}}
             \PY{k}{for} \PY{n}{i} \PY{o+ow}{in} \PY{n+nb}{range}\PY{p}{(}\PY{n}{parameters}\PY{p}{[}\PY{l+s+s2}{\PYZdq{}}\PY{l+s+s2}{locations\PYZus{}plant}\PY{l+s+s2}{\PYZdq{}}\PY{p}{]}\PY{p}{)}\PY{p}{:}
                 \PY{n}{binary\PYZus{}plant}\PY{p}{[}\PY{p}{(}\PY{n}{i}\PY{p}{)}\PY{p}{]} \PY{o}{=} \PY{n}{m}\PY{o}{.}\PY{n}{addVar}\PY{p}{(}\PY{n}{lb} \PY{o}{=} \PY{l+m+mi}{0}\PY{p}{,} \PY{n}{vtype} \PY{o}{=} \PY{n}{GRB}\PY{o}{.}\PY{n}{BINARY}\PY{p}{,}
                                              \PY{n}{name} \PY{o}{=} \PY{l+s+s2}{\PYZdq{}}\PY{l+s+s2}{Plant(}\PY{l+s+si}{\PYZpc{}d}\PY{l+s+s2}{)}\PY{l+s+s2}{\PYZdq{}}\PY{o}{\PYZpc{}}\PY{p}{(}\PY{n}{i}\PY{p}{)}\PY{p}{)}
             
             \PY{c+c1}{\PYZsh{} binary for DC selection}
             \PY{c+c1}{\PYZsh{}binary\PYZus{}dc = m.addVars(parameters[\PYZdq{}locations\PYZus{}dc\PYZdq{}], 1, lb = 0, vtype = GRB.BINARY)}
             \PY{n}{binary\PYZus{}dc} \PY{o}{=} \PY{p}{\PYZob{}}\PY{p}{\PYZcb{}}
             \PY{k}{for} \PY{n}{i} \PY{o+ow}{in} \PY{n+nb}{range}\PY{p}{(}\PY{n}{parameters}\PY{p}{[}\PY{l+s+s2}{\PYZdq{}}\PY{l+s+s2}{locations\PYZus{}dc}\PY{l+s+s2}{\PYZdq{}}\PY{p}{]}\PY{p}{)}\PY{p}{:}
                 \PY{n}{binary\PYZus{}dc}\PY{p}{[}\PY{p}{(}\PY{n}{i}\PY{p}{)}\PY{p}{]} \PY{o}{=} \PY{n}{m}\PY{o}{.}\PY{n}{addVar}\PY{p}{(}\PY{n}{lb} \PY{o}{=} \PY{l+m+mi}{0}\PY{p}{,} \PY{n}{vtype} \PY{o}{=} \PY{n}{GRB}\PY{o}{.}\PY{n}{BINARY}\PY{p}{,}
                                              \PY{n}{name} \PY{o}{=} \PY{l+s+s2}{\PYZdq{}}\PY{l+s+s2}{DC(}\PY{l+s+si}{\PYZpc{}d}\PY{l+s+s2}{)}\PY{l+s+s2}{\PYZdq{}}\PY{o}{\PYZpc{}}\PY{p}{(}\PY{n}{i}\PY{p}{)}\PY{p}{)}
             
             \PY{n}{m}\PY{o}{.}\PY{n}{update}\PY{p}{(}\PY{p}{)}
             \PY{n}{var} \PY{o}{=} \PY{p}{\PYZob{}}
                 \PY{l+s+s2}{\PYZdq{}}\PY{l+s+s2}{prod\PYZus{}quant}\PY{l+s+s2}{\PYZdq{}}   \PY{p}{:} \PY{n}{tupledict}\PY{p}{(}\PY{n}{x}\PY{p}{)}\PY{p}{,}
                 \PY{l+s+s2}{\PYZdq{}}\PY{l+s+s2}{dist\PYZus{}quant}\PY{l+s+s2}{\PYZdq{}}   \PY{p}{:} \PY{n}{tupledict}\PY{p}{(}\PY{n}{y}\PY{p}{)}\PY{p}{,}
                 \PY{l+s+s2}{\PYZdq{}}\PY{l+s+s2}{supply\PYZus{}quant}\PY{l+s+s2}{\PYZdq{}} \PY{p}{:} \PY{n}{tupledict}\PY{p}{(}\PY{n}{z}\PY{p}{)}\PY{p}{,}
                 \PY{l+s+s2}{\PYZdq{}}\PY{l+s+s2}{decision\PYZus{}p}\PY{l+s+s2}{\PYZdq{}}   \PY{p}{:} \PY{n}{tupledict}\PY{p}{(}\PY{n}{binary\PYZus{}plant}\PY{p}{)}\PY{p}{,}
                 \PY{l+s+s2}{\PYZdq{}}\PY{l+s+s2}{decision\PYZus{}dc}\PY{l+s+s2}{\PYZdq{}}  \PY{p}{:} \PY{n}{tupledict}\PY{p}{(}\PY{n}{binary\PYZus{}dc}\PY{p}{)}
             \PY{p}{\PYZcb{}}
             \PY{k}{return} \PY{n}{m}\PY{p}{,} \PY{n}{var}
         
         \PY{c+c1}{\PYZsh{} function for constraints}
         \PY{k}{def} \PY{n+nf}{get\PYZus{}constraints}\PY{p}{(}\PY{n}{m}\PY{p}{,} \PY{n}{var}\PY{p}{,} \PY{n}{RHS\PYZus{}m}\PY{p}{,} \PY{n}{paramaeters}\PY{p}{)}\PY{p}{:}
             
             \PY{n}{con} \PY{o}{=} \PY{p}{\PYZob{}}\PY{p}{\PYZcb{}}
             
             \PY{c+c1}{\PYZsh{} unpack var}
             \PY{n}{x}            \PY{o}{=} \PY{n}{var}\PY{p}{[}\PY{l+s+s2}{\PYZdq{}}\PY{l+s+s2}{prod\PYZus{}quant}\PY{l+s+s2}{\PYZdq{}}\PY{p}{]}
             \PY{n}{y}            \PY{o}{=} \PY{n}{var}\PY{p}{[}\PY{l+s+s2}{\PYZdq{}}\PY{l+s+s2}{dist\PYZus{}quant}\PY{l+s+s2}{\PYZdq{}}\PY{p}{]}
             \PY{n}{z}            \PY{o}{=} \PY{n}{var}\PY{p}{[}\PY{l+s+s2}{\PYZdq{}}\PY{l+s+s2}{supply\PYZus{}quant}\PY{l+s+s2}{\PYZdq{}}\PY{p}{]}
             \PY{n}{binary\PYZus{}plant} \PY{o}{=} \PY{n}{var}\PY{p}{[}\PY{l+s+s2}{\PYZdq{}}\PY{l+s+s2}{decision\PYZus{}p}\PY{l+s+s2}{\PYZdq{}}\PY{p}{]}
             \PY{n}{binary\PYZus{}dc}    \PY{o}{=} \PY{n}{var}\PY{p}{[}\PY{l+s+s2}{\PYZdq{}}\PY{l+s+s2}{decision\PYZus{}dc}\PY{l+s+s2}{\PYZdq{}}\PY{p}{]}
             
             \PY{c+c1}{\PYZsh{} capacity limit on production}
             \PY{n}{con}\PY{p}{[}\PY{l+s+s2}{\PYZdq{}}\PY{l+s+s2}{1}\PY{l+s+s2}{\PYZdq{}}\PY{p}{]} \PY{o}{=} \PY{n}{m}\PY{o}{.}\PY{n}{addConstrs}\PY{p}{(}\PY{n}{x}\PY{o}{.}\PY{n}{sum}\PY{p}{(}\PY{n}{i}\PY{p}{,} \PY{l+s+s1}{\PYZsq{}}\PY{l+s+s1}{*}\PY{l+s+s1}{\PYZsq{}}\PY{p}{)} \PY{o}{\PYZlt{}}\PY{o}{=} \PY{n}{RHS\PYZus{}m}\PY{p}{[}\PY{l+s+s2}{\PYZdq{}}\PY{l+s+s2}{cap\PYZus{}supply}\PY{l+s+s2}{\PYZdq{}}\PY{p}{]}\PY{p}{[}\PY{n}{i}\PY{p}{]} \PY{k}{for} \PY{n}{i} \PY{o+ow}{in} \PY{n+nb}{range}\PY{p}{(}\PY{n}{parameters}\PY{p}{[}\PY{l+s+s2}{\PYZdq{}}\PY{l+s+s2}{suppliers}\PY{l+s+s2}{\PYZdq{}}\PY{p}{]}\PY{p}{)}\PY{p}{)}
             \PY{c+c1}{\PYZsh{}print(con[\PYZdq{}1\PYZdq{}].keys())}
             
             \PY{c+c1}{\PYZsh{} supply is possible from the plants for which binary\PYZus{}plant = 1}
             \PY{n}{con}\PY{p}{[}\PY{l+s+s2}{\PYZdq{}}\PY{l+s+s2}{2}\PY{l+s+s2}{\PYZdq{}}\PY{p}{]} \PY{o}{=} \PY{n}{m}\PY{o}{.}\PY{n}{addConstrs}\PY{p}{(}\PY{n}{y}\PY{o}{.}\PY{n}{sum}\PY{p}{(}\PY{n}{j}\PY{p}{,} \PY{l+s+s1}{\PYZsq{}}\PY{l+s+s1}{*}\PY{l+s+s1}{\PYZsq{}}\PY{p}{)}  \PY{o}{\PYZhy{}} \PY{n}{RHS\PYZus{}m}\PY{p}{[}\PY{l+s+s2}{\PYZdq{}}\PY{l+s+s2}{cap\PYZus{}plant}\PY{l+s+s2}{\PYZdq{}}\PY{p}{]}\PY{p}{[}\PY{n}{j}\PY{p}{]} \PY{o}{*} \PY{n}{binary\PYZus{}plant}\PY{p}{[}\PY{n}{j}\PY{p}{]} \PY{o}{\PYZlt{}}\PY{o}{=} \PY{l+m+mi}{0} \PY{k}{for} \PY{n}{j} \PY{o+ow}{in} \PY{n+nb}{range}\PY{p}{(}\PY{n}{parameters}\PY{p}{[}\PY{l+s+s2}{\PYZdq{}}\PY{l+s+s2}{locations\PYZus{}plant}\PY{l+s+s2}{\PYZdq{}}\PY{p}{]}\PY{p}{)}\PY{p}{)}
             \PY{c+c1}{\PYZsh{}print(con[\PYZdq{}2\PYZdq{}].keys())}
             
             \PY{c+c1}{\PYZsh{} upper bound on total number of plants to be constructed}
             \PY{n}{con}\PY{p}{[}\PY{l+s+s2}{\PYZdq{}}\PY{l+s+s2}{3}\PY{l+s+s2}{\PYZdq{}}\PY{p}{]} \PY{o}{=} \PY{n}{m}\PY{o}{.}\PY{n}{addConstr}\PY{p}{(}\PY{n}{binary\PYZus{}plant}\PY{o}{.}\PY{n}{sum}\PY{p}{(}\PY{p}{)} \PY{o}{\PYZlt{}}\PY{o}{=} \PY{n}{parameters}\PY{p}{[}\PY{l+s+s2}{\PYZdq{}}\PY{l+s+s2}{ub\PYZus{}plant}\PY{l+s+s2}{\PYZdq{}}\PY{p}{]}\PY{p}{)}
             
             \PY{c+c1}{\PYZsh{} supply to customer points is only possible from the distribution centers in existance}
             \PY{n}{con}\PY{p}{[}\PY{l+s+s2}{\PYZdq{}}\PY{l+s+s2}{4}\PY{l+s+s2}{\PYZdq{}}\PY{p}{]} \PY{o}{=} \PY{n}{m}\PY{o}{.}\PY{n}{addConstrs}\PY{p}{(}\PY{n}{z}\PY{o}{.}\PY{n}{sum}\PY{p}{(}\PY{n}{k}\PY{p}{,} \PY{l+s+s1}{\PYZsq{}}\PY{l+s+s1}{*}\PY{l+s+s1}{\PYZsq{}}\PY{p}{)} \PY{o}{\PYZhy{}} \PY{n}{RHS\PYZus{}m}\PY{p}{[}\PY{l+s+s2}{\PYZdq{}}\PY{l+s+s2}{cap\PYZus{}dc}\PY{l+s+s2}{\PYZdq{}}\PY{p}{]}\PY{p}{[}\PY{n}{k}\PY{p}{]} \PY{o}{*} \PY{n}{binary\PYZus{}dc}\PY{p}{[}\PY{n}{k}\PY{p}{]} \PY{o}{\PYZlt{}}\PY{o}{=} \PY{l+m+mi}{0} \PY{k}{for} \PY{n}{k} \PY{o+ow}{in} \PY{n+nb}{range}\PY{p}{(}\PY{n}{parameters}\PY{p}{[}\PY{l+s+s2}{\PYZdq{}}\PY{l+s+s2}{locations\PYZus{}dc}\PY{l+s+s2}{\PYZdq{}}\PY{p}{]}\PY{p}{)}\PY{p}{)}
             \PY{c+c1}{\PYZsh{}print(con[\PYZdq{}4\PYZdq{}].keys())}
             
             \PY{c+c1}{\PYZsh{} upper bound on total number of dcs to be constructed}
             \PY{n}{con}\PY{p}{[}\PY{l+s+s2}{\PYZdq{}}\PY{l+s+s2}{5}\PY{l+s+s2}{\PYZdq{}}\PY{p}{]} \PY{o}{=} \PY{n}{m}\PY{o}{.}\PY{n}{addConstr}\PY{p}{(}\PY{n}{binary\PYZus{}dc}\PY{o}{.}\PY{n}{sum}\PY{p}{(}\PY{p}{)} \PY{o}{\PYZlt{}}\PY{o}{=} \PY{n}{parameters}\PY{p}{[}\PY{l+s+s2}{\PYZdq{}}\PY{l+s+s2}{ub\PYZus{}dc}\PY{l+s+s2}{\PYZdq{}}\PY{p}{]}\PY{p}{)}
             
             \PY{c+c1}{\PYZsh{} demand}
             \PY{n}{con}\PY{p}{[}\PY{l+s+s2}{\PYZdq{}}\PY{l+s+s2}{6}\PY{l+s+s2}{\PYZdq{}}\PY{p}{]} \PY{o}{=} \PY{n}{m}\PY{o}{.}\PY{n}{addConstrs}\PY{p}{(}\PY{n}{z}\PY{o}{.}\PY{n}{sum}\PY{p}{(}\PY{l+s+s1}{\PYZsq{}}\PY{l+s+s1}{*}\PY{l+s+s1}{\PYZsq{}}\PY{p}{,} \PY{n}{l}\PY{p}{)} \PY{o}{\PYZgt{}}\PY{o}{=} \PY{n}{RHS\PYZus{}m}\PY{p}{[}\PY{l+s+s2}{\PYZdq{}}\PY{l+s+s2}{demand}\PY{l+s+s2}{\PYZdq{}}\PY{p}{]}\PY{p}{[}\PY{n}{l}\PY{p}{]} \PY{k}{for} \PY{n}{l} \PY{o+ow}{in} \PY{n+nb}{range}\PY{p}{(}\PY{n}{parameters}\PY{p}{[}\PY{l+s+s2}{\PYZdq{}}\PY{l+s+s2}{locations\PYZus{}demand}\PY{l+s+s2}{\PYZdq{}}\PY{p}{]}\PY{p}{)}\PY{p}{)}
             \PY{c+c1}{\PYZsh{}print(con[\PYZdq{}6\PYZdq{}].keys())}
             
             \PY{c+c1}{\PYZsh{} mass balance}
             \PY{n}{con}\PY{p}{[}\PY{l+s+s2}{\PYZdq{}}\PY{l+s+s2}{7}\PY{l+s+s2}{\PYZdq{}}\PY{p}{]} \PY{o}{=} \PY{n}{m}\PY{o}{.}\PY{n}{addConstrs}\PY{p}{(}\PY{n}{x}\PY{o}{.}\PY{n}{sum}\PY{p}{(}\PY{l+s+s1}{\PYZsq{}}\PY{l+s+s1}{*}\PY{l+s+s1}{\PYZsq{}}\PY{p}{,} \PY{n}{j}\PY{p}{)} \PY{o}{==} \PY{n}{y}\PY{o}{.}\PY{n}{sum}\PY{p}{(}\PY{n}{j}\PY{p}{,} \PY{l+s+s1}{\PYZsq{}}\PY{l+s+s1}{*}\PY{l+s+s1}{\PYZsq{}}\PY{p}{)} \PY{k}{for} \PY{n}{j} \PY{o+ow}{in} \PY{n+nb}{range}\PY{p}{(}\PY{n}{parameters}\PY{p}{[}\PY{l+s+s2}{\PYZdq{}}\PY{l+s+s2}{locations\PYZus{}plant}\PY{l+s+s2}{\PYZdq{}}\PY{p}{]}\PY{p}{)}\PY{p}{)}
             \PY{n}{con}\PY{p}{[}\PY{l+s+s2}{\PYZdq{}}\PY{l+s+s2}{8}\PY{l+s+s2}{\PYZdq{}}\PY{p}{]} \PY{o}{=} \PY{n}{m}\PY{o}{.}\PY{n}{addConstrs}\PY{p}{(}\PY{n}{y}\PY{o}{.}\PY{n}{sum}\PY{p}{(}\PY{l+s+s1}{\PYZsq{}}\PY{l+s+s1}{*}\PY{l+s+s1}{\PYZsq{}}\PY{p}{,} \PY{n}{k}\PY{p}{)} \PY{o}{==} \PY{n}{z}\PY{o}{.}\PY{n}{sum}\PY{p}{(}\PY{n}{k}\PY{p}{,} \PY{l+s+s1}{\PYZsq{}}\PY{l+s+s1}{*}\PY{l+s+s1}{\PYZsq{}}\PY{p}{)} \PY{k}{for} \PY{n}{k} \PY{o+ow}{in} \PY{n+nb}{range}\PY{p}{(}\PY{n}{parameters}\PY{p}{[}\PY{l+s+s2}{\PYZdq{}}\PY{l+s+s2}{locations\PYZus{}dc}\PY{l+s+s2}{\PYZdq{}}\PY{p}{]}\PY{p}{)}\PY{p}{)}
             
             
             \PY{n}{m}\PY{o}{.}\PY{n}{update}\PY{p}{(}\PY{p}{)}
             \PY{k}{return} \PY{n}{m}\PY{p}{,} \PY{n}{con}
\end{Verbatim}


    \begin{Verbatim}[commandchars=\\\{\}]
{\color{incolor}In [{\color{incolor}73}]:} \PY{c+c1}{\PYZsh{} Test Cell}
         \PY{n}{m} \PY{o}{=} \PY{n}{get\PYZus{}empty\PYZus{}model}\PY{p}{(}\PY{p}{)}
         \PY{n}{m}\PY{p}{,} \PY{n}{var} \PY{o}{=} \PY{n}{get\PYZus{}decision\PYZus{}var}\PY{p}{(}\PY{n}{m}\PY{p}{,} \PY{n}{parameters}\PY{p}{,} \PY{n}{RHS\PYZus{}m}\PY{p}{)}
         \PY{n}{m}\PY{p}{,} \PY{n}{con} \PY{o}{=} \PY{n}{get\PYZus{}constraints}\PY{p}{(}\PY{n}{m}\PY{p}{,} \PY{n}{var}\PY{p}{,} \PY{n}{RHS\PYZus{}m}\PY{p}{,} \PY{n}{parameters}\PY{p}{)}
\end{Verbatim}


    \begin{Verbatim}[commandchars=\\\{\}]
{\color{incolor}In [{\color{incolor}74}]:} \PY{c+c1}{\PYZsh{} In this cell we\PYZsq{}ll define fourth step of building model for a formulation, i.e we\PYZsq{}ll define}
         \PY{c+c1}{\PYZsh{} objective function in this cell}
         
         \PY{c+c1}{\PYZsh{} The whole objective function can be broken down into five different costs, we\PYZsq{}ll define}
         \PY{c+c1}{\PYZsh{} expressions for each cost and will add everything together for defining objective function.}
         
         \PY{k}{def} \PY{n+nf}{get\PYZus{}objective}\PY{p}{(}\PY{n}{m}\PY{p}{,} \PY{n}{var}\PY{p}{,} \PY{n}{con}\PY{p}{)}\PY{p}{:}
             
             \PY{n}{objectives} \PY{o}{=} \PY{p}{\PYZob{}}\PY{p}{\PYZcb{}}
             
             \PY{c+c1}{\PYZsh{} unpack var}
             \PY{n}{x}            \PY{o}{=} \PY{n}{var}\PY{p}{[}\PY{l+s+s2}{\PYZdq{}}\PY{l+s+s2}{prod\PYZus{}quant}\PY{l+s+s2}{\PYZdq{}}\PY{p}{]}
             \PY{n}{y}            \PY{o}{=} \PY{n}{var}\PY{p}{[}\PY{l+s+s2}{\PYZdq{}}\PY{l+s+s2}{dist\PYZus{}quant}\PY{l+s+s2}{\PYZdq{}}\PY{p}{]}
             \PY{n}{z}            \PY{o}{=} \PY{n}{var}\PY{p}{[}\PY{l+s+s2}{\PYZdq{}}\PY{l+s+s2}{supply\PYZus{}quant}\PY{l+s+s2}{\PYZdq{}}\PY{p}{]}
             \PY{n}{binary\PYZus{}plant} \PY{o}{=} \PY{n}{var}\PY{p}{[}\PY{l+s+s2}{\PYZdq{}}\PY{l+s+s2}{decision\PYZus{}p}\PY{l+s+s2}{\PYZdq{}}\PY{p}{]}
             \PY{n}{binary\PYZus{}dc}    \PY{o}{=} \PY{n}{var}\PY{p}{[}\PY{l+s+s2}{\PYZdq{}}\PY{l+s+s2}{decision\PYZus{}dc}\PY{l+s+s2}{\PYZdq{}}\PY{p}{]}
             
         
             \PY{c+c1}{\PYZsh{} 1. Production cost}
             \PY{n}{objectives}\PY{p}{[}\PY{l+s+s2}{\PYZdq{}}\PY{l+s+s2}{Production}\PY{l+s+s2}{\PYZdq{}}\PY{p}{]} \PY{o}{=} \PY{n}{x}\PY{o}{.}\PY{n}{prod}\PY{p}{(}\PY{n}{costs}\PY{p}{[}\PY{l+s+s2}{\PYZdq{}}\PY{l+s+s2}{unit\PYZus{}prod\PYZus{}cost}\PY{l+s+s2}{\PYZdq{}}\PY{p}{]}\PY{p}{)}
         
             \PY{c+c1}{\PYZsh{} 2. Distribution cost}
             \PY{n}{objectives}\PY{p}{[}\PY{l+s+s2}{\PYZdq{}}\PY{l+s+s2}{Distribution}\PY{l+s+s2}{\PYZdq{}}\PY{p}{]} \PY{o}{=} \PY{n}{y}\PY{o}{.}\PY{n}{prod}\PY{p}{(}\PY{n}{costs}\PY{p}{[}\PY{l+s+s2}{\PYZdq{}}\PY{l+s+s2}{unit\PYZus{}dist\PYZus{}cost}\PY{l+s+s2}{\PYZdq{}}\PY{p}{]}\PY{p}{)}
         
             \PY{c+c1}{\PYZsh{} 3. Supply Cost}
             \PY{n}{objectives}\PY{p}{[}\PY{l+s+s2}{\PYZdq{}}\PY{l+s+s2}{Supply}\PY{l+s+s2}{\PYZdq{}}\PY{p}{]} \PY{o}{=} \PY{n}{z}\PY{o}{.}\PY{n}{prod}\PY{p}{(}\PY{n}{costs}\PY{p}{[}\PY{l+s+s2}{\PYZdq{}}\PY{l+s+s2}{unit\PYZus{}supply\PYZus{}cost}\PY{l+s+s2}{\PYZdq{}}\PY{p}{]}\PY{p}{)}
         
             \PY{c+c1}{\PYZsh{} 4. Fixed cost for plant}
             \PY{n}{objectives}\PY{p}{[}\PY{l+s+s2}{\PYZdq{}}\PY{l+s+s2}{Fixed\PYZus{}Plant}\PY{l+s+s2}{\PYZdq{}}\PY{p}{]} \PY{o}{=} \PY{n}{binary\PYZus{}plant}\PY{o}{.}\PY{n}{prod}\PY{p}{(}\PY{n}{costs}\PY{p}{[}\PY{l+s+s2}{\PYZdq{}}\PY{l+s+s2}{fixed\PYZus{}plant}\PY{l+s+s2}{\PYZdq{}}\PY{p}{]}\PY{p}{)}
             
             \PY{c+c1}{\PYZsh{} 5. Fixed cost for distribution center}
             \PY{n}{objectives}\PY{p}{[}\PY{l+s+s2}{\PYZdq{}}\PY{l+s+s2}{Fixed\PYZus{}DC}\PY{l+s+s2}{\PYZdq{}}\PY{p}{]} \PY{o}{=} \PY{n}{binary\PYZus{}dc}\PY{o}{.}\PY{n}{prod}\PY{p}{(}\PY{n}{costs}\PY{p}{[}\PY{l+s+s2}{\PYZdq{}}\PY{l+s+s2}{fixed\PYZus{}dc}\PY{l+s+s2}{\PYZdq{}}\PY{p}{]}\PY{p}{)}
             
             \PY{c+c1}{\PYZsh{} Add objective to the model}
             \PY{k}{print}\PY{p}{(}\PY{n}{objectives}\PY{o}{.}\PY{n}{keys}\PY{p}{(}\PY{p}{)}\PY{p}{)}
             \PY{n}{m}\PY{o}{.}\PY{n}{setObjective}\PY{p}{(}\PY{n+nb}{sum}\PY{p}{(}\PY{n}{objectives}\PY{o}{.}\PY{n}{itervalues}\PY{p}{(}\PY{p}{)}\PY{p}{)}\PY{p}{,} \PY{n}{GRB}\PY{o}{.}\PY{n}{MINIMIZE}\PY{p}{)}
             
             \PY{c+c1}{\PYZsh{} update model}
             \PY{n}{m}\PY{o}{.}\PY{n}{update}\PY{p}{(}\PY{p}{)}
             
             \PY{c+c1}{\PYZsh{} solve}
             \PY{n}{m}\PY{o}{.}\PY{n}{optimize}\PY{p}{(}\PY{p}{)}
         
             \PY{c+c1}{\PYZsh{} get solution}
             \PY{n}{m}\PY{o}{.}\PY{n}{printAttr}\PY{p}{(}\PY{l+s+s1}{\PYZsq{}}\PY{l+s+s1}{x}\PY{l+s+s1}{\PYZsq{}}\PY{p}{)}
             
             \PY{k}{return} \PY{n}{m}
\end{Verbatim}


    \begin{Verbatim}[commandchars=\\\{\}]
{\color{incolor}In [{\color{incolor}75}]:} \PY{c+c1}{\PYZsh{} In this cell we\PYZsq{}ll call all the functions and then we\PYZsq{}ll solve the optimization problem to get the}
         \PY{c+c1}{\PYZsh{} solution}
         
         \PY{c+c1}{\PYZsh{} 1. define model}
         \PY{n}{m} \PY{o}{=} \PY{n}{get\PYZus{}empty\PYZus{}model}\PY{p}{(}\PY{p}{)}
         
         \PY{c+c1}{\PYZsh{} 2. define vars}
         \PY{n}{m}\PY{p}{,} \PY{n}{var} \PY{o}{=} \PY{n}{get\PYZus{}decision\PYZus{}var}\PY{p}{(}\PY{n}{m}\PY{p}{,} \PY{n}{parameters}\PY{p}{,} \PY{n}{RHS\PYZus{}m}\PY{p}{)}
         
         \PY{c+c1}{\PYZsh{} 3. define constraints}
         \PY{n}{m}\PY{p}{,} \PY{n}{con} \PY{o}{=} \PY{n}{get\PYZus{}constraints}\PY{p}{(}\PY{n}{m}\PY{p}{,} \PY{n}{var}\PY{p}{,} \PY{n}{RHS\PYZus{}m}\PY{p}{,} \PY{n}{parameters}\PY{p}{)}
         
         \PY{c+c1}{\PYZsh{} 4. solve the optimization problem}
         \PY{n}{m} \PY{o}{=} \PY{n}{get\PYZus{}objective}\PY{p}{(}\PY{n}{m}\PY{p}{,} \PY{n}{var}\PY{p}{,} \PY{n}{con}\PY{p}{)}
\end{Verbatim}


    \begin{Verbatim}[commandchars=\\\{\}]
['Distribution', 'Production', 'Fixed\_Plant', 'Fixed\_DC', 'Supply']
Optimize a model with 29 rows, 70 columns and 185 nonzeros
Variable types: 0 continuous, 70 integer (10 binary)
Coefficient statistics:
  Matrix range     [1e+00, 6e+02]
  Objective range  [3e+00, 2e+03]
  Bounds range     [1e+00, 6e+02]
  RHS range        [4e+00, 6e+02]
Found heuristic solution: objective 37910.000000
Presolve time: 0.00s
Presolved: 29 rows, 70 columns, 185 nonzeros
Variable types: 0 continuous, 70 integer (10 binary)

Root relaxation: objective 2.800354e+04, 47 iterations, 0.00 seconds

    Nodes    |    Current Node    |     Objective Bounds      |     Work
 Expl Unexpl |  Obj  Depth IntInf | Incumbent    BestBd   Gap | It/Node Time

     0     0 28003.5398    0    6 37910.0000 28003.5398  26.1\%     -    0s
H    0     0                    30400.000000 28003.5398  7.88\%     -    0s
H    0     0                    30020.000000 28003.5398  6.72\%     -    0s
     0     0 28420.9128    0   12 30020.0000 28420.9128  5.33\%     -    0s
     0     0 28519.7810    0   19 30020.0000 28519.7810  5.00\%     -    0s
     0     0 28522.0235    0   25 30020.0000 28522.0235  4.99\%     -    0s
     0     0 28675.4157    0   12 30020.0000 28675.4157  4.48\%     -    0s
H    0     0                    29997.000000 28675.4157  4.41\%     -    0s
H    0     0                    29640.000000 28675.4157  3.25\%     -    0s
     0     0 28706.4448    0   25 29640.0000 28706.4448  3.15\%     -    0s
     0     0 28715.2481    0   27 29640.0000 28715.2481  3.12\%     -    0s
     0     0 28770.0000    0   15 29640.0000 28770.0000  2.94\%     -    0s
H    0     0                    29478.000000 28770.0000  2.40\%     -    0s
     0     0 28775.0000    0   21 29478.0000 28775.0000  2.38\%     -    0s
     0     0 28781.4856    0   30 29478.0000 28781.4856  2.36\%     -    0s
H    0     0                    29440.000000 28781.4856  2.24\%     -    0s
     0     0 28783.5080    0   30 29440.0000 28783.5080  2.23\%     -    0s
     0     0 28786.8421    0   21 29440.0000 28786.8421  2.22\%     -    0s
     0     0 28786.8421    0   21 29440.0000 28786.8421  2.22\%     -    0s
H    0     0                    28960.000000 28786.8421  0.60\%     -    0s
     0     0 28786.8421    0    3 28960.0000 28786.8421  0.60\%     -    0s
     0     0 28793.3409    0   10 28960.0000 28793.3409  0.58\%     -    0s
     0     0 28821.8182    0   13 28960.0000 28821.8182  0.48\%     -    0s
     0     0 28834.0741    0   17 28960.0000 28834.0741  0.43\%     -    0s
     0     0 28843.1481    0   22 28960.0000 28843.1481  0.40\%     -    0s
     0     0 28862.5155    0   18 28960.0000 28862.5155  0.34\%     -    0s
*    0     0               0    28870.000000 28870.0000  0.00\%     -    0s

Cutting planes:
  Gomory: 1
  Implied bound: 3
  MIR: 8
  Flow cover: 1

Explored 1 nodes (176 simplex iterations) in 0.15 seconds
Thread count was 4 (of 4 available processors)

Solution count 9: 28870 28960 29440 {\ldots} 37910

Optimal solution found (tolerance 1.00e-04)
Best objective 2.887000000000e+04, best bound 2.887000000000e+04, gap 0.0000\%

    Variable            x 
-------------------------
     X(0, 4)          500 
     X(1, 1)          550 
     X(1, 2)          100 
     X(2, 2)          390 
     Y(1, 1)          550 
     Y(2, 1)           10 
     Y(2, 2)          400 
     Y(2, 4)           80 
     Y(4, 4)          500 
     Z(1, 1)          330 
     Z(1, 3)          230 
     Z(2, 2)          400 
     Z(4, 0)          460 
     Z(4, 2)           50 
     Z(4, 3)           70 
    Plant(1)            1 
    Plant(2)            1 
    Plant(4)            1 
       DC(1)            1 
       DC(2)            1 
       DC(4)            1 

    \end{Verbatim}


    % Add a bibliography block to the postdoc
    
    
    
    \end{document}
