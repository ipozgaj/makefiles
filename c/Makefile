#!/usr/bin/make -f
#
# Minimal Makefile with no extra features.
#   - assumes all sources are in the same directory as the Makefile
#   - creates all intermediate files in the sources directory
#   - automatically creates dependency tree

SHELL := /bin/bash

CFLAGS := -Wall -Wextra

target := foo

srcs := $(wildcard *.c)
objs := $(patsubst %.c,%.o,$(srcs))
deps := $(patsubst %.c,%.d,$(srcs))

ifdef DEBUG
	CFLAGS += -g -O0
endif

.SUFFIXES:
.SUFFIXES: .c .d .o

all: $(target)

-include $(deps)

$(target): $(objs)
	$(CC) $(LDFLAGS) $^ -o $@

%.o: %.c
	$(CC) $(CFLAGS) -std=c11 -c $< -o $@

%.d: %.c
	$(CC) -MM $< > $@

clean:
	rm -f $(target)
	rm -f *.o *.d

.PHONY: all clean
