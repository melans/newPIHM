# -----------------------------------------------------------------
# Version: 2.0
# Date: "Nov, 2007"
# -----------------------------------------------------------------
# Programmer: Mukesh Kumar (muk139@psu.edu)@ PSU
# -----------------------------------------------------------------
# Makefile for PIHM
#
# cvode/pihm/Makefile.
# -----------------------------------------------------------------

SHELL = /bin/sh

srcdir       = .
builddir     = .
top_builddir = ../../
top_builddir = ../../
prefix       = /Users/nidsmuks/Downloads/sundials-2.4.0/userinstall 
exec_prefix  = ${prefix}
includedir   = /Users/nidsmuks/Downloads/sundials-2.4.0/userinstall/include
libdir       = /Users/nidsmuks/Downloads/sundials-2.4.0/userinstall/lib 



CPP      = /usr/bin/cc -E
CPPFLAGS =
CC       = /usr/bin/gcc
CFLAGS   = -g -O0
#CFLAGS   =
LDFLAGS  =
LIBS     = -lm
# -DSUB_SURF_RIV is used while solving all the components of the model (surface, subsurface and river states)
# -DDIFFUSION is used for diffusion wave approximation of St. Venant's equation. Otherwise kinematic wave assumption will be used
# MACRO    = -DSUB_SURF_RIV
 MACRO    = -DSUB_SURF_RIV -DDIFFUSION -DLAYER3
# MACRO    = -DSUB_SURF_RIV -DDIFFUSION -DLAYER3 -DDCPL_VFLUX
# MACRO    = -DSUB_SURF_RIV -DDIFFUSION -DLAYER2
# MACRO    = -DSUB_SURF_RIV -DKINEMATIC -DLAYER2
# MACRO    = -DSURF_RIV -DDIFFUSION -DLAYER2 -DCONTAM -DSED
# -DSURF_RIV is used to run the model without sub-surface component. Generally used for calibration purposes
# MACRO    = -DSURF_RIV -DDIFFUSION -DLAYER2
# -DNO_UNSAT is used to run the model without unsaturated zone component. Overlandflow is set to zero 0 initially. DY for overland flow, and unsat zone is set to 0. DY for groundwater = ElePrep. Our goal is to use -DSUB_SURF_RIV -DDIFFUSION -DLAYER2. Long simulations to steady state can be performed. Note: DY for overland should not be set to zero if we want to track where lakes and rivers will be created. Exfiltration will have to be incorporated then
# MACRO    = -DSUB_SURF_RIV -DDIFFUSION -DLAYER2 -DNO_UNSAT
SRC    = pihm.c read_alloc.c initialize.c is_sm_et.c f_decouple.c f.c f_functions.c flux_cal.c update.c print.c
#SRC    = pihm.c read_alloc.c initialize.c is_sm_et.c f_decouple.c f.c f_functions.c update.c print.c

COMPILER_PREFIX =
LINKER_PREFIX   =

SUNDIALS_INC_DIR = $(includedir)
SUNDIALS_LIB_DIR = $(libdir)
SUNDIALS_LIBS    = -lsundials_cvode -lsundials_nvecserial

# EXEC_FILES = cvdx cvdxe cvbx cvkx cvkxb cvdemd cvdemk

all:
	@(echo)
	@(echo '       make pihm     - make pihm        ')
	@(echo '       make clean    - remove all executable files')
	@(echo)

pihm:
	@echo '...Compiling PIHM ...'
	@$(CC) $(CFLAGS) -I$(SUNDIALS_INC_DIR) -L$(SUNDIALS_LIB_DIR) -o $(builddir)/pihm $(SRC) $(SUNDIALS_LIBS) $(LIBS) $(MACRO)

clean:
	@rm -f *.o
	@rm -f pihm
