include_directories(${CMAKE_SOURCE_DIR}/cutil)
include_directories(${CMAKE_SOURCE_DIR}/ccutil)
include_directories(${CMAKE_SOURCE_DIR}/ccstruct)
include_directories(${CMAKE_SOURCE_DIR}/viewer)
include_directories(${CMAKE_SOURCE_DIR}/opencl)

########### next target ###############

SET(tesseract_textord_STAT_SRCS
   alignedblob.cpp
   baselinedetect.cpp
   bbgrid.cpp
   blkocc.cpp
   blobgrid.cpp
   ccnontextdetect.cpp
   cjkpitch.cpp
   colfind.cpp
   colpartition.cpp
   colpartitionset.cpp
   colpartitiongrid.cpp
   devanagari_processing.cpp
   drawedg.cpp
   drawtord.cpp
   edgblob.cpp
   edgloop.cpp
   equationdetectbase.cpp
   fpchop.cpp
   gap_map.cpp
   imagefind.cpp
   linefind.cpp
   makerow.cpp
   oldbasel.cpp
   pithsync.cpp
   pitsync1.cpp
   scanedg.cpp
   sortflts.cpp
   strokewidth.cpp
   tabfind.cpp
   tablefind.cpp
   tabvector.cpp
   tablerecog.cpp
   textlineprojection.cpp
   textord.cpp
   topitch.cpp
   tordmain.cpp
   tospace.cpp
   tovars.cpp
   underlin.cpp
   wordseg.cpp
   workingpartset.cpp
)

add_library(tesseract_textord_static STATIC ${tesseract_textord_STAT_SRCS})


########### next target ###############

SET(tesseract_textord_LIB_SRCS ${DUMMY_CPP})

add_library(tesseract_textord SHARED ${tesseract_textord_LIB_SRCS})

target_link_libraries(tesseract_textord)

set_target_properties(tesseract_textord PROPERTIES VERSION 4.2.0 SOVERSION 4)
install(TARGETS tesseract_textord DESTINATION lib)
install(TARGETS tesseract_textord_static DESTINATION lib)


########### install files ###############




#original Makefile.am contents follow:

#AM_CPPFLAGS += \
#    -DUSE_STD_NAMESPACE \
#    -I$(top_srcdir)/ccstruct -I$(top_srcdir)/ccutil \
#    -I$(top_srcdir)/viewer \
#    -I$(top_srcdir)/ccmain -I$(top_srcdir)/wordrec -I$(top_srcdir)/api \
#    -I$(top_srcdir)/cutil -I$(top_srcdir)/classify -I$(top_srcdir)/dict \
#    -I$(top_srcdir)/opencl
#if USE_OPENCL
#AM_CPPFLAGS += -I$(OPENCL_HDR_PATH)
#endif
#        
#if VISIBILITY
#AM_CPPFLAGS += -DTESS_EXPORTS \
#    -fvisibility=hidden -fvisibility-inlines-hidden
#endif
#
#
#noinst_HEADERS = \
#    alignedblob.h baselinedetect.h bbgrid.h blkocc.h blobgrid.h \
#    ccnontextdetect.h cjkpitch.h colfind.h colpartition.h colpartitionset.h \
#    colpartitiongrid.h \
#    devanagari_processing.h drawedg.h drawtord.h edgblob.h edgloop.h \
#    equationdetectbase.h \
#    fpchop.h gap_map.h imagefind.h linefind.h makerow.h oldbasel.h \
#    pithsync.h pitsync1.h scanedg.h sortflts.h strokewidth.h \
#    tabfind.h tablefind.h tabvector.h \
#    tablerecog.h textlineprojection.h textord.h \
#    topitch.h tordmain.h tovars.h \
#    underlin.h wordseg.h workingpartset.h
#
#if !USING_MULTIPLELIBS
#noinst_LTLIBRARIES = libtesseract_textord.la
#else
#lib_LTLIBRARIES = libtesseract_textord.la
#libtesseract_textord_la_LDFLAGS = -version-info $(GENERIC_LIBRARY_VERSION)
#libtesseract_textord_la_LIBADD = \
#    ../ccstruct/libtesseract_ccstruct.la \
#    ../ccutil/libtesseract_ccutil.la \
#    ../viewer/libtesseract_viewer.la \
#    ../wordrec/libtesseract_wordrec.la \
#    ../cutil/libtesseract_cutil.la \
#    ../classify/libtesseract_classify.la \
#    ../dict/libtesseract_dict.la \
#    ../opencl/libtesseract_opencl.la 
#endif
#
#libtesseract_textord_la_SOURCES = \
#    alignedblob.cpp baselinedetect.cpp bbgrid.cpp blkocc.cpp blobgrid.cpp \
#    ccnontextdetect.cpp cjkpitch.cpp colfind.cpp colpartition.cpp colpartitionset.cpp \
#    colpartitiongrid.cpp devanagari_processing.cpp \
#    drawedg.cpp drawtord.cpp edgblob.cpp edgloop.cpp \
#    equationdetectbase.cpp \
#    fpchop.cpp gap_map.cpp imagefind.cpp linefind.cpp makerow.cpp oldbasel.cpp \
#    pithsync.cpp pitsync1.cpp scanedg.cpp sortflts.cpp strokewidth.cpp \
#    tabfind.cpp tablefind.cpp tabvector.cpp \
#    tablerecog.cpp textlineprojection.cpp textord.cpp \
#    topitch.cpp tordmain.cpp tospace.cpp tovars.cpp \
#    underlin.cpp wordseg.cpp workingpartset.cpp
