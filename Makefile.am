# jshon - command line JSON parsing

ACLOCAL_AMFLAGS = -I m4 --install

CFLAGS := -std=c99 -Wall -pedantic -Wextra -Werror ${CFLAGS}
JANSSON_CFLAGS = @JANSSON_CFLAGS@
CFLAGS += $(JANSSON_CFLAGS)
JANSSON_LIBS = @JANSSON_LIBS@
LDLIBS  = -ljansson
EXTRA_LDLIBS = -lc
INSTALL = install
DESTDIR ?= /
PREFIX ?= /usr
MANDIR = $(DESTDIR)$(PREFIX)/share/man/man1/
TARGET_PATH = $(DESTDIR)$(PREFIX)/bin
MY_DISTFILES = jshon
MANFILE = jshon.1

NON_GIT_VERSION = $(shell date +%Y%m%d)
VERSION = $(shell git show -s --format="%ci" HEAD | cut -d ' ' -f 1 | tr -d '-')
OTHER_GIT_VERSION = $(shell git show -s --format="%ci" HEAD | sed -e 's/-//g' -e 's/ .*//')
MY_VERSION = $(shell grep "^#define JSHONVER" | cut -d ' ' -f 3)

all: $(MY_DISTFILES)

$(MY_DISTFILES): jshon.o
	$(CC) $(LDFLAGS) -o $(MY_DISTFILES) jshon.o $(JANSSON_LIBS) $(EXTRA_LDLIBS)

jshon.o: jshon.c
	$(CC) $(CFLAGS) $(JANSSON_CFLAGS) -o jshon.o -c jshon.c

strip: $(MY_DISTFILES)
	strip --strip-all $(MY_DISTFILES)

clean-local:
	rm -f *.o $(MY_DISTFILES)

install-jshon:
	$(INSTALL) $(MY_DISTFILES) $(TARGET_PATH)/$(MY_DISTFILES)
	$(INSTALL) $(MANFILE) $(MANDIR)/$(MANFILE)

orig-dist: clean
	sed -i "s/#define JSHONVER .*/#define JSHONVER ${VERSION}/" jshon.c
	sed -i "s/Version:.*/Version:\t${VERSION}/" jshon.spec
	mkdir jshon-${VERSION}
	cp jshon.c jshon.1 Makefile LICENSE jshon-${VERSION}
	tar czf jshon-${VERSION}.tar.gz jshon-${VERSION}
	${RM} -r jshon-${VERSION}

.PHONY: all clean dist strip

