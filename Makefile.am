osname=$(subst ganeti-instance-,,$(PACKAGE))

osdir=$(datadir)/ganeti/os/$(osname)

os_SCRIPTS = create
dist_os_SCRIPTS = import export rename
dist_os_DATA = ganeti_api_version

dist_doc_DATA = COPYING NEWS README

EXTRA_DIST = create.in

do_subst = sed -e 's,[@]sysconfdir[@],$(sysconfdir),g'

create: create.in Makefile
	$(do_subst) < $< > $@
	chmod +x $@

CLEANFILES = create