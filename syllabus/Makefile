## To build syllabus: 'make syllabus'

SHELL=/bin/bash

MAIN?=bayesian_modeling_workshop

clean:
	rm -fv *.zip *.aux *.log *.bbl *.blg *.toc *.out *.lot *.lof *.dvi *.ps *.pdf *.docx

clean_extras:
	rm -fv *.aux *.bbl *.blg *.toc *.out *.lot *.lof

syllabus: $(MAIN).pdf

$(MAIN).pdf: $(MAIN).bbl
	# Run 3x to get cross refs right
	# Ignore errors by piping on error to get status code 0
	pdflatex -interaction nonstopmode $(MAIN) || true
	pdflatex -interaction nonstopmode $(MAIN) || true
	pdflatex -interaction nonstopmode $(MAIN) && make clean_extras

$(MAIN).bbl: $(MAIN).tex
	pdflatex -interaction nonstopmode $(MAIN) || true
	bibtex $(MAIN)

