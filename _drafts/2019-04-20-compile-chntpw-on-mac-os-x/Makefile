#
# Makefile for the Offline NT Password Editor
#
#
# Change here to point to the needed OpenSSL libraries & .h files
# See INSTALL for more info.
#

#SSLPATH=/usr/local/ssl
OSSLPATH=/usr
OSSLINC=$(OSSLPATH)/include

CC=gcc

# 64 bit if default for compiler setup
CFLAGS= -DUSEOPENSSL -g -I. -I$(OSSLINC) -Wall
OSSLLIB=$(OSSLPATH)/lib


# This is to link with whatever we have, SSL crypto lib we put in static
#LIBS=-L$(OSSLLIB) $(OSSLLIB)/libcrypto.a
LIBS=-L$(OSSLLIB)


all: chntpw cpnt reged samusrgrp sampasswd

chntpw: chntpw.o ntreg.o edlib.o libsam.o
	$(CC) $(CFLAGS) -o chntpw chntpw.o ntreg.o edlib.o libsam.o $(LIBS)

cpnt: cpnt.o
	$(CC) $(CFLAGS) -o cpnt cpnt.o $(LIBS)

reged: reged.o ntreg.o edlib.o
	$(CC) $(CFLAGS) -o reged reged.o ntreg.o edlib.o

samusrgrp: samusrgrp.o ntreg.o libsam.o
	$(CC) $(CFLAGS) -o samusrgrp samusrgrp.o ntreg.o libsam.o 

sampasswd: sampasswd.o ntreg.o libsam.o
	$(CC) $(CFLAGS) -o sampasswd sampasswd.o ntreg.o libsam.o 



#ts: ts.o ntreg.o
#	$(CC) $(CFLAGS) -nostdlib -o ts ts.o ntreg.o $(LIBS)

# -Wl,-t

.c.o:
	$(CC) -c $(CFLAGS) $<

clean:
	rm -f *.o chntpw cpnt reged samusrgrp sampasswd *~

