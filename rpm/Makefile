
all install check:
	echo "Nothing to see here"

distname = Mail-IMAPTalk
VERSION_FROM= ../IMAPTalk.pm
VERSION = our $VERSION = '2.01';
rpmdirs = BUILD RPMS SOURCES SRPMS SPECS

dist: _setup
	rpmbuild -bb --define "_topdir $(PWD)" SPECS/$(distname).spec

_setup:
	for d in $(rpmdirs) ; do \
	    [ -d $$d ] || mkdir $$d ; \
	done
	tarball=`ls -t ../$(distname)-*.tar.gz |head -1` ;\
	ln -snf ../$$tarball SOURCES
	version=`grep VERSION $(VERSION_FROM) | head -1 | sed -e 's/[^0-9.]//g' ` ;\
	sed -e "s/@VERSION@/$$version/g" \
	    < $(distname).spec.in \
	    > SPECS/$(distname).spec

clean:
	$(RM) -rf $(rpmdirs) $(distname)*.tar.gz

