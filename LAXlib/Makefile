# Makefile for LAXlib

include ../make.inc

MODFLAGS= $(MOD_FLAG)../UtilXlib $(MOD_FLAG)../ELPA/src  $(MOD_FLAG)../EIGENSOLVER_GPU/lib_eigsolve $(MOD_FLAG). 

LAX = la_types.o \
la_error.o \
la_helper.o \
cdiaghg.o \
rdiaghg.o \
dspev_drv.o \
ptoolkit.o \
transto.o \
distools.o \
zhpev_drv.o \
mp_diag.o \
la_param.o


all : libqela.a


libqela.a:  $(LAX)
	$(AR) $(ARFLAGS) $@ $?       
	$(RANLIB) $@    

la_test.x : test.o libqela.a 
	$(LD) $(LDFLAGS) -o la_test.x test.o libqela.a $(QELIBS)

TEST : la_test.x

clean :
	- /bin/rm -f *.o *.a *.d *.i *~ *_tmp.f90 *.mod *.L *.x *.fh

$(LAX) : laxlib.fh  laxlib_hi.fh  laxlib_kinds.fh  laxlib_low.fh  laxlib_mid.fh  laxlib_param.fh

include make.depend
