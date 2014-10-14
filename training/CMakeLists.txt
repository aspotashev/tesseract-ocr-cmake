
########### next target ###############

SET(tesseract_training_STAT_SRCS
   boxchar.cpp
   commandlineflags.cpp
   commontraining.cpp
   degradeimage.cpp
   fileio.cpp
   ligature_table.cpp
   normstrngs.cpp
   pango_font_info.cpp
   stringrenderer.cpp
   tlog.cpp
)

add_library(tesseract_training_static STATIC ${tesseract_training_STAT_SRCS})


########### next target ###############

SET(tesseract_tessopt_STAT_SRCS
   tessopt.cpp
)

add_library(tesseract_tessopt_static STATIC ${tesseract_tessopt_STAT_SRCS})


########### next target ###############

SET(ambiguous_words_SRCS
   ambiguous_words.cpp
)

add_executable(ambiguous_words ${ambiguous_words_SRCS})

target_link_libraries(ambiguous_words tesseract_training_static tesseract_tessopt_static)

install(TARGETS ambiguous_words DESTINATION bin)
install(TARGETS ambiguous_words_static DESTINATION bin)


########### next target ###############

SET(classifier_tester_SRCS
   classifier_tester.cpp
)

add_executable(classifier_tester ${classifier_tester_SRCS})

target_link_libraries(classifier_tester tesseract_training_static tesseract_tessopt_static)

install(TARGETS classifier_tester DESTINATION bin)


########### next target ###############

SET(cntraining_SRCS
   cntraining.cpp
)

add_executable(cntraining ${cntraining_SRCS})

target_link_libraries(cntraining tesseract_training_static tesseract_tessopt_static)

install(TARGETS cntraining DESTINATION bin)


########### next target ###############

SET(combine_tessdata_SRCS
   combine_tessdata.cpp
)

add_executable(combine_tessdata ${combine_tessdata_SRCS})

target_link_libraries(combine_tessdata tesseract_ccutil tesseract)

install(TARGETS combine_tessdata DESTINATION bin)


########### next target ###############

SET(dawg2wordlist_SRCS
   dawg2wordlist.cpp
)

add_executable(dawg2wordlist ${dawg2wordlist_SRCS})

target_link_libraries(dawg2wordlist tesseract_tessopt)

install(TARGETS dawg2wordlist DESTINATION bin)


########### next target ###############

SET(mftraining_SRCS
   mftraining.cpp
   mergenf.cpp
)

add_executable(mftraining ${mftraining_SRCS})

target_link_libraries(mftraining tesseract_training tesseract_tessopt)

install(TARGETS mftraining DESTINATION bin)


########### next target ###############

SET(set_unicharset_properties_SRCS
   set_unicharset_properties.cpp
)

add_executable(set_unicharset_properties ${set_unicharset_properties_SRCS})

target_link_libraries(set_unicharset_properties tesseract_training tesseract_tessopt)

install(TARGETS set_unicharset_properties DESTINATION bin)


########### next target ###############

SET(shapeclustering_SRCS
   shapeclustering.cpp
)

add_executable(shapeclustering ${shapeclustering_SRCS})

target_link_libraries(shapeclustering tesseract_training tesseract_tessopt)

install(TARGETS shapeclustering DESTINATION bin)


########### next target ###############

SET(text2image_SRCS
   text2image.cpp
)

add_executable(text2image ${text2image_SRCS})

target_link_libraries(text2image tesseract_training tesseract_tessopt)

install(TARGETS text2image DESTINATION bin)


########### next target ###############

SET(unicharset_extractor_SRCS
   unicharset_extractor.cpp
)

add_executable(unicharset_extractor ${unicharset_extractor_SRCS})

target_link_libraries(unicharset_extractor tesseract_tessopt)

install(TARGETS unicharset_extractor DESTINATION bin)


########### next target ###############

SET(wordlist2dawg_SRCS
   wordlist2dawg.cpp
)

add_executable(wordlist2dawg ${wordlist2dawg_SRCS})

target_link_libraries(wordlist2dawg tesseract_tessopt)

install(TARGETS wordlist2dawg DESTINATION bin)


########### install files ###############




#original Makefile.am contents follow:

