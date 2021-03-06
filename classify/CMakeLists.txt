include_directories(${CMAKE_SOURCE_DIR}/cutil)
include_directories(${CMAKE_SOURCE_DIR}/ccutil)
include_directories(${CMAKE_SOURCE_DIR}/ccstruct)
include_directories(${CMAKE_SOURCE_DIR}/dict)
include_directories(${CMAKE_SOURCE_DIR}/viewer)
include_directories(${CMAKE_SOURCE_DIR}/msvsport)

########### next target ###############

SET(tesseract_classify_STAT_SRCS
   adaptive.cpp
   adaptmatch.cpp
   blobclass.cpp
   classify.cpp
   cluster.cpp
   clusttool.cpp
   cutoffs.cpp
   errorcounter.cpp
   extract.cpp
   featdefs.cpp
   flexfx.cpp
   float2int.cpp
   fpoint.cpp
   fxdefs.cpp
   intfeaturedist.cpp
   intfeaturemap.cpp
   intfeaturespace.cpp
   intfx.cpp
   intmatcher.cpp
   intproto.cpp
   kdtree.cpp
   mastertrainer.cpp
   mf.cpp
   mfdefs.cpp
   mfoutline.cpp
   mfx.cpp
   normfeat.cpp
   normmatch.cpp
   ocrfeatures.cpp
   outfeat.cpp
   picofeat.cpp
   protos.cpp
   sampleiterator.cpp
   shapeclassifier.cpp
   shapetable.cpp
   tessclassifier.cpp
   trainingsample.cpp
   trainingsampleset.cpp
   xform2d.cpp
)

add_library(tesseract_classify_static STATIC ${tesseract_classify_STAT_SRCS})


########### next target ###############

SET(tesseract_classify_LIB_SRCS ${DUMMY_CPP})

add_library(tesseract_classify SHARED ${tesseract_classify_LIB_SRCS})

target_link_libraries(tesseract_classify)

set_target_properties(tesseract_classify PROPERTIES VERSION 4.2.0 SOVERSION 4)
install(TARGETS tesseract_classify DESTINATION lib)
install(TARGETS tesseract_classify_static DESTINATION lib)


########### install files ###############




#original Makefile.am contents follow:

#AM_CPPFLAGS += \
#    -I$(top_srcdir)/cutil -I$(top_srcdir)/ccutil \
#    -I$(top_srcdir)/ccstruct -I$(top_srcdir)/dict \
#    -I$(top_srcdir)/viewer
#    
#if VISIBILITY
#AM_CPPFLAGS += -DTESS_EXPORTS \
#    -fvisibility=hidden -fvisibility-inlines-hidden
#endif
#
#noinst_HEADERS = \
#    adaptive.h blobclass.h \
#    classify.h cluster.h clusttool.h cutoffs.h \
#    errorcounter.h extern.h extract.h \
#    featdefs.h flexfx.h float2int.h fpoint.h fxdefs.h \
#    intfeaturedist.h intfeaturemap.h intfeaturespace.h \
#    intfx.h intmatcher.h intproto.h kdtree.h \
#    mastertrainer.h mf.h mfdefs.h mfoutline.h mfx.h \
#    normfeat.h normmatch.h \
#    ocrfeatures.h outfeat.h picofeat.h protos.h \
#    sampleiterator.h shapeclassifier.h shapetable.h \
#    tessclassifier.h trainingsample.h trainingsampleset.h xform2d.h
#
#if !USING_MULTIPLELIBS
#noinst_LTLIBRARIES = libtesseract_classify.la
#else
#lib_LTLIBRARIES = libtesseract_classify.la
#libtesseract_classify_la_LDFLAGS = -version-info $(GENERIC_LIBRARY_VERSION)
#libtesseract_classify_la_LIBADD = \
#    ../ccutil/libtesseract_ccutil.la \
#    ../cutil/libtesseract_cutil.la \
#    ../ccstruct/libtesseract_ccstruct.la \
#    ../dict/libtesseract_dict.la \
#    ../viewer/libtesseract_viewer.la
#endif
#
#libtesseract_classify_la_SOURCES = \
#    adaptive.cpp adaptmatch.cpp blobclass.cpp \
#    classify.cpp cluster.cpp clusttool.cpp cutoffs.cpp \
#    errorcounter.cpp extract.cpp \
#    featdefs.cpp flexfx.cpp float2int.cpp fpoint.cpp fxdefs.cpp \
#    intfeaturedist.cpp intfeaturemap.cpp intfeaturespace.cpp \
#    intfx.cpp intmatcher.cpp intproto.cpp kdtree.cpp \
#    mastertrainer.cpp mf.cpp mfdefs.cpp mfoutline.cpp mfx.cpp \
#    normfeat.cpp normmatch.cpp \
#    ocrfeatures.cpp outfeat.cpp picofeat.cpp protos.cpp \
#    sampleiterator.cpp shapeclassifier.cpp shapetable.cpp \
#    tessclassifier.cpp trainingsample.cpp trainingsampleset.cpp xform2d.cpp
#
#
