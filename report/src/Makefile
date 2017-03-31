# Makefile for dinamic library

CC=gcc

CFLAGS =-c -g -fPIC
INCLUDE =-I../inc

SRCS=read.c write.c
OBJS=$(SRCS:.c=.o)

LIBTARGET=libmyio.so.1
LIBS=-L./ -lmyio

.SUFFIXES:.c.o
.c.o:
	$(CC) $(CFLAGS) $(INCLUDE) $<

all: test

test: main.o $(LIBTARGET)
	$(CC) -o $@ main.o $(LIBS)

$(LIBTARGET):$(OBJS)
	$(CC) -shared -Wl,-soname,$@ -o $@ $(OBJS) 
	ln -fs $(LIBTARGET) $(LIBTARGET:so.1=so)

clean:
	rm -rf tet *.o $(LIBTARGET)