#AUTOMAKE_OPTIONS = subdir-objects
#AM_CPPFLAGS += \
#    -DUSE_STD_NAMESPACE -DPANGO_ENABLE_ENGINE\
#    -I$(top_srcdir)/ccmain -I$(top_srcdir)/api \
#    -I$(top_srcdir)/ccutil -I$(top_srcdir)/ccstruct \
#    -I$(top_srcdir)/viewer \
#    -I$(top_srcdir)/textord -I$(top_srcdir)/dict \
#    -I$(top_srcdir)/classify -I$(top_srcdir)/display \
#    -I$(top_srcdir)/wordrec -I$(top_srcdir)/cutil
#
#EXTRA_DIST = tesstrain.sh
#
#if T_WIN
## try static build
##AM_LDFLAGS += -all-static
##libic=-lsicuin -licudt -lsicuuc
#libicu=-licuin -licuuc
#else
#libicu=-licui18n -licuuc
#endif
## TODO: training programs can not be linked to shared library created 
## with -fvisibility 
#if VISIBILITY
#AM_LDFLAGS += -all-static
#endif
#
#noinst_HEADERS = \
#    boxchar.h commandlineflags.h commontraining.h degradeimage.h \
#      fileio.h icuerrorcode.h ligature_table.h normstrngs.h \
#      mergenf.h pango_font_info.h stringrenderer.h \
#      tessopt.h tlog.h util.h
#
#noinst_LTLIBRARIES = libtesseract_training.la libtesseract_tessopt.la
#
#libtesseract_training_la_LIBADD = \
#    ../cutil/libtesseract_cutil.la 
##    ../api/libtesseract.la
#    
#libtesseract_training_la_SOURCES = \
#    boxchar.cpp commandlineflags.cpp commontraining.cpp degradeimage.cpp \
#      fileio.cpp ligature_table.cpp normstrngs.cpp pango_font_info.cpp \
#      stringrenderer.cpp tlog.cpp
#
#libtesseract_tessopt_la_SOURCES = \
#    tessopt.cpp
#
#bin_PROGRAMS = ambiguous_words classifier_tester cntraining combine_tessdata \
#  dawg2wordlist mftraining set_unicharset_properties shapeclustering \
#  text2image unicharset_extractor wordlist2dawg
#
#ambiguous_words_SOURCES = ambiguous_words.cpp
#ambiguous_words_LDADD = \
#    libtesseract_training.la \
#    libtesseract_tessopt.la
#if USING_MULTIPLELIBS
#ambiguous_words_LDADD += \
#    ../api/libtesseract_api.la \
#    ../textord/libtesseract_textord.la \
#    ../classify/libtesseract_classify.la \
#    ../dict/libtesseract_dict.la \
#    ../ccstruct/libtesseract_ccstruct.la \
#    ../cutil/libtesseract_cutil.la \
#    ../viewer/libtesseract_viewer.la \
#    ../ccmain/libtesseract_main.la \
#    ../cube/libtesseract_cube.la \
#    ../neural_networks/runtime/libtesseract_neural.la \
#    ../wordrec/libtesseract_wordrec.la \
#    ../ccutil/libtesseract_ccutil.la
#else
#ambiguous_words_LDADD += \
#    ../api/libtesseract.la
#endif
#
#classifier_tester_SOURCES = classifier_tester.cpp
##classifier_tester_LDFLAGS = -static
#classifier_tester_LDADD = \
#    libtesseract_training.la \
#    libtesseract_tessopt.la
#if USING_MULTIPLELIBS
#classifier_tester_LDADD += \
#    ../api/libtesseract_api.la \
#    ../textord/libtesseract_textord.la \
#    ../classify/libtesseract_classify.la \
#    ../dict/libtesseract_dict.la \
#    ../ccstruct/libtesseract_ccstruct.la \
#    ../cutil/libtesseract_cutil.la \
#    ../viewer/libtesseract_viewer.la \
#    ../ccmain/libtesseract_main.la \
#    ../cube/libtesseract_cube.la \
#    ../neural_networks/runtime/libtesseract_neural.la \
#    ../wordrec/libtesseract_wordrec.la \
#    ../ccutil/libtesseract_ccutil.la
#else
#classifier_tester_LDADD += \
#    ../api/libtesseract.la
#endif
#
#combine_tessdata_SOURCES = combine_tessdata.cpp
##combine_tessdata_LDFLAGS = -static
#if USING_MULTIPLELIBS
#combine_tessdata_LDADD = \
#    ../ccutil/libtesseract_ccutil.la
#else
#combine_tessdata_LDADD = \
#    ../api/libtesseract.la
#endif
#
#cntraining_SOURCES = cntraining.cpp
##cntraining_LDFLAGS = -static
#cntraining_LDADD = \
#    libtesseract_training.la \
#    libtesseract_tessopt.la
#if USING_MULTIPLELIBS
#cntraining_LDADD += \
#    ../textord/libtesseract_textord.la \
#    ../classify/libtesseract_classify.la \
#    ../dict/libtesseract_dict.la \
#    ../ccstruct/libtesseract_ccstruct.la \
#    ../cutil/libtesseract_cutil.la \
#    ../viewer/libtesseract_viewer.la \
#    ../ccmain/libtesseract_main.la \
#    ../cube/libtesseract_cube.la \
#    ../neural_networks/runtime/libtesseract_neural.la \
#    ../wordrec/libtesseract_wordrec.la \
#    ../ccutil/libtesseract_ccutil.la
#else
#cntraining_LDADD += \
#    ../api/libtesseract.la
#endif
#
#dawg2wordlist_SOURCES = dawg2wordlist.cpp
##dawg2wordlist_LDFLAGS = -static
#dawg2wordlist_LDADD = \
#    libtesseract_tessopt.la
#if USING_MULTIPLELIBS
#dawg2wordlist_LDADD += \
#    ../classify/libtesseract_classify.la \
#    ../dict/libtesseract_dict.la \
#    ../ccstruct/libtesseract_ccstruct.la \
#    ../cutil/libtesseract_cutil.la \
#    ../viewer/libtesseract_viewer.la \
#    ../ccmain/libtesseract_main.la \
#    ../cube/libtesseract_cube.la \
#    ../neural_networks/runtime/libtesseract_neural.la \
#    ../wordrec/libtesseract_wordrec.la \
#    ../textord/libtesseract_textord.la \
#    ../ccutil/libtesseract_ccutil.la
#else
#dawg2wordlist_LDADD += \
#    ../api/libtesseract.la
#endif
#
#mftraining_SOURCES = mftraining.cpp mergenf.cpp
##mftraining_LDFLAGS = -static
#mftraining_LDADD = \
#    libtesseract_training.la \
#    libtesseract_tessopt.la
#if USING_MULTIPLELIBS
#mftraining_LDADD += \
#    ../textord/libtesseract_textord.la \
#    ../classify/libtesseract_classify.la \
#    ../dict/libtesseract_dict.la \
#    ../ccstruct/libtesseract_ccstruct.la \
#    ../cutil/libtesseract_cutil.la \
#    ../viewer/libtesseract_viewer.la \
#    ../ccmain/libtesseract_main.la \
#    ../cube/libtesseract_cube.la \
#    ../neural_networks/runtime/libtesseract_neural.la \
#    ../wordrec/libtesseract_wordrec.la \
#    ../ccutil/libtesseract_ccutil.la
#else
#mftraining_LDADD += \
#    ../api/libtesseract.la
#endif
#
#set_unicharset_properties_SOURCES = set_unicharset_properties.cpp
##set_unicharset_properties_LDFLAGS = $(pkg-config --libs icu-uc)
#set_unicharset_properties_LDADD = \
#    libtesseract_training.la \
#    libtesseract_tessopt.la \
#    $(libicu)
#if USING_MULTIPLELIBS
#set_unicharset_properties_LDADD += \
#    ../textord/libtesseract_textord.la \
#    ../classify/libtesseract_classify.la \
#    ../dict/libtesseract_dict.la \
#    ../ccstruct/libtesseract_ccstruct.la \
#    ../cutil/libtesseract_cutil.la \
#    ../viewer/libtesseract_viewer.la \
#    ../ccmain/libtesseract_main.la \
#    ../cube/libtesseract_cube.la \
#    ../neural_networks/runtime/libtesseract_neural.la \
#    ../wordrec/libtesseract_wordrec.la \
#    ../ccutil/libtesseract_ccutil.la
#else
#set_unicharset_properties_LDADD += \
#    ../api/libtesseract.la
#endif
#
#shapeclustering_SOURCES = shapeclustering.cpp
##shapeclustering_LDFLAGS = -static
#shapeclustering_LDADD = \
#    libtesseract_training.la \
#    libtesseract_tessopt.la
#if USING_MULTIPLELIBS
#shapeclustering_LDADD += \
#    ../textord/libtesseract_textord.la \
#    ../classify/libtesseract_classify.la \
#    ../dict/libtesseract_dict.la \
#    ../ccstruct/libtesseract_ccstruct.la \
#    ../cutil/libtesseract_cutil.la \
#    ../viewer/libtesseract_viewer.la \
#    ../ccmain/libtesseract_main.la \
#    ../cube/libtesseract_cube.la \
#    ../neural_networks/runtime/libtesseract_neural.la \
#    ../wordrec/libtesseract_wordrec.la \
#    ../ccutil/libtesseract_ccutil.la
#else
#shapeclustering_LDADD += \
#    ../api/libtesseract.la
#endif
#
#text2image_SOURCES = text2image.cpp
##text2image_LDFLAGS = -static
#text2image_LDADD = \
#    libtesseract_training.la \
#    libtesseract_tessopt.la
#if USING_MULTIPLELIBS
#text2image_LDADD += \
#    ../textord/libtesseract_textord.la \
#    ../classify/libtesseract_classify.la \
#    ../dict/libtesseract_dict.la \
#    ../ccstruct/libtesseract_ccstruct.la \
#    ../cutil/libtesseract_cutil.la \
#    ../viewer/libtesseract_viewer.la \
#    ../ccmain/libtesseract_main.la \
#    ../cube/libtesseract_cube.la \
#    ../neural_networks/runtime/libtesseract_neural.la \
#    ../wordrec/libtesseract_wordrec.la \
#    ../ccutil/libtesseract_ccutil.la
#else
#text2image_LDADD += \
#    ../api/libtesseract.la
#endif
#text2image_LDADD += $(libicu) -lpango-1.0 -lpangocairo-1.0 \
#		    -lgobject-2.0 -lglib-2.0 -lcairo -lpangoft2-1.0
#
#unicharset_extractor_SOURCES = unicharset_extractor.cpp
##unicharset_extractor_LDFLAGS = -static
#unicharset_extractor_LDADD = \
#    libtesseract_tessopt.la
#if USING_MULTIPLELIBS
#unicharset_extractor_LDADD += \
#    ../ccutil/libtesseract_ccutil.la \
#    ../ccstruct/libtesseract_ccstruct.la
#else
#unicharset_extractor_LDADD += \
#    ../api/libtesseract.la
#endif
#
#wordlist2dawg_SOURCES = wordlist2dawg.cpp
##wordlist2dawg_LDFLAGS = -static
#wordlist2dawg_LDADD = \
#    libtesseract_tessopt.la
#if USING_MULTIPLELIBS
#wordlist2dawg_LDADD += \
#    ../classify/libtesseract_classify.la \
#    ../dict/libtesseract_dict.la \
#    ../ccstruct/libtesseract_ccstruct.la \
#    ../cutil/libtesseract_cutil.la \
#    ../viewer/libtesseract_viewer.la \
#    ../ccmain/libtesseract_main.la \
#    ../cube/libtesseract_cube.la \
#    ../neural_networks/runtime/libtesseract_neural.la \
#    ../wordrec/libtesseract_wordrec.la \
#    ../textord/libtesseract_textord.la \
#    ../ccutil/libtesseract_ccutil.la
#else
#wordlist2dawg_LDADD += \
#    ../api/libtesseract.la
#endif
#
#if T_WIN
#ambiguous_words_LDADD += -lws2_32
#classifier_tester_LDADD += -lws2_32
#cntraining_LDADD += -lws2_32
#combine_tessdata_LDADD += -lws2_32
#dawg2wordlist_LDADD += -lws2_32
#mftraining_LDADD += -lws2_32
#set_unicharset_properties_LDADD += -lws2_32
#shapeclustering_LDADD += -lws2_32
#unicharset_extractor_LDADD += -lws2_32
#text2image_LDADD += -lws2_32
#wordlist2dawg_LDADD += -lws2_32
#
#AM_CPPFLAGS += -I$(top_srcdir)/vs2010/port
#noinst_HEADERS += ../vs2010/port/strcasestr.h
#libtesseract_training_la_SOURCES += ../vs2010/port/strcasestr.cpp
#endif
#
#if USE_OPENCL
#ambiguous_words_LDADD += $(OPENCL_LIB)
#classifier_tester_LDADD += $(OPENCL_LIB)
#cntraining_LDADD += $(OPENCL_LIB)
#combine_tessdata_LDADD += $(OPENCL_LIB)
#dawg2wordlist_LDADD += $(OPENCL_LIB)
#mftraining_LDADD += $(OPENCL_LIB)
#set_unicharset_properties_LDADD += $(OPENCL_LIB)
#shapeclustering_LDADD += $(OPENCL_LIB)
#text2image_LDADD += $(OPENCL_LIB)
#unicharset_extractor_LDADD += $(OPENCL_LIB)
#wordlist2dawg_LDADD += $(OPENCL_LIB)
#endif
