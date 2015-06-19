CFLAGS = -O3 -g0
OBJS=bitcoin.o db.o dns.o main.o netbase.o protocol.o util.o
PROGS=dnsseed
CPROGS=$(addprefix ../bin/,$(PROGS))

dnsseed: bitcoin.o db.o dns.o main.o netbase.o protocol.o util.o
	g++ -pthread $(CFLAGS) -o ../bin/$@ $(OBJS) -lcrypto

%.o: %.cpp bitcoin.h netbase.h protocol.h db.h serialize.h uint256.h util.h
	g++ -DUSE_IPV6 -pthread $(CFLAGS) -Wno-invalid-offsetof -c -o $@ $<

dns.o: dns.c
	gcc -pthread -std=c99 $(CFLAGS) dns.c -c -o dns.o

%.o: %.cpp

clean:
	rm -f $(OBJS) $(CPROGS)
