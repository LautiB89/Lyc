PARS := -V geometry:margin=2cm

p3.pdf: $(wildcard ej*.md)
	pandoc ${PARS} $^ -o $@

%.pdf: %.md
	pandoc ${PARS} $< -o $@

clean:
	rm -f *.pdf