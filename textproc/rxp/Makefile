PORTNAME=	rxp
PORTVERSION=	1.4.4
PORTREVISION=	4
CATEGORIES=	textproc
MASTER_SITES=	ftp://ftp.cogsci.ed.ac.uk/pub/richard/

MAINTAINER=	ports@virtual-estates.net
COMMENT=	Validating XML parser written in C
WWW=		https://www.cogsci.ed.ac.uk/~richard/rxp.html

LICENSE=	GPLv2

BROKEN=		Unfetchable
DEPRECATED=	Unfetchable and outdated
EXPIRATION_DATE=2024-12-31

USES=	uidfix

USE_LDCONFIG=	yes
PATCH_WRKSRC=	${WRKSRC}/${PORTNAME}-${PORTVERSION}
WRKSRC=		${WRKDIR}
MAKE_ARGS+=	VPATH=${PATCH_WRKSRC}

OPTIONS_SINGLE=	CHAR_SIZE
OPTIONS_SINGLE_CHAR_SIZE=8 16
OPTIONS_DEFAULT=8
8_DESC= 	8-bit characters (required by speech_tools, festival)
16_DESC=	16-bit characters

MAKE_ARGS+=	CHAR_SIZE=${PORT_OPTIONS:C/[^0-9]//g}

do-configure:
.for s in lib rxp
	${MKDIR} ${WRKDIR}/$s
	${LN} -s ${FILESDIR}/BSDmakefile.$s ${WRKDIR}/$s/Makefile
	${PRINTF} "SUBDIR+=\t%s\n" $s >> ${WRKDIR}/Makefile
.endfor
	${PRINTF} "\n.include <bsd.subdir.mk>\n" >> ${WRKDIR}/Makefile

post-build:
	${MKDIR} ${STAGEDIR}${PREFIX}/include/rxp

.include <bsd.port.mk>
