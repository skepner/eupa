# eupa
simple, makefile based package manager

# usage

Add to Makefile

    all: <your targets here>

    EUPA_MAKEFILE ?= ...
    EUPA_DIST ?= $(DIST)
    EUPA_BUILD ?= $(BUILD)

    ifeq ($(findstring clean,$(MAKECMDGOALS)),)
    ifeq ($(wildcard $(EUPA_MAKEFILE)),)
      $(shell git clone https://github.com/skepner/eupa.git $(dir $(EUPA_MAKEFILE)))
    endif
    include $(EUPA_MAKEFILE)
    endif

    ... <other targets> ...

    distclean: clean eupa_clean

Add to .gitignore

    eupa
