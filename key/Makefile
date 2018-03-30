_LDFLAGS := $(LDFLAGS) -lrt -lpcap -lsodium
_CFLAGS := $(CFLAGS) -Wall -O2

all: keygen

%.o: %.c *.h
	$(CC) -std=gnu99 -c -o $@ $< $(_CFLAGS)

keygen: keygen.o
	$(CC) -o $@ $^ $(_LDFLAGS)

clean:
	rm -rf keygen *~ *.o

