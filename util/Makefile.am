#
# Generic options
#
AM_CFLAGS = $(C_GENFLAGS) $(C_OPTFLAGS) $(GLIB_CFLAGS)
AM_LDFLAGS = -pthread
AM_CPPFLAGS = $(CPP_GENFLAGS)
LDADD = $(GLIB_LIBS) -ldsme -lrt

ACLOCAL_AMFLAGS = -I m4

#
# Build targets
#
sbin_PROGRAMS = dsmetool    \
                bootstate   \
                waitfordsme

sbin_SCRIPTS = dsmetemperature

noinst_PROGRAMS = dsmereboot

dsmetool_SOURCES = dsmetool.c

bootstate_SOURCES = bootstate.c

waitfordsme_SOURCES = waitfordsme.c

dsmereboot_SOURCES = dsmereboot.c
