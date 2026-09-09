# LaTeX Template

## Department of Applied Geomatics, Université de Sherbrooke

Template originally built by **Philippe Apparicio**, Full Professor, Department of Applied Geomatics, Université de Sherbrooke. This copy has been emptied of sample content and adapted for a **doctoral thesis by articles written in English** (with the French résumé kept, as required by UdeS graduate studies regulations). It is optimized for compilation on **Overleaf** (LaTeX) with the **XeLaTeX** or **pdfLaTeX** engine.

------------------------------------------------------------------------

## Project structure

```
phd_thesis/
│
├── main.tex                          ← Main file (compile this one)
├── bibliography.bib                  ← Bibliography database (BibTeX format)
│
├── auxiliary/
│   └── acronyms.tex                  ← Abbreviations and acronyms
│
├── front_matter/
│   ├── title_page.tex                ← Title page
│   ├── jury.tex                      ← Jury page
│   ├── epigraph.tex                  ← Opening quote (optional)
│   ├── abstract_resume.tex           ← Abstract (English) + Résumé (French, mandatory)
│   ├── acknowledgements.tex          ← Acknowledgements (optional)
│   ├── foreword.tex                  ← Foreword (mandatory for a thesis by articles)
│   ├── ai_declaration.tex            ← Declaration on the use of generative AI
│   └── symbols_and_formulas.tex      ← List of symbols (optional)
│
├── chapters/
│   ├── _part_I.tex
│   ├── _part_II.tex
│   ├── _part_III.tex
│   ├── 1_introduction.tex
│   ├── 2_literature_review.tex
│   ├── 3_methodology.tex
│   ├── 4_article_1.tex
│   ├── 5_article_2.tex
│   ├── 6_discussion.tex
│   ├── 7_conclusion.tex
│   └── appendices.tex
│
├── figures/                          ← Images and figures (PNG, PDF, JPG)
│
├── logos_udes/                       ← Official UdeS logos (do not modify)
│
└── scripts/                          ← Code scripts (R, Python, JavaScript, C, MATLAB)
```

------------------------------------------------------------------------

## Quick start on Overleaf

1. Upload the project folder (as a `.zip`) to [Overleaf](https://www.overleaf.com) via *New Project → Upload Project*.
2. Overleaf automatically detects `main.tex` as the main file.
3. Compile with **pdfLaTeX** (recommended: Menu → Settings → Compiler → pdfLaTeX).

------------------------------------------------------------------------

## Title page customization

In `front_matter/title_page.tex`, two banner options are available:

``` latex
\bolBandeaufalse   % Option 2: dark banner with logo inside it (default)
\bolBandeautrue    % Option 1: UdesFierte banner with logo beside it
```

Also update in this same file: the **title**, the **author's name**, the **degree mention**, the **date**, and the **copyright**.

------------------------------------------------------------------------

## Font

By default, the font is **Libertine**. To change it, uncomment the corresponding line in `main.tex` (*Font configuration* section) and comment out `\usepackage{libertine}`:

``` latex
\usepackage{libertine}   % Libertine (default)
%\usepackage{ebgaramond} % EB Garamond
%\usepackage{newpxtext}  % Palatino
%\usepackage{newtxtext}  % Times New Roman
```

The math font must be changed **consistently** with the text font (section immediately below).

------------------------------------------------------------------------

## Bibliography

`bibliography.bib` holds the references in BibTeX format. The style used is **APA** via the `biblatex` package with the `biber` backend.

The bibliography is inserted and formatted automatically at the end of the document via `main.tex`.

To cite in the text:

``` latex
\parencite{key}              % (Author, year)
\textcite{key}                % Author (year)
\textcite[p.~12]{key}         % Author (year, p. 12)
```

------------------------------------------------------------------------

## Abbreviations and acronyms

Define your acronyms in `auxiliary/acronyms.tex`:

``` latex
\newacronym{ndvi}{NDVI}{Normalized Difference Vegetation Index}
```

Use them in the text:

``` latex
\gls{ndvi}    % first use: long form (acronym)
\gls{ndvi}    % subsequent uses: acronym only
\Gls{ndvi}    % capitalized
\glspl{ndvi}  % plural form
```

The list of abbreviations and acronyms is generated automatically.

------------------------------------------------------------------------

## Figures

``` latex
\begin{figure}[H]
    \centering
    \includegraphics[width=0.8\textwidth]{figures/figurename.png}
    \caption[Short caption for the list of figures]{Full caption with description.}
    \label{fig:label}
\end{figure}

% Reference in text:
(figure~\ref{fig:label})
```

Place your image files in the `figures/` folder. Accepted formats: PNG, PDF, JPG, EPS.

------------------------------------------------------------------------

## Tables

``` latex
\begin{table}[H]
    \centering
    \singlespacing
    \begin{threeparttable}
    \caption[Short caption]{Full caption.}
    \label{tab:label}
    \begin{tabular}{l c c}
    \hline
    \textbf{Col. A} & \textbf{Col. B} & \textbf{Col. C} \\
    \hline
    Text & Text & Text \\
    \hline
    \end{tabular}
    \begin{tablenotes}[flushleft]
        \small
        \item \textit{Note:} optional text.
    \end{tablenotes}
    \end{threeparttable}
\end{table}
```

------------------------------------------------------------------------

## Equations

``` latex
\begin{equation}
    \text{RMSE} = \sqrt{\frac{\sum_{i=1}^{n}(y_i - \hat{y}_i)^2}{n}}
    \label{eq:label}
\end{equation}

% Reference: (equation~\ref{eq:label})
```

------------------------------------------------------------------------

## Scripts and programs

Scripts are included via `\lstinputlisting` with the styles defined in `main.tex`. Place your files in `scripts/`:

``` latex
% R script
\begin{lstlisting}[style=styleR, caption={[Short caption]Full caption.}, label=code:label]
library(sf)
data <- st_read("map.shp")
\end{lstlisting}

% Or from an external file:
\lstinputlisting[style=stylePython, caption={[Short caption]Full caption.}, label=code:py1]
{scripts/CodePython1.py}
```

Available styles: `styleR`, `stylePython`, `styleJavascript`, `styleC`, `styleMATLAB`.

------------------------------------------------------------------------

## Algorithms

``` latex
\begin{algorithm}[H]
\DontPrintSemicolon
\KwIn{Input}
\KwOut{Output}
\For{each element}{
    do something\;
}
\caption{Algorithm name}
\label{algo:label}
\end{algorithm}

% Reference: (algorithm~\ref{algo:label})
```

------------------------------------------------------------------------

## Optional pages

In `main.tex`, comment out the corresponding lines to remove unwanted pages:

``` latex
\input{front_matter/acknowledgements}    % optional
\input{front_matter/symbols_and_formulas} % optional
```

The `ai_declaration.tex` page is **mandatory** under current UdeS regulations, and so is the French résumé in `abstract_resume.tex`.

------------------------------------------------------------------------

## Université de Sherbrooke colors

The official colors are defined in `main.tex` and available throughout the document:

| Name                      | Hex code | Typical use          |
|---------------------------|----------|-----------------------|
| `UdesReussiteContraste1`  | #11594B  | Hyperlinks, headers    |
| `UdesReussiteContraste2`  | #18463A  | Chapter titles         |
| `UdesReussite`            | #486A5C  | Secondary elements     |
| `UdesFierteAccessible`    | #018849  | Banner (option 1)      |
| `UdesViolet`              | #805286  | Quotations             |

Full reference: [UdeS Color Chart](https://www.usherbrooke.ca/communications/fileadmin/sites/communications/uploads/CharteCouleurs_Contrastes_UdeS.pdf)
