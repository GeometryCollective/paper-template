TARGET = SelfAvoiding
DIFFVERSION = c76f4a68dd05643a7f2218d2a0d919f7d34642b0

all:
	pdflatex $(TARGET)
	open $(TARGET).pdf

diff:
	git show $(DIFFVERSION):Paper/$(TARGET).tex > $(TARGET)_old.tex
	latexdiff --exclude-textcmd="section,subsection" $(TARGET)_old.tex $(TARGET).tex > diff.tex
	pdflatex diff
	bibtex diff
	pdflatex diff
	bibtex diff
	pdflatex diff
	open diff.pdf

bib:
	pdflatex $(TARGET)
	bibtex $(TARGET)
	pdflatex $(TARGET)
	bibtex $(TARGET)
	pdflatex $(TARGET)
	open $(TARGET).pdf

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
