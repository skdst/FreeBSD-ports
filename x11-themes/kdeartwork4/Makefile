# Created by: Martin Wilke <miwi@FreeBSD.org>
# $FreeBSD$

PORTNAME=	kdeartwork
PORTVERSION=	${KDE4_VERSION}
PORTREVISION=	2
CATEGORIES=	x11-themes kde kde-kde4

MAINTAINER=	kde@FreeBSD.org
COMMENT=	KDE Artworks Themes

USES=		cmake:outsource kde:4 tar:xz
USE_KDE=	kdelibs libkexiv2 workspace automoc4
USE_QT4=	corelib gui opengl \
		moc_build qmake_build rcc_build uic_build
USE_XORG=	x11 xt

OPTIONS_DEFINE=	GNOME
GNOME_DESC=	Use Gnome screensavers
GNOME_BUILD_DEPENDS=	${LOCALBASE}/share/applications/xscreensaver-properties.desktop:x11/xscreensaver-gnome
GNOME_RUN_DEPENDS=	${GNOME_BUILD_DEPENDS}
GNOME_BUILD_DEPENDS_OFF=	xscreensaver:x11/xscreensaver
GNOME_RUN_DEPENDS_OFF=		${GNOME_BUILD_DEPENDS_OFF}

# Do not look for eigen. Eigen3 dropped the eigen2 compatibility with 3.2+. 
CMAKE_ARGS=	-DCMAKE_DISABLE_FIND_PACKAGE_Eigen3:BOOL=TRUE

post-patch:
	${REINPLACE_CMD} -e 's|/usr/local/|${LOCALBASE}|g' \
			-e 's|/usr/share|${LOCALBASE}/share|g' \
		${PATCH_WRKSRC}/cmake/modules/FindXscreensaver.cmake

.include <bsd.port.mk>
