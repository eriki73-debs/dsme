#
# Generic options
#
ACLOCAL_AMFLAGS = -I m4
AM_CFLAGS = $(C_GENFLAGS) $(C_OPTFLAGS) $(DBUS_CFLAGS) $(GLIB_CFLAGS)
AM_LDFLAGS = -Wl,--as-needed -pthread -rdynamic $(GLIB_LIBS) -ldsme -ldbus-1 -lpthread -ldl -ldsme -lcryptsetup
AM_CPPFLAGS = $(CPP_GENFLAGS) $(GLIB_CFLAGS) $(DBUS_CFLAGS)
TESTS = testmod_alarmtracker \
	testmod_emergencycalltracker \
	testmod_state \
	testmod_usbtracker

#
# Build targets
#
noinst_PROGRAMS = batttest \
		dsmetest \
		dummy_bme \
		processwdtest \
		testmod_alarmtracker \
		testmod_emergencycalltracker \
		testmod_state \
                testmod_usbtracker \
		abnormalexitwrapper_tester

pkglib_LTLIBRARIES = libabnormalexitwrapper.la

batttest_SOURCES = batttest.c

dummy_bme_SOURCES = dummy_bme.c

dsmetest_SOURCES = dsmetest.c

processwdtest_SOURCES = processwdtest.c

# FIXME: including .o files is quite hackish

testmod_alarmtracker_SOURCES = testmod_alarmtracker.c
testmod_alarmtracker_LDADD = ../dsme/dsme_server-logging.o \
                   ../dsme/dsme_server-utility.o \
                   ../dsme/dsme_server-mainloop.o

testmod_emergencycalltracker_SOURCES = testmod_emergencycalltracker.c
testmod_emergencycalltracker_LDADD = ../dsme/dsme_server-logging.o \
                                     ../dsme/dsme_server-utility.o \
                                     ../dsme/dsme_server-mainloop.o

testmod_state_SOURCES = testmod_state.c
testmod_state_LDADD = ../dsme/dsme_server-dsmesock.o \
                   ../dsme/dsme_server-logging.o \
                   ../dsme/dsme_server-utility.o \
                   ../dsme/dsme_server-mainloop.o \
                   ../dsme/dsme_server-dsme-rd-mode.o

testmod_usbtracker_SOURCES = testmod_usbtracker.c
testmod_usbtracker_LDADD = ../dsme/dsme_server-logging.o \
                           ../dsme/dsme_server-utility.o \
                           ../dsme/dsme_server-mainloop.o

abnormalexitwrapper_tester_SOURCES = abnormalexitwrapper_tester.c

libabnormalexitwrapper_la_SOURCES = abnormalexitwrapper.c
libabnormalexitwrapper_la_LDFLAGS = -pthread -module -avoid-version -shared -ldl
