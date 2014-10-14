
########### next target ###############

SET(tesseract_neural_STAT_SRCS
   input_file_buffer.cpp
   neural_net.cpp
   neuron.cpp
   sigmoid_table.cpp
)

add_library(tesseract_neural_static STATIC ${tesseract_neural_STAT_SRCS})


########### next target ###############

SET(tesseract_neural_LIB_SRCS ${DUMMY_CPP})

add_library(tesseract_neural SHARED ${tesseract_neural_LIB_SRCS})

target_link_libraries(tesseract_neural)

set_target_properties(tesseract_neural PROPERTIES VERSION 4.2.0 SOVERSION 4)
install(TARGETS tesseract_neural DESTINATION lib)
install(TARGETS tesseract_neural_static DESTINATION lib)


########### install files ###############




#original Makefile.am contents follow:

#AM_CPPFLAGS += \
#    -DUSE_STD_NAMESPACE \
#    -I$(top_srcdir)/cutil -I$(top_srcdir)/ccutil \
#    -I$(top_srcdir)/ccstruct -I$(top_srcdir)/dict \
#    -I$(top_srcdir)/image -I$(top_srcdir)/viewer
#
#if VISIBILITY
#AM_CPPFLAGS += -DTESS_EXPORTS \
#    -fvisibility=hidden -fvisibility-inlines-hidden
#endif
#
#noinst_HEADERS = \
#    input_file_buffer.h neural_net.h neuron.h
#
#if !USING_MULTIPLELIBS
#noinst_LTLIBRARIES = libtesseract_neural.la
#else
#lib_LTLIBRARIES = libtesseract_neural.la
#libtesseract_neural_la_LDFLAGS = -version-info $(GENERIC_LIBRARY_VERSION)
#endif
#
#libtesseract_neural_la_SOURCES = \
#    input_file_buffer.cpp neural_net.cpp neuron.cpp sigmoid_table.cpp
#
#
