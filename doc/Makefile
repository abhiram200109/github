BASEDIR = .
CLASSES = "$(BASEDIR)/classes/" "$(BASEDIR)/../modules/" "$(BASEDIR)/../platform/"
OUTPUTDIR = $(BASEDIR)/_build
TOOLSDIR = $(BASEDIR)/tools
JSDIR = "$(BASEDIR)/../platform/web"
LANGARG ?= en
LANGCMD = -l $(LANGARG)

.ONESHELL:

clean:
	rm -rf "$(OUTPUTDIR)"

doxygen:
	rm -rf "$(OUTPUTDIR)/doxygen"
	mkdir -p "$(OUTPUTDIR)/doxygen"
	doxygen Doxyfile

rst:
	rm -rf "$(OUTPUTDIR)/rst"
	mkdir -p "$(OUTPUTDIR)/rst"
	python3 "$(TOOLSDIR)/make_rst.py" -o "$(OUTPUTDIR)/rst" "$(LANGCMD)" $(CLASSES)

rstjs:
	rm -rf "$(OUTPUTDIR)/rstjs"
	mkdir -p "$(OUTPUTDIR)/rstjs"
	npm --prefix "$(JSDIR)" ci
	npm --prefix "$(JSDIR)" run docs -- --destination "$(OUTPUTDIR)/rstjs/html5_shell_classref.rst"
