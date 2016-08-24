#!/usr/bin/make -f
#
# Minimal Makefile with no extra features.
#   - assumes all sources are in the same directory as the Makefile
#   - creates all intermediate files in the sources directory
#   - automatically creates dependency tree

SHELL := /bin/bash

CXXFLAGS := -Wall -Wextra

target := foo

srcs := $(wildcard *.cpp)
objs := $(patsubst %.cpp,%.o,$(srcs))
deps := $(patsubst %.cpp,%.d,$(srcs))

ifdef DEBUG
	CXXFLAGS += -g -O0
endif

.SUFFIXES:
.SUFFIXES: .cpp .d .o

all: $(target)

-include $(deps)

$(target): $(objs)
	$(CXX) $(LDFLAGS) $^ -o $@

%.o: %.cpp
	$(CXX) $(CXXFLAGS) -std=c++11 -c $< -o $@

%.d: %.cpp
	$(CXX) -MM $< > $@

clean:
	rm -f $(target)
	rm -f *.o *.d

.PHONY: all clean
