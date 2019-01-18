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

PROJECT(NEOVIM_FLTK)
CMAKE_MINIMUM_REQUIRED(VERSION 3.0)

# add c++11 support, if no then exit
INCLUDE(CheckCXXCompilerFlag)
CHECK_CXX_COMPILER_FLAG("-std=c++11" COMPILER_SUPPORTS_CXX11)
CHECK_CXX_COMPILER_FLAG("-std=c++14" COMPILER_SUPPORTS_CXX14)
# CHECK_CXX_COMPILER_FLAG("-std=c++17" COMPILER_SUPPORTS_CXX17)
CHECK_CXX_COMPILER_FLAG("/std:c++17" COMPILER_SUPPORTS_CXX17)

SET(CMAKE_CXX_STANDARD_REQUIRED ON)
IF(COMPILER_SUPPORTS_CXX17)
    SET(CMAKE_CXX_STANDARD 17)
ELSEIF(COMPILER_SUPPORTS_CXX14)
    SET(CMAKE_CXX_STANDARD 14)
ELSEIF(COMPILER_SUPPORTS_CXX11)
    SET(CMAKE_CXX_STANDARD 11)
ELSE()
    MESSAGE(FATAL_ERROR "The compiler ${CMAKE_CXX_COMPILER} has no C++11 support.")
ENDIF()

ADD_SUBDIRECTORY(src)
