cmake_minimum_required(VERSION 2.6)

set(CMAKE_MODULE_PATH ${CMAKE_MODULE_PATH} ${PROJECT_SOURCE_DIR})

enable_language(CXX)

find_package(PkgConfig)
find_package(Kodi REQUIRED)
find_package(ZLIB REQUIRED)
find_package(JPEG REQUIRED)
find_package(PNG REQUIRED)
find_package(Freetype REQUIRED)
find_package(PILLOW REQUIRED)

list(APPEND DEPLIBS)

include_directories(${INCLUDES}
                    ${JPEG_INCLUDE_DIR}
                    ${PNG_INCLUDE_DIR}
                    ${Freetype_INCLUDE_DIRS}
                    ${ZLIB_INCLUDE_DIRS}
                    ${KODI_INCLUDE_DIR})
                    
list(APPEND DEPLIBS ${PILLOW_LIBRARIES} ${JPEG_LIBRARIES} ${PNG_LIBRARIES} ${FREETYPE_LIBRARIES} ${ZLIB_LIBRARIES})

build_addon(script.module.pil PILLOW DEPLIBS)

include(CPack)
