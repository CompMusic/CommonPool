Using the glossaries package is the easiest and the most efficient way to include correct transliteration of Indian, Turkish, and Chinese terms in papers written with latex. Instead of transliterating every time we encounter a term, we define a glossary entry only once and use it in the latex source whenever we wish to use the term. The acronym package handles acronyms. What's more, the package will add a glossary of terms and acronyms to the paper if needed (Not usually used, since papers need to be short). 

e.g. \gls{tala} in the source -> 'tāḷa' in the pdf

Get the packages 'glossaries' and 'acronym' from your LaTeX distribution repository. It will include a perl script called makeglossaries
See the wiki to know how to use the glossaries package and makeglossaries: http://en.wikibooks.org/wiki/LaTeX/Glossary

Use XeLaTeX for best results! If you have questions, feel free to ask. 

A typical latex source file in which I use glossaries looks like this. (I use XeLaTeX)
************************************************************************************
\usepackage{fontspec}
\setmainfont[Mapping=tex-text]{Times New Roman}
\usepackage{acronym}
\usepackage[nomain,acronym,nonumberlist,nogroupskip=true]{glossaries}
\newglossary[lgc]{CM}{gic}{goc}{Carnatic Music}  
\newglossary[lgh]{HM}{gih}{goh}{Hindustani Music} 
\newglossary[lgt]{TM}{git}{got}{Turkish Makam Music} 
\glossarystyle{index}
\makeglossaries
%%
\begin{document}
\input{CarnaticGlossary.tex}
\input{HindustaniGlossary.tex}
\input{TurkishGlossary.tex}
%%
<the paper content>
\gls{tala}
%% 
\printglossary[type=CM]		% Needed only if you need glossaries to be printed. 
\printglossary[type=HM]
\printglossary[type=TM]
\end{document}
****************************************************************************************