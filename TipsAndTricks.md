# Tips and Tricks

## Abstracts
%\addcontentsline{toc}{section}{Abstract} % add this if you want the abstract in the table of contents.
  This document outlines a few important aspects of a lab report. It contains some advice on both content and layout. The \LaTeX{} source for this document is also published, and you can use it as a template of sorts for your own report. You can find an up to date version of the source at \url{https://github.com/ntnu-itk/labreport}. The main file, ``labreport.tex'', defines the structure of the document. The ``preamble.tex'' file is the document preamble, and contains a lot of informative comments. The document is based on work done by Tor Aksel Heirung for TTK4135, and is now under continuous improvement by Andreas L. Fl{\aa}ten and Kristoffer Gryte (happily accepting suggestions and contributions from the community).

When you write your own report, this section (the abstract) should contain a \emph{very} short summary of what the lab is about and what you have done.

## Intro
Your introduction should contain an overview of the work you were assigned, as well as a few sentences putting the work into a larger perspective. You should also give a quick description of how the report is organized (as is done below).

You should of course put most of the work into doing good work in the lab and then presenting it in the report. When presenting your work in the report, both content and presentation/layout matters. Since your only way of communicating your good effort in the lab is through writing about it here, the way you write about it is essential. This means that even if you have the very best controller but describe it poorly, you will probably not be rewarded for the good results. A plot showing perfect control is worth very little if it is not accompanied by a clear description of what it represents.

Layout is naturally less important than content, but it still matters. You can think of report writing like selling an apartment; when you present your apartment for potential buyers you will of course clean the apartment and make it good looking. How clean the apartment is does of course not determine its value, but it is still important since it influences the subjective value your buyers will put on the apartment. 

\subsection{Software}
You are of course free to use whatever software you want for report writing. You can also submit a handwritten report, although this is probably not a great idea if your handwriting can be hard to read. 

You can also use Word or a similar word processor. However, it is next to impossible to achieve decent layout with Word. The support for vector graphics (discussed later) is extremely poor, and text tends to look pretty bad (bad support for kerning and ligatures). Furthermore, math is both time consuming and difficult to input, and tends to look very ugly. In general, a report written in Word looks like a draft.

It is strongly recommended to use Latex. Unless you tweak the layout too much, your report will almost certainly look very good. Although it can take a bit of effort to get started, it is also much quicker to use than Word and similar programs. The support for math and vector graphics is also great.

If you are new to Latex, you can have a look at the source for this document to get started. You can also look at the presentation by~\cite{Berland2010} (in Norwegian) or consult~\cite{Oetiker2011}. Another good reason to learn Latex is that you probably don't want to write your master's thesis in something like Word, doing so would likely be very frustrating. Being reasonably fluent in Latex before you get that far will make your thesis work much smoother.

Some of you are probably fluent in Latex and might plan to write the report using it. Please resist the temptation (if any) to change the fonts, make super fancy headers (they are not necessary for a report like this), change the margins, change the paragraph indentation and/or spacing, and similar things.

A great tool for collaborating on Latex documents is ShareLaTeX at \url{https://www.sharelatex.com/}; if you use this you won't have to install anything on your computer. Texmaker at \url{http://www.xm1math.net/texmaker/} is a good cross-platform editor. Some people like Lyx, which is a Latex editor that behaves a little bit like Word. If you prefer to compile your Latex document on the command line, the latexmk \url{https://www.ctan.org/pkg/latexmk} command is a great tool included in most TeX distributions. There is also a simple Vim plugin that uses latexmk as its backend called LaTeX-BoX \url{https://github.com/LaTeX-Box-Team/LaTeX-Box}.

\subsection{Other Comments}
Unless you have a very good reason not to, you should write the report in English. If you have problems with Latex, the solution is usually just a few Google searches away.

This report is organized as follows: \Cref{sec:prob_descr} contains some course specific equations, and some tips on how to create illustrations. Several \LaTeX{} tips can be found in \Cref{sec:latex_tips}, such as how to create a table and matrix equations. \Cref{sec:figures} contains some advice on using plots from MATLAB\@. The closing remarks are in~\Cref{sec:conclusion}, respectively. \Cref{sec:matlab} contains a MATLAB file while \Cref{sec:simulink} shows an example Simulink diagram. The Bibliography can be found at the end, on page~\pageref{sec:bibliography}.

## Alignment and Figures
You should have a section that describes the lab setup, including a model of the helicopter. If you want, you can copy the source code for the model equations:
\begin{gather}
	\ddot{e} + K_{3} K_{ed} \dot{e} + K_{3} K_{ep} e = K_{3} K_{ep} e_{c} \label{eq:model_elev} \\
	\ddot{p} + K_{1} K_{pd} \dot{p} + K_{1} K_{pp} p = K_{1} K_{pp} p_{c} \label{eq:model_pitch} \\
	\dot{\lambda} = r \label{eq:model_lambda} \\
	\dot{r} = -K_{2} p \label{eq:model_r} 
\end{gather}
Since these equations belong together, it's a good idea to number them like this:
\begin{subequations}\label{eq:model}
	\begin{gather}
		\ddot{e} + K_{3} K_{ed} \dot{e} + K_{3} K_{ep} e = K_{3} K_{ep} e_{c} \label{eq:model_se_elev} \\
		\ddot{p} + K_{1} K_{pd} \dot{p} + K_{1} K_{pp} p = K_{1} K_{pp} p_{c} \label{eq:model_se_pitch} \\
		\dot{\lambda} = r \label{eq:model_se_lambda} \\
		\dot{r} = -K_{2} p \label{eq:model_se_r} 
	\end{gather}
\end{subequations}
You can then both reference individual equations (``the elevation equation \Cref{eq:model_se_elev}'') or reference the entire model (``the linear model~\Cref{eq:model}''). Regardless of your choice of software, never hard-code a reference, always use dynamic references. 

You could also align the equations like this:
\begin{subequations}\label{eq:model_al}
	\begin{align}
		\ddot{e} + K_{3} K_{ed} \dot{e} + K_{3} K_{ep} e &= K_{3} K_{ep} e_{c} \label{eq:model_se_al_elev} \\
		\ddot{p} + K_{1} K_{pd} \dot{p} + K_{1} K_{pp} p &= K_{1} K_{pp} p_{c} \label{eq:model_se_al_pitch} \\
		\dot{\lambda} &= r \label{eq:model_se_al_lambda} \\
		\dot{r} &= -K_{2} p \label{eq:model_se_al_r} 
	\end{align}
\end{subequations}
You can consult~\cite{Downes2002} for more about writing math.


\subsection{Illustrations}
If you decide to include an illustration, that's great. You can in general copy figures and illustrations from the textbook, the assignement text, or other places. However: ALWAYS CITE THE SOURCE\@. You can also draw your own (cite the source if it is heavily based on someone else's.). \Cref{fig:layers_openloop,fig:heli} was created quickly with Ipe (\url{http://ipe.otfried.org/}). Inkscape is a good alternative for more advanced illustrations. Some people prefer the Latex package TikZ (\url{http://texample.net/tikz/examples/}), but this takes a little effort to learn.

\begin{figure}[tp]
	\centering
	\includegraphics[width=1.00\textwidth]{figures/layers_openloop.pdf}
	\caption{A figure created with Ipe for TTK4135.}
\label{fig:layers_openloop}
\end{figure}

\begin{figure}[tp]
	\centering
	\includegraphics[width=1.00\textwidth]{figures/forces.pdf}
	\caption{A figure created with Ipe for TTK4115.}
\label{fig:heli}
\end{figure}

## Tables and such
Some tips were given in \Cref{sec:intro}, and this section will elaborate with some more concrete examples.

\subsection{Matrix Equations}
Here is a matrix equation you can use as a template:
\begin{equation}
	\begin{bmatrix}
		1 &  0 &  0 & 0 & -b &  0 &  0 &  0 \\
		-a &  1 &  0 & 0 &  0 & -b &  0 &  0 \\
		0 & -a &  1 & 0 &  0 &  0 & -b &  0 \\
		0 &  0 & -a & 1 &  0 &  0 &  0 & -b                                
	\end{bmatrix}
	\begin{bmatrix} x_1 \\ x_2 \\ x_3 \\ x_4 \\ u_0 \\ u_1 \\ u_2 \\ u_3 \end{bmatrix}
	=
	\begin{bmatrix}
		ax_0 \\ 0 \\ 0 \\ 0      
	\end{bmatrix}
\end{equation}

\subsection{Tables}
If you want, you can use the source for \Cref{tab:parameters} to see how a (floating) table is made. 

Variables and symbols are always in italics, while units are not.

\begin{table}[tbp]
	\centering
	\caption{Parameters and values.}
	\begin{tabular}{llll}
		\toprule
		Symbol & Parameter & Value & Unit \\
		\midrule
		$l_a$ & Distance from elevation axis to helicopter body & $0.63$  & \meter                      \\
		$l_h$ & Distance from pitch axis to motor               & $0.18$  & \meter                      \\
		$K_f$ & Force constant motor                            & $0.25$  & \newton\per\volt            \\
		$J_e$ & Moment of inertia for elevation                 & $0.83$  & \kilogram\usk\meter\squared \\
		$J_t$ & Moment of inertia for travel                    & $0.83$  & \kilogram\usk\meter\squared \\
		$J_p$ & Moment of inertia for pitch                     & $0.034$ & \kilogram\usk\meter\squared \\
		$m_h$ & Mass of helicopter                              & $1.05$  & \kilogram                   \\
		$m_w$ & Balance weight                                  & $1.87$  & \kilogram                   \\
		$m_g$ & Effective mass of the helicopter                & $0.05$  & \kilogram                   \\
		$K_p$ & Force to lift the helicopter from the ground    & $0.49$  & \newton                     \\
		\bottomrule
	\end{tabular}
\label{tab:parameters}
\end{table}

\subsection{The \texMacro{input}{} command}
By using \texMacro{input}{whatever} in your main tex file (\texttt{labreport.tex} in this case), the content of \texttt{whatever.tex} will be included in your pdf. This way you can split the contents into different files, e.g.~one for each problem of the assignment. This makes it easier to restructure the document, and arguably improves the readability of the tex files. For instance; maybe you want each problem to start on a new page? Simply add \textbackslash{newpage} before each \texMacro{input}{} command. Alternatively, you can use the \texMacro{include}{} command to achieve more or less the same effect. See~\cite{InputVsInclude} for more information.

\subsection{Citations and Reference Management}
In academic writing, it is very important to cite your sources. In Latex this is done by defining an an entry in a \emph{BibTeX} bibliography file like this (from \texttt{bibliography.bib}):
\lstinputlisting[language=Tex, firstline=1, lastline=7]{bibliography.bib}
and then using the \texttt{\textbackslash{cite}} command in your Latex document. For instance \texttt{\textbackslash{cite}\{Chen2014\}} will produce~\cite{Chen2014}.

There are many different citation styles, and a lot of customization that is possible, so please check out e.g.~\cite{BiberBibtexEtc,WikibookLatex}\footnote{Keep citation of web pages to a minimum, and consider using \url{http://web.archive.org} if you are worried that the reference may change or be removed in the future.}.

There is also a lot of useful software to manage your references. Some popular examples include JabRef (\url{http://www.jabref.org/}), Mendeley (\url{https://www.mendeley.com/}) and EndNote. JabRef is perhaps the simplest of these three, and stores all information in a \texttt{.bib} file that you can directly use in your Latex document. Both Mendeley and EndNote can export references as BibTeX.


## Notes
Remember: all plots and results need a description, explanation, and discussion.