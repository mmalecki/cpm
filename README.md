# cpm

C package manager.

## Makefile integration

```makefile
OBJS += src/forza.o
OBJS += src/connect.o
OBJS += src/json.o

CFLAGS += -g -Wall $(shell cpm includepath)

all: libuv libsaneopt libenv forza

src/%.o: src/%.c
	gcc $(CFLAGS) -c $< -o $@

forza: $(OBJS)
	gcc $^ $(shell cpm libs) $(LDFLAGS) $(CFLAGS) -o $@

libuv:
 	$(MAKE) -C deps/libuv/

libsaneopt:
	$(MAKE) -C deps/saneopt/

libenv:
	$(MAKE) -C deps/env/

.PHONY: all test clean cleanall

```
