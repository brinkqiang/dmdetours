cmake_minimum_required(VERSION 3.2)

PROJECT(dmdetours)

LIST(APPEND CMAKE_MODULE_PATH ${CMAKE_CURRENT_SOURCE_DIR}/cmake)
INCLUDE(cmake/ModuleImport.cmake)
INCLUDE(cmake/ModuleCompileOptions.cmake)
ModuleSetCompileOptions()
ModuleSetWinCompilerFlags()

SET(DMDETOURS_VERSION_MAJOR "1")
SET(DMDETOURS_VERSION_MINOR "0")
SET(DMDETOURS_VERSION_PATCH "1")
SET(DMDETOURS_VERSION "${DMDETOURS_VERSION_MAJOR}.${DMDETOURS_VERSION_MINOR}.${DMDETOURS_VERSION_PATCH}")

MESSAGE(STATUS "VERSION: ${DMDETOURS_VERSION}")

OPTION(USE_DMDETOURS "use dmdetours" OFF)

#add_definitions(-DUNICODE -D_UNICODE)

LibImport("dmdetours" "src/dmdetours")

set_property (
    SOURCE src/dmdetours/uimports.cpp
    APPEND PROPERTY HEADER_FILE_ONLY true)

ExeImport("samples" "dmdetours")
