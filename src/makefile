#DEBUG     = -g
#DETAIL    = -qflag=i:i -qinfo=all -qinfo=nouni -qnamemangling=v5
#CC        = g++44
CC        = g++
INCLUDE   = -I ../include 
LIBS      = -lpthread
OBJECTS   = sspublic.o sspretreatment.o sscheck.o sstrans.o ssmsisdn.o
LDFLAGS   = -m64 -O2 $(DETAIL) $(LIBS) -lm
CFLAGS    = -m64 -O2 $(DETAIL) -D_REENTRANT -D_THREAD_SAFE $(DEBUG) $(INCLUDE) -g

all::  saPretreatment 
	rm -f ../bin/saPretreatment
	cp saPretreatment ../bin
	rm -f *.o saPretreatment

ssmsisdn.o:  ssmsisdn.cpp 
	$(CC) $(CFLAGS) -c -o $@ ssmsisdn.cpp 

sspublic.o:  sspublic.cpp 
	$(CC) $(CFLAGS) -c -o $@ sspublic.cpp 
	
sscheck.o:  sscheck.cpp 
	$(CC) $(CFLAGS) -c -o $@ sscheck.cpp 
	
sstrans.o:  sstrans.cpp 
	$(CC) $(CFLAGS) -c -o $@ sstrans.cpp 

sspretreatment.o:  sspretreatment.cpp 
	$(CC) $(CFLAGS) -c -o $@ sspretreatment.cpp 

## 信令分析主程序 ###############################################
saPretreatment:  $(OBJECTS)
	$(CC) $(LDFLAGS) -o $@ $(OBJECTS) $(LIBS)

clean:
	-rm -f $(OBJECTS) saPretreatment nohup.out

install: all
	-rm -f ../../../bin/c/saPretreatment
	mv ../bin/saPretreatment ../../../bin/c
