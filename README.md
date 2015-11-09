# eupa
simple, makefile based package manager

# usage

Add to Makefile

    all: <your targets here>

    EUPA_ROOT = $(BUILD)
    EUPA_JS = $(DIST)

    ifeq ($(findstring clean,$(MAKECMDGOALS)),)
    ifeq ($(wildcard eupa/Makefile.eupa),)
      $(shell git clone https://github.com/skepner/eupa.git)
    endif
    -include eupa/Makefile.eupa
    endif

    ... <other targets> ...

    distclean: clean
        rm -rf $(BUILD) eupa

Add to .gitignore

    eupa
