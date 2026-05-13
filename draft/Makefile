.PHONY: all pdf html clean help

# Variables
QMD = proposal-short.qmd
BIB = biblio.bib
PDF = proposal-short.pdf
HTML = proposal-short.html

# Default target
all: pdf html

pdf: $(PDF)

html: $(HTML)

$(PDF): $(QMD) $(BIB)
	quarto render $(QMD) --to pdf

$(HTML): $(QMD) $(BIB)
	quarto render $(QMD) --to html

clean:
	@rm -f $(PDF) $(HTML) proposal-short.log
	@rm -rf proposal-short_files

help:
	@echo "Usage: make [target]"
	@echo "  all    - Build all formats (pdf, html). Default."
	@echo "  pdf    - Build PDF."
	@echo "  html   - Build HTML."
	@echo "  clean  - Remove generated files."
	@echo "  help   - Show this help message."
