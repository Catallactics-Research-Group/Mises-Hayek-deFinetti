.PHONY: render pdf html gfm clean help

QMD_FILES  := readings-guide.qmd
PDF_FILES  := $(QMD_FILES:.qmd=.pdf)
HTML_FILES := $(QMD_FILES:.qmd=.html)
MD_FILES   := $(QMD_FILES:.qmd=.md)

# A bare `quarto render` produces all three formats (PDF, HTML, GFM
# markdown) from the same .qmd source. We track .pdf as the primary
# artifact; .html and .md are generated alongside as side effects.
# Format-specific targets (pdf/html/gfm) render only the named format.

render: $(PDF_FILES)

%.pdf: %.qmd
	quarto render $<

pdf:
	quarto render $(QMD_FILES) --to pdf

html:
	quarto render $(QMD_FILES) --to html

gfm:
	quarto render $(QMD_FILES) --to gfm

clean:
	rm -f $(PDF_FILES) $(HTML_FILES) $(MD_FILES)
	rm -rf readings-guide_files

help:
	@echo "Usage: make [target]"
	@echo ""
	@echo "A bare render produces PDF, HTML, and GitHub-flavored Markdown."
	@echo ""
	@echo "Targets:"
	@echo "  render  Render all formats (default; .pdf, .html, .md)"
	@echo "  pdf     Render PDF only"
	@echo "  html    Render HTML only"
	@echo "  gfm     Render GitHub-flavored Markdown only"
	@echo "  clean   Remove generated PDF, HTML, and Markdown files"
	@echo "  help    Show this help message"
