
.SUFFIXES: .c .o .asm .hex .bin

TARGETS = cmv_snap3 cmv_train3 cmv_hist3 cmv_perf3 lut_conf3 cmv_rcn3 
TARGETS += cmv_snap3.static cmv_hist3.static lut_conf3.static
TARGETS += pmem mimg pong

all : $(TARGETS)
	$(STRIP) $^

# PREFIX = arm-mandriva-linux-gnueabi
PREFIX = arm-linux-gnueabi

CC = $(PREFIX)-gcc
STRIP = $(PREFIX)-strip
CFLAGS += -Wall -std=gnu99 -O2
LDFLAGS += -lm

cmv_train3.o : cmv_train3.c cmv_reg.h
cmv_snap3.o : cmv_snap3.c cmv_reg.h scn_reg.h
cmv_perf3.o : cmv_perf3.c cmv_reg.h scn_reg.h
cmv_rcn3.o : cmv_rcn3.c cmv_reg.h scn_reg.h

cmv_perf3 : cmv_perf3.o
	$(CC) $(CFLAGS) -lrt -o $@ $^

pong : pong.o
	$(CC) $(CFLAGS) -lrt -lm -o $@ $^

cmv_snap3.static : cmv_snap3.o
	$(CC) $(CFLAGS) -static $(LDFLAGS) -o $@ $^

cmv_hist3.static : cmv_hist3.o
	$(CC) $(CFLAGS) -static $(LDFLAGS) -o $@ $^

lut_conf3.static : lut_conf3.o
	$(CC) $(CFLAGS) -static -o $@ $^ $(LDFLAGS)

clean:
	rm -f *.o
	rm -f $(TARGETS)
	rm -f *~ *.orig


# 	block normal .c -> .o
# %.o : %.c

