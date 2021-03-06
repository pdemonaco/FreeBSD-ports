# Created by: Frank Laszlo <laszlof@vonostingroup.com>
# $FreeBSD$

PORTNAME=	taglib
PORTVERSION=	1.11.1
CATEGORIES=	audio
MASTER_SITES=	http://taglib.github.io/releases/

MAINTAINER=	jhale@FreeBSD.org
COMMENT=	Library for manipulating ID3 tags and Ogg comments

LICENSE=	LGPL21 MPL11
LICENSE_COMB=	dual
LICENSE_FILE_LGPL21=	${WRKSRC}/COPYING.LGPL
LICENSE_FILE_MPL11=	${WRKSRC}/COPYING.MPL

USES=		cmake cpe pathfix
CMAKE_ARGS=	-DWITH_ASF:BOOL=ON \
		-DWITH_MP4:BOOL=ON \
		-DBUILD_SHARED_LIBS:BOOL=ON

USE_LDCONFIG=	yes

CPE_VENDOR=	scott_wheeler

OPTIONS_DEFINE=	RCC
OPTIONS_SUB=	yes

# The official patches for this can be obtained from:
#   http://darksoft.org/files/rusxmms/patches/
# however, they do not seem to yet have any for taglib-1.11.1.
# So instead, use:
#   https://sourceforge.net/p/qmmp-dev/code/HEAD/tree/trunk/extras/package/win32/contrib/taglib-rusxmms/
#
RCC_DESC=		Build with RusXMMS librcc patches (experimental)
RCC_LIB_DEPENDS=	librcc.so:devel/librcc
RCC_EXTRA_PATCHES=	${FILESDIR}/extrapatch-rcc
RCC_CFLAGS=		-I${LOCALBASE}/include
RCC_LDFLAGS=		-L${LOCALBASE}/lib

post-patch-RCC-on:
	@${REINPLACE_CMD} -e 's|-ltag|-ltag -lrcc|g' \
		${WRKSRC}/taglib.pc.cmake ${WRKSRC}/taglib-config.cmake
	@${REINPLACE_CMD} -e 's|-ltag_c|-ltag_c -lrcc|g' \
		${WRKSRC}/bindings/c/taglib_c.pc.cmake

.include <bsd.port.mk>
