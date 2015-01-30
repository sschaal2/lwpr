#############################################################################
#############################################################################
#
#  This is a CMakeList.txt file originally programmed for the CLMC/AMD labs
#  at the University of Southern California and the Max-Planck-Institute for
#  Intelligent Systems. We use a mixutre of explicit makefiles and cmake, but 
#  primarily we relay on cmake for all major compile dependencies. All our
#  software is provided under a slightly modified version of the LGPL license
#  to be found at http://www-clmc.usc.edu/software/license.
#
#  Copyright by Stefan Schaal, 2014
#
#############################################################################

cmake_minimum_required(VERSION 2.8)

# local defines
set(header_directory  ${CMAKE_CURRENT_SOURCE_DIR}/include)
set(src_directory     ${CMAKE_CURRENT_SOURCE_DIR}/src)
include_directories(BEFORE ${header_directory})
include_directories(BEFORE ${src_directory})

include_directories(BEFORE ${utilities_directory}/include)

set(SRCS_LIB 
	${src_directory}/lwpr.c 
	${src_directory}/lwpr_script.c 
	)

set(SRCS_A2M 
	${src_directory}/ascii2mrdplot.c 
	)

set(SRCS_XLWPR 
	${src_directory}/lwpr_test.c 
	${src_directory}/lwpr.c 
	${src_directory}/lwpr_main.c 
	${src_directory}/lwpr_script.c 
	)

set(SRCS_STAT
	${src_directory}/lwpr_stat.c 
	${src_directory}/lwpr.c 
	${src_directory}/lwpr_main.c 
	${src_directory}/lwpr_script.c 
	)

set(HEADERS 
  ${header_directory}/lwpr.h)

add_library(lwpr ${SRCS_LIB})
target_link_libraries(lwpr utility)
install(TARGETS lwpr 
  ARCHIVE DESTINATION ${LAB_LIBDIR}
  LIBRARY DESTINATION ${LAB_LIBDIR})

add_executable(xlwpr ${SRCS_XLWPR})
target_link_libraries(xlwpr utility ${LAB_STD_LIBS})
install(PROGRAMS 
        ${CMAKE_CURRENT_BINARY_DIR}/xlwpr 
        DESTINATION ${LAB_BINDIR})

add_executable(xlwprstat ${SRCS_STAT})
target_link_libraries(xlwprstat utility ${LAB_STD_LIBS})
install(PROGRAMS 
        ${CMAKE_CURRENT_BINARY_DIR}/xlwprstat 
        DESTINATION ${LAB_BINDIR})

add_executable(xascii2clmcplot ${SRCS_A2M})
target_link_libraries(xascii2clmcplot utility ${LAB_STD_LIBS})
install(PROGRAMS 
        ${CMAKE_CURRENT_BINARY_DIR}/xascii2clmcplot 
        DESTINATION ${LAB_BINDIR})

install(FILES ${HEADERS} DESTINATION ${LAB_INCLUDES})

