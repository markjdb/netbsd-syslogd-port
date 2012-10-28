.include <bsd.own.mk>

SRC=${.CURDIR}/../../dist
.PATH: ${SRC}

PROG=	syslogd
SRCS=	syslogd.c tls.c sign.c
MAN=	syslog.conf.5 syslogd.8

WARNS?=	3

LDADD+=	-L/usr/local/lib/ -lutil -levent
DPADD+=	${LIBUTIL} ${LIBEVENT}

CFLAGS+=-I/usr/local/include

.if ${MK_INET6_SUPPORT} != "no"
CFLAGS+=-DINET6
.endif

.if ${MK_OPENSSL} != "no"
LDADD+=	-lssl -lcrypto
DPADD+=	${LIBSSL} ${LIBCRYPTO}
.endif

.include <bsd.prog.mk>
