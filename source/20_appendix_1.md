
\newpage
\newpage
\appendix
\renewcommand{\thechapter}{\Alph{chapter}}

# Apéndice 1: Título
\label{sec:A1}

The following tables contain the keys and elements of the JSONs produced from the metamodels in our parsing process. The meta-model is represented as a three leveled dictionary with the following elements.

\begin{center}
\begin{table}[h]
\begin{tabular}{ | m{7em} | m{15em} | m{7em} | } 
    \hline
    \textbf{Key} & \textbf{Value} & \textbf{Type} \\
    \hline
    \textbf{'name'} & Name of the metamodel & String \\ 
    \hline
    \textbf{'annotations'} & A list of annotations, this is usually empty, but it is intended to be filled with OCL restrictions and other relevant information. & List \\ 
    \hline
    \textbf{'classes'} & Class elements of the metamodel. & List of dictionaries \\ 
    \hline
    \textbf{'enums'} & A list of enumerates &  List of dictionaries. \\
    \hline
\end{tabular}
\caption{\label{tab:meta} The JSON object is a three level dictionary that contains the following keys (first level)}
\end{table}
\end{center}
