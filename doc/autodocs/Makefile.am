# Makefile.am for y2m_inst/doc/autodocs

htmldir = $(docdir)/autodocs

html_DATA = $(wildcard *.html)
CLEANFILES = $(html_DATA)

all-local: index.html

# Note that we look one _and_ two subdirectories deep.
# There might be some duplicate filenames
# but let's solve that later. For now we want to find all Modules::.
index.html: $(srcdir)/../../src/*/*.ycp
	${YCPDOC} -d. $^

