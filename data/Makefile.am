gsettings_SCHEMAS = io.github.Celluloid.gschema.xml io.github.GnomeMpv.gschema.xml

@GSETTINGS_RULES@

appstream_in_files = io.github.Celluloid.appdata.xml.in
appstream_XML = $(appstream_in_files:.xml.in=.xml)

%.appdata.xml: %.appdata.xml.in
	$(AM_V_GEN)$(MSGFMT) --xml --template $< -d $(top_srcdir)/po -o $@

@APPSTREAM_XML_RULES@

dbusservicedir = $(datadir)/dbus-1/services
dbusservice_in_files = io.github.Celluloid.service.in
dbusservice_DATA = $(dbusservice_in_files:.service.in=.service)

%.service: %.service.in Makefile
	$(AM_V_GEN) sed -e "s|\@bindir\@|$(bindir)|" $< > $@

desktopdir = $(datadir)/applications
desktop_in_files = io.github.Celluloid.desktop.in
desktop_DATA = $(desktop_in_files:.desktop.in=.desktop)

%.desktop: %.desktop.in
	$(AM_V_GEN)$(MSGFMT) --desktop --template $< -d $(top_srcdir)/po -o $@

icondir = $(datadir)/icons/hicolor/scalable/apps
icon_DATA = io.github.Celluloid.svg

symicondir = $(datadir)/icons/hicolor/symbolic/apps
symicon_DATA = io.github.Celluloid-symbolic.svg

EXTRA_DIST =	$(appstream_in_files) \
		$(desktop_in_files) \
		$(dbusservice_in_files) \
		io.github.Celluloid.svg \
		io.github.Celluloid-symbolic.svg \
		io.github.GnomeMpv.gschema.xml \
		io.github.Celluloid.gschema.xml \
		gmpv_mpris_gdbus.xml \
		gmpv_marshal.lst \
		meson.build

DISTCLEANFILES = $(appstream_XML) $(desktop_DATA) $(dbusservice_DATA)
