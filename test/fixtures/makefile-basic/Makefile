SHELL := /bin/bash

# The name of the executable (default is current directory name)
.DEFAULT_GOAL: $(TARGET)

# These will be provided to the target
VERSION := 1.0.0

# Use linker flags to provide version/build settings to the target
# LDFLAGS=-ldflags "-X=main.Version=$(VERSION) -X=main.Build=$(BUILD)"
LDFLAGS=

# go source files, ignore vendor directory
SRC = $(shell find . -type f -name '*.go' -not -path "./vendor/*")
GOPATH=$(CURDIR)

GOCMD=@GOPATH=${GOPATH} go

.PHONY: all build clean install uninstall fmt simplify check run

all: check install

get:
	$(GOCMD) get -v -t -d ./src/...

build: get
	$(GOCMD) build ./...
	@true

install: get
	$(GOCMD) install ./...
	@true

test:
	$(GOCMD) test -v ./...
