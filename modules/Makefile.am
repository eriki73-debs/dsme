#
# Generic options
#
AM_CFLAGS = $(C_GENFLAGS) $(C_OPTFLAGS) -fPIC
AM_LDFLAGS = -pthread -module -avoid-version -shared
AM_CPPFLAGS = $(CPP_GENFLAGS) -I$(top_srcdir) \
	$(GLIB_CFLAGS)
ACLOCAL_AMFLAGS = -I m4

pkglib_LTLIBRARIES = startup.la              \
                     heartbeat.la            \
                     state.la                \
                     processwd.la            \
                     dbusproxy.la            \
                     alarmtracker.la         \
                     thermalmanager.la       \
                     emergencycalltracker.la \
                     usbtracker.la           \
                     iphb.la                 \
                     thermalflagger.la       \
                     malf.la                 \
                     diskmonitor.la          \
                     dbusautoconnector.la

noinst_HEADERS = runlevel.h \
                 heartbeat.h \
                 thermalmanager.h \
                 state-internal.h

dsmeplugin_HEADERS = dbusproxy.h \
                     dsme_dbus.h

#
## Additional dirs
#
pkgsysconfdir = @sysconfdir@
dsmeplugindir = $(includedir)/dsme-plugin

if WANT_GENERIC_THERMAL_MGMT
pkglib_LTLIBRARIES += thermalsensor_generic.la
endif

if WANT_POWERON_TIMER
pkglib_LTLIBRARIES += powerontimer.la
endif

if WANT_RUNLEVEL
pkglib_LTLIBRARIES += runlevel.la
endif

if WANT_UPSTART
pkglib_LTLIBRARIES += upstart.la
endif

if WANT_VALIDATOR_LISTENER
pkglib_LTLIBRARIES += validatorlistener.la
endif

if WANT_PWRKEY_MONITOR
pkglib_LTLIBRARIES += pwrkeymonitor.la
endif

if WANT_BATTERY_TRACKER
pkglib_LTLIBRARIES += batterytracker.la
endif

if WANT_BOOTREASON_LOGGER
pkglib_LTLIBRARIES += bootreasonlogger.la
endif

if WANT_VIBRA_FEEDBACK
pkglib_LTLIBRARIES += shutdownfeedback.la
endif

if WANT_WLAN_LOADER
pkglib_LTLIBRARIES += wlanloader.la
endif

if WANT_ABOOTSETTINGS
pkglib_LTLIBRARIES += abootsettings.la
endif

startup_la_SOURCES = startup.c

heartbeat_la_SOURCES = heartbeat.c
state_la_SOURCES = state.c
state_la_CFLAGS = $(AM_CFLAGS) $(DBUS_CFLAGS)
state_la_LIBADD =
if WANT_VIBRA_FEEDBACK
state_la_SOURCES += vibrafeedback.c vibrafeedback.h
state_la_CFLAGS += $(LIBNGF_CFLAGS)
state_la_LIBADD += $(GLIB_LIBS) $(LIBNGF_LIBS) \
	$(top_srcdir)/dbus-gmain/libdbus-gmain.la
endif

if WANT_RUNLEVEL
runlevel_la_SOURCES = runlevel.c
endif

if WANT_UPSTART
upstart_la_SOURCES = upstart.c
upstart_la_CFLAGS = $(AM_CFLAGS) $(DBUS_CFLAGS)
upstart_la_LIBADD = $(DBUS_LIBS)
endif

if WANT_VALIDATOR_LISTENER
runlevel_la_SOURCES = validatorlistener.c
endif

processwd_la_SOURCES = processwd.c

dbusproxy_la_SOURCES = dbusproxy.c dsme_dbus.c
dbusproxy_la_CFLAGS = $(AM_CFLAGS) $(GLIB_CFLAGS) $(DBUS_CFLAGS)
dbusproxy_la_LIBADD = $(DBUSGLIB_LIBS) -ldsme_dbus_if \
	$(top_srcdir)/dbus-gmain/libdbus-gmain.la

