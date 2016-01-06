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
		  ppp.c				\
		  ppp_ar.c			\
		  rcv/novatel.c		\
		  rcv/ublox.c		\
		  rcv/ss2.c			\
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
		  ppp.o				\
		  ppp_ar.o			\
		  novatel.o			\
		  ublox.o			\
		  ss2.o				\
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

CTARGET= -DENAGLO -DENAQZS -DENACMP -DNFREQ=3

CFLAGS = -Wall -O3 -ansi -pedantic -Wno-unused-but-set-variable -I./ -DTRACE $(CTARGET) -g
LDLIBS  = -lm -lrt -lpthread


all: $(PROG)

$(PROG): 
	$(CC) -Wall $(CFLAGS) -fPIC -c $(SOURCES)
	$(CC) -shared -fPIC -Wl,-soname,$(PROG).so -o $(PROG).so $(OBJS)

clean:
	rm -rf  *.o $(PROG).so
