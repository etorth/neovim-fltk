#=======================================================================================
#
#        Filename: CMakeLists.txt
#         Created: 05/03/2016 13:19:07
#     Description:
#
#         Version: 1.0
#        Revision: none
#        Compiler: cmake
#
#          Author: ANHONG
#           Email: anhonghe@gmail.com
#    Organization: USTC
#
#=======================================================================================

PROJECT(neovim_fltk)
CMAKE_MINIMUM_REQUIRED(VERSION 3.0)

SET(CMAKE_CXX_STANDARD 17)
SET(CMAKE_CXX_STANDARD_REQUIRED ON)

ADD_SUBDIRECTORY(src)

SET(COMMAND_GIT_TAG git describe --tag)
EXECUTE_PROCESS(
    COMMAND           ${COMMAND_GIT_TAG}
    OUTPUT_VARIABLE   COMMAND_GIT_TAG_OUTPUT
    WORKING_DIRECTORY ${PROJECT_SOURCE_DIR}
)
STRING(REGEX REPLACE "\n$" "" PROJ_GIT_TAG_STR ${COMMAND_GIT_TAG_OUTPUT})

INCLUDE(InstallRequiredSystemLibraries)
SET(CPACK_GENERATOR "ZIP")
SET(CPACK_PACKAGE_VERSION ${PROJ_GIT_TAG_STR})
INCLUDE(CPack)
