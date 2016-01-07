SHELL = /bin/sh
include ../comps.conf


PROG = librtk


SOURCES = rtkcmn.c 			\
		  rtksvr.c 			\
		  rtkpos.c 			\
		  geoid.c			\
		  solution.c		\
		  lambda.c			\
		  sbas.c			\
		  stream.c			\
		  rcvraw.c			\
		  rtcm.c			\
		  rtcm2.c			\
		  rtcm3.c			\
		  rtcm3e.c			\
		  preceph.c			\
		  options.c			\
		  pntpos.c			\
		  rcv/novatel.c		\
		  rcv/ublox.c		\
		  rcv/crescent.c	\
		  rcv/skytraq.c		\
		  rcv/gw10.c		\
		  rcv/javad.c		\
		  rcv/nvs.c			\
		  rcv/binex.c		\
		  rcv/rt17.c		\
		  ephemeris.c		\
		  rinex.c			\
		  ionex.c			\
		  qzslex.c			\


OBJS = 	  rtkcmn.o 			\
		  rtksvr.o 			\
		  rtkpos.o 			\
		  geoid.o			\
		  solution.o		\
		  lambda.o			\
		  sbas.o			\
		  stream.o			\
		  rcvraw.o			\
		  rtcm.o			\
		  rtcm2.o			\
		  rtcm3.o			\
		  rtcm3e.o			\
		  preceph.o			\
		  options.o			\
		  pntpos.o			\
		  novatel.o			\
		  ublox.o			\
		  crescent.o		\
		  skytraq.o			\
		  gw10.o			\
		  javad.o			\
		  nvs.o				\
		  binex.o			\
		  rt17.o			\
		  ephemeris.o		\
		  rinex.o			\
		  ionex.o			\
		  qzslex.o			\



CTARGET= -DNFREQ=3

ifeq ($(CONFIG_PPP),y)
	SOURCES +=	ppp.c ppp_ar.c
	OBJS 	+=	ppp.o ppp_ar.o
endif


ifeq ($(CONFIG_KML),y)
	SOURCES +=	convkml.c
	OBJS 	+=	convkml.o 
endif


ifeq ($(CONFIG_CONVRNX),y)
	SOURCES +=	convrnx.c
	OBJS 	+=	convrnx.o 
endif


ifeq ($(CONFIG_SS2),y)
	SOURCES +=	rcv/ss2.c
	OBJS 	+=	ss2.o 
	CTARGET += DENASS2
endif




ifeq ($(CONFIG_GLONASS),y)
	CTARGET += -DENAGLO
endif

ifeq ($(CONFIG_Galileo),y)
	CTARGET += -DENAGAL
endif

ifeq ($(CONFIG_BeiDou),y)
	CTARGET += -DENACMP
endif

ifeq ($(CONFIG_QZSS),y)
	CTARGET += -DENAQZS
endif

ifeq ($(CONFIG_TRACE),y)
	CTARGET += -DTRACE
endif

CC=gcc
STRIP=strip

CFLAGS = -Wall -O3 -ansi -pedantic -Wno-unused-but-set-variable -I./  $(CTARGET) -g
LIBNAME=$(PROG).so

ifeq ($(CONFIG_WIN32),y)
LDLIBS = -lm -lpthread -lwinmm -lws2_32
LIBNAME=$(PROG).dll
CTARGET += -DWIN32
else
LDLIBS  = -lm -lrt -lpthread
endif



all: $(PROG)

$(PROG):
	$(CC) -Wall $(CFLAGS) -fPIC -c $(SOURCES)
	$(CC) -shared -fPIC -Wl,-soname,$(LIBNAME) -o $(LIBNAME) $(OBJS) $(LDLIBS)

strip:
	$(STRIP) $(PROG).so

clean:
	rm -rf  *.o $(PROG).so
