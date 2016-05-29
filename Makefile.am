osname=$(subst ganeti-instance-,,$(PACKAGE))

osdir=$(OS_DIR)/$(osname)
variantsdir=$(DESTDIR)$(sysconfdir)/ganeti/instance-debootstrap/variants
defaultsdir=$(DESTDIR)$(sysconfdir)/default

dist_os_SCRIPTS = create import export rename verify
dist_os_DATA = ganeti_api_version variants.list parameters.list
os_DATA = common.sh

dist_doc_DATA = COPYING NEWS README

exampledir = $(docdir)/examples
exampleconfdir = $(exampledir)/confdata

dist_exampleconf_DATA = \
	examples/hooks/confdata/defaultpasswords \
	examples/hooks/confdata/timezone

dist_example_DATA = \
	examples/hooks/defaultpasswords \
	examples/hooks/grub \
	examples/hooks/hosts \
	examples/hooks/interfaces \
	examples/hooks/ssh-keys \
	examples/hooks/timezone

EXTRA_DIST = \
	common.sh.in \
	defaults \
	$(TESTS)

do_subst = sed \
	-e 's,[@]sysconfdir[@],$(sysconfdir),g' \
	-e 's,[@]localstatedir[@],$(localstatedir),g'

common.sh: common.sh.in Makefile
	$(do_subst) < $< > $@

TESTS = \
	test/install-export-import

install-exec-local:
	@mkdir_p@ $(variantsdir)
	touch $(variantsdir)/default.conf
	@mkdir_p@ $(defaultsdir)
	$(INSTALL_DATA) $(top_srcdir)/defaults \
	  $(defaultsdir)/ganeti-instance-debootstrap

uninstall-local:
	rm -f $(variantsdir)/default.conf
	rm -f $(defaultsdir)/ganeti-instance-debootstrap

CLEANFILES = common.sh
