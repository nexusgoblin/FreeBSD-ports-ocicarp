PORTNAME=	migrate
DISTVERSION=	5.0.6
CATEGORIES=	biology
MASTER_SITES=	https://peterbeerli.com/migrate-html5/download_version4/
DISTNAME=	${PORTNAME}-${PORTVERSION}.src

MAINTAINER=	eduardo@FreeBSD.org
COMMENT=	Program to estimate population sizes and migration rates
WWW=		https://popgen.sc.fsu.edu/Migrate/Migrate-n.html

LICENSE=	MIT
LICENSE_FILE=	${WRKSRC}/../README

# Waiting on build reports, 2024-03-27
#BROKEN_armv6=	fails to build: make[2]: cannot open makefile
#BROKEN_armv7=	fails to build: make[2]: cannot open makefile
#BROKEN_mips=	fails to build: make[2]: cannot open makefile
#BROKEN_riscv64=	fails to build: make[2]: cannot open makefile

GNU_CONFIGURE=	yes
CONFIGURE_ENV=	ac_cv_prog_GMAKE="${MAKE}"
MAKE_ARGS=	PRETTYCFLAGS="${CFLAGS} -DNOJPEG -DNOZLIB -DNOPNG -Iharu -DPRETTY -lstdc++"

CONFLICTS_INSTALL=	py*-sqlalchemy-migrate # bin/migrate

EXTRACT_AFTER_ARGS=	--no-same-owner --no-same-permissions --exclude zlib
WRKSRC=		${WRKDIR}/${PORTNAME}-${PORTVERSION}/src

PORTDOCS=	${PORTNAME}.html HISTORY README README_PARALLEL_GENERAL
PORTEXAMPLES=	*

OPTIONS_DEFINE=		DOCS EXAMPLES THREAD
THREAD_DESC=		Build with THREAD support
THREAD_ALL_TARGET=	thread

# Upstream tarball contains objects and binaries that need to be clean
post-extract:
	cd ${WRKSRC} && ${RM} -f *.o haru/*.o migrate-n migrate-n-mpi

post-patch:
	@${REINPLACE_CMD} -e 's|="-O "|="$$CFLAGS"|g' ${WRKSRC}/configure
	@${REINPLACE_CMD} -e '/PRETTY$$/d' ${WRKSRC}/src/definitions.h
	@${REINPLACE_CMD} -e 's|-O3||g' ${WRKSRC}/haru/makefile.gcc

do-install:
	${INSTALL_PROGRAM} ${WRKSRC}/${PORTNAME}-n ${STAGEDIR}${PREFIX}/bin
	${LN} -sf ${PORTNAME}-n ${STAGEDIR}${PREFIX}/bin/${PORTNAME}
	${INSTALL_MAN} ${WRKSRC}/${PORTNAME}.1 \
		${STAGEDIR}${PREFIX}/share/man/man1
	${LN} -sf ${PORTNAME}.1 \
		${STAGEDIR}${PREFIX}/share/man/man1/${PORTNAME}-n.1

do-install-DOCS-on:
	@${MKDIR} ${STAGEDIR}${DOCSDIR}
	${INSTALL_DATA} ${PORTDOCS:S,^,${WRKSRC}/../,} ${STAGEDIR}${DOCSDIR}
	@${MKDIR} ${STAGEDIR}${DOCSDIR}/graphics
	${INSTALL_DATA} ${WRKSRC}/../graphics/* ${STAGEDIR}${DOCSDIR}/graphics

do-install-EXAMPLES-on:
	@${MKDIR} ${STAGEDIR}${EXAMPLESDIR}
	${INSTALL_DATA} ${WRKSRC}/../example/[A-Za-z]* \
		${STAGEDIR}${EXAMPLESDIR}

.include <bsd.port.mk>
