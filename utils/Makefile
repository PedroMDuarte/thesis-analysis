all: testutils  

GSL_INC = /lab/software/apparatus3/cpptools/gsl-1.15/
APP3_CPP_INC = /lab/software/apparatus3/cpp/
CPP_TOOLS_INC = -I/lab/software/apparatus3/cpptools -I/lab/software/apparatus3/cpptools/CCfits -I/lab/software/apparatus3/cpptools/cfitsio
INC = -I${APP3_CPP_INC} ${CPP_TOOLS_INC} -I${GSL_INC}

GSL_LIB = -L/lab/software/apparatus3/cpptools/gsl-1.15/.libs/ -L/lab/software/apparatus3/cpptools/gsl-1.15/cblas/.libs/
CCFITS_LIB = /lab/software/apparatus3/cpptools/CCfits/.libs/libCCfits.so
TIFF_LIB = /lab/software/apparatus3/cpptools/tiff-4.0.0/libtiff/.libs/libtiff.so

RUN_TIME_PATHS = -R/lab/software/apparatus3/cpptools/gsl-1.15/.libs/:/lab/software/apparatus3/cpptools/gsl-1.15/cblas/.libs/:/lab/software/apparatus3/cpptools/CCfits/.libs/:/lab/software/apparatus3/cpptools/tiff-4.0.0/libtiff/.libs/

CFLAGS = -Wall ${INC} 
LFLAGS = ${GSL_LIB} -lgsl -lgslcblas -lm ${CCFITS_LIB} ${TIFF_LIB} -Xlinker ${RUN_TIME_PATHS}

objs = testutils.o /lab/software/apparatus3/cpp/qini/qini_utils.o 

testutils: testutils.o /lab/software/apparatus3/cpp/qini/qini_utils.o utils.a
	g++ $^ ${LFLAGS} -o testutils

utils.a: crop.cpp utils.h fileutils.cpp readwrite.cpp matrices.cpp
	indent utils.h
	indent fileutils.cpp 
	indent readwrite.cpp
	indent matrices.cpp
	indent crop.cpp
	g++ -c ${CFLAGS} fileutils.cpp readwrite.cpp matrices.cpp crop.cpp  
	ar rcs utils.a fileutils.o readwrite.o matrices.o crop.o 
	rm fileutils.o readwrite.o matrices.o crop.o 

clean:
	rm -f *.o

.cpp.o:
	indent $<
	g++ $< ${CFLAGS} -c




