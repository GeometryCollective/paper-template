PAPERNAME = template

all:
	pdflatex $(PAPERNAME)
	bibtex $(PAPERNAME)
	pdflatex $(PAPERNAME)
	open $(PAPERNAME).pdf

clean:
	rm -f $(PAPERNAME).pdf $(PAPERNAME).log $(PAPERNAME).aux $(PAPERNAME).bbl $(PAPERNAME).blg $(PAPERNAME).dvi $(PAPERNAME).ps $(PAPERNAME).out
