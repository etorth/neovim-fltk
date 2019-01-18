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

# create a reversion string to deploy
# generate this length-20 string by ``git rev-parse HEAD"
SET(COMMAND_GIT_HEADREV git rev-parse HEAD)
EXECUTE_PROCESS(
    COMMAND           ${COMMAND_GIT_HEADREV}
    OUTPUT_VARIABLE   PROJ_HEAD_REVISION
    WORKING_DIRECTORY ${PROJECT_SOURCE_DIR}
)
STRING(SUBSTRING ${PROJ_HEAD_REVISION} 0 20 PROJ_HEAD_REVISION_LEN10)

INCLUDE(InstallRequiredSystemLibraries)
SET(CPACK_GENERATOR "ZIP")
SET(CPACK_PACKAGE_VERSION ${PROJ_HEAD_REVISION_LEN10})
INCLUDE(CPack)
