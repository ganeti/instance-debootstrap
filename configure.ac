AC_PREREQ(2.59)
AC_INIT(ganeti-instance-debootstrap, 0.15, ganeti@googlegroups.com)

AC_CONFIG_AUX_DIR(autotools)
AC_CONFIG_SRCDIR(configure)

AM_INIT_AUTOMAKE([1.11 foreign tar-ustar -Wall -Wno-portability])

# --with-os-dir=...
AC_ARG_WITH([os-dir],
  [AS_HELP_STRING([--with-os-dir=DIR],
    [top-level OS directory under which to install]
    [ (default is $datadir/ganeti/os)]
  )],
  [os_dir="$withval"],
  [os_dir="$datadir/ganeti/os"])
AC_SUBST(OS_DIR, $os_dir)

# Check common programs
AC_PROG_INSTALL
AC_PROG_LN_S

# Check for the required programs
ROOT_PATH=[$PATH$PATH_SEPARATOR/sbin$PATH_SEPARATOR/usr/sbin]dnl
[$PATH_SEPARATOR/usr/local/sbin]

AC_ARG_VAR(KPARTX, [kpartx path])
AC_PATH_PROG(KPARTX, [kpartx], [], [$ROOT_PATH])
if test -z "$KPARTX"
then
  AC_MSG_ERROR([kpartx command not found])
fi

AC_ARG_VAR(LOSETUP, [losetup path])
AC_PATH_PROG(LOSETUP, [losetup], [], [$ROOT_PATH])
if test -z "$LOSETUP"
then
  AC_MSG_ERROR([losetup command not found])
fi

AC_ARG_VAR(DEBOOTSTRAP, [debootstrap path])
AC_PATH_PROG(DEBOOTSTRAP, [debootstrap], [], [$ROOT_PATH])
if test -z "$DEBOOTSTRAP"
then
  AC_MSG_ERROR([debootstrap command not found])
fi

AC_ARG_VAR(DUMP, [dump path])
AC_PATH_PROG(DUMP, [dump], [], [$ROOT_PATH])
if test -z "$DUMP"
then
  AC_MSG_ERROR([dump command not found])
fi

AC_ARG_VAR(RESTORE, [restore path])
AC_PATH_PROG(RESTORE, [restore], [], [$ROOT_PATH])
if test -z "$RESTORE"
then
  AC_MSG_ERROR([restore command not found])
fi

AC_CONFIG_FILES([ Makefile ])

AC_OUTPUT
