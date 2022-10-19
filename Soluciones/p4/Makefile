PARS := -V geometry:margin=2cm

p4.pdf: $(wildcard ej*.md)
	pandoc ${PARS} $^ -o $@

%.pdf: %.md
	pandoc ${PARS} $< -o $@

clean:
	rm -f *.pdf