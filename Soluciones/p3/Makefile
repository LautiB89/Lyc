PARS := -V geometry:margin=2cm

%: %.md
	pandoc ${PARS} $< -o $@.pdf

clean:
	rm -f ej*.pdf