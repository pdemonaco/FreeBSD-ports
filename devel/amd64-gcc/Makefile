# $FreeBSD$

PORTREVISION=	1
PKGNAMEPREFIX=	amd64-
PLIST=	${.CURDIR}/pkg-plist

MASTERDIR=	${.CURDIR}/../powerpc64-gcc
GCC_TARGET=	x86_64-unknown-${OPSYS:tl}${OSREL}
BU_PREFIX=	x86_64-${OPSYS:tl}
FREEBSD_EXTENSION=	yes

BROKEN_aarch64=		invalid output constraint '=a' in assembler
BROKEN_armv6=		invalid output constraint '=a' in assembler
BROKEN_armv7=		invalid output constraint '=a' in assembler
BROKEN_mips=		configure: cannot compute suffix of object files: cannot compile
BROKEN_mips64=		configure: cannot compute suffix of object files: cannot compile
BROKEN_powerpc64=	invalid output constraint in assembler

.include "${MASTERDIR}/Makefile"
