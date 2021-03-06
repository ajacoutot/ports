# $OpenBSD: Makefile,v 1.111 2018/07/06 06:04:47 espie Exp $

COMMENT=		remote desktop viewer for GNOME

GNOME_PROJECT=		vinagre
GNOME_VERSION=		3.22.0
REVISION=		8

CATEGORIES=		net

# GPLv3
PERMIT_PACKAGE_CDROM=	Yes

WANTLIB += X11 atk-1.0 avahi-client avahi-common avahi-glib avahi-gobject
WANTLIB += avahi-ui-gtk3 c cairo cairo-gobject dbus-1 dbus-glib-1
WANTLIB += freerdp2 fribidi gdk-3 gdk_pixbuf-2.0 gio-2.0
WANTLIB += glib-2.0 gnutls gobject-2.0 gthread-2.0 gtk-3 gtk-vnc-2.0
WANTLIB += gvnc-1.0 intl m pango-1.0 pangocairo-1.0 pthread secret-1
WANTLIB += spice-client-glib-2.0 spice-client-gtk-3.0 telepathy-glib
WANTLIB += util vte-2.91 xml2 z pcre2-8

MODULES=		devel/dconf \
			x11/gnome

LIB_DEPENDS=		devel/vte3 \
			net/avahi,,-gtk3 \
			net/telepathy/telepathy-glib \
			x11/freerdp \
			x11/gnome/libsecret \
			x11/gtk-vnc \
			x11/spice-gtk

MODGNOME_TOOLS=		desktop-file-utils gtk-update-icon-cache \
			shared-mime-info yelp

# for clang, because it catches non-constant formats in printf-like routines
CONFIGURE_ARGS +=	--enable-compile-warnings=minimum

CONFIGURE_STYLE=	gnu

.include <bsd.port.mk>
