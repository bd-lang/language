NAME=bdLangSpec
SPEC=$(NAME).tex
HASH=$(NAME)-hash.tex
LIST=$(NAME)-list.txt
HASHER=scripts/addlatexhash.bd

pdf:
	pdflatex $(SPEC)
	makeindex $(NAME).idx
	pdflatex $(SPEC)
	makeindex $(NAME).idx
	pdflatex $(SPEC)
	pdflatex $(SPEC)

pdfhash: hash_and_list
	pdflatex $(HASH)
	makeindex $(NAME)-hash.idx
	pdflatex $(HASH)
	makeindex $(NAME)-hash.idx
	pdflatex $(HASH)
	pdflatex $(HASH)

dvi:
	latex $(SPEC)
	makeindex $(NAME).idx
	latex $(SPEC)
	makeindex $(NAME).idx
	latex $(SPEC)
	latex $(SPEC)

dvihash: hash_and_list
	latex $(HASH)
	makeindex $(NAME)-hash.idx
	latex $(HASH)
	makeindex $(NAME)-hash.idx
	latex $(HASH)
	latex $(HASH)

hash_and_list:
	bd $(HASHER) $(SPEC) $(HASH) $(LIST)

help:
	@echo "Goals:"
	@echo "  pdf, dvi: generate the pdf/dvi file containing the spec"
	@echo "  pdfhash, dvihash: ditto, with location markers filled in"
	@echo "  cleanish: remove [pdf]latex generated intermediate files"
	@echo "  clean: remove all generated files"

cleanish:
	rm -f *.aux *.log *.toc *.out *.idx *.ilg *.ind

clean: cleanish
	rm -f *.dvi *.pdf $(HASH) $(LIST)