alarmtracker_la_SOURCES = alarmtracker.c
alarmtracker_la_CFLAGS = $(AM_CFLAGS) $(DBUS_CFLAGS)
alarmtracker_la_CPPFLAGS = $(AM_CPPFLAGS)

thermalmanager_la_SOURCES = thermalmanager.c thermalobject.c
thermalmanager_la_CFLAGS = $(AM_CFLAGS) $(DBUS_CFLAGS)
thermalmanager_la_LIBADD = -lthermalmanager_dbus_if

emergencycalltracker_la_SOURCES = emergencycalltracker.c
emergencycalltracker_la_CFLAGS = $(AM_CFLAGS) $(DBUS_CFLAGS)

usbtracker_la_SOURCES = usbtracker.c
usbtracker_la_CFLAGS = $(AM_CFLAGS) $(DBUS_CFLAGS)
usbtracker_la_LIBADD = $(GLIB_LIBS) $(DBUS_LIBS)

iphb_la_SOURCES = iphb.c
iphb_la_CFLAGS = $(AM_CFLAGS) $(DBUS_CFLAGS) $(MCE_DEV_CFLAGS)
iphb_la_LIBADD = $(GLIB_LIBS) $(DBUS_LIBS)

thermalflagger_la_SOURCES = thermalflagger.c

malf_la_SOURCES = malf.c

if WANT_GENERIC_THERMAL_MGMT
thermalsensor_generic_la_SOURCES = thermalsensor_generic.c
thermalsensor_generic_la_CFLAGS  = $(AM_CFLAGS) $(DBUS_CFLAGS)
thermalsensor_generic_la_LIBADD  = -lthermalmanager_dbus_if
endif


if WANT_POWERON_TIMER
powerontimer_la_SOURCES = powerontimer.c         \
                             powerontimer_backend.c \
                             powerontimer.h         \
                             powerontimer_backend.h
powerontimer_la_LIBADD = -lcal -lrt
endif

diskmonitor_la_SOURCES = diskmonitor.c \
				diskmonitor.h

diskmonitor_la_CFLAGS = $(AM_CFLAGS) $(DBUS_CFLAGS)

dbusautoconnector_la_SOURCES = dbusautoconnector.c
dbusautoconnector_la_CFLAGS  = $(AM_CFLAGS) $(DBUS_CFLAGS)
dbusautoconnector_la_LIBADD  = $(GLIB_LIBS)

if WANT_PWRKEY_MONITOR
pwrkeymonitor_la_SOURCES = pwrkeymonitor.c
pwrkeymonitor_la_LIBADD = $(GLIB_LIBS)
endif

if WANT_BATTERY_TRACKER
batterytracker_la_SOURCES = batterytracker.c
batterytracker_la_CFLAGS  = $(AM_CFLAGS) $(DBUS_CFLAGS) $(MCE_DEV_CFLAGS)
batterytracker_la_LIBADD  = $(GLIB_LIBS)
endif

if WANT_BOOTREASON_LOGGER
bootreasonlogger_la_SOURCES = bootreasonlogger.c
bootreasonlogger_la_CFLAGS  = $(AM_CFLAGS) $(DBUS_CFLAGS)
bootreasonlogger_la_LIBADD  = $(GLIB_LIBS)
endif

if WANT_VIBRA_FEEDBACK
shutdownfeedback_la_SOURCES = shutdownfeedback.c vibrafeedback.c vibrafeedback.h
shutdownfeedback_la_CFLAGS  = $(AM_CFLAGS) $(DBUS_CFLAGS) $(LIBNGF_CFLAGS)
shutdownfeedback_la_LIBADD  = $(GLIB_LIBS) $(LIBNGF_LIBS)
endif

if WANT_WLAN_LOADER
wlanloader_la_SOURCES = wlanloader.c
wlanloader_la_CFLAGS = $(AM_CFLAGS) $(DBUS_CFLAGS)
endif

if WANT_ABOOTSETTINGS
abootsettings_la_SOURCES = abootsettings.c
abootsettings_la_CFLAGS  = $(AM_CFLAGS) $(DBUS_CFLAGS)
abootsettings_la_LIBADD  = $(GLIB_LIBS) $(DBUS_LIBS)
endif
