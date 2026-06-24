TARGET = Paper
DIFFVERSION = ec5b098c7d94af43d6f36769d1908138a74b45a6

all:
	pdflatex $(TARGET)
	if type open > /dev/null; then open $(TARGET).pdf; fi

diff:
	git show $(DIFFVERSION):Paper/$(TARGET).tex > $(TARGET)_old.tex
	latexdiff --exclude-textcmd="section,subsection" $(TARGET)_old.tex $(TARGET).tex > diff.tex
	pdflatex diff
	bibtex diff
	pdflatex diff
	bibtex diff
	pdflatex diff
	if type open > /dev/null; then open diff.pdf; fi

bib:
	pdflatex $(TARGET)
	bibtex $(TARGET)
	pdflatex $(TARGET)
	bibtex $(TARGET)
	pdflatex $(TARGET)
	if type open > /dev/null; then open $(TARGET).pdf; fi

clean:
	rm -f $(TARGET).pdf
	rm -f $(TARGET)_old.tex
	rm -f diff.tex
	rm -f diff.pdf
	rm -f *.aux
	rm -f *.bbl
	rm -f *.blg
	rm -f *.log
	rm -f *.out
	rm -f *.cut
	rm -f *.upa
	rm -f *.upb
