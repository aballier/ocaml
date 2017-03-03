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
COBJS=bigarray_stubs.$(O) mmap_ba.$(O) mmap.$(O)
CAMLOBJS=bigarray.cmo

include ../Makefile

mmap.$(O): ../$(UNIXLIB)/mmap.c
	$(BYTECC) $(BYTECCCOMPOPTS) $(CFLAGS) -c $<
mmap_ba.$(O): ../unix/mmap_ba.c
	$(BYTECC) $(BYTECCCOMPOPTS) $(CFLAGS) -c $<

depend:
	$(CC) -MM $(CFLAGS) *.c > .depend
	$(CAMLRUN) $(ROOTDIR)/tools/ocamldep -slash *.mli *.ml >> .depend

ifeq "$(TOOLCHAIN)" "msvc"
.depend.nt: .depend
	sed -e 's/\.o/.$(O)/g' $< > $@

include .depend.nt

else
include .depend
endif
