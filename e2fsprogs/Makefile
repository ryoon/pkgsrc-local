# $NetBSD: Makefile,v 1.17 2008/04/12 22:43:12 jlam Exp $

DISTNAME=	e2fsprogs-1.41.12
CATEGORIES=	sysutils
MASTER_SITES=	${MASTER_SITE_SOURCEFORGE:=e2fsprogs/}

MAINTAINER=	pkgsrc-users@NetBSD.org
HOMEPAGE=	http://e2fsprogs.sourceforge.net/
COMMENT=	Second extended file system (ext2fs) management programs

PKG_DESTDIR_SUPPORT=	user-destdir

GNU_CONFIGURE=	yes
USE_TOOLS+=	makeinfo gmake
INFO_FILES=	# PLIST

.include "../../mk/bsd.prefs.mk"

CONFIGURE_ARGS+=	--sysconfdir=${PKG_SYSCONFDIR:Q}

# Only build fsck(8) on platforms that need it.
PLIST_VARS+=		fsck
.if ${OPSYS} == "Linux"
PLIST.fsck=		yes
.else
CONFIGURE_ARGS+=	--disable-fsck
.endif

EGDIR=			${PREFIX}/share/examples/ext2fs
CONF_FILES+=		${EGDIR}/mke2fs.conf ${PKG_SYSCONFDIR}/mke2fs.conf
INSTALL_MAKE_FLAGS=	${MAKE_FLAGS} root_sysconfdir=${EGDIR:Q}

.include "../../mk/bsd.pkg.mk"
