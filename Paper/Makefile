TARGET = template

all:
	pdflatex $(TARGET)
	open $(TARGET).pdf

bib:
	pdflatex $(TARGET)
	bibtex $(TARGET)
	pdflatex $(TARGET)
	bibtex $(TARGET)
	pdflatex $(TARGET)
	open $(TARGET).pdf

clean:
	rm -f $(TARGET).pdf
	rm -f *.aux
	rm -f *.bbl
	rm -f *.blg
	rm -f *.log
	rm -f *.out
	rm -f *.cut
