.PHONY: all test check dist clean distclean install uninstall
.PRECIOUS: Makefile

prefix = /opt/runtime/opting
mandir = $(prefix)/man
man1dir = $(mandir)/man1

all: optipng.man.txt optipng.man.ps optipng.man.pdf optipng.man.html

optipng.man.txt: optipng.1
	nroff -man -c -Tascii $< | col -b -x | uniq > $@

optipng.man.ps: optipng.1
	groff -man -Tps -P-g $< > $@

optipng.man.pdf: optipng.man.ps
	ps2pdf $< $@

optipng.man.html: optipng.1
	groff -man -Thtml -P-l $< > $@

test:

check:

dist: optipng.man.txt optipng.man.pdf optipng.man.html
	cp -f -p optipng.man.txt ../../../doc/
	cp -f -p optipng.man.pdf ../../../doc/
	cp -f -p optipng.man.html ../../../doc/

clean:
	rm -f optipng.man.txt
	rm -f optipng.man.ps
	rm -f optipng.man.pdf
	rm -f optipng.man.html

distclean: clean
	rm -f Makefile

install: optipng.1
	mkdir -p $(DESTDIR)$(man1dir)
	cp -f -p optipng.1 $(DESTDIR)$(man1dir)

uninstall:
	rm -f $(DESTDIR)$(man1dir)/optipng.1
