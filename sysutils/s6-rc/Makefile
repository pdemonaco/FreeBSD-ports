# Created by: Andris Raugulis <moo@arthepsy.eu>
# $FreeBSD$

PORTNAME=	s6-rc
PORTVERSION=	0.4.0.0
CATEGORIES=	sysutils
MASTER_SITES=	http://www.skarnet.org/software/${PORTNAME}/

MAINTAINER=	moo@arthepsy.eu
COMMENT=	skarnet.org service manager

LICENSE=	ISCL

BUILD_DEPENDS=	execline>=2.1.4.5:lang/execline
RUN_DEPENDS=	execlineb:lang/execline
LIB_DEPENDS=	libs6.so:sysutils/s6 \
		libskarnet.so:devel/skalibs

USES=		gmake

USE_LDCONFIG=	yes
HAS_CONFIGURE=	yes
CONFIGURE_ARGS+=--prefix=${PREFIX} \
	--with-include=${LOCALBASE}/include \
	--with-lib=${LOCALBASE}/lib/skalibs \
	--with-lib=${LOCALBASE}/lib/execline \
	--with-lib=${LOCALBASE}/lib/s6 \
	--with-dynlib=${LOCALBASE}/lib \
	--enable-shared

DOCS=		AUTHORS COPYING INSTALL README doc/*.html
OPTIONS_DEFINE=	DOCS

post-install:
.for d in bin libexec
	${STRIP_CMD} ${STAGEDIR}${PREFIX}/${d}/*
.endfor
	${STRIP_CMD} ${STAGEDIR}${PREFIX}/lib/libs6rc.so.${PORTVERSION}
	@${MKDIR} ${STAGEDIR}${DOCSDIR}
	cd ${WRKSRC} && ${INSTALL_DATA} ${DOCS} ${STAGEDIR}${DOCSDIR}

.include <bsd.port.mk>
