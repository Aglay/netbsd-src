#	$NetBSD: Makefile,v 1.7 2019/04/10 00:32:15 sevan Exp $

.include <bsd.own.mk>

CONFIGFILES=	daily.conf monthly.conf npf.boot.conf pkgpath.conf \
		    security.conf weekly.conf
FILESDIR=	/etc/defaults
FILESMODE=	${NONBINMODE}

# Manage arch-specific rc.conf(5) file
CONFIGFILES+=	rc_conf
FILESNAME_rc_conf=	rc.conf
FILESBUILD_rc_conf=	yes

# If present, rc.conf.append is added to the end of the default rc.conf file
RCCONF_SRCS=	${.CURDIR}/rc.conf
.if exists(../etc.${MACHINE}/rc.conf.append)
RCCONF_SRCS+=	${.CURDIR}/../etc.${MACHINE}/rc.conf.append
.endif

rc_conf: ${RCCONF_SRCS}
	${_MKTARGET_CREATE}
	${TOOL_CAT} ${RCCONF_SRCS} > ${.TARGET}

.include <bsd.prog.mk>
