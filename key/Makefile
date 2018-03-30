_LDFLAGS := $(LDFLAGS) -lpthread -lrt -lpcap -lsodium
_CFLAGS := $(CFLAGS) -Wall -O2

OBJPATH =./objs
CAMERA = ./H264_camera

all: tx keygen

$(OBJPATH)/%.o: %.c *.h
	$(CC) -std=gnu99 -c -o $@ $< $(_CFLAGS)

$(OBJPATH)/%.o: $(CAMERA)/%.cpp $(CAMERA)/*.h
	$(CXX) -std=gnu++11 -c -o $@ $< $(_CFLAGS)
$(OBJPATH)/%.o: %.cpp *.hpp *.h
	$(CXX) -std=gnu++11 -c -o $@ $< $(_CFLAGS)

tx: $(OBJPATH)/tx.o $(OBJPATH)/fec.o $(OBJPATH)/wifibroadcast.o
	$(CXX) -o $@ $^ $(_LDFLAGS)

keygen: $(OBJPATH)/keygen.o
	$(CC) -o $@ $^ $(_LDFLAGS)

clean:
	rm -rf tx keygen *~ $(OBJPATH)/*.o

