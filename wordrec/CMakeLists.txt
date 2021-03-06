include_directories(${CMAKE_SOURCE_DIR}/ccstruct)
include_directories(${CMAKE_SOURCE_DIR}/ccutil)
include_directories(${CMAKE_SOURCE_DIR}/cutil)
include_directories(${CMAKE_SOURCE_DIR}/viewer)
include_directories(${CMAKE_SOURCE_DIR}/classify)
include_directories(${CMAKE_SOURCE_DIR}/dict)

########### next target ###############

SET(tesseract_wordrec_STAT_SRCS
   associate.cpp
   chop.cpp
   chopper.cpp
   drawfx.cpp
   findseam.cpp
   gradechop.cpp
   language_model.cpp
   lm_consistency.cpp
   lm_pain_points.cpp
   lm_state.cpp
   makechop.cpp
   olutil.cpp
   outlines.cpp
   params_model.cpp
   pieces.cpp
   plotedges.cpp
   render.cpp
   segsearch.cpp
   tface.cpp
   wordclass.cpp
   wordrec.cpp
)

add_library(tesseract_wordrec_static STATIC ${tesseract_wordrec_STAT_SRCS})


########### next target ###############

SET(tesseract_wordrec_LIB_SRCS ${DUMMY_CPP})

add_library(tesseract_wordrec SHARED ${tesseract_wordrec_LIB_SRCS})

target_link_libraries(tesseract_wordrec)

set_target_properties(tesseract_wordrec PROPERTIES VERSION 4.2.0 SOVERSION 4)
install(TARGETS tesseract_wordrec DESTINATION lib)
install(TARGETS tesseract_wordrec_static DESTINATION lib)


########### install files ###############




#original Makefile.am contents follow:

#AM_CPPFLAGS += \
#    -I$(top_srcdir)/ccstruct -I$(top_srcdir)/ccutil \
#    -I$(top_srcdir)/cutil -I$(top_srcdir)/classify \
#    -I$(top_srcdir)/dict \
#    -I$(top_srcdir)/viewer
#
#if VISIBILITY
#AM_CPPFLAGS += -DTESS_EXPORTS \
#    -fvisibility=hidden -fvisibility-inlines-hidden
#endif
#
#noinst_HEADERS = \
#    associate.h chop.h \
#    chopper.h drawfx.h findseam.h gradechop.h \
#    language_model.h lm_consistency.h lm_pain_points.h lm_state.h \
#    makechop.h measure.h \
#    olutil.h outlines.h params_model.h plotedges.h \
#    render.h \
#    wordrec.h
#
#if !USING_MULTIPLELIBS
#noinst_LTLIBRARIES = libtesseract_wordrec.la
#else
#lib_LTLIBRARIES = libtesseract_wordrec.la
#libtesseract_wordrec_la_LDFLAGS = -version-info $(GENERIC_LIBRARY_VERSION)
#libtesseract_wordrec_la_LIBADD = \
#    ../ccstruct/libtesseract_ccstruct.la \
#    ../ccutil/libtesseract_ccutil.la \
#    ../cutil/libtesseract_cutil.la \
#    ../classify/libtesseract_classify.la \
#    ../dict/libtesseract_dict.la \
#    ../viewer/libtesseract_viewer.la
#endif
#
#libtesseract_wordrec_la_SOURCES = \
#    associate.cpp chop.cpp chopper.cpp \
#    drawfx.cpp findseam.cpp gradechop.cpp \
#    language_model.cpp lm_consistency.cpp lm_pain_points.cpp lm_state.cpp \
#    makechop.cpp \
#    olutil.cpp outlines.cpp params_model.cpp pieces.cpp \
#    plotedges.cpp render.cpp segsearch.cpp \
#    tface.cpp wordclass.cpp wordrec.cpp
