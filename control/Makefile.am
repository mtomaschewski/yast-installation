# Makefile.am for installation/general
#
SUBDIRS = docs tests examples

controldir = $(yast2dir)/control

control_DATA = \
	control.xml \
	control.rnc \
	control.rng

xml_files = \
	control.SLED.xml \
	control.SLES.xml \
	control.openSUSE.xml \
	add-on-template_installation.xml

# Note: The control.glade -> control.xml symlink is required to make xgettext
# auto-detect the type of this file (glade) so it will extract all
# <label>..</label> tags. The symlink is created in the toplevel
# configure.in.in file upon "autoconf" (via "make -f Makefile.cvs").
# Unfortunately, CVS doesn't support checking in symlinks - it would duplicate
# the file. 


EXTRA_DIST =  $(control_DATA) $(product_DATA) $(xml_files)

include $(top_srcdir)/Makefile.am.common

control.rng: control.rnc
	trang -I rnc -O rng control.rnc control.rng

# checks only those control files that belong to this package
check-local:
	trang -I rnc -O rng control.rnc control.rng
	xmllint --relaxng control.rng --noout control.xml
	xmllint --relaxng control.rng --noout $(xml_files)
