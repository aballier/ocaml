#**************************************************************************
#*                                                                        *
#*                                 OCaml                                  *
#*                                                                        *
#*            Xavier Leroy, projet Cristal, INRIA Rocquencourt            *
#*                                                                        *
#*   Copyright 1999 Institut National de Recherche en Informatique et     *
#*     en Automatique.                                                    *
#*                                                                        *
#*   All rights reserved.  This file is distributed under the terms of    *
#*   the GNU Lesser General Public License version 2.1, with the          *
#*   special exception on linking described in the file LICENSE.          *
#*                                                                        *
#**************************************************************************

LIBNAME=bigarray
EXTRACFLAGS=-I../$(UNIXLIB) -DIN_OCAML_BIGARRAY
EXTRACAMLFLAGS=-I ../$(UNIXLIB)
COBJS=bigarray_stubs.$(O) mmap_$(UNIX_OR_WIN32).$(O)
CAMLOBJS=bigarray.cmo
HEADERS=bigarray.h

include ../Makefile

.PHONY: depend
depend:
ifeq "$(TOOLCHAIN)" "msvc"
	$(error Dependencies cannot be regenerated using the MSVC ports)
else
	$(CC) -MM $(CFLAGS) *.c | sed -e 's/\.o/.$$(O)/g' > .depend
	$(CAMLRUN) $(ROOTDIR)/tools/ocamldep -slash *.mli *.ml >> .depend
endif

include .depend
