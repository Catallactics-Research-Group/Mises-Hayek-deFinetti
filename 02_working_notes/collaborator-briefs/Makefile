.PHONY: render clean help

QMD_FILES := brittany-michael-brief.qmd erin-emmy-brief.qmd jake-marc-brief.qmd
PDF_FILES := $(QMD_FILES:.qmd=.pdf)
MD_FILES  := $(QMD_FILES:.qmd=.md)

# Each `quarto render` produces both a PDF and a GFM markdown file
# from the same .qmd source. We track .pdf as the primary artifact;
# the .md is generated alongside as a side effect.

render: $(PDF_FILES)

%.pdf: %.qmd
	quarto render $<

clean:
	rm -f $(PDF_FILES) $(MD_FILES)

help:
	@echo "Usage: make [target]"
	@echo ""
	@echo "Each render produces both PDF and GitHub-flavored Markdown."
	@echo ""
	@echo "Targets:"
	@echo "  render  Render all three briefs (default; produces .pdf and .md)"
	@echo "  clean   Remove generated PDFs and Markdown files"
	@echo "  help    Show this help message"
